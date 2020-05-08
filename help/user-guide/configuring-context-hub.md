---
title: Configuração do ContextHub no AEM Screens
seo-title: Configuração do ContextHub no AEM Screens
description: Siga esta página para saber mais sobre o ContextHub no mecanismo de definição de metas para definir o armazenamento de dados com a finalidade de acionar a alteração do conteúdo.
seo-description: Siga esta página para saber mais sobre o ContextHub no mecanismo de definição de metas para definir o armazenamento de dados com a finalidade de acionar a alteração do conteúdo.
uuid: be06bda8-7de9-40d6-a84b-5ed8d8b3d180
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: developing
content-type: reference
discoiquuid: 9a26b5cd-b957-4df7-9b5b-f57e32b4196a
docset: aem65
translation-type: tm+mt
source-git-commit: 15afec3ed9ffdcfc918c13376af2b20f9a61ab8e
workflow-type: tm+mt
source-wordcount: '1531'
ht-degree: 1%

---


# Configuração do ContextHub no AEM Screens {#configuring-contexthub-in-aem-screens}

Esta seção enfatiza a criação e o gerenciamento de alterações de ativos orientadas por dados usando um armazenamento de dados.

## Termos principais {#key-terms}

Antes de entrarmos nos detalhes da criação e gerenciamento de canais orientados por inventário em seu projeto do AEM Screens, você deve saber alguns dos termos principais que são importantes e relevantes para os diferentes cenários.

**Marca** Refere-se à descrição de seu projeto de alto nível.

**Área** Refere-se ao nome do projeto do AEM Screens, como Sinalização de anúncios digitais

**Atividade** Define a categoria da regra, como Orientada ao inventário, Orientada ao tempo, Orientada à disponibilidade do departamento e assim por diante.

**Audiência** Define a regra.

**Segmento** Refere-se à versão do ativo a ser reproduzido para a regra específica, como se a temperatura estiver abaixo de 50 graus fahrenheit, então a tela exibe uma imagem de um café quente, caso contrário, uma bebida fria.

O diagrama a seguir fornece uma representação visual de como as Configurações do ContextHub coincidem com Atividade, Audiência e Canais.

![screen_shot_2019-05-29at53729pm](assets/screen_shot_2019-05-29at53729pm.png)

## Condições prévias {#preconditions}

Antes de start a configuração das Configurações do Context Hub para um projeto do AEM Screens, você deve configurar o Google Sheets (para fins de demonstração).

