---
title: Uso de uma sequência incorporada dinâmica
seo-title: Uso de uma sequência incorporada dinâmica
description: Siga esta página para saber como implementar sequências incorporadas dinâmicas em seu projeto do AEM Screens.
seo-description: Siga esta página para saber como implementar sequências incorporadas dinâmicas em seu projeto do AEM Screens.
uuid: 1f442489-2eeb-4dd8-b892-911fcccb3377
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: a40eb5bb-fbf7-4c0d-a34a-db79b884de8f
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# Uso de uma sequência incorporada dinâmica {#using-dynamic-embedded-sequence}

O uso de sequências incorporadas dinâmicas abrange os seguintes tópicos:

* **Visão geral**
* **Uso da experiência incorporada dinâmica em telas AEM**
* **Exibição dos resultados**
* **Restrição de usuários e modificação das ACLs**

## Visão geral {#overview}

***As Sequências*** Incorporadas Dinâmicas são criadas para projetos grandes que seguem a hierarquia secundária pai, onde o filho é referenciado dentro de uma pasta de localização e não de uma pasta de canal. It allows the user to embed a sequence inside a channel by ***Channel Role***. Ele permite que o usuário defina espaços reservados específicos de localização para diferentes escritórios usando uma sequência incorporada dentro de um canal principal.

Ao atribuir um canal a uma exibição, você tem a opção de especificar o caminho da exibição ou a função do canal que será resolvida para um canal real por contexto.

Para usar a Sequência Incorporada Dinâmica, atribua um canal por Função ***de*** canal. Função de canal define o contexto da exibição. A função é direcionada por várias ações e é independente do canal real que cumpre a função. Esta seção descreve um caso de uso que define canais por função e como você pode aproveitar esse conteúdo para um canal global. Você também pode considerar a função como um identificador para a atribuição, ou um alias para o canal no contexto de.

### Benefícios do uso de sequências incorporadas dinâmicas {#benefits-of-using-dynamic-embedded-sequences}

O principal benefício de colocar um canal de sequência dentro de um local em vez da pasta de canais é permitir que os autores locais ou regionais editem conteúdo relevante para eles enquanto são restringidos de canais de edição superiores na hierarquia.

Referencing a *Channel By Role*, allows you to create local version of a channel, in order to dynamically resolve location-specific content and also allows you to create a global channel that leverages the content for the location-specific channels.

>[!NOTE]
>
>**Sequências incorporadas versus sequências incorporadas dinâmicas**
>
>Uma Sequência Incorporada Dinâmica é semelhante a uma sequência incorporada, mas permite que o usuário siga uma hierarquia na qual as alterações/atualizações feitas em um canal são propagadas para outro em relação a outro. Ele segue a hierarquia pai-filho e também inclui ativos como imagens ou vídeos.
>
>***Sequências*** incorporadas dinâmicas permitem exibir conteúdo específico do local, enquanto as Sequências ****** incorporadas exibem apenas a apresentação geral do conteúdo. Além disso, ao configurar Sequências incorporadas dinâmicas, é necessário configurar o canal usando a função e o nome do canal. Consulte as etapas abaixo para ver a implementação prática.
>
>Para saber mais sobre a implementação de sequências incorporadas, consulte Sequências [](embedded-sequences.md) incorporadas nas telas AEM.

O exemplo a seguir fornece uma solução focando nos seguintes termos principais:

* um canal ***de sequência*** principal para a sequência global
* ***componentes de sequência*** incorporada dinâmica para cada parte localmente personalizável da sequência
* ***canais*** de sequência individuais nos respectivos locais com uma *função* na exibição que corresponde à **função *do componente de sequência incorporado*dinâmico.**

>[!NOTE]
>
>To learn more about channel assignment, see **[Channel Assignment](channel-assignment.md)** under Authoring section in AEM Screens documentation.

