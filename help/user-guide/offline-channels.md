---
title: Canais offline
seo-title: Canais offline
description: 'O player do AEM Screens oferece suporte offline para canais por meio da tecnologia ContentSync . Siga esta página para saber mais sobre os manipuladores de atualização e ativar a configuração offline para um canal.  '
seo-description: 'O player do AEM Screens oferece suporte offline para canais por meio da tecnologia ContentSync . Siga esta página para saber mais sobre os manipuladores de atualização e ativar a configuração offline para um canal.  '
uuid: 18b9d175-ff26-42db-86aa-5ea978909f71
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: developing
discoiquuid: bd572743-652f-4fc5-8b75-a3c4c74536f4
docset: aem65
feature: Desenvolvendo telas
role: Desenvolvedor
level: Intermediário
translation-type: tm+mt
source-git-commit: 9d36c0ebc985b815ab41d3f3ef44baefa22db915
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 1%

---


# Canais offline {#offline-channels}

O player do Screens fornece suporte offline para canais aproveitando a tecnologia ***ContentSync***.

Os players usam um servidor http local para veicular o conteúdo descompactado.

Quando um canal é configurado para executar *online*, o reprodutor fornece os recursos do canal acessando o servidor de AEM, mas quando o canal é configurado para executar *offline*, o reprodutor fornece os recursos do canal a partir de um servidor http local.

O fluxo de trabalho do processo é o seguinte:

1. Analisar as páginas desejadas
1. Coletar todos os ativos relacionados
1. Compactar tudo em um arquivo zip
1. Baixe o zip e extraia-o localmente
1. Exibir cópia local do conteúdo

## Atualizar Manipuladores {#update-handlers}

O ***ContentSync*** usa manipuladores de atualização para analisar e coletar todas as páginas e ativos necessários para um projeto específico. A AEM Screens usa os seguintes manipuladores de atualização:

### Opções comuns {#common-options}

* *tipo*: o tipo de manipulador de atualização a ser usado
* *caminho*: caminho para o recurso
* *[targetRootDirectory]*: pasta de destino no arquivo zip

<table>
 <tbody>
  <tr>
   <td><strong>Tipo</strong></td> 
   <td><strong>Descrição</strong></td> 
   <td><strong>Opções</strong></td> 
  </tr>
  <tr>
   <td>canais</td> 
   <td>coleta um canal</td> 
   <td>extensão: extensão do recurso para coletar<br /> [pathSuffix='']: sufixo para adicionar ao caminho do canal<br /> </td> 
  </tr>
  <tr>
   <td>clientlib</td> 
   <td>coletar a biblioteca do cliente especificada</td> 
   <td>[extension='']: pode ser css ou js, para coletar somente o primeiro ou apenas o último</td> 
  </tr>
  <tr>
   <td>ativos</td> 
   <td>coletar as representações de ativos</td> 
   <td>[renditions=[]]: lista de representações a serem coletadas. Padrões para a representação original</td> 
  </tr>
  <tr>
   <td>copiar</td> 
   <td>copiar a estrutura especificada do caminho</td> 
   <td> </td> 
  </tr>
 </tbody>
</table>

### Teste da configuração do ContentSync {#testing-contentsync-configuration}

Siga as etapas abaixo para testar a configuração do ContentSync:

1. Abrir `https://localhost:4502/libs/cq/contentsync/content/console.html`
1. Selecione sua configuração na lista
1. Clique em Limpar cache
1. Clique em Atualizar cache
1. Clique em Download completo
1. Extrair o arquivo zip
1. Iniciar um servidor local na pasta extraída
1. Abra a página inicial e verifique o status do aplicativo

## Ativar a configuração offline para um canal {#enabling-offline-config-for-a-channel}

Siga as etapas abaixo para ativar a configuração offline para um canal:

1. Inspect o conteúdo do canal e verifique se ele foi solicitado de uma Instância AEM (Online).

   ![chlimage_1-24](assets/chlimage_1-24.png)

1. Navegue até o painel do canal e clique em **...** no painel **INFORMAÇÕES DO CANAL** para alterar as propriedades.

   ![chlimage_1-25](assets/chlimage_1-25.png)

1. Navegue até as propriedades do canal e verifique se a caixa de seleção está desativada na guia **Canal**. Clique em **Salvar e fechar**.

   ![screen_shot_2017-12-19at122422pm](assets/screen_shot_2017-12-19at122422pm.png)

   Antes de o conteúdo ser devidamente implantado no dispositivo, clique no botão **Atualizar conteúdo offline**.

   ![screen_shot_2017-12-19at122637pm](assets/screen_shot_2017-12-19at122637pm.png)

   O status **Offline** em **PROPERTIES** também é atualizado adequadamente.

   ![screen_shot_2017-12-19at124735pm](assets/screen_shot_2017-12-19at124735pm.png)

1. Inspect o conteúdo do canal e verifique se ele foi solicitado do Player-Cache local.

   ![chlimage_1-26](assets/chlimage_1-26.png)

>[!NOTE]
>
>Para saber mais sobre o modelo para manipuladores de recursos offline personalizados e os requisitos mínimos no `pom.xml` para esse projeto específico, consulte [Modelo para manipuladores personalizados](/help/user-guide/developing-custom-component-tutorial-develop.md#custom-handlers) em **Desenvolvimento de um componente personalizado para AEM Screens**.