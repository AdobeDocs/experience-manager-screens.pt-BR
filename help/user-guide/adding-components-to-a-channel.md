---
title: Adição de componentes a um canal
seo-title: Adição de componentes a um canal
description: Siga esta página para saber mais sobre como adicionar componentes a canais em um projeto do AEM Screens.
seo-description: Siga esta página para saber mais sobre como adicionar componentes a canais em um projeto do AEM Screens.
uuid: 205d0edd-a696-47d0-a859-5f44d48c5e4a
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: bfbdd6eb-4921-4c2d-a179-1cac4583d568
docset: aem65
translation-type: tm+mt
source-git-commit: 209a9a833957d9a8bb7c7ec70ff421514f5b974c

---


# Adição de componentes a um canal{#adding-components-to-a-channel}

Componentes são os elementos fundamentais da experiência do AEM (Adobe Experience Manager). Você pode usar vários componentes e adicioná-los ao seu canal em um projeto do AEM Screens.

## Componentes no AEM Screens {#components-in-aem-screens}

O AEM Screens fornece diferentes componentes do AEM que podem ser usados em um projeto do Screens.

### Visualização de componentes do AEM Screens {#viewing-aem-screens-components}

Sempre que criar um projeto do AEM Screens, você verá uma lista de componentes padrão que podem ser adicionados ao projeto.

Para visualizar os componentes padrão no seu projeto do Screens, siga as etapas abaixo:

1. Selecione o canal. Por exemplo, **We.Retail In Store** --&gt; **Canais** --&gt; **Canal ocioso**.

1. Clique em **Editar** na barra de ações para abrir o editor do AEM.
1. Clique no ícone **+** na barra lateral para abrir os componentes.
1. Todos os componentes incluídos por padrão em um projeto do AEM Screens são exibidos, conforme mostrado na figura abaixo.

![screen_shot_2017-12-18at21350pm](assets/screen_shot_2017-12-18at21350pm.png)

### Adição de um novo componente {#adding-a-new-component}

O AEM fornece vários outros componentes. Você sempre pode adicionar outros componentes (não incluídos por padrão) ao seu projeto, desde que eles sejam compatíveis com o AEM Screens.

O exemplo a seguir mostra a adição de um componente do Livefyre a um projeto do AEM Screens:

1. Selecione o canal ao qual você deseja adicionar um novo componente. Por exemplo, **We.Retail In Store** --&gt; **Canais** --&gt; **Canal ocioso**.

1. Clique em **Editar** na barra de ações para abrir o editor.
1. Selecione o modo de **Design.**
1. Selecione o editor de design inteiro à direita e clique no símbolo de configurações para abrir a caixa de diálogo **ParSys (Design)**.
1. Você pode selecionar os componentes que deseja importar para o projeto do AEM Screens. O exemplo a seguir mostra a adição do componente **Livefyre** a um projeto do AEM Screens.

![add_components](assets/adding_components.gif)

>[!NOTE]
>
>Da mesma forma, você pode adicionar ao seu projeto qualquer número de outros novos componentes compatíveis com o AEM Screens.

## Noções básicas sobre os componentes do AEM Screens {#understanding-aem-screen-components}

A seção a seguir explica os componentes do AEM Screens que você pode usar em seu projeto.

>[!NOTE]
>
>Para visualizar as propriedades de qualquer componente, selecione o componente e clique no ícone de martelo para abrir/visualizar propriedades.

### Aplicativo {#application}

O componente **Aplicativo** permite adicionar um aplicativo ao seu canal.

O componente Aplicativo tem as seguintes propriedades:

| **Propriedade** | **Descrição** |
|---|---|
| ***Caminho do aplicativo*** | Selecione o caminho absoluto no qual o aplicativo existe. |
| ***Duração (ms)*** | Selecione a duração do aplicativo. Por padrão, a duração é definida como -1, o que significa que o elemento é executado para sempre (ou seja, um aplicativo de página única). Definir o valor de duração como maior que 0 mostra o elemento pela duração especificada e, em seguida, avança para o próximo. |

O exemplo a seguir mostra como incorporar um componente de aplicativo junto com a visualização de suas propriedades:

![add_components_application](assets/adding_componentsapplication.gif)

>[!NOTE]
>
>Consulte o exemplo acima para visualizar as propriedades de cada um dos componentes abaixo.

### Canal {#channel}

