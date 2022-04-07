---
title: Notas da versão 2022.3.0
description: Estas são as notas de versão do Cloud Manager versão 2022.3.0.
feature: Release Information
source-git-commit: f1d359921a11ab8a6117a15cd5eb72362bbb8360
workflow-type: tm+mt
source-wordcount: '210'
ht-degree: 4%

---


# Notas de versão do Cloud Manager versão 2022.3.0 {#release-notes}

Esta página documenta as notas de versão do [!UICONTROL Cloud Manager] versão 2022.3.0.

>[!NOTE]
>
>Para obter as notas de versão mais recentes do Cloud Manager AEM as a Cloud Service, consulte [Cloud Manager nas notas de versão atuais AEM as a Cloud Service.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html)

## Data de lançamento {#release-date}

A data de lançamento de [!UICONTROL Cloud Manager] a versão 2022.3.0 é 10 de março de 2022. A próxima versão está planejada para 7 de abril de 2022.

## Novidades {#what-is-new}

* As solicitações HTTP de saída dos testes de ativos agora vêm de um intervalo IP fixo.


## Correções de erros {#bug-fixes}

* O **Ignorar alterações no Balanceador de Carga** não foi possível desabilitar a opção.
* O **Ignorar alterações no Balanceador de Carga** não foi exibida na Implantação de desenvolvedores do AMS **Editar fluxo de trabalho do pipeline**.
* Um subconjunto de repositórios git criados manualmente tinha um valor de nome incorreto que impedia a efetivação do recurso de reuso de artefato de compilação. Os nomes desses repositórios foram alterados e os usuários verão o nome corrigido na API/interface do usuário do Cloud Manager.
* Os artefatos de construção provenientes de gasodutos que não são de produção foram reutilizados de forma imprópria em gasodutos de produção em pilha completa.
* Ao adicionar ou editar um pipeline de qualidade de código, as opções para lidar com falhas de métrica não são mais exibidas.
* Algumas configurações inesperadas de variável de pipeline podem causar na etapa de build.
