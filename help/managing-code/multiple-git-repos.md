---
title: Trabalhar com vários repositórios Git
description: Em vez de trabalhar diretamente com o repositório Git do Cloud Manager, saiba como trabalhar com o seu próprio repositório Git ou vários repositórios Git.
exl-id: 53bf78bb-489a-4a83-8459-c361f532d54a
TQID: https://experienceleague.adobe.com/xKzqOfbi12A0POy-C7Gm7-n649DEBX9JP3LfXA5UC3Y
product_v2:
  - id: c68cd75e-5bca-4bc3-a60e-9e183f816441
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
source-git-commit: a07522b4a3c0619bb57b414de58633c65d9c7b5c
workflow-type: tm+mt
source-wordcount: 727
ht-degree: 59%

---

# Trabalhar com vários repositórios Git de origem {#working-with-multiple-source-git-repos}

Em vez de trabalhar diretamente com o repositório Git do Cloud Manager, saiba como trabalhar com o seu próprio repositório Git ou vários repositórios Git.

## Sincronizar repositórios Git gerenciados pelo cliente {#syncing-customer-managed-git-repositories}

Para manter o repositório Git do Cloud Manager atualizado, configure um processo de sincronização automatizada se estiver usando um ou mais repositórios próprios.

Dependendo de onde seu repositório Git está hospedado, use uma ação do GitHub ou uma solução de integração contínua, como o Jenkins, para configurar a automação. Com a automação em vigor, cada push para seu próprio repositório pode ser encaminhado automaticamente para o repositório Git da Cloud Manager.

Embora essa automação para um único repositório Git de propriedade do cliente seja simples, configurá-lo para vários repositórios requer uma configuração inicial mais abrangente. O conteúdo de vários repositórios Git precisa ser mapeado de acordo com diretórios diferentes dentro de um mesmo repositório Git do Cloud Manager. O repositório Git da Cloud Manager precisa ser provisionado com um Maven raiz `pom.xml`, listando os diferentes subprojetos na seção de módulos

Veja abaixo um exemplo de `pom.xml` para dois repositórios Git de propriedade do cliente. O primeiro projeto é colocado no diretório chamado `project-a`, e o segundo projeto é colocado no diretório chamado `project-b`.

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

Essa raiz `pom.xml` será enviada a uma ramificação no repositório Git do Cloud Manager. Em seguida, os dois projetos precisam ser configurados para encaminhar automaticamente as alterações para o repositório Git do Cloud Manager.

Por exemplo, um push para uma ramificação no projeto A pode acionar uma ação do GitHub. A ação verifica o projeto A e o repositório Git do Cloud Manager. Ela copia todo o conteúdo do projeto A para o diretório `project-a` do repositório Git do Cloud Manager. Em seguida, ela confirma e envia a alteração por push.

Por exemplo, uma alteração na ramificação `main` do projeto A é automaticamente enviada à ramificação `main` no repositório Git do Cloud Manager. É claro que pode haver um mapeamento entre ramificações, como o envio para uma ramificação chamada `dev` no projeto A sendo enviado para uma ramificação chamada `development` no repositório Git do Cloud Manager. Etapas semelhantes são necessárias para o Projeto B.

Dependendo da estratégia de ramificação e dos fluxos de trabalho, a sincronização pode ser configurada para ramificações diferentes. Se o repositório Git em uso não fornecer um conceito semelhante às ações do GitHub, também será possível fazer a integração usando o Jenkins (ou semelhante). Nesse caso, um webhook aciona uma tarefa do Jenkins que executa a tarefa.

Siga as etapas abaixo para adicionar uma nova (terceira) fonte ou repositório:

1. Adicione uma nova ação do GitHub ao novo repositório que envia as alterações desse repositório ao repositório Git do Cloud Manager.
1. Para garantir que o código do projeto esteja no repositório Git da Cloud Manager, execute essa ação pelo menos uma vez.
1. Adicione uma referência ao novo diretório no `pom.xml` do Maven raiz no repositório Git do Cloud Manager.

## Exemplo de ação do GitHub {#sample-github-action}

Um push para a ramificação `main` aciona essa ação de exemplo do GitHub, que, em seguida, é enviada a um subdiretório do repositório Git do Cloud Manager. A ação do GitHub precisa ser fornecida com dois segredos, `MAIN_USER` e `MAIN_PASSWORD`, para poder se conectar e enviar para o repositório Git da Cloud Manager.

