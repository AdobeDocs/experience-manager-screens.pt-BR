---
title: Acesso direto à Internet
description: Acesso direto à Internet
translation-type: tm+mt
source-git-commit: 70dddffd46ebf1bd83b25515be548bc442e45fea
workflow-type: tm+mt
source-wordcount: '712'
ht-degree: 0%

---


# Acesso direto à Internet {#direct-internet-access}

O Direct Internet Access SetUp contém um ponto de acesso de entrada para acesso à Internet a fim de alcançar os AEM cloud services aos quais o AEM Screens precisa se conectar.

As Portas padrão para comunicação com AEM Screens são:
* `http (TCP Port 80)`
Ou,
* `ssl-secured https (TCP Port 443)`

As portas podem variar devido à configuração de sua configuração de AEM dedicada configurada. Dentro desta configuração, todos os dispositivos são conectados diretamente ao seu roteador de Internet, como mostra a figura abaixo.

![](/help/assets/direct-access-2.png)

A configuração também inclui um ISP (Internet Access by any Internet Provedor de serviço) e o Internet Line. A maioria dos ISPs fornece um roteador de Internet que cobre o modem da Internet, switch de rede, ponto de acesso WIFI, firewall e outras funcionalidades de rede (dependendo do fabricante e do modelo).

## Conexão do AEM Screens Player ao acesso direto à Internet {#connecting-aem-screens-players}

Siga as etapas abaixo para conectar players de tela AEM nesta configuração:

1. Verifique se cada um dos players de tela do AEM está conectado à rede de roteadores.
1. Teste a conexão com a Internet chamando um URL no navegador do sistema.

   >[!NOTE]
   >Caso receba uma mensagem de erro, verifique as configurações de rede. Basicamente, existem duas opções para uma conexão de rede adequada:
   >* DHCP
   >* Configuração de IP manual


1. Verifique se a configuração do adaptador de rede corresponde à configuração do roteador e se a quantidade máxima de endereços IP disponíveis na rede não foi atingida.

1. Verifique se o roteador está conectado corretamente à ISP Wide Area Network (Internet Link). Normalmente, isso também pode ser identificado usando um LED de sinal nos roteadores padrão.
1. Se a chamada de URL for bem-sucedida, você poderá continuar instalando os AEM Screens e registrá-los de acordo. AEM Screens Start.

   >[!NOTE]
   >**Dica de solução de problemas**
   >Se o AEM Screens não se conectar corretamente e não mostrar o conteúdo esperado:
   >
   >1. Verifique o Firewall do Internet Router se há restrições relacionadas a `TCP/IP Port 80/443`.
   >1. Verifique se todas as portas necessárias são permitidas.


## Requisitos para a configuração da rede de acesso direto {#requirements-direct}

A configuração da rede de acesso direto pode ser logicamente separada em dois blocos:

* Rede de área ampla

* Rede local

### Rede de área ampla {#wan-connection}

O desempenho da conexão com a Internet, além da acessibilidade da rede, é fornecer largura de banda suficiente para operar AEM Screens de forma agradável e suave.

*O suficiente* depende da quantidade de telas AEM conectadas e do uso de outros consumidores dentro da rede, como Smartphones, Tablets, caixas, computadores ou redes WIFI Convidadas.

>[!NOTE]
>Todos os dispositivos têm acesso simultâneo à conexão com a Internet e a largura de banda geralmente diminui linearmente quando você adiciona mais consumidores/computadores à rede.

### Rede local {#lan-connection}

O desempenho da LAN (Local Area Network, Rede local), além da acessibilidade da rede, fornece largura de banda suficiente para operar AEM Screens de forma agradável e suave.

A rede LAN normalmente corresponde a uma rede de 100 MBit/s, de modo que há largura de banda suficiente para conectar muitos dispositivos com bom desempenho ao sistema.
Caso uma solução WIFI esteja planejada para conectar AEM Screens ao Internet Link, é recomendável usar no mínimo padrões WIFI modernos, como IEEE 802.11g. Este padrão suporta conexões de até 54 Mbps. Todos os padrões *mais recentes* como o 802.11h-n são de melhor qualidade.

>[!NOTE]
>Se um WIFI Repeater for necessário, recomendamos enfaticamente as tecnologias de ponto de acesso WIFI em malha, como Google Nest Mesh WIFI ou similar. Outras tecnologias de repetição WiFi acabam com uma perda maciça de largura de banda na rede geral.

## Download de mídia e ativos {#download}

Os AEM Screens oferecem uma grande vantagem aos usuários de placas digitais. Ele baixa e salva localmente todos os arquivos de mídia necessários, como imagens e vídeos. Devido a esse conceito, o tráfego de rede principal ocorre quando há novo conteúdo a ser exibido em uma tela específica.
Para operações normais, por exemplo, tendo definido uma lista de reprodução que não é alterada com muita frequência durante o dia, isso oferta uma operação próxima da operação independente da rede, depois que todos os arquivos tiverem sido salvos no player.
Para os casos de uso em que há mais interações com sensores ou outros acionadores e o conteúdo é muito dinâmico, uma conexão de rede rápida e confiável é essencial para uma reação imediata na tela, a fim de garantir a melhor experiência possível do cliente.

A tabela a seguir fornece uma visão geral sobre os dados principais de conectividade de rede.

>[!NOTE]
>As informações permitem que você visualização o consumo de cada dispositivo na rede solicitando e baixando uma fonte da Internet. Cada uma dessas solicitações adiciona e estende o Tempo de download.

![](/help/assets/download-times-direct.png)

