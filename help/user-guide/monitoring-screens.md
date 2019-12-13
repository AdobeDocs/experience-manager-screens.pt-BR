---
title: Solução de problemas do Device Control Center
seo-title: Telas de monitoramento
description: Siga esta página para monitorar e solucionar problemas de desempenho para a atividade e o dispositivo do player do Screens usando o painel Dispositivo.
seo-description: Siga esta página para monitorar e solucionar problemas de desempenho para a atividade e o dispositivo do player do Screens usando o painel Dispositivo.
uuid: b6895d5d-c743-4e10-a166-de573e122335
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: troubleshoot
discoiquuid: 3f130808-71e8-4710-8181-021d953660f8
docset: aem65
translation-type: tm+mt
source-git-commit: 209a9a833957d9a8bb7c7ec70ff421514f5b974c

---


# Solução de problemas do Device Control Center {#troubleshooting-device-control-center}

Você pode monitorar e solucionar problemas de desempenho para a atividade e o dispositivo do player do Screens usando o painel Dispositivo. Esta página fornece informações sobre como monitorar e solucionar problemas de desempenho percebidos no player do Screens e nos dispositivos atribuídos.

## Monitor e solução de problemas do Device Control Center {#monitor-and-troubleshoot-from-device-control-center}

Você pode monitorar a atividade e, portanto, solucionar problemas do player do Screens, usando o painel Dispositivo.

### Painel do dispositivo {#device-dashboard}

Siga as etapas abaixo para navegar até o painel do dispositivo:

1. Navigate to the device dashboard from your project, for example, ***Test Project*** --&gt; ***Devices***.

   Select **Devices** and **Device Manager** from the action bar.

   ![screen_shot_2019-09-03at13823pm](assets/screen_shot_2019-09-03at13823pm.png)

1. A lista exibe os dispositivos atribuídos e não atribuídos, como mostrado na figura abaixo.

   ![screen_shot_2019-09-05at12823pm](assets/screen_shot_2019-09-05at12823pm.png)

1. Selecione o dispositivo (**NewTestDevice**) e clique em **Painel** na barra de ação.

   ![screen_shot_2019-09-05at13341pm](assets/screen_shot_2019-09-05at13341pm.png)

1. A página mostra as informações, a atividade e os detalhes do dispositivo que permitem monitorar as atividades e as funções do dispositivo.

   ![screen_shot_2019-09-05at13700pm](assets/screen_shot_2019-09-05at13700pm.png)

### Monitorar atividade do dispositivo {#monitor-device-activity}

O painel **Atividade** mostra o último ping do player de sua tela com o carimbo de data e hora. O último ping corresponde à última vez que o dispositivo entrou em contato com o servidor.

![chlimage_1](assets/chlimage_1.png)

Além disso, clique em **Coletar registros** no canto superior direito do painel **Atividade** para exibir os registros do player.

### Atualizar detalhes do dispositivo {#update-device-details}

Verifique o painel Detalhes **do** dispositivo para exibir o IP do dispositivo, o uso do armazenamento, a versão do firmware e o tempo de funcionamento do player do dispositivo.

![chlimage_1-1](assets/chlimage_1-1.png)

Além disso, clique em **Limpar cache** e em **Atualizar** para limpar o cache do dispositivo e atualizar a versão do [firmware](screens-glossary.md) , respectivamente, deste painel.

**Além disso, clique no**... no canto superior direito do painel Detalhes **do** dispositivo para reiniciar ou atualizar o status do player.

![chlimage_1-2](assets/chlimage_1-2.png)

### Atualizar informações do dispositivo {#update-device-information}

Verifique o painel INFORMAÇÕES **** DO DISPOSITIVO para exibir a atualização da configuração, o modelo do dispositivo, o SO do dispositivo e as informações do shell.

![screen_shot_2019-09-05at13853pm](assets/screen_shot_2019-09-05at13853pm.png)

Além disso, clique em (**...**) no canto superior direito do painel Informações do dispositivo para exibir as propriedades ou atualizar o dispositivo.

![screen_shot_2019-09-05at14017pm](assets/screen_shot_2019-09-05at14017pm.png)

