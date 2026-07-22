---
title: Implantação do código
description: Saiba como implantar seu código e o que acontece no Cloud Manager depois disso.
exl-id: 3d6610e5-24c2-4431-ad54-903d37f4cdb6
TQID: https://experienceleague.adobe.com/IrL3c1lGfny74kN4ZUxcNjEtHh4GJOrgH36hzbTKJI4
product_v2: id: c68cd75e-5bca-4bc3-a60e-9e183f816441id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2: id: a01bfd36-4ab8-4bf8-9dc0-5b45b890552eid: cd2426f1-5719-4006-b8c2-738e5969754b
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2: id: bce87dde-a4ab-44c9-8a18-ad66e4ddb377id: d095671a-1355-40aa-8b5f-06c33c68080b
source-git-commit: a3594b07bd6eec6f6ff7e9636f35ae83449357f3
workflow-type: tm+mt
source-wordcount: 1684
ht-degree: 82%

---

# Implantação do código {#code-deployment}

Saiba como implantar seu código e o que acontece no Cloud Manager depois disso.

## Implantar código com o Cloud Manager {#deploying-code-with-cloud-manager}

Depois de configurar o pipeline de produção, incluindo o repositório e os ambientes necessários, você poderá implantar o código.

1. Para iniciar a implantação, clique em **Implantar**.

   ![Botão Implantar](/help/assets/Deploy1.png)

1. A tela **Execução de pipeline** será exibida. Clique em **Compilação** para iniciar o processo de compilação.

   ![Botão Criar](/help/assets/Deploy2.png)

O processo de criação inicia a implantação do código, incluindo as seguintes etapas:

* Implantação de preparo
* Teste de preparo
* Implantação de produção

Você pode revisar as etapas de vários processos de implantação, visualizando os logs ou revisando os resultados dos critérios de teste.

## Etapas de implantação {#deployment-steps}

