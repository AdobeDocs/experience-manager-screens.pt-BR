---
title: Implementação do Windows 10 Player
seo-title: Implementação do Windows 10 Player
description: Siga esta página para saber mais sobre a configuração do AEM Screens Windows 10 player.
seo-description: Siga esta página para saber mais sobre a configuração do AEM Screens Windows 10 player.
uuid: da7e88bf-c251-481e-9029-f8fc4768b309
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
content-type: reference
discoiquuid: 4228e8a1-9749-49a6-a1bb-365492bc2a3d
docset: aem65
feature: Administering Screens, Windows Player
role: Administrator
level: Intermediate
translation-type: tm+mt
source-git-commit: 89c70e64ce1409888800af7c7edfbf92ab4b2c68
workflow-type: tm+mt
source-wordcount: '1003'
ht-degree: 1%

---


# Implementação do Windows 10 Player {#implementing-windows-player}

Esta seção descreve como configurar o player do AEM Screens Windows 10. Ele fornece informações sobre o arquivo de configuração e as opções disponíveis, além de recomendações sobre quais configurações usar para desenvolvimento e teste.

## Instalar o Windows Player {#installing-windows-player}

Para implementar o Windows Player para AEM Screens, instale o Windows Player para AEM Screens.

Visite a página [**AEM 6.5 Player Downloads**](https://download.macromedia.com/screens/).

>[!NOTE]
>Não há um modo de janela no Windows Player. É sempre o modo de tela cheia.

### Configuração do ambiente para o AEM Screens 6.5.5 Service Pack {#fp-environment-setup}

>[!NOTE]
>Você deve configurar um ambiente para o Windows Player se estiver usando o AEM Screens 6.5.5 Service Pack.

Defina o atributo **SameSite para os cookies do token de login** de **Lax** para **None** de **Adobe Experience Manager Web Console
Configuração** em todas as instâncias de criação e publicação AEM.

Siga as etapas abaixo:

1. Navegue até **Adobe Experience Manager Web Console
Configuração** usando `http://localhost:4502/system/console/configMgr`.

1. Procure por *Adobe Granite Token Authentication Handler*.

1. Defina o atributo **SameSite para os cookies do token de login** de **Lax** para **None**.
   ![imagem](/help/user-guide/assets/granite-updates.png)

1. Clique em **Salvar**.

### Método ad-hoc {#ad-hoc-method}

O método Ad-Hoc permite instalar o Windows Player mais recente (*.exe*). Visite a página [**AEM 6.5 Player Downloads**](https://download.macromedia.com/screens/).

Depois de baixar o aplicativo, siga as etapas no reprodutor para concluir a instalação ad-hoc:

1. Pressione e segure no canto superior esquerdo para abrir o painel do administrador.
1. Navegue até **Configuration** a partir do menu de ação esquerdo e insira o local (endereço) da instância de AEM à qual deseja se conectar e clique em **Save**.
1. Navegue até o link **Device** **Registration** no menu de ação esquerdo para verificar o status do processo de registro do dispositivo.

>[!NOTE]
>
>Se **State** for **REGISTERED**, você notará que o campo **Device id** será preenchido.
>
>Se **State** for **UNREGISTERED**, você poderá usar o **Token** para registrar o dispositivo.

## Alterar as opções padrão no Windows Installer {#changing-default-options}

Siga esta seção para saber como alterar as opções padrão no Windows Installer e a lista de personalizações disponíveis.

## Instalação usando CLI (PowerShell) {#install-powershell}

1. Crie um local personalizado **dedicado** para o Player do Screens, por exemplo:
   `C:\Users\User\screens-player`)
1. Instalar
   `aem-screens-player-electron-xxx-signed.exe /S /D=C:\Users\User\screens-player`
1. Abrir
   `Start-Process C:\Users\User\screens-player\AEMScreensPlayer.exe`

**Exemplo**

```shell
C:\Users\User\Downloads> mkdir screens-player

C:\Users\User\Downloads> .\aem-screens-player-electron-xxx-signed.exe /S /D=C:\Users\User\Downloads\screens-player

C:\Users\User\Downloads> Start-Process C:\Users\User\Downloads\screens-player\AEMScreensPlayer.exe
```

## Registro em massa do Windows Player {#bulk-registration}

Ao implementar o windows player, não é necessário configurar manualmente cada player. Em vez disso, você pode atualizar o arquivo JSON de configuração depois que ele for testado e estiver pronto para implantação.

A configuração garantirá que todos os players que fazem ping no mesmo servidor sejam fornecidos no arquivo de configuração. Você ainda deve registrar cada player manualmente.

Siga as etapas abaixo para configurar o Windows 10 Player:

1. Instale o Windows Player.
1. Localize o arquivo de configuração em ***%appdata%\com.adobe.aem.screens.player\config.json***.
1. Atualize o JSON de configuração usando as informações abaixo e copie a mesma pasta para todos os sistemas em que o reprodutor reside.

### Atributos de política {#policy-attributes}

A tabela a seguir resume os atributos de política com um exemplo de JSON de política para referência:

| **Nome da política** | **Propósito** |
|---|---|
| server | O URL para o servidor do Adobe Experience Manager (AEM). |
| resolução | A resolução do dispositivo. |
| reotSchedule | O agendamento para reiniciar o reprodutor. |
| enableAdminUI | Ative a interface do usuário do administrador para configurar o dispositivo no site. Defina como false depois que estiver totalmente configurado e em produção. |
| enableOSD | Ative a interface do usuário do seletor de canal para que os usuários alternem os canais no dispositivo. Considere a configuração como false depois de estar totalmente configurada e em produção. |
| enableActivityUI | Ative para mostrar o progresso de atividades como download e sincronização. Ative para solução de problemas e desative assim que estiver totalmente configurado e em produção. |

#### Exemplo de arquivo JSON de política {#example-policy-json-file}

```
{
    "server": "https://localhost:4502",
    "resolution": "auto",
    "rebootSchedule": "at 4:00 am",
    "enableAdminUI": false,
    "enableOSD": false,
    "enableActivityUI": false
}
```

## Ativando o modo de quiosque {#enabling-kiosk-mode}

Ao implantar o Windows player, é importante ativar um modo Quiosque para que outros aplicativos ou a barra de tarefas não apareçam na área de trabalho do Windows.

>[!CAUTION]
>
>O Adobe recomenda uma solução de gerenciamento de dispositivos para ativar o Quiosque para Windows. Siga as etapas abaixo, se você não tiver uma solução de gerenciamento de dispositivos para ativar o modo Quiosque. Esse método usa o recurso Shell Launcher disponível no Windows 10 Enterprise e no Edu. Qualquer outro meio recomendado pela Microsoft para aplicativos que não sejam UWP também pode ser aplicado para ativar o Quiosque, especialmente em outras edições do Windows.

Siga as etapas abaixo para ativar o modo Quiosque:

>[!NOTE]
>
>Antes de seguir as etapas abaixo, use o Windows 10 Enterprise ou Education.

1. Habilite o Shell Launcher.

   Consulte a seção ***Configurar o Shell Launcher*** na página **[Shell Launcher](https://docs.microsoft.com/en-us/windows-hardware/customize/enterprise/shell-launcher)** pelo suporte do Microsoft Windows para obter mais informações.

1. Crie um usuário não administrativo (se você já não tiver um) para ser usado no Quiosque. Pode ser um usuário local ou de domínio.
1. Instale o windows player para esse usuário do Quiosque na página [Downloads do AEM Screens Player](https://download.macromedia.com/screens/).
1. Consulte [Usar o Shell Launcher para criar um quiosque do Windows 10](https://docs.microsoft.com/en-us/windows/configuration/kiosk-shelllauncher) para modificar o script do PowerShell para obter mais informações.

   Modifique o script do PowerShell para substituir o nome de usuário pelo que você criou. Verifique se o caminho para o executável do aplicativo está correto. Isso definirá o shell personalizado como o aplicativo do windows player para o usuário do quiosque e o padrão como explorer.exe para outros usuários.

1. Execute o script do PowerShell como administrador.
1. Reinicialize e faça logon como o usuário do Quiosque e o aplicativo do reprodutor devem ser iniciados corretamente.

### Resolução de problemas {#troubleshooting}

Se você recebe uma tela preta ao fazer logon como usuário do Quiosque, significa que talvez você tenha especificado incorretamente o caminho para o executável do Windows Player. Faça logon novamente como administrador e verifique e execute o script novamente.

O caminho de instalação padrão do Windows player é:

***C:\Users\&amp;lt;your user>\AppData\Local\Programs\@aem-screensscreens-player-elétron\AEM Screens Player.exe***

O script de amostra nos links ativará e desativará o shell personalizado. Portanto, talvez seja necessário dividir o script em duas e ativar/desativar as linhas aplicáveis abaixo:

>[!NOTE]
>
>Em alguns ambientes do Windows, os scripts do PowerShell podem ser restritos por política (especialmente scripts não assinados). Para executar o script, talvez seja necessário desativar e reativar temporariamente essa restrição para executar o script. Abra uma janela do PowerShell e use esses comandos.
>
>*set-execution policy unlimited*  - para remover temporariamente as restrições
>
>*set-execution policy limited*  - para reativar a restrição após executar o script

```
# Remove the new custom shells.

$ShellLauncherClass.RemoveCustomShell($Admins_SID)

$ShellLauncherClass.RemoveCustomShell($Cashier_SID)
```

