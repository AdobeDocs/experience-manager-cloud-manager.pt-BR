---
title: Notificações
description: Saiba como o Cloud Manager notifica você sobre eventos importantes.
exl-id: cfd5655f-2d2c-4304-b25c-6cdffe7ff64c
source-git-commit: e767d9ff5e3df0047d2cf47d7b0842854101a01a
workflow-type: tm+mt
source-wordcount: '563'
ht-degree: 1%

---


# Notificações {#notifications}

Saiba como o Cloud Manager notifica você sobre eventos importantes.

## Notificações no Cloud Manager {#cloud-manager-notifications}

[!UICONTROL Cloud Manager] envia notificações quando um pipeline de produção é iniciado e concluído (com êxito ou sem êxito), no início de uma implantação de produção, bem como quando a variável **Aprovação ao vivo** e **Programado** as etapas são atingidas. Essas notificações são enviadas por meio da variável [!UICONTROL Experience Cloud] sistema de notificação.

>[!NOTE]
>
>A aprovação e as notificações agendadas são enviadas apenas aos usuários no **Proprietário da empresa**, **Gerenciador de programas** e **Gerenciador de implantação** funções.

As notificações são exibidas em uma barra lateral no [!UICONTROL Cloud Manager] e através do Adobe [!UICONTROL Experience Cloud].

O ícone de sino no cabeçalho está danificado quando você tem novas notificações.

![Ícone Notificações](/help/assets/notifications-bell-badged.png)

Clique no ícone de sino para abrir a barra lateral e exibir as notificações. O **Notificações** na barra lateral, lista as notificações mais recentes, como confirmações de implantação. As notificações se referem aos seus ambientes.

![Barra lateral de notificações](/help/assets/notifications-activities.png)

O **Anúncios** inclui anúncios de produto do Adobe. Os anúncios dizem respeito ao produto.

![Barra lateral de notificações](/help/assets/notificaitons-announcements.png)

Clique em uma notificação ou anúncio para exibir seus detalhes. As notificações vinculadas a atividades como implantações de pipeline levam você aos detalhes dessa atividade, como a janela de execução do pipeline.

Clique no botão **Exibir tudo** na parte inferior do painel para exibir todos os anúncios na caixa de entrada.

Clique no botão **Marcar tudo como lido** na parte inferior do painel para marcar todas as notificações não lidas como lidas e limpar o símbolo do ícone de sino.

## Configuração de notificação {#configuration}

Você pode personalizar o modo como recebe as notificações e quais elas recebem.

Clique no ícone de engrenagem na parte superior da barra lateral de notificações.

![Ícone Configurações de notificação](/help/assets/notifications-configuration.png)

Isso abre o **preferências de Experience Cloud** , onde é possível definir suas assinaturas de notificação e como você recebe suas notificações.

### Assinaturas {#subscriptions}

As assinaturas definem para quais produtos você recebe notificações e quais notificações.

![Assinaturas de notificação](/help/assets/notifications-subscriptions.png)

Por padrão, você receberá todas as notificações para todos os produtos. Clique em **Personalizar** ao lado de um produto para definir os tipos de notificações que você recebe para esse produto.

![Personalização de assinatura de notificação](/help/assets/notifications-subscriptions-customize.png)

### Prioridade {#priority}

Os alertas de prioridade serão marcados com um **ALTO** e pode ser configurado para ser recebido exclusivamente como alertas. No **Prioridade** , você pode definir quais categorias se qualificam como notificações de prioridade.

![Prioridade de notificação](/help/assets/notifications-priority.png)

Use o menu suspenso para adicionar à lista de categorias qualificadas como prioridade. Clique no X ao lado dos nomes das categorias para removê-los.

### Alertas {#alerts}

Os alertas são exibidos no canto superior direito da janela por alguns segundos. Use o **Alertas** para definir para quais notificações você recebe alertas.

![Alertas de notificação](/help/assets/notifications-alerts.png)

Você pode definir o comportamento dos alertas.

* **Mostrar alertas para** - Define os tipos de notificações que acionam alertas
* **Os alertas devem ficar na tela até que eu os descarte** - Controla se os alertas devem persistir, a menos que você os ignore ativamente
* **Duração** - Define quanto tempo o alerta deve permanecer na tela, caso não tenha escolhido que eles devem permanecer na tela.

### Emails {#emails}

As notificações estão disponíveis na interface do usuário da Web em todo o Adobe [!UICONTROL Experience Cloud] soluções. Também é possível optar por enviar essas notificações por email no **Emails** seção.

![Emails de notificação](/help/assets/notifications-emails.png)

Por padrão, nenhum email é enviado. Você pode optar por receber emails como:

* Instantaneamente
* Diariamente
* Semanalmente

When **Notificações instantâneas** for escolhida, os emails serão enviados imediatamente para cada notificação. Para **Resumo diário** e **Resumo semanal** você pode escolher quando seu resumo diário é enviado e em que dia e quando seu resumo semanal é enviado.
