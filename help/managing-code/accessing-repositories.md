---
title: Informações de acesso do repositório
description: Saiba como acessar e gerenciar repositórios Git gerenciados pelo Adobe usando o gerenciamento de conta Git por autoatendimento da Cloud Manager.
exl-id: 1cc88c82-67c7-4553-a1b8-d2ab22be466c
source-git-commit: 984269e5fe70913644d26e759fa21ccea0536bf4
workflow-type: tm+mt
source-wordcount: '361'
ht-degree: 31%

---

# Informações de acesso do repositório {#accessing-repos}

Saiba como acessar e gerenciar repositórios Git gerenciados pelo Adobe usando o gerenciamento de conta Git por autoatendimento no Cloud Manager.

## Acessar informações do repositório na página Visão geral {#overview-page}

1. Faça logon no Cloud Manager em [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) e selecione a organização e o programa apropriados.

1. Navegue até o cartão **Pipelines** a partir da página **Visão geral do programa**.

   ![Botão Acessar informações do repositório no cartão Ambientes](assets/pipelines-card.png)

1. Clique em **Acessar informações do repositório**. Na caixa de diálogo **Informações do Repositório para...**, você pode exibir o seguinte:

   * O nome de usuário do Git.
   * A senha do Git.
   * O URL para o repositório Git do Cloud Manager.
   * Comandos Git pré-criados para adicionar um remoto rapidamente ao repositório Git e enviar o código.

   ![Janela de informações do repositório](assets/access-repo-info.png)

1. Para acessar a senha, uma nova senha deve ser gerada. Clique em **`Generate password`**.

1. Na caixa de diálogo **Tem certeza...**, confirme a geração de senha clicando em **Gerar senha**.

   ![Confirmar geração de senha](assets/confirm-password-generation.png)

1. No campo **Senha**, a senha é gerada. Clique no ícone de copiar para a área de transferência.

   * Gerar uma senha invalida a senha anterior.
   * O Cloud Manager não salva sua senha de acesso. Certifique-se de salvar esta senha com segurança.
   * Se você perder a senha, deverá gerar uma nova.

   ![Exemplo de senha gerada](assets/generated-password.png)

Usando essas credenciais, o usuário pode clonar uma cópia local do repositório e fazer alterações nele, e quando pronto, pode confirmar qualquer alteração no repositório de códigos remotos no Cloud Manager.

>[!NOTE]
>
>* A opção **Acessar Informações do Repositório** está visível para usuários com a função de **Desenvolvedor** ou a função de **Gerente de Implantação**, ou ambas.
>* O botão **Acessar informações do repositório** exibe apenas as informações de acesso ao repositório para repositórios gerenciados pela Adobe. O acesso a informações sobre [repositórios privados](private-repositories.md) não está disponível no Cloud Manager.

## Acessar informações do repositório na janela Repositórios {#repositories-window}

O botão **Acessar Informações do Repositório** também está disponível na barra de ferramentas da janela [**Repositórios**](managing-repositories.md). Ele exibe as mesmas informações sobre o acesso a repositórios gerenciados por Adobe.

## Revogar uma senha de acesso {#revoke-password}

Você pode revogar uma senha de acesso a qualquer momento. [Crie um tíquete de suporte para essa solicitação](https://experienceleague.adobe.com/pt-br?support-solution=Experience+Manager&amp;support-tab=home#support).

O ticket é tratado com alta prioridade e normalmente é revogado dentro de um dia.
