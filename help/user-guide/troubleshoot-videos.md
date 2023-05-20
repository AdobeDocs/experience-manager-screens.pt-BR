---
title: Configuração da reprodução de vídeo e solução de problemas
seo-title: Troubleshooting Videos
description: Siga esta página para saber como depurar e solucionar problemas da reprodução de vídeo no seu canal.
seo-description: Follow this page to learn how to troubleshoot videos. When you upload a video to the DAM and add it your channel, you might encounter issues that video might not play in Screens player and this section describes how to debug and troubleshoot video playing in your channel.
uuid: 825b2440-5626-40d5-8c93-7689c24474d4
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: troubleshoot
discoiquuid: 65ecc6f1-ba0e-443f-85a1-ac19f9a52c2c
feature: Channels, Interactive
role: Developer
level: Intermediate
exl-id: dfdd58b6-689b-47ca-9459-9c205f1841eb
source-git-commit: 707833ddd8ab2573abcac4e9a77ec88778624435
workflow-type: tm+mt
source-wordcount: '794'
ht-degree: 0%

---

# Configuração da reprodução de vídeo e solução de problemas {#video-playback-configuration-and-troubleshooting}

Ao carregar um vídeo no DAM e adicioná-lo ao seu canal, você pode encontrar problemas em que o vídeo pode não ser reproduzido no reprodutor do Screens.

As seções a seguir descrevem como depurar e solucionar problemas de reprodução de vídeo no seu canal.

## Representações DAM {#dam-renditions}

Depois de carregar o vídeo no canal, o AEM deve começar a criar algumas representações para ele. Você pode ver seus vídeos em Ativos.

Para exibir o vídeo:

1. Navegue até o vídeo, por exemplo `http://localhost:4502/assets.html/content/dam/we-retail/en/videos`.
1. Clique no vídeo, expanda o menu superior esquerdo e clique em **Representações**.

Deve haver representações diferentes (um MP4 ou M4V).

Se não houver representação, verifique se o ffmpeg está instalado no SO em que o AEM está em execução.

