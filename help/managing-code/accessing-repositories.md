---
title: Informações de acesso do repositório
description: Saiba como acessar e gerenciar o repositório Git gerenciado pela Adobe usando o gerenciamento de conta Git por autoatendimento do Cloud Manager.
exl-id: 1cc88c82-67c7-4553-a1b8-d2ab22be466c
source-git-commit: e93285f7c7495ec9d2f11d289adaf6aaba7e58ea
workflow-type: tm+mt
source-wordcount: '400'
ht-degree: 100%

---

# Informações de acesso do repositório  {#accessing-repos}

Saiba como acessar e gerenciar o repositório Git gerenciado pela Adobe usando o gerenciamento de conta Git por autoatendimento do Cloud Manager.

## Acessar informações do repositório na página Visão geral {#overview-page}

O Cloud Manager facilita a recuperação de informações de acesso ao repositório para repositórios gerenciados pela Adobe usando o botão **Acessar informações do repositório** disponível em destaque no cartão do pipeline.

1. Faça logon no Cloud Manager em [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) e selecione a organização e o programa apropriados.

1. Navegue até o cartão **Pipelines** na página **Visão geral do programa**.

   ![Botão Acessar informações do repositório no cartão Ambientes](assets/pipelines-card.png)

1. Toque ou clique no botão **Acessar informações do repositório** para abrir a caixa de diálogo **Informações do repositório** e visualizar:

   * O nome de usuário do Git.
   * A senha do git.
   * A URL do repositório Git do Cloud Manager.
   * Comandos git pré-construídos para adicionar rapidamente um controle remoto ao seu repositório git e enviar código.

   ![Janela de informações do repositório](assets/access-repo-info.png)

1. Para acessar a senha, uma nova senha deve ser gerada. Para fazer isso, toque ou clique no botão **Gerar senha**.

1. Confirme a geração da senha na caixa de diálogo **Tem certeza...** tocando ou clicando em **Gerar senha**.

   ![Confirmar geração de senha](assets/confirm-password-generation.png)

1. A senha é gerada e fica visível para cópia no campo **Senha**.

   * Gerar uma senha invalidará a senha anterior.
   * O Cloud Manager não salvará a senha. É sua responsabilidade guardar esta senha com segurança.
   * Como o Cloud Manager não salva a senha, se você a perder, deverá gerar uma nova senha.

   ![Exemplo de senha gerada](assets/generated-password.png)

Usando essas credenciais, o usuário pode clonar uma cópia local do repositório e fazer alterações nele, e quando pronto, pode confirmar qualquer alteração no repositório de códigos remotos no Cloud Manager.

>[!NOTE]
>
>* A opção **Acessar informações do repositório** está visível para usuários com funções de **Desenvolvedor** ou **Gerente de implantação**.
>* O botão **Acessar informações do repositório** exibe apenas as informações de acesso ao repositório para repositórios gerenciados pela Adobe. O acesso a informações sobre [repositórios privados](private-repositories.md) não está disponível no Cloud Manager.

## Acesso a informações do repositório na janela Repositórios {#repositories-window}

Um botão **Acessar informações do repositório** também está disponível na barra de ferramentas da janela [**Repositórios**.O ](managing-repositories.md) exibe as mesmas informações sobre o acesso a repositórios gerenciados pela Adobe.

## Revogação de uma senha de acesso {#revoke-password}

Você pode revogar uma senha de acesso a qualquer momento. Para fazer isso, [crie um tíquete de suporte para esta solicitação.](https://experienceleague.adobe.com/pt-br?support-solution=Experience+Manager&amp;support-tab=home#support)

O tíquete será tratado com alta prioridade e deverá ser revogado dentro de um dia.
