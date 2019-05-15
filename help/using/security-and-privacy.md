---
title: Segurança e privacidade
seo-title: Segurança e privacidade do Gerenciador do AEM Cloud
description: Siga esta página para saber mais sobre a segurança e a privacidade de seus ativos (código/artefatos).
seo-description: Siga esta página para saber mais sobre a segurança e a privacidade de seus ativos (código/artefatos) usando o AEM Cloud Manager.
uuid: 68 bc 2330-a 62 c -4 c 2 c -925 c-daa 6788 b 143 a
contentOwner: jsyal
products: SG_ EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: introdução
discoiquuid: 67 a 54 bae -99 a 9-4405-91 e 3-9 a 0 a 8 b 3 ccc 98
translation-type: tm+mt
source-git-commit: 1dfb065c09569f811e5a006d3d74825d3bd7cc8d

---


# Segurança e privacidade {#security-and-privacy}

[!UICONTROL Cloud Manager] tiver funções pré-configuradas com permissões apropriadas. Por exemplo, um desenvolvedor desenvolve o código e tem a permissão de enviar o código para o **Git Repository**. Como alternativa, um proprietário de negócios tem permissões diferentes permitindo que defina os Indicadores-chave de desempenho (kpis) e aprove implantações.

## Permissões com base em funções {#role-based-permissions}

### Funções de usuário {#user-roles}

O gerenciamento de função é [!UICONTROL Cloud Manager] feito no [Adobe Admin Console](https://helpx.adobe.com/enterprise/using/admin-console.html). Qualquer usuário de [!UICONTROL Cloud Manager] deve ser um membro da Organização IMS do cliente e ter o Contexto do produto Adobe Managed Services. As associações de funções específicas são fornecidas adicionando o usuário a um [!UICONTROL Cloud Manager] Perfil de produto no Console de administração.

Para saber mais sobre como configurar suas funções, consulte [Configuração de usuários e funções](setting-up-users-and-roles.md).

A lista de tabela a seguir define as funções possíveis que podem ser atribuídas no Console de administração.

| **[!UICONTROL Cloud Manager]Função** | **Descrição** |
|---|---|
| Proprietário de negócios | Usuário principal que conclui a [!UICONTROL Cloud Manager] configuração inicial. Responsável pela definição de kpis, aprovação de implantações de produção e substituição de falhas importantes de 3 níveis. |
| Gerenciador de Programas | Usa [!UICONTROL Cloud Manager] para executar configuração de equipe, verificar o status e exibir kpis. Pode aprovar falhas importantes em 3 níveis. |
| Gerenciador de implantação | Gerencia as operações de implantação. Usa [!UICONTROL Cloud Manager] para executar implantações de estágio e produção. Pode aprovar falhas importantes em 3 níveis. Tem acesso ao repositório Git. |
| Desenvolvedor | Desenvolve e teste o código do aplicativo personalizado. Principalmente usa [!UICONTROL Cloud Manager] para exibir o status. Confirmou o acesso ao repositório Git. |
| Engenheiro de sucesso do cliente | Geralmente suporta o sucesso do cliente para clientes do AMS. Interage com [!UICONTROL Cloud Manager] a finalidade de execução de implantações que exigem a supervisão de Engenheiro de sucesso do cliente (CSE). |
| Autor de conteúdo | Geralmente não interage [!UICONTROL Cloud Manager]com. Esse usuário pode usar o [!UICONTROL Cloud Manager] Alternador de Programas (com a partir [!UICONTROL Experience Cloud]de) para acessar o Adobe Experience Manager (AEM). |

### Permissões de usuário {#user-permissions}

Cada uma das funções tem permissões específicas, tarefas pré-definidas ou permissões, associadas a cada função. Esta tabela lista as funções disponíveis e as funções que podem executar a função.

Para saber mais sobre como configurar os usuários, consulte [Configuração de usuários e funções](setting-up-users-and-roles.md).

| Permissão | Descrição | Proprietário de negócios | Gerenciador de implantação | Gerenciador de Programas | Desenvolvedor | CSE |
|--- |--- |--- |--- |--- |--- |--- |
| Ler aplicativo | Consulte detalhes do programa. | x | x | x | x | x |
| Gravar aplicativo | Configurar programa (incluindo kpis). | x |
| Ambiente de leitura | Consulte Detalhes do ambiente. | x | x | x | x | x |
| Criar execução | Iniciar pipeline. | x | x | x |
| Execução de leitura | Consulte status de execução. | x | x | x | x | x |
| Retomar execução | Pode retomar a execução quando pausada. | x | x | x | x |
| Execução de execução na produção | Forneça aprovação do golive. | x | x | x |
| Programação de execução implantada na produção | Programar implantação de produção. | x | x | x | x |
| Execução na produção na produção | Implante o aplicativo na produção quando pausado para a Supervisão CSE. | x |
| Cancelamento da execução | Cancelar execução atual. | x | x | x |
| Falhas na execução de substituição de qualidade de execução | Aprovar falhas importantes no portão de qualidade. | x | x | x |
| Criar pipeline | Configuração/Edição do pipeline. | x |
| Pipeline lido | Consulte Detalhes do pipeline. | x | x | x | x | x |
| Gravação de pipeline | Configuração/Edição do pipeline. | x |
| Pipeline Modifique aprovação | Permite a edição da opção Proprietário do negócio. | x |
| Pipeline Modifique implantação gerenciada | Permite a edição da opção Supervisão CSE. | x |
| Leitura da solução | Leia os kpis do programa. | x | x | x | x | x |
| Gravação de solução | Configurar programa (incluindo kpis) Setup/Edit Pipeline. | x |
| Etapa Ler | Consulte os resultados das métricas de qualidade da etapa. | x | x | x | x | x |

## Isolamento de recursos {#resource-isolation}

Os clientes que usam [!UICONTROL Cloud Manager] precisarão de suas credenciais IMS para autenticação, pois todas as permissões [!UICONTROL Cloud Manager] associadas serão configuradas e associadas à organização IMS. Durante o processo de ativado, a equipe de provisionamento garante que o isolamento de recursos seja aplicado [!UICONTROL Cloud Manager].

## Segurança de dados {#data-security}

O código no [!UICONTROL Cloud Manager] é criptografado em trânsito. Binários que o Cud Manager cria também são criptografados em trafego e criptografados quando armazenados.

Cada cliente recebe seu próprio **Repositório de Git** e seu código é protegido e não compartilhado com outras **Organizações**.

## Privacidade de dados {#data-privacy}

[!UICONTROL Cloud Manager] obedece aos princípios de privacidade definidos pela Adobe. Os desenvolvedores empurram o código de forma segura para o **Git Repository** em HTTPS.

O [! A interface do usuário do DNL (interface do usuário) para [!UICONTROL Cloud Manager]] é construída sobre os serviços que atendem a uma estrutura de controle comum definida pela Adobe. [! A interface do usuário do DNL (interface do usuário) para [!UICONTROL Cloud Manager]] usa serviços seguros de vários provedores de nuvem.
