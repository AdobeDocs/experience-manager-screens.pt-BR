---
title: Usar um fluxo de trabalho para automatizar atualizações de ativos para um canal do AEM Screens
description: Saiba como criar um fluxo de trabalho para processar automaticamente ativos carregados no Adobe Experience Manager e atribuí-los dinamicamente a um canal do Screens.
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: developing
feature: Developing Screens
role: Developer
level: Intermediate
source-git-commit: 8dde26d36847fb496aed6d4bf9732233116b5ea6
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 1%

---


# Usar um fluxo de trabalho para automatizar atualizações de ativos para um canal do AEM Screens {#automate-channel-updates-workflow}

Saiba como criar um fluxo de trabalho para processar automaticamente ativos carregados no Adobe Experience Manager e atribuí-los dinamicamente a um canal do Screens. Neste exemplo, um fluxo de trabalho é acionado quando uma imagem é adicionada a uma pasta específica. O fluxo de trabalho aplica uma sobreposição de texto dinâmica (processo de marca d&#39;água) e atribui a imagem a um canal do Screens. As lições aprendidas com este exemplo podem ser aplicadas a uma grande variedade de cenários de automação.

## Pré-requisitos {#prerequisites}

Para concluir este tutorial, é necessário o seguinte:

1. [AEM 6.5](https://experienceleague.adobe.com/en/docs/experience-manager-65)
1. [AEM Service Pack 8 ou superior](https://experienceleague.adobe.com/pt-br/docs/experience-manager-65/content/release-notes/release-notes)
1. [AEM 6.5 Screens FP7 ou superior](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/release-notes/release-notes-fp-202103)

## Configuração rápida {#quick-setup}

O vídeo abaixo ilustra como instalar um pacote de código de amostra que introduz um novo fluxo de trabalho no Adobe Experience Manager. Esse recurso permite que um usuário atualize as propriedades de uma pasta no AEM Assets para apontar para um canal do Screens. Sempre que uma imagem é adicionada a essa pasta, ela é adicionada ao canal do AEM Screens especificado.

>[!VIDEO](https://video.tv.adobe.com/v/333174/?quality=12&learn=on)

1. Baixe o pacote de código compilado: **[screens-demo.all-2.0.0-SNAPSHOT.zip](./assets/screens-demo.all-2.0.0-SNAPSHOT.zip)**
1. Instale o pacote acima usando o Gerenciador de pacotes AEM.

## Modelo de fluxo de trabalho {#workflow-model}

Um esquema de metadados de pasta personalizado foi criado para capturar o canal do Screens de destino ao qual as imagens devem ser adicionadas. Dois modelos de fluxo de trabalho são usados para automatizar o processamento de ativos. A variável **Ativo de atualização DAM** O fluxo de trabalho é editado para chamar um fluxo de trabalho personalizado, **Processamento de ativos de demonstração do Screens, que inspeciona a pasta que contém o ativo para determinar o canal do Screens de destino. A variável **Processamento de ativos de demonstração do Screens** O workflow também é responsável pela aplicação da marca d&#39;água à imagem.

>[!VIDEO](https://video.tv.adobe.com/v/333175/?quality=12&learn=on)

## Etapas personalizadas do processo de fluxo de trabalho {#workflow-process-step}

Duas etapas personalizadas do processo de fluxo de trabalho do Inspect usadas como parte da **Processamento de ativos de demonstração do Screens** fluxo de trabalho.

>[!VIDEO](https://video.tv.adobe.com/v/333179/?quality=12&learn=on)

A variável `AssetProcessingCheck.java` fluxo de trabalho personalizado é um processo que executa uma verificação na carga do fluxo de trabalho. Ele determina se a carga é um ativo e se a pasta que contém os dados está configurada para apontar para um canal do AEM Screens. Se os requisitos forem atendidos, a etapa do processo manterá duas propriedades, `screen-channel` e `asset-path`, aos metadados do fluxo de trabalho.

A variável `AddAssetToChannel.java` o fluxo de trabalho personalizado é uma etapa do processo que inspeciona os metadados do fluxo de trabalho e atualiza o canal do AEM Screens para fazer referência à imagem.

1. Baixe o código-fonte: **[screens-demo-main.zip](./assets/screens-demo-main.zip)**
1. Descompacte e visualize o código usando seu IDE favorito.
