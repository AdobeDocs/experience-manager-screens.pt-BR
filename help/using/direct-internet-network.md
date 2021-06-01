---
title: Acesso direto à Internet
description: Acesso direto à Internet
source-git-commit: 4611dd40153ccd09d3a0796093157cd09a8e5b80
workflow-type: tm+mt
source-wordcount: '697'
ht-degree: 0%

---


# Rede direta da Internet (com fio/sem fio) {#direct-internet-access}

A Direct Internet Network contém um ponto de acesso de entrada para acesso à Internet a fim de acessar os Serviços em Nuvem do AEM aos quais a AEM Screens precisa se conectar.

As portas padrão para comunicação com o AEM Screens são:
* `ssl-secured https (TCP Port 443)`

   <br>Ou,</br>

* `http (TCP Port 80)`, se seu caso de uso específico não exigir esse nível de segurança.

As portas podem variar devido à configuração de configuração de AEM dedicada. Nesta configuração, todos os dispositivos são conectados diretamente ao roteador da Internet, como mostrado na figura abaixo.

![](/help/assets/direct-access-2.png)

A configuração também inclui um acesso à Internet por qualquer provedor de serviços de Internet (ISP) e sua linha da Internet. A maioria dos ISPs fornece um roteador de Internet que cobre o modem da Internet, switch de rede, ponto de acesso Wi-Fi, firewall e outras funcionalidades de rede (dependendo do fabricante e do modelo).

## Conectar o Player do AEM Screens ao Acesso Direto à Internet {#connecting-aem-screens-players}

Siga as etapas abaixo para garantir a conexão correta dos players de Tela de AEM nesta configuração:

1. Certifique-se de que cada um dos players de Tela de AEM esteja conectado à Rede do Roteador.
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


## Configurando a rede de acesso direto {#requirements-direct}

A Direct Internet Network está logicamente separada em dois blocos:

* Rede de longa distância

* Rede local

### Rede de longa distância {#wan-connection}

O desempenho da conexão com a Internet além da acessibilidade da rede é fornecer largura de banda suficiente para operar o AEM Screens.

** O suficiente depende do número de telas de AEM conectadas e do uso de outros consumidores dentro da rede, como smartphones, tablets, caixas, computadores ou redes Wi-Fi convidadas.

>[!NOTE]
>
>Todos os dispositivos mencionados acima têm acesso simultâneo à conexão com a Internet e a largura de banda diminui linearmente quando você adiciona mais consumidores ou computadores à rede.

### Rede Local {#lan-connection}

O desempenho da Rede de Área Local (LAN), além da acessibilidade da rede, fornece largura de banda suficiente para operar a AEM Screens.

A rede LAN geralmente corresponde pelo menos a uma rede de 100 Mbps, de modo que haja largura de banda suficiente para conectar muitos dispositivos com bom desempenho ao sistema.
Caso esteja prevista uma solução Wi-Fi para conectar o AEM Screens ao Internet Link, é recomendável usar no mínimo os padrões Wi-Fi modernos, como `IEEE 802.11g`. Este padrão suporta conexões de até 54 Mbps. Quaisquer *padrões mais recentes* como `802.11h-n` são de melhor qualidade.

>[!NOTE]
>
>Se for necessário um Repetidor de Wi-Fi, é altamente recomendável um ponto de acesso de malha Wi-Fi, como Google Nest Mesh Wi-Fi ou similar. Outras tecnologias de repetição de Wi-Fi acabam com uma perda maciça de largura de banda na rede geral.

## Download de mídia e ativos {#download}

O AEM Screens oferece uma grande vantagem aos usuários de sinalização digital. Ele baixa e salva localmente todos os arquivos de mídia necessários, como imagens e vídeos. O principal tráfego de rede ocorre quando há novo conteúdo a ser exibido em uma exibição específica.

Para operações normais, por exemplo, uma lista de reprodução definida que é atualizada com frequência durante o dia - oferece uma operação próxima da operação independente de rede, depois que todos os arquivos forem salvos no reprodutor.

Para cenários, em que há mais interações com sensores ou acionadores e conteúdo dinâmico, uma conexão de rede rápida e confiável é essencial para uma reação de tela imediata para garantir a melhor experiência possível do cliente.

A tabela a seguir fornece uma visão geral sobre os dados da chave de conectividade de rede.

>[!NOTE]
>
>As informações permitem visualizar o consumo de cada dispositivo na rede que solicita e baixa uma fonte de Internet. Cada uma dessas solicitações adiciona e estende o Tempo de Download.

![](/help/assets/download-times-direct.png)

