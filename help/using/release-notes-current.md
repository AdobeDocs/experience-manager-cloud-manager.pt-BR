---
title: Notas da versão 2021.2.0
seo-title: Notas de versão do AEM Cloud Manager para 2021.2.0
description: Siga esta página para obter informações sobre a versão 2021.2.0 do Cloud Manager
seo-description: Siga esta página para obter informações sobre a versão 2021.2.0 do AEM Cloud Manager
translation-type: tm+mt
source-git-commit: 02d2f91d97847a1ca512c2e0f4e02274e79951de
workflow-type: tm+mt
source-wordcount: '231'
ht-degree: 5%

---

# Notas da versão 2021.2.0 {#release-notes-for}

A seção a seguir descreve as Notas de versão gerais da [!UICONTROL Cloud Manager] Versão 2021.2.0.

## Data de lançamento {#release-date}

A data de lançamento da versão 2021.2.0 [!UICONTROL Cloud Manager] é 11 de fevereiro de 2021.

## Novidades {#whats-new}

* O AEM Project Archetype usado em Projeto e criação de caixa de proteção foi atualizado para a versão 25.

* A lista de APIs obsoletas identificadas durante a digitalização de código foi refinada para incluir classes e métodos adicionais obsoletos nas versões mais recentes do Cloud Service SDK.

* As implantações de produção agora implantam nas instâncias de publicação e despachante emparelhadas em paralelo.

* O perfil SonarQube para o Cloud Manager foi atualizado para remover a regra Sonar `squid:S2142`. Isso não entrará em conflito com as verificações de interrupção de thread.

* As propriedades definidas nos arquivos `pom.xml` do cliente prefixados com o sonar agora serão removidas dinamicamente para evitar falhas de compilação e verificação de qualidade.

## Correções de erros {#bug-fixes}

* Ocasionalmente, o pipeline CI/CD (implantação) falhou durante uma etapa de teste de desempenho devido a um container que executava o teste de carga que encontrou um erro.

* Ocasionalmente, o container de teste de carga pode relatar a execução como com falha mesmo se apenas uma exceção ocorrer. A falha será relatada somente se o processo de teste não puder ser restaurado.

* Alguns erros de correspondência entre a forma como os nomes dos ambientes são armazenados resultariam em falhas no teste de desempenho.

* Algumas falhas de pipeline foram relatadas incorretamente como erros de pipeline.