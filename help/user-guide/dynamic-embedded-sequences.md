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
source-git-commit: 2a3bbdd283f983cbdb5f21b606f508603385e041
workflow-type: tm+mt
source-wordcount: '2535'
ht-degree: 3%

---


# Uso de uma sequência incorporada dinâmica {#using-dynamic-embedded-sequence}

O uso de sequências incorporadas dinâmicas abrange os seguintes tópicos:

* **Visão geral**
* **Uso da experiência incorporada dinâmica no AEM Screens**
* **Exibição dos resultados**
* **Restrição de usuários e modificação das ACLs**

## Visão geral {#overview}

***As*** Sequências Incorporadas Dinâmicas são criadas para projetos grandes que seguem a hierarquia secundária pai, na qual o filho é referenciado dentro de uma pasta de localização e não em uma pasta de canal. Permite que o usuário incorpore uma sequência dentro de um canal por ***Função de Canal***. Ele permite que o usuário defina espaços reservados específicos de localização para diferentes escritórios usando uma sequência incorporada dentro de um canal principal.

Ao atribuir um canal a uma exibição, você tem a opção de especificar o caminho da exibição ou a função do canal que será resolvida para um canal real por contexto.

Para usar a Sequência Incorporada Dinâmica, atribua um canal por ***Função do Canal***. A Função do canal define o contexto da exibição. O papel é direcionado por várias ações e é independente do canal real que cumpre o papel. Esta seção descreve um caso de uso que define canais por função e como você pode aproveitar esse conteúdo para um canal global. Você também pode considerar a função como um identificador para a atribuição, ou um alias para o canal no contexto de.

### Benefícios do uso de sequências incorporadas dinâmicas {#benefits-of-using-dynamic-embedded-sequences}

O principal benefício de colocar um canal de sequência dentro de um local em vez da pasta canais é permitir que os autores locais ou regionais editem conteúdo relevante para eles enquanto são restringidos de editar canais mais altos na hierarquia.

Fazer referência a um *Canal por função* permite criar uma versão local de um canal, a fim de resolver dinamicamente o conteúdo específico do local e também permite criar um canal global que aproveita o conteúdo dos canais específicos do local.

>[!NOTE]
>
>**Sequências incorporadas versus sequências incorporadas dinâmicas**
>
>Uma Sequência Incorporada Dinâmica é semelhante a uma sequência incorporada, mas permite que o usuário siga uma hierarquia na qual as alterações/atualizações feitas em um canal são propagadas para outro em relação a outro. Ele segue a hierarquia pai-filho e também inclui ativos como imagens ou vídeos.
>
>***As*** Sequências incorporadas dinâmicas permitem exibir conteúdo específico da localização, enquanto as  ***Sequências*** incorporadas exibem apenas a apresentação geral do conteúdo. Além disso, ao configurar Sequências incorporadas dinâmicas, é necessário configurar o canal usando a função e o nome do canal. Consulte as etapas abaixo para ver a implementação prática.
>
>Para saber mais sobre como implementar sequências incorporadas, consulte [Sequências incorporadas](embedded-sequences.md) no AEM Screens.

O exemplo a seguir fornece uma solução focando nos seguintes termos principais:

* a ***canal de sequência principal*** para a sequência global
* ***componentes de*** sequência incorporados dinâmicos para cada parte personalizável localmente da sequência
* ***os*** canais de sequência individuais nos respectivos locais com um  ** papel na exibição que corresponde à  **função *do componente de sequência incorporado*dinâmico.**

>[!NOTE]
>
>Para saber mais sobre a atribuição de canais, consulte **[Atribuição de Canais](channel-assignment.md)** na seção Criação na documentação do AEM Screens.

## Uso de uma sequência incorporada dinâmica {#using-dynamic-embedded-sequence-2}

A seção a seguir explica a criação de uma sequência incorporada dinâmica em um canal AEM Screens.

### Pré-requisitos {#prerequisites}

Antes de implementar essa funcionalidade no start, verifique se você tem os seguintes pré-requisitos prontos para o start implementando sequências incorporadas dinâmicas:

* Criar um projeto da AEM Screens (neste exemplo, **Demo**)

* Criar um canal como **Global** na pasta **Canais**

* Adicione conteúdo ao seu Canal **Global** (*Verifique **Resources.zip**para ver os ativos relevantes*)

A imagem a seguir mostra o projeto **Demo** com o canal **Global** na pasta **Canais**.
![screen_shot_2018-09-07at21032pm](assets/screen_shot_2018-09-07at21032pm.png)

