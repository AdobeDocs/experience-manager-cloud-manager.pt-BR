---
title: Notas de versão de 2019.4.0
seo-title: Notas de versão do Gerenciador do AEM Cloud para 2019.4.0
description: Siga esta página para obter informações sobre a versão 2019.4.0 do Gerenciador de nuvem.
seo-description: Siga esta página para obter informações sobre a versão 2019.4.0 do Gerenciador de AEM Cloud.
translation-type: tm+mt
source-git-commit: 1dfb065c09569f811e5a006d3d74825d3bd7cc8d

---


# Notas de versão de 2019.4.0 {#release-notes-for}

A versão [!UICONTROL Cloud Manager] 2019.4.0 não contém mudanças funcionais significativas. Siga as seções abaixo para obter mais detalhes.

## Data de lançamento {#release-date}

A Data de lançamento da [!UICONTROL Cloud Manager] versão 2019.4.0 é April 8 de abril de 28 19.

## Novidades {#whats-new}

* A interface do usuário do Experience Cloud Manager agora está disponível em inglês, francês, alemão e japonês.
* As etapas de implantação agora contêm o processo em execução, ou seja, quando um backup está em execução, os pacotes estão sendo instalados e os balanceadores de carga estão sendo reconfigurados

## Correções de erros {#bug-fixes}

* A abordagem de implantação usada para alterações do Dispatcher foi aprimorada para lidar com casos de uso adicionais.
* Alguns tipos de tamanho de instância não eram exibidos corretamente na página Ambientes.
* As regras de qualidade de código CQBP -84-dependências produziram falsos positivos para bibliotecas incorporadas da Adobe, como Componentes do WCM Core e Compartilhamento de ativos.
* O botão de detalhes da etapa de leitura do código foi ativado quando os detalhes não estavam disponíveis.
* A mensagem de erro ao especificar um valor inválido para as exibições de página por minuto KPI possuía o limite inferior errado.
* A categoria de implantação em um pipeline de não produção estava em letra maiúscula.
* A chamada para o cartão de ação na página **Visão geral** tinha um texto incorreto quando o repositório do git não era configurado corretamente.

## Problemas conhecidos {#known-issues}

* Valores SLA podem ser arredondados incorretamente.
