---
title: Layout de várias zonas
seo-title: Layout de várias zonas
description: O Layout de várias zonas permite que você crie conteúdo de várias zonas e use uma variedade de ativos, como vídeos, imagens e texto, que podem ser combinados em uma única tela. Siga esta página para saber mais.
seo-description: O Layout de várias zonas permite que você crie conteúdo de várias zonas e use uma variedade de ativos, como vídeos, imagens e texto, que podem ser combinados em uma única tela. Siga esta página para saber mais.
uuid: 2ad689ef-700a-4eed-b5e2-fc57f2288388
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: authoring
discoiquuid: 4c073172-d93c-4b73-87ab-0b08789193a3
noindex: true
feature: Telas de criação
role: Admin, Developer
level: Intermediate
exl-id: 901ed50e-d3f0-4c85-ad79-6c4595382759
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '1199'
ht-degree: 6%

---

# Layout de várias zonas {#multi-zone-layout}

A página a seguir descreve o uso do layout de várias zonas e aborda os seguintes tópicos:

* Visão geral
* Criação de layout de várias zonas
* Pré-requisitos
* Uso de ativos únicos em uma ou mais zonas
* Uso de conteúdo sequenciado em uma ou mais zonas

## Visão geral {#overview}

***O*** Layout de várias zonas permite que você crie conteúdo de várias zonas e use uma variedade de ativos, como vídeos, imagens e texto, que podem ser combinados em uma única tela. Você pode extrair imagens, vídeos e texto, permitindo que tudo se misture e crie uma experiência digital intuitiva.

De acordo com os requisitos do projeto, às vezes você precisa usar várias zonas em um canal e editá-las como uma unidade abrangente. Por exemplo, uma sequência de produtos com um feed de redes sociais relacionado executado em três zonas separadas em um único canal.


### Pré-requisitos {#prerequisites}

Antes de implementar esta funcionalidade, verifique se você tem conhecimento conceitual sobre:

