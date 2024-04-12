---
title: Permissões personalizadas
description: Saiba como criar novos perfis de permissão personalizados com permissões configuráveis e restringir o acesso a programas, pipelines e ambientes para usuários do Cloud Manager.
exl-id: a81eda9f-aa89-40ea-8e4c-52367a0a6aba
source-git-commit: 4a784f1594be4831be1c1c4aecb41b4f1b3b8be2
workflow-type: ht
source-wordcount: '1474'
ht-degree: 100%

---

# Permissões personalizadas {#custom-permissions}

Saiba como criar novos perfis de permissão personalizados com permissões configuráveis e restringir o acesso a programas, pipelines e ambientes para usuários do Cloud Manager.

## Introdução {#introduction}

O Cloud Manager possui um conjunto de funções predefinidas que controlam o acesso a vários de seus recursos:

* Proprietário da empresa
* Gerenciador de programas
* Gerenciador de implantação
* Desenvolvedor

As permissões personalizadas permitem que usuários criem novos perfis com permissões configuráveis para restringir o acesso de usuários do Cloud Manager a programas, pipelines e ambientes.

>[!TIP]
>
>Para obter detalhes sobre funções predefinidas, consulte o documento [Permissões baseadas em função.](/help/requirements/role-based-permissions.md)

## Uso de permissões personalizadas {#using}

Para criar e usar permissões personalizadas, são necessárias três etapas:

