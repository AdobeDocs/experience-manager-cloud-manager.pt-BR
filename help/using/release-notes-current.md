---
title: Notas da versão 2021.7.0
description: Siga esta página para obter informações sobre o Cloud Manager Versão 2021.7.0
feature: Informações da versão
source-git-commit: ee701dd2d0c3921455a0960cbb6ca9a3ec4793e7
workflow-type: tm+mt
source-wordcount: '243'
ht-degree: 6%

---

# Notas da versão 2021.7.0 {#release-notes-for}

A seção a seguir descreve as Notas de versão gerais para [!UICONTROL Cloud Manager] Versão 2021.7.0.

>[!NOTE]
>Consulte [Notas de versão atuais](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/getting-access/release-notes-cloud-manager/release-notes-cm-current.html?lang=en#getting-access) para ver as notas de versão mais recentes do Cloud Manager no AEM como um Cloud Service.

## Data de lançamento {#release-date}

A data de lançamento da versão 2021.7.0 é 15 de julho de 2021.
[!UICONTROL Cloud Manager]
A próxima versão está planejada para 12 de agosto de 2021.

## Novidades {#whats-new}

* Os clientes agora podem usar os JDKs do Azul 8 e 11 para seus processos de build do Cloud Manager e podem optar por usar um desses JDKs para plug-ins Maven compatíveis com cadeias de ferramentas *ou* em toda a execução do processo Maven.

* O IP de saída agora será registrado no arquivo de log da etapa de compilação.

* Os botões Gerenciar Git foram intitulados Informações do Git de Acesso e a caixa de diálogo foi atualizada visualmente.

* Algumas reconfigurações de topologia inesperadas podem resultar em relatórios de teste detalhados não mais serem disponibilizados na página de detalhes de execução do pipeline.

## Correções de erros {#bug-fixes}

* Navegar manualmente para a página de detalhes da execução de uma execução não existente não exibia um erro, apenas uma tela de carregamento infinita.

* Em alguns casos, a tentativa automática para contêineres com falha usados no desempenho do Sites não entraria em vigor por 2 horas, resultando em uma falha de teste.

## Problemas conhecidos {#known-issues}

Os clientes que alternam para usar os JDKs do Azul devem estar cientes de que nem todos os aplicativos existentes serão compilados sem erro no JDK do Azul. É altamente recomendável testar localmente antes de trocar.