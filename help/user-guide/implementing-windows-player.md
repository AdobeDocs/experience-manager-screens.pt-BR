---
title: Implementação do Windows 10 Player
seo-title: Implementing Windows 10 Player
description: Siga esta página para saber mais sobre como configurar o AEM Screens Windows 10 Player.
seo-description: Follow this page to learn about configuring AEM Screens Windows 10 player.
uuid: da7e88bf-c251-481e-9029-f8fc4768b309
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
content-type: reference
discoiquuid: 4228e8a1-9749-49a6-a1bb-365492bc2a3d
docset: aem65
feature: Administering Screens, Windows Player
role: Admin
level: Intermediate
exl-id: 50b6d9ba-e672-4f4d-a9a8-fb8387685057
source-git-commit: 970762bb08f19ab07917dd5a21f67a007ec1143f
workflow-type: tm+mt
source-wordcount: '1148'
ht-degree: 1%

---

# Implementação do Windows 10 Player {#implementing-windows-player}

Esta seção descreve a configuração do AEM Screens Windows 10 Player. Ele fornece informações do arquivo de configuração e as opções disponíveis, além de recomendações sobre quais configurações usar para desenvolvimento e teste.

## Instalar o Windows Player {#installing-windows-player}

Para implementar o Windows Player para AEM Screens, instale o Windows Player para AEM Screens.

