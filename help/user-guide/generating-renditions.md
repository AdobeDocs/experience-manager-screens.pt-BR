---
title: Representações de vídeo
seo-title: Representações de vídeo
description: Siga esta página para saber como gerar representações em full HD para seu projeto do Screens.
seo-description: Siga esta página para saber como gerar representações em full HD para seu projeto do Screens.
uuid: 0a3b009e-8a97-4396-ad47-97077fe26cde
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: 40a182fd-7772-4ef7-b4fd-29ef99390b4a
translation-type: tm+mt
source-git-commit: 209a9a833957d9a8bb7c7ec70ff421514f5b974c

---


# Representações de vídeo {#video-renditions}

Você pode gerar representações em Full HD manuais e automáticas. A seção a seguir descreve o fluxo de trabalho para adicionar representações aos seus ativos.

## Geração automática de representações em Full HD  {#automatically-generating-full-hd-renditions}

>[!NOTE]
>
>Caso as representações de vídeo do AEM Screens não sejam reproduzidas de maneira ideal no seu dispositivo, entre em contato com o fornecedor de hardware para obter as especificações do vídeo. Isso ajudará a obter o melhor desempenho no dispositivo e, portanto, criar seu próprio perfil de vídeo personalizado, fornecendo os parâmetros apropriados para o FFMPEG gerar sua representação. Em seguida, use as etapas abaixo para adicionar seu perfil de vídeo personalizado à lista de perfis.
>
>Além disso, consulte [Solução de problemas de vídeo](troubleshoot-videos.md) para depurar e solucionar problemas de reprodução de vídeo no seu canal.

Siga as etapas abaixo para gerar automaticamente as representação em Full HD:

1. Selecione o link do Adobe Experience Manager (canto superior esquerdo) e clique no ícone de martelo para selecionar ferramentas e escolha **Fluxo de trabalho**.

   Click **Models** to enter the workflow models management.

   ![screen_shot_2018-02-01at123407pm](assets/screen_shot_2018-02-01at123407pm.png)

1. Select the **DAM Update Asset** model and click Edit from the action bar to open the **DAM Update Asset** window.

   ![step5_-_edit_thedamupdateassetmodel](assets/step5_-_edit_thedamupdateassetmodel.png)

1. Clique duas vezes na etapa **Transcodificação de FFmpeg**.

   ![screen_shot_2018-02-01at124454pm](assets/screen_shot_2018-02-01at124454pm.png)

1. Selecione a guia **Processo** para editar os argumentos do processo. Enter the full HD profiles to the list in **Arguments** as: ***,profile:fullhd-bp,profile:fullhd-hp*** and click **OK**.

   ![screen_shot_2018-02-02at103340am](assets/screen_shot_2018-02-02at103340am.png)

1. Clique em **Salvar** no canto superior esquerdo da tela **Ativo de atualização DAM**.

   ![screen_shot_2018-02-02at101830am](assets/screen_shot_2018-02-02at101830am.png)

1. Navegue até **Assets** e faça o upload de um novo vídeo. Clique no vídeo e abra o painel lateral Representações e você notará os dois vídeos em HD completos.

   ![step10_-_open_thevideoasset](assets/step10_-_open_thevideoasset.png)

1. Open **Renditions** from the side rail.

   ![step11_-_open_therenditionssiderail](assets/step11_-_open_therenditionssiderail.png)

1. Você notará duas novas renderizações em full HD.

   ![step12_-_2_new_renditionsareaddedtothevideo](assets/step12_-_2_new_renditionsareaddedtothevideo.png)

## Geração manual de representações em Full HD {#manually-generating-full-hd-renditions}

Siga as etapas abaixo para gerar manualmente as representação em Full HD:

1. Selecione o link do Adobe Experience Manager (canto superior esquerdo) e clique no ícone de martelo para selecionar ferramentas e escolha **Fluxo de trabalho**.

   Click **Models** to enter the workflow models management.

   ![screen_shot_2018-02-01at123407pm-1](assets/screen_shot_2018-02-01at123407pm-1.png)

1. Select the **Screens Update Asset** model, and click the **Start Workflow** to open the **Run Workflow** dialog box.

   ![step5_-_start_a_newscreensupdateassetworkflow](assets/step5_-_start_a_newscreensupdateassetworkflow.png)

1. Select the desired video in the **Payload** and click **Run**.

   ![step6_select_thedeiredvideo](assets/step6_-_select_thedesiredvideo.png)

1. Navegue até **Assets**, faça um detalhamento até o seu ativo e clique nele.

   ![step7_-_open_thevideoasset](assets/step7_-_open_thevideoasset.png)

1. Abra o painel lateral **Representações**. Você perceberá as novas representações em full HD.

   ![step8_-_open_therenditionssiderail](assets/step8_-_open_therenditionssiderail.png)

