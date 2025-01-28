---
title: Notas de versão do Cloud Manager 2025.1.0
description: Saiba mais sobre o lançamento do Cloud Manager 2025.1.0 no Adobe Managed Services.
feature: Release Information
exlid: 669b1f2d8fc68526eb091e0f93f70ab93033d193
exl-id: cc1dc94b-129d-4de7-8e57-8fc5dcba7d9f
source-git-commit: ca9a07354ff8316f531840a42d6ecdda5c072b9b
workflow-type: ht
source-wordcount: '196'
ht-degree: 100%

---

# Notas de versão do Cloud Manager 2025.1.0 no Adobe Managed Services {#release-notes}

<!-- RELEASE WIKI  https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2024.12.0+Release -->

Saiba mais sobre o lançamento do [!UICONTROL Cloud Manager] 2025.1.0 no Adobe Managed Services.

>[!NOTE]
>
>Consulte as [notas de versão atuais do Adobe Experience Manager as a Cloud Service](https://experienceleague.adobe.com/pt-br/docs/experience-manager-cloud-service/content/release-notes/home).

## Datas de lançamento {#release-date}

<!-- SAVE FOR FUTURE POSSIBLE USE No notable bugs or features for the September release of Cloud Manager. -->

A data de lançamento do [!UICONTROL Cloud Manager] 2025.1.0 é quarta-feira, 22 de janeiro de 2024.

A próxima versão está planejada para quinta-feira, 13 de fevereiro de 2025.

## Novidades {#what-is-new}

**Regras de qualidade do código - Atualização do Sonar Cube:** a etapa de qualidade do código do Cloud Manager começará a usar o SonarQube Server 9.9 a partir da versão 2025.2.0 do Cloud Manager, que será lançada na quinta-feira, 13 de fevereiro de 2025.

Para fins de preparação, as regras atualizadas do SonarQube agora estão disponíveis em [Regras de qualidade do código](/help/using/code-quality-testing.md#code-quality-testing-step).

É possível obter uma prévia das novas regras definindo a seguinte variável de texto do pipeline (veja a captura de tela abaixo):

`CM_BUILD_IMAGE_OVERRIDE` = `self-service-build:sonar-99-upgrade-java17or21`

Além disso, defina a seguinte variável para garantir que a etapa de qualidade do código seja executada para a mesma confirmação (normalmente ignorada para a mesma `commitId`):

`CM_DISABLE_BUILD_REUSE` = `true`

![Página de configuração de variáveis](/help/release-notes/assets/variables-config.png)

>[!NOTE]
>
>A Adobe recomenda criar um novo pipeline de qualidade de código CI/CD e configurá-lo para a mesma ramificação que seu pipeline de produção principal. Defina as variáveis apropriadas *antes* do lançamento de 13 de fevereiro de 2025 para validar se as novas regras aplicadas não introduzem bloqueadores.

<!-- ## Early adoption program {#early-adoption}

Be a part of Cloud Manager's early adoption program and have a chance to test upcoming features. -->


<!-- ## Bug fixes {#bug-fixes}

* A

Known Issues {#known-issues}

* A -->