## Uso de uma sequência incorporada dinâmica {#using-dynamic-embedded-sequence-2}

A seção a seguir explica a criação de uma sequência incorporada dinâmica em um canal do AEM Screens.

### Pré-requisitos {#prerequisites}

Antes de começar a implementar essa funcionalidade, verifique se você tem os seguintes pré-requisitos prontos para iniciar a implementação de sequências incorporadas dinâmicas:

* Criar um projeto do AEM Screens (neste exemplo, **Demonstração**)

* Criar um canal como **Global** na pasta **Canais**

* Adicionar conteúdo ao seu Canal **Global** (*Verifique **Resources.zip**para obter os ativos* relevantes)

A imagem a seguir mostra o projeto de **demonstração** com o canal **Global** na pasta **Canais** .
![screen_shot_2018-09-07at21032pm](assets/screen_shot_2018-09-07at21032pm.png)

### Recursos {#resources}

Você pode baixar os seguintes recursos (imagens e adicioná-los aos ativos) e usá-los ainda mais como conteúdo de canal para fins de demonstração.

[Obter arquivo](assets/resources.zip)

>[!NOTE]
>
>Para obter informações adicionais sobre como criar um projeto e como criar um canal de sequência, consulte os recursos a seguir:
>
>* **[Criação e gerenciamento de projetos](creating-a-screens-project.md)**
>* **[Gerenciamento de um canal](managing-channels.md)**
>



A implementação da sequência incorporada dinâmica em um projeto do AEM Screens envolve três tarefas principais:

1. **Configuração da taxonomia do projeto incluindo Canais, Locais e Exibições**
1. **Criação de um agendamento**
1. **Atribuindo Programação a cada exibição**

Siga as etapas abaixo para implementar a funcionalidade:

>[!CAUTION]
>
>Ao implementar sequências incorporadas dinâmicas, tenha cuidado com os campos **Nome** e **Título** ao criar canais em cada local. Siga cuidadosamente as instruções de nomenclatura.

1. **Criar duas pastas de locais.**

   Navegue até a pasta **Locais** no projeto do AEM Screens e crie duas pastas de localização como **Região A** e **Região B**.

   >[!NOTE]
   >
   >Ao criar a pasta de localização **Região A** , certifique-se de inserir o **Título** como **Região A** e pode deixar o campo **Nome** vazio, de modo que o nome **região a** seja selecionado automaticamente.
   >
   >Semelhante, é o caso para criar a pasta de localização **Região B**, como mostrado abaixo:

   ![screen_shot_2018-09-13at23212pm](assets/screen_shot_2018-09-13at23212pm.png)

   >[!NOTE]
   >
   >Para saber como criar um local, consulte **[Criação e gerenciamento de locais](managing-locations.md)**.

1. **Crie dois locais e um canal em cada pasta de localização.**

   1. Navegue até **Demonstração** —&gt; **Locais** —&gt; **Região A**.
   1. Selecione **Região A** e clique em **+ Criar** na barra de ações.
   1. Selecione **Local** no assistente com **Título** como **Loja 1**. Da mesma forma, crie outro local do assistente chamado **Loja 2** com **Título** como **Loja 2**. Você pode deixar o campo **Nome** vazio ao criar a **Loja 1** e a **Loja 2**.
   1. Repita a etapa (b) e, agora, selecione Canal **de sequência** no assistente. Digite o **Título** como **Região A** e **Nome** como **região **para este canal.
   >[!CAUTION]
   >
   >Ao criar a **Região A** do canal, digite o **Título** como **Região A **e o **Nome** como **região**.

   ![screen_shot_2018-09-13at22857pm](assets/screen_shot_2018-09-13at22857pm.png)

   Da mesma forma, crie dois locais na **Região B** intitulados **Loja 3** e **Loja 4**. Além disso, crie um Canal **de** sequência com **Título** como **Região B** e **Nome** como **região**.

   >[!CAUTION]
   >
   >Certifique-se de usar o mesmo nome para os canais criados na **Região A** e na **Região B** como **região**.

   ![screen_shot_2018-09-13at24408pm](assets/screen_shot_2018-09-13at24408pm.png)

