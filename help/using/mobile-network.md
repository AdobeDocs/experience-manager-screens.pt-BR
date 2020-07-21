---
title: Rede móvel direta
description: A página descreve a configuração de rede móvel direta
translation-type: tm+mt
source-git-commit: 23bb59c719c675baa84c579f624adccc80377661
workflow-type: tm+mt
source-wordcount: '861'
ht-degree: 0%

---


# Rede móvel direta {#mobile-network-setup}

Os Players AEM Screens também podem ser conectados usando redes móveis ou celulares executando pelo menos uma rede 3G.

No AEM Screens, o conteúdo necessário é baixado fisicamente no controlador do player ou no computador e armazenado corretamente no sistema operacional subjacente. Portanto, a largura de banda em questão afeta apenas os tempos de download iniciais, bem como as atualizações de conteúdo, e não influencia o desempenho da reprodução regular de vídeos.

A vantagem de conectar os Players AEM Screens via celular 3/4/5G ao seu Provedor de dados do Mobile Service é que o Roteador Móvel pode ser colocado em um local otimizado para garantir a melhor cobertura disponível da rede. Normalmente, está numa posição elevada e aberta, com o menor número possível de betão circundante ou de construção metálica.

Essa configuração permite que os usuários de tela do AEM tenham uma grande flexibilidade, pois não há uma conexão fixa necessária para se conectarem aos AEM Screens. Isso é particularmente interessante para as configurações efêmeras ou móveis.

O diagrama a seguir mostra a Configuração de rede móvel direta e consiste em um segmento de conexão de rede singular e a conexão de cada player à Rede de dados móvel ou celular.

![](/help/using/assets/direct-mobile-1.png)

## Conectando o AEM Screens Player à rede móvel direta {#connecting-aem-screens-players}

Siga as etapas abaixo para garantir a conexão correta dos players de tela do AEM nesta configuração:

1. Verifique se cada um dos players de tela do AEM está conectado à rede do roteador.

1. Teste a conexão com a Internet chamando um URL no navegador do sistema.

   >[!NOTE]
   >Caso receba uma mensagem de erro, verifique as configurações de rede e verifique se há um link de rede suficiente e se o firewall do sistema operacional está configurado para permitir o acesso à rede usando as portas de comunicação do AEM Screens configuradas.

1. Se a chamada de URL for bem-sucedida, você poderá continuar instalando os AEM Screens e registrando-se. AEM Screens Start.

## Configurando a rede móvel direta {#requirements-direct}

A configuração de rede pode ser logicamente separada em dois blocos:

* Conexão com a Internet móvel

* Rede local

### Conexão com a Internet móvel {#mobile-internet-connection}

O desempenho da conexão com a Internet além da acessibilidade da rede fornece largura de banda suficiente para operar AEM Screens sem problemas.

Na rede móvel direta, cada Player está conectado a uma única placa de dados móvel à rede de provedores.

A tabela a seguir destaca as redes de dados com sua largura de banda padrão:

| Rede de dados | Largura de banda |
|--- |--- |
| 3G | 42 Mbps |
| 4G | 150 Mbps |
| 5G | 1000 - 10000 Mbps |

Ao considerar qual rede de dados deve ser usada, é recomendável responder às seguintes perguntas:

A velocidade de rede disponível depende do plano específico do provedor de dados móveis e da cobertura disponível que é atingida no local da controladora de AEM Screens.
Ao seguir essa configuração, também é necessário levar em consideração que, além da largura de banda disponível, alguns planos do provedor de dados móveis limitam a quantidade disponível de dados que chegam na conexão dentro de um período específico. É necessário garantir que haja capacidade suficiente em termos de quantidade de dados e largura de banda.
Como acompanhamento, o Pacote de dados necessário deve ser pelo menos:

`Data Package Capacity = # of Clients * (# of Content Files * Average File Size)`


>[!IMPORTANT]
>
>Para o upload inicial de arquivos de mídia, por exemplo, ao integrar novos players, é necessário esperar uma quantidade maior de dados e um aumento do tempo de download, o que está sendo refletido nos pressupostos acima. Uma rede 4G com *boa* cobertura e dados *ilimitados* devem corresponder às instalações mais comuns nesta Configuração de rede.

>[!NOTE]
>
>Um plano 3G mínimo com boa cobertura de rede deve levar a um desempenho de download aceitável para um player de AEM Screens. Se houver apenas uma cobertura justa disponível em um local específico, é necessário considerar mudar a configuração geral da rede para Rede [móvel com roteador de dados móvel e componentes](/help/using/mobile-network-router.md)de rede ativos.


### Rede local {#lan-connection}

As preocupações com o desempenho da LAN (Local Area Network), além da acessibilidade da rede, são fornecer largura de banda suficiente para operar AEM Screens sem problemas. A recomendação para as velocidades de rede da LAN é start a redes de 100 Mbps no mínimo, de modo que haja largura de banda suficiente para conectar muitos dispositivos com bom desempenho ao sistema.

Ao usar outros componentes de rede ativos, é obrigatório que todos eles correspondam aos requisitos de largura de banda da rede. Por exemplo, os componentes de rede devem corresponder pelo menos ao padrão de 100 Mbps e à largura de banda fornecida pela especificação de acesso à Internet ou roteador. Caso contrário, a largura de banda total será limitada pelo link mais fraco da cadeia de rede.

## Download de mídia e ativos {#download}

Os AEM Screens oferecem uma grande vantagem aos usuários de placas digitais. Ele baixa e salva localmente todos os arquivos de mídia necessários, como imagens e vídeos. O principal tráfego de rede ocorre quando há novo conteúdo a ser exibido em uma tela específica.

Para operações normais, por exemplo, uma lista de reprodução definida que é atualizada com frequência durante o dia - oferta uma operação próxima da operação independente da rede, depois que todos os arquivos tiverem sido salvos no player.

Para cenários, em que há mais interações com sensores ou acionadores e conteúdo dinâmico, uma conexão de rede rápida e confiável é essencial para uma reação imediata na tela, a fim de garantir a melhor experiência possível do cliente.

A tabela a seguir fornece uma visão geral sobre os dados principais de conectividade de rede.

>[!NOTE]
>
>Todas as informações se referem ao consumo de cada dispositivo na rede que solicita e baixa uma fonte de Internet. Cada uma dessas solicitações adiciona e estende o Tempo de download.

![](/help/using/assets/download-times-mobile.png)



