---
title: Notas de versão do Cloud Manager 2025.1.0
description: Saiba mais sobre o lançamento do Cloud Manager 2025.1.0 no Adobe Managed Services.
feature: Release Information
exlid: 669b1f2d8fc68526eb091e0f93f70ab93033d193
source-git-commit: 434740b5ad2dafd5a6c55d0272cf5effdfa6baac
workflow-type: tm+mt
source-wordcount: '196'
ht-degree: 39%

---

# Notas de versão do Cloud Manager 2025.1.0 no Adobe Managed Services {#release-notes}

<!-- RELEASE WIKI  https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2024.12.0+Release -->

Saiba mais sobre o lançamento do [!UICONTROL Cloud Manager] 2025.1.0 no Adobe Managed Services.

>[!NOTE]
>
>Consulte as [notas de versão atuais do Adobe Experience Manager as a Cloud Service](https://experienceleague.adobe.com/pt-br/docs/experience-manager-cloud-service/content/release-notes/home).

## Datas de lançamento {#release-date}

<!-- SAVE FOR FUTURE POSSIBLE USE No notable bugs or features for the September release of Cloud Manager. -->

A data de lançamento do [!UICONTROL Cloud Manager] 2025.1.0 é terça-feira, 22 de janeiro de 2024.

A próxima versão está planejada para sexta-feira, 13 de fevereiro de 2025.

## Novidades {#what-is-new}

**Regras de qualidade do código - Atualização do cubo do Sonar:** a etapa Qualidade do código do Cloud Manager começará a usar o SonarQube Server 9.9 com a versão Cloud Manager 2025.2.0, agendada para quinta-feira, 13 de fevereiro de 2025.

Para se preparar, as regras atualizadas do SonarQube agora estão disponíveis em [Regras de qualidade do código](/help/using/code-quality-testing.md#code-quality-testing-step).

Você pode &quot;verificar antecipadamente&quot; as novas regras definindo a seguinte variável de texto do pipeline (veja a captura de tela abaixo):

`CM_BUILD_IMAGE_OVERRIDE` = `self-service-build:sonar-99-upgrade-java17or21`

Além disso, defina a seguinte variável para garantir que a etapa de qualidade do código seja executada para a mesma confirmação (normalmente ignorada para a mesma `commitId`):

`CM_DISABLE_BUILD_REUSE` = `true`

![Página de configuração de variáveis](/help/release-notes/assets/variables-config.png)

>[!NOTE]
>
>A Adobe recomenda criar um novo pipeline de Qualidade de código CI/CD, configurado para a mesma ramificação que seu pipeline de produção principal. Defina as variáveis apropriadas *antes* da versão de 13 de fevereiro de 2025 para validar se as novas regras aplicadas não introduzem bloqueadores.

<!-- ## Early adoption program {#early-adoption}

Be a part of Cloud Manager's early adoption program and have a chance to test upcoming features. -->


<!-- ## Bug fixes {#bug-fixes}

* A

Known Issues {#known-issues}

* A -->
