---
title: Notificações
description: Saiba como o Cloud Manager notifica você sobre eventos importantes.
exl-id: cfd5655f-2d2c-4304-b25c-6cdffe7ff64c
source-git-commit: e767d9ff5e3df0047d2cf47d7b0842854101a01a
workflow-type: ht
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

A guia **Anúncios** inclui anúncios de produto da Adobe. Os anúncios se referem ao produto.

![Barra lateral de notificações](/help/assets/notificaitons-announcements.png)

Clique em uma notificação ou anúncio para visualizar seus detalhes. As notificações vinculadas a atividades como implantações de pipeline levam você aos detalhes dessa atividade, como a janela de execução do pipeline.

Clique na opção **Exibir tudo** na parte inferior do painel para exibir todos os anúncios na caixa de entrada.

Clique na opção **Marcar tudo como lido** na parte inferior do painel para marcar todas as notificações não lidas como lidas e remover o ícone de sino.

## Configuração de notificação {#configuration}

É possível personalizar como e quais notificações você recebe.

Clique no ícone de engrenagem na parte superior da barra lateral de notificações.

![Ícone Configurações de notificação](/help/assets/notifications-configuration.png)

Esse ícone abre a janela **Preferências da Experience Cloud**, onde é possível definir as assinaturas de notificação e como você recebe as notificações.

### Assinaturas {#subscriptions}

As assinaturas definem para quais produtos você recebe notificações e quais são essas notificações.

![Assinaturas de notificação](/help/assets/notifications-subscriptions.png)

Por padrão, você receberá todas as notificações de todos os produtos. Clique em **Personalizar** ao lado de um produto para definir os tipos de notificações que você recebe desse produto.

![Personalização de assinatura de notificação](/help/assets/notifications-subscriptions-customize.png)

### Prioridade {#priority}

Os alertas de prioridade serão marcados com uma tag **ALTA** e podem ser configurados para serem recebidos exclusivamente como alertas. Na seção **Prioridade**, você pode definir quais categorias se qualificam como notificações de prioridade.

![Prioridade de notificação](/help/assets/notifications-priority.png)

Use o menu suspenso para adicionar à lista de categorias qualificadas como prioridade. Clique no X ao lado dos nomes das categorias para removê-los.

### Alertas {#alerts}

Os alertas são exibidos no canto superior direito da janela por alguns segundos. Use a seção **Alertas** para definir para quais notificações você recebe alertas.

![Alertas de notificação](/help/assets/notifications-alerts.png)

Você pode definir o comportamento dos alertas.

* **Mostrar alertas para** - Define os tipos de notificações que acionam alertas
* **Os alertas devem permanecer na tela até eu descartá-los** - Controla se os alertas devem permanecer até você decidir removê-los
* **Duração** - Define por quanto tempo o alerta deve permanecer na tela caso você tenha escolhido que eles não devem permanecer.

### Emails {#emails}

As notificações estão disponíveis na interface da Web em todas as soluções da Adobe [!UICONTROL Experience Cloud]. Também é possível optar por enviar essas notificações por email na seção **Emails**.

![Emails de notificação](/help/assets/notifications-emails.png)

Por padrão, nenhum email é enviado. Você pode optar por receber emails:

* Instantaneamente
* Diariamente
* Semanalmente

Quando a opção **Notificações instantâneas** for escolhida, os emails serão enviados imediatamente para cada notificação. No caso do **Publicação diária** e **Publicação semanal**, você pode escolher quando o resumo diário é enviado e em que dia e quando o resumo semanal é enviado.
