---
title: Configuração de configurações gerais para o Gerenciador de nuvem
seo-title: Configuração de configurações gerais para o Adobe AEM Cloud Manager
description: Os pré-requisitos para configurar o Experience Cloud Manager e gerenciar conteúdo de sua interface do usuário.
seo-description: Os pré-requisitos para configurar o Adobe AEM Cloud Manager e gerenciar conteúdo de sua interface do usuário.
uuid: 65 d 795 f 9-aa 97-4816-b 66 b -03 b 5 ae 961 f 47
contentOwner: jsyal
discoiquuid: 03241 b 88-8 d 28-401 b-aa 42-17 ead 6183 cd 8
translation-type: tm+mt
source-git-commit: 1dfb065c09569f811e5a006d3d74825d3bd7cc8d

---


# Configuração de configurações gerais para [!UICONTROL Cloud Manager]{#setting-up-general-configurations-for-cloud-manager}

A seção a seguir destaca os pré-requisitos para configurar [!UICONTROL Cloud Manager] e gerenciar conteúdo de sua interface do usuário.

Esta página de seção aborda os seguintes tópicos

* **Configuração de usuários e funções**
* **Configuração do projeto do aplicativo AEM**
* **Configurações do Dispatcher**
* **Práticas recomendadas de desenvolvimento**

O diagrama a seguir ilustra as diferentes funções que permitem [!UICONTROL Cloud Manager] oferecer continuamente um código de qualidade melhor:

![](assets/screen_shot_2018-05-01at81926pm.png)

## Configuração de usuários e funções {#setting-up-users-and-roles}

As funções são gerenciadas [!UICONTROL Cloud Manager] no Adobe Admin Console. As associações de função específicas são fornecidas adicionando o usuário a um [!UICONTROL Cloud Manager] Perfil de produto no Console de administração.

>[!CAUTION]
>
>Para usar [!UICONTROL Cloud Manager], você deve ter uma Adobe ID e o Contexto do produto Adobe Managed Services.

Você pode atribuir associações de função específicas adicionando o usuário a um [!UICONTROL Cloud Manager] Perfil de produto no Console de administração.

Crie as seguintes funções usando o Console de administração para [!UICONTROL Cloud Manager]:

