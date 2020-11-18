---
title: Tizen Player
description: Esta página descreve a instalação e o funcionamento do Tizen Player.
translation-type: tm+mt
source-git-commit: 835da341fcee8e4abb3375c43a0a130d3f79d859
workflow-type: tm+mt
source-wordcount: '223'
ht-degree: 0%

---


# Implementação do Tizen Player {#tizen-player}

## Instalação do Tizen Player {#installing-tizen-player}

Siga as etapas abaixo para implementar o Tizen Player para AEM Screens:

1. Navegue até a página [**AEM 6.5 Player Downloads**](https://download.macromedia.com/screens/) para baixar o Tizen Player.

1. Instale o arquivo do Tizen player (.zip) do computador local.

## Configuração do servidor local e extração de arquivos Zip {#setting-local-server}

Siga as etapas abaixo para configurar o servidor local e copiar os arquivos extraídos:

1. Obtenha o endereço IP da sua máquina local.

   >[!NOTE]
   >Você pode obter o endereço IP do terminal de sua máquina usando os seguintes comandos:
   >* **Mac**: `ifconfig`
   >* **Windows**: `ipconfig`


1. No terminal, navegue até o mesmo diretório da pasta do instalador descompactado e verifique se o host local está funcionando.

   >[!NOTE]
   >Para **Mac**, digite `http://localhost` e verifique se o `http` servidor está em execução.

1. O Tizen player baixará o instalador do servidor local.

1. Copie os dois arquivos extraídos `AEMScreensPlayer.wgt` e `sssp_config.xml` para `/Library/WebServer/Documents`.

### Configurando atualizações no dispositivo Samsung {#config-updates}

Siga as etapas abaixo no dispositivo Samsung para concluir a instalação do AEM Screens player no dispositivo:

1. Vá para seu dispositivo Samsung e aponte para seu servidor host local.
1. Selecione Configurações **do Iniciador de** URL nas **Configurações** e insira o endereço IP do servidor host local.
1. Instale o Web App.
1. Selecione **Remoto** no Modo **de** desenvolvedor.
1. O AEM Screens Player agora deve ser instalado automaticamente em seu dispositivo Samsung.


