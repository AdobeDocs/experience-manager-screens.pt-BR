---
title: Rede Móvel com Roteador de Dados Móvel e Componentes de Rede Ativos
description: A página descreve a rede móvel com o roteador de dados móveis e os componentes de rede ativos
exl-id: a6b44a04-438d-49d4-ac98-32629c11dcdb
source-git-commit: ef74265eadf5972eae7451b7725946d8b014c198
workflow-type: tm+mt
source-wordcount: '1043'
ht-degree: 0%

---

# Rede Móvel com Roteador de Dados Móvel e Componentes de Rede Ativos {#mobile-network-setup}

Os players de AEM Screens Adobe também podem ser conectados usando redes móveis ou celulares executando pelo menos uma rede 3G.

No AEM Screens, o conteúdo necessário é baixado fisicamente para o controlador do player ou computador e armazenado corretamente no sistema operacional subjacente. Portanto, a largura de banda fornecida afeta apenas os tempos de download iniciais e as atualizações de conteúdo, e não influencia o desempenho da reprodução regular de Exibições.

A vantagem dessa configuração é que o roteador móvel pode ser colocado em um ponto otimizado para garantir a melhor cobertura de rede disponível. Este ponto é geralmente em uma posição elevada e aberta, com o menor número possível de estruturas de concreto ou metal circundantes.
Essa configuração dá aos usuários da tela AEM flexibilidade porque não é necessária uma linha fixa para se conectar ao AEM Screens. Também é interessante para configurações efêmeras ou móveis.

O diagrama a seguir mostra a configuração Rede móvel com o roteador de dados móveis e os componentes de rede ativos. Ele contém um acesso de Internet de qualquer uma das controladoras AEM Screens por acesso direto à Internet usando um próprio link de dados 3/4/5G.

![](/help/using/assets/mobile-network-1.png)

## Conectar o AEM Screens Player à rede móvel com o Roteador de dados móveis e os Componentes de rede ativos {#connecting-aem-screens-players}

Siga as etapas abaixo para garantir a conexão correta dos reprodutores de tela AEM nesta configuração:

A configuração aloca um acesso à Internet para cada Controlador AEM Screens através de acesso direto à Internet usando um Link de dados dedicado 3/4/5G.

1. Verifique se o roteador de dados móveis está conectado corretamente à rede de dados celular conforme indicado no sistema operacional. E verifique se cada um dos reprodutores de tela AEM está conectado à rede de roteadores.
1. Teste a conexão com a Internet chamando um URL no navegador do sistema.

   >[!NOTE]
   >Caso receba um erro, verifique as configurações de rede. Existem basicamente duas opções para uma conexão de rede adequada:
   >* DHCP
   >* Configuração de IP Manual

1. Verifique se a Configuração do Adaptador de Rede corresponde à Configuração do Roteador.

1. Verifique se o roteador está conectado corretamente à rede de longa distância (link de Internet) do provedor de serviços de Internet. Você pode verificar usando um LED de sinal nos roteadores padrão.
1. Caso a chamada de URL seja bem-sucedida, você pode continuar instalando o AEM Screens e se registrar. Inicie o AEM Screens.

   >[!TIP]
   >Você pode descobrir que a conexão do AEM Screens não está funcionando corretamente. O conteúdo esperado não é exibido. Nesses casos, verifique o firewall do roteador de Internet se houver restrições relacionadas a `TCP/IP Port 80/443`.


## Configurando a rede móvel com o roteador de dados móveis e os componentes de rede ativos {#requirements-direct}

A configuração de rede pode ser logicamente separada em dois blocos:

* Conexão de Internet Móvel

* Rede local

### Conexão de Internet Móvel {#mobile-internet-connection}

O desempenho da conexão com a Internet, além da acessibilidade de rede já descrita, tem de fornecer largura de banda suficiente para fazer downloads de conteúdo do AEM Screens sem problemas.

