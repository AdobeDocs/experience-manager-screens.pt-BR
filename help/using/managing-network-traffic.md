---
title: Gerenciamento do tráfego de rede
description: A página descreve Configurações de rede padrão e como gerenciar o tráfego de rede.
translation-type: tm+mt
source-git-commit: 173ce977549ed64e3750bb751a8fe1b27e277aa2
workflow-type: tm+mt
source-wordcount: '559'
ht-degree: 0%

---


# Gerenciamento do tráfego de rede {#managing-network-traffic}

Uma Configuração de rede pode ter várias estruturas. Esta seção descreve as configurações de rede mais comuns e as abordagens generalizadas seguidas em uma organização.

Este guia destaca uma introdução aos servidores proxy seguido pelas várias estruturas de rede configuradas em diferentes organizações.

>[!NOTE]
>
>**Requisitos de rede para AEM Screens**
>
>Os AEM Screens se comunicam diretamente com o AEM como um Cloud Service, portanto, é necessário estabelecer uma conexão estável entre os dois nós. Os firewalls são absolutamente obrigatórios para acesso comercial à Internet e, como cliente, você deve entender quais portas de comunicação precisam ser abertas nesses firewalls e outros componentes de rede relacionados à segurança da TI.

## Visão geral para servidores proxy {#proxy-servers}

Uma conexão com a Internet depende do uso de um servidor proxy. Um servidor proxy é um computador dedicado ou um sistema de software em execução em um computador que atua como intermediário entre um dispositivo de ponto de extremidade, como um computador, e outro servidor do qual um usuário ou cliente solicita um serviço. O servidor proxy pode existir na mesma máquina que um servidor de firewall ou pode existir em um servidor separado, que encaminha solicitações por meio do firewall.

Uma vantagem de um servidor proxy é que seu cache pode atender a todos os usuários. Se um ou mais sites da Internet forem solicitados com frequência, é provável que eles estejam no cache do proxy e isso melhora ainda mais o tempo de resposta do usuário. Um proxy também pode registrar suas interações, que podem ser usadas para solução de problemas.

Quando um servidor proxy recebe uma solicitação de um recurso da Internet (como uma página da Web ou ao se conectar a um editor AEM), ele verifica seu cache local de urls anteriormente chamados de urls. Se encontrar a página, ela a retornará ao usuário sem encaminhar a solicitação para a Internet. Se a página não estiver no cache, o servidor proxy (atua como cliente) em nome do usuário e solicita a página do servidor na Internet. Quando o conteúdo é retornado, o servidor proxy o relaciona à solicitação original e o encaminha ao usuário.

## Como entender as configurações de rede padrão {#network-setups}

Para implementar uma Configuração de rede, consulte os seguintes cenários com seus pontos fortes e detalhes de implantação.

Este Guia destaca quatro tipos diferentes de Configurações de rede em uma organização:

* **[Rede Internet direta (com fio/sem fio)](/help/using/direct-internet-network.md)**
* **[Rede móvel direta](/help/using/mobile-network.md)**
* **[Rede móvel com roteador de dados móvel e componentes de rede ativos](/help/using/mobile-network-router.md)**
* **[Rede corporativa fechada (com fio/sem fio)](/help/using/enclosed-corporate-network.md)**

A tabela a seguir descreve os diferentes tipos de configurações de rede com vantagens e desvantagens:

| Configuração de rede | Vantagens | Desvantagens |
|--- |--- |--- |
| **Rede Internet direta (com fio/sem fio)** | Fácil e direto para<br>ConfigurarBoa escolha para<br>instalações de médio ou maior porteA rede dedicada pode ser<br>EncapsuladaPoucos pontos de<br>falhaEscalabilidade relativamente<br>barata | Plano obrigatório de dados da Internet |
| **Rede móvel direta** | Fácil de<br>configurarBoa escolha para<br>instalações médias ou maioresBoa<br>escalabilidadeTelas encapsuladas | Conexão obrigatória com a Internet |
| **Rede móvel com roteador de dados móvel e componentes de rede ativos** | A escolha fácil de<br>configurarBoa escolha para<br>instalações médias ou maioresA rede dedicada pode ser<br>encapsuladaPoucos pontos de<br>falhaDimensionabilidade relativamente<br>barataBoa | Plano obrigatório de dados da Internet |
| **Rede corporativa fechada (com fio/sem fio)** | Alta flexibilidade e<br>escalabilidadeAltamente seguro devido a diferentes linhas de<br>defesa<br>redes encapsuladasFácil de monitorar e<br>manterConfiável | Complicado e<br>caroRecomendado para especialistas de rede ou integradores de sistema |
