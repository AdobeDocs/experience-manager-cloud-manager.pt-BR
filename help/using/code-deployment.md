---
title: Implantação do código
description: Saiba como implantar seu código e o que acontece no Cloud Manager quando você faz.
exl-id: 3d6610e5-24c2-4431-ad54-903d37f4cdb6
source-git-commit: 6572c16aea2c5d2d1032ca5b0f5d75ade65c3a19
workflow-type: tm+mt
source-wordcount: '1609'
ht-degree: 0%

---


# Implantação do código {#code-deployment}

Saiba como implantar seu código e o que acontece no Cloud Manager quando você faz.

## Implantação do código com o Cloud Manager {#deploying-code-with-cloud-manager}

Depois de configurar o pipeline de produção, incluindo o repositório e os ambientes necessários, você estará pronto para implantar seu código.

1. Clique em **Implantar** no Cloud Manager para iniciar o processo de implantação.

   ![Botão Implantar](/help/assets/Deploy1.png)

1. O **Execução de pipeline** será exibida. Clique em **Criar** para iniciar o processo.

   ![Botão Criar](/help/assets/Deploy2.png)

O processo de build inicia o processo de implantação do código, incluindo as seguintes etapas:

* Implantação de preparo
* Teste de preparo
* Implantação de produção

Você pode revisar as etapas de vários processos de implantação exibindo registros ou revisando resultados para os critérios de teste.

## Etapas da implantação {#deployment-steps}