```java
name: SYNC
env:
  # Username/email used to commit to Cloud Manager's Git repository
  USER_NAME: <NAME>
  USER_EMAIL: <EMAIL>
  # Directory within the Cloud Manager Git repository
  PROJECT_DIR: project-a
  # Cloud Manager's Git repository
  MAIN_REPOSITORY: https://$MAIN_USER:$MAIN_PASSWORD@git.cloudmanager.adobe.com/<PATH>
  # The branch in Cloud Manager's Git repository to push to
  MAIN_BRANCH : <BRANCH_NAME>
 
# Only run on a push to this branch
on:
  push:
     branches: [ main ]
 
jobs:
  build:
    runs-on: ubuntu-latest
 
    steps:
      # Checkout this project into a sub folder
      - uses: actions/checkout@v2
        with:
          path: sub
      # Cleanup sub project
      - name: Clean project
        run: |
          git -C sub log --format="%an : %s" -n 1 > commit.txt
          rm -rf sub/.git
          rm -rf sub/.github
      # Set global git configuration
      - name: Set git config
        run: |
          git config --global credential.helper cache
          git config --global user.email ${USER_EMAIL}
          git config --global user.name ${USER_NAME}
      # Checkout the main project
      - name: Checkout main project
        run:
          git clone -b ${MAIN_BRANCH} https://${{ secrets.PAT }}@github.com/${MAIN_REPOSITORY}.git main 
      # Move sub project
      - name: Move project to main project
        run: |
          rm -rf main/${PROJECT_DIR} 
          mv sub main/${PROJECT_DIR}
      - name: Commit Changes
        run: |
          git -C main add -f ${PROJECT_DIR}
          git -C main commit -F ../commit.txt
          git -C main push
```

Como mostrado acima, usar uma ação do GitHub é uma opção flexível. Qualquer mapeamento entre ramificações dos repositórios Git pode ser executado, assim como qualquer mapeamento dos projetos Git separados no layout de diretório do projeto principal.

>[!NOTE]
>
>O script acima usa `git add` para atualizar o repositório, o que pressupõe que as remoções estejam incluídas. Dependendo da configuração padrão do Git, substitua esse requisito por `git add --all`.

## Exemplo de processo do Jenkins {#sample-jenkins-job}

Este é um exemplo de script que pode ser usado em um processo do Jenkins ou similar. Uma alteração em um repositório Git atua como acionador. O processo do Jenkins verifica o estado mais recente desse projeto ou ramificação e então aciona esse script.

Este script verifica o repositório Git do Cloud Manager e confirma o código do projeto em um subdiretório.

O processo do Jenkins precisa de dois segredos, `MAIN_USER` e `MAIN_PASSWORD`, para poder conectar-se e enviar ao repositório Git do Cloud Manager.

```java
# Username/email used to commit to Cloud Manager's Git repository
export USER_NAME=<NAME>
export USER_EMAIL=<EMAIL>
# Directory within the Cloud Manager Git repository
export PROJECT_DIR=project-a
# Cloud Manager's Git repository
export MAIN_REPOSITORY=https://$MAIN_USER:$MAIN_PASSWORD@git.cloudmanager.adobe.com/<PATH>
# The branch in Cloud Manager's Git repository to push to
export MAIN_BRANCH=<BRANCH_NAME>
 
# clean up and init
rm -rf target
mkdir target
 
# mv project to sub folder
mkdir target/sub
for f in .* *
do
    if [ "$f" != "." -a "$f" != ".." -a "$f" != "target" ]
    then
        mv "$f" target/sub
    fi
done
cd target
 
# capture log and remove git info
cd sub
git log --format="%an : %s" -n 1 > ../commit.txt
rm -rf .git
rm -rf .github
cd ..
 
# checkout main repository
git clone -b $MAIN_BRANCH $MAIN_REPOSITORY main
cd main
 
# configure main repository
git config credential.helper cache
git config user.email $USER_EMAIL
git config user.name $USER_NAME
 
# update project in main
rm -rf $PROJECT_DIR
mv ../sub $PROJECT_DIR
 
# commit changes to main
git add -f $PROJECT_DIR
git commit -F ../commit.txt
git push
```

O uso de uma tarefa do Jenkins é flexível. Qualquer mapeamento entre ramificações dos repositórios Git pode ser executado, assim como qualquer mapeamento dos projetos Git separados no layout de diretório do projeto principal.

>[!NOTE]
>
>O script acima usa `git add` para atualizar o repositório, o que pressupõe que as remoções estejam incluídas. Dependendo da configuração padrão do Git, substitua `git add` por `git add --all`.
