---
title: Implantar o código
seo-title: Implantar o código
description: Fornece uma visão geral sobre o processo de implantação no Cloud Manager
seo-description: Saiba como implantar seu código depois de configurar o pipeline (repositório, ambiente e ambiente de teste)
uuid: 4e3807e1-437e-4922-ba48-0bcadf293a99
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: using
discoiquuid: 832a4647-9b83-4a9d-b373-30fe16092b15
feature: Implantação do código
translation-type: tm+mt
source-git-commit: c5d32d49782c899d013fcc60b9c4d2b67e9350ae
workflow-type: tm+mt
source-wordcount: '959'
ht-degree: 1%

---


# Implantar o código {#deploy-your-code}

## Implantação do código com o Cloud Manager {#deploying-code-with-cloud-manager}

Depois de configurar o Pipeline de produção (repositório, ambiente e ambiente de teste), você estará pronto para implantar seu código.

1. Clique em **Implantar** no Cloud Manager para iniciar o processo de implantação.

   ![](assets/Deploy1.png)

1. A tela **Pipeline Execution** é exibida.

   Clique em **Criar** para iniciar o processo.

   ![](assets/Deploy2.png)

1. O processo de build completo implanta seu código.

   Os seguintes estágios estão envolvidos no processo de criação:

   1. Implantação do Estágio
   1. Teste de preparo
   1. Implantação de produção

   >[!NOTE]
   >
   >Além disso, você pode revisar as etapas de vários processos de implantação exibindo registros ou revisando resultados para os critérios de teste.

   A **Implantação do preparo** envolve estas etapas:

   * Validação: Essa etapa garante que o pipeline esteja configurado para usar os recursos disponíveis no momento, por exemplo, que a ramificação configurada exista, os ambientes estarão disponíveis.
   * Teste de compilação e unidade: Essa etapa executa um processo de criação contêiner. Consulte [Compreensão do ambiente de criação](/help/using/build-environment-details.md) para obter detalhes sobre o ambiente de criação.
   * Verificação de código: Esta etapa avalia a qualidade do código de seu aplicativo. Consulte [Entender os resultados de teste](understand-your-test-results.md) para obter detalhes sobre o processo de teste.
   * Implantar no Estágio

   ![](assets/Stage_Deployment1.png)

   O **Teste de preparo** envolve as seguintes etapas:

   * Teste de segurança: Esta etapa avalia o impacto na segurança do código de seu aplicativo no ambiente de AEM. Consulte [Entender os resultados de teste](understand-your-test-results.md) para obter detalhes sobre o processo de teste.
   * Teste de desempenho: Esta etapa avalia o desempenho do código do aplicativo. Consulte [Entender os resultados de teste](understand-your-test-results.md) para obter detalhes sobre o processo de teste.

   ![](assets/Stage_Testing1.png)

   A **Implantação de produção** envolve as seguintes etapas:

   * **Pedido de aprovação**  (se estiver habilitado)
   * **Agendar implantação de produção**  (se ativada)
   * **Suporte CSE**  (se ativado)
   * **Implantar na produção**

   ![](assets/Prod_Deployment1.png)

   >[!NOTE]
   >
   >O **Agendar implantação de produção** está ativado ao configurar o pipeline.
   >
   >
   >Usando essa opção, você pode agendar a implantação de produção ou clicar em **Now** para executar a implantação de produção imediatamente.
   >
   >
   >A data e a hora programadas são especificadas em termos de fuso horário do usuário.
   >
   >
   >Clique em **Confirmar** para verificar suas configurações.

   ![](assets/Production_Deployment1.png)

   Depois de confirmar o agendamento da implantação, a implantação do código é concluída.

   A tela a seguir é exibida quando a opção **Now** é selecionada na etapa acima.

   ![](assets/Production_Deployment2.png)

## Processo de implantação {#deployment-process}

A seção a seguir descreve como os pacotes de AEM e dispatcher são implantados na fase de estágio e na fase de produção.