1. **Crie a Exibição e o Canal em cada Local.**

   1. Navegue até **Demonstração** —&gt; **Locais** —&gt; **Região A** —&gt; **Loja 1**.
   1. Selecione **Loja 1** e clique em **+ Criar** na barra de ações.
   1. Selecione **Exibir** no assistente e crie **Store1Display.**
   1. Repita a etapa (b) e, desta vez, selecione Canal **de sequência** no assistente. Insira o **Título** como **Loja1 Canal** e o **Nome** como **armazenamento**.
   >[!CAUTION]
   >
   >É importante quando você cria um canal de sequência, o **Título** do canal pode ser o seu requisito, mas o **Nome** deve ser o mesmo em todos os canais locais.
   >
   >Neste exemplo, os canais na **Região A** e **Região B** compartilham o mesmo **Nome** da **região** e os canais na **Loja 1************** **** ****, na Store 2, na Store 3, e na Store 4compartilham o mesmo Namecomo store.

   ![screen_shot_2018-09-19at120206pm](assets/screen_shot_2018-09-19at120206pm.png)

   Da mesma forma, crie uma exibição como **Store2Display** e um canal **Store2Channel** em** Store 2** (com nome como **loja**).

   >[!NOTE]
   >
   >Certifique-se de usar o mesmo nome para os canais criados na **Loja 1** e na **Loja 2** como **loja**.

   ![screen_shot_2018-09-19at120329pm](assets/screen_shot_2018-09-19at120329pm.png)

   Siga as etapas anteriores para criar um canal e exibir na **Loja 3** e na **Loja 4** na **Região B**. Novamente, certifique-se de usar o mesmo **Nome** da **loja** ao criar o canal **Store3Channel** e **Store4Channel** , respectivamente.

   A imagem a seguir mostra a exibição e o canal na **Loja 3**.

   ![screen_shot_2018-09-19at120448pm](assets/screen_shot_2018-09-19at120448pm.png)

   A imagem a seguir mostra a exibição e o canal na **Loja 4**.

   ![screen_shot_2018-09-19at120552pm](assets/screen_shot_2018-09-19at120552pm.png)

1. **Adicione conteúdo aos canais em seus respectivos locais.**

   Navegue até a **demonstração** -&gt; **Locais** -&gt; **Região A** -&gt; **Região A** e clique em **Editar** na barra de ações. Arraste e solte os ativos que deseja adicionar ao seu canal.

   >[!NOTE]
   >
   >Você pode usar o arquivo ***Resources.zip*** da seção **Resources** , acima, para usar as imagens como ativos para o conteúdo do canal.

   ![screen_shot_2018-09-12at12438pm](assets/screen_shot_2018-09-12at12438pm.png)

   Da mesma forma, navegue até a **demonstração** -&gt; **Locais** -&gt; **Região B** -&gt; **Região B** e clique em **Editar** na barra de ação para arrastar e soltar os ativos em seu canal, como mostrado abaixo:

   ![screen_shot_2018-09-12at13133pm](assets/screen_shot_2018-09-12at13133pm.png)

   Siga as etapas anteriores e os recursos para adicionar conteúdo aos seguintes canais:

   * **Store1Channel**
   * **Store2Channel**
   * **Store3Channel**
   * **Store4Channel**

1. **Criar um agendamento**

   Navegue e selecione a pasta **Programações** no projeto do AEM Screens e clique em **Criar** na barra de ações para criar um novo agendamento.

   A imagem a seguir mostra o **AdSchedule** criado no projeto de **demonstração** .

   ![screen_shot_2018-09-13at33307pm](assets/screen_shot_2018-09-13at33307pm.png)

