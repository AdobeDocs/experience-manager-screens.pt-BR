---
title: Tizen Player
description: Esta página descreve a instalação e o funcionamento do Tizen Player.
feature: Administering Screens, Players
role: Admin
level: Intermediate
exl-id: 45147959-b0ca-4d87-b89d-293e4b9af171
source-git-commit: 1e8beb9dfaf579250138d4a41eeec88cc81f2d39
workflow-type: tm+mt
source-wordcount: '1208'
ht-degree: 1%

---

# Implementação do reprodutor de tize {#tizen-player}

## Instalar o Tizen Player {#installing-tizen-player}

Siga as etapas abaixo para implementar o Tizen Player para AEM Screens:

1. Navegue até a [Downloads do AEM Screens Player](https://download.macromedia.com/screens/) para baixar o Tizen Player.

1. Instalar o reprodutor Tizen *(.zip)* arquivo do computador local.

## Configuração do servidor http {#setting-local-server}

>[!NOTE]
> Extraia o arquivo zip e disponibilize o reprodutor Tizen por meio de um `http server`. (O `http server` não é necessário ser um servidor local ou Apache).

Siga as etapas abaixo:

1. Copie os dois arquivos extraídos, como `AEMScreensPlayer.wgt` e `sssp_config.xml` para o diretório raiz do seu servidor Web Apache local.

   >[!NOTE]
   >A variável `AEMScreensPlayer.wgt`é o aplicativo do reprodutor Tizen real e `sssp_config.xml` contém informações sobre este mapa que ajudam a instalá-lo no dispositivo Tizen.

1. Obtenha o IP ou o URL do servidor HTTP local (e o caminho para a pasta que contém os arquivos extraídos na etapa 2, se extraídos para uma subpasta e não para a pasta raiz).

1. O reprodutor Tizen baixa o instalador do servidor local.

### Nomeação do reprodutor de tamanho {#name-tizen}

Você pode atribuir um nome de dispositivo amigável ao seu reprodutor de Tizen, enviando o nome de dispositivo atribuído ao Adobe Experience Manager (AEM). Esse recurso não só permite nomear o player de dimensionamento, como também permite atribuir facilmente o conteúdo apropriado.

>[!NOTE]
>Você pode escolher o nome do Player somente antes do registro. Depois que o Player é registrado, o nome do Player não pode mais ser alterado.

Siga as etapas abaixo para configurar o nome no reprodutor Tizen:

1. Clique no botão de menu no seu controle remoto.
1. Navegue até **rede** > **Nome do dispositivo** para que você possa atribuir um nome ao reprodutor.

### Configurando atualizações no dispositivo Samsung {#config-updates}

Siga as etapas abaixo no dispositivo Samsung para concluir a instalação do reprodutor AEM Screens no dispositivo:

1. Navegue até o dispositivo Samsung e ative-o.
1. Clique em **MENU** do dispositivo remoto e role para baixo até **Sistema** na barra de navegação esquerda.
1. Role para baixo e selecione o **Reproduzir via** e altere para **Iniciador de URL** opção.
   ![imagem](/help/user-guide/assets/tizen/rms-2.png)
1. Depois que o Iniciador de URL estiver definido, pressione a tecla **Início** do controle remoto.
1. Navegue até a **Configurações do inicializador de URL** e digite o endereço IP do servidor de host local e clique em **Concluído**.

   >[!NOTE]
   >O reprodutor Tizen deve ser capaz de se conectar ao servidor http.

1. O AEM Screens Player é automaticamente instalado e iniciado no dispositivo Samsung.

   >[!NOTE]
   >Tanto o dispositivo Tizen quanto o `http` O servidor deve ser capaz de se conectar entre si, ou seja, o servidor deve ser acessível ao reprodutor Tizen.


## Isenção de agentes do usuário com o problema de cookie SameSite {#exempting-user-agents}

>[!IMPORTANT]
>**Esta seção se aplica ao Adobe Experience Manager (AEM) 6.5.5 ao AEM 6.5.7**
>
>Há alguns mecanismos de navegador incompatíveis com o *`SameSite=None`* atributo usado no token de logon emitido pelo AEM 6.5.5 para AEM 6.5.7. Normalmente, o problema pode ser resolvido atualizando o navegador para a versão mais recente disponível. Às vezes, essas atualizações podem não ser possíveis, como com vídeos inteligentes, decodificadores de sinais ou outros dispositivos com mecanismos de navegação incorporados.

Siga as etapas abaixo para isentar esses clientes incompatíveis ao usar *SameSite=None*:

1. Atualize para o Adobe Experience Manager (AEM) Service Pack 6.5.7.

1. Depois que o AEM for reiniciado, vá para `/system/console/configMgr` e pesquisar **Manipulador de autenticação de token do Adobe Granite**. Defina o valor para o **SameSite** valor para **Nenhum**.

1. Você deve ver uma nova opção *`User agents to be exempted from samesite attribute`*. Preencha com um regex correspondente ao agente do usuário que é incompatível com o *SameSite=None* atributo.

   >[!NOTE]
   >
   >Consulte [SameSite=None: Clientes Incompatíveis conhecidos](https://www.chromium.org/updates/same-site/incompatible-clients) para obter mais detalhes. Para o reprodutor Tizen, use o regex: `(.*)Tizen(.*)`.

1. Registre o reprodutor Tizen no AEM instância 6.5.5 e superior e ele deve registrar e mostrar o conteúdo normalmente.

## Provisionamento remoto do reprodutor de tamanho {#remote-provisioning}

O provisionamento remoto do Tizen Player permite implantar centenas e milhares de exibições do Samsung Tizen sem muito esforço. Ele evita o esforço manual para configurar cada player com o URL do servidor e o código de registro em massa ou outros parâmetros. E, se houver AEM Screens as a Cloud Service, para configurar o modo de nuvem e o token de nuvem.

Esse recurso permite configurar remotamente o Tizen player e também atualizar essas configurações centralmente, se necessário. Tudo o que você precisa é a `HTTP` servidor usado para hospedar o aplicativo Tizen `(wgt and xml file)` e um editor de texto para salvar a `config.json` com os parâmetros adequados.

Certifique-se de ter configurado o endereço do iniciador de URL no Dispositivo de digitalização, ou seja, Botão inicial > Configurações do iniciador de URL.
No `HTTP` servidor que hospeda o aplicativo Tizen, coloque o arquivo `config.json` no mesmo local da variável `wgt` arquivo. O nome do arquivo deve ser `config.json`.
O Tizen player instala o e, na inicialização (e a cada reinicialização), verifica e aplica as configurações no `config.json` arquivo.

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

### Atributos e Finalidade da Política {#policy-attributes}

A tabela a seguir resume as políticas com suas funções.

>[!NOTE]
>As configurações de política são estritamente aplicadas e não são substituídas manualmente na interface do administrador do reprodutor. Para permitir a configuração manual do player para uma política específica, não especifique a política na configuração de política.
>Por exemplo, se você quiser permitir a configuração manual para a programação de reinicialização, não especifique a chave `rebootSchedule` na configuração de política. As Configurações de política são lidas sempre que o reprodutor é recarregado.

| **Nome da política** | **Finalidade** |
|---|---|
| servidor | O URL para o servidor Adobe Experience Manager (AEM). |
| registrationKey | Usado para registro em massa de dispositivos usando chave pré-compartilhada. |
| resolução | A resolução do dispositivo. |
| rebootSchedule | O cronograma para reinicializar o reprodutor. |
| enableAdminUI | Habilite a interface do Administrador para configurar o dispositivo no site. Defina como false depois que estiver totalmente configurado e em produção. |
| enableOSD | Habilite a interface do alternador de canal para que os usuários alternem canais no dispositivo. Considere definir como false depois que estiver totalmente configurado e em produção. |
| enableActivityUI | Habilite para que você possa mostrar o progresso de atividades como download e sincronização. Ative para solução de problemas e desative depois que estiver totalmente configurado e em produção. |
| cloudMode | Defina como verdadeiro se desejar que o reprodutor Tizen se conecte ao Screens as a Cloud Service. Defina como falso para se conectar ao AMS ou AEM no local. |
| cloudToken | Token de registro para se registrar no Screens as a Cloud Service. |


## Inscrevendo o Dispositivo de Tizen no Samsung Remote Management Service (RMS) {#enroll-tizen-device-rms}

Siga as etapas abaixo para registrar o dispositivo Tizen no Samsung Remote Management Service (RMS) e configurar remotamente o Iniciador de URL:

>[!NOTE]
>Verifique as configurações de rede e o monitor.

1. Navegue até **Menu** -> **Rede** -> **Configurações de rede do servidor** e pressione **Enter**.

1. Navegue até Endereço do servidor, digite o acesso URL do MagicInfo e pressione **Concluído**.

1. Configurar TLS, se necessário. Navegue até a porta, selecione o número da porta no servidor e selecione **Salvar**.

1. Navegue até a **Dispositivo** e verifique o dispositivo que você configurou. Quando um dispositivo for encontrado, marque a caixa de seleção e selecione **Aprovar**.

   >![imagem](/help/user-guide/assets/tizen/rms-3.png)

1. Preencha as informações necessárias e selecione um grupo de dispositivos. Selecionar **OK**.

   >![imagem](/help/user-guide/assets/tizen/rms-7.png)

1. Quando o dispositivo for aprovado, ele aparecerá na Lista de dispositivos. Selecionar *Informações* na caixa do dispositivo conforme mostrado a seguir.

   >![imagem](/help/user-guide/assets/tizen/rms-6.png)

1. A caixa de diálogo de informações do dispositivo é exibida. Selecione o **Informações do dispositivo** e selecione **Editar**.

   >![imagem](/help/user-guide/assets/tizen/rms-5.png)

1. Edite as opções do dispositivo e selecione o **Configuração** guia. Navegue até **Iniciador de URL** e insira o URL que hospeda o wgt e `SSSP config file` para que você possa instalar um `SSSP` conforme mostrado na figura abaixo.

   ![imagem](/help/user-guide/assets/tizen/rms-9.png)

1. Selecione **Salvar**.

### Uso do controle remoto do Screens {#using-remote-control}

O AEM Screens oferece a funcionalidade de Controle remoto. Saiba mais sobre esse recurso aqui: [Controle remoto do Screens](implementing-remote-control.md)
