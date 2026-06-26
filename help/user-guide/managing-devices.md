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
TQID: https://experienceleague.adobe.com/BtVUYTZ9GisSxK6-M-QsYRGdykFB51IchqI7CX-vsa8
product_v2: id: a27b4747-2f72-4fb7-9936-be5d11dd2c4aid: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2: id: a5fd0e22-1a77-4f49-a6af-7a57fff19aed
subfeature_v2: id: f5973e90-a5a3-4b84-8602-ee120d4ce9b1
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2: id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2: id: c1579802-ddd4-4214-8a91-97b2066abe11
source-git-commit: 6ffdfa02d948d50b544f6fa5164dc6dca8bff638
workflow-type: tm+mt
source-wordcount: 288
ht-degree: 1%

---

# Gerenciar dispositivos {#managing-devices}

>[!IMPORTANT]
>Esse conteúdo é válido para o AEM no local/AMS (AEM 6.5LTS e AEM 6.5). Para ver o conteúdo do AEM as a Cloud Service Screens, consulte o [guia do AEM as a Cloud Service](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/screens-as-cloud-service/overview/introduction).

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
>Toda vez que o primeiro dispositivo é adicionado a um novo projeto do Screens, um grupo de usuários é criado.Por exemplo, se o nome do nó do projeto for *we-retail*, o nome do grupo de usuários será *screens-we-retail-devices*.Este grupo é adicionado como membro do grupo **Contribuidores**, conforme mostrado na figura abaixo:

![chlimage_1-39](assets/chlimage_1-39.png)

### Próximas etapas {#the-next-steps}

Depois de conhecer a atribuição de canal a uma exibição, consulte t[Monitorar e solucionar problemas](monitoring-screens.md).

