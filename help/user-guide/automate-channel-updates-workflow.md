---
title: Usar o fluxo de trabalho para automatizar atualizações de ativos em um canal do AEM Screens
seo-title: Use workflow to automate asset updates for an AEM Screens channel
description: Saiba como criar um fluxo de trabalho para processar automaticamente ativos carregados no Adobe Experience Manager e atribuí-los dinamicamente a um canal do Screens. Neste exemplo, quando uma imagem é adicionada a uma pasta específica, um fluxo de trabalho é acionado, aplicando uma marca d'água dinâmica e atribuindo a imagem a um canal do Screens. As lições aprendidas com este exemplo podem ser aplicadas a uma grande variedade de cenários de automação.
seo-description: Learn how to create a workflow to automatically process assets uploaded to Adobe Experience Manager and dynamically assign them to a Screens channel. In this example when an image is added to a specific folder, a workflow is triggered that applies a dynamic watermark and assigns the image to a Screens channel. Lessons learned from this example can be applied to a wide variety of automation scenarios.
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: developing
feature: Developing Screens
role: Developer
level: Intermediate
source-git-commit: 8d1633dab9e70ea988516cf9ee4d1b0a780bc7e9
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 5%

---


# Usar o fluxo de trabalho para automatizar atualizações de ativos em um canal do AEM Screens {#automate-channel-updates-workflow}

Saiba como criar um fluxo de trabalho para processar automaticamente ativos carregados no Adobe Experience Manager e atribuí-los dinamicamente a um canal do Screens. Neste exemplo, quando uma imagem é adicionada a uma pasta específica, um fluxo de trabalho é acionado, aplicando uma sobreposição de texto dinâmica (processo de marca d&#39;água) e atribuindo a imagem a um canal do Screens. As lições aprendidas com este exemplo podem ser aplicadas a uma grande variedade de cenários de automação.

## Pré-requisitos {#prerequisites}

Para concluir este tutorial, é necessário o seguinte:

1. [AEM 6.5](https://experienceleague.adobe.com/docs/experience-manager-65.html?lang=pt-BR)
1. [AEM Service Pack 8 ou superior](https://experienceleague.adobe.com/docs/experience-manager-65/release-notes/service-pack/sp-release-notes.html?lang=pt-BR)
1. [AEM 6.5 Screens FP7 ou superior](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/release-notes/release-notes-fp-202103.html?lang=pt-BR)

## Configuração rápida {#quick-setup}

O vídeo abaixo ilustra como instalar um pacote de código de amostra que introduzirá um novo fluxo de trabalho no Adobe Experience Manager. Esse recurso permite que um usuário atualize as propriedades de uma pasta no AEM Assets para apontar para um canal do Screens. Sempre que uma imagem for adicionada a essa pasta, ela será adicionada ao canal de telas especificado.

>[!VIDEO](https://video.tv.adobe.com/v/333174/?quality=12&learn=on)

1. Baixe o pacote de código compilado: **[screens-demo.all-2.0.0-SNAPSHOT.zip](./assets/screens-demo.all-2.0.0-SNAPSHOT.zip)**
1. Instale o pacote acima usando o Gerenciador de pacotes AEM.

## Modelo de fluxo de trabalho {#workflow-model}

Um esquema de metadados de pasta personalizado foi criado para capturar o canal do Screens de destino ao qual as imagens devem ser adicionadas. Dois modelos de fluxo de trabalho são usados para automatizar o processamento de ativos. A variável **Ativo de atualização DAM** o workflow foi modificado para chamar um workflow personalizado, **Processamento de ativos de demonstração do Screens** que inspecionará a pasta que contém o ativo para determinar o canal do Screens de destino. A variável **Processamento de ativos de demonstração do Screens** O workflow também é responsável pela aplicação da marca d&#39;água à imagem.

>[!VIDEO](https://video.tv.adobe.com/v/333175/?quality=12&learn=on)

## Etapas personalizadas do processo de fluxo de trabalho {#workflow-process-step}

Duas etapas personalizadas do processo de fluxo de trabalho do Inspect usadas como parte da **Processamento de ativos de demonstração do Screens** fluxo de trabalho.

>[!VIDEO](https://video.tv.adobe.com/v/333179/?quality=12&learn=on)

`AssetProcessingCheck.java` é um processo de fluxo de trabalho personalizado que executa uma verificação na carga do fluxo de trabalho para determinar se a carga é um ativo e se a pasta que contém os dados está configurada para apontar para um canal do Screens. Se os requisitos forem atendidos, a etapa do processo manterá duas propriedades, `screen-channel` e `asset-path`, aos metadados do fluxo de trabalho.

`AddAssetToChannel.java` é uma etapa do processo de fluxo de trabalho personalizada que inspeciona os metadados do fluxo de trabalho e atualiza o canal do Screens para fazer referência à imagem.

1. Baixe o código-fonte: **[screens-demo-main.zip](./assets/screens-demo-main.zip)**
1. Descompacte e visualize o código usando seu IDE favorito.
