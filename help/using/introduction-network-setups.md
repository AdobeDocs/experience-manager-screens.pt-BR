---
title: Introdução às configurações de rede padrão
description: A página descreve Configurações de rede padrão
translation-type: tm+mt
source-git-commit: 8e62b3fc4ce324e02aaec6fca9df79b1aaf94d72
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 0%

---


# Gerenciamento do tráfego de rede {#managing-network-traffic}

Uma Configuração de rede pode ter várias estruturas. Esta seção descreve as configurações de rede mais comuns dentro da configuração de rede de uma organização.

Este guia destaca uma introdução aos servidores proxy seguido pelas várias estruturas de rede configuradas em diferentes organizações.

>[!NOTE]
>**Requisitos de rede para AEM Screens **>Os AEM Screens se comunicam diretamente com o AEM como um Cloud Service, portanto, é necessário estabelecer uma conexão estável entre os dois nós. Os firewalls são absolutamente obrigatórios para acesso comercial à Internet e, como cliente, você deve entender quais portas de comunicação precisam ser abertas em firewalls e outros componentes de rede relacionados à segurança da TI.

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

<table>
 <tbody>
  <tr>
   <td><strong>Configuração de rede</strong></td>
   <td><strong>Vantagens</strong></td>
   <td><strong>Desvantagens</strong></td>
  </tr>
  <tr>
   <td><strong>Rede Internet direta (com fio/sem fio)</strong></td>
   <td>Fácil e direto para configurar<br>Boa escolha para instalações de médio ou maior porteRede<br>dedicada pode ser Encapsulada<br>Poucos pontos de falha<br>Escalabilidade relativamente barata<br>boa</td>
   <td>Plano obrigatório de dados da Internet </td>
  </tr>
    <tr>
   <td><strong>Rede móvel direta</strong></td>
   <td>Fácil de configurar<br>boa escolha para instalações de médio ou maior porte<br>Telas<br>encapsuladas de dimensionamentoBom
</td>
   <td>Conexão obrigatória com a Internet</td>
  </tr>
    <tr>
<tr>
   <td><strong>Rede móvel com roteador de dados móvel e componentes de rede ativos</strong></td>
   <td>A fácil configuração<br>boa opção para instalações de médio ou maior porteRede<br>dedicada pode ser encapsulada<br>em poucos pontos de falha<br>relativamente barata<br>Boa escalabilidade</br></td>
   <td>Plano obrigatório de dados da Internet</td>
  </tr>
    <tr>

<td><strong>Rede corporativa fechada (com fio/sem fio)</strong></td>
   <td>Alta flexibilidade e escalabilidade<br>Altamente seguras devido a diferentes linhas de redes<br>encapsuladas de defesa<br>fáceis de monitorar e manter<br>confiáveis</td>
   <td>Complicado e caro<br>recomendado para especialistas de rede ou integradores de sistema</td>
  </tr>
  </tr>
 </tbody>
</table>


