---
title: Uso de representações adaptativas no AEM Screens
description: Esta página descreve como usar Representações adaptativas no AEM Screens.
index: false
source-git-commit: db6f8c438783725c6ea99e8e363f74e766a3767b
workflow-type: tm+mt
source-wordcount: '497'
ht-degree: 0%

---

# Uso de representações adaptativas no AEM Screens {#adaptive-renditions}

## Introdução {#introduction}

As Representações adaptativas permitem que os dispositivos selecionem automaticamente a melhor representação para um dispositivo com base nas regras definidas pelo cliente. Os dispositivos baixarão e reproduzirão automaticamente a representação mais apropriada de um ativo com base nessas regras, permitindo que os clientes se concentrem apenas na criação da experiência *principal*.

## Objetivo {#objective}

Como um Autor de conteúdo do AEM Screens, agora você pode configurar representações de ativos específicas do dispositivo para serem baixadas e reproduzidas automaticamente, sem precisar criar todas as variações de conteúdo manualmente.
Depois que um desenvolvedor adiciona as propriedades e regras de mapeamento de representação, você está pronto para aplicar o mapeamento de representação aos ativos e, subsequentemente, incluí-los em um canal do AEM Screens.

>[!IMPORTANT]
>Antes de começar a usar as Representações adaptativas, em um canal AEM Screens, é recomendável saber mais sobre a Visão geral e a configuração da arquitetura desse recurso. Consulte [Representações adaptativas: Visão geral da arquitetura e configurações](/help/user-guide/adaptive-renditions.md) para obter mais detalhes.

## Uso de representações adaptativas em canais {#using-adaptive-renditions}

>[!NOTE]
>Depois de adicionar [propriedade de mapeamento de representação ao Projeto do Screens](/help/user-guide/adaptive-renditions.md#rendition-mapping-new) e [regras de mapeamento de representação](/help/user-guide/adaptive-renditions.md#add-rendition-mapping-rules), como um Autor de conteúdo, você agora estará pronto para aplicar as representações aos seus ativos.

### Aplicar representações a ativos {#apply-renditions-assets}

Siga as etapas abaixo para aplicar representações aos ativos, que você deseja usar no canal de telas do tour:

1. Navegue até a pasta **Assets** na sua instância de AEM.

1. Crie uma versão do ativo que melhor se adapte à exibição de sinalização, por exemplo, `seahorse.jpg`.

1. Escolha o padrão de nomenclatura de representação, por exemplo,`landscape`, semelhante ao que foi definido na propriedade pattern no CRXDE Lite. Consulte [Adicionar regras de mapeamento de representação](/help/user-guide/adaptive-renditions.md#add-rendition-mapping-rules) para obter mais detalhes.

1. Renomeie o arquivo de ativo para que ele contenha o padrão, por exemplo, `seahorse_landscape.png`.

1. Clique em **Adicionar representação** para carregar a representação, como mostrado na figura abaixo.

   ![imagem](/help/user-guide/assets/adaptive-renditions/add-rendition.png)


## Estratégia de migração {#migration-strategy}

>[!IMPORTANT]
>Para redes grandes, é recomendável que a migração seja feita gradualmente para reduzir os riscos, pois o recurso introduzirá alterações no formato de armazenamento de arquivos e manifesto. Adicionar o `sling:configRef` ao projeto inteiro envolve atualizar todos os players para o Feature Pack 6.5.9. Caso tenha atualizado alguns reprodutores, é necessário adicionar o `sling:configRef` somente àquelas exibições, locais ou pastas de canal que tenham todos os reprodutores atualizados para o Feature Pack 6.5.9.

O diagrama a seguir descreve a estratégia de migração para redes grandes:

![imagem](/help/user-guide/assets/adaptive-renditions/migration-strategy1.png)

Para ativar o recurso, adicione pelo menos uma regra de mapeamento e verifique se a configuração de mapeamento de representação é resolvível no contexto de exibições e canais. Siga as etapas abaixo para migrar:

1. Adicione [Regras de mapeamento de representação](/help/user-guide/adaptive-renditions.md).
1. Crie uma pasta para novos canais e adicione uma referência apontando para a configuração do mapeamento de representação.
1. Crie novos canais substituindo os antigos e faça upload de representações.
1. Atribuir novamente exibições aos novos canais.
1. Adicione uma referência às exibições ou locais migrados apontando para a configuração do mapeamento de representação.
1. Repita as etapas 3, 4 e 5 para todos os canais e exibições restantes.

   >[!NOTE]
   >Após concluir a migração, remova todas as referências de configuração de canais, exibições e locais e adicione uma única ao nó de conteúdo do projeto.

