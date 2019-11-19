---
title: Configuração e solução de problemas da reprodução de vídeo
seo-title: Solução de problemas de vídeos
description: null
seo-description: Siga esta página para saber como solucionar problemas de vídeos. Ao carregar um vídeo no DAM e adicioná-lo ao seu canal, você pode encontrar problemas que o vídeo pode não ser reproduzido no Screens player e esta seção descreve como depurar e solucionar problemas de reprodução de vídeo no seu canal.
uuid: 825b2440-5626-40d5-8c93-7689c24474d4
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: troubleshoot
discoiquuid: 65ecc6f1-ba0e-443f-85a1-ac19f9a52c2c
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# Configuração e solução de problemas da reprodução de vídeo {#video-playback-configuration-and-troubleshooting}

Ao carregar um vídeo no DAM e adicioná-lo ao seu canal, você pode encontrar problemas que podem não ser reproduzidos no player do Screens.

As seções a seguir descrevem como depurar e solucionar problemas de reprodução de vídeo em seu canal.

## Representações de DAM {#dam-renditions}

Depois de fazer upload do vídeo para o canal, o AEM deve começar a criar algumas execuções para ele. Você pode exibir seus vídeos em Ativos.

Para exibir o vídeo:

1. Navegue até o vídeo, por exemplo `http://localhost:4502/assets.html/content/dam/we-retail/en/videos`.
1. Clique no vídeo, expanda o menu superior esquerdo e clique em **Representações**.

Deve haver representações diferentes (um MP4 ou M4V).

Se não houver renderização, verifique se você tem ffmpeg instalado no SO em que o AEM está sendo executado.

