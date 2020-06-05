---
title: Diretrizes de seleção de hardware para dispositivos de player
description: Diretrizes de seleção de hardware para dispositivos de player
translation-type: tm+mt
source-git-commit: 7fdd812c71c995424a27db18264ef2db420d5717
workflow-type: tm+mt
source-wordcount: '220'
ht-degree: 2%

---


# Diretrizes de seleção de hardware para o dispositivo do player {#hardware-selection}

A seção a seguir fornece as diretrizes de seleção de hardware para um player do AEM Screens.

## Considerações importantes {#important-considerations}

* Projetor ou painel de vídeo para o player do PC e para o ***monitor*** ou para o projetor, sempre obtenha componentes do nível comercial ou ***industrial*** .

* Sempre envolva-se com fornecedores que servem o mercado de placas digitais.
* Considere sempre fatores ambientais como temperatura ambiente e umidade relativa.
* Verifique sempre os requisitos de energia e o condicionamento de energia.
* Analise cuidadosamente as necessidades de desempenho e as portas de E/S necessárias para o aplicativo.

## Configurações de hardware {#hardware-configurations}

A tabela a seguir resume as configurações de hardware com casos de uso típicos de um projeto do AEM Screens:

<table>
 <tbody>
  <tr>
   <tr>
   <td><strong>Configuração do player</strong></td>
   <td><strong>Processador</strong></td>
   <td><strong>Memória</strong></td>
   <td><strong>Armazenamento SSD</strong></td>
   <td><strong>GPU</strong></td>
   <td><strong>Exibir</strong></td>
   <td><strong>E/S</strong></td>
   <td><strong>Casos de uso típicos</strong></td>
  </tr>
  <tr>
   <td>Básico</td>
   <td>Processador Intel® Atom de núcleo duplo, i3 ou núcleo quádruplo básico</td>
   <td><p>4 GB de memória</p> <p>2 MB de cache</p> </td>
   <td><p>・ChromeOS 32 GB</p> <p>・ Windows 128GB</p> </td>
   <td>OnBoard</td>
   <td>1920x1080</td>
   <td>DVI,<br /> Ethernet / sem fio,<br /> 2xUSB</td>
   <td>
    <ul>
     <li>Looping padrão em tela cheia<br /> </li>
     <li>Partilha de Dia</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Padrão</td>
   <td>Quad Core, processador Intel® Core i5</td>
   <td><p>8 GB de memória</p> <p>4 MB de cache</p> </td>
   <td>128 GBB</td>
   <td>OnBoard</td>
   <td>3840 x 2160 (4 K)</td>
   <td>DVI, HDMI<br /> Ethernet / sem fio,<br /> 2xUSB</td>
   <td>
    <ul>
     <li>Conteúdo dinâmico de origem única</li>
     <li>Interativo simples</li>
     <li>1-3 Layouts de zona</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Avançado    </td>
   <td>Quad Core com hyperthreading, processador Intel® Core i7</td>
   <td><p>16 GB de memória</p> <p>8 MB de cache</p> </td>
   <td>256 GB</td>
   <td>GPU de gráficos dedicados</td>
   <td>3840 x 2160 (4 K)</td>
   <td>DVI, HDMI<br /> Ethernet / Wireless,<br /> 4xUSB</td>
   <td>
    <ul>
     <li>4 ou mais zonas de conteúdo, reprodução de vídeo simultâneo</li>
     <li>Multipáginas interativas</li>
     <li>Acionadores de dados de várias fontes</li>
    </ul> </td>
  </tr>
 </tbody>
</table>
