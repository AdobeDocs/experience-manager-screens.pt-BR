---
title: Analytics com AEM Screens
seo-title: Analytics com AEM Screens
description: A página descreve o Analytics com o AEM Screens
seo-description: A página descreve as análises com o AEM Screens
translation-type: tm+mt
source-git-commit: 54c5a2f2f3f755e4da4028d54042f4bd8f2df369
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 0%

---


# Analytics com AEM Screens {#analytics-screens}

>[!NOTE]
>
>Participantes típicos desta atividade são um Estratégista de marketing/negócios.

A AEM Screens oferta a capacidade de capturar localmente cada evento rastreável que cada dispositivo player executa. Esses dados serão armazenados localmente até que possam ser carregados na nuvem para processamento. Além de todos os dados do evento, uma deviceID e um carimbo de data e hora também são adicionados. Isso garante que os dados de um player possam ser diferenciados de outro player e os dados executados em diferentes horários do dia possam ser avaliados separadamente, se desejado.

Há duas razões fundamentais para podermos querer capturar esses dados.

O primeiro envolve **repetições de feedback e aprendizado de máquina** enquanto o segundo envolve a **criação de gráficos, painéis e relatórios** destinados ao consumo humano.

No caso de uso do ciclo de feedback, não estamos preocupados com relatórios visuais ou painéis, mas, em vez disso, queremos definir regras que AEM possam ser executadas para a modificação do conteúdo. Ao consumir e processar todos os dados de evento do player do Screens de um determinado período, podemos definir uma regra que avalia a eficácia de image1 versus image2. Ao combinar dados de vendas com dados de reprodução, AEM pode determinar que image1 tenha um impacto muito maior nas vendas e instrui automaticamente todos os players a usar image1.

O segundo caso de uso com o Analytics é o processamento de eventos de reprodução e dados de uso para consumo humano por meio de relatórios e painéis.
Podemos usar esses dados para criar um mapa de calor de uma experiência interativa para determinar o mapa de jornada preferido através de nosso aplicativo. Também podemos escolher criar um painel que forneça uma interpretação gráfica de quantas vezes os consumidores interagem com nosso aplicativo.

