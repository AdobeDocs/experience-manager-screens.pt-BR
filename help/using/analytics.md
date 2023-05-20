---
title: Analytics com AEM Screens
seo-title: Analytics with AEM Screens
description: A página descreve o Analytics com AEM Screens
seo-description: The page describes the analytics with AEM Screens
exl-id: cfb47e94-9f65-43f3-b197-07222f3f6424
source-git-commit: 707833ddd8ab2573abcac4e9a77ec88778624435
workflow-type: tm+mt
source-wordcount: '285'
ht-degree: 0%

---

# Analytics com AEM Screens {#analytics-screens}

>[!NOTE]
>
>As partes interessadas típicas dessa atividade são os Estrategistas de marketing/negócios.

O AEM Screens oferece a capacidade de capturar localmente todos os eventos rastreáveis que cada dispositivo de reprodução executa. Esses dados serão armazenados localmente até que possam ser carregados na nuvem para processamento. Além de todos os dados do evento, um deviceID e um carimbo de data e hora também são adicionados. Isso garante que os dados de um player possam ser diferenciados de outro player e os dados executados em momentos diferentes do dia possam ser avaliados separadamente, se desejado.

Há dois motivos fundamentais pelos quais podemos querer capturar esses dados.

O primeiro envolve **loops de feedback e aprendizado de máquina** enquanto o segundo envolve a **criação de gráficos, painéis e relatórios** destinados ao consumo humano.

No caso de uso de loop de comentários, não estamos preocupados com relatórios visuais ou painéis, mas, em vez disso, queremos definir regras nas quais o AEM pode ser executado para modificação de conteúdo. Consumindo e processando todos os dados do evento do reprodutor do Screens de um determinado período, podemos definir uma regra que avalie a eficácia da image1 versus image2. Ao combinar dados de vendas com dados de reprodução, o AEM pode determinar que a image1 tem um impacto muito maior nas vendas e instrui automaticamente todos os players a usar a image1.

O segundo caso de uso que usa o Analytics é para processar eventos de reprodução e dados de uso para consumo humano por meio de relatórios e painéis.
Podemos usar esses dados para criar um mapa de calor de uma experiência interativa para determinar o mapa de jornadas preferido por meio de nosso aplicativo. Também podemos escolher a criação de um painel que forneça uma interpretação gráfica de quantas vezes os consumidores interagem com nosso aplicativo.
