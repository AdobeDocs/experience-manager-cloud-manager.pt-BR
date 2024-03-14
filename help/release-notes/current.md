---
title: Notas da versão 2024.3.0
description: Estas são as notas de versão do Cloud Manager 2024.3.0.
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: 22730ba281f7c1c4720158a3a813c56b815a0af1
workflow-type: tm+mt
source-wordcount: '268'
ht-degree: 68%

---


# Notas de versão do Cloud Manager 2024.3.0 {#release-notes}

Esta página documenta as notas de versão do [!UICONTROL Cloud Manager] 2024.3.0.

>[!NOTE]
>
>Para obter as notas de versão mais recentes do Cloud Manager no AEM as a Cloud Service, consulte [Notas de versão atuais do Cloud Manager no AEM as a Cloud Service.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html)

## Data de lançamento {#release-date}

A data de lançamento do [!UICONTROL Cloud Manager] A versão 2024.3.0 é 14 de março de 2024. A próxima versão está planejada para 11 de abril de 2024.

## Novidades {#what-is-new}

* Detalhes que incluem informações de IP/DNS (FQDN) de servidores verdes agora são exibidos na interface do Cloud Manager.

## Programa de adoção antecipada {#early-adoption}

Faça parte de nosso programa de adoção antecipada e tenha a oportunidade de testar alguns recursos futuros

### Traga seu próprio GitHub {#byo-github}

Se você usa o GitHub para gerenciar repositórios, [agora é possível validar o código diretamente nos seus repositórios do GitHub por meio do Cloud Manager.](/help/managing-code/byo-github.md) Essa integração elimina a necessidade de sincronizar consistentemente o código com o repositório da Adobe e permite confirmar solicitações de “pull” antes de mesclá-las às ramificações principais. Esse recurso é exclusivo do GitHub público. A compatibilidade com o GitHub auto-hospedado não está disponível.

Se tiver interesse em testar esse novo recurso e compartilhar seu feedback, envie um email para `Grp-CloudManager_BYOG@adobe.com` utilizando o endereço de email associado à sua Adobe ID.

## Correções de erros {#bug-fixes}

* Correção de um erro quando os logs apropriados não eram gerados durante a etapa de teste de desempenho quando a métrica de taxa de erro falhava.
* A lógica aprimorada no serviço de teste de desempenho encarregado de detectar a ausência de uma página no site (404) agora garante uma implantação mais estável e ininterrupta.
