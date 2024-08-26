---
title: Pipelines de CI/CD
description: Saiba mais sobre os pipelines de CI/CD e como eles lidam com implantações em ambientes de preparo e produção no Cloud Manager.
exl-id: 7130e5b7-6986-48c8-900c-90f3e4187f91
source-git-commit: 984269e5fe70913644d26e759fa21ccea0536bf4
workflow-type: tm+mt
source-wordcount: '562'
ht-degree: 59%

---


# Pipelines de CI/CD {#ci-cd-pipeline}

Saiba mais sobre os pipelines de CI/CD e como eles lidam com implantações em ambientes de preparo e produção no Cloud Manager.

## Visão geral {#overview}

O [!UICONTROL Cloud Manager] inclui uma estrutura de integração/entrega contínua (CI/CD), que permite que as equipes de implementação testem rapidamente e entreguem códigos novos ou atualizados. As equipes de implementação podem definir, configurar e iniciar um pipeline de CI/CD automatizado. Esse pipeline segue as práticas recomendadas de codificação de Adobe para executar uma verificação de código abrangente e garantir a mais alta qualidade do código.

O pipeline de CI/CD também automatiza processos de teste de unidade e desempenho para aumentar a eficiência da implantação e identificar proativamente problemas críticos que são caros de corrigir após a implantação. As equipes de implementação podem acessar um relatório abrangente de desempenho de código para obter visibilidade sobre o impacto potencial em KPIs e validações críticas de segurança se o código for implantado na produção.

## Sobre o processo de pipeline {#pipeline-process}

O diagrama a seguir ilustra o que acontece quando uma versão é acionada no [!UICONTROL Cloud Manager] usando um pipeline.

![O processo de pipeline](/help/assets/screen_shot_2018-05-30at82457pm.png)

| Etapa do pipeline | Descrição |
| --- | --- |
| 1. Iniciar um lançamento | Um gerente de implantação aciona um lançamento manualmente, com uma confirmação do Git ou com base em uma programação recorrente. |
| 2. Criar uma tag de lançamento | A [!UICONTROL Cloud Manager] cria uma marca Git para marcar o lançamento usando um número de versão gerado automaticamente; por exemplo, `2018.531.245527.0000001222`. |
| 3. Criar lançamento com a versão gerada automaticamente | O [!UICONTROL Cloud Manager] cria o aplicativo com o número de versão atribuído recentemente. |
| 4. Avaliar a qualidade do código | O [!UICONTROL Cloud Manager] verifica o código-fonte e fornece um resumo antes que o código possa ser implantado no ambiente de preparo. |
| 5. Artefatos de versão armazenados | Os artefatos de versão são armazenados para uso posterior nas etapas de implantação. |
| 6. Implantação automática de artefatos no preparo do AEM do AMS | O artefato de lançamento é implantado no ambiente de preparo. |
| 7. Acionar testes automatizados | O [!UICONTROL Cloud Manager] executa testes de desempenho e segurança no artefato. |
| 8. Implantação do acionador de produção | Após a conclusão dos testes automatizados, o [!UICONTROL Cloud Manager] inicia a implantação para produção. |
| 9. O [!UICONTROL Cloud Manager] obtém o(s) artefato(s) para implantar | O [!UICONTROL Cloud Manager] extrai os artefatos de lançamento armazenados. |
| 10. Implantar artefatos para produção | Os artefatos de lançamento são implantados no ambiente de produção. |

### Como configurar um pipeline de CI/CD {#how-to-setup-a-ci-cd-pipeline}

Para saber mais sobre a configuração de pipelines, consulte os documentos [Configuração de pipelines de produção](/help/using/production-pipelines.md) e [Configuração de pipelines de não produção](/help/using/non-production-pipelines.md).

## Portas de qualidade {#quality-gates}

O pipeline de CI/CD fornece portas de qualidade ou critérios de aceitação, que devem ser atendidos antes que o código possa ser movido do ambiente de preparo para o ambiente de implantação. Há três portas no pipeline:

* Qualidade do código
* Teste de desempenho
* Teste de segurança

Para cada uma dessas portas, há três níveis de problemas que podem ser identificados:

* **Crítico**: problemas críticos identificados pela porta causam uma falha imediata do pipeline.
* **Importante**: problemas importantes identificados pela porta fazem com que o pipeline entre em pausa. Um gerente de implantação, gerente de projeto ou proprietário da empresa pode anular os problemas, permitindo que o pipeline continue. Como alternativa, eles podem aceitar os problemas, fazendo com que o pipeline pare com uma falha.
* **Informações**: os problemas de informação identificados pela porta são fornecidos exclusivamente para fins informativos e não têm impacto na execução do pipeline.

Veja a seguir um exemplo de verificação de código com problemas identificados.

![Exemplo de verificação de código](/help/assets/quality-gate-failed.png)

### Como configurar portões {#how-to-setup-gates}

Consulte o documento [Configuração de pipelines de produção](/help/using/production-pipelines.md) para obter detalhes sobre configuração de código, qualidade e portas de desempenho.
