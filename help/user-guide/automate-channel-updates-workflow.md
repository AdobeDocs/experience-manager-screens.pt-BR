---
title: Usar fluxo de trabalho para automatizar atualizações de ativos de um canal do AEM Screens
seo-title: Usar fluxo de trabalho para automatizar atualizações de ativos de um canal do AEM Screens
description: Saiba como criar um workflow para processar automaticamente ativos carregados no Adobe Experience Manager e atribuí-los dinamicamente a um canal do Screens. Neste exemplo, quando uma imagem é adicionada a uma pasta específica, é acionado um fluxo de trabalho que aplica uma marca d'água dinâmica e atribui a imagem a um canal do Screens. As lições aprendidas com este exemplo podem ser aplicadas a uma grande variedade de cenários de automação.
seo-description: Saiba como criar um workflow para processar automaticamente ativos carregados no Adobe Experience Manager e atribuí-los dinamicamente a um canal do Screens. Neste exemplo, quando uma imagem é adicionada a uma pasta específica, é acionado um fluxo de trabalho que aplica uma marca d'água dinâmica e atribui a imagem a um canal do Screens. As lições aprendidas com este exemplo podem ser aplicadas a uma grande variedade de cenários de automação.
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: developing
feature: Desenvolvendo telas
role: Developer
level: Intermediate
translation-type: tm+mt
source-git-commit: 1667fd10f415214a5301e9740d205eb33cc34f89
workflow-type: tm+mt
source-wordcount: '533'
ht-degree: 3%

---


# Usar fluxo de trabalho para automatizar atualizações de ativos para um canal AEM Screens {#automate-channel-updates-workflow}

Saiba como criar um workflow para processar automaticamente ativos carregados no Adobe Experience Manager e atribuí-los dinamicamente a um canal do Screens. Neste exemplo, quando uma imagem é adicionada a uma pasta específica, é acionado um fluxo de trabalho que aplica uma marca d&#39;água dinâmica e atribui a imagem a um canal do Screens. As lições aprendidas com este exemplo podem ser aplicadas a uma grande variedade de cenários de automação.

## Pré-requisitos {#prerequisites}

Para concluir este tutorial, é necessário o seguinte:

1. [AEM 6.5](https://experienceleague.adobe.com/docs/experience-manager-65.html?lang=pt-BR)
1. [AEM Service Pack 8 ou superior](https://experienceleague.adobe.com/docs/experience-manager-65/release-notes/service-pack/sp-release-notes.html?lang=pt-BR)
1. [AEM 6.5 Screens FP7 ou superior](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/release-notes/release-notes-fp-202103.html)

## Configuração rápida {#quick-setup}

O vídeo abaixo ilustra como instalar um pacote de código de amostra que introduzirá um novo fluxo de trabalho ao Adobe Experience Manager. Esse recurso permite que um usuário atualize as propriedades de uma pasta no AEM Assets para apontar para um canal do Screens. Sempre que uma imagem for adicionada a essa pasta, ela será adicionada ao canal de telas especificado.

>[!VIDEO](https://video.tv.adobe.com/v/333174/?quality=12&learn=on)

1. Baixe o pacote de código compilado: **[screens-demo.all-2.0.0-SNAPSHOT.zip](./assets/screens-demo.all-2.0.0-SNAPSHOT.zip)**
1. Instale o pacote acima usando o Gerenciador de pacotes AEM.

## Modelo de fluxo de trabalho {#workflow-model}

Um esquema de metadados de pasta personalizado foi criado para capturar o canal do Screens de destino no qual as imagens devem ser adicionadas. Dois modelos de workflows são usados para automatizar o processamento de ativos. O workflow **DAM Update Asset** é modificado para chamar um workflow personalizado, **Screens Demo Asset Processing**, que inspecionará a pasta que contém o ativo para determinar o canal do Screens de destino. O workflow **Screens Demo Asset Processing** também é responsável por aplicar a marca d&#39;água à imagem.

>[!VIDEO](https://video.tv.adobe.com/v/333175/?quality=12&learn=on)

## Etapas do processo do fluxo de trabalho personalizado {#workflow-process-step}

As duas etapas do processo de fluxo de trabalho personalizado do Inspect que são usadas como parte do fluxo de trabalho **Processamento de ativo de demonstração do Screens** .

>[!VIDEO](https://video.tv.adobe.com/v/333179/?quality=12&learn=on)

`AssetProcessingCheck.java` é um processo de fluxo de trabalho personalizado que realiza uma verificação na carga do fluxo de trabalho para determinar se a carga é um ativo e se a pasta que o contém está configurada para apontar para um canal do Screens. Se os requisitos forem atendidos, a etapa do processo persistirá em duas propriedades, `screen-channel` e `asset-path`, para os metadados do fluxo de trabalho.

`AddAssetToChannel.java` é uma etapa do processo de fluxo de trabalho personalizado que inspeciona os metadados do fluxo de trabalho e atualiza o canal do Screens para fazer referência à imagem.

1. Baixe o código-fonte: **[screens-demo-main.zip](./assets/screens-demo-main.zip)**
1. Descompacte e visualize o código usando seu IDE favorito.
