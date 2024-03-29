---
title: Rede Móvel com Roteador de Dados Móvel e Componentes de Rede Ativos
description: A página descreve a rede móvel com o roteador de dados móveis e os componentes de rede ativos
exl-id: a6b44a04-438d-49d4-ac98-32629c11dcdb
source-git-commit: 707833ddd8ab2573abcac4e9a77ec88778624435
workflow-type: tm+mt
source-wordcount: '1035'
ht-degree: 0%

---

# Rede Móvel com Roteador de Dados Móvel e Componentes de Rede Ativos {#mobile-network-setup}

Os players de AEM Screens Adobe também podem ser conectados usando redes móveis ou celulares executando pelo menos uma rede 3G.

No AEM Screens, o conteúdo necessário é baixado fisicamente para o controlador do player ou computador e armazenado corretamente no sistema operacional subjacente. Portanto, a largura de banda fornecida afeta apenas os tempos de download iniciais, bem como as atualizações de conteúdo, e não influencia o desempenho da reprodução regular de Exibições.

A vantagem dessa configuração é que o roteador móvel pode ser colocado em um local otimizado para garantir a melhor cobertura de rede disponível. Esta é geralmente em uma posição elevada e aberta, com o menor número possível de concreto ou construção de metal circundante.
Essa configuração permite flexibilidade aos usuários da Tela AEM, pois não é necessário um telefone fixo para se conectar ao AEM Screens. Isso é particularmente interessante para configurações efêmeras ou móveis.

O diagrama a seguir mostra a configuração de Mobile Network with Mobile Data Router and Ative Network Components e contém um acesso à Internet de qualquer um dos controladores AEM Screens por acesso direto à Internet usando um próprio link de dados 3/4/5G.

![](/help/using/assets/mobile-network-1.png)

## Conectar o AEM Screens Player à rede móvel com o Roteador de dados móveis e os Componentes de rede ativos {#connecting-aem-screens-players}

Siga as etapas abaixo para garantir a conexão correta dos reprodutores de tela AEM nesta configuração:

A configuração aloca um acesso à Internet para cada controlador AEM Screens por acesso direto à Internet usando um link de dados dedicado 3/4/5G.

1. Verifique se o roteador de dados móveis está conectado corretamente à rede de dados celular conforme indicado no sistema operacional e se cada um dos players de tela AEM está conectado à rede de roteadores.
1. Teste a conexão com a Internet chamando um URL no navegador de sistemas.
   >[!NOTE]
   >Caso receba um erro, verifique as configurações de rede.Basicamente, há duas opções para uma conexão de rede adequada:
   >* DHCP
   >* Configuração de IP Manual


1. Verifique se a Configuração do Adaptador de Rede corresponde à Configuração do Roteador.

1. Verifique se o roteador está conectado corretamente à ISP Wide Area Network (Internet Link). Isso também pode ser identificado usando um LED de sinal em roteadores padrão.
1. Caso a chamada de URL seja bem-sucedida, você pode continuar instalando o AEM Screens e se registrar. Inicie o AEM Screens.

   >[!NOTE]
   >**Dica de solução de problemas**
   >Se o AEM Screens não se conectar corretamente e o conteúdo esperado não for exibido, verifique no firewall do roteador de Internet se há restrições relacionadas a `TCP/IP Port 80/443`.


## Configurando a rede móvel com o roteador de dados móveis e os componentes de rede ativos {#requirements-direct}

A configuração de rede pode ser logicamente separada em dois blocos:

* Conexão de Internet Móvel

* Rede local

### Conexão de Internet Móvel {#mobile-internet-connection}

O desempenho da conexão com a Internet, além da acessibilidade de rede já descrita, tem de fornecer largura de banda suficiente para fazer downloads de conteúdo do AEM Screens sem problemas.

