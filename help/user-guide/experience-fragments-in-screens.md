---
title: Uso de Fragmentos de experiência
description: Saiba como usar Fragmentos de experiência no AEM Screens.
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
docset: aem65
feature: Authoring Screens, Experience Fragments
role: Admin, Developer
level: Intermediate
exl-id: 13c0d75e-435f-433e-8886-f451df863517
source-git-commit: 8dde26d36847fb496aed6d4bf9732233116b5ea6
workflow-type: tm+mt
source-wordcount: '1102'
ht-degree: 1%

---

# Uso de Fragmentos de experiência {#using-experience-fragments}

Esta página abrange os seguintes tópicos:

* **Visão geral**
* **Uso de fragmentos de experiência no AEM Screens**
* **Propagando Alterações na Página**

## Visão geral {#overview}

Um ***Fragmento de experiência*** é um grupo de um ou mais componentes, incluindo conteúdo e layout que podem ser referenciados nas páginas. Os Fragmentos de experiência podem conter qualquer componente. Por exemplo, ela pode conter um ou vários componentes que podem conter qualquer item em um sistema de parágrafo referenciado na experiência completa ou solicitado por um terceiro endpoint.


## Uso de fragmentos de experiência no AEM Screens {#using-experience-fragments-in-aem-screens}

>[!NOTE]
>O exemplo a seguir usa **`We.Retail`** como um projeto de demonstração em que o Fragmento de experiência é aplicado de um **Sites** para um projeto do AEM Screens.

Como exemplo, o fluxo de trabalho a seguir demonstra o uso de Fragmentos de experiência de `We.Retail` no Sites. Você pode escolher uma página da Web e usar esse conteúdo no canal do AEM Screens em um de seus projetos.

### Pré-requisitos {#pre-requisites}

**Criação de um projeto de demonstração com um canal**

***Criação de um projeto***

1. Para criar um projeto, clique em **Criar projeto do Screens**.
1. Insira o Título como **DemoProject**.
1. Clique em **Salvar**.

A **DemoProject** é adicionado à sua AEM Screens.

***Criação de um canal***

1. Navegue até a **DemoProject** você criou e clique no link **Canais** pasta.

1. Clique em **Criar** na barra de ações para que você possa abrir o assistente.
1. Escolha o **Canal de sequência** do assistente e clique em **Próxima**.

1. Insira o **Título** as **TestChannel** e clique em **Criar**.

A **TestChannel** é adicionado ao seu **DemoProject**.\
![screen_shot_2019-07-29at105101am](assets/screen_shot_2019-07-29at105101am.png)


### Criação de um fragmento de experiência {#creating-an-experience-fragment}

Siga as etapas abaixo para aplicar o conteúdo de **`We.Retail`** ao seu **TestChannel** in **DemoProject**.

1. **Navegue até a página Sites no We.Retail**

   1. Navegue até Sites e clique em **`We.Retail`** > **Estados Unidos** > **Inglês** > **Equipamento** e clique nesta página para usá-la como um Fragmento de experiência para o canal do Screens.

   1. Clique em **Editar** na barra de ação para que você possa abrir a página que deseja usar como fragmento de experiência para o canal do Screens.

1. **Reutilizar o conteúdo**

   1. Clique no fragmento que deseja incluir no canal.
   1. Clique no último ícone à direita para poder abrir o **Converter em fragmento de experiência** caixa de diálogo.

   ![screen_shot_2019-07-29at105314am](assets/screen_shot_2019-07-29at105314am.png)

1. **Criação de um fragmento de experiência**

   1. Escolha o **Ação** as **Criar um novo fragmento de experiência**.

   1. Clique em **Caminho principal**.
   1. Clique em **Modelo**. Escolha o **Fragmento de experiência - Variação de telas** modelo aqui (valor no campo `/libs/settings/screens/experience-fragments/templates/experience-fragment-template-screens`).

   1. Insira o **Título do fragmento** as **FragmentoTelas**.

   1. Para concluir a criação de um novo Fragmento de experiência, clique na marca de seleção.

   ![screen_shot_2019-07-29at105918am](assets/screen_shot_2019-07-29at105918am.png)

   Para selecionar uma opção mais fácil, clique na marca de seleção à direita do campo para abrir a caixa de diálogo de seleção.

1. **Criação de Live Copy do Fragmento de experiência**

   1. Navegue até a página inicial do AEM.
   1. Clique em **Fragmentos de experiência** e destaque a **FragmentoTelas** e clique em **Variação como Live Copy**, conforme mostrado na figura abaixo:

   ![screen_shot_2019-07-29at110443am](assets/screen_shot_2019-07-29at110443am.png)

   c. Clique no link **FragmentoTelas** do **Criar Live Copy** e clique em **Próxima**.

   d. Insira o **Título** e **Nome** as **Screens**.

   e. Clique em **Criar** para criar a Live Copy.

   f. Clique em **Concluído** para que você possa voltar para o **FragmentoTelas** página.

   ![screen_shot_2019-07-29at110616am](assets/screen_shot_2019-07-29at110616am.png)

   >[!NOTE]
   >
   >Depois de criar um fragmento do AEM Screens, você pode editar as propriedades do fragmento. Clique no fragmento e em **Propriedades** na barra de ações.

   **Edição de propriedades de um fragmento do Screens**

   1. Navegue até a **FragmentoTelas** (você criou nas etapas anteriores) e clique em **Propriedades** na barra de ações.

   1. Clique em **Configuração offline** conforme mostrado na figura abaixo.

   Você pode adicionar o **Bibliotecas do cliente** (Java™ e CSS) e **Arquivos estáticos** ao seu Fragmento de experiência.

   O exemplo a seguir mostra a adição de bibliotecas do lado do cliente e das fontes como parte dos arquivos estáticos ao seu Fragmento de experiência.  ![fragmento](assets/fragment.gif)

