---
title: Suporte a miniaturas para vídeos no AEM Screens
description: Saiba como adicionar Suporte a miniaturas para vídeos no AEM Screens.
exl-id: d2d87807-1699-47e3-b241-07c5b7e56f15
TQID: https://experienceleague.adobe.com/VlgvGuLabotRAwprPRl4UFIAycPi7M1oqz47nQZIpVU
product_v2: id: a27b4747-2f72-4fb7-9936-be5d11dd2c4aid: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554
source-git-commit: 0b0bfcd803c3da9298122200a0a1715fc2d5e49c
workflow-type: tm+mt
source-wordcount: 396
ht-degree: 2%

---

# Suporte a miniaturas para vídeos {#thumbnail-support-videos}

## Introdução {#introduction}

Um Autor de conteúdo pode definir uma miniatura de vídeos para que a imagem seja usada como um espaço reservado. Ele pode testar adequadamente a reprodução e o direcionamento do conteúdo, enquanto a equipe apropriada finaliza o vídeo real. A imagem também pode ser usada caso a reprodução do vídeo falhe.

A adição de suporte para uma imagem em miniatura no componente de vídeo permite que o cliente adicione corretamente um componente válido no canal, com conteúdo real, e execute qualquer configuração de direcionamento antes da entrega do vídeo.

>[!NOTE]
>A imagem em miniatura, se definida no componente de vídeo, é reproduzida se houver falha de reprodução no reprodutor de vídeo. Esse fallback permite enviar a mensagem desejada para o público-alvo (reproduzindo o conteúdo) em vez de ignorá-la completamente.

O suporte a miniaturas permite:

* Prepare uma experiência de canal quando os vídeos ainda não estiverem prontos ou quando você não quiser necessariamente testar um download de um grande ativo nos reprodutores

* Defina um mecanismo de fallback, caso haja problemas de reprodução no dispositivo.

## Utilização de miniaturas em vídeos {#using-thumbnails}

Siga as etapas abaixo para usar uma miniatura em vídeos:

1. Navegue até um canal do AEM Screens existente ou crie um canal.

1. Clique no canal e em **Editar** na barra de ações.

   ![imagem](/help/user-guide/assets/thumbnails/thumbnail-1.png)

1. Adicione ou edite um componente de vídeo existente, como mostrado na figura abaixo.

   ![imagem](/help/user-guide/assets/thumbnails/thumbnail-2.png)

1. Clique no vídeo e clique na *chave inglesa*.

   ![imagem](/help/user-guide/assets/thumbnails/thumbnail-3.png)

1. A caixa de diálogo **Vídeo** é aberta, onde você pode exibir a zona de destino **Miniatura**.

   ![imagem](/help/user-guide/assets/thumbnails/thumbnail-4.png)

1. Arraste e solte uma imagem do seletor de ativos na zona de destino **Miniatura** e clique em **Concluído**.

   ![imagem](/help/user-guide/assets/thumbnails/thumbnail-5.png)

1. Clique em **Visualizar**.

1. Se um vídeo estiver definido no componente, ele será reproduzido. Caso contrário, e a miniatura estiver definida, a miniatura será reproduzida. Caso contrário, o componente será considerado não configurado e será ignorado.

## Casos de uso compatíveis ao usar a miniatura em vídeos {#understand-use-case}

A miniatura em vídeos oferece suporte aos seguintes casos de uso:

* Um componente de vídeo sem nada configurado é ignorado.

* Um componente de vídeo com apenas o conjunto de miniaturas reproduz a miniatura.

* Um componente de vídeo com o vídeo (se o vídeo tiver a representação correta) e o conjunto de miniaturas reproduz o vídeo.

* Um componente de vídeo com o conjunto de vídeos reproduz a miniatura, se houver um erro de reprodução, ou salta para o próximo item, caso a miniatura não esteja configurada.
