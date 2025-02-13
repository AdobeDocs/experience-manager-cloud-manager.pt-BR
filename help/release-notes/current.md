---
title: Notas de versão do Cloud Manager 2025.2.0
description: Saiba mais sobre o lançamento do Cloud Manager 2025.2.0 no Adobe Managed Services.
feature: Release Information
exlid: 669b1f2d8fc68526eb091e0f93f70ab93033d193
exl-id: cc1dc94b-129d-4de7-8e57-8fc5dcba7d9f
source-git-commit: 9d9bf7d689c0ace41bce3f31febe8ba78636c01f
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 93%

---

# Notas de versão do Cloud Manager 2025.2.0 no Adobe Managed Services {#release-notes}

<!-- RELEASE WIKI  https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2025.02.0+Release -->

Saiba mais sobre o lançamento do [!UICONTROL Cloud Manager] 2025.2.0 no Adobe Managed Services.

Consulte também as [notas de versão atuais do Adobe Experience Manager as a Cloud Service](https://experienceleague.adobe.com/pt-br/docs/experience-manager-cloud-service/content/release-notes/home).

## Datas de lançamento {#release-date}

*Não há erros ou recursos notáveis para a versão de fevereiro do Cloud Manager.*

A data de lançamento do [!UICONTROL Cloud Manager] 2025.2.0 é sexta-feira, 13 de fevereiro de 2025.

A próxima versão está planejada para sexta-feira, 13 de março de 2025.

## Novidades {#what-is-new}

<!-- * The AEM Code Quality step now uses SonarQube 9.9 Server, replacing the older 7.4 version. This upgrade brings additional security, performance, and code quality checks, offering more comprehensive analysis and coverage for your projects. --> <!-- CMGR-45683 -->

* A partir de quinta-feira, 13 de fevereiro de 2025, a etapa de qualidade do código do Cloud Manager usará uma versão atualizada do SonarQube 9.9.5.90363.

  As regras atualizadas, disponíveis para o AMS [neste link](/help/using/code-quality-testing.md#code-quality-testing-step), determinam as pontuações de segurança e a qualidade do código para os pipelines do Cloud Manager. Esta atualização pode afetar suas portas de qualidade, possivelmente bloqueando implantações.

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
