---
title: Adição de repositórios privados no Cloud Manager
description: Saiba como configurar o Cloud Manager para trabalhar com os seus repositórios privados do GitHub.
feature: Release Information
exl-id: e0d103c9-c147-4040-bf53-835e93d78a0b
TQID: https://experienceleague.adobe.com/YQUazTRNh7C31piqZwe-1zAkRWIqt9fVY6jTD5T3ZpI
product_v2: id: c68cd75e-5bca-4bc3-a60e-9e183f816441id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2: id: d095671a-1355-40aa-8b5f-06c33c68080b
source-git-commit: 32dc7aaf4c228d9aee1adedab3f52375f1807bb5
workflow-type: tm+mt
source-wordcount: 837
ht-degree: 76%

---

# Adição de repositórios privados no Cloud Manager {#private-repositories}

Saiba como configurar o Cloud Manager para trabalhar com os seus repositórios privados do GitHub.

## Visão geral {#overview}

Configurar o Cloud Manager com os seus repositórios privados do GitHub permite validar o código diretamente no GitHub, eliminando a necessidade de sincronização frequente com o repositório da Adobe.

>[!NOTE]
>
>Esse recurso é exclusivo do GitHub público. A compatibilidade com o GitHub auto-hospedado não está disponível.

## Configuração {#configuration}

A configuração consiste em duas etapas principais:

