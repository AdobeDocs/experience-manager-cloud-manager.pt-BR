---
title: Notas da versão 2021.2.0
seo-title: Notas de versão do AEM Cloud Manager para 2021.2.0
description: Siga esta página para obter informações sobre o Cloud Manager Versão 2021.2.0
seo-description: Siga esta página para obter informações sobre o AEM Cloud Manager Versão 2021.2.0
translation-type: tm+mt
source-git-commit: b5233e1932888b515d8dc26a6493cbd26686bc3c
workflow-type: tm+mt
source-wordcount: '244'
ht-degree: 4%

---

# Notas da versão 2021.2.0 {#release-notes-for}

A seção a seguir descreve as Notas de versão gerais para [!UICONTROL Cloud Manager] Versão 2021.2.0.

## Data de lançamento {#release-date}

A Data de lançamento da versão 2021.2.0 é 11 de fevereiro de 2021.[!UICONTROL Cloud Manager]

## Novidades {#whats-new}

* O Arquétipo de projeto AEM usado na Criação de projeto e sandbox foi atualizado para a versão 25.

* A lista de APIs obsoletas identificadas durante a verificação de código foi refinada para incluir classes e métodos adicionais obsoletos nas versões mais recentes do SDK do Cloud Service.

* As implantações de produção agora são implantadas nas instâncias de publicação e dispatcher emparelhadas em paralelo.

* O perfil SonarQube para o Cloud Manager foi atualizado para remover a regra Sonar `squid:S2142`. Isso não entrará mais em conflito com as verificações de interrupção de thread.

* As propriedades definidas nos arquivos `pom.xml` do cliente prefixados com o sonar agora serão removidas dinamicamente para evitar falhas de verificação de qualidade e criação.

* Foram adicionadas Regras de qualidade de código adicionais para cobrir problemas de compatibilidade de Cloud Service.

## Correções de erros {#bug-fixes}

* Ocasionalmente, o pipeline de CI/CD (implantação) falhou durante uma etapa de teste de desempenho devido a um contêiner que executava o teste de carga que encontrou um erro.

* Ocasionalmente, o contêiner de teste de carga pode relatar a execução como falhou, mesmo se apenas uma exceção ocorrer. A falha será relatada somente se o processo de teste não puder ser restaurado.

* Certos erros de correspondência de maiúsculas e minúsculas entre a maneira como os nomes dos ambientes eram armazenados resultariam em falhas no teste de desempenho.

* Algumas falhas de pipeline eram relatadas incorretamente como erros de pipeline.