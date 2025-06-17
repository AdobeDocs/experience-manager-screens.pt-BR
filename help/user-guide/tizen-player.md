---
title: Jogador de tizen
description: Saiba mais sobre a instalação e o funcionamento do reprodutor Tizen.
feature: Administering Screens, Players
role: Admin
level: Intermediate
exl-id: 45147959-b0ca-4d87-b89d-293e4b9af171
source-git-commit: dcaaa1c7ab0a55cecce70f593ed4fded8468130b
workflow-type: tm+mt
source-wordcount: '1218'
ht-degree: 1%

---

# Implementação do reprodutor Tizen {#tizen-player}

## Instalação do reprodutor Tizen {#installing-tizen-player}

Siga as etapas abaixo para implementar o reprodutor Tizen para o AEM Screens:

1. Navegue até a página [Downloads do AEM Screens Player](https://download.macromedia.com/screens/) para baixar o reprodutor Tizen.

1. Instale o arquivo *(.zip)* do reprodutor Tizen do computador local.

## Configuração do servidor http {#setting-local-server}

>[!NOTE]
> Extraia o arquivo zip e disponibilize o reprodutor Tizen por meio de um `http server`. (Não é necessário que `http server` seja um servidor Local ou Apache).

Siga as etapas abaixo:

1. Copie os dois arquivos extraídos, como `AEMScreensPlayer.wgt` e `sssp_config.xml`, para o diretório raiz do seu servidor Web Apache local.

   >[!NOTE]
   >O `AEMScreensPlayer.wgt` é o aplicativo de reprodução real do Tizen e `sssp_config.xml` contém informações sobre este mapa que ajudam a instalá-lo no dispositivo Tizen.

1. Obtenha o IP ou o URL do servidor HTTP local (e o caminho para a pasta que contém os arquivos extraídos na etapa 2, se extraídos para uma subpasta e não para uma pasta raiz).

1. O reprodutor Tizen baixa o instalador do servidor local.

### Nomeação do reprodutor Tizen {#name-tizen}

Você pode atribuir um nome de dispositivo amigável ao seu reprodutor de tamanho, enviando o nome de dispositivo atribuído ao Adobe Experience Manager (AEM). Esse recurso não só permite nomear o player de dimensionamento, como também permite atribuir facilmente o conteúdo apropriado.

>[!NOTE]
>Você pode escolher o nome do Player somente antes do registro. Depois que o Player é registrado, o nome do Player não pode mais ser alterado.

Siga as etapas abaixo para configurar o nome no reprodutor Tizen:

1. Clique no botão de menu no seu controle remoto.
1. Navegue até **Rede** > **Nome do Dispositivo** para poder atribuir um nome ao reprodutor.

### Configurando atualizações no dispositivo Samsung {#config-updates}

Siga as etapas abaixo no dispositivo Samsung para concluir a instalação do AEM Screens Player no dispositivo:

1. Navegue até o dispositivo Samsung e ative-o.
1. Clique no botão **MENU** no controle remoto do dispositivo e role até **Sistema** na barra de navegação esquerda.
1. Role para baixo e clique na opção **Reproduzir por meio de** e altere para a opção **Iniciador de URL**.
   ![imagem](/help/user-guide/assets/tizen/rms-2.png)
1. Quando o Inicializador de URL estiver definido, pressione o botão **Início** no controle remoto.
1. Navegue até as **Configurações do Iniciador de URL**, digite o endereço IP do servidor de host local e clique em **Concluído**.

   >[!NOTE]
   >O reprodutor Tizen deve ser capaz de se conectar ao servidor HTTP.

1. O AEM Screens Player é automaticamente instalado e iniciado no dispositivo Samsung.

   >[!NOTE]
   >O dispositivo Tizen e o servidor `http` devem poder se conectar entre si, ou seja, o servidor deve ser acessível ao reprodutor Tizen.


## Isenção de agentes do usuário com o problema de cookie SameSite {#exempting-user-agents}

>[!IMPORTANT]
>**Esta seção se aplica ao Adobe Experience Manager (AEM) 6.5.5 a AEM 6.5.7**
>
>Alguns mecanismos de navegador são incompatíveis com o atributo *`SameSite=None`* usado no token de logon emitido pelo AEM 6.5.5 para o AEM 6.5.7. Normalmente, o problema pode ser resolvido atualizando o navegador para a versão mais recente disponível. Às vezes, essas atualizações podem não ser possíveis, como com vídeos inteligentes, decodificadores de sinais ou outros dispositivos com mecanismos de navegação incorporados.

Siga as etapas abaixo para isentar esses clientes incompatíveis ao usar *SameSite=None*:

1. Atualize para o Adobe Experience Manager (AEM) Service Pack 6.5.7.

1. Depois que o AEM for reiniciado, vá para `/system/console/configMgr` e procure por **Manipulador de autenticação de token do Adobe Granite**. Defina o valor de **SameSite** como **None**.

1. Você deve ver uma nova opção *`User agents to be exempted from samesite attribute`*. Preencha esta opção com um regex correspondente ao agente do usuário que é(são) incompatível(is) com o atributo *SameSite=None*.

   >[!NOTE]
   >
   >Consulte [SameSite=None: Clientes Incompatíveis Conhecidos](https://www.chromium.org/updates/same-site/incompatible-clients) para obter mais detalhes. Para o reprodutor Tizen, use o regex: `(.*)Tizen(.*)`.

1. Registre o reprodutor Tizen na instância do AEM 6.5.5 e superior e ele deve registrar e mostrar o conteúdo normalmente.

## Provisionamento remoto do reprodutor de tamanho {#remote-provisioning}

O provisionamento remoto do player Tizen permite implantar centenas e milhares de exibições do Samsung Tizen sem muito esforço. Ele evita o esforço manual para configurar cada player com o URL do servidor e o código de registro em massa ou outros parâmetros. E, se houver AEM Screens as a Cloud Service, para configurar o modo de nuvem e o token de nuvem.

Esse recurso permite configurar remotamente o Tizen player e também atualizar essas configurações centralmente, se necessário. Tudo o que você precisa é o servidor `HTTP` usado para hospedar o aplicativo Tizen `(wgt and xml file)` e um editor de texto para salvar o `config.json` com os parâmetros apropriados.

Verifique se você configurou o endereço do Iniciador de URL no dispositivo Tizen. Clique no botão Início > Configurações do iniciador de URL.
No servidor `HTTP` que hospeda o aplicativo Tizen, coloque o arquivo `config.json` no mesmo local do arquivo `wgt`. O nome do arquivo deve ser `config.json`.
O Tizen player instala e, na inicialização (e a cada reinicialização), verifica e aplica as configurações no arquivo `config.json`.

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
>As configurações de política da interface do administrador do reprodutor são estritamente aplicadas e não são substituídas manualmente. Para permitir a configuração manual do player para uma política específica, não especifique a política na configuração de política.
>>Por exemplo, se você deseja permitir a configuração manual para o agendamento de reinicialização, não especifique a chave `rebootSchedule` na configuração de política. As Configurações de política são lidas sempre que o reprodutor é recarregado.

| **Nome da Política** | **Finalidade** |
|---|---|
| servidor | O URL para o servidor do Adobe Experience Manager (AEM). |
| registrationKey | Usado para registro em massa de dispositivos usando chave pré-compartilhada. |
| resolução | A resolução do dispositivo. |
| rebootSchedule | O cronograma para reinicializar o reprodutor. |
| enableAdminUI | Habilite a interface do Administrador para configurar o dispositivo no site. Defina como false depois que estiver totalmente configurado e em produção. |
| enableOSD | Habilite a interface do usuário do alternador de canais para que os usuários alternem canais no dispositivo. Considere configurá-lo como falso depois que estiver totalmente configurado e em produção. |
| enableActivityUI | Ative para que possa mostrar o progresso de atividades, como download e sincronização. Ative para solução de problemas e desative depois que estiver totalmente configurado e em produção. |
| cloudMode | Defina como verdadeiro se desejar que o reprodutor Tizen se conecte ao Screens as a Cloud Service. Defina como falso para se conectar ao AMS ou à AEM no local. |
| cloudToken | Token de registro para se registrar no Screens as a Cloud Service. |


## Inscrevendo o Dispositivo de Tizen no Samsung Remote Management Service (RMS) {#enroll-tizen-device-rms}

Siga as etapas abaixo para registrar o dispositivo Tizen no Samsung Remote Management Service (RMS) e configurar remotamente o Iniciador de URL:

>[!NOTE]
>Verifique as configurações de rede e o monitor.

1. Navegue até **Menu** -> **Rede** -> **Configurações de Rede do Servidor** e pressione **Enter**.

1. Navegue até o endereço do Servidor, digite o acesso URL do MagicInfo e pressione **Concluído**.

1. Configurar TLS, se necessário. Navegue até a porta, clique no número da porta no servidor e clique em **Salvar**.

1. Navegue até a guia **Dispositivo** e verifique o dispositivo que você configurou. Quando um dispositivo for encontrado, clique na caixa de seleção e em **Aprovar**.

   >![imagem](/help/user-guide/assets/tizen/rms-3.png)

1. Preencha as informações necessárias e clique em um grupo de dispositivos. Clique em **OK**.

   >![imagem](/help/user-guide/assets/tizen/rms-7.png)

1. Quando o dispositivo for aprovado, ele aparecerá na Lista de dispositivos. Clique em *Informações* na caixa do dispositivo conforme mostrado a seguir.

   >![imagem](/help/user-guide/assets/tizen/rms-6.png)

1. A caixa de diálogo de informações do dispositivo é exibida. Clique na guia **Informações do dispositivo** e em **Editar**.

   >![imagem](/help/user-guide/assets/tizen/rms-5.png)

1. Edite as opções do dispositivo e clique na guia **Instalação**. Navegue até a seção **Iniciador de URL** e insira a URL que hospeda o wgt e o `SSSP config file` para que você possa instalar um aplicativo `SSSP`, como mostrado na figura abaixo.

   ![imagem](/help/user-guide/assets/tizen/rms-9.png)

1. Clique em **Salvar**.

### Usar o controle remoto do Screens {#using-remote-control}

O AEM Screens oferece a funcionalidade de Controle remoto. Saiba mais sobre este recurso aqui: [Controle Remoto do Screens](implementing-remote-control.md)
