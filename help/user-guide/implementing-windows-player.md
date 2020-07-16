---
title: Implementação do Windows 10 Player
seo-title: Implementação do Windows 10 Player
description: Siga esta página para saber mais sobre como configurar o AEM Screens Windows 10 player.
seo-description: Siga esta página para saber mais sobre como configurar o AEM Screens Windows 10 player.
uuid: da7e88bf-c251-481e-9029-f8fc4768b309
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
content-type: reference
discoiquuid: 4228e8a1-9749-49a6-a1bb-365492bc2a3d
docset: aem65
translation-type: tm+mt
source-git-commit: db3429d93833ec22ba60732c45da274830692b39
workflow-type: tm+mt
source-wordcount: '878'
ht-degree: 0%

---


# Implementação do Windows 10 Player {#implementing-windows-player}

Esta seção descreve como configurar o AEM Screens Windows 10 player. Ele fornece informações sobre o arquivo de configuração e as opções disponíveis e recomendações sobre quais configurações usar para desenvolvimento e teste.

## Instalação do Windows Player {#installing-windows-player}

Para implementar o Windows Player para AEM Screens, instale o Windows Player para AEM Screens.

Visite a página Downloads [****](https://download.macromedia.com/screens/)do AEM 6.5 Player.

### Método ad-hoc {#ad-hoc-method}

O método Ad-Hoc permite instalar o Windows Player mais recente (*.exe*). Visite a página Downloads [****](https://download.macromedia.com/screens/)do AEM 6.5 Player.

Depois de baixar o aplicativo, siga as etapas no player para concluir a instalação ad-hoc:

1. Pressione longamente no canto superior esquerdo para abrir o painel admin.
1. Navegue até **Configuração** no menu de ação esquerdo e digite o local (endereço) da instância do AEM à qual você deseja se conectar e clique em **Salvar**.
1. Navegue até o link **Device** **Registration** no menu de ação esquerdo para verificar o status do processo de registro do dispositivo.

>[!NOTE]
>
>Se o **Estado** for **REGISTRADO**, você observará que o campo ID **do** dispositivo será preenchido.
>
>Se o **estado** for **NÃO REGISTRADO**, você poderá usar o **token** para registrar o dispositivo.

### Configuração do servidor em massa: Registrando vários Players do Windows 10 com uma configuração {#bulk-server-configuration-registering-multiple-windows-players-with-one-configuration}

Depois de instalar o Windows player, você pode registrar vários players com uma configuração.

>[!NOTE]
>
>**Registro em massa do Windows Player**
>
>Ao implementar o Windows player, não é necessário configurar manualmente cada player. Em vez disso, você pode atualizar o arquivo JSON de configuração depois que ele for testado e estiver pronto para implantação.
>
>A configuração garantirá que todos os players que executam ping no mesmo servidor sejam fornecidos no arquivo de configuração. Você ainda deve registrar cada player manualmente.

Siga as etapas abaixo para configurar o Windows 10 Player:

1. Instale o Windows Player.
1. Localize o arquivo de configuração em ***%appdata%\com.adobe.aem.screens.player\config.json***.
1. Atualize o JSON de configuração usando as informações abaixo e copie a mesma pasta para todos os sistemas em que o player reside.

### Atributos de política {#policy-attributes}

A tabela a seguir resume os atributos de política com um exemplo de política JSON para referência:

| **Nome da política** | **Propósito** |
|---|---|
| server | O URL para o servidor Adobe Experience Manager (AEM). |
| resolução | A resolução do dispositivo. |
| rebootSchedule | O cronograma para reinicializar o player. |
| enableAdminUI | Ative a interface de usuário do administrador para configurar o dispositivo no site. Definido como falso depois que estiver totalmente configurado e em produção. |
| enableOSD | Ative a interface do comutador de canais para que os usuários alternem canais no dispositivo. Considere a configuração como false depois de estar totalmente configurada e em produção. |
| enableActivityUI | Ative para mostrar o progresso de atividades como download e sincronização. Ative para solução de problemas e desabilite-o assim que estiver totalmente configurado e em produção. |

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

Quando você estiver implantando o Windows player, é importante ativar um modo de quiosque para que outros aplicativos ou a barra de tarefas não apareçam na área de trabalho do Windows.

>[!CAUTION]
>
>A Adobe recomenda uma solução de gerenciamento de dispositivos para habilitar o Kiosk para Windows. Siga as etapas abaixo se você não tiver uma solução de gerenciamento de dispositivos para ativar o modo Kiosk. Este método usa o recurso Shell Launcher disponível nas empresas Windows 10 e Edu. Qualquer outro meio recomendado pela Microsoft para aplicativos que não sejam de UWP também pode ser aplicado para ativar o Kiosk, especialmente em outras edições do Windows.

Siga as etapas abaixo para ativar o modo Kiosk:

>[!NOTE]
>
>Antes de seguir as etapas abaixo, certifique-se de usar o Windows 10 Enterprise ou Education.

1. Ative o Shell Launcher.

   Consulte a seção ***Configurar o Shell Launcher*** na página do **[Shell Launcher](https://docs.microsoft.com/en-us/windows-hardware/customize/enterprise/shell-launcher)**pelo suporte do Microsoft Windows para obter mais informações.

1. Crie um usuário não administrativo (se você já não tiver um) para ser usado para o Kiosk. Pode ser um usuário local ou de domínio.
1. Instale o Windows player para esse usuário do Kiosk na página Downloads [do](https://download.macromedia.com/screens/) AEM Screens Player.
1. Consulte [Usar o Shell Launcher para criar um quiosque](https://docs.microsoft.com/en-us/windows/configuration/kiosk-shelllauncher) do Windows 10 para modificar o script do PowerShell para obter mais informações.

   Modifique o script do PowerShell para substituir o nome de usuário pelo que você criou. Verifique se o caminho para o executável do aplicativo está correto. Isso definirá o shell personalizado como o aplicativo do Windows player para o usuário do quiosque e o padrão como explorer.exe para outros usuários.

1. Execute o script do PowerShell como administrador.
1. Reinicialize e faça login como o usuário do Kiosk e o aplicativo do player devem ser start imediatamente.

### Resolução de Problemas{#troubleshooting}

Se você receber uma tela preta ao fazer login como usuário do Kiosk, isso significa que você pode ter especificado incorretamente o caminho para o executável do Windows player. Faça logon novamente como administrador e verifique e execute novamente o script.

O caminho de instalação padrão do Windows player é:

***C:\Users\&amp;lt;your user>\AppData\Local\Programs\@aem-screensscreensscreens-player-eletron\AEM Screens Player.exe***

O script de amostra nos links ativará e desativará o shell personalizado. Portanto, talvez seja necessário dividir o script em duas e ativar/desativar as linhas aplicáveis abaixo:

>[!NOTE]
>
>Em alguns ambientes do Windows, os scripts do PowerShell podem ser restritos por política (especialmente scripts não assinados). Para executar o script, talvez seja necessário desativar e reativar temporariamente essa restrição para executar o script. Abra uma janela do PowerShell e use esses comandos.
>
>*set-Executionpolicy sem restrições* - para remover temporariamente restrições
>
>*set-Executionpolicy restricted* - para reativar a restrição após executar o script

```
# Remove the new custom shells.

$ShellLauncherClass.RemoveCustomShell($Admins_SID)

$ShellLauncherClass.RemoveCustomShell($Cashier_SID)
```

