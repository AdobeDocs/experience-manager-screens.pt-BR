---
title: Acesso Direto à Internet
description: Acesso Direto à Internet
exl-id: a393ce2f-b774-4cd5-9001-c5cc24d445ae
source-git-commit: 873e6ff8b506416bce8660f5eb2cbea75227a9c8
workflow-type: tm+mt
source-wordcount: '694'
ht-degree: 0%

---

# Rede de Internet Direta (Com Fio/Sem Fio) {#direct-internet-access}

A Direct Internet Network contém um ponto de acesso de entrada para acesso à Internet para alcançar o AEM Cloud Service que o AEM Screens deve ter para se conectar.

As portas padrão para comunicação do AEM Screens são:

* `ssl-secured https (TCP Port 443)`
  <br>Ou,</br>

* `http (TCP Port 80)`, se o seu caso de uso específico não exigir esse nível de segurança.

As portas podem variar devido à configuração do AEM dedicado. Nessa Configuração, todos os dispositivos são conectados diretamente ao roteador de Internet, conforme mostrado na figura abaixo.

![](/help/assets/direct-access-2.png)

A configuração também inclui um acesso à Internet por qualquer provedor de serviços de Internet (ISP) e sua linha de Internet. A maioria dos ISPs fornece um roteador de Internet que cobre o modem de Internet, switch de rede, ponto de acesso Wi-Fi, firewall e outras funcionalidades de rede (dependendo do fabricante e do modelo).

## Conexão do AEM Screens Player ao Direct Internet Access

Siga as etapas abaixo para garantir a conexão correta dos reprodutores de tela AEM nesta configuração:

1. Verifique se cada um dos reprodutores de tela AEM está conectado à rede do roteador.
1. Teste a conexão com a Internet chamando um URL no navegador do sistema.

   >[!NOTE]
   >Caso receba um erro, verifique as configurações de rede. Existem basicamente duas opções para uma conexão de rede adequada:
   >* DHCP
   >* Configuração de IP Manual

1. Verifique se a configuração do adaptador de rede corresponde às configurações do roteador; verifique se o número máximo de endereços IP disponíveis na rede não foi atingido.
1. Verifique se o roteador está conectado corretamente à Rede de longa distância ISP (Internet Link). Ou também pode ser identificado usando um LED de sinal nos roteadores padrão.
1. Caso a chamada de URL seja bem-sucedida, você pode continuar instalando o AEM Screens e se registrar. Inicie o AEM Screens.

   >[!NOTE]
   >**Dica de solução de problemas**
   >Se o AEM Screens não se conectar corretamente e o conteúdo esperado não for exibido:
   >
   >1. Verifique no firewall do roteador de Internet se houver restrições relacionadas a `TCP/IP Port 80/443`.
   >1. Verifique se todas as portas necessárias são permitidas.

## Configurando a rede de Internet direta {#requirements-direct}

A Direct Internet Network é separada logicamente em dois blocos:

* Rede de longa distância

* Rede local

### Rede de longa distância {#wan-connection}

O desempenho da conexão com a Internet, além da acessibilidade da rede, é fornecer largura de banda suficiente para operar o AEM Screens.

*Suficiente* depende do número de AEM Screens conectados. Também depende do uso de outros consumidores na rede, como smartphones, tablets, caixas, computadores ou redes Wi-Fi de convidado.

>[!NOTE]
>
>Os dispositivos mencionados acima têm acesso simultâneo à conexão de Internet e a largura de banda diminui linearmente quando você adiciona mais consumidores ou computadores à rede.

### Rede local {#lan-connection}

O desempenho da LAN (Local Area Network), além da acessibilidade da rede, é fornecer largura de banda suficiente para operar o AEM Screens.

A rede LAN geralmente corresponde pelo menos a uma rede de 100 Mbps, de modo que haja largura de banda suficiente para conectar vários dispositivos com bom desempenho ao sistema.
No caso de se prever uma solução Wi-Fi para ligar o AEM Screens à ligação Internet, recomenda-se a utilização de normas Wi-Fi modernas, como `IEEE 802.11g` no mínimo. Este padrão suporta conexões de até 54 Mbps. Qualquer *mais recente* Padrões como `802.11h-n` são de melhor qualidade.

>[!NOTE]
>
>Se um repetidor Wi-Fi for necessário, o Adobe recomenda um ponto de acesso Wi-Fi em malha, como o Google Nest Mesh Wi-Fi ou similar. Outras tecnologias repetitivas Wi-Fi causam uma perda maciça de largura de banda na rede como um todo.

## Download de mídia e ativos {#download}

O AEM Screens oferece uma vantagem significativa aos usuários de sinalização digital. Ele baixa e salva localmente todos os arquivos de mídia necessários, como imagens e vídeos. A maior parte do tráfego de rede ocorre quando há conteúdo novo a ser exibido em uma exibição específica.

Para operações normais, por exemplo, uma lista de reprodução definida que é atualizada frequentemente durante o dia - oferece uma operação próxima à operação independente da rede, depois que todos os arquivos são salvos no reprodutor.

Para cenários onde há mais interações com sensores ou acionadores e conteúdo dinâmico, uma conexão de rede rápida e confiável é essencial para uma reação imediata na tela a fim de garantir a melhor experiência possível do cliente.

A tabela a seguir fornece uma visão geral dos dados principais de conectividade de rede.

>[!NOTE]
>
>As informações permitem visualizar o consumo de cada dispositivo na rede, solicitando e baixando uma fonte da Internet. Cada uma dessas solicitações adiciona e estende o Tempo de download.

![](/help/assets/download-times-direct.png)
