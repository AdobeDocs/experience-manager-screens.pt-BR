---
title: Visão geral e configurações da arquitetura de representações adaptáveis
description: Saiba mais sobre a visão geral da arquitetura e as configurações no CRXDE Lite para representações adaptáveis no AEM Screens.
exl-id: 0419b9c6-3c27-4a61-84ff-a6fe697e773f
source-git-commit: 3b44fd920dd6c98ecc0e2b45bf95b81685647c0f
workflow-type: tm+mt
source-wordcount: '622'
ht-degree: 2%

---

# Representações adaptáveis: visão geral e configurações da arquitetura {#adaptive-renditions}

## Introdução {#introduction}

As representações adaptáveis permitem que os dispositivos selecionem automaticamente a melhor representação para um dispositivo com base em regras definidas pelo cliente. Os dispositivos baixam e reproduzem automaticamente a representação mais apropriada de um ativo com base nessas regras, permitindo que os clientes se concentrem apenas no design do *main* experiência.

## Objetivo {#objective}

Como um Desenvolvedor do AEM Screens, agora você pode configurar representações de ativos específicas do dispositivo para serem baixadas e reproduzidas automaticamente sem precisar criar todas as variações de conteúdo manualmente. Configure as Representações adaptáveis antes que um Autor de conteúdo possa usar esse recurso em um canal do AEM Screens.

## Visão geral da arquitetura {#architectural-overview}

As representações adaptáveis são baseadas na ideia de ter várias representações de um ativo nomeadas de acordo com uma convenção de nomenclatura específica. A decisão de reproduzir uma representação específica é tomada avaliando expressões de consulta de mídia que só podem ser resolvidas em dispositivos com os recursos esperados.

A capacidade de ter um padrão de nomenclatura de representação associado define uma regra de mapeamento de representação, como retrato ou paisagem, como mostrado na figura abaixo. Após calcular todas as expressões disponíveis, o reprodutor do Screens coleta os padrões de nomenclatura correspondentes às regras correspondentes. Os padrões são usados para encontrar as representações corretas durante a reprodução da sequência, procurando os padrões nos nomes das representações.

![imagem](/help/user-guide/assets/adaptive-renditions/adaptive-renditions.png)

## Adicionar a propriedade de mapeamento de representação ao projeto do Telas {#rendition-mapping-new}

Para ativar o recurso Representações adaptáveis, as seguintes regras de mapeamento devem estar presentes e a Configuração sensível ao contexto (CA) deve ser resolvida para canais e exibições.

>[!NOTE]
>Para saber mais sobre Configurações sensíveis a conteúdo, consulte [aqui](https://sling.apache.org/documentation/bundles/context-aware-configuration/context-aware-configuration.html).

Siga as etapas abaixo para configurar a configuração:

1. Navegue até **CRXDE Lite**. Verifique se a variável **mapeamento de representação** a configuração existe em `/conf/screens/sling:configs/rendition-mapping`, conforme mostrado na figura abaixo.

   >![imagem](/help/user-guide/assets/adaptive-renditions/mapping-rules1.png)

   >[!IMPORTANT]
   >Se você instalou o Feature Pack 202109 mais recente, **mapeamento de representação** estrutura de nó pré-preenchida em `/conf/screens/sling:configs/rendition-mapping` em CRXDE Lite. Consulte [Notas de versão do Pacote de recursos 202109](/help/user-guide/release-notes-fp-202109.md) para obter detalhes sobre o pacote de recursos mais recente.
   >Para projetos existentes, verifique se o projeto do Screens tem a **mapeamento de representação** configuração associada. Consulte [Adicionar mapeamento de representação a um projeto existente](#rendition-mapping-existing) para obter mais informações.

### Adicionar a propriedade de mapeamento de representação a um projeto existente {#rendition-mapping-existing}

1. Navegue até **CRXDE Lite**.

1. Definir explicitamente a associação de mapeamento de representação adicionando `sling:configRef` propriedade apontando para `/conf/screens` ao nó de conteúdo do projeto, conforme mostrado na figura abaixo.

   ![imagem](/help/user-guide/assets/adaptive-renditions/renditon-mapping2.png)


## Adição de regras de mapeamento de representação {#add-rendition-mapping-rules}

Siga as etapas abaixo para adicionar um nó em Mapeamento de representação:

1. Navegar até este caminho `/conf/screens/sling:configs/rendition-mapping` de **CRXDE Lite**.
1. Criar um nó em **mapeamento de representação**. Clique com o botão direito do mouse **mapeamento de representação** e selecione **Criar** > **Criar nó**, conforme mostrado na figura abaixo.

   ![imagem](/help/user-guide/assets/adaptive-renditions/add-node1.png)

1. Insira o **Nome** para sua regra de mapeamento, como **regra1** e o nó **Tipo** as **`nt:unstructured`** in **Criar nó** caixa de diálogo. Selecionar **OK**.

   ![imagem](/help/user-guide/assets/adaptive-renditions/add-node2.png)


1. Adicione a propriedade de expressão com o valor contendo a expressão de consulta.

   >[!NOTE]
   >Consulte [Uso da sintaxe de consulta de mídia](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_media_queries/Using_media_queries) para saber mais.

   Selecionar **regra1** que você criou e insira **expressão** in **Nome** e **(orientação:paisagem)** in **Valor**, conforme mostrado abaixo. Selecionar **Adicionar**.

   ![imagem](/help/user-guide/assets/adaptive-renditions/add-node3.png)

1. Adicione a propriedade pattern com o valor contendo o padrão de nomeação de representação.

   >[!NOTE]
   >O valor definido na propriedade pattern corresponde à nova representação do ativo e é selecionado se a expressão for avaliada como verdadeira.

   Para adicionar a propriedade do padrão, selecione **regra1** que você criou e insira **padrão** in **Nome** e **paisagem** in **Valor**, conforme mostrado abaixo. Selecionar **Adicionar**.

   ![imagem](/help/user-guide/assets/adaptive-renditions/add-node4.png)

1. Selecionar **Salvar tudo** e observe as propriedades no nó criado em **mapeamento de representação**.

   ![imagem](/help/user-guide/assets/adaptive-renditions/add-node5.png)

## Próximas etapas {#next-steps}

Depois de adicionar propriedades e regras de mapeamento de representação, como um Autor de conteúdo, você pode configurar os ativos. Para fazer isso, use as representações adaptáveis e migre seus dispositivos para redes grandes para usar esse recurso em seus canais do AEM Screens. Consulte [Uso de representações adaptáveis no AEM Screens](/help/user-guide/using-adaptive-renditions.md) para obter mais informações.
