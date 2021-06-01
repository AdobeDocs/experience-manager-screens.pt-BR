---
title: Gerenciamento do tráfego de rede
description: A página descreve as Configurações de rede padrão e como gerenciar o tráfego da rede.
source-git-commit: 4611dd40153ccd09d3a0796093157cd09a8e5b80
workflow-type: tm+mt
source-wordcount: '559'
ht-degree: 0%

---


# Gerenciamento do tráfego de rede {#managing-network-traffic}

Uma Configuração de Rede pode ter várias estruturas. Esta seção descreve as configurações de rede mais comuns e as abordagens generalizadas seguidas em uma organização.

Este guia destaca uma introdução aos servidores proxy seguida pelas várias estruturas de rede configuradas em diferentes organizações.

>[!NOTE]
>**Requisitos de rede AEM Screens**
>O AEM Screens se comunica diretamente com o AEM como um Cloud Service, portanto, é necessário estabelecer uma conexão estável entre os dois nós. Os firewalls são absolutamente obrigatórios para acesso comercial à Internet e, como cliente, você deve entender quais portas de comunicação precisam ser abertas nesses firewalls e outros componentes de rede relacionados à segurança de TI.

## Visão geral dos servidores proxy {#proxy-servers}

Uma conexão com a Internet depende do uso de um Servidor Proxy. Um Servidor Proxy é um computador dedicado ou um sistema de software em execução em um computador que atua como um intermediário entre um dispositivo de ponto de extremidade, como um computador, e outro servidor do qual um usuário ou cliente está solicitando um serviço. O servidor proxy pode existir na mesma máquina que um servidor de firewall ou pode existir em um servidor separado, que encaminha solicitações por meio do firewall.

Uma vantagem de um servidor proxy é que seu cache pode atender a todos os usuários. Se um ou mais sites da Internet forem solicitados com frequência, provavelmente estarão no cache do proxy, e isso melhora ainda mais o tempo de resposta do usuário. Um proxy também pode registrar suas interações, que podem ser usadas para solução de problemas.

Quando um servidor proxy recebe uma solicitação de um recurso da Internet (como uma página da Web ou ao se conectar a um Editor de AEM), ele verifica seu cache local de urls chamados anteriormente. Se encontrar a página, ela a retorna ao usuário sem encaminhar a solicitação para a Internet. Se a página não estiver no cache, o servidor proxy (age como um cliente) em nome do usuário e solicita a página do servidor na Internet. Quando o conteúdo é retornado, o servidor proxy o relaciona à solicitação original e a encaminha ao usuário.

## Noções básicas sobre as configurações de rede padrão {#network-setups}

Para implementar uma Configuração de rede, você deve consultar os seguintes cenários com seus pontos fortes e detalhes de implantação.

Este guia destaca quatro tipos diferentes de Configurações de rede em uma organização:

* **[Rede direta da Internet (com fio/sem fio)](/help/using/direct-internet-network.md)**
* **[Rede móvel direta](/help/using/mobile-network.md)**
* **[Rede móvel com roteador de dados móvel e componentes de rede ativos](/help/using/mobile-network-router.md)**
* **[Rede corporativa fechada (com fio/sem fio)](/help/using/enclosed-corporate-network.md)**

A tabela a seguir descreve os diferentes tipos de configurações de rede com vantagens e desvantagens:

| Configuração de rede | Vantagens | Desvantagens |
|--- |--- |--- |
| **Rede direta da Internet (com fio/sem fio)** | Fácil e direto para SetUp<br>A boa opção para instalações de médio ou maior porte<br>A rede dedicada pode ser encapsulada<br>Poucos pontos de falha<br>Escalabilidade relativamente barata<br>Boa escalabilidade | Plano Obrigatório de Dados da Internet |
| **Rede móvel direta** | Fácil de configurar<br>Boa opção para instalações de médio ou maior porte<br>Boa escalabilidade<br>Telas encapsuladas | Conexão obrigatória com a Internet |
| **Rede móvel com roteador de dados móvel e componentes de rede ativos** | Fácil de configurar<br>Boa opção para instalações de médio ou maior porte<br>A rede dedicada pode ser encapsulada<br>Poucos pontos de falha<br>Escalabilidade relativamente barata<br>Boa escalabilidade | Plano Obrigatório de Dados da Internet |
| **Rede corporativa fechada (com fio/sem fio)** | Alta flexibilidade e escalabilidade<br>Altamente seguro devido a diferentes linhas de defesa<br>Encapsulated Networks<br>Fácil de monitorar e manter<br>Confiável | Complicado e caro<br>Recomendado para especialistas de rede ou integradores de sistema |
