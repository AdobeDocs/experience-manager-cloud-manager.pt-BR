---
title: Adicionar um repositório da Adobe no Cloud Manager
description: Saiba como adicionar repositórios gerenciados pela Adobe no Cloud Manager.
exl-id: 24c6ca97-ea70-41b8-b4c7-b8b0f406a57d
source-git-commit: 675568426df0df5890dd8c72bfb53c24a4c5d666
workflow-type: ht
source-wordcount: '230'
ht-degree: 100%

---

# Adicionar um repositório da Adobe no Cloud Manager {#adobe-repositories}

Saiba como adicionar um repositório gerenciado pela Adobe no Cloud Manager.

A página **Repositórios** facilita a adição de repositórios adicionais gerenciados pela Adobe a um programa selecionado.

**Para adicionar um repositório da Adobe no Cloud Manager:**

1. Faça logon no Cloud Manager em [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) e selecione a organização apropriada e o programa ao qual você deseja adicionar um repositório gerenciado pela Adobe.

1. Na página **Visão geral do programa**, no menu lateral, clique no ![ícone de Pasta](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Folder_18_N.svg) na guia **Repositórios**.

1. Na página **Repositórios**, próximo ao canto superior direito, clique em **Adicionar Repositório**.

   ![Botão Adicionar repositório](/help/managing-code/assets/repositories-tab.png)

1. Na caixa de diálogo **Adicionar repositório**, verifique se **Repositório da Adobe** está selecionado como o tipo de repositório.

1. Nos respectivos campos de texto, insira o seguinte:

   * **Nome do repositório**: um nome expressivo para o novo repositório.
   * **Visualização do URL do repositório**: não é necessário inserir um caminho de URL ou editar o caminho já existente, pois a infraestrutura do repositório já está em vigor e é totalmente integrada e gerenciada pela Adobe.
   * **Descrição (opcional)**: uma descrição detalhada do repositório.

   ![Caixa de diálogo Adicionar repositório](/help/managing-code/assets/repository-add-adobe.png)

1. Clique em **Salvar**.
O novo repositório é exibido na tabela da página **Repositórios**.

Agora você pode associar um [pipeline de CI/CD](/help/overview/ci-cd-pipelines.md) a ele ou gerenciá-lo na [**página ** Repositórios](/help/managing-code/managing-repositories.md).

>[!TIP]
>
>Também é possível adicionar repositórios GitHub que você mesmo gerencia como [repositórios privados](/help/managing-code/private-repositories.md).
