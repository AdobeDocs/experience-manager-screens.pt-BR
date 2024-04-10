---
title: Gerenciando o tráfego de rede
description: A página descreve Configurações de rede padrão e como gerenciar o tráfego de rede.
exl-id: b6d8f4a3-fca2-4556-9455-b9e27b138154
source-git-commit: 67560ae17646424985032c81f33c937c6eeb5957
workflow-type: tm+mt
source-wordcount: '556'
ht-degree: 0%

---

# Gerenciando o tráfego de rede {#managing-network-traffic}

Uma Configuração de rede pode ter várias estruturas. Esta seção descreve as configurações de rede mais comuns e as abordagens generalizadas seguidas em uma organização.

Este guia destaca uma introdução aos servidores proxy, seguida pelas várias estruturas de rede configuradas em diferentes organizações.

>[!NOTE]
>**Requisitos de rede da AEM Screens**
>O AEM Screens se comunica diretamente com o AEM as a Cloud Service, portanto, é necessário estabelecer uma conexão estável entre os dois nós. Os firewalls são absolutamente obrigatórios para o acesso comercial à Internet e, como cliente, você deve entender quais portas de comunicação precisam ser abertas nesses firewalls e outros componentes de rede relacionados à Segurança da TI.

## Visão geral para servidores proxy {#proxy-servers}

Uma conexão com a Internet depende do uso de um Servidor Proxy. Um Servidor Proxy é um computador dedicado ou um sistema de software em execução em um computador que atua como um intermediário entre um dispositivo de ponto de extremidade, como um computador, e outro servidor do qual um usuário ou cliente está solicitando um serviço. O servidor proxy pode existir na mesma máquina que um servidor de firewall ou em um servidor separado, que encaminha solicitações por meio do firewall.

Uma vantagem de um servidor proxy é que seu cache pode servir a todos os usuários. Se um ou mais sites da Internet forem solicitados com frequência, provavelmente estarão no cache do proxy, o que melhora ainda mais o tempo de resposta do usuário. Um proxy também pode registrar suas interações, que podem ser usadas para solucionar problemas.

Quando um servidor proxy recebe uma solicitação de um recurso da Internet (como uma página da Web ou ao se conectar a um AEM Publisher), ele verifica seu cache local de urls chamados anteriormente. Se encontrar a página, ela a retornará ao usuário sem encaminhar a solicitação à Internet. Se a página não estiver no cache, o servidor proxy (age como um cliente) em nome do usuário e solicita a página do servidor na Internet. Quando o conteúdo é retornado, o servidor proxy o relaciona à solicitação original e a encaminha ao usuário.

## Noções básicas sobre as configurações de rede padrão {#network-setups}

Para implementar uma Configuração de rede, consulte os seguintes cenários com seus pontos fortes e detalhes de implantação.

Este guia destaca quatro tipos diferentes de configurações de rede em uma organização:

* **[Rede de Internet Direta (Com Fio/Sem Fio)](/help/using/direct-internet-network.md)**
* **[Rede móvel direta](/help/using/mobile-network.md)**
* **[Rede Móvel com Roteador de Dados Móvel e Componentes de Rede Ativos](/help/using/mobile-network-router.md)**
* **[Rede corporativa fechada (com fio/wireless)](/help/using/enclosed-corporate-network.md)**

A tabela a seguir descreve os diferentes tipos de configurações de rede com vantagens e desvantagens:

| Configuração de rede | Vantagens | Desvantagens |
|--- |--- |--- |
| **Rede de Internet Direta (Com Fio/Sem Fio)** | Fácil e direto para a configuração<br>Boa opção para instalações de médio porte ou maiores<br>A rede dedicada pode ser encapsulada<br>Alguns pontos de falha<br>Relativamente barato<br>Boa escalabilidade | Plano de dados de Internet obrigatório |
| **Rede móvel direta** | Fácil de configurar<br>Boa escolha para instalações de médio ou grande porte<br>Boa escalabilidade<br>Telas encapsuladas | Conexão obrigatória com a Internet |
| **Rede Móvel com Roteador de Dados Móvel e Componentes de Rede Ativos** | Fácil de configurar<br>Boa escolha para instalações de médio ou grande porte<br>A rede dedicada pode ser encapsulada<br>Alguns pontos de falha<br>Relativamente barato<br>Boa escalabilidade | Plano de dados de Internet obrigatório |
| **Rede corporativa fechada (com fio/wireless)** | Alta flexibilidade e escalabilidade<br>Altamente seguro devido a diferentes linhas de defesa<br>Redes encapsuladas<br>Fácil de monitorar e manter<br>Confiável | Complicado e caro<br>Recomendado para especialistas em rede ou integradores de sistemas |
