---
title: Criando e Gerenciando Exibições
seo-title: Managing Displays
description: Siga esta página para saber mais sobre como criar uma nova exibição e configuração de dispositivo. Além disso, saiba mais sobre o painel de exibição.
seo-description: Follow this page to learn about creating a new display and device config. Additionally, learn about the display dashboard.
uuid: dfde0740-5c8b-4e6c-bc83-bf8fbb31a16a
contentOwner: Jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: f8e2e7a3-f3a1-4c35-b055-166752c3fb86
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: c55dc128-208d-4379-95a8-60a39d495dc0
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '752'
ht-degree: 1%

---

# Criando e Gerenciando Exibições {#creating-and-managing-displays}

Uma exibição é um agrupamento virtual de telas que geralmente são posicionadas uma ao lado da outra. O visor é geralmente permanente em relação a uma instalação. Esse será o objeto com o qual os autores de conteúdo trabalharão e sempre se referirão como exibição lógica em vez de suas contrapartes físicas.

Depois de criar um local, é necessário criar uma nova exibição para o local.

Esta página mostra como criar e gerenciar exibições para o Screens.

**Pré-requisitos**:

* [Configuração e implantação do Screens](configuring-screens-introduction.md)
* [Criar e gerenciar projeto do Screens](creating-a-screens-project.md)
* [Criar e gerenciar canais](managing-channels.md)
* [Criar e Gerenciar Locais](managing-locations.md)

## Criação de uma nova exibição {#creating-a-new-display}

>[!NOTE]
>
>É necessário criar um local antes de criar uma exibição. Para ver como criar um local, consulte [Criar e Gerenciar Locais](managing-locations.md) para obter mais informações.

Para criar uma nova exibição em seu local, siga as etapas abaixo:

1. Navegue até o local apropriado, por exemplo `http://localhost:4502/screens.html/content/screens/TestProject`.
1. Selecione a pasta de local e toque/clique **Criar** ao lado do ícone de adição na barra de ações. Um assistente será aberto.
1. Selecionar **Exibir** do **Criar** e clique em **Próxima**.

1. Enter **Nome** e **Título** para o seu local de exibição.

1. No **Exibir** escolha os detalhes do Layout. Escolha o desejado **Resolução** (por exemplo, como **Full HD**). Além disso, você pode escolher o número de dispositivos horizontal e verticalmente.

1. Clique em **Criar**.

A exibição (*StoreDisplay*) é criada e adicionada ao local (*San Jose*).

![exibição](assets/display.gif)

Depois de ter a exibição na posição, a próxima etapa será criar uma configuração de dispositivo para essa exibição específica. Siga a seção abaixo para criar uma nova configuração de dispositivo.

>[!NOTE]
>
>**A próxima etapa**:
>
>Depois de criar uma exibição para sua localização, você precisa atribuir um canal à exibição para aproveitar o conteúdo.
>
>Consulte [Atribuir canais](channel-assignment.md) para saber como atribuir um canal à exibição.

## Criando uma nova configuração de dispositivo {#creating-a-new-device-config}

Uma configuração de dispositivo atua como um espaço reservado para um dispositivo de sinalização digital real que ainda não está instalado.

Siga as etapas abaixo para criar uma nova configuração de dispositivo:

1. Navegue até a exibição apropriada, por exemplo, `http://localhost:4502/screens.html/content/screens/TestProject/locations/newlocation`.
1. Selecione a pasta de exibição e toque/clique **Exibir painel** na barra de ações.
1. Toque/clique no **+ Adicionar configuração do dispositivo** na parte superior direita do **Dispositivos** painel.

1. Selecione o **Configuração do dispositivo** como o modelo necessário, e toque/clique em **Próxima**.

1. Insira as propriedades conforme necessário e toque/clique **Criar**.

A configuração do dispositivo é criada e adicionada à exibição atual (na demonstração a seguir, a nova configuração do dispositivo é *DeviceConfig*).

![deviceconfig](assets/deviceconfig.gif)

Depois que uma configuração de dispositivo é definida para sua exibição no local, a próxima etapa será atribuir um canal à exibição.

>[!NOTE]
>
>Depois que uma configuração de dispositivo é definida para sua exibição no local, a próxima etapa será atribuir um canal à exibição.
>
>Como mostrado na figura abaixo, se a configuração do dispositivo for exibida como não atribuída na variável **DISPOSITIVOS** painel, se nenhum canal estiver atribuído a essa configuração de dispositivo específica.
>
>Você deve ter conhecimento prévio sobre a criação e o gerenciamento de canais. Consulte [Criar e gerenciar canais](managing-channels.md) para obter mais detalhes.

![chlimage_1-9](assets/chlimage_1-9.png)

## Exibir painel {#display-dashboard}

O painel de exibição fornece painéis diferentes para gerenciar dispositivos de exibição e configurações de dispositivo para seu dispositivo.

![screen_shot_2018-08-23at42810pm](assets/screen_shot_2018-08-23at42810pm.png)

>[!NOTE]
>
>Você pode selecionar as listas de painéis e acionar ações em massa nos itens, em vez de percorrer cada item individualmente.
>
>Por exemplo, a imagem a seguir mostra como selecionar vários canais no painel de exibição.

![cqdoc9456](assets/cqdoc9456.gif)

### Exibir painel de informações {#display-information-panel}

A variável **EXIBIR INFORMAÇÕES** Panel fornece as propriedades de exibição.

Clique no botão **..**) no canto superior direito da janela **EXIBIR INFORMAÇÕES** painel para exibir as propriedades e pré-visualizar a exibição.


#### Visualizando propriedades {#viewing-properties}

Clique em **Propriedades** para exibir ou alterar as propriedades da exibição.

Além disso, é possível ajustar o valor do temporizador do evento para o canal interativo em **Tempo ocioso** propriedade em **Exibir** guia. O valor padrão está definido como *300 segundos*.

Uso **CRXDE Lite**, para acessar o **idleTimeout** propriedade, ou seja, `http://localhost:4502/crx/de/index.jsp#/content/screens/we-retail/locations/demo/flagship/single/jcr%3Acontent/channels` .


### Painel Canais atribuídos {#assigned-channels-panel}

A variável **CANAIS ATRIBUÍDOS** exibe os canais atribuídos a este dispositivo.


### Painel Dispositivos {#devices-panel}

A variável **DISPOSITIVOS** O painel fornece informações sobre as configurações do dispositivo.

Clique no botão **..**) no canto superior direito da janela **DISPOSITIVOS** painel para adicionar configurações de dispositivo e atualizar dispositivos.

Além disso, clique na configuração do dispositivo para exibir as propriedades, atribuir um dispositivo ou excluí-lo completamente.

![chlimage_1-13](assets/chlimage_1-13.png)

#### Próximas etapas {#the-next-steps}

Depois de concluir a criação de uma exibição para sua localização, você precisa atribuir um canal para sua exibição.

Consulte [Atribuir canais](channel-assignment.md) para obter mais detalhes.
