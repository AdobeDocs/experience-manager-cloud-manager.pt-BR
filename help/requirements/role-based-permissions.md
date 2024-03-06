---
title: Permissões com base em função
description: Saiba mais sobre as permissões pré-configuradas com base em funções do Cloud Manager para gerenciar o acesso aos recursos da nuvem.
exl-id: b66533fb-db93-40e8-919d-581261fdbf24
source-git-commit: 10297789ac8f905f242ac52bdc6fc4812b989e8a
workflow-type: tm+mt
source-wordcount: '602'
ht-degree: 93%

---


# Permissões baseadas em função {#role-based-permissions}

O [!UICONTROL Cloud Manager] tem funções pré-configuradas com permissões apropriadas. Por exemplo, um desenvolvedor desenvolve código e tem permissão para enviar o código para o repositório Git. Um proprietário de empresa tem permissões diferentes que permitem definir os KPIs (indicadores-chave de desempenho) e aprovar implantações.

>[!NOTE]
>
>Esta documentação descreve as permissões com base em funções do Cloud Manager para Adobe Managed Services (AMS).
>
>A documentação equivalente para o AEM as a Cloud Service pode ser encontrada no documento [Introdução ao Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/concepts/cloud-manager-introduction.html#role-based-permissions) na documentação as a Cloud Service do AEM.

## Funções de usuário {#user-roles}

O gerenciamento de funções do [!UICONTROL Cloud Manager] é feito usando o [Admin Console.](https://helpx.adobe.com/br/enterprise/using/admin-console.html) Qualquer usuário do [!UICONTROL Cloud Manager] deve ser membro da organização IMS do cliente e ter o Contexto de produto do Adobe Managed Services. Aa associações de função específicas são fornecidas adicionando o usuário a um perfil de produto do [!UICONTROL Cloud Manager] no Admin Console.

Para saber mais sobre como configurar suas funções, consulte o documento [Configuração de usuários e funções.](/help/requirements/users-and-roles.md)

Esta tabela lista as funções que podem ser atribuídas no Admin Console.

| Função no [!UICONTROL Cloud Manager] | Descrição |
|---|---|
| Proprietário da empresa | Esse é o usuário principal que conclui a configuração inicial do [!UICONTROL Cloud Manager] e é responsável por definir KPIs, aprovar implantações de produção e substituir falhas importantes de nível 3 quando necessário. |
| Gerenciador de programas | Esse usuário usa o [!UICONTROL Cloud Manager] para executar a configuração da equipe, revisar o status, exibir KPIs e aprovar falhas importantes de nível 3, quando necessário. |
| Gerenciador de implantação | Este usuário gerencia as operações de implantação usando o [!UICONTROL Cloud Manager] para executar implantações de estágio e produção, pode aprovar falhas importantes de nível 3 quando necessário, com acesso ao repositório Git. |
| Desenvolvedor | Esse usuário desenvolve e testa o código de aplicativo personalizado, usa principalmente o [!UICONTROL Cloud Manager] para exibir o status da implantação e tem acesso de confirmação ao repositório git. |
| Engenheiro de sucesso do cliente | Esse usuário geralmente oferece suporte ao sucesso do cliente para clientes do AMS e interage com o [!UICONTROL Cloud Manager] com o propósito de executar implantações que exigem a supervisão do CSE (Engenheiro de sucesso do cliente). |
| Autor de conteúdo | Esse usuário geralmente não interage com o [!UICONTROL Cloud Manager], mas pode usar o programa para alternar do [!UICONTROL Cloud Manager] (tendo navegado pela [!UICONTROL Experience Cloud]) para acessar o Adobe Experience Manager (AEM). |

## Permissões de usuário {#user-permissions}

Cada uma das funções tem permissões pré-configuradas associadas específicas. Esta tabela lista as permissões disponíveis e as funções que podem executá-las.


| Permissão | Descrição | Proprietário da empresa | Gerente de implantação | Gerente de programas | Desenvolvedor | CSE |
|--- |--- |--- |--- |--- |--- |--- |
| Aplicativo de leitura | KPIs do programa de leitura | x | x | x | x | x |
| Aplicativo de gravação | Configuração ou edição do programa | x |  |  |  |  |
| Adicionar programa | Adicionar novo programa | x |  |  |  |  |
| Ambiente de leitura | Ver detalhes do ambiente | x | x | x | x | x |
| Criar execução | Iniciar pipeline | x | x | x |  |  |
| Execução de leitura | Ver status de execução | x | x | x | x | x |
| Retomar execução | Pode retomar a execução quando pausado | x | x | x |  | x |
| Aprovação da execução da implantação para produção | Fornecer aprovação em tempo real | x | x | x |  |  |
| Implantação do cronograma de execução para produção | Programar implantação de produção | x | x | x |  | x |
| Implantação de Execução para Produção | Implantar aplicativo para produção quando pausado para supervisão do CSE |  |  |  |  | x |
| Cancelamento de execuções | Cancelar a execução atual |  |  | x |  |  |
| Falhas na porta de qualidade de substituição de execução | Aprovar falhas importantes na porta de qualidade | x | x | x |  |  |
| Criação de pipeline | Configurar/editar pipeline |  | x |  |  |  |
| Leitura do pipeline | Ver detalhes do pipeline | x | x | x | x | x |
| Gravação do pipeline | Configurar/editar pipeline. |  | x |  |  |  |
| Aprovação de modificação de pipeline | Permite editar a opção Proprietário do negócio |  | x |  |  |  |
| Implementação gerenciada de modificação de pipeline | Permite a edição da opção de supervisão do CSE |  | x |  |  |  |
| Exclusão de pipeline | Permite a exclusão do pipeline |  | x |  |  |  |
| Leitura da etapa | Ver os resultados das métricas de qualidade da etapa | x | x | x | x | x |
| Gerar token de acesso pessoal | Acesso ao Git |  | x |  | x |  |

Para saber mais sobre como configurar seus usuários, consulte o documento [Configuração de usuários e funções.](/help/requirements/users-and-roles.md)
