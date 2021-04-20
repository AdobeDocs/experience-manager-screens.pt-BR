---
title: Configuração do ContextHub no AEM Screens
seo-title: Configuração do ContextHub no AEM Screens
description: Siga esta página para saber mais sobre o ContextHub no mecanismo de direcionamento para definir o armazenamento de dados com o objetivo de alterar o conteúdo do acionador de dados.
seo-description: Siga esta página para saber mais sobre o ContextHub no mecanismo de direcionamento para definir o armazenamento de dados com o objetivo de alterar o conteúdo do acionador de dados.
uuid: be06bda8-7de9-40d6-a84b-5ed8d8b3d180
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: developing
content-type: reference
discoiquuid: 9a26b5cd-b957-4df7-9b5b-f57e32b4196a
docset: aem65
feature: Developing Screens
role: Developer
level: Intermediate
translation-type: tm+mt
source-git-commit: 89c70e64ce1409888800af7c7edfbf92ab4b2c68
workflow-type: tm+mt
source-wordcount: '1535'
ht-degree: 1%

---


# Configuração do ContextHub no AEM Screens {#configuring-contexthub-in-aem-screens}

Esta seção enfatiza a criação e o gerenciamento de alterações de ativos orientadas por dados usando um armazenamento de dados.

## Termos principais {#key-terms}

Antes de abordarmos os detalhes da criação e do gerenciamento de canais orientados pelo inventário em seu projeto do AEM Screens, você deve aprender alguns dos termos principais que são importantes e relevantes para os diferentes cenários.

**** MarcaRefere-se à descrição de seu projeto de alto nível.

**** ÁreaRefere-se ao nome do seu projeto AEM Screens, como Sinalização de anúncio digital

**** AtividadeDefine a categoria da regra, como Orientada por Inventário, Orientada por Tempo, Orientada por Disponibilidade do Departamento e assim por diante.

**** Público-alvo Define a regra.

**** SegmentRefere-se à versão do ativo a ser reproduzido para a regra específica, como se a temperatura estiver abaixo de 50 graus fahrenheit, então a tela exibe uma imagem de um café quente, caso contrário, uma bebida fria.

O diagrama a seguir fornece uma representação visual de como as configurações do ContextHub coincidem com Atividade, Público-alvo e Canais.

![screen_shot_2019-05-29at53729pm](assets/screen_shot_2019-05-29at53729pm.png)

## Pré-condições {#preconditions}

Antes de começar a configurar as Configurações do Context Hub para um projeto do AEM Screens, você deve configurar as Folhas do Google (para fins de demonstração).

