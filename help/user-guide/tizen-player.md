---
title: Tizen Player
description: Esta página descreve a instalação e o funcionamento do Tizen Player.
translation-type: tm+mt
source-git-commit: dc2fedaa5726e1013e1b51f429ba19e4a709de28
workflow-type: tm+mt
source-wordcount: '675'
ht-degree: 0%

---


# Implementação do Tizen Player {#tizen-player}

## Instalação do Tizen Player {#installing-tizen-player}

Siga as etapas abaixo para implementar o Tizen Player para AEM Screens:

1. Navegue até a página [AEM 6.5 Player Downloads](https://download.macromedia.com/screens/) para baixar o Tizen Player.

1. Instale o arquivo Tizen player *(.zip)* do computador local.

## Configuração do servidor local e extração de arquivos Zip {#setting-local-server}

Siga as etapas abaixo para configurar o servidor local e copiar os arquivos extraídos:

1. Obtenha o endereço IP da sua máquina local.
   >[!NOTE]
   >Consulte a documentação oficial para saber como ativar o servidor local em sua plataforma.

1. No terminal, navegue até o mesmo diretório da pasta do instalador descompactado e verifique se o host local está funcionando.

1. O Tizen player baixará o instalador do servidor local.

1. Copie os dois arquivos extraídos, como `AEMScreensPlayer.wgt` e `sssp_config.xml`, para o diretório raiz do servidor Web Apache local.

   >[!NOTE]
   >O `AEMScreensPlayer.wgt`é o aplicativo Tizen player real e `sssp_config.xml` contém informações sobre esse mapa que ajudam a instalá-lo no dispositivo Tizen.

### Configurando atualizações no dispositivo Samsung {#config-updates}

Siga as etapas abaixo no dispositivo Samsung para concluir a instalação do AEM Screens player no dispositivo:

1. Navegue até seu dispositivo Samsung e ligue-o.

1. Clique no botão **MENU** do controle remoto do dispositivo e role para baixo até **System** da barra de navegação esquerda.

1. Role para baixo e selecione a opção **Reproduzir por meio do URL Launcher**.
   ![imagem](/help/user-guide/assets/tizen/url-launcher.png)

1. Pressione o botão **Home** do seu controle remoto.

1. Insira o endereço IP do servidor host local.

1. Selecione **Remote** no **Developer Mode**.

1. Clique no botão **Início** no controle remoto do dispositivo e selecione **Iniciador de URL**.

1. O AEM Screens Player agora deve instalar e iniciar automaticamente em seu dispositivo Samsung.

## Provisionamento em massa do Tizen Player {#bulk-provisioning-tizen-player}

>[!NOTE]
>Pode ser um esforço tedioso inserir manualmente o endereço do servidor AEM na interface do usuário do administrador de cada dispositivo para um grande número de dispositivos. É recomendável usar a solução Samsung Remote Management (RMS) para implantar e gerenciar a solução. Consulte [Registrando o dispositivo Tizen no serviço de gerenciamento remoto Samsung (RMS)](#enroll-tizen-device-rm) para obter mais detalhes.

Siga as etapas abaixo para fornecer o aplicativo em massa para apontar para a instância do autor AEM quando ele for iniciado:

1. Baixe e instale o [Tizen Studio](https://developer.tizen.org/development/tizen-studio/download).
1. Abra o arquivo `wgt` usando o estúdio Tizen.
1. Abra o arquivo `firmware-platform.js` e procure `DEFAULT_PREFERENCES` e altere o URL do servidor para o URL do autor AEM e salve.
1. Crie o novo arquivo `wgt`.

   >[!NOTE]
   >Talvez seja necessário criar ou configurar um certificado de assinatura.

1. Implante este novo arquivo `wgt` RMS e quando o player o iniciar, ele deverá apontar automaticamente para o servidor para que você não precise inseri-lo manualmente em todos os dispositivos.

### Registrando o dispositivo Tizen no serviço de gerenciamento remoto Samsung (RMS) {#enroll-tizen-device-rms}

Siga as etapas abaixo para inscrever o Tizen Device no Samsung Remote Management Service (RMS) e configurar remotamente o URL Launcher:

>[!NOTE]
>Verifique as configurações de rede e o monitor.

1. Navegue até **Menu** -> **Rede** -> **Definições de Rede do Servidor** e prima **Enter**.

   >[!NOTE]
   >Verifique se a tela está configurada para Reproduzir por meio do URL Launcher.

1. Navegue até Server Address (Endereço do servidor) e digite o acesso ao URL MagicInfo e pressione Done (Concluído).

1. Configure TLS para usar ou Não usar, dependendo do caso
   1. Vá para a porta e selecione o número da porta no servidor.
   1. Pressione Salvar quando as opções estiverem prontas.

1. Navegue até a guia Dispositivo depois de conectado ao MIS
   1. Procure o dispositivo que você acabou de configurar, observando o endereço IP e/ou seu endereço Mac.
   1. Depois que um dispositivo for encontrado, clique na caixa de seleção e selecione Aprovar.

1. Depois de clicar no botão Aprovado, o seguinte pop-up será exibido
   1. Preencha as informações necessárias
   1. selecionar um grupo de dispositivos
   1. Clique no botão OK para concluir o processo de aprovação.

1. Depois que o dispositivo é aprovado, ele deve aparecer como a seguir na Lista do dispositivo.
   1. Clique no botão Information (Informações) localizado na caixa &quot;i&quot; do dispositivo

1. O menu Device Information Pop-up (Informações do dispositivo) será exibido como segue e clique no botão Edit (Editar).

1. As opções Editar dispositivo serão exibidas conforme a seguir e selecione a guia Configuração.

1. Localize a Seção Iniciador de URL e insira o URL que hospeda o wgt e `SSSP config file` para instalar um aplicativo SSSP.




