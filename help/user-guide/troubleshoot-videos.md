---
title: Configuração da reprodução de vídeo e solução de problemas
description: Saiba como depurar e solucionar problemas de reprodução de vídeo no seu canal do AEM Screens.
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: troubleshoot
feature: Channels, Interactive
role: Developer
level: Intermediate
exl-id: dfdd58b6-689b-47ca-9459-9c205f1841eb
source-git-commit: dcaaa1c7ab0a55cecce70f593ed4fded8468130b
workflow-type: tm+mt
source-wordcount: '794'
ht-degree: 0%

---

# Configuração da reprodução de vídeo e solução de problemas {#video-playback-configuration-and-troubleshooting}

Ao carregar um vídeo no DAM e adicioná-lo ao seu canal, você pode encontrar problemas em que o vídeo pode não ser reproduzido no AEM Screens Player.

As seções a seguir descrevem como depurar e solucionar problemas de reprodução de vídeo no seu canal.

## Representações DAM {#dam-renditions}

Após carregar o vídeo no canal, o AEM deve começar a criar algumas representações para ele. Você pode ver seus vídeos no Assets.

Para exibir o vídeo:

1. Navegue até o vídeo, por exemplo `http://localhost:4502/assets.html/content/dam/we-retail/en/videos`.
1. Clique no vídeo, expanda o menu superior esquerdo e clique em **Representações**.

Deve haver diferentes representações (um MP4 ou M4V).

Se não houver representação, verifique se o FFMPEG está instalado no SO em que o AEM está em execução.

