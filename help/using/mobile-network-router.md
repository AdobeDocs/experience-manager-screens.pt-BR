---
title: Rede móvel com roteador de dados móvel e componentes de rede ativos
description: A página descreve Rede móvel com roteador de dados móvel e componentes de rede ativos
source-git-commit: 4611dd40153ccd09d3a0796093157cd09a8e5b80
workflow-type: tm+mt
source-wordcount: '1035'
ht-degree: 0%

---


# Rede móvel com roteador de dados móvel e componentes de rede ativos {#mobile-network-setup}

Os Players Adobe AEM Screens também podem ser conectados usando redes móveis ou celulares executando pelo menos uma rede 3G.

No AEM Screens, o conteúdo necessário é baixado fisicamente no controlador do reprodutor ou no computador e armazenado corretamente no sistema operacional subjacente. Portanto, a largura de banda fornecida afeta apenas os tempos de download iniciais, bem como as atualizações de conteúdo, e não influencia o desempenho da reprodução regular de telas.

O benefício dessa configuração é que o Roteador Móvel pode ser colocado em um local otimizado para garantir a melhor cobertura disponível da rede. Isso geralmente está em uma posição elevada e aberta, com o menor número possível de betão circundante ou de construção de metal.
Essa configuração permite AEM flexibilidade dos usuários de tela, pois não há necessidade de linha fixa para se conectar ao AEM Screens. Isso é particularmente interessante para configurações efêmeras ou móveis.

O diagrama a seguir mostra a configuração Rede móvel com roteador de dados móvel e componentes de rede ativos e contém um acesso à Internet de qualquer um dos controladores AEM Screens pelo acesso direto à Internet usando um próprio link de dados 3/4/5G.

![](/help/using/assets/mobile-network-1.png)

## Conectar o AEM Screens Player à rede móvel com o roteador de dados móvel e os componentes de rede ativos {#connecting-aem-screens-players}

Siga as etapas abaixo para garantir a conexão correta dos players de Tela de AEM nesta configuração:

A configuração aloca um Acesso à Internet para cada Controlador AEM Screens pelo Acesso direto à Internet usando um Link de dados dedicado 3/4/5G.

1. Certifique-se de que o Roteador de Dados Móveis está corretamente ligado à Rede de Dados Celular, conforme indicado no Sistema Operacional, e de que cada um dos leitores de Tela de AEM está ligado à Rede de Roteadores.
1. Teste a conexão com a Internet chamando um URL no navegador do sistema.
   >[!NOTE]
   >Caso receba um erro, verifique as definições de rede.Existem basicamente duas opções para uma ligação de rede adequada:
   >* DHCP
   >* Configuração IP manual


1. Verifique se a configuração do adaptador de rede corresponde à configuração do roteador.

1. Verifique se o roteador está conectado corretamente à rede de área larga ISP (Internet Link). Isso também pode ser identificado usando um LED de sinal em roteadores padrão.
1. Caso a chamada de URL seja bem-sucedida, você pode continuar instalando o AEM Screens e se registrar. Inicie o AEM Screens.

   >[!NOTE]
   >**Dica de solução de problemas**
   >Se o AEM Screens não se conectar corretamente e o conteúdo esperado não for exibido, verifique o firewall do Internet Router se houver restrições relacionadas a `TCP/IP Port 80/443`.


## Configurando a rede móvel com o roteador de dados móvel e os componentes de rede ativos {#requirements-direct}

A configuração da rede pode ser logicamente separada em dois blocos:

* Conexão de Internet móvel

* Rede local

### Conexão de Internet móvel {#mobile-internet-connection}

O desempenho da conexão com a Internet, além da acessibilidade da rede já descrita, tem que fornecer largura de banda suficiente para realizar downloads de conteúdo do AEM Screens sem problemas.

