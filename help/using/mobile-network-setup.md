---
title: Rede móvel direta
description: A página descreve a configuração de rede móvel direta
translation-type: tm+mt
source-git-commit: 0b1106b3cf7f83857f83e43f773a0d19556cfec5
workflow-type: tm+mt
source-wordcount: '951'
ht-degree: 0%

---


# Rede móvel direta {#mobile-network-setup}

Os Players AEM Screens também podem ser conectados usando redes móveis ou celulares executando pelo menos uma rede 3G.

Dentro dos AEM Screens, o conteúdo necessário é baixado fisicamente no controlador do player ou no computador e armazenado corretamente no sistema operacional subjacente. Dessa forma, a largura de banda em questão afeta apenas os tempos iniciais de download e não influencia o desempenho dos monitores.

Conexão de players AEM Screens com uma conexão celular 3/4/5G ao seu provedor de dados do Mobile Service. A vantagem desta configuração é que o roteador móvel pode ser colocado em um local otimizado para garantir a melhor cobertura disponível da rede. Geralmente, está numa posição elevada e aberta, com o máximo de concreto circundante ou de construção metálica possível.

Essa configuração permite que os usuários de tela do AEM tenham uma grande flexibilidade, pois não há uma conexão fixa necessária para conectar AEM Screens.

![](/help/using/assets/direct-mobile-1.png)

## Conectando o AEM Screens Player à rede móvel direta {#connecting-aem-screens-players}

Siga as etapas abaixo para conectar players de tela AEM nesta configuração:

1. Verifique se cada um dos players de tela do AEM está conectado à rede de roteadores.

1. Teste a conexão com a Internet chamando um URL no navegador do sistema.

   >[!NOTE]
   >Caso receba uma mensagem de erro, verifique as configurações de rede. Basicamente, existem duas opções para uma conexão de rede adequada:
   >* DHCP
   >* Configuração de IP manual


1. Verifique se a configuração do adaptador de rede corresponde à configuração do roteador.
1. Verifique se o roteador está conectado corretamente à ISP Wide Area Network (Internet Link). Normalmente, isso também pode ser identificado usando um LED de sinal nos roteadores padrão.
1. Se tudo o acima estiver configurado corretamente e uma mensagem de erro ainda estiver aparecendo, verifique seus componentes ativos de rede, como Switches ou Roteadores adicionais, se houver alguma restrição de Porta.
1. Caso a chamada de URL tenha sido bem-sucedida, você pode continuar instalando os AEM Screens e registrá-los adequadamente. AEM Screens Start.

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


### Rede local {#lan-connection}

O desempenho da LAN, além da capacidade de alcance da rede já descrita, fornece Bandwith suficiente para operar AEM Screens de forma agradável e suave. Atualmente, a rede LAN normalmente corresponde a uma rede de 100 MBit/s, de modo que deve haver Bandwith suficiente para conectar muitos dispositivos com bom desempenho ao sistema. Ao usar outro componente de rede ativo, é obrigatório que todos eles correspondam aos requisitos da banda de rede. Por exemplo, os componentes de rede devem corresponder pelo menos ao padrão de 100 Mbit/s e corresponder ao Bandade fornecido pela especificação de acesso à Internet/roteador.

## Download de mídia e ativos {#download}

Os AEM Screens oferecem uma grande vantagem aos usuários de placas digitais. Ele está baixando e salvando localmente todos os arquivos de mídia necessários, como Imagens e Vídeo. Devido a este conceito, o tráfego de rede principal está ocorrendo no caso de o novo conteúdo ser exibido em uma tela específica.
Para operação normal, por exemplo, tendo definido uma lista de reprodução que não é alterada com muita frequência durante o dia, isso oferta uma operação próxima da operação independente de rede, depois que todos os arquivos tiverem sido salvos no player.
Para os casos de uso em que há mais interações com Sensores ou outros Acionadores e o conteúdo é muito dinâmico, uma conexão de rede rápida e confiável é essencial para uma reação imediata na tela, a fim de garantir a melhor experiência possível do cliente.
As tabelas a seguir ofertas uma boa visão geral do que os dados chave de conectividade da rede significam para o desempenho que pode ser esperado e os possíveis tempos de espera.
Todas as informações devem ser vistas como o consumo de cada dispositivo na rede que solicita e baixa uma fonte de Internet. Portanto, cada uma dessas solicitações somam e estendem o Tempo de Download.

![](/help/using/assets/download-times-mobile.png)