### Recursos {#resources}

Você pode baixar os seguintes recursos (imagens e adicioná-los aos ativos) e usá-los ainda mais como conteúdo de canal para fins de demonstração.

[Obter arquivo](assets/resources.zip)

>[!NOTE]
>
>Para obter informações adicionais sobre como criar um projeto e como criar um canal de sequência, consulte os recursos a seguir:
>
>* **[Criação e gerenciamento de projetos](creating-a-screens-project.md)**
>* **[Gerenciar um Canal](managing-channels.md)**

>



A implementação da sequência incorporada dinâmica em um projeto AEM Screens envolve três tarefas principais:

1. **Configuração da taxonomia do projeto incluindo Canais, Locais e Exibições**
1. **Criação de um agendamento**
1. **Atribuindo Programação a cada exibição**

Siga as etapas abaixo para implementar a funcionalidade:

>[!CAUTION]
>
>Ao implementar sequências incorporadas dinâmicas, tenha cuidado com os campos **Name** e **Title** ao criar canais em cada localização. Siga cuidadosamente as instruções de nomenclatura.

1. **Criar duas pastas de locais.**

   Navegue até a pasta **Locations** no seu projeto AEM Screens e crie duas pastas de localização como **Região A** e **Região B**.

   >[!NOTE]
   >
   >Ao criar a pasta de localização **Região A**, certifique-se de que introduza o campo **Title** como **Região A** e pode deixar o campo **Name** vazio, pelo que o nome **region-a** é selecionado automaticamente.
   >
   >Semelhante, é o caso da criação da pasta de localização **Região B**, como mostrado abaixo:

   ![screen_shot_2018-09-13at23212pm](assets/screen_shot_2018-09-13at23212pm.png)

   >[!NOTE]
   >Para saber como criar um local, consulte **[Criação e gerenciamento de locais](managing-locations.md)**.

1. **Crie dois locais e um Canal em cada pasta de localização.**

   1. Navegue até **Demonstração** —> **Locais** —> **Região A**.
   1. Selecione **Região A** e clique em **+ Criar** na barra de ações.
   1. Selecione **Localização** no assistente com **Título** como **Loja 1**. Da mesma forma, crie outro local do assistente chamado **Loja 2** com **Título** como **Loja 2**. Você pode deixar o campo **Nome** vazio ao criar **Loja 1** e **Loja 2**.
   1. Repita a etapa (b) e selecione **Canal de sequência** do assistente. Digite **Title** como **Região A** e **Nome** como **região** para este canal.

   >[!CAUTION]
   >
   >Certifique-se de que ao criar o canal **Região A**, digite **Título** como **Região A** e **Nome** como **região**.

   ![screen_shot_2018-09-13at22857pm](assets/screen_shot_2018-09-13at22857pm.png)

   Da mesma forma, crie dois locais em **Região B** intitulados como **Loja 3** e **Loja 4**. Além disso, crie um **Canal de sequência** com **Título** como **Região B** e **Nome** como **região**.

   >[!CAUTION]
   >
   >Certifique-se de usar o mesmo nome para os canais criados em **Região A** e **Região B** como **região**.

   ![screen_shot_2018-09-13at24408pm](assets/screen_shot_2018-09-13at24408pm.png)

1. **Criar exibição e Canal em cada localização.**

   1. Navegue até **Demonstração** —> **Locais** —> **Região A** —> **Loja 1**.
   1. Selecione **Loja 1** e clique em **+ Criar** na barra de ações.
   1. Selecione **Display** do assistente e crie **Store1Display.**
   1. Repita a etapa (b) e, desta vez, selecione **Canal de sequência** no assistente. Digite **Title** como **Store1Canal** e **Name** como **store**.

   >[!CAUTION]
   >
   >É importante quando você cria um canal de sequência, o **Title** do canal pode ser o seu requisito, mas o **Name** deve ser o mesmo em todos os canais locais.
   >Neste exemplo, os canais em **Região A** e **Região B** compartilham o mesmo **Nome** como **região** e canais em **Loja 1**, **Loja 2**, &lt;a 12/>A Loja 3 **e** Loja 4 **partilham o mesmo** Nome **que** store **.**

   ![screen_shot_2018-09-19at120206pm](assets/screen_shot_2018-09-19at120206pm.png)

   Da mesma forma, crie uma exibição como **Store2Display** e um canal **Store2Canal** em **Loja 2** (com o nome **store**).

   >[!NOTE]
   >Certifique-se de usar o mesmo nome para os canais criados em **Loja 1** e **Loja 2** como **store**.

   ![screen_shot_2018-09-19at120329pm](assets/screen_shot_2018-09-19at120329pm.png)

   Siga as etapas anteriores para criar um canal e exibi-lo em **Loja 3** e **Loja 4** em **Região B**. Novamente, certifique-se de usar o mesmo **Nome** como **store** ao criar o canal **Store3Canal** e **Store4Canal** respectivamente.

   A imagem a seguir mostra a exibição e o canal em **Loja 3**.

   ![screen_shot_2018-09-19at120448pm](assets/screen_shot_2018-09-19at120448pm.png)

   A imagem a seguir mostra a exibição e o canal em **Loja 4**.

   ![screen_shot_2018-09-19at120552pm](assets/screen_shot_2018-09-19at120552pm.png)

