---
title: Gerenciando dispositivos
seo-title: Managing Devices
description: Esta página descreve a atribuição de dispositivos.
seo-description: Follow this page to learn about device assignment. The Devices console allows you to access the device manager to assign your device to a display.
uuid: 889cc11c-60f7-4966-82b5-9ebdd082a3c5
contentOwner: Jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: 8dc08e29-a377-4e84-84ee-442470c19019
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 10749ff2-9128-44e7-9f10-c8e783a6f695
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '241'
ht-degree: 1%

---

# Gerenciando dispositivos {#managing-devices}

Esta página descreve a atribuição de dispositivos.

O console Dispositivos permite acessar o gerenciador de dispositivos para atribuir seu dispositivo a uma exibição.

>[!CAUTION]
>
>Antes de atribuir seu dispositivo, é necessário registrá-lo. Para obter mais informações, consulte [Registro do dispositivo](device-registration.md).

## Atribuição de dispositivo {#device-assignment}

Siga as etapas abaixo para atribuir um dispositivo a uma exibição:

1. Navegue até a pasta Dispositivos do projeto, por exemplo

   `http://localhost:4502/screens.html/content/screens/TestProject`

   ![chlimage_1-32](assets/chlimage_1-32.png)

1. Selecione o **Dispositivos** e toque/clique **Gerenciador de dispositivos** na barra de ações. Os dispositivos atribuídos e não atribuídos são exibidos.

   ![chlimage_1-33](assets/chlimage_1-33.png)

1. Selecione um dispositivo não atribuído na lista e toque/clique no **Atribuir dispositivo** na barra de ações.

   ![chlimage_1-34](assets/chlimage_1-34.png)

1. Selecione na lista o vídeo ao qual deseja atribuir o dispositivo e toque/clique no **Atribuir**.

   ![chlimage_1-35](assets/chlimage_1-35.png)

1. Toque/clique no **Concluir** para concluir o processo de atribuição.


   O painel de exibição exibe o dispositivo atribuído na variável **DISPOSITIVOS** painel.

   ![chlimage_1-37](assets/chlimage_1-37.png)

   Clique no botão **..**) no canto superior direito da **DISPOSITIVOS** para adicionar a configuração do dispositivo ou atualizar os dispositivos.

   ![chlimage_1-38](assets/chlimage_1-38.png)

>[!NOTE]
>
>Toda vez que o primeiro dispositivo é adicionado a um novo projeto do Screens, um grupo de usuários é criado.
>Por exemplo, se o nome do nó do projeto for *we-retail*, o nome do grupo de usuários será *screens-we-retail-devices*.
>Este grupo será adicionado como um membro de **Colaboradores** conforme mostrado na figura abaixo:

![chlimage_1-39](assets/chlimage_1-39.png)

### Próximas etapas {#the-next-steps}

Depois de conhecer a atribuição de um canal a uma exibição, consulte os seguintes recursos:

* [Monitorar e solucionar problemas](monitoring-screens.md)
