---
title: Acesso direto à Internet
description: Acesso direto à Internet
translation-type: tm+mt
source-git-commit: ed683a86b7e8c6ec06309577bd0a8690a9cc4684
workflow-type: tm+mt
source-wordcount: '688'
ht-degree: 0%

---


# Rede Internet direta (com fio/sem fio) {#direct-internet-access}

A Direct Internet Network contém um ponto de acesso de entrada para acesso à Internet, a fim de alcançar os AEM cloud services aos quais o AEM Screens precisa se conectar.

As Portas padrão para comunicação com AEM Screens são:
* `http (TCP Port 80)`

   <br>Ou,</br>

* `ssl-secured https (TCP Port 443)`

As portas podem variar devido à configuração de sua configuração de AEM dedicada configurada. Dentro desta configuração, todos os dispositivos são conectados diretamente ao seu roteador de Internet, como mostra a figura abaixo.

![](/help/assets/direct-access-2.png)

A configuração também inclui um acesso à Internet por qualquer ISP (Internet Provedor de serviço) e sua linha da Internet. A maioria dos ISPs fornece um roteador de Internet que cobre o modem da Internet, switch de rede, ponto de acesso Wi-Fi, firewall e outras funcionalidades de rede (dependendo do fabricante e do modelo).

## Conexão do AEM Screens Player ao acesso direto à Internet {#connecting-aem-screens-players}

Siga as etapas abaixo para garantir a conexão correta dos players de tela do AEM nesta configuração:

1. Verifique se cada um dos players de tela do AEM está conectado à rede de roteadores.
1. Teste a conexão com a Internet chamando um URL no navegador do sistema.

   >[!NOTE]
   >Caso receba um erro, verifique as configurações de rede. Basicamente, existem duas opções para uma conexão de rede adequada:
   >* DHCP
   >* Configuração de IP manual


1. Verifique se a configuração do adaptador de rede corresponde às configurações do roteador e se a quantidade máxima de endereços IP disponíveis na rede não foi atingida.

1. Verifique se o roteador está conectado corretamente à rede de área ampla ISP (Internet Link). Isso também pode ser identificado usando um LED de sinal nos roteadores padrão.
1. Se a chamada de URL for bem-sucedida, você poderá continuar instalando os AEM Screens e registrando-se. AEM Screens Start.

   >[!NOTE]
   >**Dica de solução de problemas**
   >Se o AEM Screens não se conectar corretamente e o conteúdo esperado não for exibido:
   >
   >1. Verifique o firewall do Internet Router se há restrições relacionadas a `TCP/IP Port 80/443`.
   >1. Verifique se todas as portas necessárias são permitidas.


## Requisitos para a configuração da rede de acesso direto {#requirements-direct}

A Direct Internet Network é logicamente separada em dois blocos:

* Rede de área ampla

* Rede local

### Rede de área ampla {#wan-connection}

O desempenho da conexão com a Internet além da acessibilidade da rede é fornecer largura de banda suficiente para operar AEM Screens.

*O suficiente* depende do número de telas AEM conectadas e do uso de outros consumidores na rede, como smartphones, tablets, caixas, computadores ou redes Wi-Fi convidadas.

>[!NOTE]
>Todos os dispositivos mencionados acima têm acesso simultâneo à conexão com a Internet e a largura de banda diminui linearmente quando você adiciona mais consumidores ou computadores à rede.

### Rede local {#lan-connection}

O desempenho da Rede local (LAN), além da acessibilidade da rede, fornece largura de banda suficiente para operar AEM Screens.

A rede LAN normalmente corresponde a uma rede de 100 Mbps, de modo que haja largura de banda suficiente para conectar muitos dispositivos com bom desempenho ao sistema.
Caso esteja prevista uma solução Wi-Fi para conectar AEM Screens ao Internet Link, é recomendável usar padrões Wi-Fi modernos, como `IEEE 802.11g` mínimo. Este padrão suporta conexões de até 54 Mbps. Quaisquer padrões *mais recentes* como `802.11h-n` são de melhor qualidade.

>[!NOTE]
>Se for necessário um Repetidor Wi-Fi, é altamente recomendável um ponto de acesso Wi-Fi Mesh, como o Google Nest Mesh Wi-Fi ou similar. Outras tecnologias de repetição Wi-Fi acabam com uma perda enorme de largura de banda na rede geral.

## Download de mídia e ativos {#download}

Os AEM Screens oferecem uma grande vantagem aos usuários de placas digitais. Ele baixa e salva localmente todos os arquivos de mídia necessários, como imagens e vídeos. O principal tráfego de rede ocorre quando há novo conteúdo a ser exibido em uma tela específica.

Para operações normais, por exemplo, uma lista de reprodução definida que é atualizada com frequência durante o dia - oferta uma operação próxima da operação independente da rede, depois que todos os arquivos tiverem sido salvos no player.

Para cenários, em que há mais interações com sensores ou acionadores e conteúdo dinâmico, uma conexão de rede rápida e confiável é essencial para uma reação imediata na tela, a fim de garantir a melhor experiência possível do cliente.

A tabela a seguir fornece uma visão geral sobre os dados principais de conectividade de rede.

>[!NOTE]
>As informações permitem que você visualização o consumo de cada dispositivo na rede solicitando e baixando uma fonte da Internet. Cada uma dessas solicitações adiciona e estende o Tempo de download.

![](/help/assets/download-times-direct.png)

