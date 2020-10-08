---
title: Rede móvel com roteador de dados móvel e componentes de rede ativos
description: A página descreve Rede móvel com roteador de dados móvel e componentes de rede ativos
translation-type: tm+mt
source-git-commit: 9b54b153676852742859b704ac9aedf908fceecf
workflow-type: tm+mt
source-wordcount: '1035'
ht-degree: 0%

---


# Rede móvel com roteador de dados móvel e componentes de rede ativos {#mobile-network-setup}

Os Players Adobe AEM Screens também podem ser conectados usando redes móveis ou celulares executando pelo menos uma rede 3G.

No AEM Screens, o conteúdo necessário é baixado fisicamente no controlador do player ou no computador e armazenado corretamente no sistema operacional subjacente. Portanto, a largura de banda em questão afeta apenas os tempos de download iniciais, bem como as atualizações de conteúdo, e não influencia o desempenho da reprodução regular de vídeos.

A vantagem dessa configuração é que o Roteador móvel pode ser colocado em um ponto otimizado para garantir a melhor cobertura disponível da rede. Normalmente, está numa posição elevada e aberta, com o menor número possível de betão circundante ou de construção metálica.
Esta configuração permite AEM usuários de tela flexibilidade, pois não há necessidade de uma linha fixa para se conectar ao AEM Screens. Isso é particularmente interessante para as configurações efêmeras ou móveis.

O diagrama a seguir mostra a configuração Rede móvel com roteador de dados móveis e componentes de rede ativos e contém um acesso à Internet de qualquer um dos controladores AEM Screens pelo acesso direto à Internet usando um link de dados 3/4/5G próprio.

![](/help/using/assets/mobile-network-1.png)

## Conectando o AEM Screens Player à rede móvel com o roteador de dados móvel e os componentes de rede ativos {#connecting-aem-screens-players}

Siga as etapas abaixo para garantir a conexão correta dos players de tela AEM nesta configuração:

A configuração aloca um Acesso à Internet para cada Controlador AEM Screens através do Acesso direto à Internet usando um Link de Dados dedicado 3/4/5G.

1. Verifique se o Mobile Data Router está conectado corretamente à Rede de dados celular, conforme indicado no sistema operacional, e se cada um dos players de tela AEM está conectado à Rede de roteadores.
1. Teste a conexão com a Internet chamando um URL no navegador do sistema.
   >[!NOTE]
   >Caso receba um erro, verifique as configurações de rede. Basicamente, existem duas opções para uma conexão de rede adequada:
   >* DHCP
   >* Configuração de IP manual


1. Verifique se a configuração do adaptador de rede corresponde à configuração do roteador.

1. Verifique se o roteador está conectado corretamente à ISP Wide Area Network (Internet Link). Isso também pode ser identificado usando um LED de sinal nos roteadores padrão.
1. Se a chamada de URL for bem-sucedida, você pode continuar instalando o AEM Screens e se registrar. Start AEM Screens.

   >[!NOTE]
   >**Dica de solução de problemas**
   >Se a AEM Screens não se conectar corretamente e o conteúdo esperado não for exibido, verifique o firewall do Internet Router se há restrições relacionadas a `TCP/IP Port 80/443`.


## Configuração de rede móvel com roteador de dados móvel e componentes de rede ativos {#requirements-direct}

A configuração de rede pode ser logicamente separada em dois blocos:

* Conexão com a Internet móvel

* Rede local

### Conexão com a Internet móvel {#mobile-internet-connection}

O desempenho da conexão com a Internet, além da acessibilidade da rede já descrita, tem que fornecer largura de banda suficiente para executar downloads de conteúdo da AEM Screens sem problemas.

