---
title: Tizen Player
description: Esta página descreve a instalação e o funcionamento do Tizen Player.
feature: Administração de telas, players
role: Administrator
level: Intermediate
source-git-commit: e955838d33cbe74719b237e568fb0bfd1a6844a2
workflow-type: tm+mt
source-wordcount: '1209'
ht-degree: 1%

---


# Implementação do Tizen Player {#tizen-player}

## Instalar o Tizen Player {#installing-tizen-player}

Siga as etapas abaixo para implementar o Tizen Player no AEM Screens:

1. Navegue até a página [AEM Screens Player Downloads](https://download.macromedia.com/screens/) para baixar o Tizen Player.

1. Instale o arquivo Tizen player *(.zip)* do computador local.

## Configuração do servidor local e extração de arquivos Zip {#setting-local-server}

>[!NOTE]
> Extraia o arquivo zip e disponibilize o reprodutor Tizen por meio de um `http server`. (O `http server` não precisa ser um servidor Local ou Apache).

Siga as etapas abaixo:

1. Copie os dois arquivos extraídos, como `AEMScreensPlayer.wgt` e `sssp_config.xml`, para o diretório raiz do servidor Web Apache local.

   >[!NOTE]
   >O `AEMScreensPlayer.wgt`é o aplicativo real do player Tizen e `sssp_config.xml` contém informações sobre esse mapa que ajudam a instalá-lo no dispositivo Tizen.

1. Obtenha o IP ou o URL do seu servidor HTTP local (e o caminho para a pasta que contém os arquivos extraídos na etapa 2, se extraídos para uma subpasta e não para a pasta raiz)

1. O Tizen player baixará o instalador do servidor local.

### Nomear reprodutor Tizen {#name-tizen}

Você pode atribuir um nome de dispositivo amigável ao seu player Tizen, enviando o nome do dispositivo atribuído ao Adobe Experience Manager (AEM). Esse recurso permite não apenas nomear o player Tizen, mas também atribuir facilmente o conteúdo apropriado.

Siga as etapas abaixo para configurar o nome no Tizen player:

1. Clique no botão de menu no controle remoto.
1. Navegue até **network** —> **Nome do Dispositivo** para atribuir um nome ao player.

### Configurando atualizações no dispositivo Samsung {#config-updates}

Siga as etapas abaixo no dispositivo Samsung para concluir a instalação do player do AEM Screens no dispositivo:

1. Navegue até o seu dispositivo Samsung e ative-o.

1. Clique no botão **MENU** no controle remoto do dispositivo e role para baixo até **Sistema** na barra de navegação esquerda.

1. Role para baixo e selecione a opção **Reproduzir via** e altere para **Iniciador de URL**.
   ![imagem](/help/user-guide/assets/tizen/rms-2.png)

1. Depois que o URL Launcher estiver definido, pressione o botão **Home** no seu remoto.

1. Navegue até **Configurações do Iniciador de URL**, insira o endereço IP do servidor host local e clique em **Concluído**.
   >[!NOTE]
   >O reprodutor Tizen deve ser capaz de se conectar ao servidor http.

1. O AEM Screens Player agora deve instalar e iniciar automaticamente em seu dispositivo Samsung.

   >[!NOTE]
   >O dispositivo Tizen e o servidor `http` devem ser capazes de se conectar, ou seja, o servidor deve estar acessível ao reprodutor Tizen.


## Isentando Agentes de Usuário com o Problema de Cookie SameSite {#exempting-user-agents}

>[!IMPORTANT]
>**Esta seção aplica-se ao Adobe Experience Manager (AEM) 6.5.5 a AEM 6.5.7**
>Há alguns mecanismos de navegador incompatíveis com o atributo *SameSite=None* usado no token de logon emitido pelo AEM 6.5 para AEM 6.7. Na maioria dos casos, o problema pode ser resolvido atualizando o navegador para a versão mais recente disponível. Em alguns casos, essas atualizações podem não ser possíveis, como com telas inteligentes, caixas de seleção ou outros dispositivos com mecanismos de navegação incorporados.

Siga as etapas abaixo para isentar esses clientes incompatíveis ao usar *SameSite=None*:

1. Atualize para o Adobe Experience Manager (AEM) Service Pack 6.5.7.

1. Depois AEM reiniciar, vá para `/system/console/configMgr` e procure por **Adobe Granite Token Authentication Handler**. Defina o valor do valor **SameSite** para **None**.

1. Você deve ver uma nova opção *Agentes do usuário a serem isentos do mesmo atributo do site*. Preencha isso com um regex correspondente ao(s) agente(s) do usuário que é(são) incompatível(m) com o atributo *SameSite=None* .
   >[!NOTE]
   >Consulte [SameSite=None: Clientes incompatíveis conhecidos](https://www.chromium.org/updates/same-site/incompatible-clients) para obter mais detalhes. Para o reprodutor Tizen, use o regex: `(.*)Tizen(.*)`.

1. Registre o Tizen player em sua instância AEM 6.5.5 e superior e ele deve registrar e mostrar conteúdo normalmente.

## Provisionamento remoto do Tizen Player {#remote-provisioning}

O provisionamento remoto do Tizen Player permite implantar centenas e milhares de exibições da Samsung Tizen sem muito esforço. Evita o esforço manual tedioso de configurar cada reprodutor com o URL do servidor e o código de registro em massa ou outros parâmetros e, no caso do Screens como Cloud Service para configurar o modo de nuvem e o token de nuvem.

Esse recurso permite que você configure remotamente o Tizen player e também atualize essas configurações centralmente, se necessário. Tudo o que você precisa é do servidor `HTTP` usado para hospedar o aplicativo Tizen `(wgt and xml file)` e um editor de texto para salvar o `config.json` com os parâmetros apropriados.

Verifique se você configurou o endereço do iniciador do URL no Dispositivo Tizen, ou seja, o Botão inicial —> Configurações do Iniciador do URL.
No servidor `HTTP` que hospeda o aplicativo Tizen, coloque o arquivo `config.json` no mesmo local que o arquivo `wgt`. O nome do arquivo deve ser `config.json`.
O Tizen player instalará e, na inicialização (e a cada reinicialização), verificará e aplicará as configurações no arquivo `config.json`.

### Exemplo de política JSON {#example-json}

```java
{
  "server":  "http://your-aem-instance.com:4502",
  "registrationKey": "AdobeRocks!!",
  "enableAdminUI": true,
  "enableOSD": true,
  "enableActivityUI": true
}
```

### Atributos de política e finalidade {#policy-attributes}

O quadro seguinte resume as políticas com as suas funções.

>[!NOTE]
>As configurações de política são estritamente aplicadas e não são substituídas manualmente na interface do usuário do administrador do reprodutor. Para permitir a configuração manual do reprodutor para uma política específica, não especifique a política na configuração da política, por exemplo, se você deseja permitir a configuração manual para o agendamento de reinicialização, não especifique a chave `rebootSchedule` na configuração da política. As Configurações de Política são lidas sempre que o reprodutor é recarregado.

| **Nome da política** | **Propósito** |
|---|---|
| server | O URL para o servidor do Adobe Experience Manager (AEM). |
| registrationKey | Usado para o registro em massa de dispositivos usando chave pré-compartilhada. |
| resolução | A resolução do dispositivo. |
| reotSchedule | O agendamento para reiniciar o reprodutor. |
| enableAdminUI | Ative a interface do usuário do administrador para configurar o dispositivo no site. Defina como false depois que estiver totalmente configurado e em produção. |
| enableOSD | Ative a interface do usuário do seletor de canal para que os usuários alternem os canais no dispositivo. Considere a configuração como false depois de estar totalmente configurada e em produção. |
| enableActivityUI | Ative para mostrar o progresso de atividades como download e sincronização. Ative para solução de problemas e desative assim que estiver totalmente configurado e em produção. |
| cloudMode | Defina como true se desejar que o Tizen player se conecte a telas como um serviço de nuvem. falso para se conectar ao AMS ou ao AEM do onPrem. |
| cloudToken | Token de registro para registrar-se no Screens como um Cloud Service. |


## Registrando o dispositivo Tizen no serviço de gerenciamento remoto da Samsung (RMS) {#enroll-tizen-device-rms}

Siga as etapas abaixo para inscrever o dispositivo Tizen no Samsung Remote Management Service (RMS) e configurar remotamente o URL Launcher:

>[!NOTE]
>Verifique as configurações de rede e o monitor.

1. Navegue até **Menu** -> **Rede** -> **Definições de Rede de Servidor** e prima **Enter**.

1. Navegue até Server address (Endereço do servidor) e digite o acesso MagicInfo URL e pressione **Concluído**.

1. Configure o TLS, se necessário. Navegue até a porta, selecione o número da porta no servidor e clique em **Salvar**.

1. Navegue até a guia **Dispositivo** e verifique o dispositivo que acabou de configurar. Depois que um dispositivo for encontrado, clique na caixa de seleção e selecione **Aprovar**.

   >![imagem](/help/user-guide/assets/tizen/rms-3.png)

1. Preencha as informações necessárias e selecione um grupo de dispositivos. Clique em **OK** para concluir o processo de aprovação.

   >![imagem](/help/user-guide/assets/tizen/rms-7.png)

1. Depois que o dispositivo for aprovado, ele deverá aparecer na lista Dispositivo. Clique no botão *Information* localizado na caixa do dispositivo, ou seja **i**, conforme mostrado na figura abaixo.

   >![imagem](/help/user-guide/assets/tizen/rms-6.png)

1. A caixa de diálogo de informações do dispositivo é exibida. Selecione a guia **Informações do dispositivo** e clique em **Editar**.

   >![imagem](/help/user-guide/assets/tizen/rms-5.png)

1. Edite as opções do dispositivo e selecione a guia **Setup**. Navegue até a seção **Iniciador de URL** e insira o URL que hospeda o wgt e `SSSP config file` para instalar um aplicativo `SSSP`, conforme mostrado na figura abaixo.

   ![imagem](/help/user-guide/assets/tizen/rms-9.png)

1. Clique em **Save** para que as alterações sejam exibidas na tela de exibição.