Várias ações ocorrem durante cada etapa da implantação, descritas nesta seção. Consulte [Detalhes do Processo de Implantação](#deployment-process) para obter detalhes técnicos sobre como o próprio código é implantado.

### Etapa de implantação de preparo {#stage-deployment}

A etapa **Implantação de preparo** inclui as seguintes ações:

* **Validação**: esta etapa garante que o pipeline esteja configurado para usar os recursos disponíveis no momento. Por exemplo, se a ramificação configurada existe e se os ambientes estão disponíveis.
* **Teste de build e unidade**: essa etapa executa um processo de build em containers. Consulte [O ambiente de build](/help/getting-started/build-environment.md) para mais detalhes.
* **Verificação de código**: esta etapa avalia a qualidade do código de seu aplicativo. Consulte [Entender os resultados dos testes](/help/using/code-quality-testing.md) para mais detalhes sobre o processo de teste.
* **Implantar para o preparo**

![Implantação de preparo](/help/assets/Stage_Deployment1.png)

### Etapa de teste de preparo {#stage-testing}

A etapa **Teste de preparo** inclui as seguintes ações:

* **Teste de segurança**: esta etapa avalia o impacto sobre a segurança do código no ambiente do AEM. Consulte o documento [Como entender os resultados do teste](/help/using/code-quality-testing.md) para obter detalhes sobre o processo de teste.
  * **Teste de desempenho**: esta etapa avalia o desempenho do código. Consulte [Entender os resultados dos testes](/help/using/code-quality-testing.md) para mais detalhes sobre o processo de teste.

### Etapa de implantação de produção {#production-deployment}

A etapa **Implantação de produção** inclui as seguintes ações:

* **Pedido de aprovação**
  * Essa opção é habilitada ao configurar o pipeline.
  * Com essa opção, você pode agendar a implantação de produção ou clicar em **Agora** para executar a implantação de produção imediatamente.
* **Programar implantação de produção**
  * Essa opção é habilitada ao configurar o pipeline.
  * A data e a hora agendadas são especificadas no fuso horário do usuário.
    ![Programar implantação](/help/assets/Production_Deployment1.png)
* **Suporte do CSE** (se estiver habilitado)
* **Implantar para produção**

![Implantação de produção](/help/assets/Prod_Deployment1.png)

Quando a implantação for concluída, o código estará em seu ambiente de destino e você poderá visualizar os logs.

![Implantação concluída](/help/assets/Production_Deployment2.png)

## Tempos limite {#timeouts}

As seguintes etapas atingirão o tempo-limite se forem deixadas aguardando o feedback do usuário:

| Etapa | Tempo-limite |
|--- |--- |
| Teste de qualidade do código | 7 dias |
| Teste de segurança | 7 dias |
| Teste de desempenho | 7 dias |
| Pedido de aprovação (preparo) | 7 dias |
| Pedido de aprovação (produção) | 14 dias |
| Agendar implantação em produção | 14 dias |
| Implantação de produção gerenciada | 14 dias |

## Detalhes do processo de implantação {#deployment-process}

O Cloud Manager carrega todos os `target/*.zip` arquivos produzidos pelo processo de compilação para um local de armazenamento. Esses artefatos são recuperados desse local durante as fases de implantação do pipeline.

Quando o Cloud Manager é implantado em topologias que não sejam de produção, a meta é concluir a implantação da maneira mais eficiente possível. Portanto, os artefatos são implantados em todos os nós simultaneamente da seguinte maneira:

1. O Cloud Manager determina se cada artefato é um pacote do AEM ou do Dispatcher.
1. O Cloud Manager remove todos os que são do Dispatcher do balanceador de carga para isolar o ambiente durante a implantação.

   * A menos que configurado de outra forma, você pode ignorar as alterações do balanceador de carga nas implantações de desenvolvimento e preparo. Ou seja, para o ambiente de desenvolvimento, desconecte e conecte etapas em pipelines de não produção; e para o ambiente de preparo, as etapas do pipeline de produção.

   ![Ignorar balanceador de carga](/help/assets/load_balancer.png)

   >[!NOTE]
   >
   >Espera-se que os clientes 1-1-1 usem esse recurso.

1. Cada artefato do AEM é implantado em toda instância do AEM por meio de APIs de gerenciador de pacotes, com as dependências de pacote determinando a ordem da implantação.

   * Saiba mais sobre como você pode usar pacotes para instalar novas funcionalidades, transferir conteúdo entre instâncias e fazer backup do conteúdo do repositório. Consulte [Gerenciador de pacotes](https://experienceleague.adobe.com/pt-br/docs/experience-manager-cloud-service/content/implementing/developer-tools/package-manager).

   >[!NOTE]
   >
   >Todos os artefatos do AEM são implantados tanto para o autor quanto para os editores. Os modos de execução devem ser usados quando configurações específicas de nó são necessárias. Para saber mais sobre como os modos de execução permitem ajustar a sua instância do AEM para uma finalidade específica, consulte a seção [Modos de execução do documento Implantação no AEM as a Cloud Service](https://experienceleague.adobe.com/pt-br/docs/experience-manager-cloud-service/content/implementing/deploying/overview#runmodes).

1. O artefato do Dispatcher é implantado em cada Dispatcher da seguinte maneira:

   1. O backup das configurações atuais é feito e copiado para um local temporário.
   1. Todas as configurações são excluídas, exceto os arquivos imutáveis. Consulte [Configurações do Dispatcher](/help/getting-started/dispatcher-configurations.md) para mais detalhes. Essa abordagem limpa os diretórios para garantir que nenhum arquivo órfão permaneça.
   1. O artefato é extraído para o diretório `httpd`. Arquivos imutáveis não são substituídos. Quaisquer alterações feitas em arquivos imutáveis no repositório Git serão ignoradas no momento da implantação. Esses arquivos são essenciais para a estrutura do AMS Dispatcher e não podem ser alterados.
   1. O Apache executa um teste de configuração. Se nenhum erro for encontrado, o serviço é reiniciado. Se forem encontrados erros, as configurações serão restauradas a partir do backup, o serviço será recarregado e o erro será relatado ao Cloud Manager.
   1. Cada caminho especificado na configuração do pipeline é invalidado ou removido do cache do Dispatcher.

   >[!NOTE]
   >
   >O Cloud Manager espera que o artefato do Dispatcher contenha o conjunto completo de arquivos. Todos os arquivos de configuração do Dispatcher devem estar presentes no repositório Git. Arquivos ou pastas ausentes resultarão em falhas de implantação.

1. Após a implantação bem-sucedida de todos os pacotes do AEM e do Dispatcher em todos os nós, os pacotes do Dispatcher são adicionados novamente ao balanceador de carga, e a implantação será concluída.

   >[!NOTE]
   >
   >Você pode ignorar as alterações do balanceador de carga em implantações de desenvolvimento e preparo. Ou seja, para ambientes de desenvolvimento, desconecte e conecte etapas em pipelines de não produção e, para ambientes de preparo, o pipeline de produção.

### Implantação para a fase de produção {#deployment-production-phase}

O processo de implantação das topologias de produção é um pouco diferente para minimizar o impacto para visitantes de sites do AEM.

As implantações de produção seguem as mesmas etapas descritas acima, mas de maneira contínua:

1. Implante pacotes do AEM para o autor.
1. Desconecte dispatcher1 do balanceador de carga.
1. Implante pacotes do AEM para publish1 e o pacote do Dispatcher para dispatcher1 em paralelo, e, em seguida, limpe o cache do Dispatcher.
1. Coloque dispatcher1 de volta no balanceador de carga.
1. Quando dispatcher1 estiver novamente em serviço, desconecte dispatcher2 do balanceador de carga.
1. Implante pacotes do AEM para publish2 e o pacote do Dispatcher para dispatcher2 em paralelo, e, em seguida, limpe o cache do Dispatcher.
1. Coloque dispatcher2 de volta no balanceador de carga.

Esse processo continua até que a implantação tenha atingido todos os editores e dispatchers na topologia.

## Modo de execução de pipeline de emergência {#emergency-pipeline}

Em cenários urgentes, os clientes do Adobe Managed Services precisam implantar alterações de código em seus ambientes de preparo e produção imediatamente. Essa capacidade permite ignorar o ciclo de teste completo do Cloud Manager.

Para lidar com essas situações, o pipeline de produção do Cloud Manager pode ser executado em um modo de emergência. Quando esse modo é usado, as etapas de teste de segurança e desempenho não são executadas. Todas as outras etapas, incluindo qualquer etapa de aprovação configurada, são executadas como no modo de execução normal do pipeline.

>[!NOTE]
>
>O recurso de modo de execução de pipeline de emergência é ativado programa por programa. Os engenheiros de sucesso do cliente executam a ativação.

### Usar o modo de execução de pipeline de emergência {#using-emergency-pipeline}

Ao iniciar a execução de um pipeline de produção, você pode escolher entre o modo normal e o modo de emergência em uma caixa de diálogo. Essa opção estará disponível se o recurso de modo de execução de pipeline de emergência estiver ativado para o programa. Essa opção fica disponível após a habilitação do recurso.

![Executar opções de pipeline](/help/assets/execution-emergency1.png)

Ao visualizar a página de detalhes da execução do pipeline para uma execução em modo de emergência, as navegações estruturais na parte superior da tela mostram um indicador de que o pipeline está sendo executado no modo de emergência.

![Navegação estrutural no modo de emergência](/help/assets/execution-emergency2.png)

A execução de um pipeline no modo de emergência também pode ser feita por meio da API ou CLI do Cloud Manager. Para iniciar uma execução em modo de emergência, envie uma solicitação `PUT` para o ponto de acesso de execução do pipeline com o parâmetro de consulta `?pipelineExecutionMode=EMERGENCY` ou, ao usar a CLI:

```
$ aio cloudmanager:pipeline:create-execution PIPELINE_ID --emergency
```

## Reexecutar uma implantação de produção {#reexecute-deployment}

Em casos raros, as etapas de implantação de produção podem falhar por motivos transitórios. Nesses casos, é possível executar novamente a etapa de implantação em produção, desde que ela tenha sido concluída, independentemente de ter sido bem-sucedida, cancelada ou malsucedida. A reexecução é realizada com o mesmo pipeline, que consiste nas três etapas a seguir:

1. **A etapa de validação**: a mesma validação que ocorre durante uma execução de pipeline normal.
1. **A etapa de compilação** - No contexto de uma reexecução, a etapa de compilação copia artefatos e não executa um novo processo de compilação.
1. **A etapa de implantação em produção**: usa as mesmas configurações e opções que a etapa de implantação em produção em uma execução de pipeline normal.

Nessas circunstâncias, quando uma reexecução for possível, a página de status do pipeline de produção fornecerá a opção **Reexecutar** ao lado da opção tradicional **Baixar log de compilação**.

![A opção Reexecutar na janela de visão geral do pipeline](/help/assets/re-execute.png)

>[!NOTE]
>
>Em uma reexecução, a etapa de compilação apresenta informações na interface que indicam que está copiando artefatos, não os recompilando.

### Limitações {#limitations}

* A reexecução da etapa de implantação de produção só está disponível para a última execução.
* A reexecução não está disponível para execuções de reversão ou de atualização por push.
* Se a última execução falhar em qualquer ponto antes da etapa de implantação em produção, não será possível iniciar uma reexecução.


### Reexecutar API {#reexecute-api}

Além de estar disponível na interface, [a API do Cloud Manager](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api#tag/Pipeline-Execution) pode ser usada para acionar reexecuções e identificar execuções que foram acionadas como reexecuções.

#### Acionar uma reexecução {#triggering}

Para acionar uma reexecução, uma solicitação `PUT` precisa ser feita para o link HAL `http://ns.adobe.com/adobecloud/rel/pipeline/reExecute` no estado da etapa de implantação de produção.

* Se esse link estiver presente, a execução poderá ser reiniciada dessa etapa.
* Se estiver ausente, a execução não poderá ser reiniciada a partir dessa etapa.

Esse link só está disponível para a etapa de implantação de produção.

```javascript
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

A sintaxe do valor `href` do link HAL é apenas um exemplo e o valor real deve sempre ser lido do link HAL, portanto, não deve ser gerado.

O envio de uma solicitação `PUT` a este ponto de acesso resultará em uma resposta `201`, se bem-sucedido. O corpo da resposta é a representação da nova execução. Essa funcionalidade é semelhante a iniciar uma execução normal por meio da API.

#### Identificar uma reexecução {#identifying}

O sistema identifica execuções reexecutadas pelo valor `RE_EXECUTE` no campo de acionador.