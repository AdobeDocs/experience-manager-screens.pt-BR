---
title: Canais off-line
seo-title: Canais off-line
description: 'O AEM Screens player oferece suporte offline para canais, aproveitando a tecnologia ContentSync. Siga esta página para saber mais sobre os manipuladores de atualizações e como ativar a configuração offline para um canal.  '
seo-description: 'O AEM Screens player oferece suporte offline para canais, aproveitando a tecnologia ContentSync. Siga esta página para saber mais sobre os manipuladores de atualizações e como ativar a configuração offline para um canal.  '
uuid: 18b9d175-ff26-42db-86aa-5ea978909f71
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: developing
discoiquuid: bd572743-652f-4fc5-8b75-a3c4c74536f4
docset: aem65
translation-type: tm+mt
source-git-commit: f25176be89424059b8c51296969f069687328536
workflow-type: tm+mt
source-wordcount: '481'
ht-degree: 1%

---


# Canais off-line {#offline-channels}

O Screens player fornece suporte offline para os canais, aproveitando a tecnologia ***ContentSync*** .

Os players usam um servidor http local para servir o conteúdo descompactado.

Quando um canal é configurado para execução *on-line*, o player serve os recursos do canal acessando o servidor AEM, mas quando o canal é configurado para execução *off-line*, ele serve os recursos do canal de um servidor http local.

O fluxo de trabalho do processo é o seguinte:

1. Analisar as páginas desejadas
1. Coletar todos os ativos relacionados
1. Empacotar tudo em um arquivo zip
1. Baixe o zip e extraia-o localmente
1. Exibir cópia local do conteúdo

## Manipuladores de Atualização {#update-handlers}

O ***ContentSync*** usa manipuladores de atualização para analisar e coletar todas as páginas e ativos necessários para um projeto específico. O AEM Screens usa os seguintes manipuladores de atualização:

### Opções comuns {#common-options}

* *tipo*: o tipo de manipulador de atualização a ser usado
* *caminho*: caminho para o recurso
* *[targetRootDirectory]*: pasta público alvo no arquivo zip

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
   <td>extensão: extensão do recurso para coletar<br /> [pathSuffix='']: sufixo a ser adicionado ao caminho do canal<br /> </td> 
  </tr>
  <tr>
   <td>clientlib</td> 
   <td>coletar a biblioteca de cliente especificada</td> 
   <td>[extension='']: pode ser css ou js, para coletar somente a primeira, ou apenas a última</td> 
  </tr>
  <tr>
   <td>ativos</td> 
   <td>coletar as representações de ativos</td> 
   <td>[execuções=[]]: lista de execuções a serem coletadas. O padrão é a execução original</td> 
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
1. Extraia o arquivo zip
1. Start de um servidor local na pasta extraída
1. Abra a página start e verifique o status do aplicativo

## Ativar a configuração offline para um Canal {#enabling-offline-config-for-a-channel}

Siga as etapas abaixo para ativar a configuração offline para um canal:

1. Inspecione o conteúdo do canal e verifique se ele foi solicitado de uma instância do AEM (Online).

   ![chlimage_1-24](assets/chlimage_1-24.png)

1. Navegue até o painel do canal e clique em **...** no Painel INFORMAÇÕES **do** CANAL para alterar as propriedades.

   ![chlimage_1-25](assets/chlimage_1-25.png)

1. Navegue até as propriedades do canal e verifique se a caixa de seleção está desativada na guia **Canal** . Clique em **Salvar e fechar**.

   ![screen_shot_2017-12-19at122422pm](assets/screen_shot_2017-12-19at122422pm.png)

   Antes que o conteúdo seja implantado corretamente no dispositivo, clique em **Atualizar conteúdo** offline.

   ![screen_shot_2017-12-19at122637pm](assets/screen_shot_2017-12-19at122637pm.png)

   O status **Offline** em **PROPRIEDADES** também é atualizado de acordo.

   ![screen_shot_2017-12-19at124735pm](assets/screen_shot_2017-12-19at124735pm.png)

1. Inspecione o conteúdo do canal e verifique se ele foi solicitado do Player-Cache local.

   ![chlimage_1-26](assets/chlimage_1-26.png)

>[!NOTE]
>
>Para saber mais sobre o modelo para manipuladores de recursos offline personalizados e os requisitos mínimos no `pom.xml` para esse projeto específico, consulte [Modelo para manipuladores](/help/user-guide/developing-custom-component-tutorial-develop.md#custom-handlers) personalizados em **Desenvolvimento de um componente personalizado para AEM Screens**.