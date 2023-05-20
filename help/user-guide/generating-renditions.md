---
title: Representações de vídeo
seo-title: Video Renditions
description: Siga esta página para saber mais sobre como gerar representações de alta definição total para o seu projeto do Screens.
seo-description: Follow this page to learn about generating full HD renditions for your Screens project.
uuid: 0a3b009e-8a97-4396-ad47-97077fe26cde
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: 40a182fd-7772-4ef7-b4fd-29ef99390b4a
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 752c74d7-5d6d-4363-97ef-b96e97d2f6b1
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 0%

---

# Representações de vídeo {#video-renditions}

Você pode gerar representações manuais e automáticas de Full HD. A seção a seguir descreve o fluxo de trabalho para adicionar representações aos seus ativos.

## Gerando representações de alta definição total automaticamente  {#automatically-generating-full-hd-renditions}

>[!NOTE]
>
>Se as representações de vídeo do AEM Screens não forem executadas de forma ideal no dispositivo, entre em contato com o fornecedor do hardware para obter as especificações do vídeo. Isso ajudará a obter o melhor desempenho no dispositivo e, portanto, criar seu próprio perfil de vídeo personalizado, onde você fornece os parâmetros apropriados para o FFMPEG gerar sua representação. Posteriormente, use as etapas abaixo para adicionar seu perfil de vídeo personalizado à lista de perfis.
>
>Além disso, consulte [Vídeos de solução de problemas](troubleshoot-videos.md) para depurar e solucionar problemas de reprodução de vídeo no seu canal.

Siga as etapas abaixo para gerar representações de alta definição total automaticamente:

1. Selecione o link Adobe Experience Manager (parte superior esquerda) e clique no ícone de martelo para selecionar ferramentas **Fluxo de trabalho**.

   Clique em **Modelos** para inserir o gerenciamento de modelos de workflow.

   ![screen_shot_2018-02-01at123407pm](assets/screen_shot_2018-02-01at123407pm.png)

1. Selecione o **Ativo de atualização DAM** e clique em Editar na barra de ações para abrir a variável **Ativo de atualização DAM** janela.

   ![step5_-_edit_thedamupdateassetmodel](assets/step5_-_edit_thedamupdateassetmodel.png)

1. Clique duas vezes no ícone **Transcodificação FFmpeg** etapa.

   ![screen_shot_2018-02-01at124454pm](assets/screen_shot_2018-02-01at124454pm.png)

1. Selecione o **Processo** para editar os argumentos do processo. Insira os perfis de alta definição total na lista em **Argumentos** como: ***,profile:fullhd-bp,profile:fullhd-hp*** e clique em **OK**.

   ![screen_shot_2018-02-02at103340am](assets/screen_shot_2018-02-02at103340am.png)

1. Clique em **Salvar** na parte superior esquerda do **Ativo de atualização DAM** tela.

   ![screen_shot_2018-02-02at101830am](assets/screen_shot_2018-02-02at101830am.png)

1. Navegue até **Assets** e carregue um novo vídeo. Clique no vídeo e abra o painel lateral Representações e você notará os dois vídeos em alta definição total.

   ![step10_-_open_thevideoasset](assets/step10_-_open_thevideoasset.png)

1. Abertura **Representações** do painel lateral.

   ![step11_-_open_therenditionssiderail](assets/step11_-_open_therenditionssiderail.png)

1. Você observará duas novas execuções de alta definição total.

   ![step12_-_2_new_renditionsareaddedtothevideo](assets/step12_-_2_new_renditionsareaddedtothevideo.png)

## Gerando manualmente representações de alta definição total {#manually-generating-full-hd-renditions}

Siga as etapas abaixo para gerar representações de alta definição total manualmente:

1. Selecione o link Adobe Experience Manager (parte superior esquerda) e clique no ícone de martelo para selecionar ferramentas **Fluxo de trabalho**.

   Clique em **Modelos** para inserir o gerenciamento de modelos de workflow.

   ![screen_shot_2018-02-01at123407pm-1](assets/screen_shot_2018-02-01at123407pm-1.png)

1. Selecione o **Ativo de atualização do Screens** e clique no link **Iniciar fluxo de trabalho** para abrir o **Executar fluxo de trabalho** caixa de diálogo.

   ![step5_-_start_a_newscreensupdateassetworkflow](assets/step5_-_start_a_newscreensupdateassetworkflow.png)

1. Selecione o vídeo desejado na caixa **Carga** e clique em **Executar**.

   ![etapa6_-_select_thedesejredvideo](assets/step6_-_select_thedesiredvideo.png)

1. Navegue até **Assets**, faça drill-down para o ativo e clique nele.

   ![step7_-_open_thevideoasset](assets/step7_-_open_thevideoasset.png)

1. Abra o **Representações** painel lateral e você notará as novas execuções de alta definição total.

   ![step8_-_open_therenditionssiderail](assets/step8_-_open_therenditionssiderail.png)
