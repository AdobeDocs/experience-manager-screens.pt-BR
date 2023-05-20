---
title: Suporte a miniaturas para vídeos no AEM Screens
description: Esta página descreve como adicionar suporte a miniaturas para vídeos no Screens.
exl-id: d2d87807-1699-47e3-b241-07c5b7e56f15
source-git-commit: ec58cd9171e359b451eaad7015d42b41ef1bff3f
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 2%

---

# Suporte a miniaturas para vídeos {#thumbnail-support-videos}

## Introdução {#introduction}

Um autor de conteúdo pode definir uma miniatura de vídeos para que a imagem possa ser usada como um espaço reservado e testar corretamente a reprodução e o direcionamento do conteúdo, enquanto o vídeo real está sendo finalizado pela equipe apropriada. A imagem também pode ser usada caso a reprodução do vídeo falhe.

A adição de suporte para uma imagem em miniatura no componente de vídeo permite que o cliente adicione corretamente um componente válido no canal, com conteúdo real, e execute qualquer configuração de direcionamento antes que o vídeo seja realmente entregue.

>[!NOTE]
>A imagem em miniatura, se definida no componente de vídeo, é reproduzida em caso de falha na reprodução do vídeo no reprodutor. Isso permite enviar a mensagem desejada para o público-alvo (reproduzindo o conteúdo) em vez de ignorá-la completamente.

O Suporte a miniaturas permite:

* Prepare uma experiência de canal quando os vídeos ainda não estiverem prontos ou quando você não quiser necessariamente testar um download de um grande ativo nos reprodutores

* Defina um mecanismo de fallback, caso haja problemas de reprodução no dispositivo.

## Utilização de miniaturas em vídeos {#using-thumbnails}

Siga as etapas abaixo para usar a miniatura em vídeos:

1. Navegue até um canal do Screens existente ou crie um novo canal.

1. Selecione o canal e clique em **Editar** na barra de ações para abrir o editor.

   ![imagem](/help/user-guide/assets/thumbnails/thumbnail-1.png)

1. Adicione ou edite um componente de vídeo existente, como mostrado na figura abaixo.

   ![imagem](/help/user-guide/assets/thumbnails/thumbnail-2.png)

1. Selecione o vídeo e clique no botão *chave inglesa* ícone para abrir as propriedades do vídeo.

   ![imagem](/help/user-guide/assets/thumbnails/thumbnail-3.png)

1. A variável **Vídeo** será aberta, onde você exibirá a **Miniatura** área de lançamento.

   ![imagem](/help/user-guide/assets/thumbnails/thumbnail-4.png)

1. Arraste e solte uma imagem do seletor de ativos para a **Miniatura** área designada e clique em **Concluído**.

   ![imagem](/help/user-guide/assets/thumbnails/thumbnail-5.png)

1. Clique em **Visualizar**.

1. Se um vídeo estiver definido no componente, ele será reproduzido. Caso contrário, e a miniatura estiver definida, a miniatura será reproduzida. Caso contrário, o componente será considerado não configurado e será ignorado.

## Casos de uso compatíveis ao usar a miniatura em vídeos {#understand-use-case}

A miniatura em vídeos oferece suporte aos seguintes casos de uso:

* Um componente de vídeo sem nada configurado será ignorado.

* Um componente de vídeo com apenas o conjunto de miniaturas reproduzirá a miniatura.

* Um componente de vídeo com o vídeo (se o vídeo tiver a representação correta) e o conjunto de miniaturas reproduzirá o vídeo.

* Um componente de vídeo com o conjunto de vídeos reproduzirá a miniatura, em caso de erro de reprodução, ou pulará para o próximo item, caso a miniatura não esteja configurada.
