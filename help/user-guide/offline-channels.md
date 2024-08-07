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
source-git-commit: 8dde26d36847fb496aed6d4bf9732233116b5ea6
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 0%

---

# Canais offline {#offline-channels}

O Screens player oferece suporte offline para os canais usando a tecnologia ***ContentSync***.

Os players usam um servidor http local para veicular o conteúdo descompactado.

Quando um canal é configurado para executar o *online*, o player serve os recursos do canal acessando o servidor AEM. No entanto, quando o canal é configurado para executar *offline*, o player serve os recursos de canal de um servidor http local.

O fluxo de trabalho do processo é o seguinte:

1. Analise as páginas desejadas.
1. Coletar todos os ativos relacionados.
1. Compactar tudo em um arquivo zip.
1. Baixe o zip e extraia-o localmente.
1. Exiba uma cópia local do conteúdo.

## Manipuladores de atualização {#update-handlers}

O ***ContentSync*** usa manipuladores de atualização para analisar e coletar todas as páginas e ativos necessários para um projeto específico. O AEM Screens usa os seguintes manipuladores de atualização:

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
   <td><code>channels</code></td> 
   <td>coleta um canal</td> 
   <td>extensão: extensão do recurso a coletar<br /> [pathSuffix='']: sufixo a ser adicionado ao caminho do canal<br /> </td> 
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

1. Abrir `https://localhost:4502/libs/cq/contentsync/content/console.html`.
1. Clique em sua configuração na lista.
1. Clique em **Limpar cache**.
1. Clique em **Atualizar cache**.
1. Clique em **Download Completo**.
1. Extraia o arquivo zip.
1. Iniciar um servidor local na pasta extraída.
1. Abra a página inicial e verifique o status do aplicativo.

## Ativação da configuração offline para um canal {#enabling-offline-config-for-a-channel}

Siga as etapas abaixo para habilitar a configuração offline de um canal:

1. Inspect o conteúdo do canal e verifique se ele é solicitado de uma instância AEM (Online).

   ![chlimage_1-24](assets/chlimage_1-24.png)

1. Navegue até o painel do canal.
1. Clique em **...** no painel **INFORMAÇÕES DO CANAL**.

   ![chlimage_1-25](assets/chlimage_1-25.png)

1. Navegue até as propriedades do canal.
1. Na guia (Canal), verifique se a caixa de seleção está desabilitada e clique em **Salvar e fechar**.

   ![screen_shot_2017-12-19at122422pm](assets/screen_shot_2017-12-19at122422pm.png)

   Antes de implantar o conteúdo corretamente no dispositivo, clique em **Atualizar Conteúdo Offline**.

   ![screen_shot_2017-12-19at122637pm](assets/screen_shot_2017-12-19at122637pm.png)

   O status **Offline** em **PROPRIEDADES** também é atualizado adequadamente.

   ![screen_shot_2017-12-19at124735pm](assets/screen_shot_2017-12-19at124735pm.png)

1. Inspect o conteúdo do canal e verifique se ele é solicitado do Player-Cache local.

   ![chlimage_1-26](assets/chlimage_1-26.png)

>[!NOTE]
>
>Saiba mais sobre o modelo para manipuladores de recursos offline personalizados. E saiba mais sobre os requisitos mínimos no `pom.xml` do projeto. Consulte [Modelo para Manipuladores personalizados](/help/user-guide/developing-custom-component-tutorial-develop.md#custom-handlers) em **Desenvolvendo um componente personalizado para o AEM Screens**.
