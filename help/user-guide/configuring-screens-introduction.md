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
source-git-commit: d076b0f2362b5feccc78d3984306d3036a6d916b

---


# Configuring and Deploying AEM Screens {#configuring-and-deploying-aem-screens}

Esta página mostra como instalar e configurar os players do Screens em seus dispositivos.

## Server Configuration {#server-configuration}

>[!NOTE]
>
>**Importante**:
>
>O AEM Screens player não usa o token CSRF (Cross-Site Request Forgery). Portanto, para configurar e o servidor AEM estar pronto para usar para o AEM Screens, ignore o filtro de referenciador permitindo referenciadores vazios.

## Estrutura de verificação de integridade {#health-check-framework}

A estrutura de verificação de integridade permite que o usuário verifique se duas configurações necessárias estão configuradas antes de executar um projeto do AEM Screens.

Ele permite que o usuário verifique as duas verificações de configuração a seguir para executar um projeto do AEM Screens, ou seja, para verificar o estado dos dois filtros a seguir:

1. **Permitir Referenciador Vazio**
2. **https**

Siga as etapas abaixo para verificar se essas duas configurações vitais estão habilitadas para o AEM Screens:

1. Navegue até [Adobe Experience Manager Web ConsoleVerificação](http://localhost:4502/system/console/healthcheck?tags=screensconfigs&overrideGlobalTimeout=)de integridade do Sling.

   ![ativos](assets/health-check1.png)


2. Clique em **Executar verificações** de integridade selecionadas para executar a validação de duas propriedades listadas acima.

   Se ambos os filtros estiverem ativados, o Serviço **de Integridade da Configuração da** Tela mostrará o **Resultado** como **OK** com ambas as configurações como ativado.

   ![ativos](assets/health-check2.png)

   Se um ou ambos os filtros estiverem desativados, um alerta será exibido para o usuário, como mostra a figura abaixo.

   O alerta a seguir mostra se os dois filtros estão desativados:
   ![ativos](assets/health-check3.png)

>[!NOTE]
>
>* Para habilitar o Filtro **do Referenciador do** Apache Sling, consulte [Permitir solicitações](/help/user-guide/configuring-screens-introduction.md#allow-empty-referrer-requests)vazias do referenciador.
>* Para habilitar o serviço **HTTP** , consulte [Apache Felix Jetty Based HTTP Service](/help/user-guide/configuring-screens-introduction.md#allow-apache-felix-service).


### Pré-requisitos {#prerequisites}

Os seguintes pontos chave abaixo ajudam a configurar e o servidor AEM a estar pronto para uso no AEM Screens.

#### Permitir solicitações de referenciador vazias {#allow-empty-referrer-requests}

1. Navegue até Configuração **do console da Web do** Adobe Experience Manager por meio da instância do AEM —> ícone de martelo —> **Operações** —> Console **da** Web.

   ![screen_shot_2019-07-31at91253am](assets/screen_shot_2019-07-31at91253am.png)

1. **A Configuração** do console da Web do Adobe Experience Manager é aberta. Procure por sling referrer.

   Para pesquisar a propriedade do referenciador sling, pressione **Command+F** para **Mac** e **Control+F** para **Windows**.

   ![screen_shot_2019-07-31at91728am](assets/screen_shot_2019-07-31at91728am.png)

1. Marque a opção **Permitir vazio** , conforme mostrado na figura abaixo.

   ![screen_shot_2019-07-31at91807am](assets/screen_shot_2019-07-31at91807am.png)

1. Clique em **Salvar** para ativar o Filtro de referência Apache Sling Permitir vazio.

#### Serviço HTTP Apache Felix Jetty {#allow-apache-felix-service}

1. Navegue até Configuração **do console da Web do** Adobe Experience Manager por meio da instância do AEM —> ícone de martelo —> **Operações** —> Console **da** Web.

   ![screen_shot_2019-07-31at91253am](assets/screen_shot_2019-07-31at91253am.png)

1. **A Configuração** do console da Web do Adobe Experience Manager é aberta. Procure o serviço HTTP baseado em Jetty do Apache Felix.

   Para pesquisar essa propriedade, pressione **Command+F** para **Mac** e **Control+F** para **Windows**.

1. Marque a opção **ATIVAR HTTP** , conforme mostrado na figura abaixo.

   ![screen_shot_2019-07-31at91807am](assets/http-image.png)

1. Clique em **Salvar** para ativar o serviço *http* .

#### Ativar interface de usuário de toque para telas AEM {#enable-touch-ui-for-aem-screens}

O AEM Screens requer a interface de usuário TOQUE e não funcionará com a interface de usuário CLASSIC do Adobe Experience Manager (AEM).

1. Navegue até *&lt;yourAuthorInstance>/system/console/configMgr/com.day.cq.wcm.core.impl.AuthoringUIModeServiceImpl*
1. Certifique-se de que o modo **de criação da interface de usuário** padrão esteja definido como **TOUCH (TOQUE**), como mostrado na figura abaixo

Como alternativa, você também pode executar a mesma configuração usando *&lt;yourAuthorInstance>*->*ferramentas (ícone de martelo)* -> **Operações** -> Console **da** Web e pesquisar o Serviço **de modo de interface de criação** WCM.

![screen_shot_2018-12-04at22425pm](assets/screen_shot_2018-12-04at22425pm.png)

>[!NOTE]
>
>Você sempre pode ativar a interface clássica para usuários específicos usando as preferências do usuário.

#### AEM no modo de execução NOSAMPLECONTENT {#aem-in-nosamplecontent-runmode}

A execução do AEM na produção usa o modo de execução **NOSAMPLECONTENT** . *Remova o cabeçalho X-Frame-Options=SAMEORIGIN* (na seção do cabeçalho de resposta adicional) de

`https://localhost:4502/system/console/configMgr/org.apache.sling.engine.impl.SlingMainServlet`.

Isso é necessário para que o AEM Screens Player reproduza canais online.

#### Restrições de senha {#password-restrictions}

Com as alterações mais recentes em ***DeviceServiceImpl ***, não é necessário remover as restrições de senha.

Você pode configurar ***DeviceServiceImpl ***a partir do link abaixo para habilitar a restrição de senha ao criar a senha para os usuários do dispositivo de telas:

`https://localhost:4502/system/console/configMgr/com.adobe.cq.screens.device.impl.DeviceService`

Siga as etapas abaixo para configurar ***DeviceServiceImpl ***:

1. Navegue até Configuração **do console da Web do** Adobe Experience Manager por meio da instância do AEM —> ícone de martelo —> **Operações** —> Console **da** Web.

1. **A configuração do console da Web do Adobe Experience Manager **é aberta. Procure o serviço de dispositivos. Para pesquisar a propriedade, pressione **Command+F** para **Mac** e **Control+F** para **Windows**.

![screen_shot_2019-07-31at92058am](assets/screen_shot_2019-07-31at92058am.png)

#### Configuração do Dispatcher {#dispatcher-configuration}

Para saber como configurar o dispatcher para um projeto do AEM Screens, consulte [Configuração do Dispatcher para um projeto](dispatcher-configurations-aem-screens.md)do AEM Screens.

#### Codificação Java {#java-encoding}

Defina a codificação ******Java como Unicode. Por exemplo,*Dfile.encoding=Cp1252 *não funcionará.

>[!NOTE]
>
>**Recomendação:**
>
>É recomendável usar HTTPS para o AEM Screens Server em uso de produção.








