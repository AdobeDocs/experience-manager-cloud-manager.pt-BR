---
title: Notas da versão 2023.11.0
description: Estas são as notas de versão do Cloud Manager 2023.11.0.
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: 264c7ffcbc9e10903880a511a4ca605be666f7e8
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 19%

---


# Notas de versão do Cloud Manager 2023.11.0 {#release-notes}

Esta página documenta as notas de versão do [!UICONTROL Cloud Manager] 2023.11.0.

>[!NOTE]
>
>Para obter as notas de versão mais recentes do Cloud Manager no AEM as a Cloud Service, consulte [Notas de versão atuais do Cloud Manager no AEM as a Cloud Service.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html?lang=pt-BR)

## Data de lançamento {#release-date}

A data de lançamento do [!UICONTROL Cloud Manager] versão 2023.11.0 é 14 de novembro de 2023. A próxima versão está planejada para 7 de dezembro de 2023.

## Novidades {#what-is-new}

* [A página de detalhes de execução do pipeline](/help/using/managing-pipelines.md#view-details) Agora, o mostrará todas as etapas em uma execução de pipeline com as que ainda não foram iniciadas esmaecidas.
* Em ambos **[Atividade](/help/using/managing-pipelines.md#activity)** e **[Pipelines](/help/using/managing-pipelines.md#pipelines)** páginas, um resumo da execução do pipeline agora está disponível ao clicar em um pipeline com um status de execução.
* Um novo **Duração** A seção foi adicionada à seção [página de detalhes do pipeline](/help/using/managing-pipelines.md#view-details) que inclui a duração média da etapa do pipeline com base na tendência histórica desse programa.
* No [página de execução do pipeline,](/help/using/managing-pipelines.md#activity-window) as etapas concluídas agora exibem a duração
* O Cloud Manager [ferramenta de cópia de conteúdo](/help/using/content-copy.md) O permite que os usuários copiem conteúdo mutável sob demanda de seus ambientes de produção AEM 6.x hospedados no AMS para ambientes inferiores para fins de teste.
* Execuções que [reutilizar artefatos de build](/help/getting-started/project-setup.md#build-artifact-reuse) Agora, o mostrará o link para a execução que criou esses artefatos inicialmente.
* A opção para selecionar **Falhas de métricas importantes** agora pode ser configurado para [pipelines de qualidade de código](/help/using/non-production-pipelines.md) também.

## Programa de adoção antecipada {#early-adoption}

Faça parte de nosso programa de adoção antecipada e tenha a chance de testar alguns recursos futuros

### Traga seu próprio GitHub {#byo-github}

Se você usar o GitHub para gerenciar os repositórios, [agora você pode validar o código diretamente nos repositórios GitHub por meio do Cloud Manager.](/help/managing-code/byo-github.md) Essa integração elimina a necessidade de sincronizar consistentemente o código com o repositório Adobe e permite verificar solicitações de pull antes de mesclá-las às ramificações principais.

Se você estiver interessado em testar esse novo recurso e compartilhar seu feedback, envie um email para `Grp-CloudManager_BYOG@adobe.com` do endereço de email associado à Adobe ID.

### Permissões personalizadas {#custom-permissions}

[Permissões personalizadas do Cloud Manager](/help/using/custom-permissions.md) O permite criar novos perfis de permissão personalizados com permissões configuráveis para restringir o acesso a programas, pipelines e ambientes para usuários do Cloud Manager.

Se você estiver interessado em testar esse novo recurso e compartilhar seu feedback, envie e envie um email `Grp-CloudManager_ams_custompermissions@adobe.com` do endereço de email associado à Adobe ID.