1. **Adicione conteúdo aos Canais em seus respectivos locais.**

   Navegue até **Demo** -> **Locais** -> **Região A** -> **Região A** e clique em **Editar** na barra de ações. Arraste e solte os ativos que deseja adicionar ao seu canal.

   >[!NOTE]
   >Você pode usar o arquivo ***Resources.zip*** da seção **Resources** acima para usar as imagens como ativos para o conteúdo do seu canal.

   ![screen_shot_2018-09-12at12438pm](assets/screen_shot_2018-09-12at12438pm.png)

   Da mesma forma, navegue até **Demo** -> **Locais** -> **Região B** -> **Região B** e clique em **Editar** na barra de ações para arrastar e soltar os ativos no seu canal, conforme mostrado abaixo:

   ![screen_shot_2018-09-12at13133pm](assets/screen_shot_2018-09-12at13133pm.png)

   Siga as etapas anteriores e os recursos para adicionar conteúdo aos seguintes canais:

   * **Canal Store1**
   * **Canal Store2**
   * **Canal Store3**
   * **Canal Store4**

1. **Criar um agendamento**

   Navegue e selecione a pasta **Programações** no seu projeto AEM Screens e clique em **Criar** na barra de ações para criar um novo agendamento.

   A imagem a seguir mostra o **AdSchedule** criado no projeto **Demo**.

   ![screen_shot_2018-09-13at33307pm](assets/screen_shot_2018-09-13at33307pm.png)

1. **Atribuir Canais a uma programação**

   1. Navegue até **Demo** —> **Programações** —> **AdSchedule** e clique em **Painel** na barra de ações.
   1. Clique em **+ Atribuir Canal** do painel **CANAIS ATRIBUÍDOS** para abrir a caixa de diálogo **Atribuição de Canal**.
   1. Selecione **Canal de referência**. por caminho.
   1. Selecione **Caminho do Canal** como **Demo** —> ***Canais*** —> ***Global***.
   1. Digite **Função do Canal** como **GlobalAdSegment**.
   1. Selecione **Eventos suportados** como **Carregamento inicial**, **Ecrã inativo** e **Interação do utilizador**.
   1. Clique em **Salvar**.

   **Atribuir Canal por função para a região:**

   1. Clique em **+ Atribuir Canal** do painel **CANAIS ATRIBUÍDOS** para abrir a caixa de diálogo **Atribuição de Canal**.
   1. Selecione **Canal de referência**. por nome.
   1. Digite **Nome do Canal** como **região***.
   1. Digite **Função do Canal** como **RegionAdSegment**.
   1. Clique em **Salvar**.

   **Atribuir Canal por função para a loja:**

   1. Clique em **+ Atribuir Canal** do painel **CANAIS ATRIBUÍDOS** para abrir a caixa de diálogo **Atribuição de Canal**.
   1. Selecione **Canal de referência**. por nome.
   1. Digite **Nome do Canal** como **store**.
   1. Digite **Função do Canal** como **StoreAdSegment**.
   1. Clique em **Salvar**.

   A imagem a seguir mostra os canais atribuídos por caminho e por função.

   ![screen_shot_2018-09-12at21429pm](assets/screen_shot_2018-09-12at21429pm.png)

1. **Configuração da sequência incorporada dinâmica para o Canal global.**

   Navegue até o Canal **Global** que você criou inicialmente no projeto **Demo**.

   Clique em **Editar** na ação para abrir o editor.

   ![screen_shot_2018-09-13at52754pm](assets/screen_shot_2018-09-13at52754pm.png)

   Arraste e solte dois componentes **Sequência incorporada dinâmica** no editor de canais.

   Abra as propriedades de um dos componentes e digite **Função de Atribuição de Canal** como **RegionAdSegment**.

   Da mesma forma, selecione o outro componente e abra as propriedades para inserir a **Função de Atribuição de Canal** como **StoreAdSegment**.

   ![caneldisplay4](assets/channeldisplay4.gif)