>[!NOTE]
>
>O Adobe Admin Console fornece um local central para gerenciar seus direitos da Adobe em toda a organização.
>
>Para saber mais sobre o Adobe Admin Console, consulte a documentação do [Console de administração](https://helpx.adobe.com/enterprise/using/admin-console.html).

| **[!UICONTROL Cloud Manager]Funções** | **Descrição** |
|---|---|
| Proprietário de negócios | Responsável pela definição de kpis, aprovação de implantações de produção e substituição de falhas importantes de 3 níveis. |
| Gerenciador de Programas | Usa [!UICONTROL Cloud Manager] para executar configuração de equipe, verificar o status e exibir kpis. Pode aprovar falhas importantes em 3 níveis. |
| Gerenciador de implantação | Gerencia operações de implantação. Usa [!UICONTROL Cloud Manager] para executar implantações de estágio/produção. Pode aprovar falhas importantes em 3 níveis. Tem acesso git. |
| Desenvolvedor | Desenvolve e teste o código do aplicativo personalizado. Principalmente usa [!UICONTROL Cloud Manager] para exibir o status. Confirme o acesso ao git. |
| Engenheiro de sucesso do cliente | Geralmente suporta o sucesso do cliente para clientes do AMS. Interage com [!UICONTROL Cloud Manager] a finalidade de execução de implantações que exigem a supervisão CSE. |
| Autor de conteúdo | Geralmente não interage [!UICONTROL Cloud Manager]com. Pode usar [!UICONTROL Cloud Manager] o Alternador de programas (com a partir [!UICONTROL Experience Cloud]de) para acessar o AEM. |

### Como usar o Console de administração para Configurar equipe {#using-admin-console-to-set-up-team}

Para fornecer permissões apropriadas com base em funções aos [!UICONTROL Cloud Manager] usuários, um administrador da organização do cliente deve criar novos Perfis de produto no contexto [!UICONTROL AEM Managed Services] do produto.

>[!NOTE]
>
>Para acesse o admin Console e configure sua equipe (usuários e funções), abra um navegador e visite [https://adminconsole.adobe.com](https://adminconsole.adobe.com/enterprise).

A adição de usuários (ou grupos) a esses Perfis de produto é feita usando a funcionalidade normal do Console de administração, como mostrado na figura abaixo:

1. Faça logon no Admin Console e clique **em Novo perfil** para adicionar um novo perfil.

   ![](assets/admin_console_roles.png)

1. Preencha os campos para [!UICONTROL Cloud Manager]configurar uma nova função.

   Digite **Nome do perfil**, **Descrição** para criar um novo perfil. Além disso, você pode selecionar um **Grupo de permissões** para o perfil.

   Clique **em Concluído** para concluir a etapa de criação do perfil.

   ![](assets/screen_shot_2018-04-23at75014am.png)

## Configuração do projeto do aplicativo AEM {#aem-application-project-setup}

Antes de configurar o projeto do aplicativo em [!UICONTROL Cloud Manager], você deve considerar um dos dois cenários. Você pode ser novo no AEM 6.4 ou já ser um cliente existente.

>[!NOTE]
>
>Para ter acesso, entre em contato [!UICONTROL Cloud Manager]com os Engenheiros de sucesso do cliente (CSE) para obter o URL e as credenciais para começar.

Você pode configurar um projeto de aplicativo para [!UICONTROL Cloud Manager], com base nos seguintes cenários:

* **Novo projeto do AEM**:

Um novo projeto do AEM vai aproveitar seu projeto existente e trabalhar [!UICONTROL Cloud Manager]com.

Para obter mais informações, consulte [Introdução ao AEM 6.4](https://chl-author./content/help/en/experience-manager/6-4/sites/deploying/using/deploy.html). Além disso, consulte Recursos [do AEM](https://www.adobe.com/marketing-cloud/experience-manager/resources.html?promoid=759X6WV8&mv=other) para obter mais informações.

* **Projeto AEM existente**:

Um projeto AEM existente deve confirmar para as regras na configuração do projeto. Você pode atualizar sua instalação do AEM existente para obter novos recursos e melhorias oferecidos no AEM 6.4 e começar a usar [!UICONTROL Cloud Manager]. Esses critérios devem funcionar com alterações mínimas. Entre em contato com os Engenheiros de sucesso do cliente (CSE) para obter suporte.

Para obter informações adicionais sobre como atualizar sua instância do AEM para 6.4, consulte [Atualizar para o AEM 6.4](https://helpx.adobe.com/experience-manager/6-4/sites/deploying/using/upgrade.html).

### Configuração do repositório {#setting-up-repository}

A single, initially empty, git repository is provisioned for each program onboarded in [!UICONTROL Cloud Manager]. Os desenvolvedores e os gerentes de implantação são fornecidos com o URL do git e credenciais de seu CSE.

Com essas informações, um desenvolvedor pode adicionar seu código, seguindo as diretrizes na seção** Projeto configurado** na seção seguinte abaixo, para concluir os requisitos de configuração antes de Usar [!UICONTROL Cloud Manager].

## Configurações do Dispatcher {#dispatcher-configurations}

[!UICONTROL Cloud Manager] é capaz de implantar arquivos de configuração do servidor da Web e do expedidor supondo que eles sejam armazenados no repositório git, além dos pacotes normais de conteúdo AEM.

Para aproveitar esse recurso, a compilação do Maven produz um arquivo zip que contém dois diretórios - ***conf*** e ***conf. d***.

Após a implantação para uma instância do dispatcher, o conteúdo desses diretórios substituirá o conteúdo desses diretórios na instância do expedidor. Como os arquivos de configuração do servidor Web e do dispatcher frequentemente exigem informações específicas do ambiente, para que esse recurso seja usado corretamente, primeiro você precisará trabalhar com os Engenheiros de Sucesso do Cliente (CSE) para extrair essas variáveis de ambiente em /etc/sysconfig/httpd.

Siga as etapas abaixo para concluir o processo inicial na configuração do dispatcher:

1. Obtenha os arquivos de configuração de produção atuais de seu CSE.
1. Remova dados específicos do ambiente codificado (por exemplo, publicar IP do renderizador) e substituir por variáveis.
1. Defina as variáveis necessárias em pares de valores chave para cada dispatcher de destino e solicita que CSE adicione a ***/etc/sysconfig/httpd*** em cada instância.
1. Teste as configurações atualizadas no palco e, em seguida, solicite CSE a implantar na produção para garantir que elas funcionem corretamente.
1. Confirme os arquivos no git.
1. Deploy through [!UICONTROL Cloud Manager].

O arquivo zip real pode ser produzido usando o maven-assembly-plugin. Os projetos gerados usando o modelo AEM Mathule de Lazybones podem ter a estrutura correta do projeto Maven criada como parte da criação do projeto.

>[!NOTE]
>
>A configuração do dispatcher é feita durante a contratação [!UICONTROL Cloud Manager], mas também pode ser feita em um estágio posterior.

### Configuração do Dispatcher para teste de desempenho {#configuring-dispatcher-for-performance-testing}

Para executar [!UICONTROL Cloud Manager] corretamente testes de desempenho, o servidor do dispatcher deve responder aos mesmos nomes de host que o dispatcher de produção de uma maneira consistente com o servidor de produção.

*Por exemplo*, se um cliente tiver [www.myco.com](http://www.myco.com/) e [www.myotherco.com](http://www.myotherco.com,/) como seus nomes de host de produção e stage-myco. adobecqms. net como nome de host do palco, uma solicitação como esta deve responder adequadamente:

```
curl -H"Host: www.myco.com" http://stage-myco.adobecqms.net/en/home.html
```

Isso exigirá não apenas que os nomes de host sejam configurados corretamente na configuração do dispatcher, mas também que ***/etc/map***, qualquer Apache reescreva ou realmente qualquer outra regra ***de mapeamento/filtro*** de caminho sejam implementados de maneira consistente entre o palco e a produção.

## Práticas recomendadas de desenvolvimento {#development-best-practices}

Antes de usar [!UICONTROL Cloud Manager], é aconselhável compreender algumas práticas recomendadas para configurar o projeto e configurar a configuração de servidor ou de dispather.

### Configuração do projeto {#project-set-up}

Seus projetos devem atender a alguns critérios para trabalhar [!UICONTROL Cloud Manager].

Siga as práticas recomendadas para configurar o projeto em [!UICONTROL Cloud Manager]:

* A única ferramenta de compilação fornecida e compatível é Apache Maven. O Apache Maven 3.3.9 está instalado.
* Constrói em um ambiente Linux em um contêiner do Docker como o usuário raiz.
* A versão Java instalada é Oracle JDK 8 u 161.
* Há alguns pacotes de sistema adicionais instalados como, bzip 2, descompactação, libpng, imagemagick e graphicsmagick. Se você precisar de outros pacotes, será necessário solicitar aqueles por meio do CSE.
* O Maven sempre é executado com o comando mvn -b limpo.
* Você receberá exatamente um repositório de git. Deve haver um arquivo pom.xml na raiz desse repositório. Esse arquivo pom.xml pode se referir a submódulos (que, por sua vez, podem ter outros submódulos etc.) conforme necessário, mas deve haver apenas um ponto de entrada.
* Maven é configurado em nível de sistema com um arquivo settings.xml que inclui automaticamente o repositório de artefato público da Adobe (repo.adobe.com).
* Você pode adicionar repositórios adicionais em seus pom.xml. No entanto, não há suporte para o acesso a repositórios protegidos por senha ou de rede protegidos por rede.
* Os pacotes de conteúdo implantáveis são descobertos por meio da leitura de arquivos zip contidos em um diretório chamado target. Novamente, qualquer número de submódulos pode produzir pacotes de conteúdo.
* Se houver mais de um pacote de conteúdo, a ordem das implantações do pacote não será garantida. Se uma ordem específica for necessária, as dependências do pacote de conteúdo poderão ser usadas para definir a ordem.

<!-- 

Comment Type: annotation
Last Modified By: jsyal
Last Modified Date: 2018-05-02T18:18:15.028-0400

change as per KT

 -->

### Próximas etapas {#the-next-steps}

Depois de configurar as configurações gerais, você está pronto para usar [!UICONTROL Cloud Manager].

Consulte [Usar [! UICONTROL Cloud Manager]](https://helpx.adobe.com/experience-manager/cloud-manager/using/using-cloud-manager.html) para começar [!UICONTROL Cloud Manager]a usar.