1. **Atribuir canais a uma programação**

   1. Navegue até **Demo** —&gt; **Programações** —&gt; **AdSchedule** e clique em **Dashboard** na barra de ações.
   1. Clique em **+ Atribuir canal** do painel CANAIS **** ATRIBUÍDOS para abrir a caixa de diálogo Atribuição **de** canal.
   1. Select **Reference Channel**.. by path.
   1. Selecione o Caminho **do** canal como **Demo*** —&gt; ***Canais*** —&gt; ***Global***.
   1. Enter the **Channel Role** as **GlobalAdSegment**.
   1. Selecione os eventos **** suportados como carga **** inicial, tela **** inativa e interação **com** o usuário.
   1. Clique em **Salvar**.
   **Atribuir canal por função para a região:**

   1. Clique em **+ Atribuir canal** do painel CANAIS **** ATRIBUÍDOS para abrir a caixa de diálogo Atribuição **de** canal.
   1. Selecione Canal **de** referência.. por nome.
   1. Digite o Nome **do** Canal como **região***.*
   1. Enter the **Channel Role** as **RegionAdSegment**.
   1. Clique em **Salvar**.
   **Atribuir canal por função para a loja:**

   1. Clique em **+ Atribuir canal** do painel CANAIS **** ATRIBUÍDOS para abrir a caixa de diálogo Atribuição **de** canal.
   1. Selecione Canal **de** referência.. por nome.
   1. Digite o Nome **do** canal como **loja**.
   1. Enter the **Channel Role** as **StoreAdSegment**.
   1. Clique em **Salvar**.
   A imagem a seguir mostra os canais atribuídos por caminho e por função.

   ![screen_shot_2018-09-12at21429pm](assets/screen_shot_2018-09-12at21429pm.png)

1. **Configuração da sequência incorporada dinâmica para o canal global.**

   Navegue até o Canal **Global** , criado inicialmente no projeto de **demonstração** .

   Click **Edit** from the action to open the editor.

   ![screen_shot_2018-09-13at52754pm](assets/screen_shot_2018-09-13at52754pm.png)

   Arraste e solte dois componentes de Sequência **Incorporada** Dinâmica no editor de canal.

   Abra as propriedades de um dos componentes e insira a Função **de Atribuição de** Canal como **RegionAdSegment**.

   Da mesma forma, selecione o outro componente e abra as propriedades para inserir a Função **de Atribuição de** Canal como **StoreAdSegment**.

   ![channeldisplay4](assets/channeldisplay4.gif)

1. **Atribuindo Programação a cada Exibição**

   1. Navegue até cada exibição, como **Demonstração** —&gt; **Locais** —&gt; **Região A** —&gt;**Loja 1** —&gt;**Loja1 Exibição**.
   1. Click **Dashboard** from the action to open the display dashboard.
   1. **Clique em**... no painel CANAIS E PROGRAMAS **ATRIBUÍDOS** e clique em **+Atribuir agendamento**.
   1. Selecione o caminho para Agendamento (por exemplo, aqui, **Demonstração** —&gt; **Agendamentos** —&gt;**AdSchedule**).
   1. Clique em **Salvar**.

## Exibição dos resultados {#viewing-the-results}

Depois de configurar os canais e exibir a conclusão, inicie o AEM Screens player para exibir o conteúdo.

