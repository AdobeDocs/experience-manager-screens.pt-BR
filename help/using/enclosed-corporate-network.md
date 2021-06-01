---
title: Rede corporativa fechada
description: Rede corporativa fechada
source-git-commit: 4611dd40153ccd09d3a0796093157cd09a8e5b80
workflow-type: tm+mt
source-wordcount: '709'
ht-degree: 0%

---


# Rede corporativa fechada (com fio/sem fio) {#enclosed-corporate-networks}

O Enclosure Corporate Network SetUp é aplicável a empresas menores, maiores e corporativas. Pode ser teoricamente mais complexo e a configuração lógica é mostrada na figura abaixo.

![](/help/using/assets/enclosed-network-1.png)


## Conectar o Player do AEM Screens ao Acesso Direto à Internet {#connecting-aem-screens-players}

Siga as etapas abaixo para garantir a conexão correta dos players de Tela de AEM nesta configuração:

1. Verifique se cada um dos players de Tela de AEM está conectado à Rede de Roteadores.
1. Teste a conexão com a Internet chamando um URL no navegador do sistema.

   >[!NOTE]
   >Caso receba um erro, verifique as definições de rede.Existem basicamente duas opções para uma ligação de rede adequada:
   >* DHCP
   >* Configuração IP manual


1. Verifique se a configuração do adaptador de rede corresponde às configurações do roteador e se a quantidade máxima de endereços IP disponíveis na rede não foi atingida.

1. Verifique se o roteador está conectado corretamente à rede de área larga ISP (Internet Link). Isso também pode ser identificado usando um LED de sinal em roteadores padrão.
1. Caso a chamada de URL seja bem-sucedida, você pode continuar instalando o AEM Screens e se registrar. Inicie o AEM Screens.

   >[!NOTE]
   >**Dica de solução de problemas**
   >Se o AEM Screens não se conectar corretamente e o conteúdo esperado não for exibido:
   >
   >1. Verifique o firewall do Internet Router se houver restrições relacionadas a `TCP/IP Port 80/443`.
   >1. Certifique-se de que todas as portas necessárias sejam permitidas.


## Configurando redes corporativas fechadas {#requirements-enclosed-networks}

A configuração de rede corporativa incluída pode ser logicamente separada em dois blocos:

* Rede de longa distância (WAN)
* Rede local interna (LAN).

### Rede de longa distância {#wan-connection}

O desempenho da conexão com a Internet, além da acessibilidade da rede, tem que fornecer largura de banda suficiente para operar atualizações de conteúdo do AEM Screens sem problemas.
*A* largura de banda suficiente depende da quantidade de telas de AEM conectadas e do uso de outros consumidores dentro da rede, como smartphones, tablets, caixas, computadores ou redes Wi-Fi convidadas.

>[!NOTE]
>
>Todos os dispositivos têm acesso simultâneo à conexão com a Internet e a largura de banda diminui linearmente quando você adiciona mais consumidores ou computadores à rede.

### Rede Local {#lan-connection}

O desempenho da LAN (Local Area Network), além da acessibilidade da rede, tem que fornecer largura de banda suficiente para operar atualizações de conteúdo do AEM Screens sem problemas.

A rede LAN em organizações corporativas é geralmente de pelo menos 1000 MBit/s, de modo que há largura de banda suficiente para conectar muitos dispositivos com bom desempenho ao sistema. Ao usar outros componentes de rede ativos, é obrigatório que todos correspondam aos requisitos de largura de banda da rede.

Por exemplo, os componentes de Rede devem corresponder pelo menos ao padrão de 100 Mbps e corresponder à largura de banda fornecida pela especificação de acesso/roteador de Internet.

### Outras especificações de redes corporativas {#other-networks}

As redes corporativas têm vários dispositivos conectados, são separados em várias sub-redes e têm conexões redundantes ou multiplexadas com a Internet para fornecer desempenho suficiente para muitos milhares de acessos simultâneos.
Esse esquema é simplificado e se encaixa na maioria dos casos nos ambientes disponíveis para o cliente.

Caso esteja prevista uma solução Wi-Fi para conectar o Screens ao Internet Link, é recomendável usar padrões Wi-Fi modernos, como `IEEE 802.11g` no mínimo. Esta Norma suporta conexões de até 54 Mbps. Quaisquer *padrões mais recentes* como `802.11h-n` são de melhor qualidade. Se for necessário um Repetidor de Wi-Fi, recomendamos enfaticamente as tecnologias de pontos de acesso Wi-Fi de malha, como o Google Nest Mesh Wi-Fi ou similar.
Outras tecnologias de repetição de Wi-Fi acabam com uma perda maciça de largura de banda na rede geral.

## Download de mídia e ativos {#download}

O AEM Screens oferece uma grande vantagem aos usuários de sinalização digital. Ele baixa e salva localmente todos os arquivos de mídia necessários, como imagens e vídeos. O principal tráfego de rede ocorre quando há novo conteúdo a ser exibido em uma exibição específica.

Para operações normais, por exemplo, uma lista de reprodução definida que é atualizada com frequência durante o dia - oferece uma operação próxima da operação independente de rede, depois que todos os arquivos forem salvos no reprodutor.

Para cenários, em que há mais interações com sensores ou acionadores e conteúdo dinâmico, uma conexão de rede rápida e confiável é essencial para uma reação de tela imediata para garantir a melhor experiência possível do cliente.

A tabela a seguir fornece uma visão geral sobre os dados da chave de conectividade de rede.

>[!NOTE]
>As informações permitem visualizar o consumo de cada dispositivo na rede que solicita e baixa uma fonte de Internet. Cada uma dessas solicitações adiciona e estende o Tempo de Download.

![](/help/using/assets/enclosed-network-download.png)