>[!CAUTION]
>
>Se não houver representação, verifique se o ffmpeg está instalado no SO em que o AEM está em execução.
>
>Clique em [aqui](https://www.ffmpeg.org/download.html) para instalar o ffmpeg.

## Ativos de vídeo {#video-assets}

Se você não vir um atributo de origem em vídeo, pode ser que o vídeo não tenha sido transcodificado. Se o vídeo for corretamente transcodificado, ele aparecerá no painel, como mostrado na figura abaixo.

Verifique se o ffmpeg está instalado e os perfis de vídeo.

![chlimage_1-2](assets/chlimage_1-2.png)

### Verificar perfil de vídeo {#checking-video-profile}

1. Navegue até a **Perfil de vídeo**, ou seja, `http://localhost:4502/etc/dam/video.html` e clique em **Carregar vídeo de teste**.

   ![chlimage_1-3](assets/chlimage_1-3.png)

1. Carregue um vídeo de teste e clique em **Ok** para iniciar a transcodificação.

   Se o transcode falhar, expanda a saída ffmpeg para entender quaisquer erros na saída do console do ffmpeg.

   ![chlimage_1-4](assets/chlimage_1-4.png)

   Além disso, se a transcodificação de vídeo tiver êxito, é possível baixar o arquivo transcodificado.

   ![chlimage_1-5](assets/chlimage_1-5.png)

   >[!NOTE]
   >
   >Certifique-se de dar tempo suficiente para o vídeo transcodificar (ele deve mostrar a tag nova em vez de processar) antes de adicioná-la a qualquer canal.

### Verificação de perfil com um componente de vídeo {#checking-profile-with-a-video-component}

Verifique a lista de perfis do design da página se o componente de vídeo não estiver configurado corretamente.

1. Navegue até o canal e selecione a **Design** modo.

   ![chlimage_1-6](assets/chlimage_1-6.png)

1. Selecione o vídeo e abra a janela **Editar** diálogo. Abra o **Perfis** guia.

   >[!NOTE]
   >Selecione perfis diferentes (pelo menos o perfil &quot;H.264 de alta qualidade&quot; deve estar lá).

### Verificação do vídeo no reprodutor da Web {#checking-the-video-in-the-web-player}

Use o **Web Player** `http://localhost:4502/content/mobileapps/cq-screens-player/firmware.html/content/screens/we-retail/locations/demo/flagship/single/device0` para validar a reprodução em navegadores (Chrome e Safari). O Chrome é usado em dispositivos Android, enquanto o Safari é o navegador OSX e iOS.

Se o vídeo não for executado no Safari, ele não será executado nos players OSX e iOS. Isso provavelmente é um problema de codificação e o vídeo deve ser codificado novamente.

Siga estas etapas para usar um fluxo de trabalho DAM para criar representações FullHD:

1. Navegue até a *administrador do modelo de fluxo de trabalho*, ou seja, `http://localhost:4502/libs/cq/workflow/admin/console/content/models.html/etc/workflow/models`.
1. Selecione o **Ativo de atualização do Screens** modelo.
1. click **Iniciar fluxo de trabalho** na barra de ações para abrir a variável **Executar fluxo de trabalho** caixa de diálogo.

1. Selecione o ativo de vídeo na **Carga**.
1. Clique em **Executar**.

>[!NOTE]
>
>Permita algum tempo para criar as representações, mas, após alguns segundos/minutos (dependendo do tamanho do vídeo), recarregue o reprodutor da Web no Safari.

#### Troubleshooting do Sinalizador de Política de Reprodução Automática {#troubleshooting-autoplay-policy-flag}

Caso o reprodutor do AEM Screens pegue o vídeo, mas não o exiba, é necessário solucionar problemas do sinalizador de Política de reprodução automática.

Siga as etapas abaixo para solucionar problemas do sinalizador de política de reprodução automática do Google:

1. Navegue até ***chrome://flags/#autoplay-policy***
1. Alterar **Política de reprodução automática** de **Padrão** para **nenhum gesto do usuário é necessário**

1. Inicie novamente seu navegador da Web e atualize o reprodutor

>[!NOTE]
>
>Para saber mais sobre as práticas recomendadas para boas experiências do usuário com as novas políticas de reprodução automática no Chrome, consulte a documentação para *Alterações na política de reprodução automática*, ou seja, `https://developers.google.com/web/updates/2017/09/autoplay-policy-changes#webaudio`.

### Sincronização de vídeo em vários players {#syncing-video-across-multiple-players}

Para reproduzir vídeos de forma síncrona em vários dispositivos, você deve usar a estratégia absoluta para a sequência da qual o vídeo faz parte.

#### Requisitos {#requirements}

* 2+ players idênticos
* hardware idealmente semelhante
* topologia de rede idêntica (os players são conectados a um servidor NTP que alinha seus relógios internos do sistema)

#### Como configurar a estratégia absoluta {#setting-up-the-absolute-strategy}

A estratégia absoluta:

* calcula uma hora de âncora (meia-noite do dia atual)
* calcula a duração da sequência (soma da duração de todos os itens)
* em qualquer momento, ele calcula qual item deve ser reproduzido no momento e o próximo item resolvendo a sequência _remaining_time = (current_time - anchor_time) % sequence_duration.

Siga as etapas abaixo para configurar uma estratégia absoluta:

1. Navegue até o autor do canal e selecione o componente de sequência, como mostrado na figura abaixo.
1. Abra a caixa de diálogo de configuração.
1. Edite o **Estratégia** e adicione absoluto.

   ![chlimage_1-8](assets/chlimage_1-8.png)

   >[!NOTE]
   >O SO dos reprodutores deve ter o mesmo relógio.

**Alinhamento de relógios no OS X** Siga as etapas abaixo para alinhar os relógios no OSX:

1. Abertura **Data e hora** preferências em cada caixa OSX
1. Marcar **Definir data e hora automaticamente**
1. Cole o valor 0.pool.ntp.org, 1.pool.ntp.org, 2.pool.ntp.org, 3.pool.ntp.org, time.apple.com na lista suspensa ou simplesmente execute *sudo ntpdate -u -v 0.pool.ntp.org*
1. Iniciar os 2+ players

Pode levar algum tempo até que os jogadores iniciem uma nova sequência alinhada.
