---
title: Solução de problemas do Centro de controle de dispositivos
description: Saiba como monitorar e solucionar problemas de desempenho da atividade e do dispositivo do AEM Screens Player usando o painel Dispositivo.
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: troubleshoot
docset: aem65
feature: Digital Signage, Content, Players
role: Developer
level: Intermediate
exl-id: 57105d6d-51ff-44ca-bbf2-ae9cce8addd0
source-git-commit: 1cf90de7892d051b2b94b4dd57de7135269b1ee8
workflow-type: tm+mt
source-wordcount: '779'
ht-degree: 0%

---

# Solução de problemas do Centro de controle de dispositivos {#troubleshooting-device-control-center}

Você pode monitorar e solucionar problemas de desempenho da atividade e do dispositivo do AEM Screens Player usando o painel Dispositivo. Esta página fornece informações sobre como monitorar e solucionar problemas de desempenho percebidos do reprodutor do Screens e dos dispositivos atribuídos.

## Monitorar e solucionar problemas no Centro de controle de dispositivos {#monitor-and-troubleshoot-from-device-control-center}

É possível monitorar a atividade e, portanto, solucionar problemas do AEM Screens Player, usando o Painel de dispositivos.

### Painel do dispositivo {#device-dashboard}

Siga as etapas abaixo para navegar até o painel do dispositivo:

1. Navegue até o painel do dispositivo em seu projeto, por exemplo, ***Testar projeto*** > ***Dispositivos***.

   Clique em **Dispositivos** e **Gerenciador de dispositivos** na barra de ações.

   ![screen_shot_2019-09-03at13823pm](assets/screen_shot_2019-09-03at13823pm.png)

1. A lista exibe os dispositivos atribuídos e não atribuídos, como mostrado na figura abaixo.

   ![screen_shot_2019-09-05at12823pm](assets/screen_shot_2019-09-05at12823pm.png)

1. Clique no dispositivo (**NovoDispositivoDeTeste**) e clique em **Painel** na barra de ações.

   ![screen_shot_2019-09-05at13341pm](assets/screen_shot_2019-09-05at13341pm.png)

1. A página mostra as informações do dispositivo, a atividade e os detalhes do dispositivo que permitem monitorar as atividades e funções do dispositivo.

   ![screen_shot_2019-09-05at13700pm](assets/screen_shot_2019-09-05at13700pm.png)

### Monitorar atividade do dispositivo {#monitor-device-activity}

A variável **Atividade** mostra o último ping do AEM Screens Player com o carimbo de data e hora. O último ping corresponde à última vez que o dispositivo entrou em contato com o servidor.

![chlimage_1](assets/chlimage_1.png)

Além disso, clique **Coletar registros** no canto superior direito da **Atividade** para exibir os registros do reprodutor.

### Atualizar detalhes do dispositivo {#update-device-details}

Verifique a **Detalhes do dispositivo** para que você possa visualizar o IP do dispositivo, o uso do armazenamento, a versão do firmware e o tempo de atividade do player do seu dispositivo.

![chlimage_1-1](assets/chlimage_1-1.png)

Além disso, clique **Limpar cache** e **Atualizar** para limpar o cache do dispositivo e atualizar o [firmware](screens-glossary.md) desse painel.

Além disso, clique **..** no canto superior direito da **Detalhes do dispositivo** painel para reiniciar ou atualizar o status do player.

![chlimage_1-2](assets/chlimage_1-2.png)

### Atualizar informações do dispositivo {#update-device-information}

Verifique a **INFORMAÇÕES DO DISPOSITIVO** painel. Aqui você pode ver a atualização de configuração, o modelo do dispositivo, o SO do dispositivo e as informações do shell.

![screen_shot_2019-09-05at13853pm](assets/screen_shot_2019-09-05at13853pm.png)

Clique também em (**..**) no canto superior direito do painel Informações do dispositivo para exibir as propriedades ou atualizar o dispositivo.

![screen_shot_2019-09-05at14017pm](assets/screen_shot_2019-09-05at14017pm.png)

Clique em **Propriedades** para que você possa visualizar o **Propriedades do dispositivo** caixa de diálogo. Você pode editar o título do dispositivo ou escolher a opção para atualizações de configuração como **Manual** ou **Automático**.