1. [Crie um novo perfil de produto.](#create)
1. [Atribua permissões personalizadas ao novo perfil de produto.](#assign-permissions)
1. [Atribua usuários ao novo perfil de produto.](#assign-users)

Esta seção detalhará essas etapas. Talvez seja útil consultar as sessões [Termos](#terms) e [Permissões configuráveis](#configurable-permissions) ao criar permissões personalizadas.

>[!NOTE]
>
>Você deve ter direitos de admin de produto no Admin Console para criar novos perfis e gerenciar permissões no Cloud Manager.

### Crie um novo perfil de produto {#create}

Você deve primeiro criar um novo perfil de produto, ao qual poderá atribuir permissões personalizadas.

1. Faça logon no Cloud Manager em [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)

1. Selecione o produto **AEM Managed Services**.

1. Pesquise por uma instância com um nome correspondente ao padrão `*-cloud-manager` e toque ou clique para gerenciar usuários e permissões.

1. Você será redirecionado(a) para a guia **Produtos** do Admin Console, onde é possível gerenciar usuários e permissões do Cloud Manager. No Admin Console, toque ou clique no botão **Novo perfil**.

![Botão Novo perfil](/help/assets/admin-console-new-profile.png)

1. Forneça os detalhes gerais sobre o perfil.

   * **Nome do perfil de produto**: um nome descritivo para o perfil
   * **Nome de exibição**: um nome abreviado que será exibido na interface (opções)
   * **Descrição**: uma descrição informativa do perfil que explique sua finalidade (opcional)
   * **Notificar usuários por email**: ao selecionar essa opção, usuários serão notificados por email quando forem adicionados ou removidos deste perfil.

1. Toque ou clique em **Salvar** após concluir.

O novo perfil de produto é salvo e torna-se visível na lista de perfis de produto no Admin Console.

### Atribuir permissões personalizadas ao perfil {#assign-permissions}

Agora que você tem um novo perfil de produto, é possível atribuir permissões personalizadas.

1. No Admin Console, toque ou clique no nome do [perfil de produto recém-criado.](#create)

1. Na janela aberta, selecione a guia **Permissões** para exibir uma lista de permissões editáveis.

   ![Permissões editáveis](/help/assets/permissions-tab.png)

1. Toque ou clique no link **Editar** de uma permissão para editá-la.

1. A janela **Editar permissões** é aberta.
   * A permissão selecionada na etapa anterior é selecionada na coluna à esquerda.
   * Os itens de permissão disponíveis para atribuição estão na coluna do meio rotulada **Itens de permissão disponíveis**.
   * Os itens de permissões atribuídos estão na coluna à direita rotulada **Itens de permissão incluídos**.

   ![Editar itens de permissão](/help/assets/edit-permission-items.png)

1. Toque ou clique no ícone de adição (`+`) próximo ao item de permissão para adicioná-lo à coluna **Itens de permissão incluídos**.

   * Toque ou clique no ícone `i` próximo ao item de permissão para obter mais informações.

1. Toque ou clique em **Adicionar tudo** na parte superior da coluna **Permissões disponíveis** para adicionar todas as permissões. Da mesma forma, toque ou clique em **Remover tudo** para remover todas as permissões selecionadas anteriormente.

1. Toque ou clique em **Salvar** quando terminar de definir os itens de permissão para o novo perfil de produto.

O novo perfil de produto é salvo com as permissões personalizadas.

### Atribuir usuários às permissões personalizadas {#assign-users}

Agora é possível atribuir usuários ao novo perfil de produto criado com permissões personalizadas.

1. Na Admin Console, toque ou clique no nome do [novo perfil de produto ao qual você atribuiu permissões personalizadas.](#assign-permissions)

1. Na janela aberta, selecione a guia **Usuários**.

1. Toque ou clique em **Adicionar usuários** e atribua usuários ao novo perfil de produto com permissões personalizadas.

Consulte a seção **Adicionar usuários e grupos de usuários a um perfil de produto** do documento [Gerenciar perfis de produto para usuários corporativos](https://helpx.adobe.com/br/enterprise/using/manage-product-profiles.html) para obter mais detalhes sobre como usar o Admin Console.

## Permissões configuráveis {#configurable-permissions}

As seguintes permissões estão disponíveis para criar perfis personalizados.

| Permissão | Descrição |
|---|---|
| Acesso ao programa | Permitir que usuários acessem programas |
| Editar programa | Permitir que usuários editem programas |
| Criação de pipeline | Permitir que usuários criem novos pipelines |
| Exclusão de pipeline | Permitir que usuários excluam pipelines |
| Edição de pipeline | Permitir que usuários editem pipelines |
| Aprovar e rejeitar implantações de produção | Permitir que usuários aprovem ou rejeitem uma etapa de implantação de produção |
| Cancelamento de execuções de pipeline | Permitir que usuários cancelem execuções de pipeline |
| Iniciar execuções de pipeline | Permitir que usuários iniciem novas execuções de pipeline |
| Ignorar e rejeitar falhas de métrica importantes | Permitir que usuários ignorem ou rejeitem falhas de métrica importantes |
| Programação de implantações de produção | Permitir que usuários programem uma etapa de implantação de produção |
| Acesso às informações do repositório | Permitir que usuários acessem as informações do repositório e gerem a senha de acesso |
| Criar repositório | Permitir que usuários criem novos repositórios Git |
| Exclusão de repositório | Permitir que usuários excluam repositórios Git |
| Edição de repositório | Permitir que usuários editem repositórios Git |
| Geração de códigos do repositório | Permitir que usuários gerem projetos a partir do arquétipo |
| Gerenciamento de cópias de conteúdo | Permitir que usuários gerenciem operações de cópia do conteúdo |

### Permissões no nível da organização {#organization-level}

As permissões no nível da organização se referem às permissões que são sempre fornecidas em todos os programas de uma organização.

Estas são permissões no nível da organização:

* **Acesso às informações do repositório**: essa permissão no nível do locatário/organização permite que usuários gerem um nome de usuário, senha e URL do repositório para acessar e colaborar com o projeto de cliente.
   * O nome de usuário e a senha para acesso ao repositório serão comuns em todos os repositórios na organização, no entanto, o URL do repositório será exclusivo para cada programa.
   * Consulte o documento [Repositório de código-fonte](/help/requirements/source-code-repository.md) para obter mais informações.

## Termos {#terms}

Os termos a seguir são usados na criação e no gerenciamento de permissões personalizadas e funções predefinidas.

| Termo | Descrição |
|---|---|
| Permissões predefinidas | Funções predefinidas como **Proprietário da empresa**, **Gerente de implantação** etc. para controlar vários recursos do Cloud Manager. Para obter detalhes sobre funções predefinidas, consulte o documento [Permissões baseadas em função.](/help/requirements/role-based-permissions.md) |
| Permissões personalizadas | Recursos do Cloud Manager que permitem que usuários criem perfis de permissão para definir funções de controle de recursos compatíveis do Cloud Manager |
| Perfil de permissão | Criado no Admin Console para gerenciar permissões configuráveis que serão aplicáveis a usuários que fazem parte do perfil de permissão |
| Permissão configurável | Permissões do Cloud Manager que podem ser configuradas no perfil de permissão |
| Item de permissão | Um recurso do programa, ambiente ou pipeline no qual uma permissão pode ser aplicada |

Os itens de permissão se referem ao escopo no qual a permissão será aplicada. Normalmente, será um dos seguintes:

| Tipo de item de permissão | Exemplo | Descrição |
|---|---|---|
| Organização | organização:empresaA | Todos os recursos aplicáveis de uma organização. Um recurso pode ser um programa, ambiente ou pipeline. Se o usuário adicionar uma organização para qualquer permissão, todos os novos recursos dessa organização também possuirão essa permissão. |
| Programa | Programa A | Todos os recursos aplicáveis de um programa |
| Ambiente | Programa A : ambiente | Aplicável em um ambiente específico |
| Pipeline | Programa A : pipeline | Aplicável em um pipeline específico |

## Limitações {#limitations}

Lembre-se das limitações a seguir ao usar permissões personalizadas.

* Um [conjunto limitado de permissões está disponível](#configurable-permissions) para criar perfis personalizados.
* Recursos (como o programa, ambiente, pipeline etc.) criados no Cloud Manager podem levar até dois minutos para serem exibidos no Admin Console para a configuração de permissões.
* Em situações raras nas quais o serviço de permissões personalizadas não responde, os perfis predefinidos ainda estarão disponíveis e usuários desses perfis ainda possuirão o acesso apropriado.

## Perguntas frequentes {#faq}

### Quais são os perfis de permissão predefinidos?

* Proprietário da empresa
* Gerenciador de programas
* Gerenciador de implantação
* Desenvolvedor

Para obter detalhes sobre funções predefinidas, consulte o documento [Permissões baseadas em função.](/help/requirements/role-based-permissions.md)

### O que acontece com os perfis de permissão predefinidos com a introdução dos perfis personalizados?

Os perfis de produto padrão e as funções do Cloud Manager continuarão funcionando da mesma forma que antes.

### Posso editar os perfis de permissão predefinidos?

Não, os perfis padrão não são editáveis. Não é possível adicionar ou remover permissões do perfil de permissões padrão. Você só pode adicionar ou remover usuários de perfis predefinidos.

### Devo excluir os perfis de permissão predefinidos, já que os perfis personalizados estão disponíveis?

Os perfis de permissão predefinidos não devem ser excluídos do Admin Console.

### Posso adicionar usuários a vários perfis de permissão?

Sim, um usuário pode fazer parte de vários perfis, incluindo perfis de permissão predefinidos e personalizados. Quando um usuário é atribuído a vários perfis, as permissões combinadas de todos os perfis de permissão atribuídos são disponibilizadas para esse usuário.

### O que acontece se um usuário possuir permissão para editar um ambiente ou pipeline, mas não possuir acesso ao programa que contenha o ambiente ou pipeline?

Nesse caso, o usuário não poderá acessar o ambiente ou pipeline se não tiver as permissões de **Acesso ao programa** que os contêm.

### O que acontece se eu possuir os programas AEM as a Cloud Service e AMS na mesma organização IMS? Posso gerenciar permissões de um perfil? {#ams-and-aemaacs}

Você deve criar um perfil separado para cada tipo de produto (por exemplo, um para o AEM as a Cloud Service e um para o Adobe Managed Services ou AMS).
