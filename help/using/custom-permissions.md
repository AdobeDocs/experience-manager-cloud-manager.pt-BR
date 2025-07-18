---
title: Permissões personalizadas
description: Saiba como usar permissões personalizadas para criar novos perfis de permissão personalizados com permissões configuráveis e restringir o acesso a programas, pipelines e ambientes para usuários do Cloud Manager.
exl-id: a81eda9f-aa89-40ea-8e4c-52367a0a6aba
source-git-commit: fb3c2b3450cfbbd402e9e0635b7ae1bd71ce0501
workflow-type: tm+mt
source-wordcount: '1373'
ht-degree: 98%

---

# Permissões personalizadas {#custom-permissions}

Saiba como usar permissões personalizadas para criar novos perfis de permissão personalizados com permissões configuráveis e restringir o acesso a programas, pipelines e ambientes para usuários do Cloud Manager.

## Introdução {#introduction}

O Cloud Manager possui um conjunto de funções predefinidas que controlam o acesso a vários de seus recursos:

* Proprietário da empresa
* Gerenciador de programas
* Gerenciador de implantação
* Desenvolvedor

As permissões personalizadas permitem que usuários criem novos perfis com permissões configuráveis para restringir o acesso de usuários do Cloud Manager a programas, pipelines e ambientes.

>[!TIP]
>
>Para obter detalhes sobre funções predefinidas, consulte [Permissões baseadas em funções](/help/requirements/role-based-permissions.md).

## Usar permissões personalizadas {#using}

Criar e usar suas próprias permissões personalizadas requer estas três etapas:

