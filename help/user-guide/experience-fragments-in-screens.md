---
title: Uso de Fragmentos de experiência
seo-title: Using Experience Fragments
description: Siga esta página para saber mais sobre como usar Fragmentos de experiência no AEM Screens.
seo-description: Follow this page to learn about using Experience Fragments in AEM Screens.
uuid: 6ee16a94-3c53-43e0-99d5-c35cb9e01120
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: 0e88e9e0-a95b-4acd-98ea-499d4d4e3c99
docset: aem65
feature: Authoring Screens, Experience Fragments
role: Admin, Developer
level: Intermediate
exl-id: 13c0d75e-435f-433e-8886-f451df863517
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '1112'
ht-degree: 1%

---

# Uso de Fragmentos de experiência {#using-experience-fragments}

Esta página abrange os seguintes tópicos:

* **Visão geral**
* **Uso de fragmentos de experiência no AEM Screens**
* **Propagando Alterações na Página**

## Visão geral {#overview}

Um ***Fragmento de experiência*** é um grupo de um ou mais componentes, incluindo conteúdo e layout que podem ser referenciados nas páginas. Os fragmentos de experiência podem conter qualquer componente, como um ou vários componentes que podem conter qualquer item em um sistema de parágrafo, que será referenciado na experiência completa ou solicitado por um terceiro endpoint.


## Uso de fragmentos de experiência no AEM Screens {#using-experience-fragments-in-aem-screens}

>[!NOTE]
>O exemplo a seguir usa **We.Retail** como um projeto de demonstração em que o Fragmento de experiência é aproveitado de um **Sites** para um projeto do AEM Screens.

Como exemplo, o fluxo de trabalho a seguir demonstra o uso de fragmentos de experiência do We.Retail no Sites. Você pode escolher uma página da Web e aproveitar esse conteúdo no seu canal do AEM Screens em um de seus projetos.

### Pré-requisitos {#pre-requisites}

**Criação de um projeto de demonstração com um canal**

***Criação de um projeto***

1. Clique em **Criar projeto do Screens** para criar um novo projeto.
1. Insira o Título como **DemoProject**.
1. Clique em **Salvar**.

A **DemoProject** serão adicionados à sua AEM Screens.

***Criação de um canal***

1. Navegue até a **DemoProject** você criou e selecione a variável **Canais** pasta.

1. Clique em **Criar** na barra de ações para abrir o assistente.
1. Escolha o **Canal de sequência** do assistente e clique em **Próxima**.

1. Insira o **Título** as **TestChannel** e clique em **Criar**.

A **TestChannel** será adicionado ao seu **DemoProject**.\
![screen_shot_2019-07-29at105101am](assets/screen_shot_2019-07-29at105101am.png)


### Criação de um fragmento de experiência {#creating-an-experience-fragment}

Siga as etapas abaixo para aproveitar o conteúdo de **We.Retail** ao seu **TestChannel** in **DemoProject**.

1. **Navegue até a página Sites no We.Retail**

   1. Navegue até Sites e selecione **We.Retail** -> **Estados Unidos** -> **Inglês** -> **Equipamento** e selecione esta página para usá-la como um fragmento de experiência para o canal do Screens.

   1. Clique em **Editar** na barra de ações para abrir a página que deseja usar como fragmento de experiência para o canal do Screens.

1. **Reutilizar o conteúdo**

   1. Selecione o fragmento que deseja incluir no canal.
   1. Clique no último ícone à direita para abrir a **Converter em fragmento de experiência** caixa de diálogo.

   ![screen_shot_2019-07-29at105314am](assets/screen_shot_2019-07-29at105314am.png)

1. **Criação do fragmento de experiência**

   1. Escolha o **Ação** as **Criar um novo fragmento de experiência**.

   1. Selecione o **Caminho principal**.
   1. Selecione o **Modelo**. Escolha o **Fragmento de experiência - Variação de telas** modelo aqui (valor no campo `/libs/settings/screens/experience-fragments/templates/experience-fragment-template-screens`).

   1. Insira o **Título do fragmento** as **FragmentoTelas**.

   1. Clique na marca de seleção para concluir a criação de um novo fragmento de experiência.

   ![screen_shot_2019-07-29at105918am](assets/screen_shot_2019-07-29at105918am.png)

   Observação: para facilitar a seleção de uma opção, clique na marca de seleção à direita dos campos para abrir a caixa de diálogo de seleção.

1. **Criação de Live Copy do Fragmento de experiência**

   1. Navegue até a página inicial do AEM.
   1. Selecionar **Fragmentos de experiência** e destaque a **FragmentoTelas** e clique em **Variação como Live Copy**, conforme mostrado na figura abaixo:

   ![screen_shot_2019-07-29at110443am](assets/screen_shot_2019-07-29at110443am.png)

   c. Selecione o **FragmentoTelas** de **Criar Live Copy** e clique em **Próxima**.

   d. Insira o **Título** e **Nome** as **Screens**.

   e. Clique em **Criar** para criar a Live Copy.

   f. Clique em **Concluído** para voltar para **FragmentoTelas** página.

   ![screen_shot_2019-07-29at110616am](assets/screen_shot_2019-07-29at110616am.png)

   >[!NOTE]
   >
   >Depois de criar o fragmento do Screens, você pode editar as propriedades do fragmento. Selecione o fragmento e clique em **Propriedades** na barra de ações.

   **Edição de propriedades de um fragmento do Screens**

   1. Navegue até a **FragmentoTelas** (você criou nas etapas anteriores) e clique em **Propriedades** na barra de ações.

   1. Selecione o **Configuração offline** conforme mostrado na figura abaixo.

   Você pode adicionar o **Bibliotecas do cliente** (java e css) e **Arquivos estáticos** ao seu fragmento de experiência.

   O exemplo a seguir mostra a adição de bibliotecas do lado do cliente e das fontes como parte dos arquivos estáticos ao fragmento de experiência.  ![fragmento](assets/fragment.gif)

