---
title: Rede móvel com roteador de dados móvel e componentes de rede ativos
description: A página descreve Rede móvel com roteador de dados móvel e componentes de rede ativos
translation-type: tm+mt
source-git-commit: 6d6637d5222e861fa9a83f555baf0699f56f150a
workflow-type: tm+mt
source-wordcount: '1095'
ht-degree: 0%

---


# Rede móvel com roteador de dados móvel e componentes de rede ativos {#mobile-network-setup}

Os Players do Adobe AEM Screens também podem ser conectados usando redes móveis/celulares executando pelo menos uma rede 3G.
Nos AEM Screens, o conteúdo necessário é baixado fisicamente no Player Controller/Computer e armazenado corretamente no sistema operacional subjacente. Dessa forma, a largura de banda em questão está afetando apenas os tempos de download iniciais e não influencia o desempenho dos sistemas de exibição.
Conexão de players AEM Screens com uma conexão celular 3/4/5G ao seu provedor de dados do Mobile Service. O benefício desta configuração é que o roteador móvel pode ser colocado em um ponto otimizado para garantir a melhor cobertura disponível da rede. Geralmente, está numa posição elevada e aberta, com o máximo de concreto circundante ou de construção metálica possível.
Essa configuração permite que os usuários de tela do AEM tenham uma grande flexibilidade, pois não há necessidade de uma linha fixa para conectar AEM Screens.

![](/help/using/assets/mobile-network-1.png)

## Conectando o AEM Screens Player à rede móvel com o Mobile Data Router e os componentes de rede ativos {#connecting-aem-screens-players}

Siga as etapas abaixo para conectar players de tela AEM nesta configuração:

A configuração contém um Acesso à Internet de qualquer um dos Controladores de AEM Screens por Acesso direto à Internet usando um link de dados 3/4/5G próprio.
A conexão adequada dos players de tela do AEM nesta configuração é simples:

1. Verifique se o Mobile Data Router está conectado corretamente à Rede de dados celular, conforme indicado no sistema operacional.
1. Verifique se cada um dos players de tela do AEM está conectado à rede de roteadores
1. Teste a conexão com a Internet chamando um URL no navegador do sistema.
   >[!NOTE]
   >Caso receba uma mensagem de erro, verifique as configurações de rede. Basicamente, existem duas opções para uma conexão de rede adequada:
   >* DHCP
   >* Configuração de IP manual


1. Verifique se a configuração do adaptador de rede corresponde à configuração do roteador.
1. Verifique se o roteador está conectado corretamente à ISP Wide Area Network (Internet Link). Normalmente, isso também pode ser identificado usando um LED de sinal nos roteadores padrão. Se isso não parecer OK, entre em contato com o serviço ISP para verificar o roteador remotamente.
iv. Se todas as opções acima estiverem configuradas corretamente e ainda houver uma mensagem de erro, verifique seus componentes ativos de rede, como Switches ou Roteadores adicionais, se houver alguma restrição de Porta.
1. Caso a chamada de URL tenha sido bem-sucedida, você pode continuar instalando os AEM Screens e registrá-los adequadamente. AEM Screens Start

   >[!NOTE]
   >**Dica de solução de problemas**
   >Se o AEM Screens não se conectar corretamente e não mostrar o conteúdo esperado:
   >
   >1. Verifique o Firewall do Internet Router se há restrições relacionadas a `TCP/IP Port 80/443`.
   >1. Verifique se todas as portas necessárias são permitidas.



## Requisitos para a configuração de rede móvel com roteador de dados móvel e componentes de rede ativos {#requirements-direct}

A configuração de rede pode ser logicamente separada em dois blocos:

* Conexão com a Internet móvel

* Rede local

### Conexão com a Internet móvel {#mobile-internet-connection}

O desempenho da Conexão com a Internet, além da capacidade de alcance da rede já descrita, fornece largura de banda suficiente para operar AEM Screens de forma agradável e suave. Em detalhes, &quot;suficiente&quot; depende da quantidade de telas AEM conectadas e do uso de outros consumidores dentro da rede, como Smartphones, Tablets, caixas, Computadores ou redes WIFI Convidadas.
Lembre-se de que todos os dispositivos têm acesso simultâneo à conexão com a Internet e que a largura de banda geralmente diminui linearmente, adicionando mais consumidores/computadores à rede.
Além da conexão teórica de rede específica que deve ser assegurada, a cobertura do roteador móvel é pelo menos &quot;boa&quot; (consulte o Manual do roteador móvel). Além disso, o plano mensal subjacente tem que cobrir capacidade de dados suficiente e largura de banda suficiente para atender a todos os clientes conectados dentro da LAN conectada.
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
>Para o upload inicial de arquivos de mídia, por exemplo, ao integrar novos players, é necessário esperar uma quantidade maior de dados e um aumento do tempo de download, que está sendo refletido nas premissas acima. Uma rede 4G com *boa* cobertura e dados ilimitados deve corresponder às instalações mais comuns nesta Configuração de rede.


### Rede local {#lan-connection}

O desempenho da LAN, além da capacidade de alcance da rede já descrita, fornece largura de banda suficiente para operar AEM Screens de forma agradável e suave. Atualmente, a rede LAN normalmente corresponde a uma rede de 100 Mbps, de modo que deve haver largura de banda suficiente para conectar muitos dispositivos com bom desempenho ao sistema. Ao usar outro componente de rede ativo, é obrigatório que todos eles correspondam aos requisitos de largura de banda da rede. Por exemplo, os componentes de rede devem corresponder pelo menos ao padrão de 100 Mbps e corresponder à largura de banda fornecida pela especificação Internet Access/Router.
Caso uma solução WiFI esteja planejada para conectar a tela ao Internet Link, é recomendável usar no mínimo padrões WIFI modernos, como IEEE 802.11g. Este padrão suporta conexões de até 54 Mbps. Todos os padrões &quot;mais recentes&quot; como o 802.11h-n são de melhor qualidade. Se for necessário um Repetidor WIFI, recomendamos fortemente as tecnologias de ponto de acesso Wifi em malha, como Google Nest Mesh WIFI ou similar.
Outras tecnologias de repetição WiFi acabam com uma perda maciça de largura de banda na rede geral.

## Download de mídia e ativos {#download}

Os AEM Screens oferecem uma grande vantagem aos usuários de placas digitais. Ele está baixando e salvando localmente todos os arquivos de mídia necessários, como Imagens e Vídeo. Devido a este conceito, o tráfego de rede principal está ocorrendo no caso de o novo conteúdo ser exibido em uma tela específica.
Para operação normal, por exemplo, tendo definido uma lista de reprodução que não é alterada com muita frequência durante o dia, isso oferta uma operação próxima da operação independente de rede, depois que todos os arquivos tiverem sido salvos no player.
Para os casos de uso em que há mais interações com Sensores ou outros Acionadores e o conteúdo é muito dinâmico, uma conexão de rede rápida e confiável é essencial para uma reação imediata na tela, a fim de garantir a melhor experiência possível do cliente.
As tabelas a seguir ofertas uma boa visão geral do que os dados chave de conectividade da rede significam para o desempenho que pode ser esperado e os possíveis tempos de espera.

>[!NOTE]
>Todas as informações se referem ao consumo de cada dispositivo na rede que solicita e baixa uma fonte de Internet. Cada uma dessas solicitações adiciona e estende o Tempo de download.

![](/help/using/assets/mobile-router-download.png)



