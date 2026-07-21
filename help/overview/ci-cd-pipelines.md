---
title: Pipelines de CI/CD
description: Saiba mais sobre os pipelines de CI/CD e como eles lidam com implantações em ambientes de preparo e produção no Cloud Manager.
exl-id: 7130e5b7-6986-48c8-900c-90f3e4187f91
TQID: https://experienceleague.adobe.com/BwkZH2MIbXrzSxf0yk9yeDZZIpw7-Ldue-OPQPkWrdg
product_v2: id: c68cd75e-5bca-4bc3-a60e-9e183f816441id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2: id: cd2426f1-5719-4006-b8c2-738e5969754bid: ff09c71c-26a9-449a-85f8-2aeb8ce96100
subfeature_v2: id: c14b2f98-ee16-4c49-b87b-919c91b01d9d
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2: id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87cid: d095671a-1355-40aa-8b5f-06c33c68080b
source-git-commit: f83ddaa74a656abd2328cd3969ff0cc10b79d729
workflow-type: tm+mt
source-wordcount: 1085
ht-degree: 50%

---

# Pipelines de CI/CD {#ci-cd-pipeline}

Saiba mais sobre os pipelines de CI/CD e como eles lidam com implantações em ambientes de preparo e produção no Cloud Manager.

## Visão geral {#overview}

O [!UICONTROL Cloud Manager] inclui uma estrutura de CI/CD (integração contínua/entrega contínua), que permite que as equipes de implementação testem e entreguem rapidamente códigos novos ou atualizados. As equipes de implementação podem definir, configurar e iniciar um pipeline de CI/CD automático. Esse pipeline segue as práticas recomendadas de codificação da Adobe para executar uma verificação de código abrangente e garantir a mais alta qualidade do código.

O pipeline de CI/CD também automatiza processos de teste de unidade e desempenho para aumentar a eficiência da implantação e identificar proativamente problemas críticos que são caros de corrigir após a implantação. As equipes de implementação podem acessar um relatório abrangente de desempenho de código para obter visibilidade sobre o impacto potencial em KPIs e validações críticas de segurança se o código for implantado na produção.

## Sobre o processo de pipeline {#pipeline-process}

Este diagrama ilustra o que acontece quando uma versão é acionada no [!UICONTROL Cloud Manager] usando um pipeline.

![O processo de pipeline](/help/assets/screen_shot_2018-05-30at82457pm.png)

| Etapa do pipeline | Descrição |
| --- | --- |
| &#x200B;1. Iniciar uma versão | Um gerente de implantação aciona um lançamento manualmente, com uma confirmação do Git ou com base em uma programação recorrente. |
| &#x200B;2. Criar uma tag de lançamento | O [!UICONTROL Cloud Manager] cria uma tag do Git para marcar o lançamento usando um número de versão gerado automaticamente; por exemplo, `2018.531.245527.0000001222`. |
| &#x200B;3. Criar lançamento com a versão gerada automaticamente | O [!UICONTROL Cloud Manager] cria o aplicativo com o número de versão atribuído recentemente. |
| &#x200B;4. Avaliar a qualidade do código | O [!UICONTROL Cloud Manager] verifica o código-fonte e fornece um resumo antes que o código possa ser implantado no ambiente de preparo. |
| &#x200B;5. Artefatos com versão armazenados | Os artefatos de versão são armazenados para uso posterior nas etapas de implantação. |
| &#x200B;6. Implantação automática de artefatos no preparo do AMS AEM | O artefato de lançamento é implantado no ambiente de preparo. |
| &#x200B;7. Acionar testes automatizados | O [!UICONTROL Cloud Manager] executa testes de desempenho e segurança no artefato. |
| &#x200B;8. Implantação do acionador de produção | Após a conclusão dos testes automatizados, o [!UICONTROL Cloud Manager] inicia a implantação para produção. |
| &#x200B;9. O [!UICONTROL Cloud Manager] obtém o(s) artefato(s) para implantar | O [!UICONTROL Cloud Manager] extrai os artefatos de lançamento armazenados. |
| &#x200B;10. Implantar artefatos para produção | Os artefatos de lançamento são implantados no ambiente de produção. |

### Fontes de código {#code-sources}

Os pipelines também podem diferir pelo tipo de código que implantam, além de produção e não produção.

