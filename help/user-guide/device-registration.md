---
title: Registro do dispositivo
seo-title: Registro do dispositivo
description: Esta página descreve o processo de registro do dispositivo em um projeto da AEM Screens.
seo-description: Esta página descreve o processo de registro do dispositivo em um projeto da AEM Screens.
uuid: 5365e506-1641-4a0c-b34d-c39da02f700b
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: administering
discoiquuid: 523084f6-bd71-4daf-95b7-fc4c481f76dc
docset: aem65
translation-type: tm+mt
source-git-commit: 85d50951caa27b62b1e05fc808de96ffb4e526b5
workflow-type: tm+mt
source-wordcount: '785'
ht-degree: 1%

---


# Registro do dispositivo {#device-registration}

A página a seguir descreve o processo de registro do dispositivo em um projeto da AEM Screens.

## Registrando um dispositivo {#registering-a-device}

O processo de registro do dispositivo é feito em duas máquinas separadas:

* O dispositivo real a ser registrado, por exemplo, sua tela de cartazes
* O servidor AEM usado para registrar seu dispositivo

>[!NOTE]
>
>Depois de baixar o Windows Player mais recente (*.exe*), na página [AEM 6.4 Player Downloads](https://download.macromedia.com/screens/), siga as etapas no player para concluir a instalação ad hoc:
>
>1. Pressione longamente no canto superior esquerdo para abrir o painel admin.
>1. Navegue até **Configuração** no menu de ação esquerdo e digite o endereço de localização da instância AEM em **Servidor** e clique em **Salvar**.
>1. Clique no link **Registration** no menu de ação esquerdo e nas etapas abaixo para concluir o processo de registro do dispositivo.

>



![screen_shot_2018-11-26at12118pm](assets/screen_shot_2018-11-26at12118pm.png)

1. Em seu dispositivo, start o AEM Screens Player. A interface do usuário de registro é exibida.

   ![screen_shot_2018-11-26at104230am](assets/screen_shot_2018-11-26at104230am.png)

1. Em AEM, navegue até a pasta **Devices** do seu projeto.

   >[!NOTE]
   >
   >Para obter mais informações sobre como criar um novo projeto para o Screens no painel AEM, consulte [Criar e gerenciar projeto do Screens](creating-a-screens-project.md).

1. Toque/clique no botão **Gerenciador de dispositivos** na barra de ações.

   ![screen_shot_2018-11-26at104702am](assets/screen_shot_2018-11-26at104702am.png)

1. Toque/clique no botão **Device Registration** no canto superior direito.

   ![screen_shot_2018-11-26at104815am](assets/screen_shot_2018-11-26at104815am.png)

1. Selecione o dispositivo desejado (o mesmo que a etapa 1) e toque/clique em **Registrar dispositivo**.

   ![screen_shot_2018-11-26at105112am](assets/screen_shot_2018-11-26at105112am.png)

1. Em AEM, aguarde o dispositivo enviar seu código de registro.

   ![screen_shot_2018-11-26at105150am](assets/screen_shot_2018-11-26at105150am.png)

1. No dispositivo, verifique o **Código de Registro**.

   ![screen_shot_2018-11-26at105227am](assets/screen_shot_2018-11-26at105227am.png)

1. Se o **Código de Registro** for o mesmo em ambos os computadores, toque/clique no botão **Validar** no AEM, conforme mostrado na etapa (6).
1. Defina o nome desejado para o dispositivo e clique em **Register**.

   ![screen_shot_2018-11-26at105357am](assets/screen_shot_2018-11-26at105357am.png)

1. Toque/clique em **Finish** para concluir o processo de registro.

   ![screen_shot_2018-11-26at105456am](assets/screen_shot_2018-11-26at105456am.png)

   >[!NOTE]
   >
   >O **Registrar Novo** permite registrar um novo dispositivo.
   >
   >O **Atribuir Vídeo** permite que você adicione diretamente o dispositivo a uma tela.

   Se você clicar em **Concluir**, precisará atribuir o dispositivo a uma tela.

   ![screen_shot_2018-11-26at105740am](assets/screen_shot_2018-11-26at105740am.png)

   >[!NOTE]
   >
   >Para saber mais sobre como criar e gerenciar uma exibição para o seu projeto do Screens, consulte [Criação e gerenciamento de exibições](managing-displays.md).

### Atribuindo dispositivo a um monitor {#assigning-device-to-a-display}

Se você não atribuiu o dispositivo a uma tela, siga as etapas abaixo para atribuir seu dispositivo a uma tela em seu projeto do AEM Screens:

1. Selecione o dispositivo e clique em **Atribuir dispositivo** na barra de ações.

   ![screen_shot_2018-11-26at11026am](assets/screen_shot_2018-11-26at111026am.png)

1. Selecione o caminho da exibição em **Caminho de configuração de exibição/dispositivo**.

   ![screen_shot_2018-11-26at111252am](assets/screen_shot_2018-11-26at111252am.png)

1. Clique em **Atribuir** quando selecionar o caminho.

   ![screen_shot_2018-11-26at111722am](assets/screen_shot_2018-11-26at111722am.png)

1. Clique em **Concluir** depois que o dispositivo for atribuído com êxito, como mostrado na figura abaixo.

   ![screen_shot_2018-11-26at112041am](assets/screen_shot_2018-11-26at112041am.png)

   Além disso, você pode visualização o painel de exibição ao clicar em **Concluir**.

   ![screen_shot_2018-11-26at112154am](assets/screen_shot_2018-11-26at112154am.png)

## Como pesquisar um dispositivo no Gerenciador de dispositivos {#search-device}

Depois de registrar os dispositivos no player, você poderá visualização todos os dispositivos da interface do usuário do Gerenciador de dispositivos.

1. Navegue até a interface do usuário do Gerenciador de dispositivos do seu projeto AEM Screens, por exemplo, **DemoScreens** —> **Dispositivos**.

1. Selecione a pasta **Dispositivos** e clique em **Gerenciador de dispositivos** na barra de ações.

   ![imagem](/help/user-guide/assets/device-manager/device-manager-1.png)

1. A lista dos dispositivos registrados é exibida.

1. Se tiver uma lista longa de dispositivos registrados, agora é possível pesquisar usando o ícone de pesquisa na barra de ações

   ![imagem](/help/user-guide/assets/device-manager/device-manager-2.png)

   Ou,

   Clique em `/` (barra) para chamar a funcionalidade de pesquisa.

   ![imagem](/help/user-guide/assets/device-manager/device-manager-3.png)


### Limitações da funcionalidade de pesquisa {#limitations}

* O usuário poderá pesquisar qualquer palavra existente na *ID do dispositivo* ou *Nome do dispositivo*.

   >[!NOTE]
   >É recomendável criar os nomes dos dispositivos em várias palavras, como *Boston Store Lobby*, em vez de um único *BostonStoreLobby*.

* Se você criar nomes de dispositivos como *Boston Store Lobby*, ele permitirá procurar por qualquer palavra *boston*, *store* ou *lobby*, mas se o nome do dispositivo for conhecido como *BostonStoreLobby* pesquisando *boston* não mostrará os resultados.

* Caractere curinga, `*` é suportado para pesquisa. Caso deseje encontrar todos os dispositivos com nomes começando com *boston*, você pode usar *boston**.

* Se o nome do dispositivo for *BostonStoreLobby* e a procura por *boston* não devolverá o resultado, utilizando *boston** nos seus critérios de pesquisa, o resultado será devolvido.

## Limitações no registro do dispositivo {#limitations-on-device-registration}

As restrições de senha de usuário em todo o sistema podem causar falha no registro do dispositivo. O registro do dispositivo usa uma senha gerada aleatoriamente para criar o usuário do dispositivo.

Se a senha for restrita pela configuração *AuthorizableActionProvider*, a criação do usuário do dispositivo poderá falhar.

>[!NOTE]
>
>A senha aleatória gerada atualmente é composta de 36 caracteres ASCII, variando de 33 a 122 (inclui quase todos os caracteres especiais).

```java
25.09.2016 16:54:03.140 *ERROR* [59.100.121.82 [1474844043109] POST /content/screens/svc/registration HTTP/1.1] com.adobe.cq.screens.device.registration.impl.RegistrationServlet Error during device registration
javax.jcr.nodetype.ConstraintViolationException: Password violates password constraint (^(?=.*\d).{7,9}$).
        at org.apache.jackrabbit.oak.spi.security.user.action.PasswordValidationAction.validatePassword(PasswordValidationAction.java:105)
        at org.apache.jackrabbit.oak.spi.security.user.action.PasswordValidationAction.onPasswordChange(PasswordValidationAction.java:76)
        at org.apache.jackrabbit.oak.security.user.UserManagerImpl.onPasswordChange(UserManagerImpl.java:308)
```

### Recursos adicionais {#additional-resources}

Para saber mais sobre o AEM Screens Player, consulte [AEM Screens Player](working-with-screens-player.md).