1. **Uso do fragmento de experiência como um componente no canal do Screens**

   1. Navegue até o canal do Screens onde deseja usar o **Screens** fragmento.
   1. Clique em **TestChannel** e clique em **Editar** na barra de ações.

   1. Clique no ícone componentes na guia lateral.
   1. Arraste e solte a **Fragmento de experiência** ao seu canal.

   ![screen_shot_2019-07-29at123115pm](assets/screen_shot_2019-07-29at123115pm.png)

   e. Clique no botão **Fragmento de experiência** e clique no ícone superior esquerdo (chave inglesa) para abrir a **Fragmento de experiência** caixa de diálogo.

   f. Clique no botão **Screens** Live Copy do fragmento que você criou no *Etapa 3* in **Caminho**.

   ![screen_shot_2019-07-26at82650pm](assets/screen_shot_2019-07-26at82650pm.png)

   f. Clique no botão **Screens** Live Copy do fragmento que você criou no *Etapa 3* no **Fragmento de experiência**.

   ![screen_shot_2019-07-26at82509pm](assets/screen_shot_2019-07-26at82509pm.png)

   h. Insira os milissegundos em **Duração**.

   i. Clique no botão **Configuração offline** do **Fragmentos de experiência** para que você possa definir as bibliotecas do lado do cliente e os arquivos estáticos.

   >[!NOTE]
   >
   >Para adicionar bibliotecas do lado do cliente ou os arquivos estáticos, além do que você configurou na etapa (4), é possível adicionar do **Configuração offline** na guia **Fragmento de experiência** caixa de diálogo.

   ![screen_shot_2019-07-26at82844pm](assets/screen_shot_2019-07-26at82844pm.png)

   j. Clique na marca de seleção para concluir o processo.

### Validar o resultado {#validating-the-result}

Após concluir as etapas anteriores, você pode validar o fragmento de experiência no **ChannelOne** por:

1. Navegar até o **TestChannel**.
1. Selecionar o **Visualizar** na barra de ações.

Exibir o conteúdo do **Sites** (Live Copy do Fragmento de experiência) no seu canal, conforme mostrado na figura abaixo:\
![screen_shot_2018-06-08at120739pm](assets/screen_shot_2018-06-08at120739pm.png)

## Propagando Alterações na Página {#propagating-changes-from-the-master-page}

***Live Copy*** refere-se à cópia (da origem) mantida pelas ações de sincronização, conforme definido pelas configurações de implantação.

Como o fragmento de experiência que você criou é uma Live Copy do **Sites** e alterar esse fragmento específico da página principal, visualize as alterações no canal. Ou visualize o destino em que você usou o Fragmento de experiência.

>[!NOTE]
>
>Para obter mais informações sobre a Live Copy, consulte Reutilizar conteúdo: gerenciador de vários sites e Live Copy.

Siga as etapas abaixo para propagar alterações do canal principal para o canal de destino:

1. Clique no Fragmento de experiência na **Sites** (principal) e clique no ícone de lápis para editar os itens no Fragmento de experiência.

   ![screen_shot_2018-06-08at122655pm](assets/screen_shot_2018-06-08at122655pm.png)

1. Clique no Fragmento de experiência e clique na chave inglesa para abrir a caixa de diálogo e editar as imagens.

   ![screen_shot_2018-06-08at25031pm](assets/screen_shot_2018-06-08at25031pm.png)

1. A variável **Grade de produtos** é aberta.

   ![screen_shot_2018-06-08at25306pm](assets/screen_shot_2018-06-08at25306pm.png)

1. É possível editar qualquer uma das imagens. Por exemplo, aqui a primeira imagem é substituída neste fragmento.

   ![screen_shot_2018-06-08at25608pm](assets/screen_shot_2018-06-08at25608pm.png)

1. Clique no Fragmento de experiência e clique no ícone Implantação para que você possa propagar alterações no fragmento usado no canal.

   ![screen_shot_2018-06-08at31352pm](assets/screen_shot_2018-06-08at31352pm.png)

1. Clique em Implantação.

   Observe que as alterações são implementadas.

   ![screen_shot_2018-06-08at32148pm](assets/screen_shot_2018-06-08at32148pm.png)

### Validar as alterações {#validating-the-changes}

Siga as etapas abaixo para confirmar as alterações no canal:

1. Navegue até a **Screens** > **Canais** > **TestChannel**.

1. Clique em **Visualizar** na barra de ações.

A imagem a seguir ilustra as alterações no **TestChannel**:\
![screen_shot_2018-06-08at33351pm](assets/screen_shot_2018-06-08at33351pm.png)
