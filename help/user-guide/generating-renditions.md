---
title: Representações de vídeo
description: Saiba mais sobre como gerar representações de alta definição total para seu projeto do AEM Screens.
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 752c74d7-5d6d-4363-97ef-b96e97d2f6b1
source-git-commit: 3b44fd920dd6c98ecc0e2b45bf95b81685647c0f
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 0%

---

# Representações de vídeo {#video-renditions}

Você pode gerar representações manuais e automáticas de Full HD. A seção a seguir descreve o fluxo de trabalho para adicionar representações aos seus ativos.

## Gerando representações de alta definição total automaticamente  {#automatically-generating-full-hd-renditions}

>[!NOTE]
>
>Se as representações de vídeo do AEM Screens não forem executadas de forma ideal no dispositivo, entre em contato com o fornecedor do hardware para obter as especificações do vídeo. Isso ajuda a obter o melhor desempenho no dispositivo e, portanto, cria seu próprio perfil de vídeo personalizado, onde você fornece os parâmetros apropriados para o FFMPEG gerar sua representação. Em seguida, siga as etapas abaixo para adicionar seu perfil de vídeo personalizado à lista de perfis.
>
>Consulte também [Vídeos de solução de problemas](troubleshoot-videos.md) para depurar e solucionar problemas de reprodução de vídeo no seu canal.

Siga as etapas abaixo para gerar representações de alta definição total automaticamente:

1. Selecione o link Adobe Experience Manager (canto superior esquerdo) e selecione o ícone de martelo para que você possa selecionar **Fluxo de trabalho**.

   Selecionar **Modelos**.

   ![screen_shot_2018-02-01at123407pm](assets/screen_shot_2018-02-01at123407pm.png)

1. No gerenciamento do modelo de fluxo de trabalho, selecione **Ativo de atualização DAM** e selecione **Editar** na barra de ações.

   ![step5_-_edit_thedamupdateassetmodel](assets/step5_-_edit_thedamupdateassetmodel.png)

1. No **Ativo de atualização DAM** clique duas vezes na janela **Transcodificação FFmpeg** etapa.

   ![screen_shot_2018-02-01at124454pm](assets/screen_shot_2018-02-01at124454pm.png)

1. Selecione o **Processo** guia.
1. Insira os perfis de alta definição total na lista em **Argumentos** como a seguir:
   ***`,profile:fullhd-bp,profile:fullhd-hp`***
1. Selecionar **OK**.

   ![screen_shot_2018-02-02at103340am](assets/screen_shot_2018-02-02at103340am.png)

1. Selecionar **Salvar** na parte superior esquerda do **Ativo de atualização DAM** tela.

   ![screen_shot_2018-02-02at101830am](assets/screen_shot_2018-02-02at101830am.png)

1. Navegue até **Assets** e carregue um novo vídeo. Selecione o vídeo e abra o painel lateral Representações. Observe os dois vídeos em alta definição total.

   ![step10_-_open_thevideoasset](assets/step10_-_open_thevideoasset.png)

1. Abertura **Representações** do painel lateral.

   ![step11_-_open_therenditionssiderail](assets/step11_-_open_therenditionssiderail.png)

1. Observe duas novas execuções de alta definição total.

   ![step12_-_2_new_renditionsareaddedtothevideo](assets/step12_-_2_new_renditionsareaddedtothevideo.png)

## Gerando manualmente representações de alta definição total {#manually-generating-full-hd-renditions}

Siga as etapas abaixo para gerar representações de alta definição total manualmente:

1. Selecione o link Adobe Experience Manager (canto superior esquerdo) e selecione o ícone de martelo para que você possa selecionar ferramentas e **Fluxo de trabalho**.

   Selecionar **Modelos**.

   ![screen_shot_2018-02-01at123407pm-1](assets/screen_shot_2018-02-01at123407pm-1.png)

1. Em gerenciamento de modelo de fluxo de trabalho, selecione **Ativo de atualização do Screens** e selecione o **Iniciar fluxo de trabalho** para abrir o **Executar fluxo de trabalho** caixa de diálogo.

   ![step5_-_start_a_newscreensupdateassetworkflow](assets/step5_-_start_a_newscreensupdateassetworkflow.png)

1. Selecione o vídeo desejado na caixa **Carga** e selecione **Executar**.

   ![etapa6_-_select_thedesejredvideo](assets/step6_-_select_thedesiredvideo.png)

1. Navegue até **Assets**, faça o drill-down para o ativo e selecione-o.

   ![step7_-_open_thevideoasset](assets/step7_-_open_thevideoasset.png)

1. Abra o **Representações** painel lateral. Observe as novas execuções de alta definição total.

   ![step8_-_open_therenditionssiderail](assets/step8_-_open_therenditionssiderail.png)
