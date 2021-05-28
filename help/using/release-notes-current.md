---
title: Notas da versão 2021.5.0
description: Siga esta página para obter informações sobre o Cloud Manager Versão 2021.5.0
feature: Informações da versão
source-git-commit: 3f17f252d89a1753c9cb121461b048f619d28415
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Notas da versão 2021.5.0 {#release-notes-for}

A seção a seguir descreve as Notas de versão gerais para [!UICONTROL Cloud Manager] Versão 2021.5.0.

>[!NOTE]
>Consulte [Notas de versão atuais](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/getting-access/release-notes-cloud-manager/release-notes-cm-current.html?lang=en#getting-access) para ver as notas de versão mais recentes do Cloud Manager no AEM como um Cloud Service.

## Data de lançamento {#release-date}

A data de lançamento da versão 2021.5.0 é 6 de maio de 2021.
[!UICONTROL Cloud Manager]
A próxima versão está planejada para 10 de junho de 2021.

## Novidades {#whats-new}

* A regra de qualidade PackageOverlaps agora detecta casos em que o mesmo pacote foi implantado várias vezes, ou seja, em vários locais incorporados, no mesmo conjunto de pacotes implantado.

* O endpoint do repositório na API pública agora inclui o URL do Git.

* No fluxo de trabalho Editar programa, o usuário só poderá definir valores KPI não decimais.

* Falhas intermitentes encontradas ao enviar o código para o Adobe Git foram resolvidas.

* A experiência Editar programa foi atualizada.

## Correções de erros {#bug-fixes}

* Em vez de remover variáveis &quot;excluídas&quot;, a API de variáveis de pipelines somente as marcaria com o status &quot;EXCLUÍDO&quot;.

* Alguns problemas de qualidade do tipo Código Smell estavam afetando incorretamente a Classificação de confiabilidade.

* Quando uma execução de pipeline era iniciada entre meia-noite e 1h UTC, a versão de artefato gerada pelo Cloud Manager não tinha garantia de ser maior do que uma versão criada no dia anterior.

* Determinados clientes do Adobe Managed Services (AMS) não conseguiram criar novos projetos no Console do desenvolvedor do Adobe I/O usando a API do Cloud Manager.