** O suficiente depende da quantidade de dispositivos de telas de AEM conectados e do uso de outros consumidores dentro da rede, como Smartphones, Tablets, caixas, computadores ou redes Wi-Fi Convidadas.
Lembre-se de que todos os dispositivos têm acesso simultâneo à conexão com a Internet e que a largura de banda geralmente diminui linearmente ao mesmo tempo em que adiciona mais consumidores/computadores à rede.
Para além da ligação teórica específica à rede, é necessário assegurar que a cobertura do roteador móvel seja pelo menos &quot;boa&quot;. Além disso, o Plano Mensal subjacente deve cobrir capacidade de dados suficiente e largura de banda suficiente para atender todos os clientes conectados dentro da LAN conectada.

A tabela a seguir destaca as redes de dados com sua largura de banda padrão:

| Rede de dados | Largura de banda |
|--- |--- |
| 3G | 42 Mbps |
| 4G | 150 Mbps |
| 5G | 1000 - 10000 Mbps |

Ao considerar qual Rede de Dados deve ser usada, é recomendável responder as seguintes perguntas:

* Quantos clientes estão conectados ao roteador?

* Quantas Alterações de conteúdo são esperadas e quais são esses tamanhos médios de arquivo?

>[!NOTE]
>
>O Pacote de dados necessário deve ser pelo menos:
>
>`Data Package Capacity = # of Clients * (# of Content Files * Average File Size)`

>[!IMPORTANT]
>
>Para o upload inicial de arquivos de mídia, por exemplo, ao integrar novos players, é necessário esperar uma quantidade maior de dados e um maior tempo de download e refleti-los nas suposições acima. Uma rede 4G com *boa* cobertura e dados ilimitados devem corresponder às instalações mais comuns nesta Configuração de rede.


### Rede Local {#lan-connection}

O desempenho da LAN, além da acessibilidade de rede já descrita, tem que fornecer largura de banda suficiente para operar downloads de conteúdo AEM Screens sem problemas. Atualmente, a rede LAN geralmente corresponde pelo menos a uma rede de 100 Mbps, de modo que deve haver largura de banda suficiente para conectar muitos dispositivos com bom desempenho ao sistema. Ao usar outro componente de rede ativo, é obrigatório que todos correspondam aos requisitos de largura de banda da rede.

Por exemplo, os Componentes de rede devem corresponder pelo menos ao padrão de 100 Mbps e corresponder à largura de banda fornecida pela especificação do Acesso à Internet/Roteador.

Caso esteja prevista uma solução Wi-Fi para conectar a tela ao Internet Link, é recomendável usar no mínimo os padrões Wi-Fi modernos, como IEEE 802.11g. Este padrão suporta conexões de até 54 Mbps. Quaisquer padrões *mais recentes* como 802.11h-n são de melhor qualidade. Se for necessário um Repetidor de Wi-Fi, recomendamos enfaticamente tecnologias de pontos de acesso Wi-Fi de malha, como Google Nest Mesh Wi-Fi ou similar.

## Download de mídia e ativos {#download}

O AEM Screens oferece uma grande vantagem aos usuários de sinalização digital. Ele baixa e salva localmente todos os arquivos de mídia necessários, como imagens e vídeo. Devido a esse conceito, o tráfego de rede principal está ocorrendo caso haja novo conteúdo a ser exibido em uma tela específica.
Para operação normal, por exemplo, depois de definir uma lista de reprodução que não é atualizada com frequência durante o dia, ela oferece uma operação de fechamento para a rede independente, uma vez que todos os arquivos tenham sido salvos no reprodutor.
Para os casos de uso em que há mais interações com Sensores ou outros Acionadores e o conteúdo é muito dinâmico, uma conexão de rede rápida e confiável é essencial para uma reação imediata na tela, para garantir a melhor experiência possível do cliente.
As tabelas a seguir oferecem uma boa visão geral do que os dados principais de conectividade de rede significam para o desempenho que pode ser esperado e os tempos de espera potenciais.

>[!NOTE]
>
>Todas as informações se referem ao consumo de cada dispositivo na rede que solicita e baixa uma fonte de Internet. Cada uma dessas solicitações adiciona e estende o Tempo de Download.

![](/help/using/assets/mobile-router-download.png)
