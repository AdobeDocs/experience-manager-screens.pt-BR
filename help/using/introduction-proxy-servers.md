---
title: Entender servidores proxy
seo-title: Entender servidores proxy
description: A página descreve os servidores proxy
seo-description: A página descreve os servidores proxy
translation-type: tm+mt
source-git-commit: 6a0460fd6c62fd6408d3c7665b626818929351d9
workflow-type: tm+mt
source-wordcount: '347'
ht-degree: 0%

---


# Introdução às configurações de rede padrão {#intro-standard-networks}

Uma Configuração de rede pode ter várias estruturas. Esta seção fornece uma visão geral das estruturas de rede implantadas em um ambiente. Há configurações diferentes que às vezes são implementadas do zero.

Esta seção destaca uma introdução aos servidores proxy seguida pelas diferentes estruturas de rede configuradas em diferentes organizações.

## Servidores proxy {#proxy-servers}

Um servidor proxy é um computador dedicado ou um sistema de software em execução em um computador que atua como intermediário entre um dispositivo de ponto de extremidade, como um computador, e outro servidor do qual um usuário ou cliente solicita um serviço. O servidor proxy pode existir na mesma máquina que um servidor de firewall ou pode estar em um servidor separado, que encaminha solicitações por meio do firewall.

Uma vantagem de um servidor proxy é que seu cache pode atender a todos os usuários. Se um ou mais sites da Internet forem solicitados com frequência, provavelmente estarão no cache do proxy, o que melhorará o tempo de resposta do usuário. Um proxy também pode registrar suas interações, o que pode ser útil para a solução de problemas.

## Como entender as configurações de rede {#network-setups}

Para implementar uma Configuração de rede, consulte os seguintes cenários com prós e contras.

Há três tipos principais de configurações de rede:

1. Configuração do Internet Access
1. Configuração de rede móvel
1. Configuração de rede corporativa fechada

A tabela a seguir descreve os diferentes tipos de configurações de rede com vantagens e desvantagens:

<table>
 <tbody>
  <tr>
   <td><strong>Configuração de rede</strong></td>
   <td><strong>Vantagens</strong></td>
   <td><strong>Desvantagens</strong></td>
  </tr>
  <tr>
   <td><strong>Configuração do Internet Access</strong></td>
   <td>Fácil e direto para configurar<br>Boa escolha para instalações de médio ou maior porteRede<br>dedicada pode ser encapsulada<br>Poucos pontos de falha<br>Escalabilidade relativamente barata<br>Boa</td>
   <td>Necessário um plano de dados da Internet</td>
  </tr>
    <tr>
   <td><strong>Configuração de rede móvel</strong></td>
   <td>Fácil e direto para configurar<br>Boa escolha para instalações de médio ou grande porteA Rede<br>dedicada pode ser encapsulada<br>Poucos pontos de falha<br>Relativamente barata<br>Boa escalabilidade</br></td>
   <td>Conexão com a Internet apropriada obrigatória</td>
  </tr>
    <tr>
   <td><strong>Rede corporativa fechada</strong></td>
   <td>Alta flexibilidade e escalabilidade<br>Altamente seguras devido a diferentes linhas de redes<br>encapsuladas de defesa<br>fáceis de monitorar e manter<br>confiáveis</td>
   <td>Recomendados especialistas em<br>rede complicados e caros ou integradores de sistema</td>
  </tr>
  </tr>
 </tbody>
</table>