1. **Uso do fragmento de experiência como um componente no canal do Screens**

   1. Navegue até o canal do Screens onde deseja usar o **Screens** fragmento.
   1. Selecione o **TestChannel** e clique em **Editar** na barra de ações.

   1. Clique no ícone componentes na guia lateral.
   1. Arraste e solte a **Fragmento de experiência** ao seu canal.

   ![screen_shot_2019-07-29at123115pm](assets/screen_shot_2019-07-29at123115pm.png)

   e. Selecione a **Fragmento de experiência** e selecione o ícone superior esquerdo (chave inglesa) para abrir o **Fragmento de experiência** caixa de diálogo.

   f. Selecione o **Screens** live copy do fragmento que você criou no *Etapa 3* in **Caminho**.

   ![screen_shot_2019-07-26at82650pm](assets/screen_shot_2019-07-26at82650pm.png)

   f. Selecione o **Screens** live copy do fragmento que você criou no *Etapa 3* no **Fragmento de experiência**.

   ![screen_shot_2019-07-26at82509pm](assets/screen_shot_2019-07-26at82509pm.png)

   h. Insira os milissegundos em **Duração**.

   i. Selecione a **Configuração offline** do **Fragmentos de experiência** para definir as bibliotecas do lado do cliente e os arquivos estáticos.

   >[!NOTE]
   >
   >Se você quiser adicionar bibliotecas do lado do cliente ou os arquivos estáticos além do que você configurou na etapa (4), é possível adicionar do **Configuração offline** na guia **Fragmento de experiência** caixa de diálogo.

   ![screen_shot_2019-07-26at82844pm](assets/screen_shot_2019-07-26at82844pm.png)

   j. Clique na marca de seleção para concluir o processo.

### Validar o resultado {#validating-the-result}

Após a conclusão das etapas anteriores, você pode validar o fragmento de experiência no **ChannelOne** por:

1. Navegar até o **TestChannel**.
1. Selecionar o **Visualizar** na barra de ações.

Você visualizará o conteúdo do **Sites** (live-copy do fragmento de experiência) no seu canal, conforme mostrado na figura abaixo:\
![screen_shot_2018-06-08at120739pm](assets/screen_shot_2018-06-08at120739pm.png)

## Propagando Alterações na Página {#propagating-changes-from-the-master-page}

***Live Copy*** refere-se à cópia (da origem) mantida pelas ações de sincronização, conforme definido pelas configurações de implantação.

Como o fragmento de experiência, criamos uma Live Copy do **Sites** páginas, portanto, se você fizer alterações nesse fragmento específico na página principal, visualizará as alterações no canal ou no destino em que usou o Fragmento de experiência.

>[!NOTE]
>
>Para obter mais informações sobre a Live Copy, consulte Reutilizar conteúdo: gerenciador de vários sites e Live Copy.

Siga as etapas abaixo para propagar as alterações do canal principal para o canal de destino:

1. Selecione o Fragmento de experiência na **Sites** (principal) e clique no ícone de lápis para editar os itens no Fragmento de experiência.

   ![screen_shot_2018-06-08at122655pm](assets/screen_shot_2018-06-08at122655pm.png)

1. Selecione o Fragmento de experiência e clique na chave inglesa para abrir a caixa de diálogo e editar as imagens.

   ![screen_shot_2018-06-08at25031pm](assets/screen_shot_2018-06-08at25031pm.png)

1. A variável **Grade de produtos** é aberta.

   ![screen_shot_2018-06-08at25306pm](assets/screen_shot_2018-06-08at25306pm.png)

1. É possível editar qualquer uma das imagens. Por exemplo, aqui a primeira imagem é substituída neste fragmento.

   ![screen_shot_2018-06-08at25608pm](assets/screen_shot_2018-06-08at25608pm.png)

1. Selecione o Fragmento de experiência e clique no ícone Implantação para propagar alterações no fragmento usado no canal.

   ![screen_shot_2018-06-08at31352pm](assets/screen_shot_2018-06-08at31352pm.png)

1. Clique em Implantação para confirmar as alterações.

   Você verá que as alterações são implementadas.

   ![screen_shot_2018-06-08at32148pm](assets/screen_shot_2018-06-08at32148pm.png)

### Validar as alterações {#validating-the-changes}

Siga as etapas abaixo para confirmar as alterações no canal:

1. Navegue até a **Screens** -> **Canais** -> **TestChannel**.

1. Clique em **Visualizar** na barra de ações para confirmar as alterações.

A imagem a seguir ilustra as alterações no **TestChannel**:\
![screen_shot_2018-06-08at33351pm](assets/screen_shot_2018-06-08at33351pm.png)
