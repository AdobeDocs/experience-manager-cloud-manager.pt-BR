---
title: Informações de acesso do repositório
description: Saiba como acessar e gerenciar os repositórios Git gerenciado pela Adobe usando o gerenciamento de conta Git por autoatendimento do Cloud Manager.
exl-id: 1cc88c82-67c7-4553-a1b8-d2ab22be466c
source-git-commit: 04fbc4a3fdba8b108055d66a4fdb1a31994cb18e
workflow-type: ht
source-wordcount: '381'
ht-degree: 100%

---

# Informações de acesso do repositório {#accessing-repos}

Saiba como acessar e gerenciar o repositório Git gerenciado pela Adobe usando o gerenciamento de conta Git por autoatendimento do Cloud Manager.

## Acessar informações do repositório na página Visão geral {#overview-page}

O Cloud Manager facilita a recuperação de informações de acesso ao repositório para repositórios gerenciados pela Adobe usando **Informações de acesso ao repositório** do cartão **Pipelines**.

A caixa de diálogo **Informações do repositório** permite que você veja as seguintes informações de acesso para repositórios gerenciados pela Adobe:

* O nome de usuário do Git.
* A senha do Git.
* O URL do repositório Git do Cloud Manager.
* Comandos Git pré-construídos para adicionar rapidamente um controle remoto ao seu repositório Git e enviar código.

  ![Janela de informações do repositório](assets/repository-info.png)

O acesso a informações sobre [repositórios privados](/help/managing-code/private-repositories.md) não está disponível no Cloud Manager.

O recurso **Acessar informações do repositório** é visível para usuários com as funções de **Desenvolvedor** ou **Gerente de implantação**.

**Para acessar informações do repositório na página Visão geral:**

1. Faça logon no Cloud Manager em [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) e selecione a organização e o programa apropriados.

1. Na página **Visão geral do programa**, no cartão **Pipelines**, clique em **Acessar informações do repositório**.

   ![Acessar informações do repositório no cartão Pipelines](/help/managing-code/assets/pipelines-card2.png)

1. Para acessar a senha, uma nova senha deve ser gerada. Na caixa de diálogo **Informações do repositório**, selecione **Gerar senha**.

1. Na caixa de diálogo de confirmação, selecione **Gerar senha**.

1. À direita do campo **Senha**, clique no ![Ícone de Copiar](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Copy_18_N.svg) para copiar a senha para a área de transferência.

   * Gerar uma senha invalidará a senha anterior.
   * O Cloud Manager não salva a senha. É sua responsabilidade guardar esta senha com segurança.
   * Como o Cloud Manager não salva a senha, se você a perder, deverá gerar uma nova.

   ![Copiar senha na caixa de diálogo Informações do repositório](/help/managing-code/assets/repository-copy-password.png)

Usando essas credenciais, é possível clonar uma cópia local do repositório e fazer alterações nele, e quando pronto, pode confirmar qualquer alteração no repositório de códigos remotos no Cloud Manager.

## Acesso a informações do repositório na janela Repositórios {#repositories-window}

O recurso **Acessar informações do repositório** também está disponível na página [**Repositórios**](/help/managing-code/managing-repositories.md). Ele exibe as mesmas informações sobre o acesso a repositórios gerenciados pela Adobe.

## Revogação de uma senha de acesso {#revoke-password}

É possível revogar uma senha de acesso a qualquer momento. 

Para fazer isso, [crie um tíquete de suporte para esta solicitação](https://experienceleague.adobe.com/pt-br?support-solution=Experience+Manager&amp;support-tab=home#support). O tíquete será tratado com alta prioridade e deverá ser revogado em um dia.
