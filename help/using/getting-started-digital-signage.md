---
title: Noções básicas de placas digitais para [!UICONTROL AEM Screens]
seo-title: Noções básicas de placas digitais para [!UICONTROL AEM Screens]
description: O guia descreve as noções básicas de um projeto de sinalização digital
seo-description: O guia descreve as noções básicas de um projeto de sinalização digital
translation-type: tm+mt
source-git-commit: 54c5a2f2f3f755e4da4028d54042f4bd8f2df369
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 2%

---


# Noções básicas de um projeto de sinalização digital {#basics-digital-signage}

Antes de mergulhar nas práticas recomendadas de implementação da AEM Screens, é importante pensar no projeto como um projeto de sinalização digital, em vez de um desenvolvimento de software tradicional.

Esta seção fornece recomendações sobre os principais elementos essenciais antes da implementação de um projeto da AEM Screens.

## Elementos chave em placas digitais {#key-elements}

Os *Elementos-chave* em um projeto de assinatura digital são:

![](/help/assets/Elements-Revised.png)

A definição dos elementos-chave é essencial antes da implementação de um projeto de sinalização digital:

1. **Hardware**

   O hardware define quais componentes de hardware são ideais para a implementação do projeto de sinalização digital:
   * O dispositivo tem espaço suficiente no armazenamento para executar todas as variações das experiências off-line?
   * Nós permitimos o tipo e a duração do cabo de vídeo? E o dispositivo suporta ambas as resoluções desejadas (HD, FullHD, 4K etc.) e codecs de vídeo que estou planejando implantar (h.264, h.265, etc.)
   * Utilização de fios físicos de cobre
   * Tamanho das telas
   * Número de telas
      * orientation
      * taxa de proporção
      * preferência de resolução

1. **Conectividade**

   A conectividade enfatiza as seguintes questões:
   * Em rede (celular ou Wi-Fi) ou independente?
      * precisamos permitir atualizações de conteúdo USB?
      * precisamos permitir a coleta de dados de uso?

1. **Instalação**

   A instalação inclui:
   * Exibe: paisagem ou retrato
   * Como a tela será montada?
      * Retrato vs. paisagem
      * Habitação total
      * Placa de cobertura
   * Suporte para correções
   * Pessoal: responsável pela instalação e conexão do equipamento à rede
   * Qual é a distância da fonte de energia do equipamento?
   * Qual é a distância entre o painel físico e o dispositivo real?

1. **Conteúdo**

   O conteúdo inclui:
   * Zona única ou multizona?
      * Quantos ativos de mídia estão na tela ao mesmo tempo?
      * Quantas páginas para aplicativos interativos?
      * Definir o Loop da UI
      * Conteúdo direcionado para dados?
   * Controle da versão

1. **Interativo**

   Interativo inclui:
   * Tipo preferido de tela sensível ao toque?(resistente, capacitivo, multitoque)?
      * Botão pressionar
      * Gesto
   * Disparo de dados (E/S)?
      * Comandos seriais de envio/recebimento (encerramento de contato, PLC etc.)
      * Os dados recebidos são exibidos na tela (RSS) ou acionam o conteúdo
      * RFID/NFC/Bluetooth/iBeacon
      * Serviços externos (meteorologia, tráfego)

1. **Autor**

   O ambiente enfatiza:
   * Exibir local?
      * Dentro vs. Fora
      * Fora do alcance ou diretamente exposta
   * Requisito de tempo especial?
   * Prova de vândalo?
   * Alta luz ambiente? Fortes contrastes?

1. **Manutenção**

   A manutenção enfatiza:

   * Guias de instalação/guias de usuário detalhados são necessários?
   * Estamos configurando (programando) o dispositivo antes do envio?
   * Precisamos capturar cada número de série para fins de rastreamento?
   * Há algum requisito de alimentação de reserva (fonte de alimentação ininterrupta)?
   * Como as atualizações do sistema são implantadas? E como os dispositivos são monitorados remotamente? Uma solução MDM é necessária?
