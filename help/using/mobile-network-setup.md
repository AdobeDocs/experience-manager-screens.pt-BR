---
title: Configuração de rede móvel
description: A página descreve a Configuração de rede móvel
translation-type: tm+mt
source-git-commit: 88ba9ab26c4ecc3f829f53244117041a9a1fd2b3
workflow-type: tm+mt
source-wordcount: '915'
ht-degree: 0%

---


# Configurações de rede móvel {#mobile-network-setup}

Os Players do Adobe AEM Screens também podem ser conectados usando redes móveis/celulares executando pelo menos uma rede 3G.
Nos AEM Screens, o conteúdo necessário é baixado fisicamente no Player Controller/Computer e armazenado corretamente no sistema operacional subjacente. Dessa forma, a largura de banda em questão está afetando apenas os tempos de download iniciais e não influencia o desempenho dos sistemas de exibição.
Conexão de players AEM Screens com uma conexão celular 3/4/5G ao seu provedor de dados do Mobile Service. O benefício desta configuração é que o roteador móvel pode ser colocado em um ponto otimizado para garantir a melhor cobertura disponível da rede. Geralmente, está numa posição elevada e aberta, com o máximo de concreto circundante ou de construção metálica possível.
Essa configuração permite que os usuários de tela do AEM tenham uma grande flexibilidade, pois não há necessidade de uma linha fixa para conectar AEM Screens.


![](/help/using/assets/mobile-network-1.png)

>[!NOTE]
>**Dica de solução de problemas **>Se o AEM Screens não se conectar corretamente e não mostrar o conteúdo esperado:
>
>1. Verifique o Firewall do Internet Router se há restrições relacionadas a `TCP/IP Port 80/443`.
>1. Verifique se todas as portas necessárias são permitidas e tente novamente.




## Requisitos para a configuração da rede móvel {#requirements-direct}

A Configuração de rede, conforme descrito em 5.5, pode ser logicamente separada em três blocos. O Bloco WAN/Outer World/Internet Connection (aqui, conexão de dados móveis), a rede local/LAN interna e as subseções opcionais da LAN separadas por componentes de rede ativos.
Para proporcionar o melhor desempenho possível, é necessário garantir que ambas as seções correspondam aos padrões mínimos recomendados.
O que significa &quot;bom desempenho&quot; no Ambiente AEM Screens?
Os AEM Screens oferecem uma grande vantagem aos usuários de placas digitais. Ele está baixando e salvando localmente todos os arquivos de mídia necessários, como Imagens e Vídeo. Devido a este conceito, o tráfego de rede principal está ocorrendo no caso de o novo conteúdo ser exibido em uma tela específica.
Para operação normal, por exemplo, tendo definido uma lista de reprodução que não é alterada com muita frequência durante o dia, isso oferta uma operação próxima da operação independente de rede, depois que todos os arquivos tiverem sido salvos no player.
Para os casos de uso em que há mais interações com Sensores ou outros Acionadores e o conteúdo é muito dinâmico, uma conexão de rede rápida e confiável é essencial para uma reação imediata na tela, a fim de garantir a melhor experiência possível do cliente.
As tabelas a seguir ofertas uma boa visão geral do que os dados chave de conectividade da rede significam para o desempenho que pode ser esperado e os possíveis tempos de espera.
Todas as informações devem ser vistas como o consumo de cada dispositivo na rede que solicita e baixa uma fonte de Internet. Portanto, cada uma dessas solicitações somam e estendem o Tempo de Download.


### Conexão WAN / Internet {#wan-connection}

O desempenho da Conexão com a Internet, além da capacidade de alcance da rede já descrita, fornece largura de banda suficiente para operar AEM Screens de forma agradável e suave. Em detalhes, &quot;suficiente&quot; depende da quantidade de telas AEM conectadas e do uso de outros consumidores dentro da rede, como Smartphones, Tablets, Caixas, Computadores ou redes Wifi Convidadas.
Lembre-se de que todos os dispositivos têm acesso simultâneo à conexão com a Internet e que a largura de banda geralmente diminui linearmente ao mesmo tempo que adiciona mais consumidores/computadores à rede.
Além da conexão teórica de rede específica que deve ser assegurada, a cobertura do roteador móvel é pelo menos &quot;boa&quot; (consulte o Manual do roteador móvel). Além disso, o plano mensal subjacente tem que cobrir capacidade de dados suficiente e largura de banda suficiente para atender a todos os clientes conectados dentro da LAN conectada.
As redes de dados fornecem uma largura de banda padrão com aprox. até:
・ 3Ir 42 Mbit/s ・ 4Ir 150 Mbit/s ・ 5Ir 1000 Mbit/s-10000 Mbit/sEmbora considere qual rede de dados deve ser usada, é recomendável responder as seguintes perguntas:
・ Quantos clientes estão conectados ao roteador?
・ Quantas alterações de conteúdo eu espero e quais são esses tamanhos médios de arquivo?
Como acompanhamento, o Pacote de dados necessário deve ser pelo menos:
Capacidade do Pacote de dados = # de Clientes * (# de arquivos de conteúdo * Tamanho médio do arquivo) Verifique se há buffer suficiente.
Atenção: Para o upload inicial de arquivos de mídia, por exemplo, ao integrar novos players, é necessário esperar uma quantidade maior de dados e um aumento do tempo de download, o que está sendo refletido nos pressupostos acima.
Como regra geral, uma rede 4G com &quot;boa&quot; cobertura e dados ilimitados deve corresponder às instalações mais comuns nesta configuração de rede


### Conexão LAN {#lan-connection}

O desempenho da LAN, além da capacidade de alcance da rede já descrita, fornece largura de banda suficiente para operar AEM Screens de forma agradável e suave. Atualmente, a rede LAN normalmente corresponde a uma rede de 100 MBit/s, de modo que deve haver largura de banda suficiente para conectar muitos dispositivos com bom desempenho ao sistema. Ao usar outro componente de rede ativo, é obrigatório que todos eles correspondam aos requisitos de largura de banda da rede. Por exemplo, os componentes de rede devem corresponder, no mínimo, ao padrão de 100 Mbit/s e corresponder à largura de banda fornecida pela especificação Internet Access/Router.
Caso uma solução WiFI esteja planejada para conectar a tela ao Internet Link, é recomendável usar no mínimo padrões WIFI modernos, como IEEE 802.11g. Este padrão suporta conexões de até 54 Mbit. Todos os padrões &quot;mais recentes&quot; como o 802.11h-n são de melhor qualidade. Se for necessário um Repetidor Wifi, recomendamos fortemente as tecnologias de ponto de acesso Wifi em malha, como Google Nest Mesh Wifi ou similar.
Outras tecnologias de repetição WiFi acabam com uma perda maciça de largura de banda na rede geral.
