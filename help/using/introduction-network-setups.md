---
title: Introdução às configurações de rede padrão
seo-title: Introdução às configurações de rede padrão
description: A página descreve Configurações de rede padrão
seo-description: A página descreve Configurações de rede padrão
translation-type: tm+mt
source-git-commit: 6d6637d5222e861fa9a83f555baf0699f56f150a
workflow-type: tm+mt
source-wordcount: '459'
ht-degree: 0%

---


# Introdução às configurações de rede padrão {#intro-standard-networks}

Uma Configuração de rede pode ter várias estruturas. Esta seção fornece uma visão geral das estruturas de rede implantadas em um ambiente. Há configurações diferentes que às vezes são implementadas do zero.

Esta seção destaca uma introdução aos servidores proxy seguida pelas diferentes estruturas de rede configuradas em diferentes organizações.

>[!NOTE]
>**Requisitos de rede para AEM Screens **>Os AEM Screens se comunicam diretamente com o Cloud Service do AEM, portanto, é necessário estabelecer uma conexão estável entre esses dois nós. Os firewalls são absolutamente obrigatórios para o acesso comercial à Internet e o cliente precisa saber quais portas de comunicação precisam ser abertas em Firewalls e outros componentes de rede relacionados à segurança da TI que estejam sob o controle do cliente.

## Servidores proxy {#proxy-servers}

Um servidor proxy é um computador dedicado ou um sistema de software em execução em um computador que atua como intermediário entre um dispositivo de ponto de extremidade, como um computador, e outro servidor do qual um usuário ou cliente solicita um serviço. O servidor proxy pode existir na mesma máquina que um servidor de firewall ou pode estar em um servidor separado, que encaminha solicitações por meio do firewall.

Uma vantagem de um servidor proxy é que seu cache pode atender a todos os usuários. Se um ou mais sites da Internet forem solicitados com frequência, provavelmente estarão no cache do proxy, o que melhorará o tempo de resposta do usuário. Um proxy também pode registrar suas interações, o que pode ser útil para a solução de problemas.

## Como entender as configurações de rede {#network-setups}

Para implementar uma Configuração de rede, consulte os seguintes cenários com pontos fortes e detalhes de implantação.

Há três tipos principais de configurações de rede:

1. [Acesso direto à Internet](/help/using/direct-internet-access.md)
1. [Rede móvel direta](/help/using/mobile-network-setup.md)
1. [Rede móvel com roteador de dados móvel e componentes de rede ativos](/help/using/mobile-network-setup-router.md)
1. [Rede corporativa fechada](/help/using/enclosed-corporate-network.md)

A tabela a seguir descreve os diferentes tipos de configurações de rede com vantagens e desvantagens:

<table>
 <tbody>
  <tr>
   <td><strong>Configuração de rede</strong></td>
   <td><strong>Vantagens</strong></td>
   <td><strong>Desvantagens</strong></td>
  </tr>
  <tr>
   <td><strong>Acesso direto à Internet</strong></td>
   <td>Fácil e direto para configurar<br>Boa escolha para instalações de médio ou maior porteRede<br>dedicada pode ser encapsulada<br>Poucos pontos de falha<br>Escalabilidade relativamente barata<br>Boa</td>
   <td>Necessário um plano de dados da Internet</td>
  </tr>
    <tr>
   <td><strong>Rede móvel direta</strong></td>
   <td>Fácil e direto para configurar<br>Boa escolha para instalações de médio ou maior porte<br>Boa escalabilidadeTelas<br>encapsuladas
</td>
   <td>Conexão com a Internet apropriada obrigatória</td>
  </tr>
    <tr>
<tr>
   <td><strong>Rede móvel com roteador de dados móvel e componentes de rede ativos</strong></td>
   <td>Fácil e direto para configurar<br>Boa escolha para instalações de médio ou grande porteA Rede<br>dedicada pode ser encapsulada<br>Poucos pontos de falha<br>Relativamente barata<br>Boa escalabilidade</br></td>
   <td>Necessário um plano de dados da Internet</td>
  </tr>
    <tr>

<td><strong>Rede corporativa fechada</strong></td>
   <td>Alta flexibilidade e escalabilidade<br>Altamente seguras devido a diferentes linhas de redes<br>encapsuladas de defesa<br>fáceis de monitorar e manter<br>confiáveis</td>
   <td>Recomendados especialistas em<br>rede complicados e caros ou integradores de sistema</td>
  </tr>
  </tr>
 </tbody>
</table>


