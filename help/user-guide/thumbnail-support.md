---
title: Suporte a miniaturas para vídeos no AEM Screens
description: Esta página descreve como adicionar suporte a miniaturas para vídeos no Screens.
index: false
source-git-commit: 07b5b6159b09c0c1301a5e782dfe959d0b83a7d2
workflow-type: tm+mt
source-wordcount: '420'
ht-degree: 0%

---

# Suporte a miniaturas para vídeos {#thumbnail-support-videos}

## Introdução {#introduction}

Um autor de conteúdo pode definir uma miniatura de vídeos para que a imagem possa ser usada como um espaço reservado e testar corretamente a reprodução e o direcionamento do conteúdo, enquanto o vídeo real está sendo finalizado pela equipe apropriada. A imagem também pode ser usada caso a reprodução do vídeo falhe.

Adicionar suporte para uma imagem em miniatura no componente de vídeo permite que o cliente adicione corretamente um componente válido no canal, com conteúdo real, e execute qualquer configuração de definição de metas antes que o vídeo seja realmente entregue.

>[!NOTE]
>A imagem em miniatura, se configurada no componente de vídeo, é reproduzida em caso de falha na reprodução do vídeo no reprodutor. Isso permite fornecer a mensagem desejada ao público-alvo (reproduzindo o conteúdo) em vez de ignorá-la completamente.

O suporte a miniaturas permite:

* Prepare uma experiência de canal quando os vídeos ainda não estiverem prontos ou quando você não quiser necessariamente testar um download de ativo grande nos players

* Defina um mecanismo de fallback, caso haja problemas de reprodução no dispositivo.

## Usar miniaturas em vídeos {#using-thumbnails}

Siga as etapas abaixo para usar a miniatura em vídeos:

1. Navegue até um canal existente do Screens ou crie um novo canal.

1. Selecione o canal e clique em **Editar** na barra de ações para abrir o editor.

1. Adicione ou edite um componente de vídeo existente, conforme mostrado na figura abaixo.

1. Selecione o vídeo e clique no ícone *chave* para abrir as propriedades do vídeo.

1. A caixa de diálogo **Vídeo** é aberta, onde você visualizará a área de soltar **Miniatura**.

1. Arraste e solte uma imagem do seletor de ativos para a área de soltar **Miniatura** e clique em **Concluído**.

1. Clique em **Visualizar**.

1. Se um vídeo estiver definido no componente, ele será reproduzido. Caso contrário, e a miniatura estiver definida, a miniatura será reproduzida. Caso contrário, o componente será considerado não configurado e será ignorado.

## Casos de uso suportados ao usar miniatura em vídeos {#understand-use-case}

A miniatura em vídeos é compatível com os seguintes casos de uso:

* Um componente de vídeo sem configuração será ignorado.

* Um componente de vídeo com apenas a miniatura definida reproduzirá a miniatura.

* Um componente de vídeo com o vídeo (se o vídeo tiver a representação correta) e o conjunto de miniaturas serão reproduzidos.

* Um componente de vídeo com o conjunto de vídeos reproduzirá a miniatura, no caso de um erro de reprodução, ou será ignorado para o próximo item, caso a miniatura não esteja configurada.