Várias ações ocorrem durante cada etapa da implantação, descritas nesta seção. Consulte a seção [Detalhes do Processo de Implantação](#deployment-process) para obter detalhes técnicos sobre como o próprio código é implantado nos bastidores.

### Etapa de implantação de estágio {#stage-deployment}

O **Implantação de preparo** A etapa inclui as seguintes ações:

* **Validação**: Essa etapa garante que o pipeline esteja configurado para usar os recursos disponíveis no momento, por exemplo, que a ramificação configurada exista e que os ambientes estejam disponíveis.
* **Teste de compilação e unidade**: Essa etapa executa um processo de criação contêiner. Consulte o documento [O ambiente de build](/help/getting-started/build-environment.md) para obter detalhes.
* **Verificação de código**: Esta etapa avalia a qualidade do código de seu aplicativo. Consulte o documento [Como entender os resultados de teste](/help/using/code-quality-testing.md) para obter detalhes sobre o processo de teste.
* **Implantar no Estágio**

![Implantação de preparo](/help/assets/Stage_Deployment1.png)

### Etapa de teste de estágio {#stage-testing}

O **Teste de preparo** A etapa inclui as seguintes ações:

* **Teste de segurança**: Esta etapa avalia o impacto na segurança do código no ambiente de AEM. Consulte o documento [Como entender os resultados de teste](/help/using/code-quality-testing.md) para obter detalhes sobre o processo de teste.
   * **Teste de desempenho**: Esta etapa avalia o desempenho do código. Consulte [Como entender os resultados de teste](/help/using/code-quality-testing.md) para obter detalhes sobre o processo de teste.

   ![Teste de preparo](/help/assets/Stage_Testing1.png)

### Etapa de implantação de produção {#production-deployment}

O **Implantação de produção** , inclui as seguintes ações:

* **Pedido de aprovação**
   * Essa opção é ativada ao configurar o pipeline.
   * Com essa opção, você pode agendar a implantação de produção ou clicar em **Agora** para executar a implantação de produção imediatamente.
* **Agendar implantação de produção**
   * Essa opção é ativada ao configurar o pipeline.
   * A data e a hora programadas são especificadas em termos de fuso horário do usuário.
      ![Agendar implantação](/help/assets/Production_Deployment1.png)
* **Suporte CSE** (se estiver habilitado)
* **Implantar na produção**

![Implantação de produção](/help/assets/Prod_Deployment1.png)

Quando a implantação for concluída, o código estará em seu ambiente de destino e você poderá visualizar os logs.

![Implantação concluída](/help/assets/Production_Deployment2.png)

## Tempos limite {#timeouts}

As etapas a seguir atingirão o tempo limite se forem deixadas aguardando o feedback do usuário:

| Etapa | Tempo limite |
|--- |--- |
| Teste de qualidade do código | 14 dias |
| Teste de segurança | 14 dias |
| Teste de desempenho | 14 dias |
| Pedido de aprovação | 14 dias |
| Agendar implantação de produção | 14 dias |
| Suporte CSE | 14 dias |

## Detalhes do Processo de Implantação {#deployment-process}

O Cloud Manager carrega todos os arquivos target/*.zip produzidos pelo processo de compilação em um local de armazenamento. Esses artefatos são recuperados desse local durante as fases de implantação do pipeline.

Quando o Cloud Manager é implantado em topologias que não são de produção, o objetivo é concluir a implantação o mais rápido possível e, portanto, os artefatos são implantados em todos os nós simultaneamente da seguinte maneira:

1. O Cloud Manager determina se cada artefato é um pacote de AEM ou dispatcher.
1. O Cloud Manager remove todos os dispatchers do balanceador de carga para isolar o ambiente durante a implantação.

   * Salvo configuração contrária, é possível ignorar as alterações do balanceador de carga em implantações de desenvolvimento e armazenamento temporário, ou seja, para o ambiente de desenvolvimento, desanexar e anexar etapas em pipelines que não sejam de produção e para o ambiente de preparo do pipeline de produção.

   ![Ignorar balanceador de carga](/help/assets/load_balancer.png)

   >[!NOTE]
   >
   >Espera-se que esse recurso seja usado principalmente por clientes 1-1-1.

1. Cada artefato de AEM é implantado em cada instância AEM por meio de APIs do Gerenciador de Pacotes, com dependências de pacote determinando a ordem de implantação.

   * Para saber mais sobre como você pode usar pacotes para instalar novas funcionalidades, transferir conteúdo entre instâncias e fazer backup do conteúdo do repositório, consulte o documento [Gerenciador de pacotes.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developer-tools/package-manager.html)
   >[!NOTE]
   >
   >Todos os artefatos AEM são implantados tanto no autor quanto nos editores. Os modos de execução devem ser aproveitados quando configurações específicas de nó são necessárias. Para saber mais sobre como os run-modes permitem ajustar a instância de AEM para uma finalidade específica, consulte o [seção Modos de execução do documento Implantação para AEM as a Cloud Service.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/deploying/overview.html#runmodes)

1. O artefato do dispatcher é implantado em cada dispatcher da seguinte maneira:

   1. O backup das configurações atuais é feito e copiado para um local temporário.
   1. Todas as configurações são excluídas, exceto os arquivos imutáveis. Consulte o documento [Configurações do Dispatcher](/help/getting-started/dispatcher-configurations.md) para obter mais detalhes. Isso limpa os diretórios para garantir que nenhum arquivo órfão seja deixado para trás.
   1. O artefato é extraído para o `httpd` diretório. Arquivos imutáveis não são substituídos. Quaisquer alterações feitas em arquivos imutáveis no repositório Git serão ignoradas no momento da implantação. Esses arquivos são fundamentais para a estrutura do AMS Dispatcher e não podem ser alterados.
   1. O Apache executa um teste de configuração. Se nenhum erro for encontrado, o serviço será recarregado. Se ocorrer um erro, as configurações são restauradas a partir do backup, o serviço é recarregado e o erro é relatado ao Cloud Manager.
   1. Cada caminho especificado na configuração do pipeline é invalidado ou liberado do cache do dispatcher.

   >[!NOTE]
   >
   >O Cloud Manager espera que o artefato do dispatcher contenha o conjunto completo de arquivos. Todos os arquivos de configuração do dispatcher devem estar presentes no repositório Git. Arquivos ou pastas ausentes resultarão em falha na implantação.

1. Após a implantação bem-sucedida de todos os pacotes de AEM e dispatcher em todos os nós, os dispatchers serão adicionados novamente ao balanceador de carga e a implantação será concluída.

   >[!NOTE]
   >
   >você pode ignorar as alterações do balanceador de carga em implantações de desenvolvimento e armazenamento temporário, ou seja, para o ambiente de desenvolvimento, desconectar e anexar etapas em pipelines não relacionados à produção e para o ambiente de preparo do pipeline de produção.

### Implantação para fase de produção {#deployment-production-phase}

O processo de implantação das topologias de produção é um pouco diferente para minimizar o impacto para AEM visitantes do site.

As implantações de produção geralmente seguem as mesmas etapas descritas acima, mas de maneira contínua:

1. Implantar pacotes de AEM para o autor.
1. Desanexar dispatcher1 do balanceador de carga.
1. Implante pacotes de AEM para publish1 e o pacote do dispatcher para dispatcher1 em paralelo, liberar o cache do dispatcher.
1. Coloque o dispatcher1 de volta no balanceador de carga.
1. Depois que o dispatcher1 estiver novamente em serviço, desconecte o dispatcher2 do balanceador de carga.
1. Implante AEM pacotes para publish2 e o pacote do dispatcher para o dispatcher2 em paralelo, liberar o cache do dispatcher.
1. Coloque o dispatcher2 de volta no balanceador de carga.

Esse processo continua até que a implantação tenha atingido todos os editores e dispatchers na topologia.

## Modo de Execução do Pipeline de Emergência {#emergency-pipeline}

Em situações críticas, os clientes do Adobe Managed Services podem precisar implantar alterações de código em seus ambientes de preparo e produção sem esperar que um ciclo de teste completo do Cloud Manager seja executado.

Para lidar com essas situações, o pipeline de produção do Cloud Manager pode ser executado em um modo de emergência. Quando esse modo é usado, as etapas de teste de segurança e desempenho não são executadas. Todas as outras etapas, incluindo qualquer etapa de aprovação configurada, são executadas como no modo de execução normal do pipeline.

>[!NOTE]
>
>O recurso de modo de execução de pipeline de emergência é ativado programa a programa pelos engenheiros de sucesso do cliente.

### Usando o Modo de Execução do Pipeline de Emergência {#using-emergency-pipeline}

Ao iniciar a execução de um pipeline de produção, se o recurso de modo de execução de pipeline de emergência tiver sido ativado para o programa, você poderá iniciar a execução no modo normal ou de emergência em uma caixa de diálogo.

![Executar opções de pipeline](/help/assets/execution-emergency1.png)

Ao visualizar a página de detalhes da execução do pipeline para uma execução em modo de emergência, as navegações estruturais na parte superior da tela mostram um indicador de que o pipeline está sendo executado no modo de emergência.

![Navegação estrutural no modo de emergência](/help/assets/execution-emergency2.png)

A execução de um pipeline no modo de emergência também pode ser feita por meio da API do Cloud Manager ou da CLI. Para iniciar uma execução em modo de emergência, envie um `PUT` solicitação para o endpoint de execução do pipeline com o parâmetro de consulta `?pipelineExecutionMode=EMERGENCY` ou, ao usar a CLI:

```
$ aio cloudmanager:pipeline:create-execution PIPELINE_ID --emergency
```

## Reexecutar uma implantação de produção {#re-execute-deployment}

A reexecução da etapa de implantação de produção está disponível para execuções em que a etapa de implantação de produção foi concluída. O tipo de conclusão não é importante. A implantação pode ser bem-sucedida (somente para programas AMS), cancelada ou malsucedida. O principal caso de uso é onde a etapa de implantação de produção falhou por motivos transitórios. A reexecução cria uma nova execução usando o mesmo pipeline. Essa nova execução consiste em três etapas:

1. **A etapa de validação** - Essa é essencialmente a mesma validação que ocorre durante uma execução normal do pipeline.
1. **A etapa de build** - No contexto de uma reexecução, a etapa de build copia artefatos e não executa realmente um novo processo de build.
1. **A etapa de implantação de produção** - Usa a mesma configuração e opções que a etapa de implantação de produção em uma execução normal de pipeline.

A etapa de criação pode ser rotulada de forma diferente na interface do usuário para refletir que está copiando artefatos, não reconstruindo.

![Reexecução](/help/assets/Re-deploy.png)

### Limitações           {#limitations}

* A reexecução da etapa de implantação de produção só está disponível para a última execução.
* A reexecução não está disponível para execuções de reversão ou execuções de atualização por push.
* Se a última execução falhar em qualquer ponto antes da etapa de implantação de produção, a reexecução não será possível.

### Identificação de uma execução de nova execução {#identifying}

Para identificar se uma execução é uma execução reexecutada, a variável `trigger` pode ser examinado. Seu valor será `RE_EXECUTE`.

### Acionando uma Reexecução {#triggering}

Para acionar uma reexecução, uma `PUT` a solicitação precisa ser feita para o HAL Link `http://ns.adobe.com/adobecloud/rel/pipeline/reExecute` no estado da etapa de implantação de produção. Se esse link estiver presente, a execução poderá ser reiniciada a partir dessa etapa. Se estiver ausente, a execução não poderá ser reiniciada dessa etapa. Esse link só estará presente na etapa de implantação de produção

```Javascript
 {
  "_links": {
    "http://ns.adobe.com/adobecloud/rel/pipeline/logs": {
      "href": "/api/program/4/pipeline/1/execution/953671/phase/1575676/step/2983530/logs",
      "templated": false
    },
    "http://ns.adobe.com/adobecloud/rel/pipeline/reExecute": {
      "href": "/api/program/4/pipeline/1/execution?stepId=2983530",
      "templated": false
    },
    "http://ns.adobe.com/adobecloud/rel/pipeline/metrics": {
      "href": "/api/program/4/pipeline/1/execution/953671/phase/1575676/step/2983530/metrics",
      "templated": false
    },
    "self": {
      "href": "/api/program/4/pipeline/1/execution/953671/phase/1575676/step/2983530",
      "templated": false
    }
  },
  "id": "6187842",
  "stepId": "2983530",
  "phaseId": "1575676",
  "action": "deploy",
  "environment": "weretail-global-b75-prod",
  "environmentType": "prod",
  "environmentId": "59254",
  "startedAt": "2022-01-20T14:47:41.247+0000",
  "finishedAt": "2022-01-20T15:06:19.885+0000",
  "updatedAt": "2022-01-20T15:06:20.803+0000",
  "details": {
  },
  "status": "FINISHED"
```

A sintaxe do link HAL `href` não se destina a ser usado como ponto de referência. O valor real deve sempre ser lido do link HAL e não gerado.

Envio de um `PUT` a solicitação para esse endpoint resultará em uma `201` se bem-sucedido e o corpo da resposta será a representação da nova execução. É semelhante a iniciar uma execução regular por meio da API.
