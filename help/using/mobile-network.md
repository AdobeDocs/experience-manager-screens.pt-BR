---
title: Rede móvel direta
description: Saiba mais sobre a configuração de rede móvel direta no AEM Screens.
exl-id: 6775bd10-7625-422f-a7af-4f7b8793fa42
source-git-commit: ce8340f24d116b4268a6ed15dd4e9f626bad1ef6
workflow-type: tm+mt
source-wordcount: '845'
ht-degree: 0%

---

# Rede móvel direta {#mobile-network-setup}

Os players da AEM Screens também podem ser conectados usando redes móveis ou celulares executando pelo menos uma rede 3G.

No AEM Screens, o conteúdo necessário é baixado fisicamente para o controlador do player ou computador e armazenado corretamente no sistema operacional subjacente. Portanto, a largura de banda fornecida afeta apenas os tempos de download iniciais e as atualizações de conteúdo, e não influencia o desempenho da reprodução regular de exibições.

A vantagem de conectar os players de AEM Screens sobre celular 3/4/5G ao seu provedor de dados de serviço móvel é que o roteador móvel pode ser colocado em um ponto otimizado. Isso garante a melhor cobertura de rede disponível. Esta localização é geralmente em uma posição elevada e aberta, com o menor número possível de estruturas de concreto ou metal circundantes.

Essa configuração permite que os usuários da tela AEM tenham grande flexibilidade porque não é necessária uma conexão fixa para se conectar ao AEM Screens. Esta disposição é interessante para configurações efêmeras ou móveis.

O diagrama a seguir mostra a Configuração direta da rede móvel. Consiste em um segmento único de conexão de rede e a conexão de cada player à rede de dados móvel ou celular.

![](/help/using/assets/direct-mobile-1.png)

## Conexão do AEM Screens Player à rede móvel direta

Siga as etapas abaixo para garantir a conexão correta dos reprodutores de tela AEM nesta configuração:

1. Verifique se cada um dos reprodutores de tela AEM está conectado à rede do roteador.

1. Teste a conexão com a Internet chamando um URL no navegador do sistema.

   >[!NOTE]
   >Se você receber uma mensagem de erro, verifique as configurações de rede e verifique se há um link de rede suficiente. Verifique também se o firewall do sistema operacional está configurado para permitir o acesso à rede ao usar as portas de comunicação configuradas da AEM Screens.

1. Se a chamada de URL for bem-sucedida, você poderá continuar instalando o AEM Screens e se registrar. Inicie o AEM Screens.

## Configurando a rede móvel direta {#requirements-direct}

A configuração de rede pode ser logicamente separada em dois blocos:

* Conexão de Internet Móvel

* Rede local

### Conexão de Internet Móvel {#mobile-internet-connection}

O desempenho da conexão com a Internet além da acessibilidade da rede fornece largura de banda suficiente para operar o AEM Screens sem problemas.

Na Direct Mobile Network, cada player é conectado a uma única placa de dados móvel à rede de dados do provedor.

A tabela a seguir destaca as redes de dados com sua largura de banda padrão:

| Rede de dados | Largura de banda |
|--- |--- |
| 3G | 42 Mbit/s |
| 4G | 150 Mbit/s |
| 5G | 1000 - 10000 Mbps |

Ao considerar qual rede de dados deve ser usada, considere o seguinte:

A velocidade da rede disponível depende do plano específico do provedor de dados móveis e da cobertura disponível que é atingida no local do controlador do AEM Screens.
Ao seguir essa configuração, considere que além da largura de banda disponível, alguns Planos do provedor de dados móveis limitam a quantidade disponível de dados que chegam através da conexão em um tempo específico. Deve-se garantir que haja capacidade suficiente nas quantidades de dados e largura de banda.
Como acompanhamento, o pacote de dados necessário deve ser pelo menos:

`Data Package Capacity = # of Clients * (# of Content Files * Average File Size)`


>[!IMPORTANT]
>Para o upload inicial de arquivos de mídia ao integrar novos players, uma quantidade maior de dados e um tempo de download maior devem ser esperados; isso se reflete nas suposições acima. Uma rede 4G com *boa* cobertura e *ilimitada* dados deve corresponder às instalações mais comuns nesta Configuração de Rede.

>[!NOTE]
>Um plano 3G mínimo com boa cobertura de rede deve levar a um desempenho de download aceitável para um AEM Screens Player. Se houver apenas cobertura adequada disponível em um local específico, considere alternar a Configuração de Rede geral para [Rede Móvel com Roteador de Dados Móveis e Componentes de Rede Ativos](/help/using/mobile-network-router.md).


### Rede local {#lan-connection}

As preocupações com o desempenho da LAN (Local Area Network), além da acessibilidade da rede, são fornecer largura de banda suficiente para operar o AEM Screens sem problemas. A recomendação para as velocidades de rede LAN é iniciar em redes de 100-Mbps pelo menos, para que haja largura de banda suficiente para conectar muitos dispositivos com bom desempenho ao sistema.

Ao usar outros componentes de rede ativos, é obrigatório que todos eles correspondam aos requisitos de largura de banda da rede. Por exemplo, os componentes de rede devem corresponder pelo menos ao padrão de 100 Mbps e corresponder à largura de banda fornecida pelo acesso à Internet ou pela especificação do roteador. Caso contrário, a largura de banda total será limitada pelo link mais fraco na cadeia de rede.

## Download de mídia e Assets {#download}

O AEM Screens oferece uma vantagem significativa aos usuários de sinalização digital. Ele baixa e salva localmente todos os arquivos de mídia necessários, como imagens e vídeos. A maior parte do tráfego de rede ocorre quando há conteúdo novo a ser exibido em uma exibição específica.

Para operações normais, por exemplo, uma lista de reprodução definida que é atualizada frequentemente durante o dia - oferece uma operação próxima à operação independente da rede, depois que todos os arquivos são salvos no reprodutor.

Para cenários onde há mais interações com sensores ou acionadores e conteúdo dinâmico, uma conexão de rede rápida e confiável é essencial para uma reação imediata na tela a fim de garantir a melhor experiência possível do cliente.

A tabela a seguir fornece uma visão geral dos dados principais de conectividade de rede.

>[!NOTE]
>
>Todas as informações se referem ao consumo de cada dispositivo na rede que solicita e faz o download de uma fonte da Internet. Cada uma dessas solicitações adiciona e estende o Tempo de download.

![](/help/using/assets/download-times-mobile.png)
