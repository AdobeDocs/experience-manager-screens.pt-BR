---
title: Uso de Fragmentos de experiência
seo-title: Uso de Fragmentos de experiência
description: 'Siga esta página para saber mais sobre o uso de Fragmentos de experiência no AEM Screens. '
seo-description: 'Siga esta página para saber mais sobre o uso de Fragmentos de experiência no AEM Screens. '
uuid: 6ee16a94-3c53-43e0-99d5-c35cb9e01120
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: 0e88e9e0-a95b-4acd-98ea-499d4d4e3c99
docset: aem65
translation-type: tm+mt
source-git-commit: 2a3bbdd283f983cbdb5f21b606f508603385e041
workflow-type: tm+mt
source-wordcount: '1100'
ht-degree: 8%

---


# Uso de Fragmentos de experiência {#using-experience-fragments}

Esta página aborda os seguintes tópicos:

* **Visão geral**
* **Usando Fragmentos de experiência no AEM Screens**
* **Propagando alterações na página**

## Visão geral {#overview}

Um ***Fragmento de experiência*** é um grupo de um ou mais componentes, incluindo o conteúdo e o layout que podem ser referenciados nas páginas. Fragmentos de experiência podem conter qualquer componente, como um ou vários componentes que podem conter qualquer elemento dentro de um sistema de parágrafos, que será referenciado na experiência completa ou solicitado por um terceiro terminal.


## Usando Fragmentos de experiência no AEM Screens {#using-experience-fragments-in-aem-screens}

>[!NOTE]
>O exemplo a seguir usa **We.Retail** como um projeto de demonstração de onde o Fragmento de experiência é aproveitado de uma página **Sites** para um projeto da AEM Screens.

Como exemplo, o fluxo de trabalho a seguir demonstra o uso de fragmentos de experiência de We.Retail em Sites. Você pode escolher uma página da Web e aproveitar esse conteúdo em seu canal AEM Screens em um de seus projetos.

### Pré-requisitos {#pre-requisites}

**Criação de um projeto de demonstração com um Canal**

***Criação de um projeto***

1. Clique em **Criar projeto do Screens** para criar um novo projeto.
1. Insira o Título como **DemoProject**.
1. Clique em **Salvar**.

Um **DemoProject** será adicionado ao seu AEM Screens.

***Criação de um canal***

1. Navegue até a pasta **DemoProject** que você criou e selecione a pasta **Canais**.

1. Clique em **Criar** na barra de ações para abrir o assistente.
1. Escolha o modelo **Canal de sequência** do assistente e clique em **Próximo**.

1. Digite **Title** como **TestChannel** e clique em **Criar**.

Um **TestChannel** será adicionado ao **DemoProject**.\
![screen_shot_2019-07-29at105101am](assets/screen_shot_2019-07-29at105101am.png)


### Criação de um fragmento de experiência {#creating-an-experience-fragment}

Siga as etapas abaixo para aproveitar o conteúdo de **We.Retail** para seu **TestChannel** em **DemoProject**.

1. **Navegue até a página Sites em We.Retail**

   1. Navegue até Sites e selecione **We.Retail In-Store** -> **Canais** ->**Canal Inativo - Night** e selecione esta página para usá-la como um fragmento de experiência para o canal do Screens.

   1. Clique em **Editar** na barra de ações para abrir a página que deseja usar como um fragmento de experiência para o seu canal do Screens.

1. **Reutilizar o conteúdo**

   1. Selecione o fragmento que deseja incluir no seu canal.
   1. Clique no último ícone à direita para abrir a caixa de diálogo **Converter em fragmento de experiência**.

   ![screen_shot_2019-07-29at105314am](assets/screen_shot_2019-07-29at105314am.png)

1. **Criar fragmento de experiência**

   1. Escolha **Action** como **Criar um novo fragmento de experiência**.

   1. Selecione **Caminho principal**.
   1. Selecione **Modelo**. Escolha o modelo **Fragmento de experiência - Variação de telas** aqui.

   1. Insira **Título do fragmento** como **ScreensFragment**.

   1. Clique na marca de seleção para concluir a criação de um novo fragmento de experiência.

   ![screen_shot_2019-07-29at105918am](assets/screen_shot_2019-07-29at105918am.png)

1. **Criar Live Copy do fragmento de experiência**

   1. Navegue até o home page AEM.
   1. Selecione **Fragmentos de experiência** e realce **ScreensFragment** e clique em **Variação como live-copy**, conforme mostrado na figura abaixo:

   ![screen_shot_2019-07-29at110443am](assets/screen_shot_2019-07-29at110443am.png)

   c. Selecione **ScreensFragment** do assistente **Criar Live Copy** e clique em **Próximo**.

   d. Digite **Title** e **Name** como **Screens**.

   e. Clique em **Criar** para criar a Live Copy.

   f. Clique em **Concluído** para voltar à página **ScreensFragment**.

   ![screen_shot_2019-07-29at110616am](assets/screen_shot_2019-07-29at110616am.png)

   >[!NOTE]
   >
   >Depois de criar o fragmento Screens, você pode editar as propriedades do fragmento. Selecione o fragmento e clique em **Propriedades** na barra de ações.

   **Editar propriedades de um fragmento de tela**

   1. Navegue até **ScreensFragment** (você criou nas etapas anteriores) e clique em **Propriedades** na barra de ações.

   1. Selecione a guia **Config offline**, conforme mostrado na figura abaixo.

   Você pode adicionar as **Bibliotecas do lado do cliente** (java e css) e **Arquivos estáticos** ao fragmento da experiência.

   O exemplo a seguir mostra a adição de bibliotecas do lado do cliente e de fontes como parte de arquivos estáticos ao fragmento da experiência.  ![fragmento](assets/fragment.gif)