1. **Atribuindo Programação a cada Exibição**

   1. Navegue até cada exibição, como **Demo** —> **Locais** —> **Região A** —>**Loja 1** —>**Loja1Display**.
   1. Clique em **Painel** na ação para abrir o painel de exibição.
   1. Clique em **...** do painel **CANAIS E PROGRAMAS ATRIBUÍDOS** e clique em **+Atribuir agendamento**.
   1. Selecione o caminho para a Programação (por exemplo, aqui, **Demo** —> **Programações** —>**AdSchedule**).
   1. Clique em **Salvar**.

## Visualizando os resultados {#viewing-the-results}

Depois que a configuração para canais e a exibição estiver concluída, inicie o AEM Screens player para visualização do conteúdo.

>[!NOTE]
>
>Para saber mais sobre AEM reprodutor de tela, consulte os seguintes recursos:
>
>* [Downloads do AEM Screens player](https://download.macromedia.com/screens/)
>* [Trabalhar com o AEM Screens Player](working-with-screens-player.md)



A saída a seguir confirma o conteúdo do canal no AEM Screens player, dependendo do caminho de exibição.

**Cenário 1**:

Se você atribuir o caminho de exibição como **Demo** —> **Locais** —> **Região A** —> **Loja 1** —> **Loja1Display**, o seguinte conteúdo será exibido no seu AEM Screens player.

![caneldisplay1](assets/channeldisplay1.gif)

**Cenário 1**:

Se você atribuir o caminho de exibição como **Demo** —> **Locais** —> **Região B** —> **Loja 3** —> **Store3Display**, o seguinte conteúdo será exibido no seu AEM Screens player.

![caneldisplay2](assets/channeldisplay2.gif)

## Restringir usuários e modificar as ACLs {#restricting-users-and-modifying-the-acls}

Você pode criar autores globais, regionais ou locais para editar o conteúdo relevante para eles, ao mesmo tempo que é restringido de editar canais superiores na hierarquia.

É necessário modificar as ACLs para restringir o acesso dos usuários ao conteúdo com base em sua localização.

### Exemplo de caso de uso {#example-use-case}

O exemplo a seguir permite criar três usuários para o projeto de demonstração acima.

Os privilégios são atribuídos a cada grupo da seguinte forma:

**Grupos**:

* **Autor** global: Consiste de usuários que têm acesso a todos os locais e canais no  **** Demoproject e que têm todas as permissões de leitura, gravação e edição.

* **Região-Autor**: Consiste de usuários que têm permissões de leitura, gravação e edição para a  **Região** e a  **Região B**.

* **Autor da loja**: Consiste de usuários que têm permissões de leitura, gravação e edição somente para a  **Loja 1**,  **Loja 2**,  **Loja 3** e  **Loja 4**.

#### Etapas para criar grupos de usuários, usuários e configurar ACLs {#steps-for-creating-user-groups-users-and-setting-up-acls}

>[!NOTE]
>
>Para saber mais detalhes sobre como separar projetos usando ACLs para que cada indivíduo ou equipe gerencie seu próprio projeto, consulte **Configurando ACLs**.

Siga as etapas abaixo para criar grupos, usuários e modificar as ACLs de acordo com as permissões:

1. **Criar grupos**

   1. Navegue até **Adobe Experience Manager**.
   1. Clique em **Ferramentas** —> **Segurança** —> **Grupos**.
   1. Clique em **Criar grupo** e insira **Global-Author** em **ID**.
   1. Clique em **Salvar e fechar**.

   Da mesma forma, crie dois outros grupos, como **Region-Author** e **Store-Author**.

   ![screen_shot_2018-09-17at34008pm](assets/screen_shot_2018-09-17at34008pm.png)

1. **Criar usuários e adicionar usuários a grupos**

   1. Navegue até **Adobe Experience Manager**.
   1. Clique em **Ferramentas** —> **Segurança** —> **Utilizadores**.
   1. Clique em **Criar usuário** e digite **Usuário global** em **ID**.
   1. Digite **Password** e confirme a senha deste usuário.
   1. Clique na guia **Grupos** e digite o nome do grupo em **Selecionar Grupo**, por exemplo, digite **Autor Global** para adicionar **Usuário Global** a esse grupo específico.
   1. Clique em **Salvar e fechar**.

   Da mesma forma, crie dois outros usuários, como **Region-User** e **Store-User**, e adicione-os a **Region-Author** e **Store-Author**, respectivamente.

   >[!NOTE]
   >É uma prática recomendada adicionar usuários em um grupo e depois atribuir permissões a cada grupo específico de usuários.

   ![screen_shot_2018-09-17at34412pm](assets/screen_shot_2018-09-17at34412pm.png)

1. **Adicionar todos os grupos aos contribuidores**

   1. Navegue até **Adobe Experience Manager**.
   1. Clique em **Ferramentas** —> **Segurança** —> **Grupos**.
   1. Selecione **Colaboradores** na lista e selecione **a guia Membros**.
   1. Selecione **Grupo** como **Autor-Global**, **Autor-Região,** e **Autor-Loja** aos contribuidores.
   1. Clique em **Salvar e fechar**.

1. **Acessar permissões para cada grupo**

   1. Navegue até *Useradmin* e use essa interface para modificar as permissões de grupos diferentes.
   1. Procure **Autor Global** e clique na guia **Permissões**, conforme mostrado na figura abaixo.
   1. Da mesma forma, você pode acessar as permissões para **Region-Author** e **Store-Author**.

   ![screen_shot_2018-09-18at73523am](assets/screen_shot_2018-09-18at73523am.png)

1. **Modificando permissões para cada grupo**

   **Para autor global:**

   1. Navegue até a guia **Permissões**
   1. Navegue até ***/content/screens/demo*** e verifique todas as permissões
   1. Navegue até ***/content/screens/demo/location*** e verifique todas as permissões
   1. Navegue até ***/content/screens/demo/location/region-a*** e verifique todas as permissões. Da mesma forma, verifique as permissões para **region-b**.

   Consulte a figura abaixo para entender as etapas:
   ![screen_shot_2018-09-18at115752am](assets/screen_shot_2018-09-18at115752am.png)

   A imagem a seguir mostra que agora o **Usuário Global** tem acesso ao **Canal Global** e às **Regiões A** e **Região B** com todas as quatro lojas, nomeadamente **Loja 1**, **Loja 2&lt;a1 1/>,** Loja 3 **e** Loja 4 **.**

   ![global](assets/global.gif)

   **Para Região-Autor:**

   1. Navegue até a guia **Permissões**.
   1. Navegue até ***/content/screens/demo*** e verifique apenas as permissões **Read**.
   1. Navegue até ***/content/screens/demo/location*** e verifique apenas as permissões **Read**.
   1. Navegue até ***/content/screens/demo/canais*** e desmarque as permissões do canal **Global**.
   1. Navegue até ***/content/screens/demo/location***/***region-a*** e verifique todas as permissões. Da mesma forma, verifique as permissões para **region-b**.

   Consulte a figura abaixo para entender as etapas:

   ![screen_shot_2018-09-18at125158pm](assets/screen_shot_2018-09-18at125158pm.png)

   A imagem a seguir mostra que agora o Usuário da Região tem acesso às **Região A** e **Região B** com todas as quatro lojas, a saber, **Loja 1**, **Loja 2**, **Loja 3** e **Loja 4** mas não acessa o Canal **Global**.

   ![região](assets/region.gif)

   **Para Autor da Loja:**

   1. Navegue até a guia **Permissões**.
   1. Navegue até ***/content/screens/demo*** e verifique apenas as permissões **Read**.
   1. Navegue até ***/content/screens/demo/location*** e verifique apenas as permissões **Read**.
   1. Navegue até ***/content/screens/demo/canais*** e desmarque as permissões do canal **Global**.
   1. Navegue até ***/content/screens/demo/location/region-a*** e verifique apenas as permissões **Read**. Da mesma forma, verifique apenas as permissões **Read** para **region-b**.
   1. Navegue até ***/content/screens/demo/location***/***region-a /store-1*** e verifique todas as permissões. Da mesma forma, verifique as permissões para **store-2, store-3,** e **store-4**.

   Consulte a figura abaixo para entender as etapas:

   ![screen_shot_2018-09-18at12415pm](assets/screen_shot_2018-09-18at12415pm.png)

   A imagem a seguir mostra que agora o **Store-User** tem acesso apenas aos quatro armazenamentos, a saber, **Loja 1**, **Loja 2**, **Loja 3** e **Loja 4**, mas não tem permissões para aceder ao &lt;a10>canais Global **ou região (** Região A **e** Região B **).**

   ![loja](assets/store.gif)

>[!NOTE]
>
>Para saber mais detalhes sobre como configurar permissões, consulte [Configurando ACLs](setting-up-acls.md).

