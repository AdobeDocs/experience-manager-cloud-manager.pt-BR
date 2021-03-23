---
title: Permissões baseadas em função
description: Siga esta página para saber mais sobre Permissões baseadas em funções.
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: introduction
discoiquuid: 67a54bae-99a9-4405-91e3-9a0a8b3ccc98
feature: Funções de usuário
translation-type: tm+mt
source-git-commit: fb10d775c930b5bb475b497aac2fd59b053a9a00
workflow-type: tm+mt
source-wordcount: '519'
ht-degree: 19%

---


# Permissões baseadas em função {#role-based-permissions}

[!UICONTROL Cloud Manager] O tem funções pré-configuradas com permissões apropriadas. Por exemplo, um desenvolvedor desenvolve código e tem permissão para enviar o código para o **Repositório Git**. Como alternativa, um proprietário de negócios tem permissões diferentes que permitem definir os Indicadores-chave de desempenho (KPIs) e aprovar implantações.

## Funções de usuário {#user-roles}

O gerenciamento de funções para [!UICONTROL Cloud Manager] é feito dentro do [Adobe Admin Console](https://helpx.adobe.com/br/enterprise/using/admin-console.html). Qualquer usuário de [!UICONTROL Cloud Manager] deve ser membro da Organização IMS do cliente e ter o Contexto de Produto dos Serviços Gerenciados da Adobe. Associações de função específicas são fornecidas adicionando o usuário a um [!UICONTROL Cloud Manager] Perfil de produto no Admin Console.

Para saber mais sobre como configurar suas funções, consulte [Configuração de usuários e funções](setting-up-users-and-roles.md).

A lista da tabela a seguir define as possíveis funções que você pode atribuir no Admin Console.

| **[!UICONTROL Cloud Manager]Função** | **Descrição** |
|---|---|
| Proprietário da empresa | Usuário principal que conclui a configuração inicial [!UICONTROL Cloud Manager]. Responsável por definir KPIs, aprovar implantações de produção e substituir falhas importantes de três níveis. |
| Gerenciador de programas | Usa [!UICONTROL Cloud Manager] para executar a configuração da equipe, revisar o status e exibir KPIs. Pode aprovar falhas importantes de três níveis. |
| Gerenciador de implantação | Gerencia as operações de implantação. Usa [!UICONTROL Cloud Manager] para executar implantações de estágio e produção. Pode aprovar falhas importantes de três níveis. Tem acesso ao repositório Git. |
| Desenvolvedor | Desenvolve e testa o código de aplicativo personalizado. Usa principalmente [!UICONTROL Cloud Manager] para visualizar o status. Tem acesso de confirmação ao repositório Git. |
| Engenheiro de Sucesso do Cliente | Geralmente oferece suporte ao sucesso do cliente para clientes do AMS. Interage com [!UICONTROL Cloud Manager] para fins de execução de implantações que exigem a supervisão do CSE (Customer Success Engineer, engenheiro de sucesso do cliente). |
| Autor do conteúdo | Geralmente não interage com [!UICONTROL Cloud Manager]. Este usuário pode usar o [!UICONTROL Cloud Manager] Seletor de programa (navegando de [!UICONTROL Experience Cloud]) para acessar o Adobe Experience Manager (AEM). |

## Permissões de usuário {#user-permissions}

Cada função está associada a permissões específicas, tarefas pré-configuradas ou permissões. Essa tabela lista as funções disponíveis e as funções que podem executar a função.

Para saber mais sobre como configurar seus usuários, consulte [Configuração de usuários e funções](setting-up-users-and-roles.md).

| Permissão | Descrição | Proprietário da empresa | Gerenciador de implantação | Gerenciador de programas | Desenvolvedor | CSE |
|--- |--- |--- |--- |--- |--- |--- |
| Ler Aplicativo | Leia os KPIs do programa. | x | x | x | x | x |
| Gravar aplicativo | Configuração ou edição do programa. | x |  |  |  |  |
| Adicionar programa | Adicionar novo programa. | x |  |  |  |  |
| Ambiente de leitura | Consulte Detalhes do ambiente . | x | x | x | x | x |
| Criar Execução | Inicie o pipeline. | x | x | x |  |  |
| Execução de Leitura | Consulte status de execução. | x | x | x | x | x |
| Retomar Execução | Pode retomar a execução quando pausado. | x | x | x |  | x |
| Execução Aprovar implantação para produção | Forneça Aprovação De GoLive. | x | x | x |  |  |
| Implantação do agendamento de execução para produção | Agendar implantação de produção. | x | x | x |  | x |
| Implementação para produção | Implante o aplicativo para produção quando pausado para CSE Oversight. |  |  |  |  | x |
| Cancelamento de execução | Cancelar a execução atual. |  |  | x |  |  |
| Falhas no Portão de Qualidade de Substituição de Execução | Aprove Falhas Importantes No Portão De Qualidade. | x | x | x |  |  |
| Criação de pipeline | Configurar/editar pipeline. |  | x |  |  |  |
| Leitura do pipeline | Consulte Detalhes do pipeline. | x | x | x | x | x |
| Gravação do pipeline | Configurar/editar pipeline. |  | x |  |  |  |
| Modificação de pipeline aprovação | Permite editar a opção Proprietário comercial. |  | x |  |  |  |
| Modificação de pipeline da implantação gerenciada | Permite a edição da opção de Superintendência de CSE. |  | x |  |  |  |
| Exclusão de pipeline | Permite a exclusão de um pipeline. |  | x |  |  |  |
| Leitura da etapa | Veja os resultados das métricas de qualidade da etapa. | x | x | x | x | x |
| Gerar Token de Acesso Pessoal | Acesse o Git. |  | x |  | x |  |

