---
title: Permissões baseadas em função
description: Siga esta página para saber mais sobre Permissões baseadas em funções.
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: introduction
discoiquuid: 67a54bae-99a9-4405-91e3-9a0a8b3ccc98
translation-type: tm+mt
source-git-commit: 9cbe8f58cf04001ba9851ba321f03c7687e58014

---


# Permissões baseadas em função {#role-based-permissions}

[!UICONTROL Cloud Manager] tem funções pré-configuradas com permissões apropriadas. Por exemplo, um desenvolvedor desenvolve código e tem permissão para enviar o código para o Repositório **Git**. Como alternativa, um proprietário de negócios tem permissões diferentes que permitem definir os Indicadores-chave de desempenho (KPIs) e aprovar implantações.

## Funções de usuário {#user-roles}

O gerenciamento de funções para [!UICONTROL Cloud Manager] é feito dentro do [Adobe Admin Console](https://helpx.adobe.com/br/enterprise/using/admin-console.html). Qualquer usuário do deve [!UICONTROL Cloud Manager] ser membro da Organização IMS do cliente e ter o Contexto de produto do Adobe Managed Services. Associações de função específicas são fornecidas adicionando o usuário a um Perfil [!UICONTROL Cloud Manager] de Produto no Admin Console.

Para saber mais sobre como configurar suas funções, consulte [Configuração de usuários e funções](setting-up-users-and-roles.md).

A lista de tabela a seguir define as possíveis funções que você pode atribuir no Admin Console.

| **[!UICONTROL Cloud Manager]Função ** | **Descrição** |
|---|---|
| Proprietário da empresa | Usuário principal que conclui a [!UICONTROL Cloud Manager] configuração inicial. Responsável por definir KPIs, aprovar implantações de produção e substituir falhas importantes de 3 níveis. |
| Gerenciador de programas | Usa [!UICONTROL Cloud Manager] para executar a configuração do grupo, verificar o status e visualização de KPIs. Pode aprovar falhas importantes de 3 níveis. |
| Gerenciador de implantação | Gerencia as operações de implantação. Usa [!UICONTROL Cloud Manager] para executar implantações de estágio e produção. Pode aprovar falhas importantes de 3 níveis. Tem acesso ao repositório Git. |
| Desenvolvedor | Desenvolve e testa o código personalizado do aplicativo. Usa principalmente [!UICONTROL Cloud Manager] para status de visualização. Tem acesso de confirmação ao repositório Git. |
| Engenheiro de sucesso do cliente | Geralmente oferece suporte ao sucesso do cliente para clientes AMS. Interage com [!UICONTROL Cloud Manager] a finalidade de executar implantações que exigem a supervisão do CSE (Customer Success Engineer). |
| Autor de conteúdo | Geralmente não interage com [!UICONTROL Cloud Manager]. Esse usuário pode usar o Comutador de [!UICONTROL Cloud Manager] Programas (que navegou de [!UICONTROL Experience Cloud]) para acessar o Adobe Experience Manager (AEM). |

## Permissões de usuário {#user-permissions}

Cada uma das funções tem permissões específicas, tarefas pré-configuradas ou permissões associadas a cada função. Esta tabela lista as funções disponíveis e as funções que podem executar a função.

Para saber mais sobre como configurar seus usuários, consulte [Configuração de usuários e funções](setting-up-users-and-roles.md).

| Permissão | Descrição | Proprietário da empresa | Gerenciador de implantação | Gerenciador de programas | Desenvolvedor | CSE |
|--- |--- |--- |--- |--- |--- |--- |
| Ler aplicativo | Leia os KPIs do Programa. | x | x | x | x | x |
| Aplicativo de gravação | Configuração ou edição do Programa. | x |  |  |  |  |
| Adicionar Programa | Adicionar novo Programa. | x |  |  |  |  |
| Ler Ambiente | Consulte os detalhes do Ambiente. | x | x | x | x | x |
| Criar execução | Start Pipeline. | x | x | x |  |  |
| Execução de leitura | Consulte status de execução. | x | x | x | x | x |
| Retomar execução | Pode retomar a execução quando pausada. | x | x | x |  | x |
| Execução Aprovar implantação para produção | Fornecer aprovação do GoLive. | x | x | x |  |  |
| Implementação da Programação de Execução para Produção | Agendar implantação de produção. | x | x | x |  | x |
| Implementação para produção | Implante o aplicativo para a produção quando pausado para o CSE Oversight. |  |  |  |  | x |
| Cancelamento de execução | Cancelar a execução atual. |  |  | x |  |  |
| Falhas na Porta de Qualidade de Substituição de Execução | Aprovar Falhas Importantes Do Portão De Qualidade. | x | x | x |  |  |
| Criação de Pipeline | Configuração / Editar Pipeline. |  | x |  |  |  |
| Leitura do Pipeline | Consulte Detalhes do pipeline. | x | x | x | x | x |
| Gravação de Pipeline | Configuração / Editar Pipeline. |  | x |  |  |  |
| Modificação de Pipeline Aprovação | Permite a edição da opção Proprietário da empresa. |  | x |  |  |  |
| Implantação gerenciada de modificação de pipeline | Permite a edição da opção Superintendência de CSE. |  | x |  |  |  |
| Exclusão de Pipeline | Permite a exclusão de um Pipeline. |  | x |  |  |  |
| Leitura da etapa | Consulte os resultados das métricas de qualidade da etapa. | x | x | x | x | x |
| Gerar Token de acesso pessoal | Git de acesso. |  | x |  | x |  |

