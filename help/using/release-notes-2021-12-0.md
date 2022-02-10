---
title: Notas da versão 2021.12.0
description: Estas são as notas de versão do Cloud Manager versão 2021.12.0.
feature: Release Information
source-git-commit: 099a4490e3a8578b9f3485fd1514d1e97db977ab
workflow-type: tm+mt
source-wordcount: '265'
ht-degree: 3%

---

# Notas de versão do Cloud Manager versão 2021.12.0 {#release-notes}

A seção a seguir descreve as Notas de versão gerais de [!UICONTROL Cloud Manager] versão 2021.12.0.

>[!NOTE]
>
>Para obter as notas de versão mais recentes do Cloud Manager AEM as a Cloud Service, consulte [Cloud Manager nas notas de versão atuais AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html)

## Data de lançamento {#release-date}

A data de lançamento de [!UICONTROL Cloud Manager] a versão 2021.12.0 é 16 de dezembro de 2021. A próxima versão está planejada para janeiro de 2022.

## Novidades {#whats-new}

* O hash de confirmação, que já está visível na interface do usuário, agora também é fornecido na API.
* A página Atividade agora inclui um pop-up para a execução de pipelines que fornece um resumo dos detalhes do pipeline imediatamente.
* Foram adicionadas atualizações para incluir detalhes adicionais apresentados na página Atividades.
* A guia Aprendizagem no Cloud Manager agora inclui acesso rápido aos guias da API e aos recursos associados.
* Um usuário com a função Deployment Manager agora pode iniciar o assistente de criação de Projeto/Ramificação para um repositório sem ramificações no menu de ação na página Repositórios.
* O Gerenciador de implantação, que está no fluxo de trabalho de adicionar ou editar pipeline, agora é informado sobre como criar uma ramificação ou projeto se o repositório selecionado não tiver ramificações.
* Na janela Editar pipeline de produção, quando houver mais de um ambiente de estágio para produção, uma lista suspensa para seleção de ambiente estará disponível.
* A versão do AEM Project Archetype usada pelo Cloud Manager foi atualizada para a versão 32.

## Correções de erros {#bug-fixes}

* Os pipelines de produção de pilha completa permanecem nomeados como &quot;Pipeline de produção&quot; mesmo quando o usuário insere um nome diferente no campo de nome.
