---
title: Repositórios do Cloud Manager
description: Saiba como acessar, criar e editar repositórios para seus programas do Cloud Manager.
exl-id: 384b197d-f7a7-4022-9b16-9d83ab788966
source-git-commit: 1d4ab9704fdb743b097e24be335fbf069d1e78bd
workflow-type: tm+mt
source-wordcount: '762'
ht-degree: 98%

---


# Repositórios do Cloud Manager {#cloud-manager-repos}

Os repositórios são onde você gerencia seu código usando o Git. Saiba como criar repositórios para seus programas do Cloud Manager.

## Acesso a repositórios {#accessing-repos}

Você pode acessar e gerenciar os repositórios Git no autoatendimento do Cloud Manager.

Para acessar seu repositório, use o botão **Acessar informações do repositório** disponível no Cloud Manager, com maior destaque no cartão de pipeline.

1. Faça logon no Cloud Manager em [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com) e selecione a organização e o programa apropriados.

1. Navegue até o cartão **Pipelines** a partir da página **Visão geral do programa** e você verá a opção **Acessar informações do repositório**, que permite acessar e gerenciar o repositório Git [configurado com este pipeline.](/help/using/production-pipelines.md)

   ![Botão Acessar informações do repositório](/help/assets/access-repo1.png)

1. Toque ou clique no **Acessar informações do repositório** botão para abrir uma caixa de diálogo que apresenta:

   * O URL para o repositório Git
   * Nome de usuário
   * Senha
   * Comando do Git para executar e clonar o repositório localmente

   ![Caixa de diálogo Informações do repositório](/help/assets/access-repo-create.png)

Use as informações fornecidas para clonar o repositório localmente, para que você possa iniciar o desenvolvimento local.

>[!NOTE]
>
>A opção **Acessar informações do repositório** está visível para os usuários nas funções de **Desenvolvedor** ou de **Gerente de implantação**.

## Adicionar repositórios {#add-repos}

Siga estas etapas para adicionar repositórios no Cloud Manager:

1. Faça logon no Cloud Manager em [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com) e selecione a organização e o programa apropriados.

1. Na página de **Visão geral do programa**, clique na guia **Repositórios** e navegue até a página **Repositórios**.

1. Clique em **Adicionar repositório** para iniciar o assistente.

   >[!NOTE]
   >
   >Você deve ter as funções de **Gerente de implantação** ou **Proprietário da empresa** para adicionar um repositório.

   ![Adicionar repositório](/help/assets/create-repo2.png)

1. Insira o nome e a descrição conforme solicitado e clique em **Salvar**.

   ![Detalhes do repositório](/help/assets/repo-1.png)

1. Selecione **Salvar**.

Seu repositório recém-criado será exibido.

Os repositórios criados no Cloud Manager estão disponíveis para você selecionar quando [criar seus pipelines.](/help/overview/ci-cd-pipelines.md)

## Visualizar e editar repositórios {#edit-repos}

Siga estas etapas para editar e visualizar repositórios no Cloud Manager:

1. Faça logon no Cloud Manager em [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com) e selecione a organização e o programa apropriados.

1. Na página **Visão geral do programa**, clique na guia **Repositórios** e navegue até a página **Repositórios**. Aqui é possível visualizar os detalhes dos repositórios existentes.

1. Selecione o repositório e clique no botão de reticências na extremidade direita da tabela para **Copiar o URL do repositório** ou **Exibir e atualizar** o repositório.

![Editar repositório](/help/assets/create-repo3.png)

## Excluindo Repositórios {#delete-repos}

Para excluir um repositório, siga as mesmas etapas [para exibir e editar repositórios](#edit-repos), mas na página **Repositórios** selecione **Excluir** no botão de reticências do repositório a ser excluído.

Observe que, quando um repositório é excluído no Cloud Manager, ele é marcado como excluído e não é mais acessível ao usuário, mas é mantido no sistema para fins de recuperação.

Se tentar criar um novo repositório depois de excluir um repositório com o mesmo nome, você receberá a mensagem de erro &quot;Ocorreu um erro ao tentar criar o repositório. Entre em contato com o Suporte CSE ou da Adobe.&quot;

Se você receber esta mensagem de erro, entre em contato com o Suporte da Adobe para que o suporte possa ajudar a renomear o repositório excluído ou escolher um nome diferente para seu novo repositório.

## Suporte a submódulos Git {#git-submodule-support}

Os submódulos Git podem ser usados para mesclar o conteúdo de várias ramificações entre repositórios Git no momento da compilação.

Quando o processo de criação do Cloud Manager é executado, depois que o repositório configurado para o pipeline é clonado e a ramificação configurada é verificada, se a ramificação contiver um arquivo `.gitmodules` no diretório raiz, o comando é executado.

```
$ git submodule update --init
```

Isso verifica cada submódulo no diretório apropriado. Essa técnica é uma alternativa potencial para [trabalhar com vários repositórios Git de origem](/help/managing-code/multiple-git-repos.md) em organizações que estão acostumadas com o uso de submódulos do Git e que não desejam gerenciar um processo de mesclagem externo.

Por exemplo, digamos que existam três repositórios, cada um contendo uma única ramificação chamada `main`. No repositório “primário”, ou seja, aquele configurado nos pipelines, a ramificação `main` tem um arquivo `pom.xml` que declara os projetos contidos nos outros dois repositórios:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/maven-v4_0_0.xsd">
    <modelVersion>4.0.0</modelVersion>
   
    <groupId>customer.group.id</groupId>
    <artifactId>customer-reactor</artifactId>
    <version>0.0.1-SNAPSHOT</version>
    <packaging>pom</packaging>
   
    <modules>
        <module>project-a</module>
        <module>project-b</module>
    </modules>
   
</project>
```

Em seguida, você adicionaria submódulos para os outros dois repositórios:

```shell
$ git submodule add -b main https://git.cloudmanager.adobe.com/ProgramName/projectA/ project-a
$ git submodule add -b main https://git.cloudmanager.adobe.com/ProgramName/projectB/ project-b
```

Isso resulta em um arquivo `.gitmodules` com esta aparência:

```text
[submodule "project-a"]
    path = project-a
    url = https://git.cloudmanager.adobe.com/ProgramName/projectA/
    branch = main
[submodule "project-b"]
    path = project-b
    url = https://git.cloudmanager.adobe.com/ProgramName/projectB/
    branch = main
```

Mais informações sobre os submódulos do Git podem ser encontradas na seção [Manual de referência do Git](https://git-scm.com/book/en/v2/Git-Tools-Submodules).

### Limitações           {#limitations}

Ao usar submódulos do Git, esteja ciente de:

* O URL do Git deve seguir exatamente a sintaxe descrita acima.
* Por motivos de segurança, não incorpore credenciais nesses URLs.
* Somente os submódulos na raiz da ramificação são permitidos.
* As referências de submódulos Git são armazenadas para confirmações do Git específicas.
   * Como resultado, quando alterações no repositório do submódulo são feitas, a confirmação referenciada precisa ser atualizada, por exemplo, usando `git submodule update --remote`.
* A menos que seja necessário, é altamente recomendável usar submódulos “superficiais”.
   * Para fazer isso, execute `git config -f .gitmodules submodule.<submodule path>.shallow true` para cada submódulo.
