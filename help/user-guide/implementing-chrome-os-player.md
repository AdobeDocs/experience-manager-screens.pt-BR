---
title: Implementação do Chrome OS Player
seo-title: Implementing Chrome OS Player
description: Siga esta página para saber mais sobre a implementação do Chrome OS Player usando o Console de gerenciamento do Chrome.
seo-description: Follow  this page to learn about the implementation of the Chrome OS Player using the Chrome Management Console.
uuid: eee84286-fa81-475c-ad6f-db2d6cf1fed5
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
discoiquuid: 1be944f0-02ed-48c6-98bc-504d758ff866
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: 4f16605b-aec1-45fa-a110-0af6925b74b0
source-git-commit: d8c420c289452e3ddb1be42c8f170758385ff7af
workflow-type: tm+mt
source-wordcount: '893'
ht-degree: 0%

---

# Implementação do Chrome OS Player  {#implementing-chrome-os-player}

Esta seção descreve como implementar o Chrome OS Player usando o Console de gerenciamento do Chrome.

## Utilização do console de gerenciamento do Chrome {#using-chrome-management-console}

Siga as etapas abaixo para configurar o console de gerenciamento do chrome:

1. Registre-se no Console de gerenciamento do Chrome. Você precisa obter uma licença para o Console de gerenciamento do Chrome. Contato [Suporte ao Google](https://support.google.com/chrome/a/answer/1375678?hl=en&amp;ref_topic=2935995) Clique em Gerenciar configurações do dispositivo Chrome para obter mais informações.
1. Inscreva seu dispositivo de sistema operacional Chrome no domínio aguarde 15 minutos para que o dispositivo seja sincronizado com o Console de gerenciamento do Chrome. Para saber mais sobre como registrar um dispositivo do Chrome, clique em [aqui](https://support.google.com/chrome/a/answer/1360534?hl=en).
1. O Chrome Player estará disponível na loja da web do Chrome.

>[!NOTE]
>
>Uma solução de gerenciamento de dispositivos, como o Console de gerenciamento do Chrome, é recomendada para implantação e gerenciamento de dispositivos de SO do Chrome. Embora, este documento forneça implementação para o Console de gerenciamento do Chrome, há outros fornecedores que afirmam fornecer funcionalidade semelhante. Entre em contato com o fornecedor do software de gerenciamento de dispositivos.

## Nomeação do reprodutor de SO Chrome {#name-chrome}

Você pode atribuir um nome de dispositivo amigável ao reprodutor do Chrome, enviando assim o nome de dispositivo atribuído ao Adobe Experience Manager (AEM). Esse recurso não só permite nomear o reprodutor do Chrome, como também permite atribuir facilmente o conteúdo apropriado.

>[!NOTE]
>Você pode escolher o nome do Player somente antes do registro. Depois que o Player é registrado, o nome do Player não pode mais ser alterado.

Siga as etapas abaixo para configurar o nome no Chrome player:

1. Como opção, você pode permitir que integradores de AV ou administradores de TI definam a ID do ativo e o local como parte da inscrição da empresa.

   ![imagem](/help/user-guide/assets/chrome-device/chrome1.png)

1. Você verá as opções quando puder registrar o dispositivo.

   ![imagem](/help/user-guide/assets/chrome-device/chrome2.jpg)

1. É possível definir a ID do ativo como parte da inscrição corporativa, bem como no console de gerenciamento do Chrome.

   ![imagem](/help/user-guide/assets/chrome-device/chrome3.png)

   >[!NOTE]
   >Os players do Chrome devem estar inscritos na inscrição corporativa e o player do Chrome deve ser implantado por meio do Console de gerenciamento do Chrome, caso contrário, a ID do ativo retornará em branco (por exemplo, chrome como uma extensão). O nome do dispositivo só é registrado no momento do registro. As alterações futuras não serão selecionadas pelo Adobe Experience Manager (AEM).

### Ativar modo de quiosque {#enabling-kiosk-mode}

Siga as etapas abaixo para ativar o modo Quiosque:

1. Faça logon no Console do desenvolvedor do Chrome.

   ![screen_shot_2017-12-08at20303pm](assets/screen_shot_2017-12-08at20303pm.png)

1. Navegue até **Gerenciamento de dispositivos** > **Gerenciamento do Chrome** > **Configurações do dispositivo**.
1. Role para baixo até **Configurações do quiosque** e clique em **Gerenciar aplicativos do quiosque**.

   ![quiosque](assets/kiosk.png)

1. Selecione o AEM Screens Player na Chrome Web Store.

   >[!NOTE]
   >
   >Um aplicativo publicado recentemente pode levar cerca de 15 minutos para ser exibido nesta lista.

1. Selecionar **AEM Screens Player** do **Aplicativo de quiosque de inicialização automática** lista suspensa.

   Dependendo da rede, pode levar alguns minutos para que as alterações entrem em vigor. Recomenda-se reinicializar.

#### Verificando o status do dispositivo remoto {#checking-remote-device-status}

1. Faça logon no Console do desenvolvedor do Chrome.
1. Navegue até **Gerenciamento de dispositivos** > **Dispositivos Chrome** e selecione o dispositivo que deseja controlar.
1. Clique em **Atividade do sistema e solução de problemas**.
1. Verifique a **Reinicializar dispositivo** e **Captura de tela** propriedades do dispositivo. Você também pode verificar o status do dispositivo e as informações de integridade.

>[!NOTE]
>
>Observe que essas configurações podem ser ativadas vários minutos após o dispositivo ser registrado. Cada opção pode ser ativada ao longo do tempo.

### Configuração remota de players de SO do Chrome {#configuring-remote-configuration-of-chrome-os-players}

O AEM Screens Player é um aplicativo habilitado para quiosque que também habilita a Configuração de política remota para players de SO do Chrome.

Siga as etapas abaixo para configurar várias opções do reprodutor:

1. Faça logon no Console de gerenciamento do Chrome.
1. Clique em **Gerenciamento de dispositivos** > **Gerenciamento do Chrome** > **Gerenciamento de aplicativos**. O AEM Screens Player é exibido na lista.
1. Clique no aplicativo **AEM Screens Player**.
1. Clique em **Configurações do quiosque** e selecione sua organização (*se estiver usando um ambiente de teste*).
1. Clique em **carregar arquivo de configuração** e faça upload da política de configuração (*Arquivo Json*).
1. Clique em **Salvar**. Você deve reinicializar o dispositivo para sincronizar a política.

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

| **Nome da política** | **Propósito** |
|---|---|
| servidor | O URL para o servidor Adobe Experience Manager (AEM). |
| registrationKey | Usado para registro em massa de dispositivos usando chave pré-compartilhada. |
| resolução | A resolução do dispositivo. |
| rebootSchedule | O cronograma para reinicializar o reprodutor. |
| enableAdminUI | Habilite a interface do Administrador para configurar o dispositivo no site. Defina como false depois que estiver totalmente configurado e em produção. |
| enableOSD | Habilite a interface do alternador de canal para que os usuários alternem canais no dispositivo. Considere definir como false depois que estiver totalmente configurado e em produção. |
| enableActivityUI | Permite mostrar o progresso de atividades como download e sincronização. Ative para solução de problemas e desative depois que estiver totalmente configurado e em produção. |
| cloudMode | Defina como verdadeiro se desejar que o reprodutor do Chrome se conecte ao Screens as a Cloud Service. Defina como falso para se conectar ao AMS ou AEM local. |
| cloudToken | Token de registro para se registrar no Screens as a Cloud Service. |

>[!NOTE]
>
>As configurações de política são estritamente aplicadas e não são substituídas manualmente na interface do administrador do reprodutor. Para permitir a configuração manual do reprodutor para uma política específica, não especifique a política no ***configuração de política,*** por exemplo, se você quiser permitir a configuração manual para a programação de reinicialização, não especifique a chave ***rebootSchedule*** na configuração de política.

### Uso do controle remoto do Screens {#using-remote-control}

O AEM Screens oferece a funcionalidade de Controle remoto. Saiba mais sobre esse recurso aqui: [Controle remoto do Screens](implementing-remote-control.md)
