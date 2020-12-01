---
title: Configurar as ramificações de liberação
seo-title: Configurar as ramificações de liberação
description: Configurar ramificações de lançamento no Git para AEM Cloud Manager
seo-description: Siga esta página para saber como configurar suas ramificações de lançamento no git.
uuid: d12a8b85-b7fd-4b55-a05a-a0f874ce598c
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: getting-started
discoiquuid: 53807ea6-9464-429d-9322-85c9f405dff6
translation-type: tm+mt
source-git-commit: 9c0df236c1e800802d62dea09996bb8e1e7033f7
workflow-type: tm+mt
source-wordcount: '307'
ht-degree: 3%

---


# Configurar as ramificações de liberação {#configure-your-release-branches}

## Configurando sua primeira ramificação no Git {#setting-up-your-first-branch-in-git}

Um único, inicialmente vazio, **Repositório Git** é provisionado para cada programa a bordo no Cloud Manager. Esse repositório pode conter quantas ramificações (ou quantos) seu processo de desenvolvimento seguir, mas deve haver pelo menos uma ramificação que seja usada pelo pipeline de CI/CD para implantar o código do aplicativo no estágio e na produção. A prática recomendada é usar `master` como o nome desta ramificação. Convenientemente, esse é o comportamento padrão dos clientes Git ao configurar novos projetos.

Por exemplo, ao configurar um novo projeto, você executará um conjunto de comandos como este:

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
>Não é um requisito para usar o cliente de linha de comando. Há uma variedade de clientes Git gráficos disponíveis como aplicativos independentes ou como parte de um Ambiente de desenvolvimento integrado (IDE), como o Eclipse ou o IntelliJ. Desde que o aplicativo cliente suporte o Git usando HTTPS, ele deve ser compatível com [!UICONTROL Cloud Manager].

## Empurrando sua primeira ramificação {#pushing-your-first-branch}

Depois de confirmar pelo menos uma revisão, você pode adicionar o repositório [!UICONTROL Cloud Manager] como um **remote** e, em seguida, enviar seus compromissos para ele:

```shell
$ git remote add adobe <url>
$ git push adobe master
Counting objects: 36, done.
Delta compression using up to 8 threads.
Compressing objects: 100% (27/27), done.
Writing objects: 100% (36/36), 7.31 KiB | 1.83 MiB/s, done.
Total 36 (delta 6), reused 0 (delta 0)
To <url>
 * [new branch]      master -> master
```

>[!NOTE]
>
>O URL específico, juntamente com suas credenciais, será fornecido ao cliente pela sua equipe de engenharia de sucesso do cliente durante a [!UICONTROL Cloud Manager] integração.

## Ramificações adicionais {#additional-branches}

Uma única ramificação `master` pode ser suficiente para projetos muito simples, mas na maioria dos casos, será necessária uma estratégia de ramificação mais complexa. Muitos clientes seguem um processo em que atividades de desenvolvimento diárias são executadas em uma ramificação chamada `develop` e a ramificação de desenvolvimento é unida na ramificação `master` quando é hora de uma implantação.

>[!NOTE]
>
>Para visualização dos comandos git comuns, consulte [Git Cheat](https://github.github.com/training-kit/downloads/github-git-cheat-sheet).