*Suficiente* depende da quantidade de dispositivos AEM conectados e do uso de outros consumidores na rede, como smartphones, tablets, caixas, computadores ou redes Wi-Fi convidadas.
Lembre-se de que todos os dispositivos têm acesso simultâneo à conexão com a Internet e a largura de banda geralmente diminui linearmente enquanto acrescenta mais consumidores/computadores à rede.
Além da conexão de rede teórica específica, é necessário garantir que a cobertura do roteador móvel seja pelo menos &quot;boa&quot;. Além disso, o plano mensal subjacente deve cobrir capacidade de dados suficiente e largura de banda suficiente para atender a todos os clientes conectados na LAN conectada.

A tabela a seguir destaca as redes de dados com sua largura de banda padrão:

| Rede de dados | Largura de banda |
|--- |--- |
| 3G | 42 Mbit/s |
| 4G | 150 Mbit/s |
| 5G | 1000 - 10000 Mbps |

Ao considerar qual rede de dados deve ser usada, é recomendável responder às seguintes perguntas:

* Quantos clientes estão conectados ao roteador?

* Quantas alterações de conteúdo são esperadas e quais são os tamanhos médios de arquivo?

>[!NOTE]
>
>O pacote de dados necessário deve ser pelo menos:
>
>`Data Package Capacity = # of Clients * (# of Content Files * Average File Size)`

>[!IMPORTANT]
>
>Para o upload inicial de arquivos de mídia, por exemplo, ao integrar novos players, uma quantidade maior de dados e um tempo de download maior devem ser esperados e refletidos nas suposições acima. Uma rede 4G com *bom* A cobertura e os dados ilimitados devem corresponder às instalações mais comuns nesta Configuração de rede.


### Rede local {#lan-connection}

O desempenho da LAN, além da acessibilidade de rede já descrita, tem de fornecer largura de banda suficiente para operar os downloads de conteúdo do AEM Screens sem problemas. Nesses dias, a rede LAN geralmente corresponde pelo menos a uma rede de 100 Mbps, de modo que deve haver largura de banda suficiente para conectar muitos dispositivos com bom desempenho ao sistema. Ao usar outro componente de rede ativo, é obrigatório que todos eles correspondam aos requisitos de largura de banda da rede.

Por exemplo, os componentes de rede devem corresponder pelo menos ao padrão de 100 Mbps e corresponder à largura de banda fornecida pela especificação de acesso à Internet/roteador.

Caso uma solução Wi-Fi esteja planejada para conectar a tela ao link da Internet, é recomendável usar no mínimo padrões Wi-Fi modernos, como IEEE 802.11g. Este padrão suporta conexões de até 54 Mbps. Qualquer *mais recente* Padrões como o 802.11h-n são de melhor qualidade. Se um repetidor Wi-Fi for necessário, recomendamos enfaticamente tecnologias de ponto de acesso Wi-Fi Mesh como Google Nest Mesh Wi-Fi ou similares.

## Download de mídia e ativos {#download}

O AEM Screens oferece uma grande vantagem aos usuários de sinalização digital. Ele baixa e salva localmente todos os arquivos de mídia necessários, como Imagens e Vídeo. Devido a esse conceito, o maior tráfego de rede está ocorrendo caso haja novo conteúdo a ser exibido em uma tela específica.
Para uma operação normal, por exemplo, tendo definido uma lista de reprodução que não é atualizada com frequência durante o dia, isto oferece uma operação próxima da rede, uma vez que todos os arquivos tenham sido salvos no leitor.
Para os casos de uso em que há mais interações com Sensores ou outros Acionadores e o conteúdo é muito dinâmico, uma conexão de rede rápida e confiável é essencial para uma reação imediata na tela para garantir a melhor experiência possível do cliente.
As tabelas a seguir oferecem uma boa visão geral do que os dados principais de conectividade de rede significam para o desempenho que pode ser esperado e os possíveis tempos de espera.

>[!NOTE]
>
>Todas as informações se referem ao consumo de cada dispositivo na rede que solicita e faz o download de uma fonte da Internet. Cada uma dessas solicitações adiciona e estende o Tempo de download.

![](/help/using/assets/mobile-router-download.png)