>[!CAUTION]
>
>Se não houver renderização, verifique se você tem ffmpeg instalado no SO em que o AEM está sendo executado.
>
>Clique [aqui](https://evermeet.cx/ffmpeg/) para instalar o ffmpeg.

## Ativos de vídeo {#video-assets}

Se você não vir um atributo de origem em vídeo, pode ser que o vídeo não tenha sido transcodificado. Se o vídeo for corretamente transcodificado, ele aparecerá no painel, como mostrado na figura abaixo.

Verifique se ffmpeg está instalado e os perfis de vídeo.

![chlimage_1-2](assets/chlimage_1-2.png)

### Verificando o perfil de vídeo {#checking-video-profile}

1. Navegue até Perfil **de** vídeo, ou seja, `http://localhost:4502/etc/dam/video.html` e clique em **Carregar vídeo** de teste.

   ![chlimage_1-3](assets/chlimage_1-3.png)

1. Carregue um vídeo de teste e clique em **Ok **para começar a transcodificação.

   Se a transcodificação falhar, expanda a saída ffmpeg para entender quaisquer erros na saída do console de ffmpeg.

   ![chlimage_1-4](assets/chlimage_1-4.png)

   Além disso, se a transcodificação de vídeo tiver êxito, é possível baixar o arquivo transcodificado.

   ![chlimage_1-5](assets/chlimage_1-5.png)

   >[!NOTE]
   >
   >Certifique-se de dar tempo suficiente para que o vídeo transcodifique (ele deve mostrar a tag new em vez de processar) antes de adicioná-lo a qualquer canal.

### Como verificar o perfil com um componente de vídeo {#checking-profile-with-a-video-component}

Verifique a lista de perfis do design da página se o componente de vídeo não está configurado corretamente.

1. Navegue até o canal e selecione o modo **Design** .

   ![chlimage_1-6](assets/chlimage_1-6.png)

1. Selecione o vídeo e abra a caixa de diálogo **Editar** . Open the **Profiles** tab.

   Selecione perfis diferentes (pelo menos o perfil "H.264" de alta qualidade deve estar presente).

   ![chlimage_1-7](assets/chlimage_1-7.png)

### Como verificar o vídeo no Web Player {#checking-the-video-in-the-web-player}

Use o **Web Player** `http://localhost:4502/content/mobileapps/cq-screens-player/firmware.html/content/screens/we-retail/locations/demo/flagship/single/device0` para validar a reprodução em navegadores (Chrome e Safari). O Chrome é usado em dispositivos Android, enquanto o Safari é o navegador OSX e iOS.

Se o vídeo não for executado no Safari, ele não será executado nos players OSX e iOS. Este é provavelmente um problema de codificação e o vídeo deve ser recodificado.

Siga estas etapas para usar um fluxo de trabalho DAM para criar execuções FullHD:

1. Navegue até o administrador *do modelo de* fluxo de trabalho, ou seja, `http://localhost:4502/libs/cq/workflow/admin/console/content/models.html/etc/workflow/models`.
1. Selecione o modelo **Screens Update Asset** .
1. clique em **Iniciar fluxo de trabalho** na barra de ações para abrir a caixa de diálogo **Executar fluxo de trabalho** .

1. Selecione seu ativo de vídeo na **Carga**.
1. Clique em **Executar**.

>[!NOTE]
>
>Aguarde algum tempo para criar as execuções, mas após alguns segundos/minutos (dependendo do tamanho do vídeo), recarregue o Web player no Safari.

#### Sinalizador de Política de Execução Automática {#troubleshooting-autoplay-policy-flag}

Caso o reprodutor do AEM Screens capture o vídeo, mas não o exiba, é necessário solucionar o problema do sinalizador de Política de reprodução automática.

Siga as etapas abaixo para solucionar o problema de sinalização da política de reprodução automática do google:

1. Navegue até ***chrome://flags/#autoplay-policy***
1. Alterar a política **de reprodução** automática de **Padrão** para **nenhum gesto de usuário é necessário**

1. Reinicie o navegador da Web e atualize o player

>[!NOTE]
>
>Para saber mais sobre as práticas recomendadas para boas experiências de usuário com as novas políticas de reprodução automática no Chrome, consulte a documentação de Alterações *na política de reprodução* automática, ou seja, `https://developers.google.com/web/updates/2017/09/autoplay-policy-changes#webaudio`.

### Sincronização de vídeo entre vários players {#syncing-video-across-multiple-players}

Para reproduzir vídeos sincronicamente em vários dispositivos, use a estratégia absoluta para a sequência da qual o vídeo faz parte.

#### Requisitos {#requirements}

* dois ou mais players idênticos
* hardware idealmente semelhante
* topologia de rede idêntica (os players estão conectados a um servidor NTP que alinha seus relógios internos do sistema)

#### Configuração da estratégia absoluta {#setting-up-the-absolute-strategy}

A estratégia absoluta:

* calcula um tempo de ancoragem (meia-noite do dia atual)
* calcula a duração da sequência (soma da duração de todos os seus itens)
* a qualquer momento, calcula qual item deve ser reproduzido no momento e o próximo item, solucionando a sequência _remain_time = (current_time - anchor_time) % sequence_duration.

Siga as etapas abaixo para configurar uma estratégia absoluta:

1. Navegue até o autor do canal e selecione o componente de sequência, conforme mostrado na figura abaixo.
1. Abra a caixa de diálogo de configuração.
1. Edite a **Estratégia** e adicione absoluto.

![chlimage_1-8](assets/chlimage_1-8.png)

>[!NOTE]
>
>O SO dos players deve ter o mesmo relógio.

**Alinhamento de blocos no OS X** Siga as etapas abaixo para alinhar os relógios no OSX:

1. Abrir preferências de **data e hora** em cada caixa OSX
1. Verificar** Definir data e hora automaticamente**
1. Cole o valor 0.pool.ntp.org, 1.pool.ntp.org, 2.pool.ntp.org, 3.pool.ntp.org, time.apple.com na lista suspensa ou simplesmente execute *sudo ntpdate -u -v 0.pool.ntp.org*
1. Iniciar mais de 2 players

Pode levar algum tempo até que os players iniciem uma nova sequência alinhada.