O Cloud Manager carrega todos os arquivos target/*.zip produzidos pelo processo de compilação em um local de armazenamento.  Esses artefatos são recuperados desse local durante as fases de implantação do pipeline.

Quando o Cloud Manager é implantado em topologias que não são de produção, o objetivo é concluir a implantação o mais rápido possível e, portanto, os artefatos são implantados em todos os nós simultaneamente da seguinte maneira:

1. O Cloud Manager determina se cada artefato é um pacote de AEM ou dispatcher.
1. O Cloud Manager remove todos os dispatchers do Balanceador de Carga para isolar o ambiente durante a implantação.

   A menos que configurado de outra forma, você pode ignorar as Alterações no Balanceador de Carga nas Implantações de Desenvolvimento e Estágio, ou seja, desanexar e anexar etapas em pipelines não de produção, para ambientes de desenvolvimento e o pipeline de produção, para ambientes de preparo.

   ![](assets/load_balancer.png)

   >[!NOTE]
   >
   >Espera-se que esse recurso seja usado principalmente por clientes 1-1-1.

1. Cada artefato de AEM é implantado em cada instância AEM por meio de APIs do Gerenciador de Pacotes, com dependências de pacote determinando a ordem de implantação.

   Para saber mais sobre como usar pacotes para instalar novas funcionalidades, transferir conteúdo entre instâncias e fazer backup do conteúdo do repositório, consulte Como trabalhar com pacotes.

   >[!NOTE]
   >
   >Todos os artefatos AEM são implantados tanto no autor quanto nos editores. Os run-modes devem ser usados quando configurações específicas a nós são necessárias. Para saber mais sobre como os run-modes permitem ajustar a instância de AEM para uma finalidade específica, consulte Modos de Execução.

1. O artefato do dispatcher é implantado em cada dispatcher da seguinte maneira:

   1. O backup das configurações atuais é feito e copiado para um local temporário
   1. Todas as configurações são excluídas, exceto os arquivos imutáveis. Consulte Gerenciar suas configurações do Dispatcher para obter mais detalhes. Isso limpa os diretórios para garantir que nenhum arquivo órfão seja deixado para trás.
   1. O artefato é extraído para o diretório `httpd`.  Arquivos imutáveis não são substituídos. Quaisquer alterações feitas em arquivos imutáveis no repositório Git serão ignoradas no momento da implantação.  Esses arquivos são fundamentais para a estrutura do AMS Dispatcher e não podem ser alterados.
   1. O Apache executa um teste de configuração. Se nenhum erro for encontrado, o serviço será recarregado. Se ocorrer um erro, as configurações serão restauradas a partir do backup, o serviço será recarregado e o erro será relatado ao Cloud Manager.
   1. Cada caminho especificado na configuração do pipeline é invalidado ou liberado do cache do dispatcher.

   >[!NOTE]
   >O Cloud Manager espera que o artefato do dispatcher contenha o conjunto completo de arquivos.  Todos os arquivos de configuração do dispatcher devem estar presentes no repositório Git. Arquivos ou pastas ausentes resultarão em falha na implantação.

1. Após a implantação bem-sucedida de todos os pacotes de AEM e dispatcher em todos os nós, os dispatchers serão adicionados novamente ao balanceador de carga e a implantação será concluída.

   >[!NOTE]
   >É possível ignorar as alterações do Balanceador de Carga nas implantações de desenvolvimento e estágio, ou seja, desanexar e anexar etapas em pipelines não relacionados à produção, para ambientes do desenvolvedor e no pipeline de produção, para ambientes de preparo.

### Implantação para Fase de Produção {#deployment-production-phase}

O processo de implantação das topologias de produção é um pouco diferente para minimizar o impacto para AEM visitantes do Site.

As implantações de produção geralmente seguem as mesmas etapas descritas acima, mas de maneira contínua:

1. Implantar pacotes de AEM para o autor.
1. Desanexar dispatcher1 do balanceador de carga.
1. Implante pacotes de AEM para publish1 e o pacote do dispatcher para dispatcher1 em paralelo, liberar o cache do dispatcher.
1. Coloque o dispatcher1 de volta no balanceador de carga.
1. Depois que o dispatcher1 estiver novamente em serviço, desconecte o dispatcher2 do balanceador de carga.
1. Implante AEM pacotes para publish2 e o pacote do dispatcher para o dispatcher2 em paralelo, liberar o cache do dispatcher.
1. Coloque o dispatcher2 de volta no balanceador de carga.
Esse processo continua até que a implantação tenha atingido todos os editores e dispatchers na topologia.


