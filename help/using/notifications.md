---
title: Notificações
description: Saiba como o Cloud Manager notifica você sobre eventos importantes.
exl-id: cfd5655f-2d2c-4304-b25c-6cdffe7ff64c
source-git-commit: e767d9ff5e3df0047d2cf47d7b0842854101a01a
workflow-type: tm+mt
source-wordcount: '573'
ht-degree: 100%

---


# Notificações {#notifications}

Saiba como o Cloud Manager notifica você sobre eventos importantes.

## Notificações no Cloud Manager {#cloud-manager-notifications}

O [!UICONTROL Cloud Manager] envia notificações quando um pipeline de produção é iniciado e concluído (com sucesso ou não). Ele realiza esse envio no início de uma implantação de produção, bem como quando as etapas **Aprovação de ativação** e **Programado** são atingidas. Essas notificações são enviadas por meio do sistema de notificações da [!UICONTROL Experience Cloud].

>[!NOTE]
>
>A aprovação e as notificações programadas são enviadas apenas aos usuários nas funções de **Proprietário da empresa**, **Gerente de programa** e **Gerente de implantação**.

As notificações são exibidas em uma barra lateral no [!UICONTROL Cloud Manager] e na Adobe [!UICONTROL Experience Cloud].

O ícone de sino no cabeçalho é destacado quando você tem novas notificações.

![Ícone de notificações](/help/assets/notifications-bell-badged.png)

Clique no ícone de sino para abrir a barra lateral e exibir as notificações. A guia **Notificações** na barra lateral lista as notificações mais recentes, como confirmações de implantação. As notificações se referem aos seus ambientes.

![Barra lateral de notificações](/help/assets/notifications-activities.png)

A guia **Avisos** inclui avisos de produto da Adobe. Os avisos dizem respeito ao produto.

![Barra lateral de notificações](/help/assets/notificaitons-announcements.png)

Clique em uma notificação ou anúncio para exibir os detalhes. As notificações vinculadas a atividades como implantações de pipeline levam você aos detalhes dessa atividade, como a janela de execução do pipeline.

Clique na opção **Exibir tudo** na parte inferior do painel para exibir todos os avisos na caixa de entrada.

Clique na opção **Marcar tudo como lido** na parte inferior do painel para marcar todas as notificações não lidas como lidas e limpar o símbolo do ícone de sino.

## Configuração de notificação {#configuration}

Você pode personalizar como recebe notificações e quais notificações recebe.

Clique no ícone de engrenagem na parte inferior da barra lateral de notificações.

![Ícone Configurações de notificação](/help/assets/notifications-configuration.png)

Isso abre a janela **Preferências da Experience Cloud**, onde é possível definir suas assinaturas de notificação e como você recebe as notificações.

### Assinaturas {#subscriptions}

As assinaturas definem para quais produtos você recebe notificações e quais notificações.

![Assinaturas de notificação](/help/assets/notifications-subscriptions.png)

Por padrão, você receberá todas as notificações para todos os produtos. Clique em **Personalizar** ao lado de um produto para definir os tipos de notificações que você recebe para esse produto.

![Personalização de assinatura de notificação](/help/assets/notifications-subscriptions-customize.png)

### Prioridade {#priority}

Os alertas de prioridade serão marcados com uma tag **ALTA** e podem ser configurados para serem recebidos exclusivamente como alertas. Na seção **Prioridade**, você pode definir quais categorias se qualificam como notificações de prioridade.

![Prioridade de notificação](/help/assets/notifications-priority.png)

Use o menu suspenso para adicionar à lista de categorias que se qualificam como prioridade. Clique no X ao lado dos nomes das categorias para removê-las.

### Alertas {#alerts}

Os alertas são exibidos no canto superior direito da janela por alguns segundos. Use a seção **Alertas** para definir para quais notificações você recebe alertas.

![Alertas de notificação](/help/assets/notifications-alerts.png)

Você pode definir o comportamento dos alertas.

* **Mostrar alertas para** - Define os tipos de notificações que acionam alertas
* **Os alertas devem ficar na tela até que eu os descarte** - Controla se os alertas devem persistir, a menos que você os ignore ativamente
* **Duração** - Define quanto tempo o alerta deve permanecer na tela caso você não tenha escolhido que eles fiquem na tela.

### Emails {#emails}

As notificações estão disponíveis na interface da web em todas as soluções da Adobe [!UICONTROL Experience Cloud]. Também é possível optar por enviar essas notificações por email na seção **Emails**.

![Emails de notificação](/help/assets/notifications-emails.png)

Por padrão, nenhum email é enviado. Você pode optar por receber emails:

* Instantaneamente
* Diariamente
* Semanalmente

Quando a opção **Notificações instantâneas** for escolhida, os emails serão enviados imediatamente para cada notificação. Para as opções **Resumo diário** e **Resumo semanal**, você pode escolher quando o resumo diário é enviado e em que dia e quando o resumo semanal é enviado.
