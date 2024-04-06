---
title: Layout de várias zonas
seo-title: Multi-zone Layout
description: O layout de várias zonas permite criar conteúdo de várias zonas e usar vários ativos, como vídeos, imagens e texto, que podem ser combinados em uma única tela. Siga esta página para saber mais.
seo-description: Multi-zone Layout allows you to create multiple zone content and use a variety of assets such as videos, images and text that can be combined in a single screen. Follow this page to learn more.
uuid: 2ad689ef-700a-4eed-b5e2-fc57f2288388
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: authoring
discoiquuid: 4c073172-d93c-4b73-87ab-0b08789193a3
noindex: true
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 901ed50e-d3f0-4c85-ad79-6c4595382759
source-git-commit: 299018986ae58ecbdb51a30413222a9682fffc76
workflow-type: tm+mt
source-wordcount: '1112'
ht-degree: 0%

---

# Layout de várias zonas {#multi-zone-layout}

A página seguinte descreve o uso do layout de várias zonas e aborda os seguintes tópicos:

* Visão geral
* Criação de layout de várias zonas
* Pré-requisitos
* Uso de ativos únicos em uma ou mais regiões
* Uso de conteúdo sequenciado em uma ou mais regiões

## Visão geral {#overview}

***Layout de várias zonas*** O permite criar vários conteúdos de zona e usar vários ativos, como vídeos, imagens e texto, que podem ser combinados em uma única tela. Você pode inserir imagens, vídeos e texto, permitindo que todos se misturem e criem uma experiência digital intuitiva.

De acordo com os requisitos do projeto, às vezes você precisa de várias zonas em um canal e editá-las como uma unidade abrangente. Por exemplo, uma sequência de produtos com um feed de mídia social relacionado que é executado em três zonas separadas em um único canal.


### Pré-requisitos {#prerequisites}

Antes de começar a implementar essa funcionalidade, verifique se você tem o conhecimento conceitual sobre:

* [Criação de um projeto do AEM Screens](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/authoring/setting-up-projects/creating-a-screens-project.html)
* [Criação de uma exibição](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/authoring/setting-up-projects/managing-displays.html)
* [Atribuição de um Canal a uma Exibição](/help/user-guide/channel-assignment.md)

## Criação de layout de várias zonas {#creating-multi-zone-layout}

Ao criar um canal, é possível usar diferentes modelos para criar zonas no canal. Você pode adicionar uma única imagem, vídeo ou um canal incorporado que permite que vários ativos sejam exibidos em uma sequência.

**Criação de um canal**

1. Selecione o link Adobe Experience Manager (canto superior esquerdo) e **Screens**. Como alternativa, você pode ir diretamente para: `http://localhost:4502/screens.html/content/screens`.
1. Navegue até **Canais** e clique em **Criar** na barra de ações.

1. Selecionar **Canal de tela dividida 1x2** do **Criar** assistente.

1. Clique em **Próxima** e insira o **título** as **MultiZone**.

1. Clique em **Criar** para concluir a criação do canal.

### Uso de ativos únicos em uma ou mais regiões {#using-single-assets-in-one-or-more-zones}

Você pode usar ativos únicos, como uma imagem ou um vídeo, em todas as zonas individuais. Siga as etapas abaixo para a implementação:

1. **Adicionar conteúdo ao canal**

   1. Navegue até **Zonas** > **Canais**> **MultiZone**.
   1. Selecione o **MultiZone** canal e clique em **Editar** na barra de ações para abrir o editor.

1. **Adicionar imagens ao canal**

   Para reproduzir uma única imagem ou um vídeo em duas zonas, basta arrastar e soltar uma imagem em cada zona no editor de canais, como mostrado na figura abaixo:

   ![imagem](/help/user-guide/assets/multi-zone/multizone-img3.png)

### Uso de conteúdo sequenciado em uma ou mais regiões {#using-sequenced-content-in-one-or-more-zones}

Se quiser que as zonas exibam uma sequência de imagens e um vídeo nas diferentes zonas, siga as etapas abaixo para obter detalhes.

1. **Criação de uma pasta de canal**

   1. Navegue até **Zonas** > **MultiZone** > **Canais** e clique em **Criar** na barra de ações.
   1. Selecionar **Pasta de canais** do **Criar** e clique em **Próxima**.
   1. Insira o título como **EmbeddedChannels** e clique em **Criar**.

   ![screen_shot_2018-12-19at125428pm](assets/screen_shot_2018-12-19at125428pm.png)

1. **Adição de mais dois canais à Pasta de canal**

   1. Navegue até **Zonas** > **Canais** > **EmbeddedChannels** e clique em **Criar** na barra de ações.
   1. Selecionar **Canal de sequência** do **Criar** assistente para criar um canal intitulado como **Zona1**.
   1. Selecionar **Zona1** e clique em **Editar** na barra de ações para abrir o editor.
   1. Arraste e solte algumas imagens neste canal.
   1. Da mesma forma, crie outro canal de sequência chamado de **Zona2** in **EmbeddedChannels** pasta.
   1. Arraste e solte um vídeo neste canal.

   A figura a seguir mostra os canais **Zona1** e **Zona2**:

   ![screen_shot_2018-12-19at125930pm](assets/screen_shot_2018-12-19at125930pm.png)

   As imagens adicionadas ao editor de **Zona1** canal de sequência são mostrados abaixo:

   ![screen_shot_2018-12-19at125930pm](/help/user-guide/assets/multi-zone/multizone-img4.png)

   O vídeo foi adicionado ao editor do **Zona2** o canal de sequência é mostrado abaixo:

   ![screen_shot_2018-12-19at125930pm](/help/user-guide/assets/multi-zone/multizone-img5.png)

