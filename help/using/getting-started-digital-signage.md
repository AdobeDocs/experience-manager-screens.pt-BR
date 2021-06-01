---
title: Noções básicas de sinalização digital para [!UICONTROL AEM Screens]
seo-title: Noções básicas de sinalização digital para [!UICONTROL AEM Screens]
description: O guia descreve as noções básicas de um projeto de sinalização digital
seo-description: O guia descreve as noções básicas de um projeto de sinalização digital
source-git-commit: 4611dd40153ccd09d3a0796093157cd09a8e5b80
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 2%

---


# Noções básicas de um projeto de sinalização digital {#basics-digital-signage}

Antes de mergulhar nas práticas recomendadas de implementação do AEM Screens, é importante pensar no projeto como um projeto de sinalização digital, em vez de um desenvolvimento de software tradicional.

Esta seção fornece recomendações sobre os principais elementos críticos antes da implementação de um projeto do AEM Screens.

## Elementos-chave na sinalização digital {#key-elements}

Os *Elementos-chave* em um projeto de sinalização digital são:

![](/help/assets/Elements-Revised.png)

A definição dos elementos-chave é essencial antes da implementação de um projeto de sinalização digital:

1. **Hardware**

   O Hardware define quais componentes de hardware são ideais para a implementação do projeto de sinalização digital:
   * O dispositivo tem espaço de armazenamento suficiente para executar todas as variações das experiências offline?
   * Permitimos o tipo e a duração do cabo de vídeo? E o dispositivo suporta ambas as resoluções desejadas (HD, FullHD, 4K etc.) e codecs de vídeo que estou planejando implantar (h.264, h.265, etc.)
   * Utilização de fios físicos de cobre
   * Tamanho das telas
   * Número de telas
      * orientation
      * taxa de proporção
      * preferência de resolução

1. **Conectividade**

   A conectividade enfatiza as seguintes questões:
   * Em rede (célula ou wi-fi) ou independente?
      * precisamos permitir atualizações de conteúdo USB?
      * precisamos permitir a coleta de dados de uso?

1. **Instalação**

   A instalação inclui:
   * Exibe: paisagem ou retrato
   * Como a tela será montada?
      * Retrato versus paisagem
      * Alojamento completo
      * Placa de capa
   * Suporte para correção
   * Pessoal: responsável pela instalação do equipamento e pela sua ligação à rede
   * A que distância está a fonte de energia do equipamento?
   * A que distância está o painel físico do dispositivo real?

1. **Conteúdo**

   O conteúdo inclui:
   * Zona única ou várias zonas?
      * Quantos ativos de mídia estão na tela ao mesmo tempo?
      * Quantas páginas para aplicativos interativos?
      * Definir o loop da interface
      * Conteúdo orientado por dados?
   * Controle da versão

1. **Interativo**

   Interativo inclui:
   * Tipo preferido de tela sensível ao toque? (resistente, capacitivo, multitoque)?
      * Pressionar botão
      * Gesto
   * Acionamento de dados (E/S)?
      * Envio/recepção de comandos seriais (fechamento de contato, PLC, etc.)
      * Os dados recebidos vão para a tela (RSS) ou acionam o conteúdo
      * RFID/NFC/Bluetooth/iBeacon
      * Serviços externos (tempo, tráfego)

1. **Autor**

   O ambiente enfatiza:
   * Exibir local?
      * Dentro x Fora
      * Inacessível ou diretamente exposto
   * Requisito especial de temp?
   * Prova de vândalo?
   * Alta luz ambiente? Fortes contrastes?

1. **Manutenção**

   A manutenção enfatiza:

   * São necessários guias de instalação/guias de usuário detalhados?
   * Estamos configurando (programando) o dispositivo antes do envio?
   * Precisamos capturar cada número de série para fins de rastreamento?
   * Existem requisitos de alimentação de reserva (fonte de alimentação ininterrupta)?
   * Como as atualizações do sistema são implantadas? E como os dispositivos são monitorados remotamente? É necessária uma solução MDM?
