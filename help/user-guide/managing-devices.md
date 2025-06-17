---
title: Gerenciar dispositivos
description: Saiba mais sobre a atribuição e o gerenciamento de dispositivos no AEM Screens.
contentOwner: Jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 10749ff2-9128-44e7-9f10-c8e783a6f695
source-git-commit: dcaaa1c7ab0a55cecce70f593ed4fded8468130b
workflow-type: tm+mt
source-wordcount: '238'
ht-degree: 1%

---

# Gerenciar dispositivos {#managing-devices}

Esta página descreve a atribuição do dispositivo.

O console Dispositivos permite acessar o gerenciador de dispositivos para atribuir seu dispositivo a uma exibição.

>[!CAUTION]
>
>Antes de atribuir seu dispositivo, registre-o. Consulte [Registro de Dispositivo](device-registration.md).

## Atribuição de dispositivo {#device-assignment}

Siga as etapas abaixo para atribuir um dispositivo a uma exibição:

1. Navegue até a pasta Dispositivos do projeto, por exemplo

   `http://localhost:4502/screens.html/content/screens/TestProject`

   ![chlimage_1-32](assets/chlimage_1-32.png)

1. Clique na pasta **Dispositivos** e clique em **Gerenciador de Dispositivos** na barra de ações. Os dispositivos atribuídos e não atribuídos são exibidos.

   ![chlimage_1-33](assets/chlimage_1-33.png)

1. Clique em um dispositivo não atribuído na lista e, na barra de ações, clique em **Atribuir dispositivo**.

   ![chlimage_1-34](assets/chlimage_1-34.png)

1. Clique na exibição à qual você deseja atribuir o dispositivo na lista e clique em **Atribuir**.

   ![chlimage_1-35](assets/chlimage_1-35.png)

1. Clique em **Concluir** para concluir o processo de atribuição.


   O painel de exibição exibe o dispositivo atribuído no painel **DISPOSITIVOS**.

   ![chlimage_1-37](assets/chlimage_1-37.png)

   Clique em (**...**) no canto superior direito do painel **DISPOSITIVOS** para adicionar a configuração do dispositivo ou atualizar os dispositivos.

   ![chlimage_1-38](assets/chlimage_1-38.png)

>[!NOTE]
>
>Toda vez que o primeiro dispositivo é adicionado a um novo projeto do Screens, um grupo de usuários é criado.
>&#x200B;>Por exemplo, se o nome do nó do projeto for *we-retail*, o nome do grupo de usuários será *screens-we-retail-devices*.
>&#x200B;>Este grupo é adicionado como membro do grupo **Contribuidores**, conforme mostrado na figura abaixo:

![chlimage_1-39](assets/chlimage_1-39.png)

### Próximas etapas {#the-next-steps}

Depois de conhecer a atribuição de canal a uma exibição, consulte t[Monitorar e solucionar problemas](monitoring-screens.md).
