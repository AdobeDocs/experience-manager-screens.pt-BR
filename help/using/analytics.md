---
title: Analytics com AEM Screens
description: Saiba mais sobre o Adobe Analytics com o Adobe Experience Manager Screens.
exl-id: cfb47e94-9f65-43f3-b197-07222f3f6424
TQID: https://experienceleague.adobe.com/i7B7E5Kyno2U-ZTxEOPfhrr9W7fqYTWTV5vvcteRicY
product_v2:
  - id: a27b4747-2f72-4fb7-9936-be5d11dd2c4a
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
topic_v2:
  - id: eb30f47f-d87a-400f-8f78-63ce7979ff56
source-git-commit: d4664dd5678eaccabe656398c437dca264d4675e
workflow-type: tm+mt
source-wordcount: 289
ht-degree: 0%

---

# Analytics com AEM Screens {#analytics-screens}

>[!IMPORTANT]
>Esse conteúdo é válido para o AEM no local/AMS (AEM 6.5LTS e AEM 6.5). Para ver o conteúdo do AEM as a Cloud Service Screens, consulte o [guia do AEM as a Cloud Service](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/screens-as-cloud-service/overview/introduction).

>[!NOTE]
>
>As partes interessadas típicas dessa atividade são os Estrategistas de marketing/negócios.

O AEM Screens pode capturar localmente todos os eventos rastreáveis que cada dispositivo de reprodução executa. Esses dados são armazenados localmente até que possam ser carregados na nuvem para processamento. Além de todos os dados do evento, um deviceID e um carimbo de data e hora também são adicionados. Essa funcionalidade garante que os dados de um player sejam distinguíveis de outro. Além disso, os dados executados em momentos diferentes do dia podem ser avaliados separadamente, se desejado.

Há dois motivos fundamentais pelos quais você pode desejar capturar esses dados.

O primeiro envolve **loops de comentários e aprendizado de máquina**, enquanto o segundo envolve **criação de gráficos, painéis e relatórios** destinados ao consumo humano.

No caso de uso de loop de comentários, não é necessário se preocupar com relatórios visuais ou painéis, mas, em vez disso, você deseja definir regras nas quais o AEM pode ser executado para modificação de conteúdo. Ao consumir e processar todos os dados do evento do Screens player de um determinado período, você pode definir uma regra que avalia a eficácia da image1 versus image2. Ao combinar dados de vendas com dados de reprodução, a AEM pode determinar que image1 tem um maior impacto nas vendas e instrui automaticamente todos os players a usar image1.

O segundo caso de uso que usa o Analytics é para processar eventos de reprodução e dados de uso para consumo humano por meio de relatórios e painéis.
Você pode usar esses dados para criar um mapa de calor de uma experiência interativa para determinar o mapa de jornadas preferido por meio do aplicativo. Você também pode optar por criar um painel que forneça uma interpretação gráfica de quantas vezes os consumidores interagem com o aplicativo.
