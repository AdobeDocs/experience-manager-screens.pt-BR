---
title: Representações adaptáveis no AEM Screens
description: Esta página descreve a Visão geral da arquitetura e as configurações para representações adaptativas no AEM Screens.
index: false
source-git-commit: 75f7cf722880bb0a1f35ac663308cf049cd4fd20
workflow-type: tm+mt
source-wordcount: '710'
ht-degree: 1%

---


# Representações adaptativas: Visão geral e configurações da arquitetura {#adaptive-renditions}

## Introdução {#introduction}

As Representações adaptativas permitem que os dispositivos selecionem automaticamente a melhor representação para um dispositivo com base nas regras definidas pelo cliente. Os dispositivos baixarão e reproduzirão automaticamente a representação mais apropriada de um ativo com base nessas regras, permitindo que os clientes se concentrem apenas na criação da experiência *principal*.

## Objetivo {#objective}

Como desenvolvedor do AEM Screens, agora você pode configurar representações de ativos específicas do dispositivo para serem baixadas e reproduzidas automaticamente sem precisar criar todas as variações de conteúdo manualmente. Você deve configurar as representações adaptativas antes que um Autor de conteúdo possa usar esse recurso em um canal do AEM Screens.

Portanto, se você implantou vários dispositivos, o uso desse recurso permitirá que o dispositivo baixe e reproduza automaticamente a representação mais apropriada de um ativo com base nas regras.

## Visão geral da arquitetura {#architectural-overview}

As Representações adaptativas são baseadas na ideia de ter várias representações de ativos nomeadas de acordo com uma convenção de nomenclatura específica. A decisão de reproduzir uma representação específica é tomada pela avaliação de expressões de consulta de mídia que só podem ser resolvidas em dispositivos com recursos esperados. A capacidade de ter um padrão de nomenclatura de representação associado define uma regra de mapeamento de representação. Depois de calcular todas as expressões disponíveis, o player do Screens coletará os padrões de nomenclatura correspondentes às regras correspondentes. Os padrões são usados para localizar as representações corretas durante a reprodução da sequência, procurando pelos padrões nos nomes das representações.

![imagem](/help/user-guide/assets/adaptive-renditions/adaptive-renditions.png)

## Configuração para usar representações adaptativas {#setup-adaptive-renditions}

Para ativar o recurso Representações adaptativas, as regras de mapeamento devem estar presentes e a configuração da CA pode ser resolvida para canais e é exibida:

1. Verifique se a configuração de mapeamento de representação existe em `JCR`. Todos os pacotes de recursos mais recentes têm essa estrutura de nós pré-preenchida.

   >[!NOTE]
   >Todos os pacotes de recursos mais recentes têm essa estrutura de nós pré-preenchida.

   ![imagem](/help/user-guide/assets/adaptive-renditions/mapping-rules1.png)

1. Certifique-se de que o projeto do Screens tenha a configuração de mapeamento de representação associada a ele.

   * Cada novo projeto criado com o assistente do projeto do Screens conterá uma referência que aponta para a configuração do mapeamento de representação.

      ![imagem](/help/user-guide/assets/adaptive-renditions/mapping-rules2.png)

   * Em uma versão mais antiga dos projetos do Screens, a associação deve ser explicitamente definida adicionando a propriedade `sling:configRef` apontando `/conf/screens` para o nó de conteúdo do projeto.

      ![imagem](/help/user-guide/assets/adaptive-renditions/mapping-rules3.png)

## Estratégia de migração {#migration-strategy}

>[!IMPORTANT]
>Para redes grandes, é recomendável que a migração seja feita gradualmente para reduzir os riscos, pois o recurso introduzirá alterações no formato de armazenamento de arquivos e manifesto.

O diagrama a seguir descreve a estratégia de migração para redes grandes:

![imagem](/help/user-guide/assets/adaptive-renditions/migration-strategy1.png)

Para ativar o recurso, adicione pelo menos uma regra de mapeamento e verifique se a configuração de mapeamento de representação é resolvível no contexto de exibições e canais. Siga as etapas abaixo para migrar:

1. Adicione [Regras de mapeamento de representação](#adding-rendition-mapping-rules).
1. Crie uma pasta para novos canais e adicione uma referência apontando para a configuração do mapeamento de representação.
1. Crie novos canais substituindo os antigos e faça upload de representações.
1. Atribuir novamente exibições aos novos canais.
1. Adicione uma referência às exibições ou locais migrados apontando para a configuração do mapeamento de representação.
1. Repita as etapas 3, 4 e 5 para todos os canais e exibições restantes.
1. Após concluir a migração, remova todas as referências de configuração de canais, exibições e locais e adicione uma única ao nó de conteúdo do projeto.

## Configuração de autor e publicação {#setup-author-publish}

Considere as seguintes recomendações em Autor e Publicação antes de usar as Representações adaptativas:

* O mapeamento de representação tem de ser replicado manualmente.

* As representações de ativos não são replicadas por padrão. Todos os ativos relevantes precisam ser replicados manualmente.

## Adicionar regras de mapeamento de representação {#add-rendition-mapping-rules}

1. Para adicionar uma regra de mapeamento, é necessário criar um nó do tipo `nt:unstructured` no nó de mapeamento de representação.

1. Adicione a propriedade expression com o valor que contém a expressão query.

   >[!NOTE]
   >Consulte [Usando a sintaxe de consulta de mídia](https://developer.mozilla.org/en-US/docs/Web/CSS/Media_Queries/Using_media_queries) para saber mais.

1. Adicione a propriedade pattern com o valor contendo o padrão de nomenclatura de representação que será selecionado, se a expressão for avaliada como true.

   ![imagem](/help/user-guide/assets/adaptive-renditions/mapping-rules4.png)


## Upload de representações {#upload-renditions}

1. Crie uma versão do ativo que melhor se adapte à exibição de sinalização, por exemplo, `portrait orientation`.

1. Escolha o padrão de nomenclatura de representação, por exemplo,`portrait`.

1. Renomeie o arquivo de ativo para que ele contenha o padrão, por exemplo, `my_asset_portrait.png`.

1. Clique em **Adicionar representação** para carregar a representação, como mostrado na figura abaixo.

   ![imagem](/help/user-guide/assets/adaptive-renditions/add-rendition.png)

## Próximas etapas {#next-steps}

Depois de fazer upload das representações, você pode usar as Representações adaptativas, nos canais do AEM Screens. Consulte Uso de representações adaptativas para obter mais detalhes.