*O suficiente* depende da quantidade de dispositivos de telas AEM conectados e do uso de outros consumidores na rede, como Smartphones, Tablets, Caixas, Computadores ou Redes Wi-Fi Convidadas.
Lembre-se de que todos os dispositivos têm acesso simultâneo à conexão com a Internet e que a largura de banda geralmente diminui linearmente, adicionando mais consumidores/computadores à rede.
Para além da ligação teórica à rede específica, é necessário garantir que a cobertura do roteador móvel seja pelo menos &quot;boa&quot;. Além disso, o plano mensal subjacente tem que cobrir capacidade de dados suficiente e largura de banda suficiente para atender a todos os clientes conectados dentro da LAN conectada.

A tabela a seguir destaca as redes de dados com sua largura de banda padrão:

| Rede de dados | Largura de banda |
|--- |--- |
| 3G | 42 Mbps |
| 4G | 150 Mbps |
| 5G | 1000 - 10000 Mbps |

Ao considerar qual rede de dados deve ser usada, é recomendável responder às seguintes perguntas:

* Quantos clientes estão conectados ao roteador?

* Quantas alterações de conteúdo são esperadas e quais são esses tamanhos médios de arquivo?

>[!NOTE]
>
>O Pacote de dados necessário deve ser pelo menos:
>
>`Data Package Capacity = # of Clients * (# of Content Files * Average File Size)`

>[!IMPORTANT]
>
>Para o upload inicial de arquivos de mídia, por exemplo, ao integrar novos players, é necessário esperar uma quantidade maior de dados e um aumento do tempo de download, que está sendo refletido nas premissas acima. Uma rede 4G com *boa* cobertura e dados ilimitados deve corresponder às instalações mais comuns nesta Configuração de rede.


### Rede local {#lan-connection}

O desempenho da LAN, além da acessibilidade da rede já descrita, tem que fornecer largura de banda suficiente para operar downloads de conteúdo da AEM Screens sem problemas. Atualmente, a rede LAN normalmente corresponde a uma rede de 100 Mbps, de modo que deve haver largura de banda suficiente para conectar muitos dispositivos com bom desempenho ao sistema. Ao usar outros componentes de rede ativos, é obrigatório que todos eles correspondam aos requisitos de largura de banda da rede.

Por exemplo, os componentes de rede devem corresponder pelo menos ao padrão de 100 Mbps e à largura de banda fornecida pela especificação Internet Access/Router.

Caso esteja prevista uma solução Wi-Fi para conectar a tela ao Internet Link, é recomendável usar no mínimo padrões Wi-Fi modernos, como IEEE 802.11g. Este padrão suporta conexões de até 54 Mbps. Todos os padrões *mais recentes* como o 802.11h-n são de melhor qualidade. Se for necessário um Repetidor de Wi-Fi, recomendamos enfaticamente as tecnologias de ponto de acesso de malha Wi-Fi, como o Google Nest Mesh Wi-Fi ou similar.

## Download de mídia e ativos {#download}

A AEM Screens oferece uma grande vantagem aos usuários de placas digitais. Ele baixa e salva localmente todos os arquivos de mídia necessários, como Imagens e Vídeo. Devido a este conceito, o tráfego de rede principal está ocorrendo no caso de o novo conteúdo ser exibido em uma tela específica.
Para operações normais, por exemplo, tendo definido uma lista de reprodução que não é atualizada com frequência durante o dia, isso oferta uma operação próxima da operação independente da rede, depois que todos os arquivos tiverem sido salvos no player.
Para os casos de uso em que há mais interações com Sensores ou outros Acionadores e o conteúdo é muito dinâmico, uma conexão de rede rápida e confiável é essencial para uma reação imediata na tela, a fim de garantir a melhor experiência possível do cliente.
As tabelas a seguir ofertas uma boa visão geral do que os dados chave de conectividade da rede significam para o desempenho que pode ser esperado e os possíveis tempos de espera.

>[!NOTE]
>
>Todas as informações se referem ao consumo de cada dispositivo na rede que solicita e baixa uma fonte de Internet. Cada uma dessas solicitações adiciona e estende o Tempo de download.

![](/help/using/assets/mobile-router-download.png)
