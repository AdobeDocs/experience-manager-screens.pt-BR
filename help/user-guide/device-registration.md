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
source-git-commit: b65e59473e175e7c1b31fba900bb7e47eff3a263
workflow-type: tm+mt
source-wordcount: '743'
ht-degree: 0%

---

# Registro do dispositivo {#device-registration}

A página a seguir descreve o processo de registro de dispositivo em um projeto do AEM Screens.

## Registrando um dispositivo {#registering-a-device}

O processo de registro de dispositivos é feito em duas máquinas separadas:

* O dispositivo real a ser registrado, por exemplo, sua Exibição de cartazes
* O servidor AEM usado para registrar seu dispositivo

>[!NOTE]
>
>Depois de baixar o Windows Player mais recente (*.exe*), de [Downloads do reprodutor AEM 6.4](https://download.macromedia.com/screens/) siga as etapas no reprodutor para concluir a instalação ad-hoc:
>
>1. Pressione e segure no canto superior esquerdo para abrir o painel de administração.
>1. Navegue até **Configuração** no menu de ações à esquerda e insira o endereço do local da instância do AEM em **Servidor** e clique em **Salvar**.
>1. Selecione o **Registro** no menu de ação esquerdo e nas etapas abaixo para concluir o processo de registro do dispositivo.
>

![screen_shot_2018-11-26at12118pm](assets/screen_shot_2018-11-26at12118pm.png)

1. Em seu dispositivo, inicie o AEM Screens Player. A interface do usuário de registro é exibida.

   ![screen_shot_2018-11-26at104230am](assets/screen_shot_2018-11-26at104230am.png)

1. No AEM, navegue até o **Dispositivos** pasta do seu projeto.

   >[!NOTE]
   >
   >Para obter mais informações sobre como criar um projeto para o Screens no painel AEM, consulte [Criar e gerenciar projeto do Screens](creating-a-screens-project.md).

1. Toque/clique no **Gerenciador de dispositivos** na barra de ações.

   ![screen_shot_2018-11-26at104702am](assets/screen_shot_2018-11-26at104702am.png)

1. Toque/clique no **Registro do dispositivo** no canto superior direito.

   ![screen_shot_2018-11-26at104815am](assets/screen_shot_2018-11-26at104815am.png)

1. Selecione o dispositivo desejado (o mesmo que a etapa 1) e toque/clique **Registrar dispositivo**.

   ![screen_shot_2018-11-26at105112am](assets/screen_shot_2018-11-26at105112am.png)

1. No AEM, aguarde o dispositivo enviar o código de registro.

   ![screen_shot_2018-11-26at105150am](assets/screen_shot_2018-11-26at105150am.png)

1. Em seu dispositivo, verifique a **Código de registro**.

   ![screen_shot_2018-11-26at105227am](assets/screen_shot_2018-11-26at105227am.png)

1. Se a variável **Código de registro** é o mesmo em ambos os computadores, toque/clique **Validar** no AEM, conforme mostrado na etapa (6).
1. Defina o nome desejado para o dispositivo e clique em **Registrar**.

   ![screen_shot_2018-11-26at105357am](assets/screen_shot_2018-11-26at105357am.png)

1. Toque/clique **Concluir** para concluir o processo de registro.

   ![screen_shot_2018-11-26at105456am](assets/screen_shot_2018-11-26at105456am.png)

   >[!NOTE]
   >
   >A variável **Novo registro** permite registrar um novo dispositivo.
   >
   >A variável **Atribuir exibição** permite adicionar o dispositivo diretamente a uma exibição.

   Se você clicar em **Concluir**, atribua o dispositivo a uma exibição.

   ![screen_shot_2018-11-26at105740am](assets/screen_shot_2018-11-26at105740am.png)

   >[!NOTE]
   >
   >Para saber mais sobre como criar e gerenciar uma exibição para o seu projeto do Screens, consulte [Criando e Gerenciando Exibições](managing-displays.md).

### Atribuição de dispositivo a uma exibição {#assigning-device-to-a-display}

Se você não atribuiu o dispositivo a uma exibição, siga as etapas abaixo para atribuir seu dispositivo a uma exibição no projeto do AEM Screens:

1. Selecione o dispositivo e clique **Atribuir dispositivo** na barra de ações.

   ![screen_shot_2018-11-26at111026am](assets/screen_shot_2018-11-26at111026am.png)

1. Selecione o caminho da exibição em **Caminho de configuração da tela/dispositivo**.

   ![screen_shot_2018-11-26at111252am](assets/screen_shot_2018-11-26at111252am.png)

1. Clique em **Atribuir** ao selecionar o caminho.

   ![screen_shot_2018-11-26at111722am](assets/screen_shot_2018-11-26at111722am.png)

1. Clique em **Concluir** depois que o dispositivo for atribuído com êxito, conforme mostrado na figura abaixo.

   ![screen_shot_2018-11-26at112041am](assets/screen_shot_2018-11-26at112041am.png)

   Além disso, é possível exibir o painel de exibição ao clicar em **Concluir**.

   ![screen_shot_2018-11-26at112154am](assets/screen_shot_2018-11-26at112154am.png)

## Pesquisando um dispositivo no Gerenciador de dispositivos {#search-device}

Ao registrar dispositivos no reprodutor, você pode exibir todos os dispositivos na interface do usuário do Gerenciador de dispositivos.

1. Acesse a interface do usuário do Gerenciador de dispositivos a partir de seu projeto do AEM Screens, por exemplo, **DemoScreens** > **Dispositivos**.

1. Selecione o **Dispositivos** e clique em **Gerenciador de dispositivos** na barra de ações.

   ![imagem](/help/user-guide/assets/device-manager/device-manager-1.png)

1. A lista de dispositivos registrados é exibida.

1. Se você tiver uma longa lista de dispositivos registrados, agora poderá pesquisar usando o ícone de pesquisa na barra de ações

   ![imagem](/help/user-guide/assets/device-manager/device-manager-2.png)

   Ou,

   Clique em `/` (barra) para invocar a funcionalidade de pesquisa.

   ![imagem](/help/user-guide/assets/device-manager/device-manager-3.png)


### Limitações da funcionalidade de pesquisa {#limitations}

* O usuário pode pesquisar qualquer palavra existente no *ID do dispositivo* ou *Nome do dispositivo*.

  >[!NOTE]
  >É recomendável criar os nomes dos dispositivos em várias palavras, como *Lobby da Boston Store* em vez de um único *BostonStoreLobby*.

* Se você criar nomes de dispositivos como *Lobby da Boston Store*, ele pesquisa qualquer palavra *boston*, *loja* ou *lobby*. No entanto, se o nome do dispositivo for *BostonStoreLobby*, em seguida, procurando *boston* não mostra resultados.

* Curinga, `*` O é compatível com a pesquisa. Caso queira localizar todos os dispositivos com nomes que comecem com *boston*, você pode usar *boston**.

* Se o nome do dispositivo for *BostonStoreLobby* e pesquisando *boston* não retorna o resultado, usando *boston** nos critérios de pesquisa retorna o resultado.

## Limitações no registro de dispositivos {#limitations-on-device-registration}

As restrições de senha de usuário em todo o sistema podem causar falha no registro do dispositivo. O registro do dispositivo usa uma senha gerada aleatoriamente para criar o usuário do dispositivo.

Se a senha for restrita pelo *AuthorizableActionProvider* configuração, a criação do usuário do dispositivo pode falhar.

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
