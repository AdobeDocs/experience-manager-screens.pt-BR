---
title: Layout de várias zonas
seo-title: Multi-zone Layout
description: O Layout de várias zonas permite que você crie conteúdo de várias zonas e use vários ativos, como vídeos, imagens e texto, que podem ser combinados em uma única tela. Siga esta página para saber mais.
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
source-git-commit: 10a4918eeb56df5e8542bbc2e8806f766a86f781
workflow-type: tm+mt
source-wordcount: '1129'
ht-degree: 5%

---

# Layout de várias zonas {#multi-zone-layout}

A página a seguir descreve o uso do layout de várias zonas e aborda os seguintes tópicos:

* Visão geral
* Criação de layout de várias zonas
* Pré-requisitos
* Uso de ativos únicos em uma ou mais zonas
* Uso de conteúdo sequenciado em uma ou mais zonas

## Visão geral {#overview}

***Layout de várias zonas*** O permite criar conteúdo de várias zonas e usar vários ativos, como vídeos, imagens e texto, que podem ser combinados em uma única tela. Você pode extrair imagens, vídeos e texto, permitindo que tudo se misture e crie uma experiência digital intuitiva.

De acordo com os requisitos do projeto, às vezes você precisa usar várias zonas em um canal e editá-las como uma unidade abrangente. Por exemplo, uma sequência de produtos com um feed de redes sociais relacionado executado em três zonas separadas em um único canal.


### Pré-requisitos {#prerequisites}

Antes de implementar esta funcionalidade, verifique se você tem conhecimento conceitual sobre:

* [Criação de um projeto do AEM Screens](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/authoring/setting-up-projects/creating-a-screens-project.html)
* [Criação de uma exibição](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/authoring/setting-up-projects/managing-displays.html)
* [Atribuição de um canal a uma exibição](/help/user-guide/channel-assignment.md)

## Criação de layout de várias zonas {#creating-multi-zone-layout}

Ao criar um canal, você pode usar modelos diferentes para criar zonas no seu canal. É possível adicionar uma única imagem, vídeo ou canal incorporado que permite que vários ativos sejam exibidos em uma sequência.

**Criação de um canal**

1. Selecione o link do Adobe Experience Manager (parte superior esquerda) e o **Screens**. Como alternativa, você pode acessar diretamente: `http://localhost:4502/screens.html/content/screens`.
1. Navegar para **Canais** e clique em **Criar** na barra de ações.

1. Selecionar **Canal de tela dividida 1x2** do **Criar** assistente.

1. Clique em **Próximo** e insira o **título** as **MultiZone**.

1. Clique em **Criar** para concluir a criação do canal.

### Uso de ativos únicos em uma ou mais zonas {#using-single-assets-in-one-or-more-zones}

Você pode usar ativos únicos, como uma imagem ou um vídeo em todas as zonas individuais. Siga as etapas abaixo para implementação:

1. **Adicionar conteúdo ao canal**

   1. Navegar para **Zonas** —> **Canais**—> **MultiZone**.
   1. Selecione o **MultiZone** e clique em **Editar** na barra de ações para abrir o editor.

1. **Adicionar imagens ao canal**

   Para reproduzir uma única imagem ou um vídeo em duas zonas, basta arrastar e soltar uma imagem em cada zona no editor de canal, conforme mostrado na figura abaixo:

   ![imagem](/help/user-guide/assets/multi-zone/multizone-img3.png)

### Uso de conteúdo sequenciado em uma ou mais zonas {#using-sequenced-content-in-one-or-more-zones}

Se desejar que as zonas exibam a sequência de imagens e um vídeo nas diferentes zonas, siga as etapas abaixo para obter detalhes.

1. **Criação de uma pasta de canal**

   1. Navegar para **Zonas** —> **MultiZone** —> **Canais** e clique em **Criar** na barra de ações.
   1. Selecionar **Pasta Canais** do **Criar** e clique em **Próximo**.
   1. Insira o título como **Canais incorporados** e clique em **Criar**.

   ![screen_shot_2018-12-19at125428pm](assets/screen_shot_2018-12-19at125428pm.png)

1. **Adicionar mais dois canais à pasta Canal**

   1. Navegar para **Zonas** —> **Canais** —> **Canais incorporados** e clique em **Criar** na barra de ações.
   1. Selecionar **Canal de sequência** do **Criar** assistente para criar um canal chamado como **Zona1**.
   1. Selecionar **Zona1** e clique em **Editar** na barra de ações para abrir o editor.
   1. Arraste e solte algumas imagens neste canal.
   1. Da mesma forma, crie outro canal de sequência chamado como **Zona2** em **Canais incorporados** pasta.
   1. Arraste e solte um vídeo neste canal.

   A figura a seguir mostra os canais **Zona1** e **Zona2**:

   ![screen_shot_2018-12-19at125930pm](assets/screen_shot_2018-12-19at125930pm.png)

   As imagens adicionadas ao editor de **Zona1** os canais de sequência são mostrados abaixo:

   ![screen_shot_2018-12-19at125930pm](/help/user-guide/assets/multi-zone/multizone-img4.png)

   O vídeo adicionado ao editor de **Zona2** o canal de sequência é mostrado abaixo:

   ![screen_shot_2018-12-19at125930pm](/help/user-guide/assets/multi-zone/multizone-img5.png)