Clique em **Propriedades** para exibir a caixa de diálogo Propriedades **do** dispositivo. Você pode editar o título do dispositivo ou escolher a opção para atualizações de configuração como **Manual** ou **Automático**.

>[!NOTE]
>
>Para saber mais sobre os eventos associados às atualizações automáticas ou manuais do dispositivo, consulte a seção Atualizações ***automáticas versus manuais no painel*** Dispositivo em [Gerenciamento de canais](managing-channels.md).

![screen_shot_2019-09-05at14112pm](assets/screen_shot_2019-09-05at14112pm.png)

### Exibir captura de tela do player {#view-player-screenshot}

Você pode exibir a captura de tela do player do dispositivo no painel **PLAYER SCREENSHOT** .

Clique (**...**) no canto superior direito do painel Captura de tela do player e selecione **Atualizar captura de tela** para exibir o instantâneo do player em execução.

![screen_shot_2019-09-05at14205pm](assets/screen_shot_2019-09-05at14205pm.png)

### Gerenciar preferências {#manage-preferences}

O painel **PREFERÊNCIAS** permite que o usuário altere as preferências da interface do usuário **** do administrador, do comutador **de** canal e da depuração **** remota do dispositivo.

>[!NOTE]
>
>Para saber mais sobre essa opção, consulte [AEM Screens Player](working-with-screens-player.md).

![screen_shot_2019-09-05at14250pm](assets/screen_shot_2019-09-05at14250pm.png)

Além disso, clique em **Configurações** no canto superior direito para atualizar as preferências do dispositivo. Você pode atualizar as seguintes preferências:

* **URL do servidor**
* **Resolução**
* **Reinicializar agendamento**
* **Nº máx. dos arquivos de log a serem mantidos**
* **Nível de registro**

![screen_shot_2019-09-05at14511pm](assets/screen_shot_2019-09-05at14511pm.png)

>[!NOTE]
>
>Você pode selecionar qualquer um dos seguintes níveis de Log:
>
>* **Desativar**
>* **Depurar**
>* **Informações**
>* **Aviso**
>* **Erro**
>



![screen_shot_2019-09-05at15645pm](assets/screen_shot_2019-09-05at15645pm.png)

## Solução de problemas de configurações OSGI {#troubleshoot-osgi-settings}

É necessário ativar o referenciador vazio para permitir que o dispositivo publique dados no servidor. Por exemplo, se a propriedade de referenciador vazia estiver desativada, o dispositivo não poderá postar uma captura de tela novamente.

Atualmente, alguns desses recursos só estão disponíveis se o Filtro de referência do *Apache Sling Permitir vazio* estiver ativado na configuração do OSGI. O painel pode exibir um aviso de que as configurações de segurança podem impedir que alguns desses recursos funcionem.

Siga as etapas abaixo para ativar o Filtro de referência Apache Sling que permite vazio

1. Navegue até Configuração **do console da Web do** Adobe Experience Manager, ou seja, `https://localhost:4502/system/console/configMgr/org.apache.sling.security.impl.ReferrerFilter`.
1. Verifique a opção **allow.empty** .
1. Clique em **Salvar**.

![chlimage_1-3](assets/chlimage_1-3.png)

### Recomendações {#recommendations}

A seção a seguir recomenda o monitoramento dos links de rede, do servidor e dos players para entender a integridade e reagir a problemas.

O AEM fornece monitoramento integrado para:

* *Heartbeat* a cada 5 segundos para indicar que o AEM Screens Player está em operação.
* *Captura de tela* do Player que mostra o que está sendo exibido no momento no Player.
* A versão *AEM Screens Player Firmware* instalada no Player.
* *Espaço* de armazenamento livre no Player.

Recomendações para monitoramento remoto com software de terceiros:

* Uso da CPU em Players.
* Verifique se o processo do AEM Screens Player está em execução.
* Reinicialização/reinicialização remota do Player.
* Notificações em tempo real.

É recomendável implantar o hardware do Player e o SO de uma forma que permita o logon remoto para diagnosticar problemas e reiniciar o Player.

#### Additional Resources {#additional-resources}

Consulte Configuração e solução de problemas [da reprodução de](troubleshoot-videos.md) vídeo para depurar e solucionar problemas de vídeos reproduzidos em seu canal.
