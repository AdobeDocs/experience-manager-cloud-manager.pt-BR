---
title: Suporte ao submódulo Git
description: Aprenda como você pode usar submódulos Git para mesclar o conteúdo de várias ramificações em repositórios Git no momento da criação.
exl-id: f946d7e7-114a-4e33-bb82-2625d37bba2f
source-git-commit: 200366e5db92b7ffc79b7a47ce8e7825b29b7969
workflow-type: tm+mt
source-wordcount: '419'
ht-degree: 97%

---

# Suporte ao submódulo Git para repositórios da Adobe {#git-submodule-support}

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

## Limitações           {#limitations}

Ao usar submódulos do Git, esteja ciente do seguinte:

* O URL do Git deve seguir exatamente a sintaxe descrita acima.
* Por motivos de segurança, não incorpore credenciais nesses URLs.
* Somente os submódulos na raiz da ramificação são permitidos.
* As referências de submódulos Git são armazenadas para confirmações do Git específicas.
   * Como resultado, quando alterações no repositório do submódulo são feitas, a confirmação referenciada precisa ser atualizada, por exemplo, usando `git submodule update --remote`.
* A menos que seja necessário, é altamente recomendável usar submódulos “superficiais”.
   * Para fazer isso, execute `git config -f .gitmodules submodule.<submodule path>.shallow true` para cada submódulo.


## Suporte ao submódulo Git para repositórios privados {#private-repositories}

O suporte para submódulos git ao usar [repositórios privados](private-repositories.md) é basicamente o mesmo que usar repositórios da Adobe.

No entanto, após configurar o arquivo `pom.xml` e executar os comandos `git submodule`, é necessário adicionar um arquivo `.gitmodules` no diretório raiz do repositório agregador do Cloud Manager para detectar a configuração do submódulo.

![arquivo .gitmodules](assets/gitmodules.png)

![Agregador](assets/aggregator.png)

### Limitações e recomendações {#limitations-recommendations-private-repos}

Ao usar submódulos git com repositórios privados, esteja ciente das limitações a seguir.

* Os URLs do git para os submódulos podem estar no formato HTTPS ou SSH, mas devem estar vinculados a um repositório github.com
   * Adicionar um submódulo de repositório da Adobe a um repositório agregador do GitHub ou vice-versa não funcionará.
* Os submódulos do GitHub devem estar acessíveis ao aplicativo Adobe GitHub.
* [As limitações do uso de submódulos git com repositórios gerenciados pela Adobe](#limitations-recommendations) também se aplicam.
