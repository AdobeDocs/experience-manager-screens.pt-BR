---
title: Rede corporativa fechada
description: Rede corporativa fechada
translation-type: tm+mt
source-git-commit: 0b1106b3cf7f83857f83e43f773a0d19556cfec5
workflow-type: tm+mt
source-wordcount: '583'
ht-degree: 0%

---


# Redes corporativas fechadas {#enclosed-corporate-networks}

A Enclosure Corporate Network SetUp é aplicável a empresas menores, maiores e corporativas. Pode ser teoricamente mais complexo, mas a Configuração lógica é sempre como mostrado abaixo em um exemplo simplificado.

## Requisitos para a criação de redes corporativas integradas {#requirements-enclosed-networks}

A configuração de rede corporativa incluída pode ser logicamente separada em dois blocos. A WAN (Wide Area Network, rede de longa distância) e a LAN (Local Area Network, rede local interna).

![](/help/using/assets/enclosed-network-1.png)

### Rede de área ampla {#wan-connection}

O desempenho da Conexão com a Internet, além da capacidade de alcance da rede já descrita, fornece largura de banda suficiente para operar AEM Screens de forma agradável e suave.
Em detalhes, &quot;suficiente&quot; depende da quantidade de telas AEM conectadas e do uso de outros consumidores dentro da rede, como Smartphones, Tablets, caixas, Computadores ou redes WIFI Convidadas.
Lembre-se de que todos os dispositivos têm acesso simultâneo à conexão com a Internet e que a largura de banda geralmente diminui linearmente, adicionando mais consumidores/computadores à rede.

### Rede local {#lan-connection}

O desempenho da LAN, além da capacidade de alcance da rede já descrita, fornece largura de banda suficiente para operar AEM Screens de forma agradável e suave. Atualmente, a rede LAN dentro das organizações corporativas geralmente corresponde a uma rede de 1000 MBit/s, de modo que deve haver largura de banda suficiente para conectar muitos dispositivos com bom desempenho ao sistema. Ao usar outro componente de rede ativo, é obrigatório que todos eles correspondam aos requisitos de largura de banda da rede. Por exemplo, os componentes de rede devem corresponder, no mínimo, ao padrão de 1000 Mbit/s e corresponder à largura de banda fornecida pela especificação Internet Access/Router.

### Outras especificações de redes corporativas {#other-networks}

Normalmente, as redes corporativas têm uma carga de dispositivos conectados, podem ser separadas em várias sub-redes e podem ter conexões redundantes ou multiplexadas com a Internet para fornecer desempenho suficiente para muitos milhares de acessos simultâneos.
O schema acima é simplificado e se encaixa na maioria dos casos no ambiente disponível para o cliente.
Caso uma solução WiFI esteja planejada para conectar a tela ao Internet Link, é recomendável usar no mínimo padrões WIFI modernos, como IEEE 802.11g. Este padrão suporta conexões de até 54 Mbit. Todos os padrões &quot;mais recentes&quot; como o 802.11h-n são de melhor qualidade. Se um WIFI Repeater for necessário, recomendamos enfaticamente as tecnologias de ponto de acesso WIFI em malha, como Google Nest Mesh WIFI ou similar.
Outras tecnologias de repetição WiFi acabam com uma perda maciça de largura de banda na rede geral.

## Download de mídia e ativos {#download}

Os AEM Screens oferecem uma grande vantagem aos usuários de placas digitais. Ele está baixando e salvando localmente todos os arquivos de mídia necessários, como Imagens e Vídeo. Devido a este conceito, o tráfego de rede principal está ocorrendo no caso de o novo conteúdo ser exibido em uma tela específica.
Para operação normal, por exemplo, tendo definido uma lista de reprodução que não é alterada com muita frequência durante o dia, isso oferta uma operação próxima da operação independente de rede, depois que todos os arquivos tiverem sido salvos no player. Para os casos de uso em que há mais interações com Sensores ou outros Acionadores e o conteúdo é muito dinâmico, uma conexão de rede rápida e confiável é essencial para uma reação imediata na tela, a fim de garantir a melhor experiência possível do cliente.

As tabelas a seguir ofertas uma boa visão geral do que os dados chave de conectividade da rede significam para o desempenho que pode ser esperado e os possíveis tempos de espera.

Todas as informações devem ser vistas como o consumo de cada dispositivo na rede que solicita e baixa uma fonte de Internet. Portanto, cada uma dessas solicitações somam e estendem o Tempo de Download.

![](/help/using/assets/enclosed-network-download.png)