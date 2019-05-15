---
title: Notas de versão de 2018.9.0
seo-title: Notas de versão do Gerenciador do AEM Cloud para 2018.9.0
description: Siga esta página para obter informações sobre a versão 2018.9.0 do Gerenciador de nuvem.
seo-description: Siga esta página para obter informações sobre a versão 2018.9.0 do Gerenciador de AEM Cloud.
uuid: 3 af 5808 f -828 f -4846-bee 4-1 e 62194 b 48
contentOwner: jsyal
products: SG_ EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: notas-notas
discoiquuid: 85 a 1 dcf 3-2 eef -4 ba 8-b 4 d 1-09 e 4 a 88 c 7 bd 0
translation-type: tm+mt
source-git-commit: 1dfb065c09569f811e5a006d3d74825d3bd7cc8d

---


# Notas de versão de 2018.9.0 {#release-notes-for}

A versão [!UICONTROL Cloud Manager] 2018.9.0 adiciona suporte para uma API da Adobe baseada em I/O, incluindo Eventos, para a integração [!UICONTROL Cloud Manager]de pipeline CI/CD com outros sistemas. Também inicia a regravação da camada de UI em Reagir.

## Data de lançamento {#release-date}

A Data de lançamento da [!UICONTROL Cloud Manager] versão 2018.9.0 é November 1 de novembro de 21 18.

## Novidades {#whats-new}

* **Pipeline CI/CD** - Novo sistema de API e evento para a integração [!UICONTROL Cloud Manager]de pipeline CI/CD com outros sistemas. Consulte a Documentação [!UICONTROL Cloud Manager] da API (https://www.adobe.io/apis/experiencecloud/cloud-manager/docs.html) para obter mais informações.

* **IU** - Introdução à nova camada de interface de usuário, que é mais responsiva e responsável.

## Correções de erros {#bug-fixes}

* Em [!UICONTROL Cloud Manager] 2018.8.0, as durações da página Atividade foram listadas em minutos e horas, mas essas informações não eram refletidas no cabeçalho da tabela.
* Em raras ocasiões, os clientes não conseguiam iniciar o novo assistente de projeto do aplicativo.
* O rótulo do botão na nova caixa de diálogo do assistente de aplicativos do aplicativo era incorreto.
* Em algumas circunstâncias, clicar no botão Detalhes na página Atividade redirecionaria para a página Visão geral.
* Algumas circunstâncias raras e inesperadas resultavam em um cartão ausente na página Visão geral.
* O ícone Ativos foi exibido na página Lista de programas para todos os clientes.
* Quando houve falhas de back end, algumas vezes uma execução de pipeline parece permanecer na etapa *Validar* .
* Em determinadas circunstâncias, a duração da descrição do programa foi incorreta.

## Problemas conhecidos {#known-issues}

* As ramificações criadas usando o Assistente de projeto do aplicativo não podem conter traços.
* A barra lateral [!UICONTROL Experience Cloud] de Notificação da Adobe pode não carregar notificações consistentemente. No entanto, as notificações estão visíveis na Adobe [!UICONTROL Experience Cloud] e, se configuradas, ainda serão enviadas por email.