>[!CAUTION]
>
>Se não houver representação, verifique se o FFMPEG está instalado no SO em que o AEM está em execução.
>
>Clique [aqui](https://www.ffmpeg.org/download.html) para instalar o FFMPEG.

## Assets de vídeo {#video-assets}

Se você não vir um atributo de origem em vídeo, pode ser que o vídeo não tenha sido transcodificado. Se o vídeo for transcodificado corretamente, ele aparecerá no painel, conforme mostrado a seguir:

Verifique se o FFMPEG está instalado e os perfis de vídeo.

![chlimage_1-2](assets/chlimage_1-2.png)

### Verificar perfil de vídeo {#checking-video-profile}

1. Navegue até o **Perfil de Vídeo**, ou seja, `http://localhost:4502/etc/dam/video.html` e clique em **Carregar Vídeo de Teste**.

   ![chlimage_1-3](assets/chlimage_1-3.png)

1. Carregue um vídeo de teste e clique em **Ok** para começar a transcodificação.

   Se o vídeo transcodificado falhar, expanda a saída FFMPEG para entender quaisquer erros na saída do console de FFMPEG.

   ![chlimage_1-4](assets/chlimage_1-4.png)

   Além disso, se a transcodificação de vídeo tiver êxito, é possível baixar o arquivo transcodificado.

   ![chlimage_1-5](assets/chlimage_1-5.png)

   >[!NOTE]
   >
   >Certifique-se de dar tempo suficiente para o vídeo transcodificar (ele deve mostrar a nova tag em vez de processar) antes de adicioná-la a qualquer canal.

### Verificação de perfil com um componente de vídeo {#checking-profile-with-a-video-component}

Verifique a lista de perfis do design da página se o componente de vídeo não estiver configurado corretamente.

1. Navegue até o seu canal e clique no modo **Design**.

   ![chlimage_1-6](assets/chlimage_1-6.png)

1. Clique no vídeo e abra a janela **Editar**. Abra a guia **Perfis**.

   >[!NOTE]
   >Clique em perfis diferentes (pelo menos o perfil &quot;H.264 de alta qualidade&quot; deve estar lá).

### Verificação do vídeo no reprodutor da Web {#checking-the-video-in-the-web-player}

Use o **Web Player** `http://localhost:4502/content/mobileapps/cq-screens-player/firmware.html/content/screens/we-retail/locations/demo/flagship/single/device0` para validar a reprodução nos navegadores (Chrome e Safari). O Chrome é usado em dispositivos Android™, enquanto o Safari é o SO X e o navegador iOS.

Se o vídeo não for executado no Safari, ele também não será executado no OS X e nos players do iOS. Esse problema provavelmente está relacionado à codificação e o vídeo deve ser codificado novamente.

Para usar um fluxo de trabalho DAM para criar representações FullHD, faça o seguinte:

1. Navegue até o *administrador do modelo de fluxo de trabalho*, que é `http://localhost:4502/libs/cq/workflow/admin/console/content/models.html/etc/workflow/models`.
1. Clique no modelo **Ativo de atualização do Screens**.
1. Clique em **Iniciar Fluxo de Trabalho** na barra de ações.
1. Na caixa de diálogo **Executar Fluxo de Trabalho**, clique no ativo de vídeo na **Carga**.
1. Clique em **Executar**.

>[!NOTE]
>
>Permita algum tempo para criar as representações, mas, após alguns segundos/minutos (dependendo do tamanho do vídeo), recarregue o reprodutor da Web no Safari.

#### Troubleshooting do Sinalizador de Política de Reprodução Automática {#troubleshooting-autoplay-policy-flag}

Caso o AEM Screens Player pegue o vídeo, mas não o exiba, solucione o problema do sinalizador de Política de reprodução automática.

Siga as etapas abaixo para solucionar o problema do sinalizador de política de reprodução automática do Google:

1. Navegue até ***chrome://flags/#autoplay-policy***
1. Alterar **Política de reprodução automática** de **Padrão** para **nenhum gesto de usuário necessário**

1. Inicie novamente seu navegador da Web e atualize o player

>[!NOTE]
>
>Para saber mais sobre as práticas recomendadas para boas experiências do usuário com as novas políticas de reprodução automática no Chrome. Consulte *Alterações na Política de Reprodução Automática* em `https://developers.google.com/web/updates/2017/09/autoplay-policy-changes#webaudio`.

### Sincronização de vídeo em vários players {#syncing-video-across-multiple-players}

Para reproduzir vídeos de forma síncrona em vários dispositivos, você deve usar a estratégia absoluta para a sequência da qual o vídeo faz parte.

#### Requisitos {#requirements}

* 2+ players idênticos
* hardware idealmente semelhante
* topologia de rede idêntica (os players são conectados a um servidor NTP que alinha seus relógios internos do sistema)

#### Como configurar a estratégia absoluta {#setting-up-the-absolute-strategy}

A estratégia absoluta:

* Calcula uma hora de âncora (meia-noite do dia atual).
* Calcula a duração da sequência (soma da duração de todos os itens).
* Em qualquer momento, ele calcula qual item deve ser reproduzido no momento e o próximo item resolvendo a sequência _remaining_time = (current_time - anchor_time) % sequence_duration.

Siga as etapas abaixo para configurar uma estratégia absoluta:

1. Navegue até o autor do canal e clique no componente de sequência, como mostrado na figura abaixo.
1. Abra a caixa de diálogo de configuração.
1. Edite a **Estratégia** e adicione absoluta.

   ![chlimage_1-8](assets/chlimage_1-8.png)

   >[!NOTE]
   >O SO dos reprodutores deve ter o mesmo relógio.

**Alinhando relógios no OS X** Siga as etapas abaixo para alinhar os relógios no OS X:

1. Abrir preferências de **Data e hora** em cada caixa do OS X
1. Verificar **Definir data e hora automaticamente**
1. Cole o valor 0.pool.ntp.org, 1.pool.ntp.org, 2.pool.ntp.org, 3.pool.ntp.org, time.apple.com na lista suspensa ou simplesmente execute o *`sudo ntpdate -u -v 0.pool.ntp.org`*
1. Iniciar os 2+ players

Pode levar algum tempo até que os jogadores iniciem uma nova sequência alinhada.
