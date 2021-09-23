---
title: Representações adaptáveis no AEM Screens
description: Esta página descreve a Visão geral da arquitetura e as configurações para representações adaptativas no AEM Screens.
index: false
source-git-commit: 884bee85c6f081cbd0969a8b51125f18e2d85413
workflow-type: tm+mt
source-wordcount: '691'
ht-degree: 1%

---


# Representações adaptativas: Visão geral e configurações da arquitetura {#adaptive-renditions}

## Introdução {#introduction}

As Representações adaptativas permitem que os dispositivos selecionem automaticamente a melhor representação para um dispositivo com base nas regras definidas pelo cliente. Os dispositivos baixarão e reproduzirão automaticamente a representação mais apropriada de um ativo com base nessas regras, permitindo que os clientes se concentrem apenas na criação da experiência *principal*.

## Objetivo {#objective}

Como desenvolvedor do AEM Screens, agora você pode configurar representações de ativos específicas do dispositivo para serem baixadas e reproduzidas automaticamente sem precisar criar todas as variações de conteúdo manualmente. Você deve configurar as Representações adaptativas antes que um autor de conteúdo possa usar esse recurso em um canal do AEM Screens.

## Visão geral da arquitetura {#architectural-overview}

As Representações adaptativas são baseadas na ideia de ter várias representações de ativos nomeadas de acordo com uma convenção de nomenclatura específica. A decisão de reproduzir uma representação específica é tomada pela avaliação de expressões de consulta de mídia que só podem ser resolvidas em dispositivos com recursos esperados.

A capacidade de ter um padrão de nomenclatura de representação associado define uma regra de mapeamento de representação, como retrato ou paisagem, conforme mostrado na figura abaixo. Depois de calcular todas as expressões disponíveis, o player do Screens coletará os padrões de nomenclatura correspondentes às regras correspondentes. Os padrões são usados para localizar as representações corretas durante a reprodução da sequência, procurando pelos padrões nos nomes das representações.

![imagem](/help/user-guide/assets/adaptive-renditions/adaptive-renditions.png)

## Adicionar propriedade de mapeamento de representação ao projeto do Screens {#rendition-mapping-new}

Para ativar o recurso Representações adaptativas, as seguintes regras de mapeamento devem estar presentes e a Configuração com reconhecimento de contexto (CA) deve ser resolvida para canais e exibições.

>[!NOTE]
>Para saber mais sobre as configurações sensíveis a conteúdo, consulte [aqui](https://sling.apache.org/documentation/bundles/context-aware-configuration/context-aware-configuration.html).

Siga as etapas abaixo para configurar a configuração:

1. Navegue até **CRXDE Lite**. Marque a opção se a configuração **rendition-mapping** existir em `/conf/screens/sling:configs/rendition-mapping`, conforme mostrado na figura abaixo.

   >![imagem](/help/user-guide/assets/adaptive-renditions/mapping-rules1.png)

   >[!IMPORTANT]
   >Se tiver instalado o Feature Pack 202109 mais recente, você verá a estrutura de nó **rendition-mapping** pré-preenchida em `/conf/screens/sling:configs/rendition-mapping` no CRXDE Lite. Consulte [Notas de versão do Feature Pack 202109](/help/user-guide/release-notes-fp-202109.md) para obter detalhes sobre o pacote de recursos mais recente.
   >Para projetos existentes, verifique se o projeto do Screens tem a configuração **rendition-mapping** associada. Consulte a seção [Adicionar mapeamento de representação a um projeto existente](#rendition-mapping-existing) para saber mais.

### Adicionar propriedade de mapeamento de representação a um projeto existente {#rendition-mapping-existing}

1. Navegue até **CRXDE Lite**.

1. Defina explicitamente a associação de mapeamento de representação adicionando a propriedade `sling:configRef` apontando `/conf/screens` para o nó de conteúdo do projeto, conforme mostrado na figura abaixo.

   ![imagem](/help/user-guide/assets/adaptive-renditions/renditon-mapping2.png)


## Configuração de autor e publicação {#setup-author-publish}

Considere as seguintes recomendações em Autor e Publicação antes de usar as Representações adaptativas:

* O mapeamento de representação tem de ser replicado manualmente.

* As representações de ativos não são replicadas por padrão. Todos os ativos relevantes precisam ser replicados manualmente.

## Adicionar regras de mapeamento de representação {#add-rendition-mapping-rules}

Siga as etapas abaixo para adicionar um nó em Mapeamento de representação:

1. Navegue até esse caminho `/conf/screens/sling:configs/rendition-mapping` de **CRXDE Lite**.

1. Crie um nó em **rendition-mapping**. Clique com o botão direito do mouse em **rendition-mapping** e clique em **Create** —> **Create Node**, conforme mostrado na figura abaixo.

   ![imagem](/help/user-guide/assets/adaptive-renditions/add-node1.png)

1. Insira o **Nome** para sua regra de mapeamento, como **rule1** e o nó **Type** como **nt:unstructured** na caixa de diálogo **Criar nó**. Clique em **OK**.

   ![imagem](/help/user-guide/assets/adaptive-renditions/add-node2.png)


1. É necessário adicionar a propriedade expression com o valor que contém a expressão query.

   >[!NOTE]
   >Consulte [Usando a sintaxe de consulta de mídia](https://developer.mozilla.org/en-US/docs/Web/CSS/Media_Queries/Using_media_queries) para saber mais.

   Clique em **rule1** que você criou e insira **expression** em **Name** e **(orientation:landscape)** em **Value**, conforme mostrado abaixo. Clique em **Adicionar**.

   ![imagem](/help/user-guide/assets/adaptive-renditions/add-node3.png)

1. Adicione a propriedade pattern com o valor que contém o padrão de nomeação de representação.

   >[!NOTE]
   >O valor definido na propriedade pattern será correspondido à nova representação do ativo e será selecionado, se a expressão for avaliada como true.

   Para adicionar a propriedade de padrão, clique em **rule1** que você criou e insira **pattern** em **Name** e **landscape** em **Value**, conforme mostrado abaixo. Clique em **Adicionar**.

   ![imagem](/help/user-guide/assets/adaptive-renditions/add-node4.png)

1. Clique em **Salvar tudo** e você verá as propriedades no nó criado em **rendition-mapping**.

   ![imagem](/help/user-guide/assets/adaptive-renditions/add-node5.png)


## Próximas etapas {#next-steps}

Depois de ter adicionado as propriedades e regras de mapeamento de representação, agora como um Autor de conteúdo, você pode configurar seus ativos para usar as Representações adaptativas e também migrar seus dispositivos para redes grandes para aproveitar esse recurso, nos canais do AEM Screens. Consulte [Usando representações adaptativas](/help/user-guide/using-adaptive-renditions.md) para obter mais detalhes.
