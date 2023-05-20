---
title: Adicionar componentes a um canal
seo-title: Adding Components to a Channel
description: Siga esta página para saber mais sobre como adicionar componentes a canais em um projeto do AEM Screens.
seo-description: Follow this page to learn more about adding components to channels in an AEM Screens project.
uuid: 205d0edd-a696-47d0-a859-5f44d48c5e4a
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: bfbdd6eb-4921-4c2d-a179-1cac4583d568
docset: aem65
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 56dbe098-05db-4fc3-977f-e50a0a312d64
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '1443'
ht-degree: 7%

---

# Adicionar componentes a um canal{#adding-components-to-a-channel}

Os componentes são os elementos fundamentais da experiência com o AEM (Adobe Experience Manager). Você pode usar vários componentes e adicioná-los ao canal em um projeto do AEM Screens.

## Componentes no AEM Screens {#components-in-aem-screens}

O AEM Screens fornece diferentes componentes do AEM que podem ser usados em um projeto do Screens.

### Visualização de componentes do AEM Screens {#viewing-aem-screens-components}

Sempre que criar um projeto AEM Screens, você verá uma lista de componentes padrão que podem ser adicionados ao projeto.

Para exibir os componentes padrão do seu projeto do Screens, siga as etapas abaixo:

1. Selecione o canal. Por exemplo, **We.Retail Na Loja** —> **Canais** —> **Canal ocioso**.

1. Clique em **Editar** na barra de ações para abrir o editor de AEM.
1. Clique em **+** ícone na barra lateral para abrir os componentes.
1. Todos os componentes incluídos por padrão em um projeto do AEM Screens são exibidos, como mostrado na figura abaixo.

![screen_shot_2017-12-18at21350pm](assets/screen_shot_2017-12-18at21350pm.png)

### Adicionar um novo componente {#adding-a-new-component}

O AEM fornece vários outros componentes. Você sempre pode adicionar outros componentes (não incluídos por padrão) ao seu projeto, já que eles são compatíveis com o AEM Screens.

O exemplo a seguir mostra a adição de um componente Livefyre a um projeto AEM Screens:

1. Selecione o canal no qual deseja adicionar um novo componente. Por exemplo, **We.Retail Na Loja** —> **Canais** —> **Canal ocioso**.

1. Clique em **Editar** na barra de ações para abrir o editor.
1. Selecionar **Design** modo.
1. Selecione todo o editor de design à direita e clique no símbolo de configurações para abrir a **Design de ParSys** caixa de diálogo.
1. Você pode selecionar os componentes que deseja importar para o projeto do AEM Screens. O exemplo a seguir mostra a adição de **Livefyre** componente a um projeto do AEM Screens.

![add_components](assets/adding_components.gif)

>[!NOTE]
>
>Da mesma forma, você pode adicionar qualquer número de outros novos componentes compatíveis com o AEM Screens ao seu projeto.

## Compreender os componentes da tela AEM {#understanding-aem-screen-components}

A seção a seguir explica os componentes do AEM Screens que você pode usar no projeto.

>[!NOTE]
>
>Para exibir as propriedades de qualquer componente, selecione o componente e clique no ícone de martelo para abrir/exibir propriedades.

### Aplicativo {#application}

A variável **Aplicativo** permite adicionar um aplicativo ao canal.

O componente do aplicativo tem as seguintes propriedades:

| **Propriedade** | **Descrição** |
|---|---|
| ***Caminho do aplicativo*** | Selecione o caminho absoluto onde o aplicativo existe. |
| ***Duração (ms)*** | Selecione a duração do aplicativo. Por padrão, a duração é definida como -1, o que significa que o elemento é executado para sempre (ou seja, aplicativo de página única). Definir o valor de duração >0 mostra o elemento para a duração especificada e, em seguida, avança para o próximo. |

O exemplo a seguir mostra como incorporar um componente de aplicativo juntamente com a visualização de suas propriedades:

![adding_componentsapplication](assets/adding_componentsapplication.gif)

>[!NOTE]
>
>Consulte o exemplo acima para exibir as propriedades de cada um dos componentes abaixo.

### Canal {#channel}

A variável **Canal** permite adicionar um canal inteiro ao projeto.

O componente Canal tem as seguintes propriedades:

<table>
 <tbody>
  <tr>
   <td><strong>Propriedade</strong></td>
   <td><strong>Descrição</strong></td>
  </tr>
  <tr>
   <td><strong><em>Caminho do canal</em></strong></td>
   <td>Selecione esse caminho absoluto onde o aplicativo existe.<br /> </td>
  </tr>
  <tr>
   <td><strong><em>Duração (ms)</em></strong></td>
   <td>Selecione toda a duração do canal. Definir a duração como -1 indica que o canal incorporado executará seu comprimento total em um canal específico.</td>
  </tr>
 </tbody>
</table>

### Página incorporada {#embedded-page}