O componente **Canal** permite que você adicione um canal inteiro ao seu projeto.

O componente Canal tem as seguintes propriedades:

<table>
 <tbody>
  <tr>
   <td><strong>Propriedade</strong></td>
   <td><strong>Descrição</strong></td>
  </tr>
  <tr>
   <td><strong><em>Caminho do canal</em></strong></td>
   <td>Selecione o caminho absoluto no qual o aplicativo existe.<br /> </td>
  </tr>
  <tr>
   <td><strong><em>Duração (ms)</em></strong></td>
   <td>Selecione toda a duração do canal. Definir a duração como -1 indica que o canal incorporado executará sua duração total em um canal específico.</td>
  </tr>
 </tbody>
</table>

### Página incorporada {#embedded-page}

Uma **Página incorporada** permite adicionar uma página incorporada ao seu projeto. Por exemplo, ela pode ser um aplicativo web ou um catálogo de produtos.

A Página incorporada tem as seguintes propriedades:

<table>
 <tbody>
  <tr>
   <td><strong>Propriedade</strong></td>
   <td><strong>Descrição</strong></td>
  </tr>
  <tr>
   <td><strong><em>Caminho da página<br /> </em></strong></td>
   <td>Selecione o caminho absoluto onde o canal existe.<br /> </td>
  </tr>
  <tr>
   <td><strong><em>Duração (ms)</em></strong></td>
   <td>Selecione toda a duração do canal. Definir a duração como -1 indica que o canal incorporado executará sua duração total em um canal específico.</td>
  </tr>
 </tbody>
</table>

### Sequência incorporada {#embedded-sequence}

>[!NOTE]
>
>Refer to [Embedded Sequences](embedded-sequences.md) under Authoring Screens section, to learn in detail about embedded sequences.

Uma sequência incorporada permite adicionar um canal de sequência incorporada ao seu canal existente (com outros ativos).

A Sequência incorporada tem as seguintes propriedades de página:

<table>
 <tbody>
  <tr>
   <td><strong>Propriedade</strong></td>
   <td><strong>Descrição</strong></td>
  </tr>
  <tr>
   <td>Caminho do canal</td>
   <td>Selecione o caminho absoluto da sequência que você deseja incluir no seu canal.<br /> </td>
  </tr>
  <tr>
   <td><strong><em>Duração (ms)</em></strong></td>
   <td>Selecione toda a duração do canal. Definir a duração como -1 indica que o canal incorporado executará sua duração total em um canal específico.</td>
  </tr>
  <tr>
   <td><strong><em>Estratégia</em></strong></td>
   <td>Set it to <strong>original</strong> or <strong>single</strong>. Setting the value to <strong>original</strong> means that the subsequence will run fully on each cycle of the parent sequence. The other possible value is <strong>single</strong> and that would only show one item of the subsequence on each run (for instance, the 1st item on the first loop, 2nd item on the second loop, and so on.)</td>
  </tr>
 </tbody>
</table>

### Sequência incorporada dinâmica {#dynamic-embedded-sequence}

Uma sequência incorporada dinâmica permite adicionar uma sequência semelhante à mencionada acima, exceto pela função do canal.

Refer to [Embedded Sequences](embedded-sequences.md) under Authoring Screens section, to learn in detail about embedded sequences.

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
   <td>Selecione toda a duração do canal. Definir a duração como -1 indica que o canal incorporado executará sua duração total em um canal específico.</td>
  </tr>
  <tr>
   <td><strong><em>Estratégia</em></strong></td>
   <td>Set it to <strong>original</strong> or <strong>single</strong>. Setting the value to <strong>original</strong> means that the subsequence will run fully on each cycle of the parent sequence. The other possible value is <strong>single</strong> and that would only show one item of the subsequence on each run (for instance, the 1st item on the first loop, 2nd item on the second loop, and so on.)</td>
  </tr>
 </tbody>
</table>

### Fragmento de experiência {#experience-fragment}

Um Fragmento de experiência permite que você adicione um fragmento de experiência (grupo de um ou mais componentes, incluindo conteúdo e layout que podem ser referenciados nas páginas) ao canal do AEM Screens. Arraste e solte o componente no editor de AEM e selecione o fragmento da experiência.

Para saber mais sobre como criar um fragmento de experiência e aproveitá-lo em um projeto do AEM Screens, consulte [Uso de fragmentos](experience-fragments-in-screens.md)de experiência.

![exp](assets/exp.gif)

