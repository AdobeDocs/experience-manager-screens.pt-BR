---
title: Rede móvel direta
description: A página descreve a configuração de rede móvel direta
translation-type: tm+mt
source-git-commit: 8e62b3fc4ce324e02aaec6fca9df79b1aaf94d72
workflow-type: tm+mt
source-wordcount: '825'
ht-degree: 0%

---


# Rede móvel direta {#mobile-network-setup}

Os Players AEM Screens também podem ser conectados usando redes móveis ou celulares executando pelo menos uma rede 3G.

Dentro dos AEM Screens, o conteúdo necessário é baixado fisicamente no controlador do player ou no computador e armazenado corretamente no sistema operacional subjacente. Portanto, a largura de banda em questão afeta apenas os tempos de download iniciais e não influencia o desempenho dos monitores.

Conexão de players AEM Screens com uma conexão celular 3/4/5G ao seu Provedor de dados do Mobile Service. A vantagem desta configuração é que o roteador móvel pode ser colocado em um ponto otimizado para garantir a melhor cobertura disponível da rede. Esta posição é geralmente elevada e aberta, com o máximo de betão circundante ou de construção metálica possível.

Essa configuração permite que os usuários de tela do AEM tenham uma grande flexibilidade, pois não há uma conexão fixa necessária para se conectarem aos AEM Screens.

O diagrama a seguir mostra a Configuração de rede móvel direta e consiste em um segmento de conexão de rede singular, a conexão de cada player à rede móvel/celular de dados.

![](/help/using/assets/direct-mobile-1.png)

## Conectando o AEM Screens Player à rede móvel direta {#connecting-aem-screens-players}

Siga as etapas abaixo para conectar os players de AEM Screens nesta configuração:

1. Verifique se cada um dos players de tela do AEM está conectado à rede de roteadores.

1. Teste a conexão com a Internet chamando um URL no navegador do sistema.

   >[!NOTE]
   >Caso receba uma mensagem de erro, verifique as configurações de rede. Basicamente, existem duas opções para uma conexão de rede adequada:
   >* DHCP
   >* Configuração de IP manual


1. Verifique se a configuração do adaptador de rede corresponde à configuração do roteador.

1. Verifique se o roteador está conectado corretamente à ISP Wide Area Network (Internet Link). Isso também pode ser identificado usando um LED de sinal nos roteadores padrão.

1. Se a chamada de URL for bem-sucedida, você poderá continuar instalando os AEM Screens e registrando-se. AEM Screens Start.

   >[!NOTE]
   >**Dica de solução de problemas**
   >Se o AEM Screens não se conectar corretamente e não mostrar o conteúdo esperado:
   >
   >1. Verifique o Firewall do Internet Router se há restrições relacionadas a `TCP/IP Port 80/443`.
   >1. Verifique se todas as portas necessárias são permitidas.



## Requisitos para a configuração da rede móvel {#requirements-direct}

A configuração de rede pode ser logicamente separada em dois blocos:

* Conexão com a Internet móvel

* Rede local

### Conexão com a Internet móvel {#mobile-internet-connection}

O desempenho da conexão com a Internet, além da acessibilidade da rede, fornece largura de banda suficiente para operar AEM Screens sem problemas.

*O suficiente* depende da quantidade de telas AEM conectadas e do uso de outros consumidores dentro da rede, como Smartphones, Tablets, caixas, computadores ou redes WIFI Convidadas.

>[!NOTE]
>Todos os dispositivos têm acesso simultâneo à conexão com a Internet e a largura de banda diminui linearmente ao adicionar mais consumidores ou computadores à rede.

As redes de dados fornecem largura de banda padrão com:

**3G**
* 42 Mbps

**4G**
* 150 Mbps

**5G**
* 1000 Mbps-10000 Mbps

Ao considerar qual rede de dados deve ser usada, é recomendável responder às seguintes perguntas:

* Quantos clientes estão conectados ao roteador?

* Quantas alterações de conteúdo são esperadas e quais são esses tamanhos médios de arquivo?

>[!NOTE]
>O Pacote de dados necessário deve ser pelo menos:
`Data Package Capacity = # of Clients * (# of Content Files * Average File Size)`

>[!IMPORTANT]
>Verifique se há buffer suficiente.
>Para o upload inicial de arquivos de mídia, por exemplo, ao integrar novos players, é necessário esperar uma quantidade maior de dados e um aumento do tempo de download, o que está sendo refletido nas premissas acima.Uma rede 4G com *boa* cobertura e dados *ilimitados* devem corresponder às instalações mais comuns nesta configuração de rede.


### Rede local {#lan-connection}

O desempenho da LAN (Local Area Network) além da acessibilidade da rede é fornecer largura de banda suficiente para operar AEM Screens sem problemas. A rede LAN normalmente corresponde a uma rede de 100 Mbps, de modo que deve haver largura de banda suficiente para conectar muitos dispositivos com bom desempenho ao sistema.

Ao usar outros componentes de rede ativos, é obrigatório que todos eles correspondam aos requisitos de largura de banda da rede. Por exemplo, os componentes de rede devem corresponder pelo menos ao padrão de 100 Mbps e à largura de banda fornecida pela especificação Internet Access/Router.

## Download de mídia e ativos {#download}

Os AEM Screens oferecem uma grande vantagem aos usuários de placas digitais. Ele baixa e salva localmente todos os arquivos de mídia necessários, como imagens e vídeos. Devido a isso, ocorre um grande tráfego de rede caso haja novo conteúdo a ser exibido em uma tela específica.
Para operações normais, por exemplo, uma lista de reprodução definida que não é atualizada com frequência durante o dia, oferta uma operação próxima da operação independente da rede, depois que todos os arquivos tiverem sido salvos no player.
Para os casos de uso em que há mais interações com Sensores ou outros Acionadores e o conteúdo é muito dinâmico, uma conexão de rede rápida e confiável é essencial para uma reação imediata na tela, a fim de garantir a melhor experiência possível do cliente.

A tabela a seguir fornece uma visão geral dos principais dados de conectividade de rede responsáveis pelo desempenho que pode ser esperado e possíveis tempos de espera.

>[!NOTE]
>Todas as informações se referem ao consumo de cada dispositivo na rede que solicita e baixa uma fonte de Internet. Cada uma dessas solicitações adiciona e estende o Tempo de download.

![](/help/using/assets/download-times-mobile.png)



