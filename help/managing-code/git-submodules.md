---
title: Suporte ao submódulo Git
description: Saiba como você pode usar submódulos Git para mesclar o conteúdo de várias ramificações em repositórios Git no momento da criação.
exl-id: f946d7e7-114a-4e33-bb82-2625d37bba2f
source-git-commit: 984269e5fe70913644d26e759fa21ccea0536bf4
workflow-type: ht
source-wordcount: '412'
ht-degree: 100%

---

# Suporte ao submódulo Git para repositórios da Adobe {#git-submodule-support}

Os submódulos Git podem ser usados para mesclar o conteúdo de várias ramificações em repositórios Git no momento da criação.

Quando o processo de criação do Cloud Manager é executado, primeiro o repositório do pipeline é clonado e a ramificação configurada é verificada. Se a ramificação contiver um arquivo `.gitmodules` no diretório raiz, o comando será executado.

```
$ git submodule update --init
```

Esse processo verifica cada submódulo no diretório apropriado. Essa técnica é uma alternativa potencial para [trabalhar com vários repositórios Git de origem](/help/managing-code/multiple-git-repos.md) em organizações que estão acostumadas com o uso de submódulos do Git e que não desejam gerenciar um processo de mesclagem externo.

Por exemplo, digamos que existam três repositórios, cada um contendo uma única ramificação chamada `main`. No repositório “principal”, ou seja, aquele configurado nos pipelines, a ramificação `main` tem um arquivo `pom.xml` que declara os projetos contidos nos outros dois repositórios.

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

Os resultados no arquivo `.gitmodules` são parecidos com o seguinte:

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

Ao usar submódulos do Git, observe que:

* O URL do Git deve seguir exatamente a sintaxe descrita acima.
* Por motivos de segurança, não incorpore credenciais nesses URLs.
* Somente os submódulos na raiz da ramificação são permitidos.
* As referências do submódulo Git são armazenadas em confirmações Git específicas. Como resultado, quando são feitas alterações no repositório do submódulo, a confirmação referenciada precisa ser atualizada. Por exemplo, usando `git submodule update --remote`.
* A menos que seja necessário, o Adobe recomenda que você use submódulos “superficiais” executando `git config -f .gitmodules submodule.<submodule path>.shallow true` para cada submódulo.


## Suporte ao submódulo Git para repositórios privados {#private-repositories}

O suporte para submódulos Git ao usar [repositórios privados](private-repositories.md) é basicamente o mesmo da utilização de repositórios da Adobe.

No entanto, após configurar o arquivo `pom.xml` e executar os comandos `git submodule`, é necessário adicionar um arquivo `.gitmodules` no diretório raiz do repositório agregador do Cloud Manager para detectar a configuração do submódulo.

![arquivo .gitmodules](assets/gitmodules.png)

![Agregador](assets/aggregator.png)

### Limitações e recomendações {#limitations-recommendations-private-repos}

Ao usar submódulos Git com repositórios privados, esteja ciente das limitações a seguir.

* Os URLs do Git para os submódulos podem estar no formato HTTPS ou SSH, mas devem estar vinculados a um repositório Github.com. Adicionar um submódulo de repositório da Adobe a um repositório agregador do GitHub ou vice-versa não é possível.
* Os submódulos do GitHub precisam estar acessíveis ao aplicativo Adobe GitHub.
* [As limitações do uso de submódulos Git com repositórios gerenciados pela Adobe](#limitations-recommendations) também se aplicam.
