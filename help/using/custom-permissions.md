---
title: Permissões personalizadas
description: Saiba como criar novos perfis de permissão personalizados com permissões configuráveis e restringir o acesso a programas, pipelines e ambientes para usuários do Cloud Manager.
exl-id: a81eda9f-aa89-40ea-8e4c-52367a0a6aba
source-git-commit: 984269e5fe70913644d26e759fa21ccea0536bf4
workflow-type: tm+mt
source-wordcount: '1416'
ht-degree: 46%

---

# Permissões personalizadas {#custom-permissions}

Saiba como criar novos perfis de permissão personalizados com permissões configuráveis e restringir o acesso a programas, pipelines e ambientes para usuários do Cloud Manager.

## Introdução {#introduction}

O Cloud Manager tem um conjunto de funções predefinidas que controlam o acesso a vários recursos do Cloud Manager:

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

Esta seção detalha essas etapas. Talvez seja útil ver as seções [Termos](#terms) e [Permissões configuráveis](#configurable-permissions) à medida que você cria suas próprias permissões personalizadas.

>[!NOTE]
>
>Você deve ter direitos de administrador de produto no Admin Console para criar novos perfis e gerenciar permissões para o Cloud Manager.

### Criar um novo perfil de produto {#create}

Primeiro, crie um novo perfil de produto ao qual você pode atribuir permissões personalizadas.

1. Faça logon no Cloud Manager em [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)

1. Selecione o produto **AEM Managed Services**.

1. Procure por uma instância com nome correspondente ao padrão `*-cloud-manager` e clique em para gerenciar usuários e permissões.

1. Você será redirecionado para a guia **Produtos** do Admin Console, onde é possível gerenciar usuários e permissões do Cloud Manager. Na Admin Console, clique em **Novo Perfil**.

![Botão Novo perfil](/help/assets/admin-console-new-profile.png)

1. Forneça os detalhes gerais sobre o perfil.

   * **Nome do perfil de produto**: um nome descritivo para o perfil
   * **Nome de exibição** - Um nome abreviado que é mostrado na interface do usuário (opções)
   * **Descrição**: uma descrição informativa do perfil que explique sua finalidade (opcional)
   * **Notificar usuários por email** - Quando selecionado, o sistema notifica os usuários por email quando eles são adicionados ou removidos deste perfil.

1. Clique em **Salvar**.

O novo perfil de produto é salvo e torna-se visível na lista de perfis de produto no Admin Console.

### Atribuir permissões personalizadas ao novo perfil de produto {#assign-permissions}

Agora que você tem um novo perfil de produto, é possível atribuir permissões personalizadas.

1. No Admin Console, clique no nome do [novo perfil de produto que você acabou de criar](#create).

1. Na janela aberta, selecione a guia **Permissões** para exibir uma lista de permissões editáveis.

   ![Permissões editáveis](/help/assets/permissions-tab.png)

1. Clique no link **Editar** para obter permissão para editá-lo.

1. A janela **Editar permissões** é aberta.
   * A permissão selecionada na etapa anterior é selecionada na coluna à esquerda.
   * Os itens de permissão disponíveis para atribuição estão na coluna do meio rotulada **Itens de permissão disponíveis**.
   * Os itens de permissões atribuídos estão na coluna à direita rotulada **Itens de permissão incluídos**.

   ![Editar itens de permissão](/help/assets/edit-permission-items.png)

1. Clique no ícone de adição (`+`) ao lado do item de permissão para adicioná-lo à coluna **Itens de permissão incluídos**. Se necessário, clique no ícone `i` ao lado de um item de permissão para saber mais sobre ele.

1. Na parte superior da coluna **Permissões Disponíveis**, clique em **Adicionar tudo** para adicionar todas as permissões. Da mesma forma, clique em **Remover tudo** para remover todas as permissões selecionadas anteriormente.

1. Quando terminar de definir os itens de permissão para o novo perfil de produto, clique em **Salvar**.

O novo perfil de produto é salvo com as permissões personalizadas.

### Atribuir usuários ao novo perfil de produto {#assign-users}

Agora é possível atribuir usuários ao novo perfil de produto criado com permissões personalizadas.

1. No Admin Console, clique no nome do [novo perfil de produto ao qual você acabou de atribuir permissões personalizadas](#assign-permissions).

1. Na janela aberta, selecione a guia **Usuários**.

1. Clique em **Adicionar usuários** e atribua usuários ao novo perfil de produto com permissões personalizadas.

Consulte **Adicionar usuários e grupos de usuários a um perfil de produto** do documento [Gerenciar perfis de produto para usuários corporativos](https://helpx.adobe.com/br/enterprise/using/manage-product-profiles.html) para obter mais detalhes sobre como usar o Admin Console.

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
| Acesso às informações do repositório | Permitir que os usuários acessem as informações do repositório e gerem uma senha de acesso |
| Criar repositório | Permitir que os usuários criem novos repositórios Git |
| Exclusão de repositório | Permitir que os usuários excluam repositórios Git |
| Edição de repositório | Permitir que os usuários editem repositórios Git |
| Geração de códigos do repositório | Permitir que usuários gerem projetos a partir do arquétipo |
| Gerenciamento de cópias de conteúdo | Permitir que usuários gerenciem operações de cópia do conteúdo |

### Permissões no nível da organização {#organization-level}

As permissões no nível da organização são sempre aplicadas em todos os programas em uma organização.

Um exemplo de permissão em nível de organização na Cloud Manager é o **Acesso às Informações do Repositório**. Essa permissão permite que os usuários gerem um nome de usuário, senha e URL do repositório para acessar e contribuir com projetos de clientes. Embora o nome de usuário e a senha permaneçam consistentes em todos os repositórios na organização, cada programa tem um URL de repositório exclusivo.

Consulte o [Repositório de Códigos Source](/help/requirements/source-code-repository.md) para obter mais informações.

## Termos {#terms}

Os termos a seguir são usados na criação e no gerenciamento de permissões personalizadas e funções predefinidas.

| Termo | Descrição |
|---|---|
| Permissões predefinidas | Funções predefinidas como **Proprietário da empresa**, **Gerente de implantação**, entre outras. para controlar vários recursos do Cloud Manager. Para obter detalhes sobre funções predefinidas, consulte [Permissões baseadas em funções](/help/requirements/role-based-permissions.md). |
| Permissões personalizadas | Recursos do Cloud Manager que permitem aos usuários criar perfis de permissão para definir funções para controlar os recursos compatíveis do Cloud Manager |
| Perfil de permissão | Criado no Admin Console para gerenciar permissões configuráveis aplicáveis a usuários que fazem parte do perfil de permissão |
| Permissão configurável | As permissões do Cloud Manager podem ser configuradas no perfil de permissões |
| Item de permissão | Um recurso do programa, ambiente ou pipeline no qual uma permissão pode ser aplicada |

Os itens de permissão se referem ao escopo no qual as permissões são aplicadas. Normalmente, é uma das opções a seguir.

| Tipo de item de permissão | Exemplo | Descrição |
|---|---|---|
| Organização | organização:empresaA | Todos os recursos aplicáveis de uma organização. Um recurso pode ser um programa, ambiente ou pipeline. Se o usuário adicionar uma organização para qualquer permissão, todos os novos recursos nessa organização também terão essa permissão. |
| Programa | Programa A | Todos os recursos aplicáveis de um programa |
| Ambiente | Programa A : ambiente | Aplicável em um ambiente específico |
| Pipeline | Programa A : pipeline | Aplicável em um pipeline específico |

## Limitações {#limitations}

Lembre-se das seguintes limitações ao usar permissões personalizadas:

* Um [conjunto limitado de permissões está disponível](#configurable-permissions) para criar perfis personalizados.
* Recursos (como o programa, ambiente, pipeline etc.) criados no Cloud Manager podem levar até dois minutos para serem exibidos no Admin Console para a configuração de permissões.
* Em raros cenários em que um serviço de permissões personalizadas não responde, os perfis predefinidos ainda estão disponíveis e os usuários em perfis predefinidos ainda têm acesso apropriado.

## Perguntas frequentes {#faq}

### Quais são os perfis de permissão predefinidos?

* Proprietário da empresa
* Gerenciador de programas
* Gerenciador de implantação
* Desenvolvedor

Para obter detalhes sobre funções predefinidas, consulte [Permissões baseadas em funções](/help/requirements/role-based-permissions.md).

### O que acontece com os perfis de permissão predefinidos com a introdução dos perfis personalizados?

Os perfis de produto padrão e as funções do Cloud Manager continuam a funcionar da mesma forma que antes.

### Posso editar os perfis de permissão predefinidos?

Não, os perfis padrão não são editáveis. Não é possível adicionar ou remover permissões do perfil de permissão padrão. Você só pode adicionar ou remover usuários de perfis predefinidos.

### Devo excluir os perfis de permissão predefinidos, já que os perfis personalizados estão disponíveis?

Os perfis de permissão predefinidos não devem ser excluídos do Admin Console.

### Posso adicionar usuários a vários perfis de permissão?

Sim, um usuário pode fazer parte de vários perfis, incluindo perfis de permissão predefinidos e personalizados. Quando um usuário é atribuído a vários perfis, as permissões combinadas de todos os perfis de permissão atribuídos ficam disponíveis para esse usuário.

### O que acontece se um usuário tiver permissão para editar um ambiente/pipeline, mas não tiver acesso a um programa que contenha o ambiente/pipeline?

Neste cenário, o usuário não poderá acessar o ambiente ou pipeline se não tiver as permissões **Acesso ao programa** que contenham o ambiente ou pipeline.

### O que acontece se eu possuir os programas AEM as a Cloud Service e AMS na mesma organização IMS? Posso gerenciar permissões de um perfil? {#ams-and-aemaacs}

Crie um perfil separado para cada tipo de produto. Ou seja, um para AEM como Cloud Service e um para Adobe Managed Services ou AMS.
