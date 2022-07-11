---
title: Permissões com base em função
description: Saiba mais sobre as permissões pré-configuradas com base em funções do Cloud Manager para gerenciar o acesso aos recursos da nuvem.
exl-id: b66533fb-db93-40e8-919d-581261fdbf24
source-git-commit: 522e5fbc650a8159602eb1aeaf42d64f4e23e8b4
workflow-type: tm+mt
source-wordcount: '539'
ht-degree: 16%

---


# Permissões baseadas em função {#role-based-permissions}

[!UICONTROL Cloud Manager] O tem funções pré-configuradas com permissões apropriadas. Por exemplo, um desenvolvedor desenvolve código e tem permissão para enviar o código para o repositório Git. Um proprietário de negócios tem permissões diferentes que permitem definir os KPIs (indicadores-chave de desempenho) e aprovar implantações.

## Funções de usuário {#user-roles}

Gerenciamento de funções para [!UICONTROL Cloud Manager] é feito usando o [Admin Console.](https://helpx.adobe.com/br/enterprise/using/admin-console.html) Qualquer usuário de [!UICONTROL Cloud Manager] deve ser membro da organização IMS do cliente e ter o Contexto de produto do Adobe Managed Services. Associações de função específicas são fornecidas adicionando o usuário a um [!UICONTROL Cloud Manager] perfil de produto no Admin Console.

Para saber mais sobre como configurar suas funções, consulte o documento [Configurando usuários e funções.](/help/requirements/users-and-roles.md)

Esta tabela lista as funções que podem ser atribuídas no Admin Console.

| [!UICONTROL Cloud Manager] Função | Descrição |
|---|---|
| Proprietário da empresa | Esse é o usuário principal que conclui o [!UICONTROL Cloud Manager] e é responsável por definir KPIs, aprovar implantações de produção e substituir falhas importantes de 3 camadas quando necessário. |
| Gerenciador de programas | Esse usuário usa [!UICONTROL Cloud Manager] para executar a configuração da equipe, revise o status, exiba KPIs e pode aprovar falhas importantes de três níveis, quando necessário. |
| Gerenciador de implantação | Este usuário gerencia as operações de implantação usando [!UICONTROL Cloud Manager] para executar implantações de estágio e produção, pode aprovar falhas importantes de 3 camadas quando necessário e tem acesso ao repositório Git. |
| Desenvolvedor | Esse usuário desenvolve e testa o código de aplicativo personalizado, usa principalmente [!UICONTROL Cloud Manager] para exibir o status da implantação e tem acesso de confirmação ao repositório git. |
| Engenheiro de Sucesso do Cliente | Esse usuário geralmente oferece suporte ao sucesso do cliente para clientes do AMS e interage com o [!UICONTROL Cloud Manager] para executar implantações que exigem a supervisão do CSE (Customer Success Engineer, engenheiro de sucesso do cliente). |
| Autor de conteúdo | Esse usuário geralmente não interage com [!UICONTROL Cloud Manager], mas pode usar o [!UICONTROL Cloud Manager] wwitcher do programa (tendo navegado de [!UICONTROL Experience Cloud]) para acessar o Adobe Experience Manager (AEM). |

## Permissões de usuário {#user-permissions}

Cada uma das funções tem permissões pré-configuradas associadas específicas. Esta tabela lista as permissões disponíveis e as funções que podem executá-las.


| Permissão | Descrição | Proprietário da empresa | Gerenciador de implantação | Gerenciador de programas | Desenvolvedor | CSE |
|--- |--- |--- |--- |--- |--- |--- |
| Ler Aplicativo | Ler KPIs do programa | x | x | x | x | x |
| Gravar aplicativo | Configuração ou edição do programa | x |  |  |  |  |
| Adicionar programa | Adicionar novo programa | x |  |  |  |  |
| Ambiente de leitura | Veja os detalhes do ambiente | x | x | x | x | x |
| Criar Execução | Iniciar pipeline | x | x | x |  |  |
| Execução de Leitura | Consulte status de execução | x | x | x | x | x |
| Retomar Execução | Pode retomar a execução quando pausado | x | x | x |  | x |
| Execução Aprovar implantação para produção | Fornecer aprovação ao vivo | x | x | x |  |  |
| Implantação do agendamento de execução para produção | Agendar implantação de produção | x | x | x |  | x |
| Implementação para produção | Implantar aplicativo para produção quando pausado para supervisão CSE |  |  |  |  | x |
| Cancelamento de execução | Cancelar execução atual |  |  | x |  |  |
| Falhas no Portão de Qualidade de Substituição de Execução | Aprovar falhas importantes na porta de qualidade | x | x | x |  |  |
| Criação de pipeline | Configurar / editar pipeline |  | x |  |  |  |
| Leitura do pipeline | Veja os detalhes do pipeline | x | x | x | x | x |
| Gravação do pipeline | Configurar / editar pipeline. |  | x |  |  |  |
| Modificação de pipeline aprovação | Permite editar a opção Proprietário comercial |  | x |  |  |  |
| Modificação de pipeline da implantação gerenciada | Permite a edição da opção de supervisão CSE |  | x |  |  |  |
| Exclusão de pipeline | Permite a exclusão de pipeline |  | x |  |  |  |
| Leitura da etapa | Veja os resultados das métricas de qualidade da etapa | x | x | x | x | x |
| Gerar Token de Acesso Pessoal | Git de acesso |  | x |  | x |  |

Para saber mais sobre como configurar seus usuários, consulte o documento [Configurando usuários e funções.](/help/requirements/users-and-roles.md)