| **Propriedade** | **Descrição** |
|---|---|
| **Fragmento de experiência** |
| ***Fragmento de experiência*** | Selecione o fragmento da experiência. |
| ***Duração*** | Selecione a duração inteira do fragmento de experiência que é reproduzido no canal. |
| **Configuração offline** |
| ***Bibliotecas do lado do cliente*** | Arquivos Javascript e CSS. |
| ***Arquivos estáticos*** | Arquivos estáticos que você pode adicionar como configurações offline ao fragmento da sua experiência. |

>[!NOTE]
>
>As bibliotecas **do lado do** cliente e os arquivos **** estáticos adicionados a partir desse componente serão adicionados às bibliotecas **do lado do** cliente já configuradas e aos arquivos estáticos adicionados das **propriedades** do fragmento de experiência.

### Imagem {#image}

Um componente Imagem permite adicionar uma imagem ao seu canal.

O ativo de imagem possui três guias: **Imagem**, **Acessibilidade** e **Sequência**:

| **Propriedade** | **Descrição** |
|---|---|
| **Imagem** |
| ***Ativos da imagem*** | Selecione o ativo da imagem. |
| ***Título*** | Título da imagem. |
| ***Vincular ao*** | Adicione um link à imagem. |
| ***Descrição*** | Breve descrição da imagem. |
| ***Tamanho*** | Tamanho da imagem. |
| **Acessibilidade** |
| ***Texto alternativo*** | Texto alternativo para a imagem. |
| **Sequência** |
| ***Duração*** | Selecione a duração inteira da imagem. Definir a duração como -1 indica que a imagem incorporada executará sua duração total em um canal específico. |

### Transição {#transition}

O componente Transição permite adicionar uma transição ao seu projeto do Screens.

A imagem a seguir mostra o componente de transição (adicionado por arrastar e soltar) ao editor.

![screen_shot_2019-07-25at104237am](assets/screen_shot_2019-07-25at104237am.png)

Selecione o ícone de transição e clique em **Configurar** (ícone de chave) para abrir a caixa de diálogo **Transição** . Essa caixa de diálogo inclui três guias:

* **Transição**
* **Sequência**
* **Ativação**

>[!NOTE]
>
>Por padrão, a sequência é definida como 600 ms. É possível atualizar a sequência de transição para outro valor usando a guia **Sequência** .

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
   <td><p>O tipo da transição entre o elemento antes e o depois. O <strong>Tipo</strong> de transição inclui as seguintes opções:</p>
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
   <td>Selecione a duração inteira da transição. Por padrão, é definido como 600 ms.</td>
  </tr>
  <tr>
   <td><strong>Ativação</strong></td>
   <td></td>
  </tr>
  <tr>
   <td><strong><em>Ativa de</em></strong></td>
   <td>Carimbo de data e hora que descreve de quando a transição pode estar ativa.<br /> </td>
  </tr>
  <tr>
   <td><strong><em>Ativa até</em></strong></td>
   <td>Carimbo de data e hora que descreve até quando a transição pode estar ativa.</td>
  </tr>
  <tr>
   <td><strong><em>Agendamento</em></strong></td>
   <td>Adicione um agendamento predefinido.</td>
  </tr>
 </tbody>
</table>

### Vídeo {#video}

O componente Vídeo permite adicionar um vídeo ao seu projeto do Screens.

O componente Vídeo tem as seguintes propriedades:

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
   <td>Selecione a duração do vídeo. Por padrão, a duração é definida como -1, o que significa que o elemento é executado para sempre. Definir o valor de duração como maior que 0 mostra o elemento pela duração especificada e, em seguida, avança para o próximo.<br /> </td>
  </tr>
  <tr>
   <td><em><strong>Renderização</strong></em></td>
   <td><p>Se a taxa de proporção do vídeo não couber na tela, você poderá ajustar a renderização para <strong>contém</strong> ou <strong>capa</strong>.</p> <p><em>Contém</em> significa que o vídeo completo é exibido, e as áreas ausentes são preenchidas com uma borda preta.</p> <p><em>Capa</em> significa que o vídeo cobre toda a janela de exibição, mas algumas partes que transbordam nas laterais estão ocultas.</p> </td>
  </tr>
  <tr>
   <td><em><strong>Tamanho</strong></em></td>
   <td>Tamanho do vídeo.</td>
  </tr>
 </tbody>
</table>

