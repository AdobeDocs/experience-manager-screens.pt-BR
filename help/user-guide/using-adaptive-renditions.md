---
title: Uso de representações adaptáveis no AEM Screens
description: Saiba como usar representações adaptáveis no AEM Screens.
exl-id: e7f68ed4-73c3-492a-b33a-dd915ef1f8be
source-git-commit: b65e59473e175e7c1b31fba900bb7e47eff3a263
workflow-type: tm+mt
source-wordcount: '540'
ht-degree: 0%

---

# Uso de representações adaptáveis no AEM Screens {#adaptive-renditions}

## Introdução {#introduction}

As representações adaptáveis permitem que os dispositivos selecionem automaticamente a melhor representação para um dispositivo com base em regras definidas pelo cliente. Os dispositivos baixam e reproduzem automaticamente a representação mais apropriada de um ativo com base nessas regras, permitindo que os clientes se concentrem apenas no design do *main* experiência.

## Objetivo {#objective}

Como um Autor de conteúdo do AEM Screens, agora você pode configurar representações de ativos específicas do dispositivo para serem baixadas e reproduzidas automaticamente sem precisar criar todas as variações de conteúdo manualmente.
Depois que um Desenvolvedor adicionar as propriedades e regras do mapeamento de representação, você estará pronto para aplicar o mapeamento de representação aos ativos e incluí-los em um canal do AEM Screens.

>[!IMPORTANT]
>Antes de começar a usar as representações adaptáveis em um canal do AEM Screens, a Adobe recomenda que você saiba mais sobre a Visão geral e a configuração da arquitetura desse recurso. Consulte [Representações adaptáveis: visão geral e configurações da arquitetura](/help/user-guide/adaptive-renditions.md).

## Uso de representações adaptáveis em canais {#using-adaptive-renditions}

>[!NOTE]
>Depois de ter adicionado [propriedade de mapeamento de representação para o projeto do Screens](/help/user-guide/adaptive-renditions.md#rendition-mapping-new) e [regras de mapeamento de representação](/help/user-guide/adaptive-renditions.md#add-rendition-mapping-rules), como um Autor de conteúdo, agora você está pronto para aplicar as representações aos seus ativos.

### Aplicação de representações a ativos {#apply-renditions-assets}

Para aplicar representações a ativos que deseja usar no canal de telas de tour, faça o seguinte.

1. Navegue até a **Assets** pasta na instância do AEM.
1. Crie uma versão do ativo que se ajuste melhor à exibição de sinalização, por exemplo, `seahorse.jpg`.
1. Escolha o padrão de nomenclatura da representação, por exemplo,`landscape`, semelhante ao definido em **padrão** propriedade no **CRXDE Lite**. Consulte [Adição de regras de mapeamento de representação](/help/user-guide/adaptive-renditions.md#add-rendition-mapping-rules) para obter mais detalhes.
1. Clique em **Adicionar representação** para fazer upload da representação, conforme mostrado na figura abaixo.

   ![imagem](/help/user-guide/assets/adaptive-renditions/manage-pub-asset2.png)

1. Selecione o renomeado para o arquivo de ativo. A representação que você está adicionando deve conter o padrão (definido na etapa 3), por exemplo, `seahorse-landscape.png`.
1. Depois de ter adicionado o ativo, selecione-o e clique em **Gerenciar publicação** na barra de ações para publicar o ativo.

   ![imagem](/help/user-guide/assets/adaptive-renditions/manage-pub-asset1.png)

   >[!NOTE]
   >Consulte [Atualização de conteúdo sob demanda](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/authoring/content-updates/on-demand-content) para saber mais sobre como gerenciar a publicação e fornecer atualizações de conteúdo de Autor para Publicar no dispositivo.

## Estratégia de migração {#migration-strategy}

>[!IMPORTANT]
>Para grandes redes, a Adobe recomenda que a migração seja feita gradualmente para reduzir os riscos. O motivo é que o recurso pode introduzir alterações no formato de armazenamento de manifesto e arquivo. Adicionar o `sling:configRef` para todo o projeto envolve a atualização de todos os players para o Feature Pack 6.5.9. Caso tenha atualizado alguns dos reprodutores, adicione o `sling:configRef` somente para exibições, locais ou pastas de canal que têm todos os players atualizados para o Feature Pack 6.5.9.

O diagrama a seguir descreve a estratégia de migração para redes grandes:

![imagem](/help/user-guide/assets/adaptive-renditions/migration-strategy1.png)

Para ativar o recurso, adicione pelo menos uma regra de mapeamento e verifique se a configuração do mapeamento de representação pode ser resolvida no contexto de exibições e canais. Siga as etapas abaixo para migrar:

1. Adicionar [Regras de mapeamento de representação](/help/user-guide/adaptive-renditions.md).
1. Crie uma pasta para novos canais e adicione uma referência apontando para a configuração do mapeamento de representação.
1. Crie canais que substituem os antigos e faça upload de representações.
1. Reatribuir exibições para os novos canais.
1. Adicione uma referência às exibições ou locais migrados que apontam para a configuração do mapeamento de representação.
1. Repita as etapas 3, 4 e 5 para todos os canais e exibições restantes.

   >[!NOTE]
   >Após concluir a migração, remova todas as referências de configuração de canais, exibições e locais e adicione uma única ao nó de conteúdo do projeto.
