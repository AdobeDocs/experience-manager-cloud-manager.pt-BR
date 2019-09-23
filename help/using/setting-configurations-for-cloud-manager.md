---
title: Configuração de configurações gerais para o Cloud Manager
seo-title: Configuração de configurações gerais para o Adobe AEM Cloud Manager
description: Os pré-requisitos para configurar o Cloud Manager e gerenciar conteúdo de sua interface de usuário.
seo-description: Os pré-requisitos para configurar o Adobe AEM Cloud Manager e gerenciar conteúdo de sua interface de usuário.
uuid: 65d795f9-aa97-4816-b66b-03b5ae961f47
contentOwner: jsyal
discoiquuid: 03241b88-8d28-401b-aa42-17ead6183cd8
translation-type: tm+mt
source-git-commit: 093e25fa1cf2f5cdc3d8ea0bffd5c02ade854a88

---


# Configuração de configurações gerais para [!UICONTROL Cloud Manager]{#setting-up-general-configurations-for-cloud-manager}

A seção a seguir destaca os pré-requisitos para configurar [!UICONTROL Cloud Manager] e gerenciar conteúdo de sua interface de usuário.

Esta página de seção aborda os seguintes tópicos

* **Configuração de usuários e funções**
* **Configuração do projeto do aplicativo AEM**
* **Configurações do Dispatcher**
* **Práticas recomendadas de desenvolvimento**

O diagrama a seguir ilustra as diferentes funções que permitem fornecer continuamente [!UICONTROL Cloud Manager] o código de melhor qualidade:

![](assets/screen_shot_2018-05-01at81926pm.png)

## Configuração de usuários e funções {#setting-up-users-and-roles}

As funções são gerenciadas [!UICONTROL Cloud Manager] pelo Adobe Admin Console. Associações de função específicas são fornecidas adicionando o usuário a um Perfil [!UICONTROL Cloud Manager] de produto no Admin Console.

>[!CAUTION]
>
>Para usar [!UICONTROL Cloud Manager], você deve ter uma Adobe ID e o Contexto de produto do Adobe Managed Services.

É possível atribuir associações de função específicas adicionando o usuário a um Perfil [!UICONTROL Cloud Manager] de produto no Admin Console.

Crie as seguintes funções usando o Admin Console para [!UICONTROL Cloud Manager]:

