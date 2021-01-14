---
title: Tizen Player
description: Esta página descreve a instalação e o funcionamento do Tizen Player.
translation-type: tm+mt
source-git-commit: 092be09ec9477c9ff7561347d8f05641a90a9b40
workflow-type: tm+mt
source-wordcount: '899'
ht-degree: 0%

---


# Implementação do Tizen Player {#tizen-player}

## Instalação do Tizen Player {#installing-tizen-player}

Siga as etapas abaixo para implementar o Tizen Player para AEM Screens:

1. Navegue até a página [AEM 6.5 Player Downloads](https://download.macromedia.com/screens/) para baixar o Tizen Player.

1. Instale o arquivo Tizen player *(.zip)* do computador local.

## Isentando os agentes de usuário com o problema de cookie do Samesite {#exempting-user-agents}

>[!IMPORTANT]
>**Esta seção se aplica ao Adobe Experience Manager (AEM) 6.5.5 a AEM 6.5.7**
>Há alguns mecanismos de navegador que são incompatíveis com o atributo *SameSite=None* usado no token de logon emitido pelo AEM 6.5 para AEM 6.7. Na maioria dos casos, o problema pode ser resolvido atualizando o navegador para a versão mais recente disponível. Em alguns casos, essas atualizações podem não ser possíveis, como com telas inteligentes, caixas de configuração ou outros dispositivos com mecanismos de navegação incorporados.

Siga as etapas abaixo para isentar esses clientes incompatíveis ao usar *SameSite=None*:

1. Atualize para Adobe Experience Manager (AEM) Service Pack 6.5.8.

1. Navegue até `/system/console/bundles` no AEM e clique no botão `install/update`.

1. Instale o arquivo jar `crx-auth-token`. Talvez seja necessário desligar e reiniciar o AEM após a instalação deste jar, pois ele está relacionado à autenticação.

1. Depois que AEM reiniciar, vá para `/system/console/configMgr` e procure **Adobe Granite Token Authentication Handler**. Defina o valor para o valor **SameSite** como **None**.

1. Você deve ver uma nova opção *Agentes de usuário que serão isentos do mesmo atributo*. Preencha isso com um regex correspondente aos agentes do usuário que são (são) incompatíveis com o atributo *SameSite=None*.
   >[!NOTE]
   >Consulte [SameSite=None: Clientes incompatíveis conhecidos](https://www.chromium.org/updates/same-site/incompatible-clients) para obter mais detalhes. Para o Tizen player, use o regex: `(.*)Tizen (4|5)(.*)`.

1. Registre o Tizen player em sua instância AEM 6.5.5 e superior e ele deve registrar e mostrar o conteúdo normalmente.


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
   ![imagem](/help/user-guide/assets/tizen/rms-2.png)

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

Siga as etapas abaixo para inscrever o dispositivo Tizen no Samsung Remote Management Service (RMS) e configurar remotamente o URL Launcher:

>[!NOTE]
>Verifique as configurações de rede e o monitor.

1. Navegue até **Menu** -> **Rede** -> **Definições de Rede do Servidor** e prima **Enter**.

   >[!NOTE]
   >Verifique se a tela está configurada para Reproduzir por meio do URL Launcher.
   >![imagem](/help/user-guide/assets/tizen/rms-2.png)

1. Navegue até Server Address (Endereço do servidor) e digite o acesso ao URL MagicInfo e pressione Done (Concluído).

1. Configure TLS, se necessário. Navegue até a porta e selecione o número da porta no servidor. Clique em **Salvar**.

1. Navegue até a guia **Dispositivo** e verifique o dispositivo que você acabou de configurar. Depois que um dispositivo for encontrado, clique na caixa de seleção e selecione **Aprovar**.

1. Preencha as informações necessárias e selecione um grupo de dispositivos. Clique em **OK** para concluir o processo de aprovação.

   >![imagem](/help/user-guide/assets/tizen/rms-7.png)

1. Depois que o dispositivo for aprovado, ele deverá aparecer na Lista do dispositivo. Clique no botão *Information* localizado na caixa do dispositivo, ou seja **i**, conforme mostrado na figura abaixo.

   >![imagem](/help/user-guide/assets/tizen/rms-6.png)

1. A caixa de diálogo de informações do dispositivo é exibida. Selecione a guia **Informações do dispositivo** e clique em **Editar**.

   >![imagem](/help/user-guide/assets/tizen/rms-5.png)

1. Edite as opções do dispositivo e selecione a guia **Configuração**. Navegue até a seção **Iniciador de URL** e insira o URL que hospeda o wgt e `SSSP config file` para instalar um aplicativo `SSSP`, conforme mostrado na figura abaixo.

   ![imagem](/help/user-guide/assets/tizen/rms-9.png)

1. Clique em **Salvar** para que as alterações apareçam na tela de exibição.




