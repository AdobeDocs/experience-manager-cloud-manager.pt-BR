---
title: Repositórios do Cloud Manager
description: Saiba como acessar, criar e editar repositórios para seus programas do Cloud Manager.
exl-id: 384b197d-f7a7-4022-9b16-9d83ab788966
source-git-commit: 6572c16aea2c5d2d1032ca5b0f5d75ade65c3a19
workflow-type: tm+mt
source-wordcount: '666'
ht-degree: 2%

---


# Repositórios do Cloud Manager {#cloud-manager-repos}

Os repositórios são onde você gerencia seu código usando o git. Saiba como criar repositórios para seus programas do Cloud Manager.

## Acesso a repositórios {#accessing-repos}

Você pode acessar e gerenciar os repositórios git em um autoatendimento do Cloud Manager.

Para acessar seu repositório, use o **Acessar informações do repositório** disponível no Cloud Manager, mais proeminentemente no cartão de pipeline.

1. Faça logon no Cloud Manager em [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com) e selecione a organização e o programa apropriados.

1. Navegar para **Pipelines** do cartão **Visão geral do programa** e você verá a variável **Acessar informações do repositório** opção para acessar e gerenciar o repositório git [configurado com este pipeline.](/help/using/production-pipelines.md)

   ![Botão Acessar informações do repositório](/help/assets/access-repo1.png)

1. Se você alternar para a variável **Não produção** guia pipeline , a variável **Acessar informações do repositório** também está disponível lá como [configurado para o pipeline.](/help/using/non-production-pipelines.md)

   ![Gasodutos de não produção](/help/assets/access-repo-nonprod.png)

1. Clique no botão **Acessar informações do repositório** para abrir uma caixa de diálogo que apresenta:

   * O URL para o repositório Git
   * Nome de usuário
   * Senha
   * Comando Git para executar para clonar o repositório localmente

   ![Caixa de diálogo Informações do repositório](/help/assets/access-repo-create.png)

Use as informações fornecidas para clonar o repositório localmente, para que você possa iniciar o desenvolvimento local.

>[!NOTE]
>
>O **Acessar informações do repositório** está visível para os usuários no **Desenvolvedor** ou **Gerenciador de implantação** função.

## Adicionar repositórios {#add-repos}

Siga estas etapas para adicionar repositórios no Cloud Manager:

1. Faça logon no Cloud Manager em [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com) e selecione a organização e o programa apropriados.

1. No **Visão geral do programa** clique em **Repositórios** e navegue até a guia **Repositórios** página.

1. Clique em **Adicionar Repositório** para iniciar o assistente.

   >[!NOTE]
   >
   >Você deve ter o **Gerenciador de implantação** ou **Proprietário da empresa** para adicionar um repositório.

   ![Adicionar repositório](/help/assets/create-repo2.png)

1. Insira o nome e a descrição conforme solicitado e clique em **Salvar**.

   ![Detalhes do acordo de recompra](/help/assets/repo-1.png)

1. Selecione **Salvar**.

Seu acordo de recompra recém-criado será exibido.

![Novo acordo de recompra criado](/help/assets/create-repo3.png)

Os repositórios criados no Cloud Manager estão disponíveis para você selecionar quando [crie seus pipelines.](/help/overview/ci-cd-pipelines.md)

## Exibir e editar repositórios {#edit-repos}

Siga estas etapas para editar e exibir repositórios no Cloud Manager:

1. Faça logon no Cloud Manager em [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com) e selecione a organização e o programa apropriados.

1. No **Visão geral do programa** clique em **Repositórios** e navegue até a guia **Repositórios** página. Aqui você pode visualizar os detalhes dos repositórios existentes.

1. Selecione o repositório e clique no botão de reticências na extremidade direita da tabela para **Copiar URL do repositório**, **Exibir e atualizar** ou **Excluir** seu repositório.

![Editar repositório](/help/assets/create-repo3.png)

## Suporte ao Submódulo Git {#git-submodule-support}

Os submódulos Git podem ser usados para mesclar o conteúdo de várias ramificações entre repositórios Git no momento da criação.

Quando o processo de build do Cloud Manager é executado, depois que o repositório configurado para o pipeline é clonado e a ramificação configurada é desmarcada, se a ramificação contiver um `.gitmodules` no diretório raiz, o comando é executado.

```
$ git submodule update --init
```

Isso verificará cada submódulo no diretório apropriado. Essa técnica é uma alternativa potencial para [trabalhar com vários repositórios Git de origem](/help/managing-code/multiple-git-repos.md) para organizações confortáveis com o uso de submódulos git e que não desejam gerenciar um processo de mesclagem externo.

Por exemplo, digamos que existam três repositórios, cada um contendo uma única ramificação chamada `main`. No repositório &quot;primário&quot;, ou seja, aquele configurado nos pipelines, a variável `main` ramificação `pom.xml` arquivo que declara os projetos contidos nos outros dois repositórios:

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

Isso resulta em uma `.gitmodules` arquivo com esta aparência:

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

Mais informações sobre os submódulos git podem ser encontradas na seção [Manual de referência do Git](https://git-scm.com/book/en/v2/Git-Tools-Submodules).

### Limitações           {#limitations}

Ao usar submódulos git, esteja ciente de:

* O URL do git deve estar exatamente na sintaxe descrita acima.
* Por motivos de segurança, não incorpore credenciais nesses URLs.
* Somente os submódulos na raiz da ramificação são suportados.
* As referências de submódulos Git são armazenadas para confirmações Git específicas.
   * Como resultado, quando alterações no repositório do submódulo são feitas, a confirmação referenciada precisa ser atualizada, por exemplo, usando `git submodule update --remote`.
* A menos que seja necessário, é altamente recomendável usar submódulos &quot;superficiais&quot;.
   * Para fazer isso, execute `git config -f .gitmodules submodule.<submodule path>.shallow true` para cada submódulo.
