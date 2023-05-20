---
title: Rede móvel direta
description: A página descreve a configuração direta da rede móvel
exl-id: 6775bd10-7625-422f-a7af-4f7b8793fa42
source-git-commit: 707833ddd8ab2573abcac4e9a77ec88778624435
workflow-type: tm+mt
source-wordcount: '861'
ht-degree: 0%

---

# Rede móvel direta {#mobile-network-setup}

Os players da AEM Screens também podem ser conectados usando redes móveis ou celulares executando pelo menos uma rede 3G.

No AEM Screens, o conteúdo necessário é baixado fisicamente para o controlador do player ou computador e armazenado corretamente no sistema operacional subjacente. Portanto, a largura de banda fornecida afeta apenas os tempos de download iniciais, bem como as atualizações de conteúdo, e não influencia o desempenho da reprodução regular de Exibições.

A vantagem de conectar os players de AEM Screens pela rede celular 3/4/5G ao seu provedor de dados de serviço móvel é que o roteador móvel pode ser colocado em um ponto otimizado para garantir a melhor cobertura de rede disponível. Esta é geralmente em uma posição elevada e aberta, com o menor número possível de concreto ou construção de metal circundante.

Essa configuração permite que os usuários da tela AEM tenham uma grande flexibilidade, pois não é necessária uma conexão fixa para se conectar ao AEM Screens. Isso é particularmente interessante para configurações efêmeras ou móveis.

O diagrama a seguir mostra a Configuração de rede móvel direta e consiste em um segmento único de conexão de rede e a conexão de cada player à rede de dados móveis ou celulares.

![](/help/using/assets/direct-mobile-1.png)

## Conexão do AEM Screens Player à rede móvel direta {#connecting-aem-screens-players}

Siga as etapas abaixo para garantir a conexão correta dos reprodutores de tela AEM nesta configuração:

1. Verifique se cada um dos reprodutores de tela AEM está conectado à rede do roteador.

1. Teste a conexão com a Internet chamando um URL no navegador do sistema.

   >[!NOTE]
   >Caso receba uma mensagem de erro, verifique as configurações de rede e verifique se há um link de rede suficiente e se o firewall do Sistema Operacional está configurado para permitir o acesso à rede usando as Portas de comunicação AEM Screens configuradas.

1. Caso a chamada de URL seja bem-sucedida, você pode continuar instalando o AEM Screens e se registrar. Inicie o AEM Screens.

## Configurando a rede móvel direta {#requirements-direct}

A configuração de rede pode ser logicamente separada em dois blocos:

* Conexão de Internet Móvel

* Rede local

### Conexão de Internet Móvel {#mobile-internet-connection}

O desempenho da conexão com a Internet além da acessibilidade da rede fornece largura de banda suficiente para operar o AEM Screens sem problemas.

Na Direct Mobile Network, cada player é conectado com um único cartão de dados móvel à rede de dados dos provedores.

A tabela a seguir destaca as redes de dados com sua largura de banda padrão:

| Rede de dados | Largura de banda |
|--- |--- |
| 3G | 42 Mbit/s |
| 4G | 150 Mbit/s |
| 5G | 1000 - 10000 Mbps |

Ao considerar qual rede de dados deve ser usada, é recomendável responder às seguintes perguntas:

A velocidade da rede disponível depende do plano específico do provedor de dados móveis e da cobertura disponível que é atingida no local do controlador do AEM Screens.
Ao seguir essa configuração, também deve ser levado em consideração que, além da largura de banda disponível, alguns Planos do provedor de dados móveis limitam a quantidade disponível de dados provenientes da conexão em um período específico de tempo. É necessário garantir que haja capacidade suficiente em quantidade de dados e largura de banda.
Como acompanhamento, o pacote de dados necessário deve ser, pelo menos:

`Data Package Capacity = # of Clients * (# of Content Files * Average File Size)`


>[!IMPORTANT]
>Para o upload inicial de arquivos de mídia, por exemplo, ao integrar novos players, uma quantidade maior de dados e um tempo de download maior devem ser esperados e refletidos nas suposições acima. Uma rede 4G com *bom* cobertura e *ilimitado* Os dados devem corresponder às instalações mais comuns nesta Configuração de rede.

>[!NOTE]
>Um plano 3G mínimo com boa cobertura de rede deve levar a um desempenho de download aceitável para um reprodutor do AEM Screens. Se houver apenas uma cobertura razoável disponível em um local específico, é importante levar em consideração a mudança da Configuração de rede geral para [Rede Móvel com Roteador de Dados Móvel e Componentes de Rede Ativos](/help/using/mobile-network-router.md).


### Rede local {#lan-connection}

As preocupações com o desempenho da LAN (Local Area Network), além da acessibilidade da rede, são fornecer largura de banda suficiente para operar o AEM Screens sem problemas. A recomendação para velocidades de rede LAN é iniciar redes de 100 Mbps pelo menos, para que haja largura de banda suficiente para conectar muitos dispositivos com bom desempenho ao sistema.

Ao usar outros componentes de rede ativos, é obrigatório que todos eles correspondam aos requisitos de largura de banda da rede. Por exemplo, os componentes de rede devem corresponder pelo menos ao padrão de 100 Mbps e corresponder à largura de banda fornecida pelo acesso à Internet ou pela especificação do roteador. Caso contrário, a largura de banda total será limitada pelo link mais fraco na cadeia de rede.

## Download de mídia e ativos {#download}

O AEM Screens oferece uma grande vantagem aos usuários de sinalização digital. Ele baixa e salva localmente todos os arquivos de mídia necessários, como imagens e vídeos. A maior parte do tráfego de rede ocorre quando há conteúdo novo a ser exibido em uma exibição específica.

Para operações normais, por exemplo, uma lista de reprodução definida que é atualizada frequentemente durante o dia - oferece uma operação próxima à rede independente, uma vez que todos os arquivos tenham sido salvos no reprodutor.

Para cenários onde há mais interações com sensores ou acionadores e conteúdo dinâmico, uma conexão de rede rápida e confiável é essencial para uma reação imediata na tela a fim de garantir a melhor experiência possível do cliente.

A tabela a seguir fornece uma visão geral dos dados principais de conectividade de rede.

>[!NOTE]
>
>Todas as informações se referem ao consumo de cada dispositivo na rede que solicita e faz o download de uma fonte da Internet. Cada uma dessas solicitações adiciona e estende o Tempo de download.

![](/help/using/assets/download-times-mobile.png)