1. **Adicionar sequências incorporadas (componente) ao canal principal (MultiZone)**

   1. Navegue até **Zonas** > **Canais** > **MultiZone**.
   1. Clique em **Editar** na barra de ações para abrir o editor.
   1. Arraste e solte a **Sequência incorporada** componente às duas regiões.
   1. Selecione a sequência incorporada em uma das zonas.
   1. Clique em **Configurar** (chave inglesa) para uma das sequências incorporadas no editor.
   1. Selecione o caminho do canal como **Zonas** > **Canais** > **EmbeddedChannels** > **Zona1**, conforme mostrado na figura abaixo.
   1. Da mesma forma, adicione a variável **Zona2** para outro componente de sequência incorporado no editor.

      ![imagem](/help/user-guide/assets/multi-zone/multizone-3.png)

### Criação de um local e uma exibição {#creating-location}

Crie um local e uma exibição para exibir o conteúdo no reprodutor do Screens.

1. **Criação de um local**

   1. Navegue até **Zonas** > **Localizações** pasta.
   1. Selecione o **Localizações** e clique em **Criar** na barra de ações.
   1. Selecionar **Localização** do **Criar** e clique em **Próxima**.
   1. Insira o **Título** as **San Jose** e clique em **Criar**.

1. **Criação de uma exibição**

   1. Navegue até **Zonas** > **Localizações** pasta.
   1. Selecione o **San Jose** e clique em **Criar** na barra de ações.
   1. Selecionar **Exibir** do **Criar** e clique em **Próxima**.
   1. Insira o **Título** as **Lobby** e clique em **Criar**.

### Atribuição de canais à exibição {#channel-channel}

Atribua os canais à exibição para visualizar o conteúdo. Siga as etapas abaixo para atribuir o canal à exibição.

1. **Atribuição de canal à exibição**

   1. Navegue até **Zonas** > **Localizações** > **San Jose**> **Lobby**.
   1. Selecione o **Lobby** e clique em **Atribuir canal** na barra de ações.
   1. Insira o caminho para o **MultiZone** entrada de canal **Caminho do canal**.
   1. Defina o **Eventos suportados** as **Carga inicial**, **Tela inativa**, e **Temporizador**.
   1. Clique em **Salvar**.

      ![imagem](/help/user-guide/assets/multi-zone/multizone-img9.png)
   1. Da mesma forma, você deve atribuir os outros dois canais incorporados (**Zona1** e **Zona2**) para essa exibição.
   1. Depois de atribuir todos os três canais à variável **Lobby** ser capaz de visualizar os canais atribuídos a partir do painel de exibição.

      ![imagem](/help/user-guide/assets/multi-zone/multizone-img8.png)


      >[!IMPORTANT]
      >
      > Depois de atribuir o canal principal (neste caso, **MultiZone**) para a exibição, é obrigatório atribuir os outros dois canais incorporados **Zona1** e **Zona2** também para a mesma exibição.

### Registrando o dispositivo {#registering-device}

Depois de configurar um local e uma exibição, siga as etapas abaixo para registrar o dispositivo e atribuir a exibição ao dispositivo.

1. **Registrando o dispositivo**

   1. Navegue até **Zonas** > **Dispositivos** pasta.
   1. Selecione o **Dispositivos** e clique em **Gerenciador de dispositivos** na barra de ações.
   1. Clique em **Registro do dispositivo** e selecione o dispositivo pendente na lista.
      >[!NOTE]
      > O título do dispositivo deve corresponder ao token do dispositivo (**Token** campo) exibido na **Registro do dispositivo** guia.
   1. Se o título corresponder ao token do dispositivo, selecione o dispositivo e clique em **Registrar dispositivo** na barra de ações.
   1. Se o código de registro corresponder ao código no reprodutor do Screens **Registro do dispositivo** clique em **Validar** na barra de ações.
      ![imagem](/help/user-guide/assets/multi-zone/multizone-img6.png)
   1. Insira o **Título** as **Chrome-Device1** e clique em **Registrar**.
   1. Selecionar **Atribuir exibição** e selecione o caminho para a configuração do dispositivo.

   >[!NOTE]
   >Se estiver tentando exibir o conteúdo no reprodutor do Screens, clique em **Atualizar conteúdo offline** no painel do canal para cada um dos canais atribuídos à exibição.

### Exibir o resultado {#viewing-the-result}

Depois de implementar layouts de várias regiões usando as etapas anteriores, a seguinte saída é exibida.

Marque o reprodutor do Screens para exibir a saída que exibe o conteúdo em duas zonas diferentes. As zonas esquerda e direita (ambas usam uma sequência incorporada como um componente).

A zona esquerda é um canal de sequência e a zona direita inclui um vídeo.

![novo2-1](/help/user-guide/assets/multi-zone/Multi-gif.gif)
