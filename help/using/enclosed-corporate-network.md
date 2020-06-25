---
title: Rede corporativa fechada
description: Rede corporativa fechada
translation-type: tm+mt
source-git-commit: ed683a86b7e8c6ec06309577bd0a8690a9cc4684
workflow-type: tm+mt
source-wordcount: '751'
ht-degree: 0%

---


# Redes corporativas fechadas (com fio/sem fio) {#enclosed-corporate-networks}

A Enclosure Corporate Network SetUp é aplicável a empresas menores, maiores e corporativas. Pode ser teoricamente mais complexo, mas a Configuração lógica é mostrada na figura abaixo.

![](/help/using/assets/enclosed-network-1.png)


## Conexão do AEM Screens Player ao acesso direto à Internet {#connecting-aem-screens-players}

Siga as etapas abaixo para garantir a conexão correta dos players de tela do AEM nesta configuração:

1. Verifique se cada um dos players de tela do AEM está conectado à rede de roteadores.
1. Teste a conexão com a Internet chamando um URL no navegador do sistema.

   >[!NOTE]
   >Caso receba um erro, verifique as configurações de rede. Basicamente, existem duas opções para uma conexão de rede adequada:
   >* DHCP
   >* Configuração de IP manual


1. Verifique se a configuração do adaptador de rede corresponde às configurações do roteador e se a quantidade máxima de endereços IP disponíveis na rede não foi atingida.

1. Verifique se o roteador está conectado corretamente à rede de área ampla ISP (Internet Link). Isso também pode ser identificado usando um LED de sinal nos roteadores padrão.
1. Se a chamada de URL for bem-sucedida, você poderá continuar instalando os AEM Screens e registrando-se. AEM Screens Start.

   >[!NOTE]
   >**Dica de solução de problemas**
   >Se o AEM Screens não se conectar corretamente e o conteúdo esperado não for exibido:
   >
   >1. Verifique o firewall do Internet Router se há restrições relacionadas a `TCP/IP Port 80/443`.
   >1. Verifique se todas as portas necessárias são permitidas.


## Requisitos para a criação de redes corporativas integradas {#requirements-enclosed-networks}

A configuração de rede corporativa incluída pode ser logicamente separada em dois blocos:

* Rede de longa distância (WAN)
* Rede local interna (LAN).

### Rede de área ampla {#wan-connection}

O desempenho da conexão com a Internet além da acessibilidade da rede é fornecer largura de banda suficiente para operar AEM Screens de forma agradável e suave.
*A largura de banda* suficiente depende da quantidade de telas AEM conectadas e do uso de outros consumidores dentro da rede, como Smartphones, Tablets, Caixas, Computadores ou redes Wi-Fi Convidadas.

>[!NOTE]
>Todos os dispositivos têm acesso simultâneo à conexão com a Internet e a largura de banda geralmente diminui linearmente quando você adiciona mais consumidores ou computadores à rede.

### Rede local {#lan-connection}

O desempenho da LAN (Local Area Network, Rede local), além da acessibilidade da rede, é fornecer largura de banda suficiente para operar AEM Screens de forma agradável e suave.

Atualmente, a rede LAN dentro das organizações corporativas geralmente corresponde a uma rede de 1000 MBit/s, de modo que deve haver largura de banda suficiente para conectar muitos dispositivos com bom desempenho ao sistema. Ao usar outros componentes de rede ativos, é obrigatório que todos eles correspondam aos requisitos de largura de banda da rede.

Por exemplo, os componentes de rede devem corresponder pelo menos ao padrão de 1000 Mbps e à largura de banda fornecida pela especificação Internet Access/Router.

### Outras especificações de redes corporativas {#other-networks}

Geralmente, as redes corporativas têm vários dispositivos conectados, podem ser separados em várias sub-redes e podem ter conexões redundantes ou multiplexadas com a Internet para fornecer desempenho suficiente para muitos milhares de acessos simultâneos.
Esse schema é simplificado e se encaixa na maioria dos casos no ambiente disponível para o cliente.

Caso esteja prevista uma solução Wi-Fi para conectar a tela ao Internet Link, é recomendável usar padrões Wi-Fi modernos, como `IEEE 802.11g` mínimo. Este padrão suporta conexões de até 54 Mbps. Quaisquer padrões *mais recentes* como `802.11h-n` são de melhor qualidade. Se for necessário um Repetidor de Wi-Fi, recomendamos enfaticamente as tecnologias de ponto de acesso de malha Wi-Fi, como o Google Nest Mesh Wi-Fi ou similar.
Outras tecnologias de repetição Wi-Fi acabam com uma perda maciça de largura de banda na rede geral.

## Download de mídia e ativos {#download}

Os AEM Screens oferecem uma grande vantagem aos usuários de placas digitais. Ele está baixando e salvando localmente todos os arquivos de mídia necessários, como Imagens e Vídeo. Devido a este conceito, o tráfego de rede principal está ocorrendo no caso de o novo conteúdo ser exibido em uma tela específica.
Para operação normal, por exemplo, tendo definido uma lista de reprodução que não é alterada com muita frequência durante o dia, isso oferta uma operação próxima da operação independente de rede, depois que todos os arquivos tiverem sido salvos no player. Para os casos de uso em que há mais interações com Sensores ou outros Acionadores e o conteúdo é muito dinâmico, uma conexão de rede rápida e confiável é essencial para uma reação imediata na tela, a fim de garantir a melhor experiência possível do cliente.

As tabelas a seguir ofertas uma boa visão geral do que os dados chave de conectividade da rede significam para o desempenho que pode ser esperado e os possíveis tempos de espera.

>[!NOTE]
>Todas as informações devem ser vistas como o consumo de cada dispositivo na rede que solicita e baixa uma fonte de Internet. Cada uma dessas solicitações adiciona e estende o Tempo de download.

![](/help/using/assets/enclosed-network-download.png)