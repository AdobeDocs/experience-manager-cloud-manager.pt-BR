---
title: Atualizações de Service Pack para ambientes de desenvolvimento - beta privado
description: Saiba como iniciar atualizações de service pack em ambientes de desenvolvimento por meio da interface do usuário do Cloud Manager.
hide: true
hidefromtoc: true
exl-id: 996a8eee-843f-45a6-8f7a-31ea405c2b32
source-git-commit: b2a14280e84bb934053968b0e93e33d30fb6086a
workflow-type: tm+mt
source-wordcount: '453'
ht-degree: 0%

---

# Atualizações de service pack em ambientes de desenvolvimento (beta privado) {#stage-prod-only}

Saiba como iniciar atualizações de service pack em ambientes de desenvolvimento por meio da interface do usuário do Cloud Manager.

>[!NOTE]
>
>Este recurso só está disponível para [o programa beta privado](/help/release-notes/current.md#beta-program).

## Visão geral {#service-pack-updates-overview}

É possível iniciar atualizações de service pack em ambientes de desenvolvimento por meio da interface do usuário do Cloud Manager. Esse recurso permite verificar atualizações de service packs disponíveis e gerenciar o processo de instalação de maneira independente.

**Principais benefícios**

* Fornece maior controle sobre atualizações de service pack do Cloud Manager.
* Reduz a dependência dos engenheiros de sucesso do cliente (CSEs) da Adobe para iniciar atualizações.
* Rastreia todo o processo de atualização no Cloud Manager.

**Limitações atuais**

* A opção de atualização de autoatendimento só está disponível para ambientes de desenvolvimento.
* Um relatório de erros limitado está disponível para atualizações com falha.
* Se surgirem problemas, você deverá entrar em contato com os CSEs da Adobe para fazer uma investigação mais aprofundada.

## Iniciar uma atualização de pacote de serviços

1. Faça logon no Cloud Manager com privilégios de Gerente de implantação.
1. Navegue até a página Visão geral do programa.
1. Na seção Ambientes, clique no ícone ![Mais, reticências](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg).

   ![Verificar se há atualizações do service pack no menu suspenso](/help/using/assets/service-pack-check-for-updates.png)

1. No menu suspenso, clique em ![Abrir no ícone de luz](https://spectrum.adobe.com/static/icons/workflow_18/Smock_OpenInLight_18_N.svg) **Verificar Atualizações** para verificar se há atualizações de service pack disponíveis.

   ![Uma lista de atualizações disponíveis é exibida e está disponível](/help/using/assets/service-pack-versions.png)

1. Clique na versão desejada do service pack na lista.
1. Clique em **Atualizar Service Pack** para iniciar o processo de atualização.
1. Na caixa de diálogo de confirmação, revise os detalhes e confirme a atualização.

   Depois de confirmado, o processo de instalação é iniciado e o progresso pode ser rastreado no Cloud Manager.

## Rastrear a atualização do pacote de serviços

Depois de iniciar a atualização, você pode monitorar o progresso na página Atividade do Cloud Manager.

**Para acompanhar a atualização do service pack:**

1. Navegue até a página Atividade no painel Cloud Manager.
1. Procure a entrada Instalação do pacote de serviços.

   ![Instalações do Service Pack](/help/using/assets/service-pack-installation.png)

1. Clique na entrada para exibir o progresso detalhado e as atualizações de status semelhantes ao seguinte:

   ![Progresso da instalação do service pack](/help/using/assets/service-pack-progression.png)

### Solução de problemas de instalação

* Se a instalação falhar, o Cloud Manager acionará automaticamente uma reversão para o estado anterior.
* Se os problemas persistirem, clique em **Baixar log** para coletar logs de erro e contate o Suporte da Adobe para solução de problemas.

## Aprovar ou rejeitar a execução do pacote de serviços

Quando a instalação for concluída, sua aprovação ou rejeição será necessária para finalizar a atualização.

**Para aprovar ou rejeitar a execução do service pack:**

1. Abra a página Atividade no Cloud Manager.
1. Localize a solicitação de aprovação pendente para a atualização do service pack.

   ![Rejeitar ou Aprovar a atualização do service pack](/help/using/assets/service-pack-reject-approve.png)

1. Siga um destes procedimentos:

   * Para finalizar a atualização, clique em **Aprovar**.

   ![Aprovação do service pack](/help/using/assets/service-pack-approve.png)

   * Para cancelar a atualização, clique em **Rejeitar**.
A instalação do service pack foi cancelada e nenhuma alteração foi aplicada.

   ![Rejeição do pacote de serviços](/help/using/assets/service-pack-reject.png)
