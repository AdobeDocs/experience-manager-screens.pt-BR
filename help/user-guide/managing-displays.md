---
title: Criação e gerenciamento de exibições
seo-title: Gerenciar exibições
description: Siga esta página para saber mais sobre a criação de uma nova exibição ou configuração de dispositivo. Além disso, saiba mais sobre o painel de exibição.
seo-description: Siga esta página para saber mais sobre a criação de uma nova exibição ou configuração de dispositivo. Além disso, saiba mais sobre o painel de exibição.
uuid: dfde0740-5c8b-4e6c-bc83-bf8fbb31a16a
contentOwner: Jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: f8e2e7a3-f3a1-4c35-b055-166752c3fb86
feature: Telas de criação
role: Administrador, Desenvolvedor
level: Intermediário
translation-type: tm+mt
source-git-commit: 89c70e64ce1409888800af7c7edfbf92ab4b2c68
workflow-type: tm+mt
source-wordcount: '778'
ht-degree: 59%

---


# Criação e gerenciamento de exibições {#creating-and-managing-displays}

Uma exibição é um agrupamento virtual de telas que, geralmente, são posicionadas próximas umas das outras. A exibição é, em geral, permanente com relação a uma instalação. Esse será o objeto no qual os autores de conteúdo irão trabalhar e é sempre referenciado como uma exibição lógica em vez de suas contrapartes físicas.

Depois de criar uma localização, você precisa criar uma nova exibição para ela.

Esta página mostra como criar e gerenciar as exibições do Screens.

**Pré-requisitos**:

* [Configuração e implantação do Screens](configuring-screens-introduction.md)
* [Criar e gerenciar o projeto do Screens](creating-a-screens-project.md)
* [Criar e gerenciar canais](managing-channels.md)
* [Criar e gerenciar locais](managing-locations.md)

## Criação de uma nova exibição {#creating-a-new-display}

>[!NOTE]
>
>É necessário criar uma localização para criar uma exibição. Para ver como criar um local, consulte [Criar e gerenciar locais](managing-locations.md) para obter mais informações.

Para criar uma nova exibição na localização, siga as seguintes etapas:

1. Navegue até o local apropriado, por exemplo `http://localhost:4502/screens.html/content/screens/TestProject`.
1. Selecione a pasta da localização e toque/clique em **Criar** ao lado do ícone de adição na barra de ações. Um assistente será aberto.
1. Selecione **Exibir** no assistente **Criar** e clique em **Próximo**.

1. Insira **Name** e **Title** para o local de exibição.

1. Na guia **Display**, escolha os detalhes do Layout. Escolha a **Resolução** desejada (por exemplo, como **Full HD**). Além disso, é possível escolher o número de dispositivos horizontal e verticalmente.

1. Clique em **Criar**.

A exibição (*StoreDisplay*) é criada e adicionada à localização (*SanJose*).

![display](assets/display.gif)

Quando tiver a exibição em posição, a próxima etapa será criar uma configuração de dispositivo para essa exibição específica. Siga a seção abaixo para criar uma nova configuração de dispositivo.

>[!NOTE]
>
>**A próxima etapa**:
>
>Depois de criar a exibição para a localização, você deve atribuir um canal a ela para aproveitar o conteúdo.
>
>Consulte a seção [Atribuir canais](channel-assignment.md) para saber como atribuir um canal à exibição.

## Criação de uma nova configuração de dispositivo {#creating-a-new-device-config}

Uma configuração de dispositivo atua como um espaço reservado para um dispositivo de assinatura digital real que ainda não foi instalado.

Siga as etapas abaixo para criar uma nova configuração de dispositivo:

1. Navegue até a exibição apropriada, por exemplo, `http://localhost:4502/screens.html/content/screens/TestProject/locations/newlocation`.
1. Selecione a pasta de exibição e toque/clique em **Exibir painel** na barra de ações.
1. Toque/clique em **+ Adicionar configuração de dispositivo** na parte superior direita do painel **Dispositivos**.

1. Selecione o **Device Config** como o modelo necessário e toque/clique em **Next**.

1. Insira as propriedades conforme necessário e toque/clique em **Criar**.

A configuração de dispositivo é criada e adicionada à exibição atual (na demonstração a seguir, a nova configuração de dispositivo é *DeviceConfig*).

![deviceconfig](assets/deviceconfig.gif)

Quando uma configuração de dispositivo for definida para a exibição na localização, a próxima etapa será atribuir um canal à exibição.

>[!NOTE]
>
>Quando uma configuração de dispositivo for definida para a exibição na localização, a próxima etapa será atribuir um canal à exibição.
>
>Como mostrado na figura abaixo, se a configuração do dispositivo for exibida como não atribuída no painel **DEVICES**, se nenhum canal for atribuído a essa configuração de dispositivo específica.
>
>Você deve compreender como criar e gerenciar canais. Consulte [Criar e gerenciar canais](managing-channels.md) para obter mais detalhes.

![chlimage_1-9](assets/chlimage_1-9.png)

## Painel Exibição {#display-dashboard}

O painel Exibição oferece diferentes painéis para gerenciar os dispositivos de exibição e as configurações do seu dispositivo.

![screen_shot_2018-08-23at42810pm](assets/screen_shot_2018-08-23at42810pm.png)

>[!NOTE]
>
>É possível selecionar as listas de painel e executar ações em massa nos itens, em vez de processar cada item individualmente.
>
>Por exemplo, a imagem a seguir mostra como você pode selecionar vários canais no painel de exibição.

![cqdoc9456](assets/cqdoc9456.gif)

### Painel de Informações sobre a exibição {#display-information-panel}

O painel **INFORMAÇÕES SOBRE A EXIBIÇÃO** fornece as propriedades de exibição.

Clique em (**...**) no canto superior direito do painel **INFORMAÇÕES SOBRE A EXIBIÇÃO** para visualizar as propriedades e a exibição.


#### Exibição de propriedades {#viewing-properties}

Clique em **Propriedades** para ver ou alterar as propriedades da sua exibição.

Além disso, você pode ajustar o valor do temporizador de eventos para o canal interativo na propriedade **Tempo limite ocioso** na guia **Display**. O valor padrão é definido para *300 segundos*.

Use **CRXDE Lite** para acessar a propriedade **idleTimeout**, ou seja, `http://localhost:4502/crx/de/index.jsp#/content/screens/we-retail/locations/demo/flagship/single/jcr%3Acontent/channels` .


### Painel Canais atribuídos {#assigned-channels-panel}

O painel **CANAIS ATRIBUÍDOS** mostra os canais atribuídos a este dispositivo.


### Painel Dispositivos {#devices-panel}

O painel **DISPOSITIVOS** fornece informações sobre configurações de dispositivos.

Clique em (**...**) no canto superior direito do painel **DISPOSITIVOS** para adicionar configurações de dispositivo e atualizar dispositivos.

Além disso, clique na configuração do dispositivo para exibir as propriedades, atribuir um dispositivo ou excluí-la completamente.

![chlimage_1-13](assets/chlimage_1-13.png)

#### Próximas etapas {#the-next-steps}

Depois de concluir a criação de uma exibição para a localização, você deve atribuir um canal à exibição.

Consulte [Atribuir canais](channel-assignment.md) para obter mais detalhes.