1. **Adicionar sequências incorporadas (componente) ao canal principal (MultiZone)**

   1. Navegar para **Zonas** —> **Canais** —> **MultiZone**.
   1. Clique em **Editar** na barra de ações para abrir o editor.
   1. Arraste e solte a **Sequência incorporada** para ambas as zonas.
   1. Selecione a sequência incorporada em uma das zonas.
   1. Clique no botão **Configurar** ícone (chave) para uma das sequências incorporadas no editor.
   1. Selecione o caminho do canal como **Zonas** —> **Canais** —> **Canais incorporados** —> **Zona1**, conforme mostrado na figura abaixo.
   1. Da mesma forma, adicione o **Zona2** para outro componente de sequência incorporado no editor.

      ![imagem](/help/user-guide/assets/multi-zone/multizone-3.png)

### Criação de uma localização e uma exibição {#creating-location}

Crie um local e uma exibição para exibir o conteúdo no player do Screens.

1. **Criação de uma localização**

   1. Navegar para **Zonas** —> **Localizações** pasta.
   1. Selecione o **Localizações** e clique em **Criar** na barra de ações.
   1. Selecionar **Localização** do **Criar** e clique em **Próximo**.
   1. Insira o **Título** as **SanJose** e clique em **Criar**.

1. **Criação de uma exibição**

   1. Navegar para **Zonas** —> **Localizações** pasta.
   1. Selecione o **SanJose** local e clique em **Criar** na barra de ações.
   1. Selecionar **Exibir** do **Criar** e clique em **Próximo**.
   1. Insira o **Título** as **Lobby** e clique em **Criar**.

### Atribuição de canais à exibição {#channel-channel}

Atribua os canais à exibição para exibir o conteúdo. Siga as etapas abaixo para atribuir o canal à exibição.

1. **Atribuição de canal à exibição**

   1. Navegar para **Zonas** —> **Localizações** —> **SanJose**—> **Lobby**.
   1. Selecione o **Lobby** exibir e clicar em **Atribuir canal** na barra de ações.
   1. Insira o caminho para o **MultiZone** no canal em **Caminho do canal**.
   1. Defina as **Eventos compatíveis** as **Carga inicial**, **Tela Inativa** e **Temporizador**.
   1. Clique em **Salvar**.

      ![imagem](/help/user-guide/assets/multi-zone/multizone-img9.png)
   1. Da mesma forma, você deve atribuir os outros dois canais incorporados (**Zona1** e **Zona2**) para essa exibição.
   1. Depois de atribuir os três canais à **Lobby** , é possível exibir os canais atribuídos no painel de exibição.

      ![imagem](/help/user-guide/assets/multi-zone/multizone-img8.png)


      >[!IMPORTANT]
      >
      > Depois de atribuir o canal principal (nesse caso, **MultiZone**) à exibição, é obrigatório atribuir os outros dois canais incorporados **Zona1** e **Zona2** também para a mesma exibição.

### Registrando o dispositivo {#registering-device}

Depois de configurar um local e uma exibição, siga as etapas abaixo para registrar o dispositivo e atribuir a exibição ao dispositivo.

1. **Registrando o dispositivo**

   1. Navegar para **Zonas** —> **Dispositivos** pasta.
   1. Selecione o **Dispositivos** e clique em **Gerenciador de dispositivos** na barra de ações.
   1. Clique em **Registro do dispositivo** e selecione o dispositivo pendente na lista.

      >[!NOTE]
      > O título do dispositivo deve corresponder ao token do dispositivo (**Token** ) exibido na **Registro do dispositivo** guia .
   1. Se o título corresponder ao token do dispositivo, selecione o dispositivo e clique em **Registrar dispositivo** na barra de ações.
   1. Se o código de registro corresponder ao código no player do Screens **Registro do dispositivo** clique em **Validar** na barra de ações.
      ![imagem](/help/user-guide/assets/multi-zone/multizone-img6.png)
   1. Insira o **Título** as **Chrome-Device1** e clique em **Registrar**.
   1. Selecionar **Atribuir exibição** e selecione o caminho para a configuração do dispositivo.

   >[!NOTE]
   >Se você estiver tentando exibir o conteúdo no player do Screens, clique em **Atualizar conteúdo offline** no painel de canais para cada um dos canais atribuídos à exibição.

### Como visualizar o resultado {#viewing-the-result}

Depois de implementar layouts de várias zonas usando as etapas anteriores, a saída a seguir é exibida.

Marque o player do Screens para exibir a saída que exibe o conteúdo em duas zonas diferentes. As zonas esquerda e direita (ambas usam uma sequência incorporada como um componente).

A zona esquerda é um canal de sequência e a zona direita inclui um vídeo.

![new2-1](/help/user-guide/assets/multi-zone/Multi-gif.gif)
