---
title: Configurar suas ramificações de lançamento
seo-title: Configurar suas ramificações de lançamento
description: Configurar as ramificações de lançamento no Git para o Gerenciador do AEM Cloud
seo-description: Siga esta página para saber como configurar suas ramificações de lançamento no git.
uuid: d 12 a 8 b 85-b 7 fd -4 b 55-a 05 a-a 0 f 874 ce 598 c
contentOwner: jsyal
products: SG_ EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: getting-started
discoiquuid: 53807 ea 6-9464-429 d -9322-85 c 9 f 405 dff 6
translation-type: tm+mt
source-git-commit: 1dfb065c09569f811e5a006d3d74825d3bd7cc8d

---


# Configurar suas ramificações de lançamento {#configure-your-release-branches}

## Configuração da primeira ramificação no Git {#setting-up-your-first-branch-in-git}

Um único, inicialmente vazio, **o Git Repository** é provisionado para cada programa ligado no Gerenciador de nuvem. Este repositório pode conter a quantidade de ramificações (ou poucas) que o processo de desenvolvimento segue, mas deve haver pelo menos um ramo que é usado pelo pipeline CI/CD para implantar o código do aplicativo em palco e produção. A prática recomendada é usar `master` como o nome desse ramo. Convenientemente, esse é o comportamento padrão dos clientes Git ao configurar novos projetos.

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
>Não é necessário usar o cliente de linha de comando. Há uma variedade de clientes gráficos gráficos disponíveis como aplicativos independentes ou como parte de um Ambiente de desenvolvimento integrado (IDE) como Eclipse ou intellij. Desde que o aplicativo cliente ofereça suporte ao Git usando HTTPS, ele deve ser compatível [!UICONTROL Cloud Manager]com.

## Mover seu primeiro ramo {#pushing-your-first-branch}

Depois de confirmar pelo menos uma revisão, você pode adicionar o [!UICONTROL Cloud Manager] repositório como **remoto** e encaminhar suas vírgulas:

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
>O URL específico, juntamente com suas credenciais, será fornecido à sua Engenharia de sucesso do cliente durante [!UICONTROL Cloud Manager] a integração.

## Ramificações adicionais {#additional-branches}

Uma `master` única ramificação pode ser suficiente para projetos muito simples, mas, na maioria dos casos, será necessária uma estratégia de ramificação mais complexa. Muitos clientes seguem um processo em que atividades de desenvolvimento diário são executadas em uma ramificação chamada `develop` e o ramificação de revelação é mesclado no `master` ramo quando é hora de uma implantação.

>[!NOTE]
>
>Para exibir os comandos comuns de git, consulte a Planilha [Git Cheat](https://services.github.com/on-demand/downloads/github-git-cheat-sheet.pdf).

