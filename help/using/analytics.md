---
title: Analytics com AEM Screens
description: Saiba mais sobre o Adobe Analytics com o Adobe Experience Manager Screens.
exl-id: cfb47e94-9f65-43f3-b197-07222f3f6424
source-git-commit: 8dde26d36847fb496aed6d4bf9732233116b5ea6
workflow-type: tm+mt
source-wordcount: '288'
ht-degree: 0%

---

# Analytics com AEM Screens {#analytics-screens}

>[!NOTE]
>
>As partes interessadas típicas dessa atividade são os Estrategistas de marketing/negócios.

O AEM Screens pode capturar localmente todos os eventos rastreáveis que cada dispositivo de reprodução executa. Esses dados são armazenados localmente até que possam ser carregados na nuvem para processamento. Além de todos os dados do evento, um deviceID e um carimbo de data e hora também são adicionados. Essa funcionalidade garante que os dados de um player sejam distinguíveis de outro. Além disso, os dados executados em momentos diferentes do dia podem ser avaliados separadamente, se desejado.

Há dois motivos fundamentais pelos quais você pode desejar capturar esses dados.

O primeiro envolve **loops de comentários e aprendizado de máquina**, enquanto o segundo envolve **criação de gráficos, painéis e relatórios** destinados ao consumo humano.

No caso de uso de loop de comentários, não é necessário se preocupar com relatórios visuais ou painéis, mas, em vez disso, você deseja definir regras nas quais o AEM pode ser executado para modificação de conteúdo. Ao consumir e processar todos os dados do evento do Screens player de um determinado período, você pode definir uma regra que avalia a eficácia da image1 versus image2. Ao combinar dados de vendas com dados de reprodução, o AEM pode determinar que a image1 tem um maior impacto nas vendas e instrui automaticamente todos os players a usar a image1.

O segundo caso de uso que usa o Analytics é para processar eventos de reprodução e dados de uso para consumo humano por meio de relatórios e painéis.
Você pode usar esses dados para criar um mapa de calor de uma experiência interativa para determinar o mapa de jornadas preferido por meio do aplicativo. Você também pode optar por criar um painel que forneça uma interpretação gráfica de quantas vezes os consumidores interagem com o aplicativo.
