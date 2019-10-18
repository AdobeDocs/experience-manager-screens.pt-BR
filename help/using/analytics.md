---
title: Analytics com AEM Screens
seo-title: Analytics com AEM Screens
description: A página descreve o Analytics com o AEM Screens
seo-description: A página descreve a análise com o AEM Screens
translation-type: tm+mt
source-git-commit: f01b69b860a3862e2b46f11b2d9b95dede742d9c

---


# Analytics com AEM Screens {#analytics-screens}

>[!NOTE]
>
>Participantes típicos desta atividade são os Estratégistas de marketing/negócios.

O AEM Screens oferece a capacidade de capturar localmente todos os eventos rastreáveis que cada dispositivo de player executa. Esses dados serão armazenados localmente até que possam ser carregados na nuvem para processamento. Além de todos os dados do evento, uma deviceID e um carimbo de data e hora também são adicionados. Isso garante que os dados de um player possam ser diferenciados de outro player e os dados executados em diferentes horários do dia possam ser avaliados separadamente, se desejado.

Há duas razões fundamentais para podermos querer capturar esses dados.

O primeiro envolve loops de **feedback e aprendizado** de máquina enquanto o segundo envolve a **criação de gráficos, painéis e relatórios** destinados ao consumo humano.

No caso de uso do ciclo de feedback, não estamos preocupados com relatórios visuais ou painéis, mas, em vez disso, queremos definir regras que o AEM possa executar para modificação de conteúdo. Ao consumir e processar todos os dados de evento do player do Screens de um determinado período, podemos definir uma regra que avalia a eficácia de image1 versus image2. Ao combinar dados de vendas com dados de reprodução, o AEM pode determinar que image1 tem um impacto muito maior nas vendas e instrui automaticamente todos os players a usar image1.

O segundo caso de uso com o Analytics é processar eventos de reprodução e dados de uso para consumo humano por meio de relatórios e painéis.
Podemos usar esses dados para criar um mapa de calor de uma experiência interativa para determinar o mapa de jornada preferido através de nosso aplicativo. Também podemos escolher criar um painel que fornece uma interpretação gráfica de quantas vezes os consumidores interagem com nosso aplicativo.