>[!NOTE]
>
>Para saber mais sobre o AEM Screen Player, consulte os seguintes recursos:
>
>* [Downloads do AEM Screens player](https://download.macromedia.com/screens/)
>* [Trabalhar com o AEM Screens Player](working-with-screens-player.md)



A saída a seguir confirma o conteúdo do canal no player do AEM Screens, dependendo do caminho de exibição.

**Cenário 1**:

Se você atribuir o caminho de exibição como **Demo** —&gt; **Locais** —&gt; **Região A** —&gt;** Loja 1** —&gt; **Loja1Exibição**, o seguinte conteúdo será exibido no player do AEM Screens.

![channeldisplay1](assets/channeldisplay1.gif)

**Cenário 1**:

Se você atribuir o caminho de exibição como **Demo** —&gt; **Locais** —&gt; **Região B** —&gt;** Loja 3** —&gt; **Loja 3Display**, o seguinte conteúdo será exibido no player do AEM Screens.

![channeldisplay2](assets/channeldisplay2.gif)

## Restrição de usuários e modificação das ACLs {#restricting-users-and-modifying-the-acls}

Você pode criar autores globais, regionais ou locais para editar o conteúdo relevante para eles, ao mesmo tempo em que é restrito a partir de canais de edição superiores na hierarquia.

É necessário modificar as ACLs para restringir o acesso dos usuários ao conteúdo com base em sua localização.

### Exemplo de caso de uso {#example-use-case}

O exemplo a seguir permite criar três usuários para o projeto de demonstração acima.

Os privilégios são atribuídos a cada grupo da seguinte forma:

**Grupos**:

* **Autor** global: Consiste de usuários que têm acesso a todos os locais e canais no projeto de **demonstração** e que têm todas as permissões de leitura, gravação e edição.

* **Região-Autor**: Consiste de usuários que têm permissões de leitura, gravação e edição para a **Região A** e a **Região B**.

* **Autor da loja**: Consiste de usuários que têm permissões de leitura, gravação e edição somente para a **Loja 1**, **Loja 2**, **Loja 3** e **Loja 4**.

#### Etapas para criar grupos de usuários, usuários e configurar ACLs {#steps-for-creating-user-groups-users-and-setting-up-acls}

>[!NOTE]
>
>Para saber mais detalhes sobre como separar projetos usando ACLs para que cada indivíduo ou equipe gerencie seu próprio projeto, consulte **Configurando ACLs**.

Siga as etapas abaixo para criar grupos, usuários e modificar as ACLs de acordo com as permissões:

1. **Criar grupos**

   1. Navegue até **Adobe Experience Manager**.
   1. Clique em **Ferramentas** —&gt; **Segurança** —&gt; **Grupos**.
   1. Clique em **Criar grupo** e digite **Global-Author** na **ID**.
   1. Clique em **Salvar e fechar**.
   Da mesma forma, crie dois outros grupos, como **Região-Autor** e **Loja-Autor**.

   ![screen_shot_2018-09-17at34008pm](assets/screen_shot_2018-09-17at34008pm.png)

1. **Criar usuários e adicionar usuários a grupos**

   1. Navegue até **Adobe Experience Manager**.
   1. Clique em **Ferramentas** —&gt; **Segurança** —&gt; **Usuários**.
   1. Clique em **Criar usuário** e insira Usuário **** global na **ID**.
   1. Digite a **senha** e confirme a senha para este usuário.
   1. Clique na guia **Grupos** e digite o nome do grupo em **Selecionar grupo**, por exemplo, digite **Global-Author** para adicionar **Global-User** a esse grupo específico.
   1. Clique em **Salvar e fechar**.
   Da mesma forma, crie dois outros usuários, como **Região-Usuário** e **Loja-Usuário** , e adicione-os à **Região-Autor** e **Store-Author** , respectivamente.

   >[!NOTE]
   >
   >É uma prática recomendada adicionar usuários em um grupo e depois atribuir permissões a cada grupo específico de usuários.

   ![screen_shot_2018-09-17at34412pm](assets/screen_shot_2018-09-17at34412pm.png)

1. **Adicionar todos os grupos aos contribuidores**

   1. Navegue até **Adobe Experience Manager**.
   1. Clique em **Ferramentas** —&gt; **Segurança** —&gt; **Grupos**.
   1. Selecione **Colaboradores** na lista e selecione a guia **Membros** .
   1. Selecione o **Grupo** , como **Global-Author**, **Region-Author,** e **Store-Author** para os contribuidores.
   1. Clique em **Salvar e fechar**.

1. **Acessar permissões para cada grupo**

   1. Navegue até o *Useradmin* e use essa interface para modificar as permissões de grupos diferentes.
   1. Procure **Global-Author** e clique na guia **Permissões** , conforme mostrado na figura abaixo.
   1. Da mesma forma, você pode acessar as permissões para **Região-Autor** e **Store-Author**.
   ![screen_shot_2018-09-18at73523am](assets/screen_shot_2018-09-18at73523am.png)

1. **Modificando permissões para cada grupo**

   **Para autor global:**

   1. Navigate to the **Permissions** tab
   1. Navegue até ***/content/screens/demo*** e verifique todas as permissões
   1. Navegue até ***/content/screens/demo/localizações*** e verifique todas as permissões
   1. Navegue até ***/content/screens/demo/location***/***region-a*** e verifique todas as permissões. Da mesma forma, verifique as permissões para **region-b**.
   Consulte a figura abaixo para entender as etapas:
   ![screen_shot_2018-09-18at115752am](assets/screen_shot_2018-09-18at115752am.png)

   A imagem a seguir mostra que agora o Usuário **** Global tem acesso ao Canal **** Global e à **Região A** e à **Região B** com todas as quatro lojas, a **Loja 1**************, a Loja 2, a Loja 3, e a Loja 4.

   ![global](assets/global.gif)

   **Para Região-Autor:**

   1. Navigate to the **Permissions** tab.
   1. Navegue até ***/content/screens/demo*** e verifique apenas as permissões*** Ler**.
   1. Navegue até ***/content/screens/demo/localizações*** e verifique apenas as permissões de **Leitura** .
   1. Navegue até ***/content/screens/demo/anners ***e desmarque as permissões do canal**Global **.***
   1. Navegue até ***/content/screens/demo/location***/***region-a*** e verifique todas as permissões. Da mesma forma, verifique as permissões para **region-b**.
   Consulte a figura abaixo para entender as etapas:

   ![screen_shot_2018-09-18at125158pm](assets/screen_shot_2018-09-18at125158pm.png)

   A imagem a seguir mostra que agora o Usuário da Região tem acesso tanto à **Região A** quanto à **Região B** com todas as quatro lojas, a **Loja 1**, **Loja 2**, **Loja 3****** **** e aStore 4, mas não tem acesso ao GlobalChannel.

   ![região](assets/region.gif)

   **Para Autor da Loja:**

   1. Navigate to the **Permissions** tab.
   1. Navegue até ***/content/screens/demo*** e verifique somente as permissões de **Leitura** .
   1. Navegue até ***/content/screens/demo/localizações*** e verifique apenas as permissões de **Leitura** .
   1. Navegue até ***/content/screens/demo/channel*** e desmarque as permissões para canal **Global** .
   1. Navegue até ***/content/screens/demo/location/region-a*** e verifique somente as permissões de **Leitura** . Da mesma forma, verifique apenas as permissões de **Leitura** para **region-b**.
   1. Navegue até ***/content/screens/demo/location***/***region-a /store-1*** e verifique todas as permissões. Da mesma forma, verifique as permissões para **store-2,** store-3 e **store-4**.
   Consulte a figura abaixo para entender as etapas:

   ![screen_shot_2018-09-18at12415pm](assets/screen_shot_2018-09-18at12415pm.png)

   A imagem a seguir mostra que agora a **Loja-Usuário** tem acesso apenas aos quatro armazenamentos, a **Loja 1**, **Loja 2**, **Loja 3** e **Loja 4** **** ****, mas não tem permissão para acessar os canais Globalou Região A**Região A **e Região B.

   ![loja](assets/store.gif)

>[!NOTE]
>
>Para saber mais detalhes sobre como configurar permissões, consulte [Configurando ACLs](setting-up-acls.md).

