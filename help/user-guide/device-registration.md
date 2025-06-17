---
title: Registro do dispositivo
description: Saiba mais sobre o processo de registro de dispositivos em um projeto do AEM Screens.
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: administering
docset: aem65
feature: Administering Screens, Device Registration
role: Admin
level: Intermediate
exl-id: b2d3a2cd-263f-4142-80da-29ce54cbf391
source-git-commit: dcaaa1c7ab0a55cecce70f593ed4fded8468130b
workflow-type: tm+mt
source-wordcount: '721'
ht-degree: 0%

---

# Registro do dispositivo {#device-registration}

A página a seguir descreve o processo de registro de dispositivo em um projeto do AEM Screens.

## Registrando um dispositivo {#registering-a-device}

O processo de registro de dispositivos é feito em duas máquinas separadas:

* O dispositivo real a ser registrado, por exemplo, sua Exibição de cartazes
* O servidor do AEM usado para registrar seu dispositivo

>[!NOTE]
>
>Depois de baixar o Windows Player (*.exe*) mais recente na página [Downloads do AEM 6.4 Player](https://download.macromedia.com/screens/), siga as etapas no player para concluir a instalação ad-hoc:
>
>1. Pressione e segure no canto superior esquerdo para abrir o painel de administração.
>1. Navegue até **Configuração** no menu de ações esquerdo e digite o endereço do local da instância do AEM no **Servidor** e clique em **Salvar**.
>1. Clique no link **Registro** no menu de ação esquerdo e nas etapas abaixo para concluir o processo de registro do dispositivo.
>

![screen_shot_2018-11-26at12118pm](assets/screen_shot_2018-11-26at12118pm.png)

1. Em seu dispositivo, inicie o AEM Screens Player. A interface do usuário de registro é exibida.

   ![screen_shot_2018-11-26at104230am](assets/screen_shot_2018-11-26at104230am.png)

1. No AEM, navegue até a pasta **Dispositivos** do seu projeto.

   >[!NOTE]
   >
   >Para obter mais informações sobre como criar um projeto para o Screens no painel do AEM, consulte [Criar e gerenciar projeto do Screens](creating-a-screens-project.md).

1. Clique no botão **Gerenciador de dispositivos** na barra de ações.

   ![screen_shot_2018-11-26at104702am](assets/screen_shot_2018-11-26at104702am.png)

1. Clique no botão **Device Registration** na parte superior direita.

   ![screen_shot_2018-11-26at104815am](assets/screen_shot_2018-11-26at104815am.png)

1. Clique no dispositivo necessário (o mesmo da etapa 1) e clique em **Registrar dispositivo**.

   ![screen_shot_2018-11-26at105112am](assets/screen_shot_2018-11-26at105112am.png)

1. No AEM, aguarde o dispositivo enviar o código de registro.

   ![screen_shot_2018-11-26at105150am](assets/screen_shot_2018-11-26at105150am.png)

1. Em seu dispositivo, verifique o **Código de Registro**.

   ![screen_shot_2018-11-26at105227am](assets/screen_shot_2018-11-26at105227am.png)

1. Se o **Código de Registro** for o mesmo em ambos os computadores, clique no botão **Validar** no AEM, conforme mostrado na etapa (6).
1. Defina o nome desejado para o dispositivo e clique em **Registrar**.

   ![screen_shot_2018-11-26at105357am](assets/screen_shot_2018-11-26at105357am.png)

1. Clique em **Concluir** para concluir o processo de registro.

   ![screen_shot_2018-11-26at105456am](assets/screen_shot_2018-11-26at105456am.png)

   >[!NOTE]
   >
   >O **Registrar Novo** permite registrar um novo dispositivo.
   >
   >**Atribuir exibição** permite que você adicione o dispositivo diretamente a uma exibição.

   Se você clicar em **Concluir**, atribua o dispositivo a uma exibição.

   ![screen_shot_2018-11-26at105740am](assets/screen_shot_2018-11-26at105740am.png)

   >[!NOTE]
   >
   >Para saber mais sobre como criar e gerenciar uma exibição para o seu projeto do Screens, consulte [Criação e gerenciamento de exibições](managing-displays.md).

### Atribuição de dispositivo a uma exibição {#assigning-device-to-a-display}

Se você não atribuiu o dispositivo a uma exibição, siga as etapas abaixo para atribuir seu dispositivo a uma exibição no projeto do AEM Screens:

1. Clique no dispositivo e clique em **Atribuir dispositivo** na barra de ações.

   ![screen_shot_2018-11-26at111026am](assets/screen_shot_2018-11-26at111026am.png)

1. Clique no caminho da exibição em **Caminho de Configuração de Exibição/Dispositivo**.

   ![screen_shot_2018-11-26at111252am](assets/screen_shot_2018-11-26at111252am.png)

1. Clique em **Atribuir** ao clicar no caminho.

   ![screen_shot_2018-11-26at111722am](assets/screen_shot_2018-11-26at111722am.png)

1. Clique em **Concluir** depois que o dispositivo for atribuído com êxito, conforme mostrado na figura abaixo.

   ![screen_shot_2018-11-26at112041am](assets/screen_shot_2018-11-26at112041am.png)

   Você também pode exibir o painel de exibição selecionando **Concluir**.

   ![screen_shot_2018-11-26at112154am](assets/screen_shot_2018-11-26at112154am.png)

## Pesquisando um dispositivo no Gerenciador de dispositivos {#search-device}

Ao registrar dispositivos no reprodutor, você pode exibir todos os dispositivos na interface do usuário do Gerenciador de dispositivos.

1. Acesse a interface do usuário do Gerenciador de dispositivos a partir do seu projeto do AEM Screens, por exemplo, **DemoScreens** > **Dispositivos**.

1. Clique na pasta **Dispositivos** e clique em **Gerenciador de Dispositivos** na barra de ações.

   ![imagem](/help/user-guide/assets/device-manager/device-manager-1.png)

1. A lista de dispositivos registrados é exibida.

1. Se você tiver uma longa lista de dispositivos registrados, agora poderá pesquisar usando o ícone de pesquisa na barra de ações

   ![imagem](/help/user-guide/assets/device-manager/device-manager-2.png)

   Ou,

   Selecione `/` (barra) para invocar a funcionalidade de pesquisa.

   ![imagem](/help/user-guide/assets/device-manager/device-manager-3.png)


### Limitações da funcionalidade de pesquisa {#limitations}

* O usuário pode pesquisar qualquer palavra existente na *ID do dispositivo* ou no *Nome do dispositivo*.

  >[!NOTE]
  >É recomendável criar os nomes de dispositivos em várias palavras, como *`Boston Store Lobby`*, em vez de um único *`BostonStoreLobby`*.

* Se você criou nomes de dispositivos como *`Boston Store Lobby`*, ele procura qualquer palavra *`boston`*, *`store`* ou *`lobby`*. No entanto, se o nome do dispositivo for *`BostonStoreLobby`*, a pesquisa por *`boston`* não mostrará resultados.

* Curinga, `*` tem suporte para pesquisa. Caso queira localizar todos os dispositivos com nomes que começam com *`boston`*, você poderá usar *`boston`**.

* Se o nome do dispositivo for *`BostonStoreLobby`* e a pesquisa por *`boston`* não retornar o resultado, o uso de *`boston`** nos critérios de pesquisa retornará o resultado.

## Limitações no registro de dispositivos {#limitations-on-device-registration}

As restrições de senha de usuário em todo o sistema podem causar falha no registro do dispositivo. O registro do dispositivo usa uma senha gerada aleatoriamente para criar o usuário do dispositivo.

Se a configuração *AuthorizableActionProvider* restringir a senha, a criação do usuário do dispositivo poderá falhar.

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

### Outros recursos {#additional-resources}

Para saber mais sobre o AEM Screens Player, consulte [AEM Screens Player](working-with-screens-player.md).