*Suficiente* depende do número de dispositivos AEM Screens conectados. Também depende do uso de outros consumidores na rede, como Smartphones, Tablets, Caixas, Computadores ou redes Wi-Fi Guest.
Lembre-se de que todos os dispositivos têm acesso simultâneo à conexão com a Internet e a largura de banda está diminuindo linearmente enquanto acrescenta mais consumidores/computadores à rede.
Além da conexão de rede teórica específica, é necessário garantir que a cobertura do roteador móvel seja de pelo menos *boa*. Além disso, o plano mensal subjacente deve cobrir capacidade de dados suficiente e largura de banda suficiente para atender a todos os clientes conectados na LAN conectada.

A tabela a seguir destaca as redes de dados com sua largura de banda padrão:

| Rede de dados | Largura de banda |
|--- |--- |
| 3G | 42 Mbit/s |
| 4G | 150 Mbit/s |
| 5G | 1000 - 10000 Mbps |

Ao considerar qual rede de dados deve ser usada, a Adobe recomenda que você responda às seguintes perguntas:

* Quantos clientes estão conectados ao roteador?
* Quantas alterações de conteúdo são esperadas e quais são os tamanhos médios de arquivo?

>[!NOTE]
>
>O pacote de dados necessário deve ser pelo menos:
>
>`Data Package Capacity = # of Clients * (# of Content Files * Average File Size)`

>[!IMPORTANT]
>
>Para o upload inicial de arquivos de mídia durante a integração de novos players, é necessário esperar uma quantidade maior de dados e um maior tempo de download. Isso também se reflete nas suposições acima. Uma rede 4G com *boa* cobertura e dados ilimitados deve corresponder às instalações mais comuns nesta Configuração de Rede.


### Rede local {#lan-connection}

O desempenho da LAN, além da acessibilidade de rede já descrita, tem de fornecer largura de banda suficiente para operar os downloads de conteúdo do AEM Screens sem problemas. Nesses dias, a rede LAN geralmente corresponde pelo menos a uma rede de 100 Mbps, de modo que deve haver largura de banda suficiente para conectar vários dispositivos com bom desempenho ao sistema. Ao usar outros componentes de rede ativos, é obrigatório que todos eles correspondam aos requisitos de largura de banda da rede.

Por exemplo, os componentes de rede devem corresponder pelo menos ao padrão de 100 Mbps e corresponder à largura de banda fornecida pela especificação de acesso à Internet/roteador.

Caso uma solução Wi-Fi esteja planejada para conectar a tela ao Link de Internet, é recomendável usar no mínimo padrões Wi-Fi modernos, como IEEE `802.11g`. Este padrão suporta conexões de até 54 Mbps. Quaisquer *padrões mais recentes*, como `802.11h-n`, são de melhor qualidade. Se um repetidor Wi-Fi for necessário, o Adobe recomenda tecnologias de ponto de acesso Wi-Fi em malha, como Google Nest Mesh Wi-Fi ou semelhante.

## Download de mídia e Assets {#download}

O AEM Screens oferece uma vantagem significativa aos usuários de sinalização digital. Ele baixa e salva localmente todos os arquivos de mídia necessários, como Imagens e Vídeo. Devido a esse conceito, o maior tráfego de rede está ocorrendo no caso de haver novo conteúdo a ser exibido em uma tela específica.
Para operação normal, tendo uma lista de reprodução definida que não é atualizada frequentemente, ele oferece operação quase independente de rede quando todos os arquivos são salvos no reprodutor.
Para casos de uso em que há mais interações com Sensores ou outros Acionadores e o conteúdo é dinâmico, uma conexão de rede rápida e confiável é essencial para uma reação imediata da tela. Ele garante a melhor experiência possível do cliente.
As tabelas a seguir oferecem uma boa visão geral do que os dados principais de conectividade de rede significam para o desempenho que pode ser esperado e os possíveis tempos de espera.

>[!NOTE]
>
>Todas as informações se referem ao consumo de cada dispositivo na rede que solicita e faz o download de uma fonte da Internet. Cada uma dessas solicitações adiciona e estende o Tempo de download.

![](/help/using/assets/mobile-router-download.png)
