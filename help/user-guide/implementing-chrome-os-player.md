---
title: Implementação do reprodutor do sistema operacional Chrome
seo-title: Implementação do reprodutor do sistema operacional Chrome
description: Siga esta página para saber mais sobre a implementação do Player do sistema operacional Chrome usando o Console de gerenciamento do Chrome.
seo-description: Siga esta página para saber mais sobre a implementação do Player do sistema operacional Chrome usando o Console de gerenciamento do Chrome.
uuid: eee84286-fa81-475c-ad6f-db2d6cf1fed5
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
discoiquuid: 1be944f0-02ed-48c6-98bc-504d758ff866
feature: Administração do Screens
role: Administrator
level: Intermediate
source-git-commit: 7fa4207be0d89a6c7d0d9d9a04722cd40d035634
workflow-type: tm+mt
source-wordcount: '829'
ht-degree: 0%

---


# Implementação do reprodutor do Chrome OS {#implementing-chrome-os-player}

Esta seção descreve como implementar o Player do sistema operacional Chrome usando o Console de gerenciamento do Chrome.

## Usando o Console de Gerenciamento do Chrome {#using-chrome-management-console}

Siga as etapas abaixo para configurar o console de gerenciamento do Chrome:

1. Inscreva-se no Console de Gerenciamento do Chrome. Você precisa obter uma licença para o Chrome Management Console. Entre em contato com o [Suporte do Google](https://support.google.com/chrome/a/answer/1375678?hl=en&amp;ref_topic=2935995) para gerenciar as configurações do dispositivo Chrome para obter mais informações.
1. Inscreva o dispositivo do sistema operacional Chrome no domínio e aguarde 15 minutos para que o dispositivo sincronize com o Chrome Management Console. Para saber mais sobre a inscrição do dispositivo chrome, clique [aqui](https://support.google.com/chrome/a/answer/1360534?hl=en).
1. O Player do Chrome estará disponível na loja da Web do Chrome.

>[!NOTE]
>
>Uma solução de gerenciamento de dispositivos como o Console de gerenciamento do Chrome é recomendada para a implantação e o gerenciamento de dispositivos SO Chrome. Embora esse documento forneça implementação para o Console de gerenciamento do Chrome, há outros fornecedores que afirmam fornecer funcionalidade semelhante. Entre em contato com o fornecedor do software de gerenciamento de dispositivos.

## Nomeando o reprodutor do sistema operacional Chrome {#name-chrome}

Você pode atribuir um nome de dispositivo amigável ao seu player do Chrome, enviando o nome do dispositivo atribuído ao Adobe Experience Manager (AEM). Esse recurso permite não apenas nomear o player do Chrome, mas também atribuir facilmente o conteúdo apropriado.

Siga as etapas abaixo para configurar o nome no Chrome player:

1. Opcionalmente, é possível permitir que integradores de AV ou administradores de TI definam a ID do ativo e o local como parte da inscrição corporativa.

   ![imagem](/help/user-guide/assets/chrome-device/chrome1.png)

1. Você verá as opções quando conseguir inscrever o dispositivo.

   ![imagem](/help/user-guide/assets/chrome-device/chrome2.jpg)

1. Você pode definir a ID do ativo como parte da inscrição corporativa, bem como no console de gerenciamento do Chrome.

   ![imagem](/help/user-guide/assets/chrome-device/chrome3.png)

   >[!NOTE]
   >Os Players do Chrome devem ser inscritos na inscrição corporativa e o player do Chrome deve ser implantado por meio do Console de Gerenciamento do Chrome; caso contrário, a ID do ativo retornará em branco (por exemplo, chrome como uma extensão). O nome do dispositivo só é registrado no momento do registro. As alterações futuras não serão selecionadas pelo Adobe Experience Manager (AEM).

### Ativando o modo de quiosque {#enabling-kiosk-mode}

Siga as etapas abaixo para ativar o modo Quiosque:

1. Faça logon no Console do desenvolvedor do Chrome.

   ![screen_shot_2017-12-08at20303pm](assets/screen_shot_2017-12-08at20303pm.png)

1. Navegue até **Device management** > **Chrome Management** > **Device Settings**.
1. Role para baixo até **Configurações do Quiosque** e clique em **Gerenciar Aplicativos do Quiosque**.

   ![quiosque](assets/kiosk.png)

1. Selecione o Player do AEM Screens na Chrome Web Store.

   >[!NOTE]
   >
   >Um aplicativo publicado recentemente pode levar cerca de 15 minutos para ser exibido nessa lista.

1. Selecione **AEM Screens Player** na lista suspensa **Iniciar automaticamente o aplicativo do Quiosque**.

   Pode levar alguns minutos, dependendo da rede, para que as alterações entrem em vigor. É recomendável reiniciar.

#### Verificando o status do dispositivo remoto {#checking-remote-device-status}

1. Faça logon no Console do desenvolvedor do Chrome.
1. Navegue até **Device management** > **Chrome Devices** e selecione o dispositivo que deseja controlar.
1. Clique em **Atividade do sistema e solução de problemas**.
1. Verifique as propriedades **Reboot Device** e **Screen Capture** do dispositivo. Você também pode verificar o status do dispositivo e as informações de integridade.

>[!NOTE]
>
>Observe que essas configurações podem ser ativadas alguns minutos após a inscrição do dispositivo. Cada opção pode ser ativada ao longo do tempo.

### Configuração remota de players do Chrome OS {#configuring-remote-configuration-of-chrome-os-players}

O AEM Screens Player é um aplicativo habilitado para Quiosque que também habilita a Configuração de Política Remota para Players SO Chrome.

Siga as etapas abaixo para configurar várias opções do reprodutor:

1. Faça logon no Console de gerenciamento do Chrome.
1. Clique em **Gerenciamento de dispositivos** > **Gerenciamento do Chrome** > **Gerenciamento de aplicativos**. O Player do AEM Screens é exibido na lista.
1. Clique no aplicativo **AEM Screens Player**.
1. Clique em **Configurações do Quiosque** e selecione sua organização (*se estiver usando um ambiente de teste*).
1. Clique em **carregar arquivo de configuração** e faça upload da política de configuração (*Arquivo Json*).
1. Clique em **Salvar**. Você deve reiniciar o dispositivo para sincronizar a política.

>[!NOTE]
>
>Reinicialize o dispositivo para sincronizar as alterações de política.

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

### Atributos de política e finalidade {#policy-attributes-and-purpose}

O quadro seguinte resume as políticas com as suas funções.

| **Nome da política** | **Propósito** |
|---|---|
| *server* | O URL para o servidor Adobe Experience Manager |
| *resolução* | A resolução do dispositivo SO Chrome |
| *reotSchedule* | O agendamento para reiniciar o player do Chrome |
| *enableAdminUI* | Ative a interface do usuário do administrador para que os técnicos configurem o dispositivo no local. Defina como false depois que estiver totalmente configurado e em produção. |
| *enableOSD* | Ative a interface do usuário do seletor de canal para que os usuários alternem os canais no dispositivo. Considere a configuração como false depois de estar totalmente configurada e em produção. |
| *enableActivityUI* | Ative para mostrar o progresso de atividades como download e sincronização. Ative para solução de problemas e desative assim que estiver totalmente configurado e em produção. |

>[!NOTE]
>
>As configurações de política são estritamente aplicadas e não são manualmente substituídas na interface do usuário do administrador do player. Para permitir a configuração manual do player para uma política específica, não especifique a política na configuração da política ***por exemplo,***, se você deseja permitir a configuração manual para o agendamento de reinicialização, não especifique a chave ***reotSchedule*** na configuração da política.
