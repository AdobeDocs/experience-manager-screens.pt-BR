---
title: Tizen Player
description: Esta página descreve a instalação e o funcionamento do Tizen Player.
translation-type: tm+mt
source-git-commit: b3209d1dcce6defff347f288c704a1e7ea075ecf
workflow-type: tm+mt
source-wordcount: '230'
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
   >Consulte a documentação oficial para saber como ativar o servidor local em sua plataforma.

1. No terminal, navegue até o mesmo diretório da pasta do instalador descompactado e verifique se o host local está funcionando.

1. O Tizen player baixará o instalador do servidor local.

1. Copie os dois arquivos extraídos, como `AEMScreensPlayer.wgt` e `sssp_config.xml`, para o diretório raiz do servidor local.

### Configurando atualizações no dispositivo Samsung {#config-updates}

Siga as etapas abaixo no dispositivo Samsung para concluir a instalação do AEM Screens player no dispositivo:

1. Vá para seu dispositivo Samsung.

1. Clique no botão **Início** usando o controle remoto do dispositivo e selecione **Configurações do Iniciador de URL**.

1. Insira o endereço IP do servidor host local.

1. Selecione **Remote** no **Developer Mode**.

1. Clique no botão **Início** no controle remoto do dispositivo e selecione **Iniciador de URL**.

1. O AEM Screens Player agora deve instalar e iniciar automaticamente em seu dispositivo Samsung.



