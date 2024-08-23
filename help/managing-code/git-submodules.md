---
title: Suporte ao submódulo Git
description: Saiba como você pode usar os submódulos do Git para mesclar o conteúdo de várias ramificações entre repositórios Git no momento da criação.
exl-id: f946d7e7-114a-4e33-bb82-2625d37bba2f
source-git-commit: 984269e5fe70913644d26e759fa21ccea0536bf4
workflow-type: tm+mt
source-wordcount: '412'
ht-degree: 20%

---

# Suporte a submódulo Git para repositórios Adobe {#git-submodule-support}

Os submódulos Git podem ser usados para mesclar o conteúdo de várias ramificações entre repositórios Git no momento da compilação.

Quando o processo de criação do Cloud Manager é executado, ele primeiro clona o repositório do pipeline e verifica a ramificação configurada. Se a ramificação contiver um arquivo `.gitmodules` no diretório raiz, o comando será executado.

```
$ git submodule update --init
```

Esse processo verifica cada submódulo no diretório apropriado. Esta técnica é uma possível alternativa para [trabalhar com vários repositórios Git de origem](/help/managing-code/multiple-git-repos.md) em organizações familiarizadas com o uso de submódulos Git e que não desejam gerenciar um processo de mesclagem externo.

Por exemplo, digamos que existam três repositórios, cada um contendo uma única ramificação chamada `main`. No repositório &quot;primário&quot;, ou seja, aquele configurado nos pipelines, a ramificação `main` tem um arquivo `pom.xml` que declara os projetos contidos nos outros dois repositórios:

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

Em seguida, você adiciona submódulos para os outros dois repositórios:

```shell
$ git submodule add -b main https://git.cloudmanager.adobe.com/ProgramName/projectA/ project-a
$ git submodule add -b main https://git.cloudmanager.adobe.com/ProgramName/projectB/ project-b
```

Os resultados no arquivo `.gitmodules` são parecidos com os seguintes:

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

Consulte o [Manual de referência do Git](https://git-scm.com/book/en/v2/Git-Tools-Submodules) para obter mais informações sobre os submódulos do Git.

## Limitações {#limitations}

Ao usar submódulos Git, esteja ciente do seguinte:

* A URL do Git deve seguir exatamente a sintaxe descrita acima.
* Por motivos de segurança, não incorpore credenciais nesses URLs.
* Somente os submódulos na raiz da ramificação são permitidos.
* As referências do submódulo Git são armazenadas em confirmações Git específicas. Como resultado, quando alterações no repositório do submódulo são feitas, a confirmação referenciada precisa ser atualizada. Por exemplo, usando `git submodule update --remote`.
* A menos que seja necessário, o Adobe recomenda que você use submódulos &quot;superficiais&quot; executando `git config -f .gitmodules submodule.<submodule path>.shallow true` para cada submódulo.


## Suporte a submódulos Git para repositórios privados {#private-repositories}

O suporte para submódulos Git ao usar [repositórios privados](private-repositories.md) é basicamente o mesmo que ao usar repositórios Adobe.

No entanto, após configurar o arquivo `pom.xml` e executar os comandos `git submodule`, é necessário adicionar um arquivo `.gitmodules` no diretório raiz do repositório agregador do Cloud Manager para detectar a configuração do submódulo.

![arquivo .gitmodules](assets/gitmodules.png)

![Agregador](assets/aggregator.png)

### Limitações e recomendações {#limitations-recommendations-private-repos}

Ao usar submódulos do Git com repositórios privados, esteja ciente das limitações a seguir.

* Os URLs Git dos submódulos podem estar no formato HTTPS ou SSH, mas devem estar vinculados a um repositório Github.com. A adição de um submódulo do repositório de Adobe a um repositório agregador GitHub ou vice-versa não funciona.
* Os submódulos do GitHub devem estar acessíveis ao aplicativo Adobe GitHub.
* [As limitações do uso de submódulos Git com repositórios gerenciados por Adobe](#limitations-recommendations) também se aplicam.