* **[Pipelines de pilha completa](#full-stack-pipeline)** - Implante o código completo do aplicativo do AEM junto com as configurações HTTPD/Dispatcher.
* **[Pipelines de configuração no nível da Web](#web-tier-config-pipelines)** - Implante somente configurações HTTPD/Dispatcher.

### Pipelines de pilha completa {#full-stack-pipeline}

Os pipelines de pilha completa implantam o código completo do aplicativo do AEM no tempo de execução do AEM e, por padrão, também implantam configurações no nível da Web.

As restrições a seguir se aplicam.

* Um usuário deve estar conectado com a função **Gerente de Implantação** para configurar ou executar pipelines.
* Somente pode haver um pipeline de pilha completa por ambiente.

A seguir, é descrito como o pipeline de pilha completa interage com um [pipeline de configuração de camada da Web](#web-tier-config-pipelines).

* O pipeline de pilha completa para um ambiente ignora a configuração do Dispatcher se existir um pipeline de configuração no nível da Web correspondente.
* Se não existir um pipeline de configuração no nível da Web correspondente para o ambiente, o usuário poderá incluir ou ignorar a configuração do Dispatcher ao configurar o pipeline de pilha completa.

Os pipelines de pilha completa podem ser pipelines de qualidade do código ou de implantação.

#### Configurar pipelines de pilha completa {#configure-full-stack}

Consulte [Adicionar um pipeline de produção](/help/using/production-pipelines.md#full-stack-code).
Consulte [Adicionar um pipeline de não produção](/help/using/non-production-pipelines.md#add-non-production-pipeline).

### Pipelines de configuração no nível da Web {#web-tier-config-pipelines}

Os pipelines de configuração no nível da Web permitem a implantação exclusiva da configuração HTTPD/Dispatcher no tempo de execução do AEM, desvinculando-a de outras alterações de código. É um pipeline simplificado que fornece aos usuários que desejam implantar somente as alterações de configuração do Dispatcher um meio eficiente de fazê-lo rapidamente.

>[!TIP]
>
>Os pipelines de configuração no nível da Web permitem armazenar a configuração da Web no mesmo local de origem ou em um local diferente do pipeline de pilha completa, dependendo do que melhor se adapta à estrutura do projeto.

As restrições a seguir se aplicam.

* Um usuário deve estar conectado com a função **Gerente de Implantação** para configurar ou executar pipelines.
* Em um dado momento, somente pode haver um pipeline de configuração no nível da Web por ambiente.
* O usuário não pode configurar um pipeline de configuração no nível da Web quando seu pipeline de pilha completa correspondente está em execução.

O item a seguir descreve como o pipeline de configuração no nível da Web interage com o [pipeline de pilha completa](#full-stack-pipeline).

* Se um pipeline de configuração no nível da Web não estiver definido para um ambiente, o usuário poderá optar por incluir ou ignorar a configuração do Dispatcher ao configurar o pipeline de pilha completa.
* Depois que um pipeline de configuração no nível da Web é configurado para um ambiente, seu pipeline de pilha completa correspondente (se existir) ignora a configuração do Dispatcher durante a execução e a implantação.
* Depois que um pipeline de configuração no nível da Web é excluído, seu pipeline de pilha completa correspondente (se existir) é redefinido para implantar configurações do Dispatcher durante a execução.

>[!NOTE]
>
>Para programas do AMS com implantação azul-verde ativada, as atualizações no nível da Web usam implantação contínua por padrão. Use um pipeline de pilha completa se precisar de implantação azul-verde para alterações no nível da Web.

#### Configurar pipelines no nível da Web {#configure-web-tier}

Consulte [Adicionar um pipeline de produção](/help/using/production-pipelines.md#web-tier-config).
Consulte [Adicionar um pipeline de não produção](/help/using/non-production-pipelines.md#add-non-production-pipeline).

### Criações mais rápidas usando o Smart Build {#use=smart-build}

O Cloud Manager agora usa uma estratégia de compilação otimizada chamada **Compilação Inteligente**, que usa cache de módulo para acelerar o processo de compilação. Durante cada build, somente os módulos que foram alterados são recriados, enquanto os módulos inalterados são reutilizados do cache.

O Smart Build está disponível para pipelines de qualidade do código e implantação de pilha completa (desenvolvimento, preparo, produção).

Consulte [Adicionar um pipeline de não produção](/help/using/non-production-pipelines.md#add-non-production-pipeline) e [Sobre o uso do Smart Build em um pipeline de não produção](/help/using/non-production-pipelines.md#about-smart-build).


### Como configurar um pipeline de CI/CD {#how-to-setup-a-ci-cd-pipeline}

Para saber mais sobre a configuração de pipelines, consulte os documentos [Configuração de pipelines de produção](/help/using/production-pipelines.md) e [Configuração de pipelines de não produção](/help/using/non-production-pipelines.md).

## Portas de qualidade {#quality-gates}

O pipeline de CI/CD fornece portas de qualidade ou critérios de aceitação, que devem ser atendidos antes que o código possa ser movido do ambiente de preparo para o ambiente de implantação. Há três portas no pipeline:

* Qualidade do código
* Teste de desempenho
* Teste de segurança

Para cada uma dessas portas, há três níveis de problemas que podem ser identificados:

* **Crítico**: problemas críticos identificados pela porta causam uma falha imediata do pipeline.
* **Importante**: problemas importantes identificados pela porta fazem com que o pipeline entre em pausa. Um gerente de implantação, gerente de projeto ou líder de negócios pode anular os problemas, permitindo que o pipeline continue. Alternativamente, eles podem aceitar os problemas, interrompendo o pipeline com uma falha.
* **Informações**: os problemas de informação identificados pela porta são fornecidos exclusivamente para fins informativos e não têm impacto na execução do pipeline.

Este é um exemplo de verificação de código com problemas identificados.

![Exemplo de verificação de código](/help/assets/quality-gate-failed.png)

### Como configurar portas {#how-to-setup-gates}

Consulte o documento [Configuração de pipelines de produção](/help/using/production-pipelines.md) para obter detalhes sobre configuração de código, qualidade e portas de desempenho.