* [Criação de um projeto do AEM Screens](https://docs.adobe.com/content/help/en/experience-manager-screens/user-guide/authoring/setting-up-projects/creating-a-screens-project.html)
* [Criação de uma exibição](https://docs.adobe.com/content/help/en/experience-manager-screens/user-guide/authoring/setting-up-projects/managing-displays.html)
* [Atribuição de um canal a uma exibição](https://docs.adobe.com/content/help/en/experience-manager-screens/user-guide/authoring/setting-up-projects/channel-assignment.html)

## Criação de layout de várias zonas {#creating-multi-zone-layout}

Ao criar um canal, você pode usar modelos diferentes para criar zonas no seu canal. É possível adicionar uma única imagem, vídeo ou canal incorporado que permite que vários ativos sejam exibidos em uma sequência.

**Criação de um canal**

1. Selecione o link do Adobe Experience Manager (parte superior esquerda) e o **Screens**. Como alternativa, você pode acessar diretamente: `http://localhost:4502/screens.html/content/screens`.
1. Navegue até a pasta **Channels** e clique em **Create** na barra de ações.

1. Selecione **1x2 Split Screen Channel** no assistente **Create**.

1. Clique em **Next** e insira o **title** como **MultiZone**.

1. Clique em **Criar** para concluir a criação do canal.

### Uso de ativos únicos em uma ou mais zonas {#using-single-assets-in-one-or-more-zones}

Você pode usar ativos únicos, como uma imagem ou um vídeo em todas as zonas individuais. Siga as etapas abaixo para implementação:

1. **Adicionar conteúdo ao canal**

   1. Navegue até **Zonas** —> **Canais**—> **MultiZone**.
   1. Selecione o canal **MultiZone** e clique em **Editar** na barra de ações para abrir o editor.

1. **Adicionar imagens ao canal**

   Para reproduzir uma única imagem ou um vídeo em duas zonas, basta arrastar e soltar uma imagem em cada zona no editor de canal, conforme mostrado na figura abaixo:

   ![imagem](/help/user-guide/assets/multi-zone/multizone-img3.png)

### Uso de conteúdo sequenciado em uma ou mais zonas {#using-sequenced-content-in-one-or-more-zones}

Se desejar que as zonas exibam a sequência de imagens e um vídeo nas diferentes zonas, siga as etapas abaixo para obter detalhes.

1. **Criação de uma pasta de canal**

   1. Navegue até **Zonas** —> **MultiZone** —> **Canais** e clique em **Criar** na barra de ações.
   1. Selecione **Channels Folder** no assistente **Create** e clique em **Next**.
   1. Insira o título como **EmbeddedChannels** e clique em **Create**.

   ![screen_shot_2018-12-19at125428pm](assets/screen_shot_2018-12-19at125428pm.png)

1. **Adicionar mais dois canais à pasta Canal**

   1. Navegue até **Zonas** —> **Canais** —> **Canais Embutidos** e clique em **Criar** na barra de ações.
   1. Selecione **Canal de sequência** no assistente **Criar** para criar um canal chamado **Zona1**.
   1. Selecione **Zone1** e clique em **Editar** na barra de ações para abrir o editor.
   1. Arraste e solte algumas imagens neste canal.
   1. Da mesma forma, crie outro canal de sequência chamado **Zone2** na pasta **EmbeddedChannels**.
   1. Arraste e solte um vídeo neste canal.

   A figura a seguir mostra os canais **Zone1** e **Zone2**:

   ![screen_shot_2018-12-19at125930pm](assets/screen_shot_2018-12-19at125930pm.png)

   As imagens adicionadas ao editor do canal de sequência **Zone1** são mostradas abaixo:

   ![screen_shot_2018-12-19at125930pm](/help/user-guide/assets/multi-zone/multizone-img4.png)

   O vídeo adicionado ao editor do canal de sequência **Zone2** é mostrado abaixo:

   ![screen_shot_2018-12-19at125930pm](/help/user-guide/assets/multi-zone/multizone-img5.png)

1. **Adicionar sequências incorporadas (componente) ao canal principal (MultiZone)**

   1. Navegue até **Zones** —> **Canais** —> **MultiZone**.
   1. Clique em **Editar** na barra de ações para abrir o editor.
   1. Arraste e solte o componente **Sequência incorporada** em ambas as zonas.
   1. Selecione a sequência incorporada em uma das zonas.
   1. Clique no ícone **Configurar** (chave) para uma das sequências incorporadas no editor.
   1. Selecione o caminho do canal como **Zones** —> **Channels** —> **EmbeddedChannels** —> **Zone1**, conforme mostrado na figura abaixo.
   1. Da mesma forma, adicione o **Zone2** a outro componente de sequência incorporado no editor.

      ![imagem](/help/user-guide/assets/multi-zone/multizone-3.png)

### Criação de uma localização e uma exibição {#creating-location}

Você deve criar um local e uma exibição para exibir o conteúdo no player do Screens. Siga as etapas abaixo para criar um local e uma exibição.

1. **Criação de uma localização**

   1. Navegue até a pasta **Zonas** —> **Localizações**.
   1. Selecione a pasta **Localizações** e clique em **Criar** na barra de ações.
   1. Selecione **Local** no assistente **Criar** e clique em **Próximo**.
   1. Insira o **Título** como **SanJose** e clique em **Criar**.

1. **Criação de uma exibição**

   1. Navegue até a pasta **Zonas** —> **Localizações**.
   1. Selecione o local **SanJose** e clique em **Criar** na barra de ações.
   1. Selecione **Exibir** no assistente **Criar** e clique em **Próximo**.
   1. Insira o **Título** como **Lobby** e clique em **Criar**.

### Atribuição de canais à exibição {#channel-channel}

Você deve atribuir os canais à exibição para visualizar o conteúdo. Siga as etapas abaixo para atribuir o canal à exibição.

1. **Atribuição de canal à exibição**

   1. Navegue até **Zonas** —> **Localizações** —> **SanJose**—> **Lobby**.
   1. Selecione a exibição **Lobby** e clique em **Atribuir canal** na barra de ações.
   1. Insira o caminho para o canal **MultiZone** em **Caminho do Canal**.
   1. Defina **Eventos Suportados** como **Carga Inicial**, **Tela Inativa** e **Temporizador**.
   1. Clique em **Salvar**.

      ![imagem](/help/user-guide/assets/multi-zone/multizone-img9.png)
   1. Da mesma forma, você deve atribuir os outros dois canais incorporados (**Zone1** e **Zone2**) a essa exibição.
   1. Depois de atribuir todos os três canais à exibição **Lobby**, você deve conseguir exibir os canais atribuídos no painel de exibição.

      ![imagem](/help/user-guide/assets/multi-zone/multizone-img8.png)


      >[!IMPORTANT]
      >
      > Depois de atribuir o canal principal (neste caso, **MultiZone**) à exibição, é obrigatório atribuir os outros dois canais incorporados **Zone1** e **Zone2** também à mesma exibição.

### Registrando o dispositivo {#registering-device}

Depois de configurar um local e uma exibição, siga as etapas abaixo para registrar o dispositivo e atribuir a exibição ao dispositivo.

1. **Registrando o dispositivo**

   1. Navegue até **Zonas** —> **Dispositivos** pasta.
   1. Selecione a pasta **Dispositivos** e clique em **Gerenciador de Dispositivos** na barra de ações.
   1. Clique em **Device Registration** e selecione o dispositivo pendente na lista.

      >[!NOTE]
      > O título do dispositivo deve corresponder ao token do dispositivo (campo **Token**) exibido na guia **Device Registration**.
   1. Se o título corresponder ao token do dispositivo, selecione o dispositivo e clique em **Registrar dispositivo** na barra de ações.
   1. Se o código de registro corresponder ao código no player do Screens **Registro do dispositivo**, clique em **Validar** na barra de ações.
      ![imagem](/help/user-guide/assets/multi-zone/multizone-img6.png)
   1. Insira o **Title** como **Chrome-Device1** e clique em **Register**.
   1. Selecione **Atribuir exibição** e selecione o caminho para a configuração do dispositivo.

   >[!NOTE]
   >Se você estiver tentando exibir o conteúdo no player do Screens, clique em **Atualizar conteúdo offline** no painel do canal para cada um dos canais atribuídos à exibição.

### Como visualizar o resultado {#viewing-the-result}

Depois de implementar layouts de várias zonas usando as etapas anteriores, a saída a seguir é exibida.

Marque o player do Screens para exibir a saída que exibe o conteúdo em duas zonas diferentes. As zonas esquerda e direita (ambas usam a sequência incorporada como um componente).

A zona esquerda é um canal de sequência e a zona direita inclui um vídeo.

![new2-1](/help/user-guide/assets/multi-zone/Multi-gif.gif)