>[!IMPORTANT]
>
>As Google Sheets são usadas no exemplo a seguir como um sistema de banco de dados de amostra de onde os valores são buscados e são apenas para fins educacionais. O Adobe não endossa o uso das planilhas do Google para ambientes de produção.
>
>Para obter mais informações, consulte [Obter chave de API](https://developers.google.com/maps/documentation/javascript/get-api-key) na documentação do Google.

## Etapa 1: Configurar um Data Store {#step-setting-up-a-data-store}

Você pode configurar o armazenamento de dados como um evento de E/S local ou como um evento de banco de dados local.

O exemplo de acionadores de dados a nível de ativo a seguir mostra um evento de banco de dados local que configura um armazenamento de dados, como uma planilha do excel, que permite usar configurações do ContextHub e caminho de segmentos para o canal do AEM Screens.

Depois de configurar a planilha do google corretamente, por exemplo, como mostrado abaixo:

![imagem](/help/user-guide/assets/context-hub/context-hub1.png)

A seguinte validação é o que você visualizará ao verificar sua conexão inserindo os dois valores, *ID da planilha do google* e *Chave da API* no formato abaixo:

`https://sheets.googleapis.com/v4/spreadsheets/<your sheet id>/values/Sheet1?key=<your API key>`

![imagem](/help/user-guide/assets/context-hub/context-hub2.png)

>[!NOTE]
>
>O exemplo específico abaixo mostra as planilhas do google como um armazenamento de dados que acionará a alteração de ativos se o valor for maior que 100 ou menor que 50.

## Etapa 2: Configurando configurações de armazenamento {#step-setting-store-configurations}

1. **Navegar até o ContextHub**

   Navegue até a instância do AEM e clique no ícone de ferramentas na barra lateral esquerda. Clique em **Sites** —> **ContextHub**, conforme mostrado na figura abaixo.

   ![imagem](/help/user-guide/assets/context-hub/context-hub3.png)

1. **Criação de uma nova configuração de armazenamento do ContextHub**

   1. Navegue até o contêiner de configuração chamado como **screens**.

   1. Clique em **Create** > **Create Configuration Container** e insira o título como **ContextHubDemo**.

      ![imagem](/help/user-guide/assets/context-hub/context-hub4.png)

   1. **** Navegue até  **ContextHubDemo**  >  **** **CreateContentHub** Configuration e clique em  **Save**.

      >[!NOTE]
      > Depois de clicar em **Salvar** você estará na tela **Configuração do ContextHub**.

   1. Na tela **Configuração do ContextHub**, clique em **Criar** > **Configuração da Loja do ContentHub..**

      ![imagem](/help/user-guide/assets/context-hub/context-hub5.png)

      >[!CAUTION]
      >
      >Como parte do AEM 6.5 Feature Pack 4 ou AEM 6.4 Feature Pack 8, os clientes devem atualizar `/conf/screens/settings/cloudsettings` para `sling:Folder`.
      >
      >Siga as etapas abaixo:
      >
      >1. Navegue até CRXDE Lite e então até `/conf/screens/settings/cloudsettings`.
      >1. Verifique se `cloudsettings jcr:primaryType` está em `sling:Folder`. Se `jcr:primaryType` não estiver em `sling:folder`, continue para as próximas etapas.
      >1. Clique com o botão direito do mouse em `/conf/screens/settings` e crie um novo nó com *name* como **cloudsettings1** e *Type* como **sling:Folder** e salve as alterações.
      >1. Mova todos os nós em `/conf/screens/settings/cloudsettings` para `cloudsettings1`.
      >1. Exclua `cloudsettings` e salve.
      >1. Renomeie `cloudsettings1` para `cloudsettings` e salve.
      >1. Agora você deve observar que /conf/screens/settings/cloudsettings tem `jcr:primaryType` como `sling:Folder`.

      >
      >Você deve seguir essas etapas em criar e publicar antes ou depois da atualização.

   1. Insira o **Título** como **Google Sheets**, **Nome da Loja** como **googlesheets**, e **Tipo de Loja** como **contexthub.generic-jsonp** e clique **Próximo**.

      >[!CAUTION]
      >Se estiver usando o Adobe Experience Manager (AEM) 6.4, insira o **Título de configuração** como **folhas de logotipos** e o **Tipo de armazenamento** como **contexthub.generic-jsonp**.

      ![imagem](/help/user-guide/assets/context-hub/context-hub6.png)

   1. Insira sua configuração json específica. Por exemplo, você pode usar o json a seguir para fins de demonstração e clicar em **Salvar**, e você verá a configuração da loja intitulada como **Google Sheets** na configuração do ContextHub.

      >[!IMPORTANT]
      >Substitua o código por seu *&lt;Sheet ID>* e *&lt;API Key>*, que você buscou ao configurar as Google Sheets.

      ```
       {
        "service": {
        "host": "sheets.googleapis.com",
        "port": 80,
        "path": "/v4/spreadsheets/<your google sheets id>/values/Sheet1",
        "jsonp": false,
        "secure": true,
        "params": {
        "key": "<your Google API key>"
       }
      },
      "pollInterval": 10000
      }
      ```

      >[!NOTE]
      No código de amostra acima, **pollInterval** define a frequência na qual os valores são atualizados (em ms).
      Substitua o código por seu *&lt;Sheet ID>* e *&lt;API Key>*, que você buscou ao configurar as Google Sheets.

      >[!CAUTION]
      Se você criar suas configurações de armazenamento do Google Sheets fora da pasta global (por exemplo, em sua própria pasta de projeto), o direcionamento não funcionará imediatamente.


1. **Configuração da segmentação da loja**

   1. Navegue até **Configuração da Loja do ContentHub.** e crie outra configuração de loja no contêiner de configuração de telas e defina o  **** Titleas  **segmentation-contexthub**,  **Store** Name  **** segmentation e  **Store** Typeas  **aem.segmentation**.

      ![imagem](/help/user-guide/assets/context-hub/context-hub7.png)

   1. Clique em **Next** e depois em **Save**.

      >[!NOTE]
É necessário ignorar o processo de definição do json e deixá-lo em branco.


## Etapa 3: Configuração de segmentos no público-alvo {#setting-up-audience}

1. **Criação de segmentos em públicos-alvo**

   1. Navegue da instância de AEM para **Personalization** > **Audiences** > **screens**.

   1. Clique em **Criar** > **Criar segmento do Context Hub.** A caixa de diálogo  **Novo** segmento do ContextHub é aberta.

   1. Insira o **Título** como **Superior a 50** e clique em **Criar**. Da mesma forma, crie outro segmento chamado **Lowerthan50**.

      ![imagem](/help/user-guide/assets/context-hub/context-hub11.png)

   1. Selecione o segmento **Superior a 50** e clique em **Propriedades** na barra de ações.
      ![imagem](/help/user-guide/assets/context-hub/context-hub12.png)

   1. Selecione a guia **Personalization** nas **Propriedades do segmento**. Defina o **Caminho do ContextHub** para `/conf/screens/settings/cloudsettings/ContextHubDemo/contexthub configurations` e **Caminho dos segmentos** para `/conf/screens/settings/wcm/segments` e clique em **Salvar**, conforme mostrado na figura abaixo.

      ![imagem](/help/user-guide/assets/context-hub/context-hub13.png)

   1. Da mesma forma, defina o **Caminho do ContextHub** e o **Caminho de segmentos** para o segmento **Inferior a 50** também.

## Etapa 4: Configurando a marca e a área {#setting-brand-area}

Siga as etapas abaixo para criar uma marca em suas atividades e área sob a marca:

1. **Criação de uma marca nas atividades**

   1. Navegue da instância de AEM para **Personalization** > **Activities**.

   1. Clique em **Criar** > **Criar marca**.

   1. Selecione **Marca** no assistente **Criar Página** e clique em **Próximo**.

   1. Insira o **Título** como **ScreensBrand** e clique em **Criar**. Sua marca foi criada conforme mostrado abaixo.

      ![imagem](/help/user-guide/assets/context-hub/context-hub8.png)


      >[!CAUTION]
      Problema conhecido:
Para adicionar uma área, remova o principal do URL, como
      `http://localhost:4502/libs/cq/personalization/touch-ui/content/v2/activities.html/content/campaigns/screensbrand/master`.

1. **Criação de uma área em sua marca**

   Siga as etapas abaixo para criar uma área na marca:

   1. Clique em **Criar** e em **Criar área**.

      ![imagem](/help/user-guide/assets/context-hub/context-hub9.png)

   1. Selecione **Área** no assistente **Criar Página** e clique em **Próximo**.

   1. Insira o **Título** como **ScreensValue** e clique em **Criar**.
Uma área será criada em sua marca.

## Etapa 5: Criação dos segmentos em uma atividade {#step-setting-up-audience-segmentation}

Depois de configurar um armazenamento de dados e definir sua atividade (marca e área), siga as etapas abaixo para criar segmentos na atividade.

1. **Criação de segmentos nas atividades**

   1. Navegue da instância de AEM para **Personalization** > **Activities** > **ScreensBrand** >**ScreensValue**.

   1. Clique em **Criar** > **Criar atividade.** Os  **Assistentes** Configurar Atividade.

   1. Insira o **Title** como **ValueCheck50** e **Name** como **value check50**. Selecione o **Mecanismo de direcionamento** como **ContextHub (AEM)** no menu suspenso e clique em **Próximo**.

      ![imagem](/help/user-guide/assets/context-hub/context-hub14.png)

   1. Clique em **Adicionar experiência** no **Assistente para configurar atividade**.

   1. No **Públicos-alvo**, selecione o **Superior a50** e clique em **Adicionar experiência** e insira o **Título** como **superior a 50** **Nome** como um superior a 50 **.** Clique em **Ok**.

   1. No **Públicos-alvo**, selecione o **Inferior a 50** e clique em **Adicionar experiência** e insira o **Título** como **inferior a 50** **Nome** como a12/>lower than50 **.** Clique em **Ok**.

      ![imagem](/help/user-guide/assets/context-hub/context-hub15.png)

   1. Clique em **Next** e depois em **Save**. **A atividade ValueCheck50**  foi criada e configurada.

      ![imagem](/help/user-guide/assets/context-hub/context-hub16.png)

## Etapa 5: Editar os segmentos em públicos-alvo{#editing-audience-segmentation}

1. **Editar os segmentos**

   1. Navegue da instância de AEM para **Personalization** > **Audiences** > **screens**.

   1. Selecione o segmento **Superior a 50** e clique em **Editar** na barra de ações.

   1. Arraste e solte a **Comparação: Propriedade - Componente Value** para o editor.

   1. Clique no ícone da chave de fenda para abrir a caixa de diálogo **Comparação de uma propriedade com valor**.

   1. Selecione **googlesheets/value/1/0** no menu suspenso em **Nome da propriedade**.

      >[!NOTE]
A  **googlesheets/value/1/0** se refere à linha 2 e à coluna conforme preenchido nas planilhas do google na figura abaixo:

      ![imagem](/help/user-guide/assets/context-hub/context-hub17.png)

   1. Selecione **Operator** como **greater-than** no menu suspenso.

   1. Insira o **Value** como **70**.

      >[!NOTE]
      O AEM valida seus dados do Google Sheet mostrando o segmento como verde.

      ![imagem](/help/user-guide/assets/context-hub/context-hub18.png)
   Da mesma forma, edite os valores da propriedade para **Lowerthan50**.

   1. Arraste e solte a **Comparação: Propriedade - Componente Value** para o editor.

   1. Clique no ícone da chave de fenda para abrir a caixa de diálogo **Comparação de uma propriedade com valor**.

   1. Selecione **googlesheets/value/1/0** no menu suspenso em **Nome da propriedade**.

   1. Selecione **Operator** como **less-than** no menu suspenso.

   1. Insira o **Value** como **50**.



## Ativar a definição de metas em canais {#step-enabling-targeting-in-channels}

Siga as etapas abaixo para ativar o direcionamento em seus canais.

1. Navegue até um dos canais do AEM Screens. As etapas a seguir demonstram como ativar o direcionamento usando **DataDrivenChannel** criado em um Canal AEM Screens.

1. Selecione o canal **TargetChannel** e clique em **Propriedades** na barra de ações.

   ![imagem](/help/user-guide/assets/context-hub/context-hub19.png)

1. Selecione a guia **Personalization** para configurar as configurações do ContextHub.

   1. Defina o **Caminho do ContextHub** para `/conf/screens/settings/cloudsettings/ContextHubDemo/contexthub configurations` e **Caminho de segmentos** para `/conf/screens/settings/wcm/segments` e clique em **Salvar**.

   1. Clique em **Salvar e fechar**.

      >[!NOTE]
      Use o ContextHub e o caminho Segmentos, onde você salvou inicialmente suas configurações e segmentos do hub de contexto.

      ![imagem](/help/user-guide/assets/context-hub/context-hub20.png)

   1. Navegue e selecione o canal **TargetChannel** e clique em **Editar** na barra de ações.

      >[!NOTE]
      Se tiver configurado tudo corretamente, você verá a opção **Direcionamento** no menu suspenso do editor, como mostrado na figura abaixo.

      ![imagem](/help/user-guide/assets/context-hub/context-hub21.png)

## Saiba mais: Exemplo de casos de uso {#learn-more-example-use-cases}

Depois de configurar o ContextHub para seu projeto do AEM Screens, você pode seguir os diferentes Casos de uso para entender como os ativos acionados por dados desempenham um papel vital em diferentes setores:

1. **[Ativação direcionada para inventário de varejo](retail-inventory-activation.md)**
1. **[Ativação da temperatura do centro de viagens](local-temperature-activation.md)**
1. **[Ativação de Reserva de Hospitalidade](hospitality-reservation-activation.md)**