Um **Página incorporada** permite adicionar uma página incorporada ao projeto. Por exemplo, pode ser um aplicativo web ou um catálogo de produtos.

A página Incorporada tem as seguintes propriedades:

<table>
 <tbody>
  <tr>
   <td><strong>Propriedade</strong></td>
   <td><strong>Descrição</strong></td>
  </tr>
  <tr>
   <td><strong><em>Caminho da página<br /> </em></strong></td>
   <td>Selecione esse caminho absoluto onde o canal existe.<br /> </td>
  </tr>
  <tr>
   <td><strong><em>Duração (ms)</em></strong></td>
   <td>Selecione toda a duração do canal. Definir a duração como -1 indica que o canal incorporado executará seu comprimento total em um canal específico.</td>
  </tr>
 </tbody>
</table>

### Sequência incorporada {#embedded-sequence}

>[!NOTE]
>
>Consulte [Sequências incorporadas](embedded-sequences.md) na seção Criação de telas, para saber mais detalhes sobre sequências incorporadas.

Uma sequência incorporada permite adicionar um canal de sequência incorporada no canal existente (com outros ativos).

A Sequência incorporada tem as seguintes propriedades de página:

<table>
 <tbody>
  <tr>
   <td><strong>Propriedade</strong></td>
   <td><strong>Descrição</strong></td>
  </tr>
  <tr>
   <td>Caminho do canal</td>
   <td>Selecione o caminho absoluto da sequência que deseja incluir no canal.<br /> </td>
  </tr>
  <tr>
   <td><strong><em>Duração (ms)</em></strong></td>
   <td>Selecione toda a duração do canal. Definir a duração como -1 indica que o canal incorporado executará seu comprimento total em um canal específico.</td>
  </tr>
  <tr>
   <td><strong><em>Estratégia</em></strong></td>
   <td>Defina-o como <strong>original</strong> ou <strong>solteiro</strong>. Definir o valor para <strong>original</strong> significa que a subsequência será totalmente executada em cada ciclo da sequência principal. O outro valor possível é <strong>solteiro</strong> e que mostraria apenas um item da subsequência em cada execução (por exemplo, o primeiro item no primeiro loop, o segundo item no segundo loop e assim por diante).</td>
  </tr>
 </tbody>
</table>

### Sequência incorporada dinâmica {#dynamic-embedded-sequence}

Uma sequência incorporada dinâmica permite adicionar uma sequência semelhante à mencionada acima, exceto por função de canal.

Consulte [Sequências incorporadas](embedded-sequences.md) na seção Criação de telas, para saber mais detalhes sobre sequências incorporadas.

A sequência incorporada dinâmica tem as seguintes propriedades:

<table>
 <tbody>
  <tr>
   <td><strong>Propriedade</strong></td>
   <td><strong>Descrição</strong></td>
  </tr>
  <tr>
   <td><strong><em>Função da atribuição do canal</em></strong><br /> </td>
   <td>Insira a função do canal.<br /> </td>
  </tr>
  <tr>
   <td><strong><em>Duração (ms)</em></strong></td>
   <td>Selecione toda a duração do canal. Definir a duração como -1 indica que o canal incorporado executará seu comprimento total em um canal específico.</td>
  </tr>
  <tr>
   <td><strong><em>Estratégia</em></strong></td>
   <td>Defina-o como <strong>original</strong> ou <strong>solteiro</strong>. Definir o valor para <strong>original</strong> significa que a subsequência será totalmente executada em cada ciclo da sequência principal. O outro valor possível é <strong>solteiro</strong> e que mostraria apenas um item da subsequência em cada execução (por exemplo, o primeiro item no primeiro loop, o segundo item no segundo loop e assim por diante).</td>
  </tr>
 </tbody>
</table>

### Fragmento de experiência {#experience-fragment}

Um Fragmento de experiência permite adicionar um fragmento de experiência (grupo de um ou mais componentes, incluindo conteúdo e layout que podem ser referenciados nas páginas) ao canal do AEM Screens. Arraste e solte o componente no editor de AEM e selecione o fragmento de experiência.

Para saber mais sobre como criar um fragmento de experiência e aproveitá-lo em um projeto do AEM Screens, consulte [Uso de fragmentos de experiência](experience-fragments-in-screens.md).

![exp](assets/exp.gif)

| **Propriedade** | **Descrição** |
|---|---|
| **Fragmento de experiência** |
| ***Fragmento de experiência*** | Selecione o fragmento de experiência. |
| ***Duração*** | Selecione toda a duração do fragmento de experiência reproduzido no canal. |
| **Configuração offline** |
| ***Bibliotecas do lado do cliente*** | Arquivos JavaScript e CSS. |
| ***Arquivos estáticos*** | Arquivos estáticos que você pode adicionar como configurações offline ao fragmento de experiência. |

>[!NOTE]
>
>A variável **Bibliotecas do cliente** e a variável **Arquivos estáticos** que você adicionar a partir deste componente será adicionado além do já configurado **Bibliotecas do cliente** e os Arquivos estáticos que são adicionados do repositório do fragmento de experiência **Propriedades**.

