---
title: Configuração e implantação de telas AEM
seo-title: Configuração e implantação do Screens
description: O AEM Screens player está disponível para Android, Chrome OS, iOS e Windows. Esta página descreve a configuração e a implantação do AEM Screens e também resume as diretrizes de seleção h/w para o dispositivo do player.
seo-description: O AEM Screens player está disponível para Android, Chrome OS, iOS e Windows. Esta página descreve a configuração e a implantação do AEM Screens e também resume as diretrizes de seleção h/w para o dispositivo do player.
uuid: bf730d0f-e590-4c0d-a554-e1ff914eb420
contentOwner: Jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
discoiquuid: 0c7d6248-8ac0-4387-8725-57ed941f28f7
docset: aem65
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# Configuring and Deploying AEM Screens {#configuring-and-deploying-aem-screens}

Esta página mostra como instalar e configurar os players do Screens em seus dispositivos.

## Instalação do AEM Screens Player {#installing-aem-screens-player}

O AEM Screens player está disponível para Android, Chrome OS, iOS e Windows.

Para baixar o **AEM Screens Player**, visite a página Downloads [**do**](https://download.macromedia.com/screens/) AEM 6.5 Player.

>[!NOTE]
>
>Depois de baixar o Player mais recente (*.exe*), siga as etapas no player para concluir a instalação ad hoc:
>
>1. Pressione longamente no canto superior esquerdo para abrir o painel admin.
>1. Navegue até **Configuração** no menu de ação esquerdo, digite o endereço de localização da instância do AEM no **Servidor** e clique em **Salvar**.
>1. Clique no link **Registro** no menu de ação esquerdo e nas etapas abaixo para concluir o processo de registro do dispositivo.
>



### Additional Resources {#additional-resources}

Consulte os seguintes tópicos para obter informações detalhadas:

* Para baixar o Android Player, visite o **Google Play**. Para saber mais sobre como implementar o Android Watchdog, consulte [Implementação do Android Player](implementing-android-player.md).

* Para implementar o Chrome OS Player, consulte o [Chrome Management Console](implementing-chrome-os-player.md) para obter mais informações.

* Para configurar o AEM Screens Windows player, consulte [Implementação do Windows Player](implementing-windows-player.md).

## Server Configuration {#server-configuration}

>[!NOTE]
>
>**Importante**:
>
>O AEM Screens player não usa o token CSRF (Cross-Site Request Forgery). Portanto, para configurar e o servidor AEM estar pronto para usar para o AEM Screens, ignore o filtro de referenciador permitindo referenciadores vazios.

### Pré-requisitos {#prerequisites}

Os seguintes pontos chave abaixo ajudam a configurar e o servidor AEM a estar pronto para uso no AEM Screens:

#### Permitir solicitações de referenciador vazias {#allow-empty-referrer-requests}

1. Navegue até **Configuração do console da Web do Adobe Experience Manager **via instância do AEM —&gt; ícone de martelo —&gt; **Operações** —&gt; Console **da** Web.

   ![screen_shot_2019-07-31at91253am](assets/screen_shot_2019-07-31at91253am.png)

1. **A Configuração** do console da Web do Adobe Experience Manager é aberta. Procure por sling referrer.

   Para pesquisar a propriedade do referenciador sling, pressione **Command+F** para **Mac** e **Control+F** para **Windows**.

   ![screen_shot_2019-07-31at91728am](assets/screen_shot_2019-07-31at91728am.png)

1. Marque a opção **Permitir vazio **conforme mostrado na figura abaixo.

   ![screen_shot_2019-07-31at91807am](assets/screen_shot_2019-07-31at91807am.png)

1. Clique em **Salvar** para ativar o Filtro de referência Apache Sling Permitir vazio.

#### Ativar interface de usuário de toque para telas AEM {#enable-touch-ui-for-aem-screens}

O AEM Screens requer a interface de usuário TOQUE e não funcionará com a interface de usuário CLASSIC do Adobe Experience Manager (AEM).

1. Navegue até *&lt;yourAuthorInstance&gt;/system/console/configMgr/com.day.cq.wcm.core.impl.AuthoringUIModeServiceImpl*
1. Certifique-se de que o modo **de criação da interface de usuário** padrão esteja definido como **TOUCH (TOQUE**), como mostrado na figura abaixo

Como alternativa, você também pode executar a mesma configuração usando as ferramentas*&lt;yourAuthorInstance&gt; *-&gt;* (ícone de martelo)* -&gt; **Operations** -&gt;** Web Console** e procurar o Serviço **de modo de interface de criação** WCM.

![screen_shot_2018-12-04at22425pm](assets/screen_shot_2018-12-04at22425pm.png)

>[!NOTE]
>
>Você sempre pode ativar a interface clássica para usuários específicos usando as preferências do usuário.

#### AEM no modo de execução NOSAMPLECONTENT {#aem-in-nosamplecontent-runmode}

A execução do AEM na produção usa o modo de execução **NOSAMPLECONTENT** . *Remova o cabeçalho X-Frame-Options=SAMEORIGIN* (na seção do cabeçalho de resposta adicional) de

`https://localhost:4502/system/console/configMgr/org.apache.sling.engine.impl.SlingMainServlet`.

Isso é necessário para que o AEM Screens Player reproduza canais online.

#### Restrições de senha {#password-restrictions}

Com as alterações mais recentes em ***DeviceServiceImpl***, não é necessário remover as restrições de senha.

Você pode configurar ***DeviceServiceImpl*** a partir do link abaixo para habilitar a restrição de senha ao criar a senha para os usuários do dispositivo de telas:

`https://localhost:4502/system/console/configMgr/com.adobe.cq.screens.device.impl.DeviceService`

Siga as etapas abaixo para configurar ***DeviceServiceImpl***:

1. Navegue até **Configuração do console da Web do Adobe Experience Manager **via instância do AEM —&gt; ícone de martelo —&gt; **Operações** —&gt; Console **da** Web.

1. **A configuração do console da Web do Adobe Experience Manager **é aberta. Procure o serviço de dispositivos. Para pesquisar a propriedade, pressione **Command+F** para **Mac** e **Control+F** para **Windows**.

![screen_shot_2019-07-31at92058am](assets/screen_shot_2019-07-31at92058am.png)

#### Configuração do Dispatcher {#dispatcher-configuration}

Para saber como configurar o dispatcher para um projeto do AEM Screens, consulte [Configuração do Dispatcher para um projeto](dispatcher-configurations-aem-screens.md)do AEM Screens.

#### Codificação Java {#java-encoding}

Defina a codificação ****** Java como Unicode. Por exemplo, *Dfile.encoding=Cp1252* não funcionará.

>[!NOTE]
>
>**Recomendação:**
>
>É recomendável usar HTTPS para o AEM Screens Server em uso de produção.