>[!IMPORTANT]
>
>O Google Sheets é usado no exemplo a seguir como um sistema de banco de dados de amostra de onde os valores são obtidos e é usado exclusivamente para fins educacionais. A Adobe não endossa o uso do Google Sheets para ambientes de produção.
>
>Para obter mais informações, consulte [Obter chave](https://developers.google.com/maps/documentation/javascript/get-api-key) da API na documentação do Google.

## Etapa 1: Configuração de um armazenamento de dados {#step-setting-up-a-data-store}

Você pode configurar o armazenamento de dados como um evento de E/S local ou como um evento de banco de dados local.

O exemplo de acionadores de dados de nível de ativo a seguir mostra um evento de banco de dados local que configura um armazenamento de dados como uma planilha do Excel que permite usar configurações do ContextHub e caminho de segmentos para o canal do AEM Screens.

Depois de configurar a planilha do Google corretamente, por exemplo, como mostrado abaixo:

![image](/help/user-guide/assets/context-hub/context-hub1.png)

A validação a seguir é a que será visualização ao verificar sua conexão, inserindo os dois valores: ID *da planilha do* google e chave *da* API no formato abaixo:

`https://sheets.googleapis.com/v4/spreadsheets/<your sheet id>/values/Sheet1?key=<your API key>`

![image](/help/user-guide/assets/context-hub/context-hub2.png)

>[!NOTE]
> O exemplo específico abaixo mostra as planilhas do google como um armazenamento de dados que acionará a alteração de ativos se o valor for maior que 100 ou menor que 50.

## Etapa 2: Configuração das configurações da loja {#step-setting-store-configurations}

1. **Navegar para o ContextHub**

   Navegue até a instância do AEM e clique no ícone de ferramentas na barra lateral esquerda. Clique em **Sites** —> **ContextHub**, como mostrado na figura abaixo.

   ![image](/help/user-guide/assets/context-hub/context-hub3.png)

1. **Criando uma nova configuração de armazenamento do ContextHub**

   1. Navegue até o container de configuração intitulado como **telas**.

   1. Clique em **Criar** > **Criar Container** de configuração e insira o título como **ContextHubDemo**.

      ![image](/help/user-guide/assets/context-hub/context-hub4.png)

   1. **Navegue** até **ContextHubDemo** > **Criar** configuração **** do ContentHub e clique em **Salvar**.

      >[!NOTE]
      > Depois de clicar em **Salvar** , você estará na tela Configuração **do** ContextHub.

   1. Na tela Configuração **do** ContextHub, clique em **Criar** > Configuração de armazenamento **do ContentHub.**

      ![image](/help/user-guide/assets/context-hub/context-hub5.png)

      >[!CAUTION]
      >Como parte do AEM 6.5 Feature Pack 4 ou do AEM 6.4 Feature Pack 8, os clientes devem atualizar `/conf/screens/settings/cloudsettings` para `sling:Folder`.
      > 
      >Siga as etapas abaixo:
      >
      >1. Navegue até CRXDE Lite e, em seguida, vá para `/conf/screens/settings/cloudsettings`.
      >1. Verifique se `cloudsettings jcr:primaryType` está em `sling:Folder`. Se o não `jcr:primaryType` estiver em `sling:folder`, siga para as etapas seguintes.
      > 1. Clique com o botão direito do mouse em `/conf/screens/settings` e crie um novo nó com *nome* como **cloudsettings1** e *Type* como **sling:Folder** e salve as alterações.
      >1. Mova todos os nós em `/conf/screens/settings/cloudsettings` para `cloudsettings1`.
      >1. Exclua `cloudsettings` e salve.
      >1. Renomeie `cloudsettings1` para `cloudsettings` e salve.
      >1. Agora você deve observar que /conf/screens/settings/cloudsettings tem `jcr:primaryType` as mesmas configurações `sling:Folder`.
Você deve seguir essas etapas em autor e publicar antes ou depois da atualização.


   1. Insira o **Título** como **Google Sheets**, **Store Name** como **googlesheets** e **Store Type** **** **** como contexthub.generic-jsonp e clique em Next.

      >[!CAUTION]
      >Se você estiver usando o Adobe Experience Manager (AEM) 6.4, digite o Título **da** configuração como **googlesheets** e o Tipo **de** loja como **contexthub.generic-jsonp**.

      ![image](/help/user-guide/assets/context-hub/context-hub6.png)



   1. Digite sua configuração json específica. Por exemplo, você pode usar o json a seguir para fins de demonstração e clicar em **Salvar** e verá a configuração da loja intitulada como **Google Sheets** na configuração do ContextHub.

      >[!IMPORTANT]
      >Certifique-se de substituir o código por sua *&lt;ID da planilha>* e *&lt;chave da API>*, que você buscou ao configurar as planilhas do Google.

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
Substitua o código por sua *&lt;ID da planilha>* e *&lt;chave da API>*, que você buscou ao configurar as planilhas do Google.

      >[!CAUTION]
      Se você criar suas configurações de armazenamento do Google Sheets fora da pasta global (por exemplo, na sua própria pasta de projeto), a definição de metas não funcionará automaticamente.

1. **Configuração da segmentação da loja**

   1. Navegue até Configuração de armazenamento do **ContentHub.** e crie outra configuração de loja no container de configuração de telas e defina o **Título** como **segmentation-contexthub**, **Store Name** como **segmentation** e **Store Type** **** como aem.segmentation.

      ![image](/help/user-guide/assets/context-hub/context-hub7.png)

   1. Click **Next** and then **Save**.

      >[!NOTE]
Você tem que pular o processo de definição do json e deixá-lo em branco.


## Etapa 3: Configuração de segmentos na Audiência {#setting-up-audience}

1. **Criação de segmentos no Audiência**

   1. Navegue da instância do AEM para **Personalização** > **Audiências** > **telas**.

   1. Clique em **Criar** > **Criar segmento do Context Hub.** A caixa de diálogo **Novo segmento** do ContextHub é aberta.

   1. Enter the **Title** as **Higherthan50** and click **Create**. Da mesma forma, crie outro segmento chamado **Lowerthan50**.

      ![image](/help/user-guide/assets/context-hub/context-hub11.png)

   1. Selecione o segmento **Superior a 50** e clique em **Propriedades** na barra de ações.
      ![image](/help/user-guide/assets/context-hub/context-hub12.png)

   1. Selecione a guia **Personalização** em Propriedades **do** segmento. Defina Caminho **do** ContextHub como `/conf/screens/settings/cloudsettings/ContextHubDemo/contexthub configurations` e Caminho **de** segmentos como `/conf/screens/settings/wcm/segments` e clique em **Salvar**, como mostrado na figura abaixo.

      ![image](/help/user-guide/assets/context-hub/context-hub13.png)

   1. Da mesma forma, defina o Caminho **do** ContextHub e o Caminho **dos** segmentos para o segmento **Inferior a 50** também.

## Etapa 4: Configurando a marca e a área {#setting-brand-area}

Siga as etapas abaixo para criar uma marca em suas atividades e área sob a marca:

1. **Criação de uma marca no Atividade**

   1. Navegue da instância do AEM para **Personalização** > **Atividades**.

   1. Clique em **Criar** > **Criar marca**.

   1. Select **Brand** from the **Create Page** wizard and click **Next**.

   1. Enter the **Title** as **ScreensBrand** and click **Create**. Sua marca foi criada conforme mostrado abaixo.

      ![image](/help/user-guide/assets/context-hub/context-hub8.png)


      >[!CAUTION]
      Problema conhecido:
Para adicionar uma área, remova o mestre do URL, como
      `http://localhost:4502/libs/cq/personalization/touch-ui/content/v2/activities.html/content/campaigns/screensbrand/master`.

1. **Criação de uma área em sua marca**

   Siga as etapas abaixo para criar uma área na marca:

   1. Clique em **Criar** e em **Criar área**.

      ![image](/help/user-guide/assets/context-hub/context-hub9.png)

   1. Select **Area** from the **Create Page** wizard and click **Next**.

   1. Enter the **Title** as **ScreensValue** and click **Create**.
Uma área será criada em sua marca.

## Etapa 5: Criação de segmentos em uma Atividade {#step-setting-up-audience-segmentation}

Depois de configurar um armazenamento de dados e definir sua atividade (marca e área), siga as etapas abaixo para criar segmentos em sua atividade.

1. **Criação de segmentos no Atividade**

   1. Navegue da instância do AEM para **Personalização** > **Atividades** > **TelasMarca** >**ScreensValue**.

   1. Clique em **Criar** > **Criar Atividade.** O Assistente **para configuração de Atividade** é aberto.

   1. Informe o **Título** como **ValorCheck50** e **Nome** como **valorCheck50**. Selecione o mecanismo **de** definição de metas como **ContextHub (AEM)** no menu suspenso e clique em **Avançar**.

      ![image](/help/user-guide/assets/context-hub/context-hub14.png)

   1. Clique em **Adicionar experiência** no Assistente para **configurar Atividade**.

   1. Nas **Audiências**, selecione **Superior a 50** e clique em **Adicionar experiência** e insira o **Título** como **superior a 50** **** **** Nomecomo Superior a 500. Click **Ok**.

   1. Nas **Audiências**, selecione **Lowerthan50** e clique em **Adicionar experiência** e insira o **Título** como **menor que50** **** **** NomeInferior que50. Click **Ok**.

      ![image](/help/user-guide/assets/context-hub/context-hub15.png)

   1. Click **Next** and then **Save**. **A atividade ValueCheck50** agora é criada e configurada.

      ![image](/help/user-guide/assets/context-hub/context-hub16.png)

## Etapa 5: Editar os segmentos no Audiência{#editing-audience-segmentation}

1. **Editar os segmentos**

   1. Navegue da instância do AEM para **Personalização** > **Audiências** > **telas**.

   1. Selecione o segmento **Superior a 50** e clique em **Editar** na barra de ações.

   1. Arraste e solte a **Comparação: Propriedade - componente de valor** para o editor.

   1. Clique no ícone de chave para abrir a caixa de diálogo **Comparação de uma propriedade com valor** .

   1. Selecione **googlesheets/value/1/0** no menu suspenso em Nome **da** propriedade.

      >[!NOTE]
A **googlesheets/value/1/0** refere-se à linha 2 e à coluna como preenchido nas planilhas do Google na figura abaixo:

      ![image](/help/user-guide/assets/context-hub/context-hub17.png)

   1. Selecione o **Operador** como **maior que** no menu suspenso.

   1. Insira o **Valor** como **70**.

      >[!NOTE]
      O AEM valida seus dados do Google Sheet mostrando seu segmento como verde.

      ![image](/help/user-guide/assets/context-hub/context-hub18.png)
   Da mesma forma, edite os valores de propriedade para **Lowerthan50**.

   1. Arraste e solte a **Comparação: Propriedade - componente de valor** para o editor.

   1. Clique no ícone de chave para abrir a caixa de diálogo **Comparação de uma propriedade com valor** .

   1. Selecione **googlesheets/value/1/0** no menu suspenso em Nome **da** propriedade.

   1. Selecione o **Operador** como **menor que** no menu suspenso.

   1. Informe o **Valor** como **50**.



## Ativar a definição de metas em Canais {#step-enabling-targeting-in-channels}

Siga as etapas abaixo para ativar a definição de metas em seus canais.

1. Navegue até um dos canais do AEM Screens. As etapas a seguir demonstram como ativar a definição de metas usando **DataDrivenChannel** criado em um Canal do AEM Screens.

1. Selecione o canal **TargetChannel** e clique em **Propriedades** na barra de ações.

   ![image](/help/user-guide/assets/context-hub/context-hub19.png)

1. Selecione a guia **Personalização** para configurar as configurações do ContextHub.

   1. Defina Caminho **do** ContextHub como `/conf/screens/settings/cloudsettings/ContextHubDemo/contexthub configurations` e Caminho **de** segmentos como `/conf/screens/settings/wcm/segments` e clique em **Salvar**.

   1. Click **Save &amp; Close**.

      >[!NOTE]
      Use o ContextHub e o caminho Segmentos, onde você salvou inicialmente suas configurações e segmentos do hub de contexto.

      ![image](/help/user-guide/assets/context-hub/context-hub20.png)

   1. Navegue e selecione o canal **TargetChannel** e clique em **Editar** na barra de ações.

      >[!NOTE]
      Se você configurou tudo corretamente, verá a opção **Definição de metas** na lista suspensa do editor, como mostra a figura abaixo.

      ![image](/help/user-guide/assets/context-hub/context-hub21.png)

## Saiba mais: Casos de uso de exemplo {#learn-more-example-use-cases}

Depois de configurar o ContextHub para seu projeto do AEM Screens, você pode seguir os diferentes Casos de uso para entender como os ativos acionados por dados desempenham um papel vital em diferentes setores:

1. **[Ativação direcionada para inventário de varejo](retail-inventory-activation.md)**
1. **[Ativação de temperatura do centro de viagens](local-temperature-activation.md)**
1. **[Ativação de reserva de hospitalidade](hospitality-reservation-activation.md)**
