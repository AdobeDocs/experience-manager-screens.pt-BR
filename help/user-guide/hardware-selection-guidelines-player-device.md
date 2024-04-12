---
title: Diretrizes de seleção de hardware para dispositivos reprodutores
description: Saiba mais sobre as diretrizes de seleção de hardware para dispositivos AEM Screens player.
source-git-commit: ba5327077e4a2d30cc7b77f02123da5a240c67ae
workflow-type: tm+mt
source-wordcount: '227'
ht-degree: 3%

---


# Diretrizes de seleção de hardware para o dispositivo player {#hardware-selection}

A seção a seguir fornece as diretrizes de seleção de hardware para um reprodutor do AEM Screens.

## Considerações importantes {#important-considerations}

* Sempre origem ***Comercial*** ou ***Industrial*** Os componentes da nota para PC player e painel de exibição ou projetor.

* Sempre interaja com fornecedores que atendem ao mercado de sinalização digital.
* Sempre considere fatores ambientais como temperatura ambiente e umidade relativa.
* Sempre analise os requisitos de energia e o condicionamento de energia.
* Analise cuidadosamente as necessidades de desempenho e as portas de E/S necessárias para o aplicativo.

## Configurações de hardware {#hardware-configurations}

A tabela a seguir resume as configurações de hardware com casos de uso típicos de um projeto AEM Screens:

<table>
 <tbody>
  <tr>
   <tr>
   <td><strong>Configuração do reprodutor</strong></td>
   <td><strong>Processador</strong></td>
   <td><strong>Memória</strong></td>
   <td><strong>SSD de armazenamento</strong></td>
   <td><strong>GPU</strong></td>
   <td><strong>Exibir</strong></td>
   <td><strong>E/S</strong></td>
   <td><strong>Casos de uso típicos</strong></td>
  </tr>
  <tr>
   <td>Básico</td>
   <td>Processador Intel® Atom Dual Core, i3 ou quad core básico</td>
   <td><p>4 GB de memória</p> <p>2 MB de cache</p> </td>
   <td><p>*ChromeOS 32 GB</p> <p>*Windows 128 GB</p> </td>
   <td>OnBoard</td>
   <td>1920 x 1080</td>
   <td>DVI<br /> Ethernet / sem fio,<br /> 2xUSB</td>
   <td>
    <ul>
     <li>Looping de tela cheia padrão<br /> </li>
     <li>Divisão de dia</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Padrão</td>
   <td>Processador Intel® Core™ i5 de 4 núcleos</td>
   <td><p>8 GB de memória</p> <p>4 MB de cache</p> </td>
   <td>128 GB</td>
   <td>OnBoard</td>
   <td>3840x2160 (<code>4K</code>)</td>
   <td>DVI, HDMI<br /> Ethernet / sem fio,<br /> 2xUSB</td>
   <td>
    <ul>
     <li>Conteúdo dinâmico de origem única</li>
     <li>Interativo simples</li>
     <li>1-3 Layouts de zona</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Avançado </td>
   <td>Quad Core com hyperthreading, processador Intel® Core™ i7</td>
   <td><p>16 GB de memória</p> <p>8 MB de cache</p> </td>
   <td>256 GB</td>
   <td>GPU gráfica dedicada</td>
   <td>3840x2160 (<code>4K</code>)</td>
   <td>DVI, HDMI<br /> Ethernet / sem fio,<br /> 4xUSB</td>
   <td>
    <ul>
     <li>4 ou mais zonas de conteúdo, reprodução de vídeo simultânea</li>
     <li>Interativo de várias páginas</li>
     <li>Acionadores de dados de várias origens</li>
    </ul> </td>
  </tr>
 </tbody>
</table>
