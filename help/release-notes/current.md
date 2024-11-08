---
title: Notas de versão do Cloud Manager 2024.11.0
description: Saiba mais sobre o lançamento do Cloud Manager 2024.11.0.
feature: Release Information
source-git-commit: 4c22de9fa675edcd743d7acce6c7a1def8efa414
workflow-type: tm+mt
source-wordcount: '457'
ht-degree: 62%

---

# Notas de versão do Cloud Manager 2024.11.0 {#release-notes}

Saiba mais sobre a versão do [!UICONTROL Cloud Manager] 2024.11.0.

>[!NOTE]
>
>Consulte as [notas de versão atuais do Adobe Experience Manager as a Cloud Service](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/release-notes/home).

## Datas de lançamento {#release-date}

<!-- SAVE FOR FUTURE POSSIBLE USE No notable bugs or features for the September release of Cloud Manager. -->

A data de lançamento do [!UICONTROL Cloud Manager] 2024.11.0 é 7 de novembro de 2024.

A próxima versão planejada é 5 de dezembro de 2024.

## Novidades {#what-is-new}

* Quando as páginas são redirecionadas para outro domínio durante os testes de desempenho, os resultados do teste dessas páginas são excluídos, pois não representam precisamente o desempenho real. <!-- (CMGR-5637) -->

## Programa de adoção antecipada {#early-adoption}

Faça parte do programa de adoção antecipada do Cloud Manager e aproveite a oportunidade de testar alguns dos próximos recursos.

### Traga seu próprio Git: agora com suporte para GitLab e Bitbucket {#gitlab-bitbucket}

<!-- BOTH CS & AMS -->

O recurso **Traga seu próprio Git** foi expandido para incluir suporte para repositórios externos, como GitLab e Bitbucket. Esse novo suporte é uma adição ao suporte já existente para repositórios GitHub privados e empresariais. Ao adicionar esses novos repositórios, também é possível vinculá-los diretamente aos seus pipelines. Você pode hospedar esses repositórios em plataformas de nuvem pública ou em sua infraestrutura ou nuvem privada. Essa integração também elimina a necessidade de sincronização constante do código com o repositório da Adobe e oferece a capacidade de validar solicitações de pull antes de mesclá-las em uma ramificação principal.

Consulte [Adicionar repositórios externos no Cloud Manager](/help/managing-code/external-repositories.md).

![Caixa de diálogo Adicionar repositório](/help/release-notes/assets/repositories-add-release-notes.png)

>[!NOTE]
>
>Atualmente, as verificações de qualidade do código de solicitação de pull prontas para uso são exclusivas de repositórios hospedados no GitHub, mas uma atualização para estender essa funcionalidade a outros fornecedores Git está em andamento.

Se tiver interesse em testar esse novo recurso e compartilhar o seu feedback, envie um email para [Grp-CloudManager_BYOG@adobe.com](mailto:Grp-CloudManager_BYOG@adobe.com) do seu endereço de email associado à sua Adobe ID. Inclua qual plataforma Git deseja usar e se você está em uma estrutura de repositório privado/público ou empresarial.

### Pipelines somente de preparo e somente de produção {#staging-production-only-pipelines}

A Adobe anuncia a introdução do suporte para [pipelines somente de preparo e somente de produção](/help/using/stage-prod-only.md). Esse novo recurso permite dividir os pipelines de implantação de produção de pilha completa em implantações menores e mais especializadas.

Se você quiser testar esse recurso e fornecer feedback, envie um email para [Grp-cloudmanager_splitpipelines@adobe.com](mailto:Grp-cloudmanager_splitpipelines@adobe.com) do seu endereço de email associado à sua Adobe ID.

## Correções de erros

* Um bug no AEM Cloud Manager que causava um erro &quot;403&quot; durante atualizações de status para operações de cópia de conteúdo agora é resolvido. Esse problema, atribuído a um endereço IP de entrada configurado incorretamente, impedia a propagação do status e resultava em algumas atividades de cópia de conteúdo travadas e em execução indefinidamente, exigindo cancelamento manual. A correção agora garante a geração de relatórios de status adequados e a execução mais suave de tarefas de cópia de conteúdo. <!-- (CMGR-62739) -->
* Uma atualização recente abordou um problema no SonarQube em que senhas codificadas não eram detectadas em determinados casos. A correção agora inclui uma verificação de padrão expandida e se alinha aos padrões de detecção padrão no SonarQube. <!-- CMGR-62682 -->

<!-- Known Issues {#known-issues}

* A -->