>[!NOTE]
>
>O Adobe Admin Console fornece um local central para gerenciar seus direitos da Adobe em toda a organização.
>
>Para saber mais sobre o Adobe Admin Console, consulte a documentação do [Admin Console](https://helpx.adobe.com/enterprise/using/admin-console.html).

| **[!UICONTROL Cloud Manager]Funções** | **Descrição** |
|---|---|
| Proprietário da empresa | Responsável por definir KPIs, aprovar implantações de produção e substituir falhas importantes de 3 níveis. |
| Gerente do programa | Usa [!UICONTROL Cloud Manager] para executar a configuração do grupo, verificar o status e exibir KPIs. Pode aprovar falhas importantes de 3 níveis. |
| Gerenciador de implantação | Gerencia operações de implantação. Usa [!UICONTROL Cloud Manager] para executar implantações de estágio/produção. Pode aprovar falhas importantes de 3 níveis. Tem acesso. |
| Desenvolvedor | Desenvolve e testa o código personalizado do aplicativo. Utiliza principalmente [!UICONTROL Cloud Manager] para ver o estado. Tem acesso a git. |
| Engenheiro de sucesso do cliente | Geralmente oferece suporte ao sucesso do cliente para clientes AMS. Interage com [!UICONTROL Cloud Manager] a finalidade de executar implantações que exigem supervisão CSE. |
| Autor de conteúdo | Geralmente não interage com [!UICONTROL Cloud Manager]. Pode usar o [!UICONTROL Cloud Manager] Comutador de programas (navegando de [!UICONTROL Experience Cloud]) para acessar o AEM. |

### Usando o Admin Console para configurar o grupo {#using-admin-console-to-set-up-team}

Para fornecer as permissões apropriadas com base em funções aos [!UICONTROL Cloud Manager] usuários, um administrador na organização do cliente deve criar novos Perfis de produto no Contexto [!UICONTROL AEM Managed Services] do produto.

>[!NOTE]
>
>Para acessar o Admin Console e configurar sua equipe (usuários e funções), abra um navegador e visite [https://adminconsole.adobe.com](https://adminconsole.adobe.com/enterprise).

A adição de usuários (ou grupos) a esses Perfis de produto é feita usando a funcionalidade normal do Admin Console, como mostrado na figura abaixo:

1. Faça logon no Admin Console e clique em **Novo perfil** para adicionar um novo perfil.

   ![](assets/admin_console_roles.png)

1. Preencha os campos para configurar uma nova função para [!UICONTROL Cloud Manager].

   Insira o Nome **do** perfil, **Descrição** para criar um novo perfil. Além disso, você pode selecionar um Grupo **de** permissões para o perfil.

   Clique em **Concluído** para concluir a etapa de criação do perfil.

   ![](assets/screen_shot_2018-04-23at75014am.png)

## Configuração do projeto do aplicativo AEM {#aem-application-project-setup}

Antes de configurar seu projeto de aplicativo em [!UICONTROL Cloud Manager], você deverá considerar um dos dois cenários. Você pode ser novo no AEM 6.4 ou já ser um cliente existente.

>[!NOTE]
>
>Para ter acesso ao [!UICONTROL Cloud Manager], entre em contato com os engenheiros de sucesso do cliente (CSE) para obter o URL e as credenciais para começar.

Você pode configurar um projeto de aplicativo para [!UICONTROL Cloud Manager], com base nos dois cenários a seguir:

* **Novo projeto** do AEM:

Um novo projeto do AEM aproveitará seu projeto existente e trabalhará com [!UICONTROL Cloud Manager].

Para obter informações adicionais, consulte [Introdução ao AEM 6.4](https://chl-author./content/help/en/experience-manager/6-4/sites/deploying/using/deploy.html). Além disso, consulte Recursos [do](https://www.adobe.com/marketing-cloud/experience-manager/resources.html?promoid=759X6WV8&mv=other) AEM para obter mais informações.

* **Projeto** AEM existente:

Um projeto AEM existente deve confirmar as regras para a configuração do projeto. Você pode atualizar sua instalação existente do AEM para obter novos recursos e melhorias oferecidos no AEM 6.4 e começar a usar [!UICONTROL Cloud Manager]. Estes critérios devem funcionar com alterações mínimas. Entre em contato com os engenheiros de sucesso do cliente (CSE) para obter suporte.

Para obter informações adicionais sobre como atualizar sua instância do AEM para a versão 6.4, consulte [Atualização para o AEM 6.4](https://helpx.adobe.com/experience-manager/6-4/sites/deploying/using/upgrade.html).

### Configuração do repositório {#setting-up-repository}

Um único repositório git, inicialmente vazio, é provisionado para cada programa integrado no [!UICONTROL Cloud Manager]. Os desenvolvedores e os gerentes de implantação recebem o URL git e as credenciais de seu CSE.

Com essas informações, um desenvolvedor pode adicionar seu código, seguindo as diretrizes na **Configuração do projeto **na seção seguinte, para concluir os requisitos de configuração antes de Usar [!UICONTROL Cloud Manager].

## Configurações do Dispatcher {#dispatcher-configurations}

[!UICONTROL Cloud Manager] O é capaz de implantar arquivos de configuração do servidor da Web e do dispatcher, pressupondo que estejam armazenados no repositório git, além dos pacotes de conteúdo AEM normais.

Para aproveitar esse recurso, a compilação Maven produz um arquivo zip que contém dois diretórios - ***conf*** e ***conf.d***.

Após a implantação em uma instância do dispatcher, o conteúdo desses diretórios substituirá o conteúdo desses diretórios na instância do dispatcher. Como os arquivos de configuração do servidor da Web e do dispatcher geralmente exigem informações específicas do ambiente, para que esse recurso seja usado corretamente, você precisará trabalhar com os engenheiros de sucesso do cliente (CSE) para extrair essas variáveis de ambiente em /etc/sysconfig/httpd.

Siga as etapas abaixo para concluir o processo inicial na configuração do dispatcher:

1. Obtenha os arquivos de configuração de produção atuais de seu CSE.
1. Remova dados específicos do ambiente codificados permanentemente (por exemplo, IP de renderizador de publicação) e substitua por variáveis.
1. Defina as variáveis necessárias em pares de valor chave para cada despachante de destino e solicite CSE para adicionar a ***/etc/sysconfig/httpd*** em cada instância.
1. Teste as configurações atualizadas no palco e, em seguida, solicite que CSE implante na produção para garantir que elas funcionem corretamente.
1. Confirmar arquivos para obter.
1. Implantar por [!UICONTROL Cloud Manager].

O arquivo zip real pode ser produzido usando o plug-in maven-assembly. Os projetos gerados usando o Modelo Multimódulo AEM Lazybones podem ter a estrutura de projeto Maven correta criada como parte da criação do projeto.

>[!NOTE]
>
>A configuração do dispatcher é feita durante o embarque no [!UICONTROL Cloud Manager], mas também pode ser feita em uma fase posterior.

### Configuração do Dispatcher para Teste de Desempenho {#configuring-dispatcher-for-performance-testing}

Para [!UICONTROL Cloud Manager] executar testes de desempenho corretamente, o servidor do dispatcher de estágio deve responder aos mesmos nomes de host que o dispatcher de produção de uma maneira consistente com o servidor de produção.

*Por exemplo*, se um cliente tiver [www.myco.com](http://www.myco.com/) e [www.myotherco.com](http://www.myotherco.com,/) como seus nomes de host de produção e stage-myco.adobecqms.net como seu nome de host de estágio, uma solicitação como essa deverá responder adequadamente:

```
curl -H"Host: www.myco.com" http://stage-myco.adobecqms.net/en/home.html
```

Isso exigirá não apenas que os nomes de host sejam configurados corretamente na configuração do dispatcher, mas também que ***/etc/map***, quaisquer regravações do Apache ou qualquer outra regra de ***mapeamento/filtro*** de caminho sejam implementados de maneira consistente entre o palco e a produção.

## Práticas recomendadas de desenvolvimento {#development-best-practices}

Antes de usar [!UICONTROL Cloud Manager], é aconselhável compreender algumas práticas recomendadas para configurar projetos e configurar a configuração do servidor Web ou do dispather.

### Configuração do projeto {#project-set-up}

Seus projetos devem seguir alguns critérios para trabalharem com [!UICONTROL Cloud Manager].

Siga as práticas recomendadas para configurar o projeto em [!UICONTROL Cloud Manager]:

* A única ferramenta de construção fornecida e suportada é o Apache Maven. O Apache Maven 3.3.9 está instalado.
* As compilações são executadas em um ambiente Linux em um contêiner Docker como o usuário raiz.
* A versão do Java instalada é o Oracle JDK 8u161.
* Existem outros pacotes de sistema instalados, como bzip2, unzip, libpng, imagemagick e Graphicsmagick. Se você precisar de outros pacotes, será necessário solicitar esses pacotes por meio do CSE.
* O Maven é sempre executado com o comando mvn -B clean package.
* Você receberá exatamente um repositório git. Deve haver um arquivo pom.xml na raiz desse repositório. Esse arquivo pom.xml pode fazer referência a quantos submódulos (que por sua vez podem ter outros submódulos etc.) se necessário, mas só tem de haver um ponto de entrada.
* O Maven é configurado no nível do sistema com um arquivo settings.xml que inclui automaticamente o repositório público de artefatos da Adobe (repo.adobe.com).
* Você pode adicionar repositórios adicionais em seus arquivos pom.xml. No entanto, o acesso a repositórios de artefatos protegidos por senha ou pela rede não é suportado.
* Os pacotes de conteúdo implantável são detectados ao verificar se há arquivos zip contidos em um diretório chamado target. Novamente, qualquer número de submódulos pode produzir pacotes de conteúdo.
* Se houver mais de um pacote de conteúdo, a ordem de implantações de pacote não é garantida. Se uma ordem específica for necessária, as dependências do pacote de conteúdo poderão ser usadas para definir a ordem.

<!-- 

Comment Type: annotation
Last Modified By: jsyal
Last Modified Date: 2018-05-02T18:18:15.028-0400

change as per KT

 -->

### Próximas etapas {#the-next-steps}

Depois de configurar as configurações gerais, você estará pronto para usar [!UICONTROL Cloud Manager].

Consulte [Uso do [!UICONTROL Cloud Manager]](https://helpx.adobe.com/experience-manager/cloud-manager/using/using-cloud-manager.html) para começar a usar [!UICONTROL Cloud Manager].
