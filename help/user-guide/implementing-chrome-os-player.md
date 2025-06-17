---
title: Implementação do Chrome OS Player
description: Saiba mais sobre a implementação do Chrome OS Player usando o Chrome Management Console.
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: 4f16605b-aec1-45fa-a110-0af6925b74b0
source-git-commit: dcaaa1c7ab0a55cecce70f593ed4fded8468130b
workflow-type: tm+mt
source-wordcount: '870'
ht-degree: 0%

---

# Implementação do Chrome OS Player {#implementing-chrome-os-player}

Esta seção descreve como implementar o Chrome OS Player usando o Chrome Management Console.

## Utilização do console de gerenciamento do Chrome {#using-chrome-management-console}

Siga as etapas abaixo para configurar o console de gerenciamento do Chrome:

1. Registre-se no Chrome Management Console. Você deve obter uma licença para o Chrome Management Console. Contate o [Suporte da Google](https://support.google.com/chrome/a/answer/1375678?hl=en&ref_topic=2935995) para gerenciar as configurações do dispositivo Chrome para obter mais informações.
1. Inscreva seu dispositivo de sistema operacional Chrome no domínio e aguarde 15 minutos para que o dispositivo seja sincronizado com o Console de gerenciamento do Chrome. Para saber mais sobre como registrar o dispositivo Chrome, clique [aqui](https://support.google.com/chrome/a/answer/1360534?hl=en).
1. O Chrome Player está disponível na Chrome Web Store.

>[!NOTE]
>
>Recomenda-se uma solução de gerenciamento de dispositivos, como o Chrome Management Console, para a implantação e o gerenciamento de dispositivos de SO da Chrome. Embora este documento forneça implementação para o Chrome Management Console, há outros fornecedores que afirmam fornecer funcionalidade semelhante. Entre em contato com o fornecedor do software de gerenciamento de dispositivos.

## Nomeação do reprodutor de SO Chrome {#name-chrome}

Você pode atribuir um nome de dispositivo amigável ao Chrome Player, enviando o nome de dispositivo atribuído ao Adobe Experience Manager (AEM). Esse recurso não só permite nomear o Chrome Player, como também permite atribuir facilmente o conteúdo apropriado.

>[!NOTE]
>Você pode escolher o nome do Player somente antes do registro. Depois que o Player é registrado, o nome do Player não pode mais ser alterado.

Siga as etapas abaixo para configurar o nome no Chrome Player:

1. Como opção, você pode permitir que os integradores de áudio-vídeo ou administradores de TI definam a ID do ativo e o local como parte da inscrição da empresa.

   ![imagem](/help/user-guide/assets/chrome-device/chrome1.png)

1. Você verá as opções quando puder registrar o dispositivo.

   ![imagem](/help/user-guide/assets/chrome-device/chrome2.jpg)

1. Você pode definir a ID do ativo como parte da inscrição corporativa e no Chrome Management Console.

   ![imagem](/help/user-guide/assets/chrome-device/chrome3.png)

   >[!NOTE]
   >Os players da Chrome devem ser inscritos na inscrição corporativa e o player do Chrome deve ser implantado por meio do Console de gerenciamento da Chrome; caso contrário, a ID do ativo retorna em branco (por exemplo, Chrome como extensão). O nome do dispositivo só é registrado no momento do registro. As alterações futuras não serão selecionadas pelo Adobe Experience Manager (AEM).

### Ativar modo de quiosque {#enabling-kiosk-mode}

Siga as etapas abaixo para ativar o modo Quiosque:

1. Faça logon no Chrome Developer Console.

   ![screen_shot_2017-12-08at20303pm](assets/screen_shot_2017-12-08at20303pm.png)

1. Navegue até **Gerenciamento de Dispositivos** > **Gerenciamento do Chrome** > **Configurações de Dispositivos**.
1. Role para baixo até **Configurações do quiosque** e clique em **Gerenciar aplicativos do quiosque**.

   ![quiosque](assets/kiosk.png)

1. Clique em AEM Screens Player na Chrome Web Store.

   >[!NOTE]
   >
   >Um aplicativo publicado recentemente pode levar cerca de 15 minutos para ser exibido nesta lista.

1. Clique em **AEM Screens Player** na lista suspensa **Aplicativo de quiosque de Início Automático**.

   Dependendo da rede, pode levar alguns minutos para que as alterações entrem em vigor. Recomenda-se reinicializar.

#### Verificando o status do dispositivo remoto {#checking-remote-device-status}

1. Faça logon no Chrome Developer Console.
1. Navegue até **Gerenciamento de Dispositivos** > **Dispositivos Chrome** e clique no dispositivo que deseja controlar.
1. Clique em **Atividade do sistema e solução de problemas**.
1. Verifique as propriedades de **Reinicializar Dispositivo** e **Captura de Tela** do dispositivo. Você também pode verificar o status do dispositivo e as informações de integridade.

>[!NOTE]
>
>Essas configurações podem ser ativadas vários minutos após o dispositivo ser registrado. Cada opção pode ser ativada ao longo do tempo.

### Configuração remota de players de SO da Chrome {#configuring-remote-configuration-of-chrome-os-players}

O AEM Screens Player é um aplicativo habilitado para quiosque que também habilita a Configuração de política remota para players de SO do Chrome.

Siga as etapas abaixo para configurar as várias opções do reprodutor:

1. Faça logon no Chrome Management Console.
1. Clique em **Gerenciamento de Dispositivos** > **Gerenciamento do Chrome** > **Gerenciamento de Aplicativos**. O AEM Screens Player é exibido na lista.
1. Clique no aplicativo **AEM Screens Player**.
1. Clique em **Configurações do quiosque** e clique em sua organização (*se estiver usando um ambiente de teste*).
1. Clique em **carregar arquivo de configuração** e carregar a política de configuração (*arquivo JSon*).
1. Clique em **Salvar**. Reinicialize o dispositivo para sincronizar a política.

>[!NOTE]
>
>Reinicialize o dispositivo para sincronizar alterações de política.

#### Exemplo de arquivo JSON de política {#example-policy-json-file}

```java
{
  "server": {
    "Value": "https://aemscreensdemo.adobeitc.com"
  },
  "resolution": {
    "Value": "auto"
  },
  "rebootSchedule": {
    "Value": "at 4:00am"
  },
  "enableAdminUI": {
    "Value": true
  },
  "enableOSD": {
    "Value": true
  },
  "enableActivityUI": {
    "Value": true
  }
}
```

### Atributos e finalidade da política {#policy-attributes-and-purpose}

A tabela a seguir resume as políticas com suas funções.

| **Nome da Política** | **Finalidade** |
|---|---|
| servidor | O URL para o servidor do Adobe Experience Manager (AEM). |
| registrationKey | Usado para registro em massa de dispositivos usando chave pré-compartilhada. |
| resolução | A resolução do dispositivo. |
| rebootSchedule | O cronograma para reinicializar o reprodutor. |
| enableAdminUI | Habilite a interface do Administrador para configurar o dispositivo no site. Defina como false depois que estiver totalmente configurado e em produção. |
| enableOSD | Habilite a interface do usuário do alternador de canais para que os usuários alternem canais no dispositivo. Considere configurá-lo como falso depois que estiver totalmente configurado e em produção. |
| enableActivityUI | Ative para que possa mostrar o progresso de atividades, como download e sincronização. Ative para solução de problemas e desative depois que estiver totalmente configurado e em produção. |
| cloudMode | Defina como verdadeiro se desejar que o Chrome Player se conecte ao Screens as a Cloud Service. Defina como falso para se conectar ao AMS ou à AEM no local. |
| cloudToken | Token de registro para se registrar no Screens as a Cloud Service. |

>[!NOTE]
>
>As configurações de política são estritamente aplicadas e a interface do administrador do player não é substituída manualmente. Para permitir a configuração manual do player para uma política específica, não especifique a política na ***configuração de política***. Por exemplo, se você deseja permitir a configuração manual para o agendamento de reinicialização, não especifique a chave ***rebootSchedule*** na configuração de política.

### Usar o controle remoto do Screens {#using-remote-control}

O AEM Screens oferece a funcionalidade de Controle remoto. Saiba mais sobre este recurso aqui: [Controle Remoto do Screens](implementing-remote-control.md)
