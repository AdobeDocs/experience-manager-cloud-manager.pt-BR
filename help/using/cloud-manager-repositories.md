---
title: Repositórios do Cloud Manager
description: Repositórios do Cloud Manager
exl-id: 384b197d-f7a7-4022-9b16-9d83ab788966
source-git-commit: 280d760766cf445e609b865f827c01b4ab1db69c
workflow-type: tm+mt
source-wordcount: '443'
ht-degree: 0%

---

# Repositórios do Cloud Manager {#cloud-manager-repos}

Os repositórios criados e disponíveis no Cloud Manager podem ser visualizados e gerenciados por meio da página Repositórios .

## Adicionar e gerenciar repositórios {#add-manage-repos}

Siga as etapas abaixo para visualizar e gerenciar repositórios no Cloud Manager:

1. No **Visão geral do programa** clique em **Repositórios** e navegue até a guia **Repositórios** página.

1. Clique em **Adicionar Repositório** para iniciar o assistente.

   >[!NOTE]
   >Um usuário na função Deployment Manager ou Business Owner deve estar conectado para poder adicionar um repositório.

   ![](assets/create-repo2.png)


1. Insira o nome e a descrição conforme solicitado e clique em **Salvar**.

   ![](assets/repo-1.png)

1. Selecione **Salvar**. O acordo de recompra recém-criado será exibido na tabela, conforme mostrado abaixo.

   ![](assets/create-repo3.png)

   >[!NOTE]
   >Os repositórios criados no Cloud Manager também estarão disponíveis para você selecionar durante as etapas de adição ou edição do pipeline.

1. Você pode selecionar o repositório e clicar nas opções de menu na extremidade direita da tabela para **Copiar URL do repositório**, **Exibir e atualizar** ou **Excluir** seu repositório, conforme mostrado na figura abaixo.

   ![](assets/create-repo3.png)



## Suporte ao Submódulo Git {#git-submodule-support}

Os submódulos Git podem ser usados para mesclar o conteúdo de várias ramificações entre repositórios Git no momento da criação. Quando o processo de build do Cloud Manager é executado, depois que o repositório configurado para o pipeline é clonado e a ramificação configurada é desmarcada, se a ramificação contiver um `.gitmodules` no diretório raiz, o comando é executado.

```
$ git submodule update --init
```

Isso verificará cada submódulo no diretório apropriado. Essa técnica é uma alternativa potencial para [trabalhar com vários repositórios Git de origem](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/managing-code/working-with-multiple-source-git-repos.html) para organizações confortáveis com o uso de submódulos git e que não desejam gerenciar um processo de mesclagem externo.

Por exemplo, digamos que existam três repositórios, cada um contendo uma única ramificação chamada main . No repositório &quot;primário&quot;, ou seja, o configurado nos pipelines, a ramificação principal tem um arquivo pom.xml declarando os projetos contidos nos outros dois repositórios:

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

```
$ git submodule add -b main https://git.cloudmanager.adobe.com/ProgramName/projectA/ project-a
$ git submodule add -b main https://git.cloudmanager.adobe.com/ProgramName/projectB/ project-b
```

Isso resulta em uma `.gitmodules` arquivo com esta aparência:

```
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

Ao usar submódulos git, lembre-se dos seguintes itens:

* O URL do Git deve estar exatamente na sintaxe descrita acima. Por motivos de segurança, não incorpore credenciais nesses URLs.
* Somente os submódulos na raiz da ramificação são suportados.
* As referências de submódulos Git são armazenadas para confirmações Git específicas. Como resultado, quando alterações no repositório do submódulo são feitas, a confirmação referenciada precisa ser atualizada, por exemplo, usando `git submodule update --remote`.
* A menos que seja necessário, é altamente recomendável usar submódulos &quot;superficiais&quot;. Para fazer isso, execute `git config -f .gitmodules submodule.<submodule path>.shallow true` para cada submódulo.
