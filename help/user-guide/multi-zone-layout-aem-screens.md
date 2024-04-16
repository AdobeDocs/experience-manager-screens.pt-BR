---
title: Layout de várias zonas
description: Saiba como criar conteúdo com várias zonas e usar vários ativos, como vídeos, imagens e texto, que podem ser combinados em uma única tela no AEM Screens.
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: authoring
noindex: true
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 901ed50e-d3f0-4c85-ad79-6c4595382759
source-git-commit: fff2df02661fc3fb3098be40e090b8bc6925bcc2
workflow-type: tm+mt
source-wordcount: '1124'
ht-degree: 0%

---

# Layout de várias zonas {#multi-zone-layout}

A página seguinte descreve o uso do layout de várias zonas e aborda os seguintes tópicos:

* Visão geral
* Criação de layout de várias zonas
* Pré-requisitos
* Uso de ativos únicos em uma ou mais regiões
* Uso de conteúdo sequenciado em uma ou mais regiões

## Visão geral {#overview}

***Layout de várias zonas*** O permite criar vários conteúdos de zona e usar vários ativos, como vídeos, imagens e texto, que podem ser combinados em uma única tela. Você pode inserir imagens, vídeos e texto, permitindo que todos se misturem e criem uma experiência digital intuitiva.

De acordo com os requisitos do projeto, às vezes você precisa de várias zonas em um canal e editá-las como uma unidade abrangente. Por exemplo, uma sequência de produtos com um feed de mídia social relacionado que é executado em três zonas separadas em um único canal.

>[!NOTE]
>Em canais de várias zonas, o agendamento no nível do ativo não é recomendado devido a possíveis conflitos e comportamento não intencional. Se a programação no nível do ativo for necessária, é recomendável criar um canal de sequência separado e aplicar a lógica de programação nesse canal. Em seguida, incorpore o canal de sequência no canal de várias regiões.

### Pré-requisitos {#prerequisites}

Antes de começar a implementar essa funcionalidade, verifique se você tem o conhecimento conceitual sobre:

* [Criação de um projeto do AEM Screens](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/authoring/setting-up-projects/creating-a-screens-project)
* [Criação de uma exibição](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/authoring/setting-up-projects/managing-displays)
* [Atribuição de um Canal a uma Exibição](/help/user-guide/channel-assignment.md)

## Criação de layout de várias zonas {#creating-multi-zone-layout}

Ao criar um canal, é possível usar diferentes modelos para criar zonas no canal. Você pode adicionar uma única imagem, vídeo ou um canal incorporado que permite que vários ativos sejam exibidos em uma sequência.

**Criação de um canal**

1. Clique no link Adobe Experience Manager (canto superior esquerdo) e **Screens**. Como alternativa, você pode ir diretamente para: `http://localhost:4502/screens.html/content/screens`.
1. Navegue até **Canais** e clique em **Criar** na barra de ações.

1. Clique em **Canal de tela dividida 1x2** do **Criar** assistente.

1. Clique em **Próxima** e insira o **título** as **MultiZone**.

1. Clique em **Criar** para concluir a criação do canal.

### Uso de ativos únicos em uma ou mais regiões {#using-single-assets-in-one-or-more-zones}

Você pode usar ativos únicos, como uma imagem ou um vídeo, em todas as zonas individuais. Siga as etapas abaixo para a implementação:

1. **Adicionar conteúdo ao canal**

   1. Navegue até **Zonas** > **Canais**> **MultiZone**.
   1. Clique em **MultiZone** canal e clique em **Editar** na barra de ações.

1. **Adicionar imagens ao canal**

   Para reproduzir uma única imagem ou um vídeo em duas zonas, basta arrastar e soltar uma imagem em cada zona no editor de canais, como mostrado na figura abaixo:

   ![imagem](/help/user-guide/assets/multi-zone/multizone-img3.png)

### Uso de conteúdo sequenciado em uma ou mais regiões {#using-sequenced-content-in-one-or-more-zones}

Se quiser que as zonas exibam uma sequência de imagens e um vídeo nas diferentes zonas, siga as etapas abaixo para obter detalhes.

1. **Criação de uma pasta de canal**

   1. Navegue até **Zonas** > **MultiZone** > **Canais** e clique em **Criar** na barra de ações.
   1. Clique em **Pasta de canais** do **Criar** e clique em **Próxima**.
   1. Insira o título como **EmbeddedChannels** e clique em **Criar**.

   ![screen_shot_2018-12-19at125428pm](assets/screen_shot_2018-12-19at125428pm.png)

1. **Adição de mais dois canais à Pasta de canal**

   1. Navegue até **Zonas** > **Canais** > **EmbeddedChannels** e clique em **Criar** na barra de ações.
   1. Clique em **Canal de sequência** do **Criar** assistente para criar um canal intitulado como **`Zone1`**.
   1. Clique em **`Zone1`** e clique em **Editar** na barra de ações.
   1. Arraste e solte algumas imagens neste canal.
   1. Da mesma forma, crie outro canal de sequência chamado de **`Zone2`** in **EmbeddedChannels** pasta.
   1. Arraste e solte um vídeo neste canal.

   A figura a seguir mostra os canais **`Zone1`** e **`Zone2`**:

   ![screen_shot_2018-12-19at125930pm](assets/screen_shot_2018-12-19at125930pm.png)

   As imagens adicionadas ao editor de **`Zone1`** canal de sequência são mostrados abaixo:

   ![screen_shot_2018-12-19at125930pm](/help/user-guide/assets/multi-zone/multizone-img4.png)

   O vídeo foi adicionado ao editor do **`Zone2`** o canal de sequência é mostrado abaixo:

   ![screen_shot_2018-12-19at125930pm](/help/user-guide/assets/multi-zone/multizone-img5.png)

