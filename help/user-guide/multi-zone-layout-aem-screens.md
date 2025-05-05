---
title: Layout de várias zonas
description: Saiba como criar conteúdo com várias zonas e usar vários ativos, como vídeos, imagens e texto, que se combinam em uma única tela no AEM Screens.
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: authoring
noindex: true
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 901ed50e-d3f0-4c85-ad79-6c4595382759
source-git-commit: cdff56f0807f6d5fea4a4b1d545aecb1e80245bb
workflow-type: tm+mt
source-wordcount: '1127'
ht-degree: 0%

---

# Layout de várias zonas {#multi-zone-layout}

A página seguinte descreve o uso do layout de várias zonas e aborda os seguintes tópicos:

* Visão geral
* Criação de layout de várias zonas
* Pré-requisitos
* Utilização de Assets único em uma ou mais regiões
* Uso de conteúdo sequenciado em uma ou mais regiões

## Visão geral {#overview}

O ***Layout de várias zonas*** permite que você crie conteúdo de várias zonas e use vários ativos, como vídeos, imagens e texto, que podem ser combinados em uma única tela. Você pode inserir imagens, vídeos e texto, permitindo que todos se misturem e criem uma experiência digital intuitiva.

De acordo com os requisitos do projeto, às vezes você precisa de várias zonas em um canal e editá-las como uma unidade abrangente. Por exemplo, uma sequência de produtos com um feed de mídia social relacionado que é executado em três zonas separadas em um único canal.

>[!NOTE]
>Em canais de várias zonas, o agendamento no nível do ativo não é recomendado devido a possíveis conflitos e comportamento não intencional. Se a programação no nível do ativo for necessária, crie um canal de sequência separado e aplique a lógica de programação nesse canal. Em seguida, incorpore o canal de sequência no canal de várias regiões.

### Pré-requisitos {#prerequisites}

Antes de começar a implementar essa funcionalidade, verifique se você tem o conhecimento conceitual sobre:

* [Criando um projeto do AEM Screens](https://experienceleague.adobe.com/pt-br/docs/experience-manager-screens/user-guide/authoring/setting-up-projects/creating-a-screens-project)
* [Criando uma Exibição](https://experienceleague.adobe.com/pt-br/docs/experience-manager-screens/user-guide/authoring/setting-up-projects/managing-displays)
* [Atribuição de um Canal a uma Exibição](/help/user-guide/channel-assignment.md)

## Criação de layout de várias zonas {#creating-multi-zone-layout}

Ao criar um canal, é possível usar diferentes modelos para criar zonas no canal. É possível adicionar uma única imagem, vídeo ou canal incorporado que permita a exibição de vários ativos em uma sequência.

**Criando um Canal**

1. Clique no link do Adobe Experience Manager (canto superior esquerdo) e depois em **Screens**. Como alternativa, você pode ir diretamente para: `http://localhost:4502/screens.html/content/screens`.
1. Navegue até a pasta **Canais** e clique em **Criar** na barra de ações.

1. Clique em **Canal de tela dividida 1x2** no assistente **Criar**.

1. Clique em **Avançar** e insira o **título** como **MultiZone**.

1. Clique em **Criar** para concluir a criação do canal.

### Utilização de Assets único em uma ou mais regiões {#using-single-assets-in-one-or-more-zones}

Você pode usar ativos únicos, como uma imagem ou um vídeo, em todas as zonas individuais. Siga as etapas abaixo para a implementação:

1. **Adicionando conteúdo ao canal**

   1. Navegue até **Zonas** > **Canais**> **MultiZone**.
   1. Clique no canal **MultiZone** e clique em **Editar** na barra de ações.

1. **Adicionando imagens ao canal**

   Para reproduzir uma única imagem ou um vídeo em duas zonas, basta arrastar e soltar uma imagem em cada zona no editor de canais, como mostrado na figura abaixo:

   ![imagem](/help/user-guide/assets/multi-zone/multizone-img3.png)

### Uso de conteúdo sequenciado em uma ou mais regiões {#using-sequenced-content-in-one-or-more-zones}

Se quiser que as zonas exibam uma sequência de imagens e um vídeo nas diferentes zonas, siga as etapas abaixo para obter detalhes.

1. **Criando uma Pasta de Canal**

   1. Navegue até **Zonas** > **MultiZona** > **Canais** e clique em **Criar** na barra de ações.
   1. Clique em **Pasta de canais** no assistente **Criar** e clique em **Avançar**.
   1. Insira o título como **EmbeddedChannels** e clique em **Criar**.

   ![screen_shot_2018-12-19at125428pm](assets/screen_shot_2018-12-19at125428pm.png)

1. **Adicionando mais dois canais à Pasta de Canal**

   1. Navegue até **Zonas** > **Canais** > **EmbeddedChannels** e clique em **Criar** na barra de ações.
   1. Clique em **Canal de Sequência** no assistente **Criar** para criar um canal denominado **`Zone1`**.
   1. Clique em **`Zone1`** e em **Editar** na barra de ações.
   1. Arraste e solte algumas imagens neste canal.
   1. Da mesma forma, crie outro canal de sequência chamado **`Zone2`** na pasta **EmbeddedChannels**.
   1. Arraste e solte um vídeo neste canal.

   A figura a seguir mostra os canais **`Zone1`** e **`Zone2`**:

   ![screen_shot_2018-12-19at125930pm](assets/screen_shot_2018-12-19at125930pm.png)

   As imagens adicionadas ao editor do canal de sequência **`Zone1`** são mostradas abaixo:

   ![screen_shot_2018-12-19at125930pm](/help/user-guide/assets/multi-zone/multizone-img4.png)

   O vídeo adicionado ao editor do canal de sequência **`Zone2`** é mostrado abaixo:

   ![screen_shot_2018-12-19at125930pm](/help/user-guide/assets/multi-zone/multizone-img5.png)

1. **Adicionando sequências inseridas (componente) ao canal principal (MultiZone)**

   1. Navegue até **Zonas** > **Canais** > **MultiZone**.
   1. Clique em **Editar** na barra de ações.
   1. Arraste e solte o componente **Sequência Incorporada** em ambas as zonas.
   1. Clique na sequência incorporada em uma das zonas.
   1. Clique no ícone **Configurar** (chave inglesa) para uma das sequências inseridas no editor.
   1. Clique no caminho do canal como **Zonas** > **Canais** > **EmbeddedChannels** > **`Zone1`**, conforme mostrado na figura abaixo.
   1. Da mesma forma, adicione **`Zone2`** a outro componente de sequência inserido no editor.

      ![imagem](/help/user-guide/assets/multi-zone/multizone-3.png)

### Criação de um local e uma exibição {#creating-location}

Crie um local e uma exibição para exibir o conteúdo no AEM Screens Player.

1. **Criando um Local**

   1. Navegue até a pasta **Zonas** > **Locais**.
   1. Clique na pasta **Locais** e clique em **Criar** na barra de ações.
   1. Clique em **Local** no assistente **Criar** e em **Avançar**.
   1. Insira o **Título** como **SanJose** e clique em **Criar**.

1. **Criando uma Exibição**

   1. Navegue até a pasta **Zonas** > **Locais**.
   1. Clique no local **SanJose** e clique em **Criar** na barra de ações.
   1. Clique em **Exibir** do assistente **Criar** e clique em **Avançar**.
   1. Insira o **Título** como **Lobby** e clique em **Criar**.

### Atribuição de canais à exibição {#channel-channel}

Atribua os canais à exibição para visualizar o conteúdo. Siga as etapas abaixo para atribuir o canal à exibição.

1. **Atribuindo canal à exibição**

   1. Navegue até **Zonas** > **Locais** > **SanJose**> **Lobby**.
   1. Clique na exibição **Lobby** e clique em **Atribuir canal** na barra de ações.
   1. Insira o caminho para o canal **MultiZone** em **Caminho do Canal**.
   1. Defina os **Eventos com Suporte** como **Carregamento Inicial**, **Tela Inativa** e **Timer**.
   1. Clique em **Salvar**.

      ![imagem](/help/user-guide/assets/multi-zone/multizone-img9.png)
   1. Da mesma forma, atribua os outros dois canais inseridos (**`Zone1`** e **`Zone2`**) a esta exibição.
   1. Depois de atribuir todos os três canais à exibição **Lobby**, você poderá exibir os canais atribuídos no painel de exibição.

      ![imagem](/help/user-guide/assets/multi-zone/multizone-img8.png)


      >[!IMPORTANT]
      >
      >Depois de atribuir o canal principal (neste caso, **MultiZone**) à exibição, é obrigatório atribuir os outros dois canais inseridos **`Zone1`** e **`Zone2`** também à mesma exibição.

### Registrando o dispositivo {#registering-device}

Depois de configurar um local e uma exibição, siga as etapas abaixo para registrar o dispositivo e atribuir a exibição ao dispositivo.

1. **Registrando o Dispositivo**

   1. Navegue até a pasta **Zonas** > **Dispositivos**.
   1. Clique na pasta **Dispositivos** e clique em **Gerenciador de Dispositivos** na barra de ações.
   1. Clique em **Device Registration** e clique no dispositivo pendente da lista.

      >[!NOTE]
      > O título do dispositivo deve corresponder ao token do dispositivo (campo **Token**) exibido na guia **Registro de Dispositivo**.

   1. Se o título corresponder ao token do dispositivo, clique no dispositivo e em **Registrar Dispositivo** na barra de ações.
   1. Se o código de registro corresponder ao código na guia **Registro de Dispositivo** do Screens player, clique em **Validar** na barra de ações.

      ![imagem](/help/user-guide/assets/multi-zone/multizone-img6.png)
   1. Insira o **Título** como **`Chrome-Device1`** e clique em **Registrar**.
   1. Clique em **Atribuir exibição** e clique no caminho para a configuração do dispositivo.

   >[!NOTE]
   >Se estiver tentando exibir o conteúdo no reprodutor do Screens, clique em **Atualizar Conteúdo Offline** no painel de canais para cada um dos canais atribuídos à exibição.

### Exibir o resultado {#viewing-the-result}

Quando você implementa layouts de várias regiões usando as etapas anteriores, a seguinte saída é exibida.

Marque o reprodutor do Screens para exibir a saída que exibe o conteúdo em duas zonas diferentes. As zonas esquerda e direita (ambas usam uma sequência incorporada como um componente).

A zona esquerda é um canal de sequência e a zona direita inclui um vídeo.

![novo2-1](/help/user-guide/assets/multi-zone/Multi-gif.gif)
