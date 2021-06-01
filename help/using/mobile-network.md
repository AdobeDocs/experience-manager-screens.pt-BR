---
title: Rede móvel direta
description: A página descreve a configuração da rede móvel direta
source-git-commit: 4611dd40153ccd09d3a0796093157cd09a8e5b80
workflow-type: tm+mt
source-wordcount: '861'
ht-degree: 0%

---


# Rede móvel direta {#mobile-network-setup}

Os Players AEM Screens também podem ser conectados usando redes móveis ou celulares executando pelo menos uma rede 3G.

No AEM Screens, o conteúdo necessário é baixado fisicamente no controlador do reprodutor ou no computador e armazenado corretamente no sistema operacional subjacente. Portanto, a largura de banda fornecida só afeta os tempos de download iniciais, bem como as atualizações de conteúdo, e não influencia o desempenho da reprodução regular de telas.

A vantagem de conectar os Players AEM Screens através da Rede Celular 3/4/5G ao seu Provedor de Dados do Serviço Móvel é que o Roteador Móvel pode ser colocado em um local otimizado para garantir a melhor cobertura disponível da rede. Isso geralmente está em uma posição elevada e aberta, com o menor número possível de betão circundante ou de construção de metal.

Essa configuração permite que AEM usuários de tela tenha grande flexibilidade, pois não é necessária uma conexão fixa para se conectar ao AEM Screens. Isso é particularmente interessante para configurações efêmeras ou móveis.

O diagrama a seguir mostra o Direct Mobile Network Setup (Configuração de rede móvel direta) e consiste em um segmento de conexão de rede singular e a conexão de cada reprodutor à rede de dados móvel ou celular.

![](/help/using/assets/direct-mobile-1.png)

## Conectar o AEM Screens Player à rede móvel direta {#connecting-aem-screens-players}

Siga as etapas abaixo para garantir a conexão correta dos players de Tela de AEM nesta configuração:

1. Certifique-se de que cada um dos players de Tela de AEM esteja conectado à Rede do Roteador.

1. Teste a conexão com a Internet chamando um URL no navegador do sistema.

   >[!NOTE]
   >Caso receba uma mensagem de erro, verifique as configurações da rede e verifique se há um link de rede suficiente e se o firewall do Sistema operacional está configurado para permitir acesso à rede usando as portas de comunicação configuradas do AEM Screens.

1. Caso a chamada de URL seja bem-sucedida, você pode continuar instalando o AEM Screens e se registrar. Inicie o AEM Screens.

## Configurando a rede móvel direta {#requirements-direct}

A configuração da rede pode ser logicamente separada em dois blocos:

* Conexão de Internet móvel

* Rede local

### Conexão de Internet móvel {#mobile-internet-connection}

O desempenho da conexão com a Internet além da acessibilidade da rede fornece largura de banda suficiente para operar o AEM Screens sem problemas.

Na rede móvel direta, cada reprodutor é conectado a uma placa de dados móvel singular à rede de provedores de dados.

A tabela a seguir destaca as redes de dados com sua largura de banda padrão:

| Rede de dados | Largura de banda |
|--- |--- |
| 3G | 42 Mbps |
| 4G | 150 Mbps |
| 5G | 1000 - 10000 Mbps |

Ao considerar qual Rede de Dados deve ser usada, é recomendável responder as seguintes perguntas:

A velocidade de rede disponível depende do plano específico do provedor de dados móveis e da cobertura disponível que é alcançada no local do Controlador AEM Screens.
Ao seguir essa configuração, também é necessário considerar que, além da largura de banda disponível, alguns planos de provedores de dados móveis limitam a quantidade disponível de dados que vêm através da conexão em um período específico. É necessário garantir que haja capacidade suficiente em quantidade de dados e largura de banda.
Como acompanhamento, o Pacote de dados necessário deve ser pelo menos:

`Data Package Capacity = # of Clients * (# of Content Files * Average File Size)`


>[!IMPORTANT]
>Para o upload inicial de arquivos de mídia, por exemplo, ao integrar novos players, é necessário esperar uma quantidade maior de dados e um maior tempo de download e refleti-los nas suposições acima. Uma rede 4G com *boa* cobertura e dados *ilimitados* devem corresponder às instalações mais comuns nesta Configuração de Rede.

>[!NOTE]
>Um plano mínimo de 3G com boa cobertura de rede deve levar a um desempenho de download aceitável para um reprodutor AEM Screens. Se houver apenas uma cobertura justa disponível em um local específico, é necessário considerar mudar a configuração geral da rede para [Rede móvel com roteador de dados móvel e componentes de rede ativos](/help/using/mobile-network-router.md).


### Rede Local {#lan-connection}

As preocupações de desempenho da LAN (Local Area Network), além da acessibilidade da rede, são fornecer largura de banda suficiente para operar o AEM Screens sem problemas. A recomendação para as velocidades de rede da LAN é iniciar pelo menos em redes de 100 Mbps, de modo que haja largura de banda suficiente para conectar muitos dispositivos com bom desempenho ao sistema.

Ao usar outros componentes de rede ativos, é obrigatório que todos correspondam aos requisitos de largura de banda da rede. Por exemplo, os componentes de rede devem corresponder pelo menos ao padrão de 100 Mbps e corresponder à largura de banda fornecida pela especificação de acesso à Internet ou Roteador. Caso contrário, a largura de banda total será limitada pelo elo mais fraco da cadeia de rede.

## Download de mídia e ativos {#download}

O AEM Screens oferece uma grande vantagem aos usuários de sinalização digital. Ele baixa e salva localmente todos os arquivos de mídia necessários, como imagens e vídeos. O principal tráfego de rede ocorre quando há novo conteúdo a ser exibido em uma exibição específica.

Para operações normais, por exemplo, uma lista de reprodução definida que é atualizada com frequência durante o dia - oferece uma operação próxima da operação independente de rede, depois que todos os arquivos forem salvos no reprodutor.

Para cenários, em que há mais interações com sensores ou acionadores e conteúdo dinâmico, uma conexão de rede rápida e confiável é essencial para uma reação de tela imediata para garantir a melhor experiência possível do cliente.

A tabela a seguir fornece uma visão geral sobre os dados da chave de conectividade de rede.

>[!NOTE]
>
>Todas as informações se referem ao consumo de cada dispositivo na rede que solicita e baixa uma fonte de Internet. Cada uma dessas solicitações adiciona e estende o Tempo de Download.

![](/help/using/assets/download-times-mobile.png)