>[!NOTE]
>
>Para saber mais sobre os eventos associados às atualizações automáticas ou manuais do dispositivo, consulte a seção ***Atualizações automáticas e manuais no painel de dispositivos*** in [Gerenciamento de canais](managing-channels.md).

![screen_shot_2019-09-05at14112pm](assets/screen_shot_2019-09-05at14112pm.png)

### Exibir captura de tela do reprodutor {#view-player-screenshot}

Você pode exibir a captura de tela do reprodutor do dispositivo na **CAPTURA DE TELA DO REPRODUTOR** painel.

Clique em (**..**) no canto superior direito do painel Captura de tela do player e clique em **Atualizar captura de tela** para ver o instantâneo do reprodutor em execução.

![screen_shot_2019-09-05at14205pm](assets/screen_shot_2019-09-05at14205pm.png)

### Gerenciar preferências {#manage-preferences}

A variável **PREFERÊNCIAS** permite que o usuário altere as preferências de **Interface do administrador**, **Alternador de canal**, e **Depuração remota** para o dispositivo.

>[!NOTE]
>Para saber mais sobre essas opções, consulte [AEM Screens Player](working-with-screens-player.md).

![screen_shot_2019-09-05at14250pm](assets/screen_shot_2019-09-05at14250pm.png)

Além disso, clique **Configurações** no canto superior direito para atualizar as preferências do dispositivo. Você pode atualizar as seguintes preferências:

* **URL do servidor**
* **Resolução**
* **Reinicializar programação**
* **Nº máx. de arquivos de log a serem mantidos**
* **Nível de registro**

![screen_shot_2019-09-05at14511pm](assets/screen_shot_2019-09-05at14511pm.png)

>[!NOTE]
>Você pode clicar em qualquer um dos seguintes níveis de Log:
>* **Desativar**
>* **Depurar**
>* **Informações**
>* **Aviso**
>* **Erro**

![screen_shot_2019-09-05at15645pm](assets/screen_shot_2019-09-05at15645pm.png)

## Solução de problemas de configurações do OSGi {#troubleshoot-osgi-settings}

Ative o referenciador vazio para permitir que o dispositivo publique dados no servidor. Por exemplo, se a propriedade referenciador vazia estiver desativada, o dispositivo não poderá postar uma captura de tela.

Atualmente, alguns desses recursos só estarão disponíveis se o *Permitir filtro de referenciador do Apache Sling vazio* está ativado na configuração do OSGi. O painel pode exibir um aviso de que as configurações de segurança podem impedir que alguns desses recursos funcionem.

Siga as etapas abaixo para ativar o Apache Sling Referrer Filter Allow Empty

1. Navegue até **Configuração do console da Web do Adobe Experience Manager**, ou seja, `https://localhost:4502/system/console/configMgr/org.apache.sling.security.impl.ReferrerFilter`.
1. Verifique a **allow.empty** opção.
1. Clique em **Salvar**.

![chlimage_1-3](assets/chlimage_1-3.png)

### Recomendações {#recommendations}

A seção a seguir recomenda monitorar os links de rede, servidores e players para entender a integridade e reagir a problemas.

O AEM fornece monitoramento integrado para:

* *Heartbeat* a cada 5 segundos para indicar que o AEM Screens Player está em operação.
* *Captura de tela* do reprodutor que mostra o que é exibido no reprodutor.
* A variável *Firmware do AEM Screens Player* está instalada no Player.
* *Espaço livre de armazenamento* no reprodutor.

Recommendations para monitoramento remoto com software de terceiros:

* Uso da CPU em Players.
* Verifique se o processo do AEM Screens Player está em execução.
* Reinicialização/reinicialização remota do Player.
* Notificações em tempo real.

É recomendável implantar o hardware e o SO do player de uma maneira que permita o logon remoto para diagnosticar problemas e reiniciar o player.

#### Outros recursos {#additional-resources}

Consulte [Configuração da reprodução de vídeo e solução de problemas](troubleshoot-videos.md) se quiser depurar e solucionar problemas de vídeos reproduzidos no seu canal.