### Imagem {#image}

Uma imagem permite adicionar uma imagem ao seu canal.

O ativo de imagem tem três guias: **Imagem**, **Acessibilidade**, e **Sequência**:

| **Propriedade** | **Descrição** |
|---|---|
| **Imagem** |
| ***Ativo de imagem*** | Selecione o ativo de imagem. |
| ***Título*** | Título da imagem. |
| ***Vincular a*** | Adicione um link à imagem. |
| ***Descrição*** | Breve descrição da imagem. |
| ***Tamanho*** | Tamanho da imagem. |
| **Acessibilidade** |
| ***Texto alternativo*** | Texto alternativo para a imagem. |
| **Sequência** |
| ***Duração*** | Por padrão, a duração está definida como *8000 ms*. Se quiser alterar a duração da reprodução da imagem, atualize o **Duração** campo. |

### Transição {#transition}

O componente de Transição permite adicionar uma transição ao projeto do Screens.

A imagem a seguir mostra o componente de transição (adicionado via arrastar e soltar) ao editor.

![screen_shot_2019-07-25at104237am](assets/screen_shot_2019-07-25at104237am.png)

Selecione o ícone de transição e clique no botão **Configurar** (ícone de chave inglesa) para abrir a **Transição** caixa de diálogo. Essa caixa de diálogo inclui três guias:

* **Transição**
* **Sequência**
* **Ativação**

>[!NOTE]
>
>Por padrão, a sequência é definida como 600 ms. É possível atualizar a sequência de transição para outro valor usando o **Sequência** guia.

![transição](assets/transition.gif)

O componente de transição tem as seguintes propriedades:

<table>
 <tbody>
  <tr>
   <td><strong>Propriedade</strong></td>
   <td><strong>Descrição</strong></td>
  </tr>
  <tr>
   <td><strong>Transição</strong></td>
   <td></td>
  </tr>
  <tr>
   <td><strong><em>Tipo</em></strong></td>
   <td><p>O tipo de transição entre o elemento anterior e o posterior. A transição <strong>Tipo</strong> O inclui as seguintes opções:</p>
    <ul>
     <li><strong>Normal</strong></li>
     <li><strong>Esmaecer</strong></li>
     <li><strong>Deslizar da direita</strong></li>
     <li><strong>Deslizar da esquerda</strong></li>
     <li><strong>Deslizar do topo</strong></li>
     <li><strong>Deslizar da parte inferior</strong></li>
    </ul> </td>
  </tr>
  <tr>
   <td><strong>Sequência</strong></td>
   <td></td>
  </tr>
  <tr>
   <td><strong><em>Duração</em></strong></td>
   <td>Selecione toda a duração da transição. Por padrão, é definido como 600 ms.</td>
  </tr>
  <tr>
   <td><strong>Ativação</strong></td>
   <td></td>
  </tr>
  <tr>
   <td><strong><em>Ativo desde</em></strong></td>
   <td>Carimbo de data e hora que descreve quando a transição pode estar ativa.<br /> </td>
  </tr>
  <tr>
   <td><strong><em>Ativo até</em></strong></td>
   <td>Carimbo de data e hora que descreve até quando a transição pode estar ativa.</td>
  </tr>
  <tr>
   <td><strong><em>Programação</em></strong></td>
   <td>Adicione um agendamento predefinido.</td>
  </tr>
 </tbody>
</table>

### Vídeo {#video}

O componente de Vídeo permite que você adicione um vídeo ao seu projeto do Screens.

O componente de vídeo tem as seguintes propriedades:

<table>
 <tbody>
  <tr>
   <td><strong>Propriedade</strong></td>
   <td><strong>Descrição</strong></td>
  </tr>
  <tr>
   <td><em><strong>Ativo de vídeo </strong></em></td>
   <td>Selecione o link para o vídeo.</td>
  </tr>
  <tr>
   <td><em><strong>Duração</strong></em></td>
   <td>Selecione a duração do vídeo. Por padrão, a duração é definida como -1, o que significa que o elemento é executado para sempre. Definir o valor de duração &gt;0 mostra o elemento para a duração especificada e, em seguida, avança para o próximo.<br /> </td>
  </tr>
  <tr>
   <td><em><strong>Renderização</strong></em></td>
   <td><p>Se a taxa de proporção do vídeo não couber na tela, é possível ajustar a renderização para <strong>contain</strong> ou <strong>capa</strong>.</p> <p><em>Contain</em> significa que o vídeo completo é exibido e as áreas ausentes são preenchidas com uma borda preta.</p> <p><em>Capa</em> significa que o vídeo cobre toda a janela de visualização, mas algumas partes que transbordam nas laterais ficam ocultas.</p> </td>
  </tr>
  <tr>
   <td><em><strong>Tamanho</strong></em></td>
   <td>Tamanho do vídeo.</td>
  </tr>
 </tbody>
</table>
