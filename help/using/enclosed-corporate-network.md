---
title: Rede Corporativa Fechada
description: Rede Corporativa Fechada
exl-id: b8c52e72-86da-4089-ba02-0c643862419f
source-git-commit: 1e8beb9dfaf579250138d4a41eeec88cc81f2d39
workflow-type: tm+mt
source-wordcount: '703'
ht-degree: 0%

---

# Rede corporativa fechada (com fio/wireless) {#enclosed-corporate-networks}

A Configuração de Rede Corporativa Fechada é aplicável a empresas menores, maiores e corporativas. Pode ser teoricamente mais complexa, e a configuração lógica é mostrada na figura abaixo.

![](/help/using/assets/enclosed-network-1.png)


## Conexão do AEM Screens Player ao Direct Internet Access

Siga as etapas abaixo para garantir a conexão correta dos reprodutores de tela AEM nesta configuração:

1. Verifique se cada um dos reprodutores de tela AEM está conectado à rede de roteadores.
1. Teste a conexão com a Internet chamando um URL no navegador do sistema.

   >[!NOTE]
   >Caso receba um erro, verifique as configurações de rede. Existem basicamente duas opções para uma conexão de rede adequada:
   >* DHCP
   >* Configuração de IP Manual

1. Verifique se a Configuração do Adaptador de Rede corresponde às Configurações do Roteador e se o número máximo de endereços IP disponíveis na rede não foi atingido.

1. Verifique se o roteador está conectado corretamente à rede de longa distância ISP (Internet Link). Isso também pode ser identificado usando um LED de sinal nos roteadores padrão.
1. Caso a chamada de URL seja bem-sucedida, você pode continuar instalando o AEM Screens e se registrar. Inicie o AEM Screens.

   >[!NOTE]
   >**Dica de solução de problemas**
   >Se o AEM Screens não se conectar corretamente e o conteúdo esperado não for exibido:
   >
   >1. Verifique o firewall do roteador de Internet se houver restrições relacionadas a `TCP/IP Port 80/443`.
   >1. Verifique se todas as portas necessárias são permitidas.

## Configurando Redes Corporativas Fechadas {#requirements-enclosed-networks}

A Configuração de Rede Corporativa Incluída pode ser separada logicamente em dois blocos:

* Rede de longa distância (WAN)
* Rede local (LAN) interna.

### Rede de longa distância {#wan-connection}

O desempenho da conexão com a Internet, além da acessibilidade da rede, tem de fornecer largura de banda suficiente para operar atualizações de conteúdo do AEM Screens sem problemas.
*Largura de banda suficiente* depende do número de telas AEM conectadas e do uso de outros consumidores na rede, como smartphones, tablets, caixas, computadores ou redes Wi-Fi guest.

>[!NOTE]
>
>Todos os dispositivos têm acesso simultâneo à conexão com a Internet e a largura de banda diminui linearmente quando você adiciona mais consumidores ou computadores à rede.

### Rede local {#lan-connection}

O desempenho da LAN (Local Area Network, rede local), além da acessibilidade da rede, precisa fornecer largura de banda suficiente para operar as atualizações de conteúdo do AEM Screens sem problemas.

A rede LAN dentro das organizações corporativas é geralmente uma rede de pelo menos 1000 MBit/seg, de modo que haja largura de banda suficiente para conectar muitos dispositivos com bom desempenho ao sistema. Ao usar outros componentes de rede ativos, é obrigatório que todos eles correspondam aos requisitos de largura de banda da rede.

Por exemplo, os componentes de rede devem corresponder pelo menos ao padrão de 100 Mbps e corresponder à largura de banda fornecida pela especificação de acesso/roteador da Internet.

### Outras especificações de redes corporativas {#other-networks}

As redes corporativas têm vários dispositivos conectados, são separadas em várias sub-redes e têm conexões de Internet redundantes ou multiplexadas para fornecer desempenho suficiente para milhares de acessos simultâneos.
Esse esquema é simplificado e se adapta à maioria dos casos aos ambientes disponíveis para o cliente.

No caso de se prever uma solução Wi-Fi para ligar o Screens à ligação Internet, recomenda-se a utilização de normas Wi-Fi modernas, como `IEEE 802.11g` no mínimo. Este padrão suporta conexões de até 54 Mbps. Qualquer *mais recente* Padrões como `802.11h-n` são de melhor qualidade. Se um repetidor Wi-Fi for necessário, o Adobe recomenda tecnologias de ponto de acesso Wi-Fi em malha, como Google Nest Mesh Wi-Fi ou semelhante.
Outras tecnologias repetitivas Wi-Fi causam uma perda maciça de largura de banda na rede como um todo.

## Download de mídia e ativos {#download}

O AEM Screens oferece uma vantagem significativa aos usuários de sinalização digital. Ele baixa e salva localmente todos os arquivos de mídia necessários, como imagens e vídeos. A maior parte do tráfego de rede ocorre quando há conteúdo novo a ser exibido em uma exibição específica.

Para operações normais, por exemplo, uma lista de reprodução definida que é atualizada frequentemente durante o dia - oferece uma operação próxima à operação independente da rede, depois que todos os arquivos são salvos no reprodutor.

Para cenários onde há mais interações com sensores ou acionadores e conteúdo dinâmico, uma conexão de rede rápida e confiável é essencial para uma reação imediata na tela a fim de garantir a melhor experiência possível do cliente.

A tabela a seguir fornece uma visão geral dos dados principais de conectividade de rede.

>[!NOTE]
>As informações permitem visualizar o consumo de cada dispositivo na rede que solicita e faz o download de uma origem na Internet. Cada uma dessas solicitações adiciona e estende o Tempo de download.

![](/help/using/assets/enclosed-network-download.png)
