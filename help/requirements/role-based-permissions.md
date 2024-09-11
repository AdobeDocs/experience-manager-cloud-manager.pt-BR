---
title: Permissões com base em função
description: Saiba mais sobre as permissões pré-configuradas com base em funções do Cloud Manager para gerenciar o acesso aos recursos da nuvem.
exl-id: b66533fb-db93-40e8-919d-581261fdbf24
source-git-commit: 984269e5fe70913644d26e759fa21ccea0536bf4
workflow-type: ht
source-wordcount: '616'
ht-degree: 100%

---


# Permissões baseadas em funções {#role-based-permissions}

O [!UICONTROL Cloud Manager] tem funções pré-configuradas com permissões apropriadas. Por exemplo, um desenvolvedor desenvolve códigos e tem permissão para enviá-los para o repositório Git. Um proprietário de empresa tem permissões diferentes que permitem definir os indicadores principais de desempenho (KPIs) e aprovar implantações.

>[!NOTE]
>
>Esta documentação descreve permissões baseadas em funções do Cloud Manager para Adobe Managed Services (AMS).
>
>Você pode encontrar a documentação equivalente para o AEM as a Cloud Service no documento [Introdução ao Cloud Manager](https://experienceleague.adobe.com/pt-br/docs/experience-manager-cloud-service/content/onboarding/concepts/cloud-manager-introduction#role-based-permissions), presente na documentação do AEM as a Cloud Service.

## Funções do usuário {#user-roles}

O gerenciamento de funções do [!UICONTROL Cloud Manager] é feito usando o [Admin Console](https://helpx.adobe.com/br/enterprise/using/admin-console.html). Todo usuário do [!UICONTROL Cloud Manager] deve ser membro da organização IMS do cliente e ter o Contexto de produto do Adobe Managed Services. As associações de função específicas são fornecidas adicionando o usuário a um perfil de produto do [!UICONTROL Cloud Manager] no Admin Console.

Para saber mais sobre como configurar usuários, consulte [Configuração de usuários e funções](/help/requirements/users-and-roles.md).

A tabela a seguir lista as funções que podem ser atribuídas no Admin Console.

| Função no [!UICONTROL Cloud Manager] | Descrição |
|---|---|
| Proprietário da empresa | O usuário principal que conclui a configuração inicial do [!UICONTROL Cloud Manager] e é responsável por definir KPIs, aprovar implantações de produção e neutralizar falhas importantes de nível 3 quando necessário. |
| Autor de conteúdo | Geralmente não interage com o Cloud Manager, mas pode usar o seletor de programa do Cloud Manager (navegando a partir da Experience Cloud) para acessar o Adobe Experience Manager (AEM). |
| Engenheiro de sucesso do cliente (CSE) | Oferece suporte principalmente ao sucesso do cliente do AMS e interage com o [!UICONTROL Cloud Manager] para executar implantações. Essas implantações exigem a supervisão de um Engenheiro de sucesso do cliente (CSE) da Adobe. |
| Gerenciador de implantação | Gerencia as operações de implantação usando o [!UICONTROL Cloud Manager] para executar implantações de preparo e produção, pode aprovar falhas importantes de nível 3 quando necessário e tem acesso ao repositório Git. |
| Desenvolvedor | Desenvolve e testa o código de aplicativo personalizado, usa principalmente o [!UICONTROL Cloud Manager] para exibir o status da implantação e tem acesso de confirmação ao repositório Git. |
| Gerenciador de programas | Usa o [!UICONTROL Cloud Manager] para configurar a equipe, revisar o status, exibir KPIs e aprovar falhas importantes de nível 3, quando necessário. |

## Permissões de usuário {#user-permissions}

Cada uma das funções tem permissões pré-configuradas associadas específicas. A tabela a seguir lista as permissões disponíveis e as funções que podem executá-las.

| Permissão | Descrição | Proprietário da empresa | Gerenciador de implantação | Gerenciador de programas | Desenvolvedor | CSE |
| --- | --- | --- | --- | --- | --- | --- |
| Aplicativo de leitura | KPIs do programa de leitura | x | x | x | x | x |
| Aplicativo de gravação | Configuração ou edição do programa | x | | | | |
| Adicionar programa | Adicionar novo programa | x | | | | |
| Ambiente de leitura | Ver detalhes do ambiente | x | x | x | x | x |
| Criar execução | Iniciar pipeline | x | x | x | | |
| Execução de leitura | Ver status de execução | x | x | x | x | x |
| Retomar execução | Capacidade de retomar a execução ao pausar | x | x | x | | x |
| Aprovação da execução da implantação para produção | Fornecer aprovação em tempo real | x | x | x | | |
| Implantação do cronograma de execução para produção | Programar implantação de produção | x | x | x | | x |
| Implantação de Execução para Produção | Implantar aplicativo para produção quando pausado para supervisão do CSE | | | | | x |
| Cancelamento de execuções | Cancelar a execução atual | | | x | | |
| Falhas na porta de qualidade de substituição de execução | Aprovar falhas importantes na porta de qualidade | x | x | x | | |
| Criação de pipeline | Configurar/editar pipeline | | x | | | |
| Leitura do pipeline | Ver detalhes do pipeline | x | x | x | x | x |
| Gravação do pipeline | Configurar/editar pipeline | | x | | | |
| Aprovação de modificação de pipeline | Permite editar a opção Proprietário do negócio | | x | | | |
| Implementação gerenciada de modificação de pipeline | Permite a edição da opção de supervisão do CSE | | x | | | |
| Exclusão de pipeline | Permite a exclusão do pipeline | | x | | | |
| Leitura da etapa | Ver os resultados das métricas de qualidade da etapa | x | x | x | x | x |
| Gerar token de acesso pessoal | Acessar Git | | x | | x | |

Para saber mais sobre como configurar usuários, consulte [Configuração de usuários e funções](/help/requirements/users-and-roles.md).

>[!TIP]
>
>Também estão disponíveis perfis personalizados com permissões configuráveis. Consulte [Permissões personalizadas](/help/using/custom-permissions.md) para obter mais detalhes.
