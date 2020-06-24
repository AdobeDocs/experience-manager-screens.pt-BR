---
title: Gerenciamento do tráfego de rede
description: A página descreve Configurações de rede padrão e como gerenciar o tráfego de rede.
translation-type: tm+mt
source-git-commit: 93cc11459e23d3eb22d865bedeb26deaf7135636
workflow-type: tm+mt
source-wordcount: '450'
ht-degree: 0%

---


# Gerenciamento do tráfego de rede {#managing-network-traffic}

Uma Configuração de rede pode ter várias estruturas. Esta seção descreve as configurações de rede mais comuns dentro da configuração de rede de uma organização.

Este guia destaca uma introdução aos servidores proxy seguido pelas várias estruturas de rede configuradas em diferentes organizações.

>[!NOTE]
>
>**Requisitos de rede para AEM Screens**
>
>Os AEM Screens se comunicam diretamente com o AEM como um Cloud Service, portanto, é necessário estabelecer uma conexão estável entre os dois nós. Os firewalls são absolutamente obrigatórios para acesso comercial à Internet e, como cliente, você deve entender quais portas de comunicação precisam ser abertas em firewalls e outros componentes de rede relacionados à segurança da TI.

## Visão geral para servidores proxy {#proxy-servers}

Uma conexão com a Internet depende do uso de um servidor proxy. Um servidor proxy é um computador dedicado ou um sistema de software em execução em um computador que atua como intermediário entre um dispositivo de ponto de extremidade, como um computador, e outro servidor do qual um usuário ou cliente solicita um serviço. O servidor proxy pode existir na mesma máquina que um servidor de firewall ou pode estar em um servidor separado, que encaminha solicitações por meio do firewall.

Uma vantagem de um servidor proxy é que seu cache pode atender a todos os usuários. Se um ou mais sites da Internet forem solicitados com frequência, é provável que eles estejam no cache do proxy, isso melhora o tempo de resposta do usuário. Um proxy também pode registrar suas interações, que são usadas para solução de problemas.

## Como entender as configurações de rede padrão {#network-setups}

Para implementar uma Configuração de rede, consulte os seguintes cenários com seus pontos fortes e detalhes de implantação.

Há quatro tipos principais de configurações de rede:

1. [Rede Internet direta (com fio/sem fio)](/help/using/direct-internet-network.md)
1. [Rede móvel direta](/help/using/mobile-network.md)
1. [Rede móvel com roteador de dados móvel e componentes de rede ativos](/help/using/mobile-network-router.md)
1. [Rede corporativa fechada (com fio/sem fio)](/help/using/enclosed-corporate-network.md)

A tabela a seguir descreve os diferentes tipos de configurações de rede com vantagens e desvantagens:

| Configuração de rede | Vantagens | Desvantagens |
|--- |--- |--- |
| Rede Internet direta (com fio/sem fio) | Fácil e direto para<br>ConfigurarBoa escolha para<br>instalações de médio ou maior porteA rede dedicada pode ser<br>EncapsuladaPoucos pontos de<br>falhaEscalabilidade relativamente<br>barata | Plano obrigatório de dados da Internet |
| Rede móvel direta | Fácil de<br>configurarBoa escolha para<br>instalações médias ou maioresBoa<br>escalabilidadeTelas encapsuladas | Conexão obrigatória com a Internet |
| Rede móvel com roteador de dados móvel e componentes de rede ativos | A escolha fácil de<br>configurarBoa escolha para<br>instalações médias ou maioresA rede dedicada pode ser<br>encapsuladaPoucos pontos de<br>falhaDimensionabilidade relativamente<br>barataBoa | Plano obrigatório de dados da Internet |
| Rede corporativa fechada (com fio/sem fio) | Alta flexibilidade e<br>escalabilidadeAltamente seguro devido a diferentes linhas de<br>defesa<br>redes encapsuladasFácil de monitorar e<br>manterConfiável | Complicado e<br>caroRecomendado para especialistas de rede ou integradores de sistema |
