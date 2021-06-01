---
title: Analytics com AEM Screens
seo-title: Analytics com AEM Screens
description: A página descreve o Analytics com o AEM Screens
seo-description: A página descreve a análise com o AEM Screens
source-git-commit: 4611dd40153ccd09d3a0796093157cd09a8e5b80
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 0%

---


# Analytics com AEM Screens {#analytics-screens}

>[!NOTE]
>
>Os participantes típicos dessa atividade são um Estrategista de marketing/negócios.

O AEM Screens oferece a capacidade de capturar localmente cada evento rastreável que cada dispositivo de reprodução executa. Esses dados serão armazenados localmente até que possam ser carregados na nuvem para processamento. Além de todos os dados do evento, uma deviceID e um carimbo de data e hora também são adicionados. Isso garante que os dados de um reprodutor possam ser diferenciados de outro reprodutor e os dados executados em momentos diferentes do dia possam ser avaliados separadamente, se desejado.

Há duas razões fundamentais para capturar esses dados.

O primeiro envolve **ciclos de feedback e aprendizado de máquina** enquanto o segundo envolve a **criação de gráficos, painéis e relatórios** que são destinados ao consumo humano.

No caso de uso do loop de comentários, não estamos preocupados com relatórios visuais ou painéis, mas queremos definir regras que AEM possam ser executadas para modificação de conteúdo. Ao consumir e processar todos os dados de evento do player do Screens de um determinado período, podemos definir uma regra que avalie a eficácia de image1 versus image2. Ao combinar dados de vendas com dados de reprodução, AEM pode determinar que image1 tem um impacto muito maior nas vendas e instrui automaticamente todos os players a usar image1.

O segundo caso de uso que usa a análise é processar eventos de reprodução e dados de uso para consumo humano por meio de relatórios e painéis.
Podemos usar esses dados para criar um mapa de calor de uma experiência interativa para determinar o mapa de jornadas preferencial por meio de nosso aplicativo. Também podemos escolher criar um painel que forneça uma interpretação gráfica de quantas vezes os consumidores interagem com nosso aplicativo.

