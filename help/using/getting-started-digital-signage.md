---
title: Noções básicas de sinalização digital para [!UICONTROL AEM Screens]
description: Aprenda os conceitos básicos de um projeto de sinalização digital.
exl-id: e3913be2-9028-4773-a034-e16924a71e04
source-git-commit: 8dde26d36847fb496aed6d4bf9732233116b5ea6
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 0%

---

# Noções básicas de um projeto de sinalização digital {#basics-digital-signage}

Antes de mergulhar nas práticas recomendadas de implementação do AEM Screens, é importante considerar o projeto como um projeto de sinalização digital, em vez de um desenvolvimento de software tradicional.

Esta seção fornece recomendações sobre os principais elementos essenciais para uma implementação de projeto do AEM Screens.

## Principais elementos em sinalização digital {#key-elements}

Os *Elementos principais* em um projeto de sinalização digital são:

![](/help/assets/Elements-Revised.png)

A definição dos principais elementos é essencial antes da implementação de um projeto de sinalização digital:

1. **Hardware**

   O hardware define quais componentes de hardware são ideais para a implementação do projeto de sinalização digital:
   * O dispositivo tem espaço de armazenamento suficiente para executar todas as variações das experiências off-line?
   * Você permitiu o tipo e o comprimento do cabo de vídeo? O dispositivo também oferece suporte às resoluções desejadas (HD, FullHD, `4K` e assim por diante) e aos codecs de vídeo que estou planejando implantar (h.264, h.265 e assim por diante)?
   * Utilização de fio de cobre físico
   * Tamanho das telas
   * Número de telas
      * Orientação
      * taxa de proporção
      * preferência de resolução

1. **Conectividade**

   A conectividade enfatiza as seguintes questões:
   * Em rede (celular ou wi-fi) ou independente?
      * Você precisa permitir atualizações de conteúdo USB?
      * Você precisa permitir o uso da coleção de dados?

1. **Instalação**

   A instalação inclui:
   * Exibições: paisagem ou retrato
   * Como a tela é montada?
      * Orientação retrato versus orientação paisagem
      * Alojamento completo
      * Placa de cobertura
   * Suporte a dispositivos fixos
   * Pessoal: responsável pela instalação do equipamento e sua conexão à rede
   * A que distância está a fonte de energia da instalação elétrica?
   * A que distância está o painel físico do dispositivo real?

1. **Conteúdo**

   O conteúdo inclui:
   * Uma ou várias regiões?
      * Quantos ativos de mídia estão na tela ao mesmo tempo?
      * Quantas páginas para aplicativos interativos?
      * Definir o loop da interface do usuário
      * Conteúdo orientado por dados?
   * Controle da versão

1. **Interativo**

   Interativo inclui:
   * Tipo de tela de toque preferencial?(resistiva, capacitiva, multitoque)?
      * Pressionar o botão
      * Gesto
   * Acionamento de dados (E/S)?
      * Enviando/Recebendo comandos seriais (fechamento de contato, PLC e assim por diante)
      * Os dados recebidos vão para a tela (RSS) ou acionam o conteúdo
      * RFID/NFC/Bluetooth/iBeacon
      * Serviços externos (meteorologia, tráfego)

1. **Ambiente**

   O ambiente enfatiza:
   * Exibir local?
      * Dentro vs. fora
      * Fora de alcance ou diretamente exposto
   * Requisito de temperatura especial?
   * Prova de vândalo?
   * Alta luz ambiente? Contrastes fortes?

1. **Manutenção**

   Manutenção com ênfase em:

   * Os guias de instalação e de usuário são obrigatórios?
   * Você está configurando (programando) o dispositivo antes do envio?
   * Você deve capturar cada número de série para fins de rastreamento?
   * Existem requisitos de alimentação de reserva (fonte de alimentação ininterrupta)?
   * Como as atualizações do sistema são implantadas? E como os dispositivos são monitorados remotamente? É necessária uma solução de MDM?