1. [Criar um novo perfil de produto](#create).
1. [Atribuir permissões personalizadas ao novo perfil de produto](#assign-permissions).
1. [Atribuir usuários ao novo perfil de produto](#assign-users).

Esta seção detalha essas etapas. Talvez seja útil consultar as sessões [Termos](#terms) e [Permissões configuráveis](#configurable-permissions) ao criar permissões personalizadas.

>[!NOTE]
>
>Você deve ter direitos de administrador de produto no Admin Console para criar novos perfis e gerenciar permissões no Cloud Manager.

### Criar um novo perfil de produto {#create}

Primeiro crie um novo perfil de produto, ao qual poderá atribuir permissões personalizadas.

1. Faça logon no Cloud Manager em [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)

1. Selecione o produto **AEM Managed Services**.

1. Pesquise uma instância com um nome correspondente ao padrão `*-cloud-manager` e clique para gerenciar usuários e permissões.

1. Você será redirecionado(a) para a guia **Produtos** do Admin Console, onde é possível gerenciar usuários e permissões do Cloud Manager. No Admin Console, clique em **Novo Perfil**.

![Botão Novo perfil](/help/assets/admin-console-new-profile.png)

1. Forneça os detalhes gerais sobre o perfil.

   * **Nome do perfil de produto**: um nome descritivo para o perfil
   * **Nome de exibição**: um nome abreviado que é mostrado na interface (opções)
   * **Descrição**: uma descrição informativa do perfil que explique sua finalidade (opcional)
   * **Notificar usuários por email**: ao selecionar esta opção, os usuários serão notificados por email quando forem adicionados ou removidos deste perfil.

1. Clique em **Salvar**.

O novo perfil de produto é salvo e torna-se visível na lista de perfis de produto no Admin Console.

### Atribuir permissões personalizadas ao novo perfil de produto {#assign-permissions}

Agora que você tem um novo perfil de produto, é possível atribuir permissões personalizadas.

1. No Admin Console, clique no nome do [novo perfil de produto recém-criado](#create).

1. Na janela aberta, selecione a guia **Permissões** para exibir uma lista de permissões editáveis.

   ![Permissões editáveis](/help/assets/permissions-tab.png)

1. Clique no link **Editar** para obter permissão de edição.

1. A janela **Editar permissões** é aberta.
   * A permissão selecionada na etapa anterior é selecionada na coluna à esquerda.
   * Os itens de permissão disponíveis para atribuição estão na coluna do meio rotulada **Itens de permissão disponíveis**.
   * Os itens de permissões atribuídos estão na coluna à direita rotulada **Itens de permissão incluídos**.

   ![Editar itens de permissão](/help/assets/edit-permission-items.png)

1. Clique no ícone de mais (`+`) próximo ao item de permissão para adicioná-lo à coluna **Itens de permissão inclusos**. Se necessário, clique no ícone `i` próximo a um item de permissão para obter mais informações.

1. Na parte superior da coluna **Permissões disponíveis**, clique em **Adicionar tudo** para adicionar todas as permissões. Da mesma forma, clique em **Remover tudo** para remover todas as permissões selecionadas anteriormente.

1. Clique em **Salvar** quando terminar de definir os itens de permissão para o novo perfil de produto.

O novo perfil de produto é salvo com as permissões personalizadas.

### Atribuir usuários ao novo perfil de produto {#assign-users}

Agora é possível atribuir usuários ao novo perfil de produto criado com permissões personalizadas.

1. No Admin Console, clique no nome do [novo perfil de produto ao qual você atribuiu permissões personalizadas](#assign-permissions).

1. Na janela aberta, selecione a guia **Usuários**.

1. Clique em **Adicionar usuários** e atribua usuários ao novo perfil de produto com permissões personalizadas.

Consulte a seção **Adicionar usuários e grupos de usuários a um perfil de produto** do documento [Gerenciar perfis de produto para usuários corporativos](https://helpx.adobe.com/br/enterprise/using/manage-product-profiles.html) para obter mais detalhes sobre como usar o Admin Console.

## Permissões configuráveis {#configurable-permissions}

As seguintes permissões estão disponíveis para criar perfis personalizados.

| Permissão | Descrição |
| --- | --- |
| `Program Access` | Permitir que usuários acessem programas |
| `Program Edit` | Permitir que usuários editem programas |
| `Pipeline Create` | Permitir que usuários criem novos pipelines |
| `Pipeline Delete` | Permitir que usuários excluam pipelines |
| `Pipeline Edit` | Permitir que usuários editem pipelines |
| `Production Deployments Approve/Reject` | Permitir que usuários aprovem ou rejeitem uma etapa de implantação de produção |
| `Pipeline Executions Cancel` | Permitir que usuários cancelem execuções de pipeline |
| `Pipeline Executions Start` | Permitir que usuários iniciem novas execuções de pipeline |
| `Override/Reject Important Metric Failures` | Permitir que usuários ignorem ou rejeitem falhas de métrica importantes |
| `Production Deployments Schedule` | Permitir que usuários programem uma etapa de implantação de produção |
| `Repository Info Access` | Permitir que os usuários acessem as informações do repositório e gerem uma senha de acesso |
| `Repository Create` | Permitir que usuários criem novos repositórios Git |
| `Repository Delete` | Permitir que usuários excluam repositórios Git |
| `Repository Edit` | Permitir que os usuários editem repositórios Git |
| `Repository Code Generate` | Permitir que usuários gerem projetos a partir do arquétipo |
| `Content Copy Manage` | Permitir que usuários gerenciem operações de cópia do conteúdo |

### Permissões no nível da organização {#organization-level}

As permissões no nível da organização são sempre aplicadas em todos os programas de uma organização.

Um exemplo de permissão no nível da organização no Cloud Manager é o **Acesso às informações do repositório**. Essa permissão permite que os usuários gerem um nome de usuário, uma senha e um URL do repositório para acessar e contribuir para projetos de clientes. Embora o nome de usuário e a senha permaneçam consistentes em todos os repositórios da organização, cada programa tem um URL de repositório exclusivo.

Consulte o documento [Repositório de código-fonte](/help/requirements/source-code-repository.md) para mais informações.

## Termos {#terms}

Os termos a seguir são usados na criação e no gerenciamento de permissões personalizadas e funções predefinidas.

| Termo | Descrição |
| --- | --- |
| Permissões predefinidas | Funções predefinidas, como **Proprietário da empresa**, **Gerente de implantação** etc. para controlar vários recursos do Cloud Manager. Para mais detalhes sobre funções predefinidas, consulte [Permissões baseadas em funções](/help/requirements/role-based-permissions.md). |
| Permissões personalizadas | Recursos do Cloud Manager que permitem que os usuários criem perfis de permissão para definir funções de controle dos recursos compatíveis do Cloud Manager |
| Perfil de permissão | Criado no Admin Console para gerenciar permissões configuráveis que são aplicáveis a usuários que fazem parte do perfil de permissão |
| Permissão configurável | Permissões do Cloud Manager que podem ser configuradas no perfil de permissão |
| Item de permissão | Um recurso do programa, ambiente ou pipeline no qual uma permissão pode ser aplicada |

Os itens de permissão referem-se ao escopo de aplicação das permissões. Normalmente, é um dos seguintes.

| Tipo de item de permissão | Exemplo | Descrição |
| --- | --- | --- |
| Organização | organização:empresaA | Todos os recursos aplicáveis de uma organização. Um recurso pode ser um programa, ambiente ou pipeline. Se o usuário adicionar uma organização para qualquer permissão, todos os novos recursos dessa organização também possuirão essa permissão. |
| Programa | Programa A | Todos os recursos aplicáveis de um programa. |
| Ambiente | Programa A : ambiente | Aplicável em um ambiente específico. |
| Pipeline | Programa A : pipeline | Aplicável em um pipeline específico. |

## Limitações {#limitations}

Lembre-se das seguintes limitações ao usar permissões personalizadas:

* Um [conjunto limitado de permissões está disponível](#configurable-permissions) para criar perfis personalizados.
* Recursos (como o programa, ambiente, pipeline etc.) criados no Cloud Manager podem levar até dois minutos para serem exibidos no Admin Console para a configuração de permissões.
* Em situações raras nas quais o serviço de permissões personalizadas não responde, os perfis predefinidos ainda estarão disponíveis, e os usuários desses perfis ainda possuirão o acesso apropriado.

## Perguntas frequentes {#faq}

### Quais são os perfis de permissão predefinidos?

* Proprietário da empresa
* Gerenciador de programas
* Gerenciador de implantação
* Desenvolvedor

Para mais detalhes sobre funções predefinidas, consulte [Permissões baseadas em funções](/help/requirements/role-based-permissions.md).

### O que acontece com os perfis de permissão predefinidos com a introdução dos perfis personalizados?

Os perfis de produtos padrão e as funções do Cloud Manager continuarão funcionando como antes.

### Posso editar os perfis de permissão predefinidos?

Não, os perfis padrão não são editáveis. Não é possível adicionar nem remover permissões do perfil de permissão padrão. Você só pode adicionar ou remover usuários de perfis predefinidos.

### Devo excluir os perfis de permissão predefinidos, já que os perfis personalizados estão disponíveis?

Os perfis de permissão predefinidos não devem ser excluídos do Admin Console.

### Posso adicionar usuários a vários perfis de permissão?

Sim, um usuário pode fazer parte de vários perfis, incluindo perfis de permissão predefinidos e personalizados. Quando um usuário é atribuído a vários perfis, as permissões combinadas de todos os perfis de permissão atribuídos são disponibilizadas para esse usuário.

### O que acontece se um usuário possuir permissão para editar um ambiente ou pipeline, mas não possuir acesso ao programa que contém o ambiente ou pipeline?

Nesse caso, o usuário não poderá acessar o ambiente ou pipeline se não tiver as permissões de **Acesso ao programa** que contêm o ambiente ou pipeline.

### O que acontece se eu possuir os programas AEM as a Cloud Service e AMS na mesma organização IMS? Posso gerenciar permissões de um perfil? {#ams-and-aemaacs}

Crie um perfil separado para cada tipo de produto. Ou seja, um para o AEM as a Cloud Service e um para o Adobe Managed Services, ou AMS.
