---
title: Notas de versão do Cloud Manager 2025.2.0
description: Saiba mais sobre o lançamento do Cloud Manager 2025.2.0 no Adobe Managed Services.
feature: Release Information
exlid: 669b1f2d8fc68526eb091e0f93f70ab93033d193
exl-id: cc1dc94b-129d-4de7-8e57-8fc5dcba7d9f
source-git-commit: 51dd060ec9b922ace9ce537cac669c61154284e8
workflow-type: tm+mt
source-wordcount: '241'
ht-degree: 26%

---

# Notas de versão do Cloud Manager 2025.2.0 no Adobe Managed Services {#release-notes}

<!-- RELEASE WIKI  https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2025.02.0+Release -->

Saiba mais sobre o lançamento do [!UICONTROL Cloud Manager] 2025.2.0 no Adobe Managed Services.

Consulte também as [notas de versão atuais do Adobe Experience Manager as a Cloud Service](https://experienceleague.adobe.com/pt-br/docs/experience-manager-cloud-service/content/release-notes/home).

## Datas de lançamento {#release-date}

A data de lançamento do [!UICONTROL Cloud Manager] 2025.2.0 é sexta-feira, 13 de fevereiro de 2025.

A próxima versão está planejada para sexta-feira, 13 de março de 2025.

## Novidades {#what-is-new}

<!-- * The AEM Code Quality step now uses SonarQube 9.9 Server, replacing the older 7.4 version. This upgrade brings additional security, performance, and code quality checks, offering more comprehensive analysis and coverage for your projects. --> <!-- CMGR-45683 -->

* **SonarQube atualizado**

  A partir de quinta-feira, 13 de fevereiro de 2025, a etapa de qualidade do código do Cloud Manager agora usa SonarQube 9.9.5.90363.

  As regras atualizadas, disponíveis para o AMS em [este link](/help/using/code-quality-testing.md#code-quality-testing-step), determinam as pontuações de segurança e a qualidade do código para os pipelines do Cloud Manager.

* O SonarQube 9.9 agora é o mecanismo de verificação de qualidade de código padrão para todos os clientes.

* **Suporte ao ambiente de compilação do Java 17 e Java 21**

  Agora, os clientes podem, opcionalmente, criar com o Java 17 ou Java 21, beneficiando-se de melhorias de desempenho e novos recursos de linguagem. Consulte [Criar ambiente](/help/getting-started/build-environment.md) para obter as etapas de configuração, incluindo a atualização da descrição do projeto Maven e determinadas versões da biblioteca.

  >[!NOTE]
  >Para ambientes Cloud Service, quando a versão de build é definida como Java 17 ou Java 21, o tempo de execução assume o Java 21 como padrão.

* **Validações de Cópia de Conteúdo estendidas**

  As regras de validação da cópia de conteúdo foram atualizadas. Com esta versão, os usuários não poderão mais acionar uma cópia de conteúdo se houver execuções de pipeline ativas no ambiente de origem ou de destino. Os usuários devem aguardar até que todas as execuções de pipeline em andamento sejam concluídas antes de iniciar uma cópia de conteúdo.

<!-- 
## Early adoption program {#early-adoption}

Be a part of Cloud Manager's early adoption program and have a chance to test upcoming features.

### Bring Your Own Git - now with support for GitLab and Bitbucket {#gitlab-bitbucket}

The **Bring Your Own Git** feature has been expanded to include support for external repositories, such as GitLab and Bitbucket. This new support is in addition to the already existing support for private and enterprise GitHub repositories. When you add these new repos, you can also link them directly to your pipelines. You can host these repositories on public cloud platforms or within your private cloud or infrastructure. This integration also removes the need for constant code synchronization with the Adobe repository and provides the ability to validate pull requests before merging them into a main branch.

Pipelines using external repositories (excluding GitHub-hosted ones) and the **Deployment Trigger** set to **On Git Changes** now start automatically.

See [Add external repositories in Cloud Manager](/help/managing-code/external-repositories.md).

![Add Repository dialog box](/help/release-notes/assets/repositories-add-release-notes.png)

>[!NOTE]
>
>Currently, the out-of-the-box pull request code quality checks are exclusive to GitHub-hosted repositories, but an update to extend this functionality to other Git vendors is in the works.

If you are interested in testing this new feature and sharing your feedback, send an email to [Grp-CloudManager_BYOG@adobe.com](mailto:Grp-CloudManager_BYOG@adobe.com) from your email address associated with your Adobe ID. Be sure to include which Git platform you want to use and whether you are on a private/public or enterprise repository structure. -->


<!-- ## Bug fixes {#bug-fixes}

* A

Known Issues {#known-issues}

* A -->
