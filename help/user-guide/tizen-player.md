---
title: Tizen Player
description: Esta página descreve a instalação e o funcionamento do Tizen Player.
translation-type: tm+mt
source-git-commit: baefade9fa013bc77ed1f112d0ad2098c992dde5
workflow-type: tm+mt
source-wordcount: '191'
ht-degree: 0%

---


# Implementação do Tizen Player {#tizen-player}

## Instalação do Tizen Player {#installing-tizen-player}

Siga as etapas abaixo para implementar o Tizen Player para AEM Screens:

1. Navegue até a página [**AEM 6.5 Player Downloads**](https://download.macromedia.com/screens/) para baixar o Tizen Player.

1. Instale o arquivo do Tizen player (.zip) do computador local.

1. Obtenha o endereço IP da sua máquina local.

   >[!NOTE]
   >No Terminal da sua máquina, digite os seguintes comandos para:
   >**Comando usar para Mac** `ifconfig`
   >**Windows**, use o comando `ipconfig`

1. No terminal, navegue até o mesmo diretório da pasta do instalador descompactado e verifique se o host local está funcionando.

   >[!NOTE]
   >Para **Mac**, digite `http://localhost` e verifique se o `http` servidor está em execução.

1. O Tizen player baixará o instalador do servidor local.

1. Copie os dois arquivos extraídos `AEMScreensPlayer.wgt` e `sssp_config.xml` para `/Library/WebServer/Documents`.

### Atualizações de configuração no dispositivo SamSung {#config-updates}

Siga as etapas abaixo no dispositivo Samsung para concluir a instalação do AEM Screens player no dispositivo:

1. Clique no botão **Home** do Samsung Remote.
1. Selecione Inicializador **de** URL nas **Configurações**.
1. Selecione **Remoto** no modo Desenvolvedor.
1. Instale o Web App e insira o endereço IP da sua máquina.
O AEM Screens Player deve ser instalado automaticamente no dispositivo Samsung.


