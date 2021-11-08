---
title: Notas da versão 2021.10.0
description: Siga esta página para obter informações sobre o Cloud Manager Versão 2021.10.0
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: e89420ef9e5621cb10ef80715e96fd25e486c9bd
workflow-type: tm+mt
source-wordcount: '358'
ht-degree: 3%

---

# Notas da versão 2021.10.0 {#release-notes-for}

A seção a seguir descreve as Notas de versão gerais de [!UICONTROL Cloud Manager] Versão 2021.10.0.

>[!NOTE]
>Consulte [Notas de versão atuais](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/getting-access/release-notes-cloud-manager/release-notes-cm-current.html?lang=en#getting-access) para ver as notas de versão mais recentes do Cloud Manager AEM as a Cloud Service.

## Data de lançamento {#release-date}

A data de lançamento para [!UICONTROL Cloud Manager] A versão 2021.10.0 é 14 de outubro de 2021.

## Novidades {#whats-new}

* Os pipelines de produção agora podem ser executados em modo de &quot;emergência&quot;, ignorando as etapas de teste de segurança e desempenho para implantações de emergência.

* Para fins de consistência com o Cloud Service, os pipelines de implantação existentes agora serão referenciados e rotulados na interface do usuário como pipelines &quot;Full Stack&quot;.

* O cartão de pipeline foi atualizado para exibir agora uma única face integrada que mostra os pipelines de produção e não de produção, e o usuário pode selecionar Executar/Pausar/Retomar diretamente do menu de ação associado a cada pipeline.

* Um usuário na função Gerenciador de implantação agora pode excluir o pipeline de Produção de maneira automatizada por meio da interface do usuário.

* Adicionar e editar experiências de pipeline foi atualizado para agora usar modais modernos e familiares.

* Os usuários do Cloud Manager agora podem enviar feedback diretamente da interface do usuário por meio do **Feedback** na parte superior direita da landing page.

* Os gráficos de SLA anuais agora podem ser baixados na interface do usuário do Cloud Manager.

* As execuções de pipeline de não produção e qualidade de código agora usam um processo de clonagem superficial mais eficiente durante a etapa de compilação, resultando em um tempo de compilação mais rápido para clientes com repositórios Git especialmente grandes.

* A documentação da API do Cloud Manager agora inclui um playground interativo que permite que os usuários conectados façam experiências com a API a partir de seu navegador. Consulte [Reprodução da API do Cloud Manager](https://www.adobe.io/experience-cloud/cloud-manager/reference/playground/) para obter mais detalhes.

* A dica de ferramenta no cartão Programa será mais descritiva se uma opção de seleção em &quot;Navegar para&quot; estiver desativada. Agora, ele dirá: &quot;Um ambiente de produção não existe.&quot;


## Correções de erros {#bug-fixes}

* Quando os dados lidos de sistemas internos não eram inseridos corretamente, os dados não relacionados fornecidos por CSEs não eram refletidos corretamente no Cloud Manager.

* Em situações específicas do cliente, artefatos inválidos baixados durante a etapa de build que deveriam ter causado uma falha de build estavam sendo ignorados.
