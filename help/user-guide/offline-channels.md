---
title: Canais offline
description: Saiba mais sobre como o AEM Screens Player fornece suporte offline para canais usando a tecnologia ContentSync.
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: developing
docset: aem65
feature: Developing Screens
role: Developer
level: Intermediate
exl-id: 5ad1046f-8b64-490b-9966-ce9008180d54
source-git-commit: 6643f4162c8f0ee7bcdb0fd3305d3978234f5cfd
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 0%

---

# Canais offline {#offline-channels}

O reprodutor do Screens fornece suporte offline para os canais usando o ***ContentSync*** tecnologia.

Os players usam um servidor http local para veicular o conteúdo descompactado.

Quando um canal é configurado para ser executado *online*, o reprodutor serve os recursos do canal acessando o servidor AEM. No entanto, quando o canal está configurado para ser executado *offline*, o reprodutor serve os recursos de canal de um servidor http local.

O fluxo de trabalho do processo é o seguinte:

1. Analise as páginas desejadas.
1. Coletar todos os ativos relacionados.
1. Compactar tudo em um arquivo zip.
1. Baixe o zip e extraia-o localmente.
1. Exibir cópia local do conteúdo.

## Manipuladores de atualização {#update-handlers}

A variável ***ContentSync*** O usa manipuladores de atualização para analisar e coletar todas as páginas e ativos necessários para um projeto específico. O AEM Screens usa os seguintes manipuladores de atualização:

### Opções comuns {#common-options}

* *type*: o tipo de manipulador de atualização a ser usado
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
   <td><code>channels</code></td> 
   <td>coleta um canal</td> 
   <td>extensão: extensão do recurso a ser coletado<br /> [pathSuffix='']: sufixo a ser adicionado ao caminho do canal<br /> </td> 
  </tr>
  <tr>
   <td><code>clientlib</code></td> 
   <td>coletar a biblioteca do cliente especificada</td> 
   <td>[extension='']: pode ser css ou js, para coletar apenas o primeiro ou apenas o último</td> 
  </tr>
  <tr>
   <td><code>assetrenditions</code></td> 
   <td>coletar as representações de ativos</td> 
   <td>[renditions=[]]: lista de representações a serem coletadas. O padrão é a representação original</td> 
  </tr>
  <tr>
   <td><code>copy</code></td> 
   <td>copiar a estrutura especificada do caminho</td> 
   <td> </td> 
  </tr>
 </tbody>
</table>

### Testar a configuração do ContentSync {#testing-contentsync-configuration}

Siga as etapas abaixo para testar a configuração do ContentSync:

1. Abertura `https://localhost:4502/libs/cq/contentsync/content/console.html`
1. Clique em sua configuração na lista
1. Clique em Limpar cache
1. Clique em Atualizar cache
1. Clique em Baixar completo
1. Extraia o arquivo zip
1. Iniciar um servidor local na pasta extraída
1. Abra a página inicial e verifique o status do aplicativo

## Ativação da configuração offline para um canal {#enabling-offline-config-for-a-channel}

Siga as etapas abaixo para habilitar a configuração offline de um canal:

1. Inspect o conteúdo do canal e verifique se ele é solicitado de uma instância AEM (Online).

   ![chlimage_1-24](assets/chlimage_1-24.png)

1. Navegue até o painel do canal.
1. Clique em **..** no **INFORMAÇÕES DO CANAL** Painel.

   ![chlimage_1-25](assets/chlimage_1-25.png)

1. Navegue até as propriedades do canal.
1. Na guia (Canal), verifique se a caixa de seleção está desativada e clique em **Salvar e fechar**.

   ![screen_shot_2017-12-19at122422pm](assets/screen_shot_2017-12-19at122422pm.png)

   Antes que o conteúdo seja implantado corretamente no dispositivo, clique no link **Atualizar conteúdo offline**.

   ![screen_shot_2017-12-19at122637pm](assets/screen_shot_2017-12-19at122637pm.png)

   A variável **Offline** status em **PROPRIEDADES** O também é atualizado de acordo.

   ![screen_shot_2017-12-19at124735pm](assets/screen_shot_2017-12-19at124735pm.png)

1. Inspect o conteúdo do canal e verifique se ele é solicitado do Player-Cache local.

   ![chlimage_1-26](assets/chlimage_1-26.png)

>[!NOTE]
>
>Para saber mais sobre o modelo para manipuladores de recursos offline personalizados e os requisitos mínimos na `pom.xml` para esse projeto específico, consulte [Modelo para manipuladores personalizados](/help/user-guide/developing-custom-component-tutorial-develop.md#custom-handlers) in **Desenvolvimento de um componente personalizado para o AEM Screens**.
