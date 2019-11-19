---
title: Implementação do Chrome OS Player
seo-title: Implementação do Chrome OS Player
description: Siga esta página para saber mais sobre a implementação do Chrome OS Player usando o Chrome Management Console.
seo-description: Siga esta página para saber mais sobre a implementação do Chrome OS Player usando o Chrome Management Console.
uuid: eee84286-fa81-475c-ad6f-db2d6cf1fed5
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
discoiquuid: 1be944f0-02ed-48c6-98bc-504d758ff866
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# Implementação do Chrome OS Player {#implementing-chrome-os-player}

Esta seção descreve como implementar o Chrome OS Player usando o Chrome Management Console.

## Usando o console de gerenciamento do Chrome {#using-chrome-management-console}

Siga as etapas abaixo para configurar o console de gerenciamento de cromo:

1. Registre-se no Chrome Management Console. É necessário obter uma licença para o Chrome Management Console. Entre em contato com o suporte [do](https://support.google.com/chrome/a/answer/1375678?hl=en&ref_topic=2935995) Google para gerenciar as configurações do dispositivo Chrome para obter mais informações.
1. Registre seu dispositivo do Chrome OS no domínio e aguarde 15 minutos para que o dispositivo seja sincronizado com o Chrome Management Console. Para saber mais sobre como inscrever o dispositivo de cromo, clique [aqui](https://support.google.com/chrome/a/answer/1360534?hl=en).
1. O Chrome Player estará disponível na loja da Web do Chrome.

>[!NOTE]
>
>Uma solução de gerenciamento de dispositivos como o Chrome Management Console é recomendada para implantação e gerenciamento de dispositivos do Chrome OS. Embora este documento forneça a implementação do Chrome Management Console, há outros fornecedores que afirmam fornecer funcionalidade semelhante. Entre em contato com o fornecedor do software de gerenciamento de dispositivos.

### Ativando o modo de quiosque {#enabling-kiosk-mode}

Siga as etapas abaixo para ativar o modo Kiosk:

1. Faça logon no Chrome Developer Console.

   ![screen_shot_2017-12-08at20303pm](assets/screen_shot_2017-12-08at20303pm.png)

1. Navegue até Gerenciamento **de** dispositivos &gt; Gerenciamento **do** Chrome **&gt; Configurações** do dispositivo.
1. Role para baixo até Configurações **de** quiosque e clique em **Gerenciar aplicativos** de quiosque.

   ![quiosque](assets/kiosk.png)

1. Selecione o AEM Screens Player na Chrome Web Store.

   >[!NOTE]
   >
   >Um aplicativo publicado recentemente pode levar cerca de 15 minutos para aparecer nessa lista.

1. Selecione **AEM Screens Player** na lista suspensa Iniciar **automaticamente o aplicativo** Kiosk.

   Pode levar alguns minutos, dependendo da rede, para que as alterações entrem em vigor. É recomendável reinicializar.

#### Verificando o status do dispositivo remoto {#checking-remote-device-status}

1. Faça logon no Chrome Developer Console.
1. Navegue até Gerenciamento **de** dispositivos &gt; Dispositivos **Chrome** e selecione o dispositivo que deseja controlar.
1. Clique em Atividade **do sistema e solução de problemas**.
1. Verifique as propriedades **Reboot Device (Dispositivo** de reinicialização) e **Screen Capture (Captura** de tela) do dispositivo. Você também pode verificar o status e as informações de integridade do dispositivo.

>[!NOTE]
>
>Observe que essas configurações podem estar ativadas alguns minutos depois que o dispositivo é inscrito. Cada opção pode ser ativada ao longo do tempo.

### Configuração remota de players do Chrome OS {#configuring-remote-configuration-of-chrome-os-players}

O AEM Screens Player é um aplicativo habilitado para Kiosk que também habilita a Configuração de política remota para players do Chrome OS.

Siga as etapas abaixo para configurar várias opções do player:

1. Faça logon no Chrome Management Console.
1. Clique em Gerenciamento **de** dispositivos &gt; Gerenciamento **** Chrome &gt; Gerenciamento **** de aplicativos. O AEM Screens Player é exibido na lista.
1. Clique no aplicativo AEM Screens Player ****.
1. Clique em Configurações **de** quiosque e selecione sua organização (*se estiver usando um ambiente* de teste).
1. Clique em **fazer upload do arquivo** de configuração e faça upload da política de configuração (arquivo ** Json).
1. Clique em **Salvar**. É necessário reinicializar o dispositivo para sincronizar a política.

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

### Atributos e finalidade da política {#policy-attributes-and-purpose}

A tabela a seguir resume as políticas com suas funções.

| **Nome da política** | **Propósito** |
|---|---|
| *server* | O URL para o Adobe Experience Manager Server |
| *resolução* | A resolução do dispositivo Chrome OS |
| *rebootSchedule* | O cronograma para reiniciar o Chrome player |
| *enableAdminUI* | Ative a interface de usuário do administrador para que os técnicos configurem o dispositivo no local. Definido como falso depois que estiver totalmente configurado e em produção. |
| *enableOSD* | Ative a interface do comutador de canal para que os usuários alternem os canais no dispositivo. Considere a configuração como false depois de estar totalmente configurada e em produção. |
| *enableActivityUI* | Permite mostrar o progresso de atividades como download e sincronização. Ative para solução de problemas e desabilite-o assim que estiver totalmente configurado e em produção. |

>[!NOTE]
>
>As configurações de política são rigorosamente aplicadas e não são substituídas manualmente na interface do usuário do administrador do player. Para permitir a configuração manual do player para uma política específica, não especifique a política na configuração da ***política,*** por exemplo, se você deseja permitir a configuração manual para a programação de reinicialização, não especifique a ***reinicializaçãoSchedule*** da chave na configuração da política.
