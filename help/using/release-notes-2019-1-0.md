---
title: Notas de versão para 2019.1.0
seo-title: Notas de versão do AEM Cloud Manager para 2019.1.0
description: Siga esta página para obter informações sobre a versão 2019.1.0 do Cloud Manager.
seo-description: Siga esta página para obter informações sobre a versão 2019.1.0 do AEM Cloud Manager.
uuid: 3af5808f-828f-4846-bee4-1e62194b48ad
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: notas de versão
discoiquuid: 85a1dcf3-2eef-4ba8-b4d1-09e4a88c7bd0
translation-type: tm+mt
source-git-commit: 12d787ef2f9b2dd229b8ed0f8c602fbf5c06aa80

---


# Notas de versão para 2019.1.0 {#release-notes-for}

A versão [!UICONTROL Cloud Manager] 2018.9.0 adiciona suporte a testes de programas do AEM Assets, bem como tipos de pipeline adicionais que executam as etapas de qualidade de código e criação, implantando opcionalmente em um ambiente que não seja de produção.

## Data de lançamento {#release-date}

A data de lançamento da [!UICONTROL Cloud Manager] versão 2019.1.0 é 17 de janeiro de 2019.

## Novidades {#whats-new}

* Adicionado suporte para teste de desempenho dos ativos AEM. Consulte Configurar seu [CI/CD](configuring-pipeline.md)Pipeline para obter mais detalhes.
* Adicionado suporte para pipelines que executam somente etapas de criação e qualidade de código e implantação para ambientes que não sejam de produção. Consulte a seção Pipelines **somente para** não produção e qualidade de código em [Configure seu pipeline](configuring-pipeline.md) CI/CD para obter mais detalhes.
* Adicionado suporte para variáveis de ambiente personalizadas no ambiente de compilação. Consulte [Criar um projeto](create-an-application-project.md) de aplicativo AEM para obter mais detalhes.
* Para clientes com vários ambientes de estágio ou de produção, a seleção para qual ambiente será implantado como parte do pipeline de produção está disponível em [Configure sua página do pipeline](configuring-pipeline.md) CI/CD.
* httxt2dbm foi adicionado para construir o contêiner.
* Todos os itens do menu de ajuda abrem uma nova guia.

## Correções de erros {#bug-fixes}

* Durante a edição de um programa, foi possível desmarcar todos os conjuntos de páginas.
* A etapa de aprovação tinha título incorreto.
* Em algumas situações, o logotipo do programa era incompatível.
* Se apenas o pacote de configuração do dispatcher fosse criado, a etapa de implantação falharia.
* Os ambientes que continham instâncias de espera frias não eram tratados corretamente.
* Alguns programas encerrados apareciam no alternador de programas.
* Se uma nova ramificação foi adicionada ao repositório git enquanto o pipeline estava sendo editado, talvez não tenha sido selecionado imediatamente.
* Em algumas telas, o ícone do Developer Connection no menu Ajuda não estava visível.
* A tecla tab não foi manipulada corretamente na caixa de diálogo de configuração de envio do dispatcher.

## Problemas conhecidos {#known-issues}

* Ao abrir um programa que tenha Sites, mas não Ativos, KPIs definidos, todos os usuários veem uma chamada para um cartão de ação com um botão **Setup Program** . Entretanto, somente os usuários na função Proprietário da empresa podem clicar no botão **Configurar programa** .