1. **Adicionar sequências incorporadas (componente) ao canal principal (MultiZone)**

   1. Navegue até **Zonas** > **Canais** > **MultiZone**.
   1. Clique em **Editar** na barra de ações.
   1. Arraste e solte a **Sequência incorporada** componente às duas regiões.
   1. Clique na sequência incorporada em uma das zonas.
   1. Clique em **Configurar** (chave inglesa) para uma das sequências incorporadas no editor.
   1. Clique no caminho do canal como **Zonas** > **Canais** > **EmbeddedChannels** > **`Zone1`**, conforme mostrado na figura abaixo.
   1. Da mesma forma, adicione a variável **`Zone2`** para outro componente de sequência incorporado no editor.

      ![imagem](/help/user-guide/assets/multi-zone/multizone-3.png)

### Criação de um local e uma exibição {#creating-location}

Crie um local e uma exibição para exibir o conteúdo no reprodutor do AEM Screens.

1. **Criação de um local**

   1. Navegue até **Zonas** > **Localizações** pasta.
   1. Clique em **Localizações** e clique em **Criar** na barra de ações.
   1. Clique em **Localização** do **Criar** e clique em **Próxima**.
   1. Insira o **Título** as **San Jose** e clique em **Criar**.

1. **Criação de uma exibição**

   1. Navegue até **Zonas** > **Localizações** pasta.
   1. Clique em **San Jose** e clique em **Criar** na barra de ações.
   1. Clique em **Exibir** do **Criar** e clique em **Próxima**.
   1. Insira o **Título** as **Lobby** e clique em **Criar**.

### Atribuição de canais à exibição {#channel-channel}

Atribua os canais à exibição para visualizar o conteúdo. Siga as etapas abaixo para atribuir o canal à exibição.

1. **Atribuição de canal à exibição**

   1. Navegue até **Zonas** > **Localizações** > **San Jose**> **Lobby**.
   1. Clique em **Lobby** e clique em **Atribuir canal** na barra de ações.
   1. Insira o caminho para o **MultiZone** entrada de canal **Caminho do canal**.
   1. Defina o **Eventos suportados** as **Carga inicial**, **Tela inativa**, e **Temporizador**.
   1. Clique em **Salvar**.

      ![imagem](/help/user-guide/assets/multi-zone/multizone-img9.png)
   1. Da mesma forma, atribua os outros dois canais incorporados (**`Zone1`** e **`Zone2`**) para essa exibição.
   1. Depois de atribuir todos os três canais à variável **Lobby** ser capaz de visualizar os canais atribuídos a partir do painel de exibição.

      ![imagem](/help/user-guide/assets/multi-zone/multizone-img8.png)


      >[!IMPORTANT]
      >
      >Depois de atribuir o canal principal (neste caso, **MultiZone**) para a exibição, é obrigatório atribuir os outros dois canais incorporados **`Zone1`** e **`Zone2`** também para a mesma exibição.

### Registrando o dispositivo {#registering-device}

Depois de configurar um local e uma exibição, siga as etapas abaixo para registrar o dispositivo e atribuir a exibição ao dispositivo.

1. **Registrando o dispositivo**

   1. Navegue até **Zonas** > **Dispositivos** pasta.
   1. Clique em **Dispositivos** e clique em **Gerenciador de dispositivos** na barra de ações.
   1. Clique em **Registro do dispositivo** e clique no dispositivo pendente na lista.

      >[!NOTE]
      > O título do dispositivo deve corresponder ao token do dispositivo (**Token** campo) exibido na **Registro do dispositivo** guia.

   1. Se o título corresponder ao token do dispositivo, clique no dispositivo e em **Registrar dispositivo** na barra de ações.
   1. Se o código de registro corresponder ao código no reprodutor do Screens **Registro do dispositivo** clique em **Validar** na barra de ações.
      ![imagem](/help/user-guide/assets/multi-zone/multizone-img6.png)
   1. Insira o **Título** as **`Chrome-Device1`** e clique em **Registrar**.
   1. Clique em **Atribuir exibição** e clique no caminho para a configuração do dispositivo.

   >[!NOTE]
   >Se estiver tentando exibir o conteúdo no reprodutor do Screens, clique em **Atualizar conteúdo offline** no painel do canal para cada um dos canais atribuídos à exibição.

### Exibir o resultado {#viewing-the-result}

Quando você implementa layouts de várias regiões usando as etapas anteriores, a seguinte saída é exibida.

Marque o reprodutor do Screens para que você possa exibir a saída que exibe o conteúdo em duas zonas diferentes. As zonas esquerda e direita (ambas usam uma sequência incorporada como um componente).

A zona esquerda é um canal de sequência e a zona direita inclui um vídeo.

![novo2-1](/help/user-guide/assets/multi-zone/Multi-gif.gif)
