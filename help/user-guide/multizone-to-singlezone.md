---
title: Caso de uso de transições de MultiZone para SingleZone
description: Siga esta página para saber mais sobre o caso de uso de MultiZone para SingleZone Transitions.
seo-description: Casos de uso de Transições de MultiZone para SingleZone.
contentOwner: Jyotika Syal
translation-type: tm+mt
source-git-commit: 0cae7c19759fe3418a13ab2d7cc68f1b220f397d

---


# Transição de MultiZone para SingleZone {#multizone-to-singlezone-use-case}


## Descrição do caso de uso {#use-case-description}

Esta seção descreve um exemplo de caso de uso que enfatiza como configurar um canal de layout multizona que alterna com um canal de layout de zona única. Cada canal tem ativos de imagem/vídeo em sequência.

### Condições prévias {#preconditions}

Antes de iniciar este caso de uso, certifique-se de saber como:

* **[Criar e gerenciar canais](managing-channels.md)**
* **[Criar e gerenciar locais](managing-locations.md)**
* **[Criar e gerenciar programações](managing-schedules.md)**
* **[Registro do dispositivo](device-registration.md)**

### Principais intervenientes {#primary-actors}

Autores de conteúdo

##  Configuração do projeto {#setting-up-the-project}

Siga as etapas abaixo para configurar um projeto:

1. Crie um projeto do AEM Screens chamado de **ChannelTransition**, como mostrado abaixo.



1. **Criação de um canal de tela dividida**

   1. Selecione a pasta **Canais** e clique em **Criar** na barra de ações para abrir o assistente para criar um canal.
   1. Selecione Canal **de tela dividida da barra** esquerda L no assistente e crie o canal chamado **MultiZoneLayout**.



   1. Select the **MultiZoneLayout** channel and click **Edit** from the action bar to open the editor. Arraste e solte os ativos em cada uma das zonas. O exemplo a seguir mostra um vídeo, uma imagem e um banner de texto no canal, como mostrado abaixo.


1. **Criação de um canal 2X2 com quatro imagens**

   1. Selecione a pasta **Canais** e clique em **Criar** na barra de ações para abrir o assistente para criar um canal.

   1. Selecione o modelo Canal **de tela dividida** 2X2 no assistente e crie o canal chamado **TwobyTwoChannel**.


   1. Selecione o canal e clique em **Editar** na barra de ações para abrir o editor e arraste e solte quatro imagens (quatro zonas diferentes) nesse canal, como mostrado abaixo.


1. **Criação de um canal de tela dividida 1X2 com duas imagens**

   1. Selecione a pasta **Canais** e clique em **Criar** na barra de ações para abrir o assistente para criar um canal.

   1. Selecione o modelo **1X2 de Canal** de Tela Dividida do assistente e crie o canal chamado **OneTwoChannel**.


   1. Selecione o canal e clique em **Editar** na barra de ações para abrir o editor e arraste e solte duas imagens (duas zonas diferentes) nesse canal, como mostrado abaixo.


1. **Criação de um canal com um vídeo em tela cheia**

   1. Selecione a pasta **Canais** e clique em **Criar** na barra de ações para abrir o assistente para criar um canal.

   1. Selecione o modelo de Canal **de** sequência no assistente e crie o canal chamado **FullScreensVideo**.


   1. Selecione o canal e clique em **Editar** na barra de ações para abrir o editor, arrastar e soltar o componente de vídeo nesse canal e adicionar o vídeo desejado, como mostrado abaixo.

