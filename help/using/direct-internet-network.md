---
title: Acesso Direto à Internet
description: Acesso Direto à Internet
exl-id: a393ce2f-b774-4cd5-9001-c5cc24d445ae
source-git-commit: 707833ddd8ab2573abcac4e9a77ec88778624435
workflow-type: tm+mt
source-wordcount: '697'
ht-degree: 0%

---

# Rede de Internet Direta (Com Fio/Sem Fio) {#direct-internet-access}

A Direct Internet Network contém um ponto de acesso de entrada para acesso à Internet para acessar os serviços em nuvem do AEM aos quais o AEM Screens precisa se conectar.

As portas padrão para comunicação do AEM Screens são:
* `ssl-secured https (TCP Port 443)`

   <br>Ou,</br>

* `http (TCP Port 80)`, se o seu caso de uso específico não exigir esse nível de segurança.

As portas podem variar devido à configuração do seu AEM dedicado. Nessa Configuração, todos os dispositivos são conectados diretamente ao roteador de Internet, conforme mostrado na figura abaixo.

![](/help/assets/direct-access-2.png)

A configuração também inclui um acesso à Internet por qualquer ISP (Internet Service Provider [fornecedor do serviço de acesso à Internet]) e sua linha de Internet. A maioria dos ISPs fornece um roteador de Internet que cobre o modem de Internet, switch de rede, ponto de acesso Wi-Fi, firewall e outras funcionalidades de rede (dependendo do fabricante e do modelo).

## Conexão do AEM Screens Player ao Direct Internet Access {#connecting-aem-screens-players}

Siga as etapas abaixo para garantir a conexão correta dos reprodutores de tela AEM nesta configuração:

1. Verifique se cada um dos reprodutores de tela AEM está conectado à rede do roteador.
1. Teste a conexão com a Internet chamando um URL no navegador do sistema.

   >[!NOTE]
   >Caso receba um erro, verifique as configurações de rede.Basicamente, há duas opções para uma conexão de rede adequada:
   >* DHCP
   >* Configuração de IP Manual


1. Verifique se a Configuração do Adaptador de Rede corresponde às Configurações do Roteador e se a quantidade máxima de endereços IP disponíveis na rede não foi atingida.

1. Verifique se o roteador está conectado corretamente à rede de longa distância ISP (link de Internet). Isso também pode ser identificado usando um LED de sinal nos roteadores padrão.
1. Caso a chamada de URL seja bem-sucedida, você pode continuar instalando o AEM Screens e se registrar. Inicie o AEM Screens.

   >[!NOTE]
   >**Dica de solução de problemas**
   >Se o AEM Screens não se conectar corretamente e o conteúdo esperado não for exibido:
   >
   >1. Verifique o firewall do roteador de Internet se houver restrições relacionadas a `TCP/IP Port 80/443`.
   >1. Verifique se todas as portas necessárias são permitidas.


## Configurando a Rede de Acesso Direto {#requirements-direct}

A Direct Internet Network é separada logicamente em dois blocos:

* Rede de longa distância

* Rede local

### Rede de longa distância {#wan-connection}

O desempenho da conexão com a Internet além da acessibilidade da rede é fornecer largura de banda suficiente para operar o AEM Screens.

*Suficiente* depende do número de telas AEM conectadas e do uso de outros consumidores na rede, como smartphones, tablets, caixas, computadores ou redes Wi-Fi de convidado.

>[!NOTE]
>
>Todos os dispositivos mencionados acima têm acesso simultâneo à conexão de Internet e a largura de banda diminui linearmente quando você adiciona mais consumidores ou computadores à rede.

### Rede local {#lan-connection}

O desempenho da Rede Local (LAN), além da acessibilidade da rede, fornece largura de banda suficiente para operar o AEM Screens.

A rede LAN geralmente corresponde a uma rede de 100 Mbps, de modo que haja largura de banda suficiente para conectar vários dispositivos com bom desempenho ao sistema.
No caso de se prever uma solução Wi-Fi para ligar o AEM Screens à ligação Internet, recomenda-se a utilização de normas Wi-Fi modernas, como `IEEE 802.11g` no mínimo. Este padrão suporta conexões de até 54 Mbps. Qualquer *mais recente* Padrões como `802.11h-n` são de melhor qualidade.

>[!NOTE]
>
>Se um Repetidor Wi-Fi for necessário, é altamente recomendável um ponto de acesso Wi-Fi Mesh como o Google Nest Mesh Wi-Fi ou similar. Outras tecnologias repetitivas Wi-Fi causam uma perda maciça de largura de banda na rede como um todo.

## Download de mídia e ativos {#download}

O AEM Screens oferece uma grande vantagem aos usuários de sinalização digital. Ele baixa e salva localmente todos os arquivos de mídia necessários, como imagens e vídeos. A maior parte do tráfego de rede ocorre quando há conteúdo novo a ser exibido em uma exibição específica.

Para operações normais, por exemplo, uma lista de reprodução definida que é atualizada frequentemente durante o dia - oferece uma operação próxima à rede independente, uma vez que todos os arquivos tenham sido salvos no reprodutor.

Para cenários onde há mais interações com sensores ou acionadores e conteúdo dinâmico, uma conexão de rede rápida e confiável é essencial para uma reação imediata na tela a fim de garantir a melhor experiência possível do cliente.

A tabela a seguir fornece uma visão geral dos dados principais de conectividade de rede.

>[!NOTE]
>
>As informações permitem visualizar o consumo de cada dispositivo na rede que solicita e faz o download de uma origem na Internet. Cada uma dessas solicitações adiciona e estende o Tempo de download.

![](/help/assets/download-times-direct.png)
