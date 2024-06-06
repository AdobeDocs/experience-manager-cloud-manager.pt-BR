---
title: Notas da versão 2024.6.0
description: Estas são as notas de versão do Cloud Manager 2024.6.0.
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: a41ea35cb685d4e88e016bc887eb2465963747e1
workflow-type: tm+mt
source-wordcount: '291'
ht-degree: 48%

---


# Notas de versão do Cloud Manager 2024.6.0 {#release-notes}

Esta página documenta as notas de versão do [!UICONTROL Cloud Manager] 2024.6.0.

>[!NOTE]
>
>Para obter as notas de versão mais recentes do Cloud Manager no AEM as a Cloud Service, consulte [Notas de versão atuais do Cloud Manager no AEM as a Cloud Service.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html?lang=pt-BR)

## Data de lançamento {#release-date}

A data de lançamento do [!UICONTROL Cloud Manager] A versão 2024.6.0 é 6 de junho de 2024. A próxima versão está planejada para 11 de julho de 2024.

## Novidades {#what-is-new}

* Agora você pode [usar seus próprios repositórios GitHub](/help/managing-code/private-repositories.md) como fontes para pipelines de pilha completa e de front-end.
   * Além disso, você pode aproveitar os repositórios GitHub com o [submódulos Git,](/help/managing-code/git-submodules.md) fornecendo controle aprimorado sobre os pipelines gerados automaticamente usados para validação de solicitação de pull e permitindo definir comportamentos para métricas cruciais durante a fase de verificação de código.
   * [Você também tem a escolha](/help/managing-code/github-check-config.md) para preservar o histórico de relatórios no GitHub, nomeie o pipeline e defina variáveis de pipeline para atender às suas necessidades.
* Novas regras do OakPal foram adicionadas à [Verificação de qualidade de código do Cloud Manager.](/help/using/custom-code-quality-rules.md#oakpal-ui-content-package)
   * Cada nova regra adicionada a partir de junho de 2024 é uma alteração ininterrupta.
   * Você é solicitado a resolver isso o mais rápido possível, pois essas novas regras causarão falhas nos pipelines a partir da versão de agosto de 2024 do Cloud Manager.

## Programa de adoção antecipada {#early-adoption}

Faça parte de nosso programa de adoção antecipada e tenha a oportunidade de testar alguns recursos futuros

### Pipelines somente de preparo e somente de produção {#staging-production-only-pipelines}

O suporte para [pipelines somente de preparo e somente de produção](/help/using/stage-prod-only.md) foi introduzido, permitindo dividir os pipelines de implantação de produção de pilha completa em implantações menores e especializadas.

Se tiver interesse em testar esse novo recurso e compartilhar seu feedback, envie um email para `Grp-cloudmanager_splitpipelines@adobe.com` utilizando o endereço de email associado à sua Adobe ID.
