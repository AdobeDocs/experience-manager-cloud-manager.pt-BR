---
title: Notas da versão 2021.11.0
description: Siga esta página para obter informações sobre o Cloud Manager Versão 2021.11.0
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: 6852df51d4b9b4947f1d5ce0b5a284bef94d0589
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 3%

---

# Notas da versão 2021.11.0 {#release-notes-for}

A seção a seguir descreve as Notas de versão gerais de [!UICONTROL Cloud Manager] Versão 2021.11.0.

>[!NOTE]
>Consulte [Notas de versão atuais](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/getting-access/release-notes-cloud-manager/release-notes-cm-current.html?lang=en#getting-access) para ver as notas de versão mais recentes do Cloud Manager AEM as a Cloud Service.

## Data de lançamento {#release-date}

A data de lançamento para [!UICONTROL Cloud Manager] A versão 2021.11.0 é 4 de novembro de 2021.
A próxima versão está planejada para 16 de dezembro de 2021.

## Novidades {#whats-new}

* A ID de confirmação de Git agora será exibida nos detalhes de execução do pipeline, facilitando o rastreamento do código que foi criado.

* O `x-request-id` o cabeçalho de resposta agora está visível no Reprodução da API em [www.adobe.io](https://www.adobe.io/). Esse cabeçalho é útil ao enviar problemas de atendimento ao cliente para solução de problemas.

* Como usuário, vejo que o pipeline card com zero pipelines me fornece a orientação apropriada.

* Uma nova Página de atividade agora está disponível, onde atividades como pipeline e execuções de código podem ser visualizadas junto com seus detalhes associados. Com o tempo, as atividades listadas nesta página se expanderão no escopo junto com os detalhes fornecidos.

* Uma nova página Pipelines com uma oferta de status on-hover para facilitar a visualização do resumo dos detalhes está disponível. As execuções de pipeline podem ser visualizadas junto com seus detalhes associados.

* A API Editar pipeline agora oferece suporte à configuração da invalidação do dispatcher e aos caminhos de liberação.

* A API Editar pipeline agora oferece suporte à alteração do ambiente usado nas fases de implantação.

* Uma otimização no processo de varredura do OakPal foi introduzida para pacotes grandes.

* O arquivo CSV do problema de qualidade agora contém o carimbo de data e hora de cada problema de qualidade.

* O botão Gerenciar na página Ambientes não estará mais visível na interface do usuário.

## Correções de erros {#bug-fixes}

* Certas configurações de build não ortodoxas resultaram no armazenamento de arquivos desnecessários no cache de artefatos Maven do pipeline que resultaram em I/O de rede irrelevante ao iniciar e parar o contêiner de compilação.

* A API do PATCH de pipeline falha se a fase de implantação não existir.

* O `ClientlibProxyResourceCheck` a regra de qualidade gerava problemas de falso positivo quando havia bibliotecas de clientes com caminhos de base comuns.

* Mensagem de erro quando o número máximo de repositórios foi atingido não especificou o motivo do erro.

* Em casos raros, os pipelines estavam falhando devido ao tratamento inadequado de tentativas de determinados códigos de resposta.
