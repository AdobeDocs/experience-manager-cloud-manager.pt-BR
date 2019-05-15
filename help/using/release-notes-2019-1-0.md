---
title: Notas de versão de 2019.1.0
seo-title: Notas de versão do Gerenciador do AEM Cloud para 2019.1.0
description: Siga esta página para obter informações sobre a versão 2019.1.0 do Gerenciador de nuvem.
seo-description: Siga esta página para obter informações sobre a versão 2019.1.0 do Gerenciador de AEM Cloud.
uuid: 3 af 5808 f -828 f -4846-bee 4-1 e 62194 b 48
contentOwner: jsyal
products: SG_ EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: notas-notas
discoiquuid: 85 a 1 dcf 3-2 eef -4 ba 8-b 4 d 1-09 e 4 a 88 c 7 bd 0
translation-type: tm+mt
source-git-commit: 1dfb065c09569f811e5a006d3d74825d3bd7cc8d

---


# Notas de versão de 2019.1.0 {#release-notes-for}

A versão [!UICONTROL Cloud Manager] 2018.9.0 oferece suporte para o teste do AEM Assets, bem como para tipos de pipeline adicionais que executam etapas de qualidade de compilação e código, opcionalmente implantação para um ambiente que não seja de produção.

## Data de lançamento {#release-date}

A Data de lançamento da [!UICONTROL Cloud Manager] versão 2019.1.0 é January 7 de janeiro de 27 19.

## Novidades {#whats-new}

* Adicionado suporte para testar o desempenho dos ativos AEM. Consulte Configurar seu [CI/CD Pipelinepara](configuring-pipeline.md)obter mais detalhes.
* Adicionado suporte para gasodutos que executam somente etapas de qualidade de compilação e código e gasodutos implantando em ambientes de não produção. Consulte **a** seção de vídeos de não produção e de qualidade de código em [Configurar seu CI/CD Pipeline](configuring-pipeline.md) para obter mais detalhes.
* Adicionado suporte para variáveis de ambiente personalizadas em ambiente de criação. Consulte [Criar um projeto do AEM Application](create-an-application-project.md) para obter mais detalhes.
* Para clientes com diversos ambientes stage ou production, a seleção de qual ambiente será implantada como parte do pipeline de produção estará disponível em [Configurar sua página de pipeline](configuring-pipeline.md) CI/CD.
* httxt 2 dbm foi adicionado para construir contêiner.
* Todos os itens do menu Ajuda abrem uma nova guia.

## Correções de erros {#bug-fixes}

* Ao editar um programa, era possível cancelar a seleção de todos os conjuntos de páginas.
* A etapa de aprovação foi nomeada incorretamente.
* Em algumas situações, o logotipo do programa era incorretamente controlado.
* Se apenas o pacote de configuração do dispatcher fosse criado, a etapa de implantação falharia.
* Os ambientes que continham instâncias de espera frio não eram tratados corretamente.
* Alguns programas encerrados apareciam no alternador de programa.
* Se uma nova ramificação foi adicionada ao repositório do git enquanto o pipeline estava sendo editado, talvez não tenha sido selecionável imediatamente.
* Em algumas telas, o ícone de Developer Connection no menu Ajuda não estava visível.
* A tecla tab não era tratada corretamente na caixa de diálogo de configuração de limpeza do expedidor.

## Problemas conhecidos {#known-issues}

* Ao abrir um programa com Sites, mas não Ativos, kpis definidas, todos os usuários veem uma chamada para o cartão de ação com um botão **de Configuração do Programa** . No entanto, somente os usuários na função Proprietário de negócios podem clicar **no** botão Programa de configuração.