1. **Uso do fragmento de experiência como componente no Canal do Screens**

   1. Navegue até o canal Screens onde deseja usar o fragmento **Screens**.
   1. Selecione **TestChannel** e clique em **Editar** na barra de ações.

   1. Clique no ícone de componentes na guia lateral.
   1. Arraste e solte o **Fragmento de experiência** no seu canal.

   ![screen_shot_2019-07-29at123115pm](assets/screen_shot_2019-07-29at123115pm.png)

   e. Selecione o componente **Fragmento de experiência** e selecione o ícone superior esquerdo (chave) para abrir a caixa de diálogo **Fragmento de experiência**.

   f. Selecione a **Screens** cópia ativa do fragmento criado em *Etapa 3* em **Caminho**.

   ![screen_shot_2019-07-26at82650pm](assets/screen_shot_2019-07-26at82650pm.png)

   f. Selecione a **Screens** cópia ativa do fragmento criado em *Etapa 3* no **Fragmento de experiência**.

   ![screen_shot_2019-07-26at82509pm](assets/screen_shot_2019-07-26at82509pm.png)

   h. Digite os milissegundos em **Duration**.

   i. Selecione **Configuração offline** na caixa de diálogo **Fragmentos de experiência** para definir as bibliotecas do lado do cliente e os arquivos estáticos.

   >[!NOTE]
   >
   >Se quiser adicionar bibliotecas do lado do cliente ou arquivos estáticos além do que você configurou na etapa 4, adicione a partir da guia **Configuração offline** na caixa de diálogo **Fragmento de experiência**.

   ![screen_shot_2019-07-26at82844pm](assets/screen_shot_2019-07-26at82844pm.png)

   j. Clique na marca de seleção para concluir o processo.

### Validando o resultado {#validating-the-result}

Após concluir as etapas anteriores, você pode validar seu fragmento de experiência em **ChannelOne** ao:

1. Navegando até **TestChannel**.
1. Selecionando **Pré-visualização** na barra de ações.

Você vai visualização o conteúdo da página **Sites** (live-copy do fragmento de experiência) no seu canal, como mostrado na figura abaixo:\
![screen_shot_2018-06-08at120739pm](assets/screen_shot_2018-06-08at120739pm.png)

## Propagando Alterações na Página {#propagating-changes-from-the-master-page}

***A Live*** Copy se refere à cópia (da origem), mantida pelas ações de sincronização, conforme definido pelas configurações de implantação.

Desde o Fragmento de experiência, criamos uma cópia ao vivo das páginas **Sites**, portanto, se você fizer alterações nesse fragmento específico a partir da página principal, você visualização as alterações no canal ou no destino em que usou o Fragmento de experiência.

>[!NOTE]
>
>Para obter mais informações sobre o Live Copy, consulte Reutilizando conteúdo: Gerenciador de vários sites e Live Copy.

Siga as etapas abaixo para propagar as alterações do canal principal para o canal de destino:

1. Selecione o Fragmento de experiência na página **Sites** (principal) e clique no ícone de lápis para editar os itens no Fragmento de experiência.

   ![screen_shot_2018-06-08at122655pm](assets/screen_shot_2018-06-08at122655pm.png)

1. Selecione o Fragmento de experiência e clique no ícone de chave para abrir a caixa de diálogo para editar as imagens.

   ![screen_shot_2018-06-08at25031pm](assets/screen_shot_2018-06-08at25031pm.png)

1. A caixa de diálogo **Grade do Produto** é aberta.

   ![screen_shot_2018-06-08at25306pm](assets/screen_shot_2018-06-08at25306pm.png)

1. É possível editar qualquer uma das imagens. Por exemplo, aqui a primeira imagem é substituída nesse fragmento.

   ![screen_shot_2018-06-08at25608pm](assets/screen_shot_2018-06-08at25608pm.png)

1. Selecione o Fragmento de experiência e clique no ícone de Rollout para propagar as alterações no fragmento usado no seu canal.

   ![screen_shot_2018-06-08at31352pm](assets/screen_shot_2018-06-08at31352pm.png)

1. Clique em Rollout para confirmar as alterações.

   Você verá que as alterações foram distribuídas.

   ![screen_shot_2018-06-08at32148pm](assets/screen_shot_2018-06-08at32148pm.png)

### Validando as Alterações {#validating-the-changes}

Siga as etapas abaixo para confirmar as alterações em seu canal:

1. Navegue até **Screens** -> **Canais** -> **TestChannel**.

1. Clique em **Pré-visualização** na barra de ações para confirmar as alterações.

A imagem a seguir ilustra as alterações em seu **TestChannel**:\
![screen_shot_2018-06-08at33351pm](assets/screen_shot_2018-06-08at33351pm.png)

