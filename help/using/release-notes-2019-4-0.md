---
title: Notas de versão para 2019.4.0
seo-title: Notas de versão do AEM Cloud Manager para 2019.4.0
description: Siga esta página para obter informações sobre a versão 2019.4.0 do Cloud Manager.
seo-description: Siga esta página para obter informações sobre a versão 2019.4.0 do AEM Cloud Manager.
translation-type: tm+mt
source-git-commit: b368c46c2a9f40d0c3867db6eb2a333bd71fe22a

---


# Notas de versão para 2019.4.0 {#release-notes-for}

A versão [!UICONTROL Cloud Manager] 2019.4.0 não contém alterações funcionais significativas. Siga as seções abaixo para obter mais detalhes.

## Data de lançamento {#release-date}

A data de lançamento da [!UICONTROL Cloud Manager] versão 2019.4.0 é 18 de abril de 2019.

## Novidades {#whats-new}

* A interface do usuário do Cloud Manager agora está disponível em inglês, francês, alemão e japonês.
* As etapas de implantação agora contêm o processo em execução, ou seja, quando um backup é executado, os pacotes estão sendo instalados e os balanceadores de carga estão sendo reconfigurados

## Correções de erros {#bug-fixes}

* A abordagem de implantação usada para alterações do Dispatcher foi aprimorada para lidar com casos de uso adicionais.
* Alguns tipos de tamanho de instância não eram exibidos corretamente na página Ambientes.
* As regras de qualidade do código dependências CQBP-84 produziram falsos positivos para bibliotecas incorporadas da Adobe, como componentes principais do WCM e Commons de compartilhamento de ativos.
* O botão de detalhes da etapa de verificação de código foi ativado quando os detalhes não estavam disponíveis.
* A mensagem de erro ao especificar um valor inválido para exibições de página por minuto do KPI tinha o limite inferior errado.
* A categoria de implantação em um pipeline que não seja de produção foi capitalizada incorretamente.
* A chamada para o cartão de ação na página **Visão geral** tinha texto incorreto quando o repositório git não estava configurado corretamente.

## Problemas conhecidos {#known-issues}

* Os valores de SLA podem ser arredondados incorretamente.
