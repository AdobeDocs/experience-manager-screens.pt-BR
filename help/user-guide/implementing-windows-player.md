---
title: Implementação do Windows Player
description: Saiba como configurar o Windows Player no AEM Screens.
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
content-type: reference
docset: aem65
feature: Administering Screens, Windows Player
role: Admin
level: Intermediate
exl-id: 50b6d9ba-e672-4f4d-a9a8-fb8387685057
source-git-commit: dcaaa1c7ab0a55cecce70f593ed4fded8468130b
workflow-type: tm+mt
source-wordcount: '1118'
ht-degree: 1%

---

# Implementação do Windows Player {#implementing-windows-player}

Esta seção descreve como configurar o Windows Player no AEM Screens. Ele fornece informações do arquivo de configuração e as opções disponíveis, além de recomendações sobre quais configurações usar para desenvolvimento e teste.

## Instalar o Windows Player {#installing-windows-player}

Para implementar o Windows Player para AEM Screens, instale o Windows Player para AEM Screens.

Visite a página [**Downloads do AEM 6.5 Player**](https://download.macromedia.com/screens/).

>[!NOTE]
>Não há modo de janela no Windows Player. Está sempre no modo de tela cheia.

### Configuração do ambiente para o AEM Screens 6.5.5 Service Pack {#fp-environment-setup}

>[!NOTE]
>Configure um ambiente para o Windows Player se estiver usando o AEM Screens 6.5.5 Service Pack.

Defina o atributo **SameSite para os cookies de token de logon** do **Lax** para **None** no **Console da Web do Adobe Experience Manager
Configuração** em todas as instâncias de autor e publicação do AEM.

Siga as etapas abaixo:

1. Navegue até o **Console da Web do Adobe Experience Manager
Configuração** usando `http://localhost:4502/system/console/configMgr`.

1. Pesquise por *Manipulador de autenticação de token do Adobe Granite*.

1. Defina o atributo **SameSite para os cookies de token de logon** do **Lax** para **None**.
   ![imagem](/help/user-guide/assets/granite-updates.png)

1. Clique em **Salvar**.

### Método Ad-Hoc {#ad-hoc-method}

O método Ad-Hoc permite instalar o Windows Player mais recente (*.exe*). Visite a página [**Downloads do AEM 6.5 Player**](https://download.macromedia.com/screens/).

Depois de baixar o aplicativo, siga as etapas no reprodutor para concluir a instalação ad-hoc:

1. Pressione e segure no canto superior esquerdo para abrir o painel de administração.
1. Navegue até **Configuração** no menu de ação esquerdo e digite o local (endereço) da instância do AEM à qual você deseja se conectar e clique em **Salvar**.
1. Navegue até o link **Dispositivo** **Registro** no menu de ação esquerdo para verificar o status do processo de registro do dispositivo.

>[!NOTE]
>
>Se o **Estado** for **REGISTRADO**, observe que o campo **ID do dispositivo** está preenchido.
>
>Se o **Estado** for **NÃO REGISTRADO**, você poderá usar o **Token** para registrar o dispositivo.

## Nomeando Windows Player {#name-windows}

Você pode atribuir um nome de dispositivo amigável ao seu Windows Player, enviando o nome de dispositivo atribuído ao Adobe Experience Manager (AEM). Esse recurso não só permite nomear o Windows Player, como também permite atribuir facilmente o conteúdo apropriado.

>[!NOTE]
>Você pode escolher o nome do Player somente antes do registro. Depois que o Player é registrado, o nome do Player não pode mais ser alterado.

Siga as etapas abaixo para configurar o nome no Windows Player:

1. Clique em **iniciar** > **executar**.
1. Digite `system.cpl`.
1. Use a guia Nome do computador para definir o nome de host do computador.

## Alterando as opções padrão no Windows Installer {#changing-default-options}

Siga esta seção para saber como alterar as opções padrão no Windows Installer e a lista de personalizações disponíveis.

## Instalação usando CLI (PowerShell) {#install-powershell}

1. Crie um local personalizado **dedicado** para o Screens Player, por exemplo:
   `C:\Users\User\screens-player`
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

Ao implementar o Windows Player, não é necessário configurar manualmente todos os reprodutores. Em vez disso, você pode atualizar o arquivo JSON de configuração depois que ele for testado e estiver pronto para implantação.

A configuração garante que todos os players executem ping no mesmo servidor fornecido no arquivo de configuração. Registre manualmente cada player.

Siga as etapas abaixo para configurar o Windows 10 Player:

1. Instale o Windows Player.
1. Localize o arquivo de configuração em ***%appdata%\com.adobe.aem.screens.player\config.json***.
1. Atualize a configuração JSON usando as informações abaixo e, em seguida, copie a mesma pasta para todos os sistemas em que o reprodutor reside.

### Atributos da política {#policy-attributes}

A tabela a seguir resume os atributos da política com um exemplo de JSON de política para referência:


| **Nome da Política** | **Finalidade** |
|---|---|
| servidor | O URL para o servidor do Adobe Experience Manager (AEM). |
| registrationKey | Usado para registro em massa de dispositivos usando chave pré-compartilhada. |
| resolução | A resolução do dispositivo. |
| rebootSchedule | O cronograma para reinicializar o reprodutor. |
| enableAdminUI | Habilite a interface do Administrador para configurar o dispositivo no site. Defina como false depois que estiver totalmente configurado e em produção. |
| enableOSD | Habilite a interface do usuário do alternador de canais para que os usuários alternem canais no dispositivo. Considere configurá-lo como falso depois que estiver totalmente configurado e em produção. |
| enableActivityUI | Ative para que possa mostrar o progresso de atividades, como download e sincronização. Ative para solução de problemas e desative depois que estiver totalmente configurado e em produção. |
| cloudMode | Defina como verdadeiro se desejar que o Windows Player se conecte ao Screens as a Cloud Service. Defina como falso para se conectar ao AMS ou à AEM no local. |
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

Ao implantar o Windows Player, é importante habilitar um modo de Quiosque para que outros aplicativos ou a barra de tarefas não apareçam na área de trabalho do Windows.

>[!CAUTION]
>
>A Adobe recomenda uma solução de gerenciamento de dispositivos para habilitar o Quiosque para Windows. Siga as etapas abaixo se você não tiver uma solução de gerenciamento de dispositivos para ativar o modo Quiosque. Este método usa o recurso Shell Launcher disponível no Windows 10 Enterprise e no Edu. Qualquer outro meio recomendado pela Microsoft para aplicativos não UWP também pode ser aplicado para habilitar o Quiosque, especialmente em outras edições do Windows.

Siga as etapas abaixo para ativar o modo Quiosque:

>[!NOTE]
>
>Antes de seguir as etapas abaixo, certifique-se de usar o Windows 10 Enterprise ou Education.

1. Habilite o Shell Launcher.

   Consulte a página ***Configurar Iniciador do Shell*** em **[Iniciador do Shell](https://learn.microsoft.com/en-us/windows/configuration/shell-launcher/)** do suporte do Microsoft® Windows para obter informações adicionais.

1. Crie um usuário não administrativo (se você já não tiver um) para ser usado para o Quiosque. Ele pode ser um usuário local ou de domínio.
1. Instale o Windows Player para esse usuário do Quiosque a partir da página [Downloads do AEM Screens Player](https://download.macromedia.com/screens/).
1. Consulte [Usar o Inicializador do Shell para criar um quiosque do Windows 10](https://learn.microsoft.com/en-us/windows/configuration/shell-launcher/?tabs=intune) e modificar seu script do PowerShell para obter mais informações.

   Modifique o script do PowerShell para poder substituir o nome de usuário pelo que você criou. Verifique se o caminho para o executável do aplicativo está correto. Isso define o shell personalizado como o aplicativo do Windows Player para o usuário do quiosque e define o padrão como explorer.exe para outros usuários.

1. Execute o script do PowerShell como administrador.
1. Reinicialize e faça login como o usuário do Kiosk e o aplicativo reprodutor deve iniciar imediatamente.

### Resolução de problemas {#troubleshooting}

Se aparecer uma tela preta depois de fazer logon como o usuário do Kiosk, isso significa que talvez você tenha especificado incorretamente o caminho para o executável do Windows Player. Efetue login novamente como administrador e verifique e execute o script novamente.

O caminho de instalação padrão do Windows Player é:

***C:\Users\&lt;seu usuário>\AppData\Local\Programs\@aem-screensscreens-player-electronic\AEM Screens Player.exe***

O exemplo de script nos links ativa e desativa o shell personalizado. Portanto, divida o script em duas e ative/desative as linhas aplicáveis abaixo:

>[!NOTE]
>
>Alguns ambientes do Windows restringem scripts do PowerShell por política, especialmente se os scripts não estiverem assinados. Para executar o script, desative temporariamente e ative novamente essa restrição para executar o script. Abra uma janela do PowerShell e use esses comandos.
>
>*`set-executionpolicy unrestricted`* - para remover temporariamente as restrições.
>
>*`set-executionpolicy restricted`* - para reabilitar a restrição após a execução do script.

```
# Remove the new custom shells.

$ShellLauncherClass.RemoveCustomShell($Admins_SID)

$ShellLauncherClass.RemoveCustomShell($Cashier_SID)
```

### Usar o controle remoto do Screens {#using-remote-control}

O AEM Screens oferece a funcionalidade de Controle remoto. Saiba mais sobre este recurso aqui: [Controle Remoto do Screens](implementing-remote-control.md)