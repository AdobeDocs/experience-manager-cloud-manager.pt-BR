---
title: Notas de versão do Cloud Manager 2024.12.0
description: Saiba mais sobre o lançamento do Cloud Manager 2024.12.0 no Adobe Managed Services.
feature: Release Information
exl-id: 811567af-66c9-4c1f-ae9e-60603b70ef80
source-git-commit: dcf2a4727b800f4364fcc7d757d281bde2738a55
workflow-type: tm+mt
source-wordcount: '360'
ht-degree: 87%

---

# Notas de versão do Cloud Manager 2024.12.0 no Adobe Managed Services {#release-notes}

<!-- RELEASE WIKI  https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2024.12.0+Release -->

Saiba mais sobre o lançamento do [!UICONTROL Cloud Manager] 2024.12.0 no Adobe Managed Services.

>[!NOTE]
>
>Consulte as [notas de versão atuais do Adobe Experience Manager as a Cloud Service](https://experienceleague.adobe.com/pt-br/docs/experience-manager-cloud-service/content/release-notes/home).

## Datas de lançamento {#release-date}

<!-- SAVE FOR FUTURE POSSIBLE USE No notable bugs or features for the September release of Cloud Manager. -->

A data de lançamento do [!UICONTROL Cloud Manager] 2024.12.0 é 5 de dezembro de 2024.

A próxima versão está planejada para 23 de janeiro de 2025.

## Novidades {#what-is-new}

<!-- * The AEM Code Quality step now uses SonarQube 9.9 Server, replacing the older 7.4 version. This upgrade brings additional security, performance, and code quality checks, offering more comprehensive analysis and coverage for your projects. --> <!-- CMGR-45683 -->

* A partir de quinta-feira, 13 de fevereiro de 2025, a etapa de qualidade do código do Cloud Manager agora usa uma versão atualizada do SonarQube 9.9.5.90363.

  As regras atualizadas, disponíveis para o AMS em [este link](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-manager/content/using/code-quality-testing#code-quality-testing-step), determinam as pontuações de segurança e a qualidade do código para os pipelines do Cloud Manager. Essa atualização pode afetar seus quality gates (portais de qualidade), bloqueando possivelmente as implantações.

## Programa de adoção antecipada {#early-adoption}

Faça parte do programa de adoção antecipada do Cloud Manager e aproveite a oportunidade de testar alguns dos próximos recursos.

### Traga seu próprio Git: agora com suporte para GitLab e Bitbucket {#gitlab-bitbucket}

<!-- BOTH CS & AMS -->

O recurso **Traga seu próprio Git** foi expandido para incluir suporte para repositórios externos, como GitLab e Bitbucket. Esse novo suporte é uma adição ao suporte já existente para repositórios GitHub privados e empresariais. Ao adicionar esses novos repositórios, também é possível vinculá-los diretamente aos seus pipelines. Você pode hospedar esses repositórios em plataformas de nuvem pública ou em sua infraestrutura ou nuvem privada. Essa integração também elimina a necessidade de sincronização constante do código com o repositório da Adobe e oferece a capacidade de validar solicitações de pull antes de mesclá-las em uma ramificação principal.

Os pipelines que usam repositórios externos (exceto os hospedados pelo GitHub) e o **Acionador de implantação** definidos como **Sobre alterações do Git** agora são iniciados automaticamente.

Consulte [Adicionar repositórios externos no Cloud Manager](/help/managing-code/external-repositories.md).

![Caixa de diálogo Adicionar repositório](/help/release-notes/assets/repositories-add-release-notes.png)

>[!NOTE]
>
>Atualmente, as verificações de qualidade do código de solicitação de pull prontas para uso são exclusivas de repositórios hospedados no GitHub, mas uma atualização para estender essa funcionalidade a outros fornecedores Git está em andamento.

Se tiver interesse em testar esse novo recurso e compartilhar o seu feedback, envie um email para [Grp-CloudManager_BYOG@adobe.com](mailto:Grp-CloudManager_BYOG@adobe.com) do seu endereço de email associado à sua Adobe ID. Inclua qual plataforma Git deseja usar e se você está em uma estrutura de repositório privado/público ou empresarial.


<!-- ## Bug fixes {#bug-fixes}

* A

Known Issues {#known-issues}

* A -->
