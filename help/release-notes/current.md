---
title: Notas da versão 2023.12.0
description: Estas são as notas de versão do Cloud Manager 2023.12.0.
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: 2ac254508e4015fea21c4fcd087703ac5fbeeec6
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 63%

---


# Notas de versão do Cloud Manager 2023.12.0 {#release-notes}

Esta página documenta as notas de versão do [!UICONTROL Cloud Manager] 2023.12.0.

>[!NOTE]
>
>Para obter as notas de versão mais recentes do Cloud Manager no AEM as a Cloud Service, consulte [Notas de versão atuais do Cloud Manager no AEM as a Cloud Service.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html?lang=pt-BR)

## Data de lançamento {#release-date}

A data de lançamento do [!UICONTROL Cloud Manager] A versão 2023.12.0 é 14 de dezembro de 2023. A próxima versão está planejada para 18 de janeiro de 2024.

## Novidades {#what-is-new}

* As [permissões personalizadas do Cloud Manager](/help/using/custom-permissions.md) permitem criar novos perfis com permissões configuráveis para restringir o acesso a programas, pipelines e ambientes para usuários do Cloud Manager.
* As implantações de atualizações no [ambiente de compilação](/help/getting-started/build-environment.md) que foram [anunciado e iniciado com a versão de outubro do Cloud Manager](/help/release-notes/2023/2023-10-0.md) foram concluídas.
   * O suporte para o Nó 18 foi adicionado para [pipelines de front-end e pilha completa.](/help/overview/ci-cd-pipelines.md)
   * A versão secundária do Java 8 foi atualizada para `jdk1.8.0_371`.
   * A versão secundária do Java 11 foi atualizada para `jdk-11.0.20`.
   * O Maven foi atualizado para a versão 3.8.8
      * O Maven agora desativa todos os inseguros `http://*` espelhos por padrão.
      * [Adobe recomenda](/help/getting-started/build-environment.md#https-maven) Os usuários do atualizam os repositórios Maven para usar HTTPS em vez de HTTP.
* A imagem base do container de build foi atualizada para Ubuntu 22.04.

## Programa de adoção antecipada {#early-adoption}

Faça parte de nosso programa de adoção antecipada e tenha a oportunidade de testar alguns recursos futuros

### Traga seu próprio GitHub {#byo-github}

Se você usa o GitHub para gerenciar repositórios, [agora é possível validar o código diretamente nos seus repositórios do GitHub por meio do Cloud Manager.](/help/managing-code/byo-github.md) Essa integração elimina a necessidade de sincronizar consistentemente o código com o repositório da Adobe e permite verificar solicitações “pull” antes de mesclá-las às ramificações principais.

Se tiver interesse em testar esse novo recurso e compartilhar seu feedback, envie um email para `Grp-CloudManager_BYOG@adobe.com` utilizando o endereço de email associado à sua Adobe ID.