Visite o [**Downloads do reprodutor AEM 6.5**](https://download.macromedia.com/screens/) página.

>[!NOTE]
>Não há modo de janela no Windows Player. É sempre o modo de tela cheia.

### Configuração do ambiente para o AEM Screens 6.5.5 Service Pack {#fp-environment-setup}

>[!NOTE]
>Você deve configurar um ambiente para o Windows Player se estiver usando o AEM Screens 6.5.5 Service Pack.

Defina o **Atributo SameSite para os cookies de token de logon** de **Lax** para **Nenhum** de **Configuração do console da Web do Adobe Experience Manager** em todas as instâncias de autor e publicação do AEM.

Siga as etapas abaixo:

1. Navegue até **Configuração do console da Web do Adobe Experience Manager** usar `http://localhost:4502/system/console/configMgr`.

1. Pesquisar por *Manipulador de autenticação de token do Adobe Granite*.

1. Defina o **Atributo SameSite para os cookies de token de logon** de **Lax** para **Nenhum**.
   ![imagem](/help/user-guide/assets/granite-updates.png)

1. Clique em **Salvar**.

### Método Ad-Hoc {#ad-hoc-method}

O método Ad-Hoc permite instalar o Windows Player mais recente (*.exe*). Visita [**Downloads do reprodutor AEM 6.5**](https://download.macromedia.com/screens/) página.

Depois de baixar o aplicativo, siga as etapas no reprodutor para concluir a instalação ad-hoc:

1. Pressione e segure no canto superior esquerdo para abrir o painel de administração.
1. Navegue até **Configuração** no menu de ação esquerdo, digite o local (endereço) da instância de AEM à qual deseja se conectar e clique em **Salvar**.
1. Navegue até a **Dispositivo** **Registro** no menu de ação esquerdo para verificar o status do processo de registro do dispositivo.

>[!NOTE]
>
>Se a variável **Estado** é **REGISTRADO**, você observará o **ID do dispositivo** será preenchido.
>
>Se a variável **Estado** é **NÃO REGISTRADO**, você pode usar o **Token** para registrar o dispositivo.

## Nomeando Windows Player {#name-windows}

Você pode atribuir um nome de dispositivo amigável ao seu reprodutor do Windows, enviando assim o nome de dispositivo atribuído ao Adobe Experience Manager (AEM). Esse recurso não só permite nomear o player do Windows, como também permite atribuir facilmente o conteúdo apropriado.

>[!NOTE]
>Você pode escolher o nome do Player somente antes do registro. Depois que o Player é registrado, o nome do Player não pode mais ser alterado.

Siga as etapas abaixo para configurar o nome no reprodutor do Windows:

1. Clique em **start** —> **executar**
1. Insira `system.cpl`
1. Use a guia Nome do computador para definir o nome de host do computador

## Alterando as opções padrão no Windows Installer {#changing-default-options}

Siga esta seção para saber como alterar as opções padrão no Windows Installer e a lista de personalizações disponíveis.

## Instalação usando CLI (PowerShell) {#install-powershell}

1. Criar um local personalizado **dedicado** para o Screens Player, por exemplo:
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

Ao implementar o Windows Player, não é necessário configurar manualmente todos os players. Em vez disso, você pode atualizar o arquivo JSON de configuração depois que ele for testado e estiver pronto para implantação.

A configuração garantirá que todos os players executem ping no mesmo servidor fornecido no arquivo de configuração. Você ainda deve registrar manualmente cada player.

Siga as etapas abaixo para configurar o Windows 10 Player:

1. Instale o Windows Player.
1. Encontre o arquivo de configuração em ***%appdata%\com.adobe.aem.screens.player\config.json***.
1. Atualize a configuração JSON usando as informações abaixo e, em seguida, copie a mesma pasta para todos os sistemas em que o reprodutor reside.

### Atributos da política {#policy-attributes}

A tabela a seguir resume os atributos da política com um exemplo de JSON de política para referência:


| **Nome da política** | **Propósito** |
|---|---|
| servidor | O URL para o servidor Adobe Experience Manager (AEM). |
| registrationKey | Usado para registro em massa de dispositivos usando chave pré-compartilhada. |
| resolução | A resolução do dispositivo. |
| rebootSchedule | O cronograma para reinicializar o reprodutor. |
| enableAdminUI | Habilite a interface do Administrador para configurar o dispositivo no site. Defina como false depois que estiver totalmente configurado e em produção. |
| enableOSD | Habilite a interface do alternador de canal para que os usuários alternem canais no dispositivo. Considere definir como false depois que estiver totalmente configurado e em produção. |
| enableActivityUI | Permite mostrar o progresso de atividades como download e sincronização. Ative para solução de problemas e desative depois que estiver totalmente configurado e em produção. |
| cloudMode | Defina como verdadeiro se desejar que o reprodutor Tizen se conecte ao Screens as a Cloud Service. Defina como falso para se conectar ao AMS ou AEM local. |
| cloudToken | Token de registro para se registrar no Screens as a Cloud Service. |

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

## Ativar modo de quiosque {#enabling-kiosk-mode}

Ao implantar o Windows Player, é importante ativar um modo de Quiosque para que outros aplicativos ou a barra de tarefas não apareçam na área de trabalho do Windows.

>[!CAUTION]
>
>A Adobe recomenda uma solução de gerenciamento de dispositivos para habilitar o Kiosk para Windows. Siga as etapas abaixo se você não tiver uma solução de gerenciamento de dispositivos para ativar o modo Quiosque. Este método usa o recurso Shell Launcher disponível no Windows 10 Enterprise e no Edu. Qualquer outro meio recomendado pela Microsoft para aplicativos não UWP também pode ser aplicado para habilitar o Quiosque, especialmente em outras edições do Windows.

Siga as etapas abaixo para ativar o modo Quiosque:

>[!NOTE]
>
>Antes de seguir as etapas abaixo, certifique-se de usar o Windows 10 Enterprise ou Education.

1. Habilite o Shell Launcher.

   Consulte a seção ***Configurar o Shell Launcher*** in **[Iniciador do Shell](https://docs.microsoft.com/en-us/windows-hardware/customize/enterprise/shell-launcher)** página de suporte do Microsoft Windows para obter mais informações.

1. Crie um usuário não administrativo (se você já não tiver um) para ser usado para o Quiosque. Pode ser um usuário local ou de domínio.
1. Instale o Windows Player para esse usuário do Quiosque em [Downloads do AEM Screens Player](https://download.macromedia.com/screens/) página.
1. Consulte [Usar o Shell Launcher para criar um quiosque do Windows 10](https://docs.microsoft.com/en-us/windows/configuration/kiosk-shelllauncher) para modificar o script do PowerShell para obter mais informações.

   Modifique o script do PowerShell para substituir o nome de usuário pelo que você criou. Verifique se o caminho para o executável do aplicativo está correto. Isso definirá o shell personalizado como o aplicativo do Windows Player para o usuário do quiosque e o padrão como explorer.exe para outros usuários.

1. Execute o script do PowerShell como administrador.
1. Reinicialize e faça login como o usuário do Kiosk e o aplicativo reprodutor deve iniciar imediatamente.

### Resolução de problemas {#troubleshooting}

Se aparecer uma tela preta quando você se autenticar como o usuário do Kiosk, significa que você pode ter especificado incorretamente o caminho para o executável do Windows Player. Efetue login novamente como administrador e verifique e execute o script novamente.

O caminho de instalação padrão do Windows Player é:

***C:\Users\&amp;lt;seu usuário>\AppData\Local\Programs\@aem-screensscreens-player-electronic\AEM Screens Player.exe***

O exemplo de script nos links habilitará e desabilitará o shell personalizado. Portanto, talvez seja necessário dividir o script em duas e ativar/desativar as linhas aplicáveis abaixo:

>[!NOTE]
>
>Em alguns ambientes Windows, os scripts do PowerShell podem ser restritos pela política (especialmente scripts não assinados). Para executar o script, talvez seja necessário desativar temporariamente e reativar essa restrição para executar o script. Abra uma janela do PowerShell e use esses comandos.
>
>*set-execution policy irrestrito* - para remover temporariamente as restrições
>
>*política de execução de conjunto restrita* - para reativar a restrição após executar o script

```
# Remove the new custom shells.

$ShellLauncherClass.RemoveCustomShell($Admins_SID)

$ShellLauncherClass.RemoveCustomShell($Cashier_SID)
```

### Uso do controle remoto do Screens {#using-remote-control}

O AEM Screens oferece a funcionalidade de Controle remoto. Saiba mais sobre esse recurso aqui: [Controle remoto do Screens](implementing-remote-control.md)