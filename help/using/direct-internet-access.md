---
title: Acesso direto à Internet
description: Acesso direto à Internet
translation-type: tm+mt
source-git-commit: 6a0460fd6c62fd6408d3c7665b626818929351d9
workflow-type: tm+mt
source-wordcount: '584'
ht-degree: 0%

---


# Acesso direto à Internet {#direct-internet-access}

O Direct Internet Access SetUp contém um ponto de acesso de entrada para acesso à Internet a fim de alcançar os AEM cloud services aos quais o AEM Screens precisa se conectar.

As Portas padrão para comunicação com AEM Screens são:
* `http (TCP Port 80)`
Ou,
* `ssl-secured https (TCP Port 443)`

As portas podem variar devido à configuração de sua configuração de AEM dedicada. Dentro desta configuração, todos os dispositivos são conectados diretamente ao seu roteador de Internet, como mostra a figura abaixo.

![](/help/assets/direct-access-2.png)

A configuração também inclui um ISP (Internet Access by any Internet Provedor de serviço) e o Internet Line. A maioria dos ISPs fornece um roteador de Internet que cobre o modem da Internet, switch de rede, ponto de acesso WIFI, firewall e outras funcionalidades de rede (dependendo do fabricante e do modelo).

>[!NOTE]
>**Dica de solução de problemas **>Se o AEM Screens não se conectar corretamente e mostrar o conteúdo esperado:
>
>1. Verifique o Firewall do Internet Router se há restrições relacionadas a `TCP/IP Port 80/443`.
>1. Verifique se todas as portas necessárias são permitidas e tente novamente.


## Requisitos para a configuração da rede de acesso direto {#requirements-direct}

A configuração da rede de acesso direto pode ser logicamente separada em dois blocos. O Bloco WAN/Outer World/Internet Connection e a Rede Local/LAN interna.

### Conexão WAN / Internet {#wan-connection}

O desempenho da Conexão com a Internet, além da capacidade de alcance da rede já descrita, fornece largura de banda suficiente para operar AEM Screens de forma agradável e suave. Em detalhes, &quot;suficiente&quot; depende da quantidade de telas AEM conectadas e do uso de outros consumidores dentro da rede, como Smartphones, Tablets, caixas, Computadores ou redes WIFI Convidadas.
Lembre-se de que todos os dispositivos têm acesso simultâneo à conexão com a Internet e que a largura de banda geralmente diminui linearmente, adicionando mais consumidores/computadores à rede.

### Conexão LAN {#lan-connection}

O desempenho da LAN, além da capacidade de alcance da rede já descrita, fornece largura de banda suficiente para operar AEM Screens de forma agradável e suave. Atualmente, a rede LAN normalmente corresponde a uma rede de 100 MBit/s, de modo que deve haver largura de banda suficiente para conectar muitos dispositivos com bom desempenho ao sistema.
Caso uma solução WIFI esteja planejada para conectar a tela ao Internet Link, é recomendável usar no mínimo padrões WIFI modernos, como IEEE 802.11g. Este padrão suporta conexões de até 54 Mbit. Todos os padrões *mais recentes* como o 802.11h-n são de melhor qualidade. Se um WIFI Repeater for necessário, recomendamos enfaticamente as tecnologias de ponto de acesso WIFI em malha, como Google Nest Mesh WIFI ou similar.
Outras tecnologias de repetição WiFi acabam com uma perda maciça de largura de banda na rede geral.

## Download de mídia e ativos {#download}

Os AEM Screens oferecem uma grande vantagem aos usuários de placas digitais. Ele está baixando e salvando localmente todos os arquivos de mídia necessários, como imagens e vídeos. Devido a este conceito, o tráfego de rede principal está ocorrendo no caso de o novo conteúdo ser exibido em uma tela específica.
Para operações normais, por exemplo, tendo definido uma lista de reprodução que não é alterada com muita frequência durante o dia, isso oferta uma operação próxima da operação independente da rede, depois que todos os arquivos tiverem sido salvos no player.
Para os casos de uso em que há mais interações com sensores ou outros acionadores e o conteúdo é muito dinâmico, uma conexão de rede rápida e confiável é essencial para uma reação imediata na tela, a fim de garantir a melhor experiência possível do cliente.

A tabela a seguir fornece uma visão geral sobre os dados principais de conectividade de rede:

![](/help/assets/download-times-direct.png)

>[!NOTE]
>As informações permitem que você visualização o consumo de cada dispositivo na rede solicitando e baixando uma fonte da Internet. Cada uma dessas solicitações agregam e estendem o tempo de download.