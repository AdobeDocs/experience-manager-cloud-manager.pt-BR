---
title: Configuração de ramificações
description: Saiba como configurar sua primeira ramificação no Git e como ela é usada pelo pipeline CI/CD para implantar seu código de aplicativo.
exl-id: ff2ae28f-902e-4fb2-aeb1-3636cb5cd9bb
source-git-commit: 984269e5fe70913644d26e759fa21ccea0536bf4
workflow-type: tm+mt
source-wordcount: '324'
ht-degree: 4%

---


# Configurar ramificações {#configuring-branches}

Saiba como configurar sua primeira ramificação no Git e como ela é usada pelo pipeline CI/CD para implantar seu código de aplicativo.

## Configurar a primeira ramificação no Git {#setting-up-your-first-branch-in-git}

Um único repositório Git, inicialmente vazio, [está provisionado](/help/requirements/environment-provisioning.md) para cada programa integrado no Cloud Manager. Esse repositório pode conter quantas ramificações seu processo de desenvolvimento necessitar, mas deve haver pelo menos uma ramificação usada pelo pipeline CI/CD para implantar o código do aplicativo no preparo e na produção. A prática recomendada é usar `main` como o nome desta ramificação. Convenientemente, essa abordagem é o comportamento padrão dos clientes Git ao configurar novos projetos.

Por exemplo, ao configurar um novo projeto, você executa um conjunto de comandos semelhantes aos seguintes.

```shell
$ git init
Initialized empty Git repository in /Users/myname/workspace/new-project/.git/
... steps which add Maven build files and source code ...
$ git add pom.xml core/pom.xml core/src ui.apps/pom.xml ui.apps/src
$ git commit -m "initial commit"
 19 files changed, 777 insertions(+)
 create mode 100644 core/pom.xml
 create mode 100644 pom.xml
 create mode 100644 ui.apps/pom.xml
 create mode 100644 ui.apps/src/main/content/META-INF/vault/config.xml
 create mode 100644 ui.apps/src/main/content/META-INF/vault/definition/.content.xml
 create mode 100644 ui.apps/src/main/content/META-INF/vault/filter.xml
 create mode 100644 ui.apps/src/main/content/META-INF/vault/nodetypes.cnd
 create mode 100644 ui.apps/src/main/content/META-INF/vault/properties.xml
 create mode 100644 ui.apps/src/main/content/jcr_root/apps/my-aem-project/install/.vltignore
 create mode 100644 ui.apps/src/main/content/jcr_root/conf/.content.xml
 create mode 100644 ui.apps/src/main/content/jcr_root/conf/my-aem-project/.content.xml
 create mode 100644 ui.apps/src/main/content/jcr_root/conf/my-aem-project/settings/.content.xml
 create mode 100644 ui.apps/src/main/content/jcr_root/conf/my-aem-project/settings/wcm/.content.xml
 create mode 100644 ui.apps/src/main/content/jcr_root/conf/my-aem-project/settings/wcm/policies/.content.xml
 create mode 100644 ui.apps/src/main/content/jcr_root/conf/my-aem-project/settings/wcm/policies/_rep_policy.xml
 create mode 100644 ui.apps/src/main/content/jcr_root/conf/my-aem-project/settings/wcm/template-types/.content.xml
 create mode 100644 ui.apps/src/main/content/jcr_root/conf/my-aem-project/settings/wcm/template-types/_rep_policy.xml
 create mode 100644 ui.apps/src/main/content/jcr_root/conf/my-aem-project/settings/wcm/templates/.content.xml
 create mode 100644 ui.apps/src/main/content/jcr_root/conf/my-aem-project/settings/wcm/templates/_rep_policy.xml
```

>[!NOTE]
>
>Não é um requisito usar o cliente de linha de comando. Há uma variedade de clientes gráficos do Git disponíveis como aplicativos independentes ou como parte de um ambiente de desenvolvimento integrado (IDE), como o Eclipse ou o IntelliJ. Desde que o aplicativo cliente seja compatível com o uso de HTTPS do Git, ele deve ser compatível com o [!UICONTROL Cloud Manager].

## Encaminhar a primeira ramificação {#pushing-your-first-branch}

Ao confirmar pelo menos uma revisão, é possível adicionar o repositório do [!UICONTROL Cloud Manager] como remoto e, em seguida, enviar suas confirmações para ele.

```shell
$ git remote add adobe <url>
$ git push adobe master
Counting objects: 36, done.
Delta compression using up to 8 threads.
Compressing objects: 100% (27/27), done.
Writing objects: 100% (36/36), 7.31 KiB | 1.83 MiB/s, done.
Total 36 (delta 6), reused 0 (delta 0)
To <url>
 * [new branch]      main -> main
```

>[!NOTE]
>
>A URL específica, juntamente com suas credenciais, é fornecida pelo Adobe CSE (Engenheiro de Sucesso do Cliente) durante a integração do [!UICONTROL Cloud Manager].

## Ramificações adicionais {#additional-branches}

Uma única ramificação `main` pode ser suficiente para projetos muito simples, mas, na maioria dos casos, é necessária uma estratégia de ramificação mais complexa. Muitos clientes seguem um processo em que as atividades diárias de desenvolvimento são executadas em uma ramificação chamada `develop`. A ramificação de desenvolvimento é então mesclada à ramificação `main` no momento de uma implantação.

>[!TIP]
>
>Para ver comandos comuns do Git, consulte a [Folha de características do Git](https://training.github.com/downloads/github-git-cheat-sheet).
