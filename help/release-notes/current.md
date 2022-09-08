---
title: Notas da versão 2022.9.0
description: Estas são as notas de versão do Cloud Manager versão 2022.9.0.
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: e74d386d0b2d50a7e276bb7ead7594ef448742ae
workflow-type: tm+mt
source-wordcount: '196'
ht-degree: 4%

---


# Notas de versão do Cloud Manager versão 2022.9.0 {#release-notes}

Esta página documenta as notas de versão do [!UICONTROL Cloud Manager] versão 2022.9.0.

>[!NOTE]
>
>Para obter as notas de versão mais recentes do Cloud Manager AEM as a Cloud Service, consulte [Cloud Manager nas notas de versão atuais AEM as a Cloud Service.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html)

## Data de lançamento {#release-date}

A data de lançamento de [!UICONTROL Cloud Manager] a versão 2022.9.0 é 8 de setembro de 2022. A próxima versão está prevista para 6 de outubro de 2022.

## Novidades {#what-is-new}

* Suporte do Cloud Manager para dimensionamento automático horizontal de várias regiões.
* Novo cartão de Página de boas-vindas personalizado para usuários que têm somente uma função de Usuário do Cloud Manager, guiando-os sobre como navegar para ambientes AEM e acesso restrito ao programa.
* Clientes sem nenhuma função do Cloud Manager não poderão acessar os detalhes do programa. No entanto, eles podem navegar até os pontos de extremidade do autor da página de aterrissagem do CM.
* Elimine falhas de pipeline decorrentes de falhas de repetição obtidas ao construir maior resiliência.

## Correções de erros {#bug-fixes}

* Feedback do cliente aprimorado relacionado à criação do aplicativo de AEM do cliente quando o Maven enfrenta problemas de conectividade com acordos de recompra privados.
* Em raras ocasiões, quando o sistema de verificação de integridade não for capaz de recuperar uma pontuação de integridade válida, um evento de dimensionamento automático não será acionado.
