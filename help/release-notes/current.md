---
title: Notas de versão do Cloud Manager 2025.4.0
description: Saiba mais sobre o lançamento do Cloud Manager 2025.4.0 no Adobe Managed Services.
feature: Release Information
exl-id: cc1dc94b-129d-4de7-8e57-8fc5dcba7d9f
source-git-commit: 54c03955e66f4b893829d4e8186babc30d4dbdb3
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 93%

---

# Notas de versão do Cloud Manager 2025.4.0 no Adobe Managed Services {#release-notes}

<!-- RELEASE WIKI  https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2025.04.0+Release -->

Saiba mais sobre o lançamento do [!UICONTROL Cloud Manager] 2025.4.0 no Adobe Managed Services.

Consulte também as [notas de versão atuais do Adobe Experience Manager as a Cloud Service](https://experienceleague.adobe.com/pt-br/docs/experience-manager-cloud-service/content/release-notes/home).

## Datas de lançamento {#release-date}

A data de lançamento do [!UICONTROL Cloud Manager] 2025.4.0 é sexta-feira, 10 de abril de 2025.

A próxima versão está planejada para sexta-feira, 8 de maio de 2025.

<!--
## What's new {#what-is-new}

* 
-->


## Programa de adoção antecipada {#early-adoption}

Participe do Programa de adoção antecipada da Cloud Manager para obter acesso exclusivo aos recursos futuros antes do lançamento geral.

As seguintes oportunidades de adoção antecipada estão disponíveis atualmente:

### Traga seu próprio Git: agora com suporte para GitLab e Bitbucket {#gitlab-bitbucket}

O recurso **Traga seu próprio Git** foi expandido para incluir suporte para repositórios externos, como GitLab e Bitbucket. Esse novo suporte é uma adição ao suporte já existente para repositórios GitHub privados e empresariais. Ao adicionar esses novos repositórios, também é possível vinculá-los diretamente aos seus pipelines. Você pode hospedar esses repositórios em plataformas de nuvem pública ou em sua infraestrutura ou nuvem privada. Essa integração também elimina a necessidade de sincronização constante do código com o repositório da Adobe e oferece a capacidade de validar solicitações de pull antes de mesclá-las em uma ramificação principal.

Os pipelines que usam repositórios externos (exceto os hospedados pelo GitHub) e o **Acionador de implantação** definidos como **Sobre alterações do Git** agora são iniciados automaticamente.

Consulte [Adicionar repositórios externos no Cloud Manager](/help/managing-code/external-repositories.md).

![Caixa de diálogo Adicionar repositório](/help/release-notes/assets/repositories-add-release-notes.png)

>[!NOTE]
>
>Atualmente, as verificações de qualidade do código de solicitação de pull prontas para uso são exclusivas de repositórios hospedados no GitHub, mas uma atualização para estender essa funcionalidade a outros fornecedores Git está em andamento.

Se tiver interesse em testar esse novo recurso e compartilhar o seu feedback, envie um email para [Grp-CloudManager_BYOG@adobe.com](mailto:Grp-CloudManager_BYOG@adobe.com) do seu endereço de email associado à sua Adobe ID. Inclua qual plataforma Git deseja usar e se você está em uma estrutura de repositório privado/público ou empresarial.

### Pipelines somente de preparo e somente de produção {#staging-production-only-pipelines}

A Adobe anuncia a introdução do suporte para [pipelines somente de preparo e somente de produção](/help/using/stage-prod-only.md). Esse novo recurso permite dividir os pipelines de implantação de produção de pilha completa em implantações menores e mais especializadas.

Se você quiser testar esse recurso e fornecer feedback, envie um email para [Grp-cloudmanager_splitpipelines@adobe.com](mailto:Grp-cloudmanager_splitpipelines@adobe.com) do seu endereço de email associado à sua Adobe ID.



<!--
### Self-service Service Pack updates for AMS Cloud Manager customers 

As part of the early adopters program, Adobe Managed Services Cloud Manager customers can now perform self-service service pack updates through the **Cloud Manager** user interface. This feature is currently available *only for development environments* and includes limited error reporting for failures.  

Customers can check for service pack updates on the **Program Overview** page under the **Environments** section (**three-dot menu**).

![Check for updates menu option](/help/release-notes/assets/check-for-updates-1.png)

![Update Service Pack dialog box](/help/release-notes/assets/check-for-updates-2.png)

The installation and upgrade process can be tracked on the **Activity** page. 

Once the process is complete, customers must **approve the execution** for the service pack upgrade to finalize successfully.

![Approve service page update](/help/release-notes/assets/check-for-updates-3.png)

If you are interested in testing this new feature and sharing your feedback, contact your Adobe Customer Success Engineer.

See also [Service Pack Updates for Development Environments - Early Adopter](/help/using/service-packs-environments.md).
-->


<!--
## Bug fixes {#bug-fixes}

* A

Known Issues {#known-issues}

* A -->
