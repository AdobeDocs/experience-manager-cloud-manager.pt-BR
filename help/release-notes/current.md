---
title: Notas da versão 2024.5.0
description: Estas são as notas de versão do Cloud Manager 2024.5.0.
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: 395fe2a42fc2d6413dff38c9e4620c62039f87e2
workflow-type: ht
source-wordcount: '287'
ht-degree: 100%

---


# Notas de versão do Cloud Manager 2024.5.0 {#release-notes}

Esta página documenta as notas de versão do [!UICONTROL Cloud Manager] 2024.5.0.

>[!NOTE]
>
>Para obter as notas de versão mais recentes do Cloud Manager no AEM as a Cloud Service, consulte [Notas de versão atuais do Cloud Manager no AEM as a Cloud Service.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html?lang=pt-BR)

## Data de lançamento {#release-date}

A data de lançamento da versão 2024.5.0 do [!UICONTROL Cloud Manager] é 9 de maio de 2024. A próxima versão está planejada para 6 de junho de 2024.

## Novidades {#what-is-new}

* A etapa da Auditoria de conteúdo agora é ignorada quando um pipeline está em execução no [modo de emergência.](/help/using/code-deployment.md#emergency-pipeline)

## Programa de adoção antecipada {#early-adoption}

Faça parte de nosso programa de adoção antecipada e tenha a oportunidade de testar alguns recursos futuros

### Pipelines somente de preparo e somente de produção {#staging-production-only-pipelines}

O suporte para [pipelines somente de preparo e somente de produção](/help/using/stage-prod-only.md) foi introduzido, permitindo dividir os pipelines de implantação de produção de pilha completa em implantações menores e especializadas.

Se tiver interesse em testar esse novo recurso e compartilhar seu feedback, envie um email para `Grp-cloudmanager_splitpipelines@adobe.com` utilizando o endereço de email associado à sua Adobe ID.

### Traga seu próprio GitHub {#byo-github}

Se você usa o GitHub para gerenciar repositórios, [agora é possível validar o código diretamente nos seus repositórios do GitHub por meio do Cloud Manager.](/help/managing-code/byo-github.md) Essa integração elimina a necessidade de sincronizar consistentemente o código com o repositório da Adobe e permite confirmar solicitações de “pull” antes de mesclá-las às ramificações principais. Esse recurso é exclusivo do GitHub público. A compatibilidade com o GitHub auto-hospedado não está disponível.

Se tiver interesse em testar esse novo recurso e compartilhar seu feedback, envie um email para `Grp-CloudManager_BYOG@adobe.com` utilizando o endereço de email associado à sua Adobe ID.

## Correções de erros {#bug-fixes}

* Um erro em que o Cloud Manager reutilizava artefatos com o hash de confirmação errado foi corrigido.