1. [Adicionar repositório](#add-repo)
1. [Validação de propriedade de repositório privado](#validate-ownership)



### Adicionar um repositório {#add-repo}

1. Na página **Visão geral do programa** do Cloud Manager, clique na guia **Repositórios** para alternar para a página **Repositórios** e clique em **Adicionar repositório**.

1. Na caixa de diálogo **Adicionar repositório**, selecione **Repositório privado** como o tipo de repositório.

1. Forneça os seguintes detalhes do seu repositório:

   * **Nome do Repositório** - Um nome descritivo.
   * **URL do repositório** - A URL do repositório, que deve terminar em `.git`.
   * **Descrição** (opcional) - Uma descrição mais longa do repositório, conforme necessário.

   ![Adicionar repositório próprio](/help/assets/repositories/add-own-github.png)

1. Clique em **Salvar**.

>[!TIP]
>
>Para obter detalhes sobre como gerenciar repositórios no Cloud Manager, consulte [Repositórios do Cloud Manager](/help/managing-code/managing-repositories.md).



### Validar a propriedade de um repositório privado {#validate-ownership}

Agora o Cloud Manager está configurado com seu repositório GitHub, mas ainda requer autorização para acessá-lo. Para conceder acesso, é necessário instalar o aplicativo GitHub da Adobe e confirmar que você é proprietário(a) do repositório especificado.

1. Após adicionar seu próprio repositório, a caixa de diálogo **Validação de propriedade de repositório privado** é exibida.

   ![Validação de propriedade de repositório privado](/help/assets/repositories/private-repo-validate.png)

1. O Cloud Manager usa um aplicativo GitHub para interagir de maneira segura com o repositório.

   Um proprietário de sua organização do GitHub deve instalar o aplicativo localizado em `https://github.com/apps/cloud-manager-for-aem` e fornecer acesso ao repositório. Consulte a documentação do GitHub para obter mais detalhes.

1. Para melhorar a segurança, crie um arquivo secreto na ramificação padrão do repositório. Clique em **Gerar**.

1. Confirme a geração do arquivo secreto clicando em **Confirmar**.

   ![Confirmar geração de segredo](/help/assets/repositories/confirm-generation.png)

1. De volta à caixa de diálogo **Validação de propriedade de repositório privado**, o Cloud Manager terá gerado o conteúdo no campo **Conteúdo do arquivo secreto**. Copie o conteúdo desse campo.

   O conteúdo do arquivo secreto é mostrado apenas uma vez. Se você não copiar o conteúdo antes de fechar esta janela, será necessário gerar o segredo novamente.

   ![Copiar conteúdo do arquivo secreto](/help/assets/repositories/new-secret.png)

1. Crie um novo arquivo na ramificação padrão do seu repositório GitHub chamada `.well-known/adobe/cloud-manager-challenge`, cole o conteúdo do arquivo secreto nesse arquivo e salve.

1. Após a instalação do aplicativo e a adição do arquivo secreto no repositório, clique em **Validar** na caixa de diálogo **Validação de propriedade de repositório privado**.

O aplicativo pode ser instalado e você pode gerar um arquivo secreto em qualquer ordem. No entanto, ambas as etapas devem ser concluídas para que você possa validar.

Até a validação, o repositório será listado com um ícone vermelho, indicando que ainda não foi validado e não pode ser usado.

![Repositório não validado](/help/assets/repositories/unvalidated-repo.png)

Observe que a coluna **Tipo** identifica facilmente os repositórios fornecidos pela Adobe (**Adobe**) e os seus repositórios do GitHub (**GitHub**).

Para retornar ao repositório mais tarde e concluir a validação, vá para a página **Repositórios**. Clique em ![Mais ícone, reticências](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) ao lado do repositório GitHub adicionado e clique em **Validação de propriedade**.


## Utilização de repositórios privados com o Cloud Manager {#using}

Após a validação do repositório do GitHub no Cloud Manager, a integração é concluída e é possível usar o repositório com o Cloud Manager.

**Para usar repositórios privados com o Cloud Manager:**

1. Ao criar uma solicitação de pull, começa uma verificação do GitHub automaticamente.

   ![Verificações do GitHub](/help/assets/repositories/github-checks.png)

1. Para cada solicitação de pull, é criado um [pipeline de qualidade de código de pilha completa](/help/using/managing-pipelines.md) automaticamente. Esse pipeline é iniciado a cada atualização de solicitação de pull.

1. A verificação do GitHub permanece em estado de execução até que as verificações de qualidade do código sejam concluídas. Os resultados de qualidade do código são então propagados para a verificação do GitHub.

   ![Verificações de qualidade do código do GitHub](/help/assets/repositories/github-code-quality.png)

Quando a solicitação de “pull” é fechada ou mesclada, o pipeline de qualidade de código de pilha completa criado é excluído automaticamente.

>[!TIP]
>
>Consulte o documento [Anotações de verificação do GitHub](github-annotations.md) para obter detalhes sobre as informações fornecidas pelo GitHub quando as verificações de solicitação de pull são executadas.

>[!TIP]
>
>Você pode controlar os pipelines criados automaticamente para validar cada solicitação de pull para um repositório privado. Consulte [Configuração de verificação do GitHub para repositórios privados](github-check-config.md) para obter mais informações.



## Associação de repositórios privados a pipelines {#pipelines}

Repositórios privados validados podem ser associados a [pipelines de pilha completa e front-end](/help/overview/ci-cd-pipelines.md).



## Limitações {#limitations}

Certas limitações se aplicam ao uso de repositórios privados com o Cloud Manager.

* Nenhuma tag do Git será criada e enviada ao usar repositórios privados em pipelines de pilha completa de produção.
* Se o aplicativo GitHub da Adobe for removido da organização GitHub, essa ação removerá o recurso de validação de solicitação de pull para todos os repositórios.
* Os pipelines que usam repositórios privados e o acionador de build não confirmado não são iniciados automaticamente quando uma nova confirmação é enviada para a ramificação selecionada.
* A [Funcionalidade de reutilização de artefato](/help/getting-started/project-setup.md#build-artifact-reuse) não se aplica a repositórios privados.
* Não é possível pausar a validação da solicitação de pull usando a verificação do GitHub no Cloud Manager. Se o repositório do GitHub for validado no Cloud Manager, o Cloud Manager tentará validar as solicitações de pull criadas para esse repositório.
* Se sua organização GitHub impor restrições de IP, abra um caso de suporte para obter a lista de endereços IP que devem ser permitidos.
