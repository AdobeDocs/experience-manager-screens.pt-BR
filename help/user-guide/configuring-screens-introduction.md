---
title: Configuração e implantação do AEM Screens
description: O AEM Screens player está disponível para Android&trade;, Chrome OS, iOS e Windows. Saiba mais sobre a configuração e implantação do AEM Screens.
contentOwner: Jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
docset: aem65
role: Admin
level: Intermediate
exl-id: 8cf4240c-1d6c-441d-b8a0-f01516455543
source-git-commit: fff2df02661fc3fb3098be40e090b8bc6925bcc2
workflow-type: tm+mt
source-wordcount: '679'
ht-degree: 1%

---

# Configuração e implantação do AEM Screens {#configuring-and-deploying-aem-screens}

Esta página mostra como instalar e configurar os reprodutores do Screens em seus dispositivos.

## Configuração do servidor {#server-configuration}

>[!IMPORTANT]
>
>O AEM Screens player não usa o token CSRF (Falsificação de solicitação entre sites). Portanto, para configurar o servidor AEM para que esteja pronto para uso no AEM Screens, ignore o filtro de referenciador, permitindo referenciadores vazios.

## Estrutura de verificação de integridade {#health-check-framework}

A estrutura de verificação de integridade permite que o usuário verifique se duas configurações necessárias estão definidas antes de executar um projeto do AEM Screens.

Ela permite que o usuário verifique as duas verificações de configuração a seguir para executar um projeto do AEM Screens, ou seja, verificar o estado dos dois filtros a seguir:

1. **Permitir referenciador vazio**
2. **https**

Siga as etapas abaixo para verificar se essas duas configurações vitais estão habilitadas para o AEM Screens:

1. Navegue até [Verificação de integridade do Sling no console da Web do Adobe Experience Manager](http://localhost:4502/system/console/healthcheck?tags=screensconfigs&amp;overrideGlobalTimeout=).

   ![ativos](assets/health-check1.png)


2. Clique em **Executar verificações de integridade selecionadas** para que você possa executar a validação de duas propriedades listadas acima.

   Se ambos os filtros estiverem ativados, a variável **Serviço de integridade da configuração do Screens** mostra o **Resultado** as **OK** com ambas as configurações ativadas.

   ![ativos](assets/health-check2.png)

   Se um ou ambos os filtros estiverem desativados, um alerta será exibido para o usuário, como mostrado na figura abaixo.

   O alerta a seguir mostra se ambos os filtros estão desativados:
   ![ativos](assets/health-check3.png)

>[!NOTE]
>
>* Para ativar o **Filtro referenciador do Apache Sling**, consulte [Permitir Solicitações de Referenciador Vazias](/help/user-guide/configuring-screens-introduction.md#allow-empty-referrer-requests).
>* Para ativar o **HTTP** serviço, consulte [Serviço HTTP baseado no Apache Felix Jetty](/help/user-guide/configuring-screens-introduction.md#allow-apache-felix-service).

### Pré-requisitos {#prerequisites}

Os principais pontos a seguir ajudam a configurar o e o servidor AEM para que estejam prontos para uso no AEM Screens.

#### Permitir Solicitações de Referenciador Vazias {#allow-empty-referrer-requests}

1. Navegue até **Configuração do console da Web do Adobe Experience Manager** via instância AEM > ícone de martelo > **Operações** > **Console da Web**.

   ![imagem](assets/config/empty-ref1.png)

1. **Configuração do console da Web do Adobe Experience Manager** é aberto. Pesquisar referenciador do sling.

   Para pesquisar a propriedade do referenciador do sling, pressione **Command+F** para **Mac** e **Ctrl+F** para **Windows**.

1. Verifique a **Permitir vazio** como mostrado na figura abaixo.

   ![imagem](assets/config/empty-ref2.png)

1. Clique em **Salvar** para ativar o Apache Sling Referrer Filter Allow Empty.


#### Serviço HTTP baseado no Apache Felix Jetty {#allow-apache-felix-service}

1. Navegue até **Configuração do console da Web do Adobe Experience Manager** via instância AEM > ícone de martelo > **Operações** > **Console da Web**.

   ![imagem](assets/config/empty-ref1.png)

1. **Configuração do console da Web do Adobe Experience Manager** é aberto. Procure por Serviço HTTP baseado em Apache Felix Jetty.

   Para pesquisar essa propriedade, pressione **Command+F** para **Mac** e **Ctrl+F** para **Windows**.

1. Verifique a **ATIVAR HTTP** como mostrado na figura abaixo.

   ![imagem](assets/config/config-1.png)

1. Clique em **Salvar** para habilitar o *http* serviço.

#### Habilitar a interface de toque para o AEM Screens {#enable-touch-ui-for-aem-screens}

O AEM Screens exige a interface TOUCH e não funciona com a interface CLASSIC do Adobe Experience Manager (AEM).

1. Navegue até `*<yourAuthorInstance>/system/console/configMgr/com.day.cq.wcm.core.impl.AuthoringUIModeServiceImpl*`
1. Certifique-se de que o **Modo de interface de usuário de criação padrão** está definida como **TOQUE**, conforme mostrado na figura abaixo

Como alternativa, você também pode executar a mesma configuração usando yourAuthorInstance *>* ferramentas (ícone de martelo) > **Operações** > **Console da Web** e pesquisar **Serviço de modo de interface do usuário de criação do WCM**.

![screen_shot_2018-12-04at22425pm](assets/screen_shot_2018-12-04at22425pm.png)

>[!NOTE]
>
>Você sempre pode habilitar a IU Clássica para usuários específicos usando as preferências do usuário.

#### AEM no modo de execução NOSAMPLECONTENT {#aem-in-nosamplecontent-runmode}

A execução do AEM na produção usa o **NOSAMPLECONTENT** modo de execução. Remova o *X-Frame-Options=SAMEORIGIN* cabeçalho (na seção cabeçalho de resposta adicional) de

`https://localhost:4502/system/console/configMgr/org.apache.sling.engine.impl.SlingMainServlet`.

Isso é necessário para que o AEM Screens Player reproduza canais online.

#### Restrições de senha {#password-restrictions}

Com as alterações mais recentes no ***DeviceServiceImpl***, não é necessário remover as restrições de senha.

Você pode configurar ***DeviceServiceImpl*** no link abaixo para ativar a restrição de senha ao criar a senha para os usuários do dispositivo de tela:

`https://localhost:4502/system/console/configMgr/com.adobe.cq.screens.device.impl.DeviceService`

Siga as etapas abaixo para configurar ***DeviceServiceImpl***:

1. Navegue até **Configuração do console da Web do Adobe Experience Manager** por meio da instância AEM > ícone de martelo > **Operações** > **Console da Web**.

1. **Configuração do console da Web do Adobe Experience Manager** é aberto. Pesquisar por `*deviceservice*`. Para pesquisar a propriedade, pressione **Command+F** para o macOS e **Ctrl+F** para Microsoft® Windows.

![screen_shot_2019-07-31at92058am](assets/screen_shot_2019-07-31at92058am.png)

#### Configuração do Dispatcher {#dispatcher-configuration}

Para saber como configurar o Dispatcher para um projeto do AEM Screens, consulte [Configuração do Dispatcher para um projeto do AEM Screens](dispatcher-configurations-aem-screens.md).

#### Codificação Java™ {#java-encoding}

Defina o ***Codificação Java™*** para Unicode. Por exemplo, `*Dfile.encoding=Cp1252*` não funciona.

>[!NOTE]
>
>Use HTTPS para o AEM Screens Server no uso de produção.
