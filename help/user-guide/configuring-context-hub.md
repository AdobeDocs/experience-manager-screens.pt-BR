---
title: Configuração do ContextHub no AEM Screens
seo-title: Configuração do ContextHub no AEM Screens
description: Siga esta página para saber mais sobre o ContextHub no mecanismo de definição de metas para definir o armazenamento de dados com a finalidade de acionar a alteração de conteúdo.
seo-description: Siga esta página para saber mais sobre o ContextHub no mecanismo de definição de metas para definir o armazenamento de dados com a finalidade de acionar a alteração de conteúdo.
uuid: be06bda8-7de9-40d6-a84b-5ed8d8b3d180
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: developing
content-type: reference
discoiquuid: 9a26b5cd-b957-4df7-9b5b-f57e32b4196a
docset: aem65
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# Configuração do ContextHub no AEM Screens {#configuring-contexthub-in-aem-screens}

Esta seção enfatiza a criação e o gerenciamento de alterações de ativos orientadas por dados usando um armazenamento de dados.

## Termos principais {#key-terms}

Antes de entrarmos nos detalhes da criação e gerenciamento de canais orientados por inventário em seu projeto do AEM Screens, você deve saber alguns termos importantes e relevantes para os diferentes cenários.

**Marca** Refere-se à descrição de seu projeto de alto nível.

**Área** Refere-se ao nome do projeto do AEM Screens, como Sinalização de anúncios digitais

**Atividade** Define a categoria da regra, como Dirigida ao inventário, Orientada ao tempo, Orientada à disponibilidade do departamento e assim por diante.

**Público-alvo** Define a regra.

**Segmento** Refere-se à versão do ativo a ser reproduzido para a regra específica, como se a temperatura estiver abaixo de 50 graus fahrenheit, então a tela exibe uma imagem de um café quente, caso contrário, uma bebida fria.

O diagrama a seguir fornece uma representação visual de como as Configurações do ContextHub coincidem com Atividade, Público-alvo e Canais.

![screen_shot_2019-05-29at53729pm](assets/screen_shot_2019-05-29at53729pm.png)

## Condições prévias {#preconditions}

Antes de iniciar a configuração de um armazenamento de dados para configurar as Configurações do Context Hub para um projeto do AEM Screens, você deve configurar o Google Sheets (para fins de demonstração).

>[!CAUTION]
>
>O Google Sheets é usado no exemplo a seguir como um sistema de banco de dados de amostra de onde os valores são obtidos e é usado exclusivamente para fins educacionais. A Adobe não endossa o uso do Google Sheets para ambientes de produção.
>
>Para obter mais informações, consulte [Obter chave](https://developers.google.com/maps/documentation/javascript/get-api-key) da API na documentação do Google.

## Etapa 1: Configuração de um armazenamento de dados {#step-setting-up-a-data-store}

Siga as etapas abaixo para configurar um armazenamento de dados que permite usar configurações do ContextHub e caminho de segmentos para o canal do AEM Screens.

1. **Navegar para o ContextHub**

   Navegue até a instância do AEM e clique no ícone de ferramentas na barra lateral esquerda. Clique em **Sites** —&gt; **ContextHub**, como mostrado na figura abaixo.

   ![screen_shot_2019-04-22at53222pm](assets/screen_shot_2019-04-22at53222pm.png)

1. **Criando uma nova configuração de armazenamento do ContextHub**

   1. Navegue até **global** &gt; **padrão** &gt; Configuração **do** ContextHub.

   1. Clique em** Criar &gt; Contêiner de configuração **e insira o título como** ContextHubDemo**.

   1. **** Navegue **até** ContextHubDemo **&gt; Configuração da loja** do ContentHub... para abrir o assistente **Configurar**.

   1. Insira o **Título** como **Google Sheets**, **Store Name** como **googlesheets** e **Store Type** **como contexthub.generic-jsonp**

   1. Clique em **Avançar**
   1. Digite sua configuração json específica**.** Por exemplo, você pode usar o json a seguir para fins de demonstração.
   1. Clique em **Salvar**.

   ```
   {
     "service": {
       "host": "sheets.googleapis.com",
       "port": 80,
       "path": "/v4/spreadsheets/<your sheet it>/values/Sheet1",
       "jsonp": false,
       "secure": true,
       "params": {
         "key": "<your API key>"
       }
     },
     "pollInterval": 3000
   }
   ```

   >[!NOTE]
   >
   >No código de amostra acima, **pollInterval** define a frequência na qual os valores são atualizados (em ms).
   >
   >
   >Substitua o código por sua *&lt;ID da planilha&gt;* e *&lt;chave da API&gt;*, que você buscou ao configurar as planilhas do Google.

   >[!CAUTION]
   Se você criar suas configurações de armazenamento do Google Sheets fora da pasta herdada (por exemplo, na sua própria pasta de projeto), o direcionamento não funcionará da caixa.
   Caso deseje configurar as configurações de armazenamento do Google Sheets fora da pasta herdada global, defina o Nome **da** loja como **segmentação** e Tipo **de** armazenamento como **aem.segmentation**. Além disso, é necessário ignorar o processo de definição do json, conforme definido acima.

1. **Criação de uma marca nas atividades**

   1. Navegue da instância do AEM para **Personalização** &gt; **Atividades**

   1. Clique em **Criar** &gt; **Criar marca**

   1. Select **Brand** from the **Create Page** wizard and click **Next**

   1. Enter the **Title** as **ContextHubDemo** and click **Create**. Sua marca foi criada conforme mostrado abaixo.
   ![screen_shot_2019-05-05at44305pm](assets/screen_shot_2019-05-05at44305pm.png)


   >[!CAUTION]
   Problema conhecido:
   Para adicionar uma área, remova o mestre do URL, como
   `https://localhost:4502/libs/cq/personalization/touch-ui/content/v2/activities.html/content/campaigns/contexthubdemo/master`

1. **Criação de uma área em sua marca**

   Siga as etapas abaixo para criar uma área na marca:

   1. Clique em **Criar** e em **Criar área**

   1. Select **Area** from the **Create Page** wizard and click Next

   1. Enter the **Title** as **GoogleSheets** and click **Create**.
Sua área será criada em sua atividade.

## Etapa 2: Configuração da segmentação do público-alvo {#step-setting-up-audience-segmentation}

Depois de configurar um armazenamento de dados e definir sua marca, siga as etapas abaixo para configurar os segmentos do público-alvo.

1. **Criação de segmentos em públicos-alvo**

   1. Navegue da instância do AEM para **Personalização** &gt; **Públicos** &gt; **We.Retail**.

   1. Clique em **Criar** &gt; **Criar segmento do Context Hub.** A caixa de diálogo **Novo segmento** do ContextHub é aberta.

   1. Enter the **Title** as **SheetA1 1** and click **Create**. Da mesma forma, crie outro segmento chamado **SheetA2 2**.

1. **Editar os segmentos**

   1. Selecione as **planilhas de segmentos A1 1** (criadas na etapa 5) e clique em **Editar** na barra de ações.

   1. Arraste e solte a **Comparação: Propriedade - componente de valor** para o editor.
   1. Clique no ícone de chave para abrir a caixa de diálogo **Comparação de uma propriedade com valor** .
   1. Selecione **googlesheets/value/1/0** no menu suspenso em Nome **da** propriedade.

   1. Selecione o **Operador** como **igual** no menu suspenso.

   1. Informe o **Valor** como **1**.
   >[!NOTE]
   O AEM valida seus dados do Google Sheet mostrando seu segmento como verde.

   ![screen_shot_2019-04-23at20142pm](assets/screen_shot_2019-04-23at20142pm.png)

   Da mesma forma, edite os valores de propriedade para as **planilhas A1 2**.

   1. Arraste e solte a **Comparação: Propriedade - componente de valor** para o editor.
   1. Clique no ícone de chave para abrir a caixa de diálogo **Comparação de uma propriedade com valor** .
   1. Selecione **googlesheets/value/1/0** no menu suspenso em Nome **da** propriedade.

   1. Selecione o **Operador** como **igual** no menu suspenso.

   1. Informe o **Valor** como **2**.
   >[!NOTE]
   As regras aplicadas nas etapas anteriores são apenas um exemplo de como você configura segmentos para implementar os seguintes casos de uso.

## Etapa 3: Habilitar definição de metas em canais {#step-enabling-targeting-in-channels}

Siga as etapas abaixo para ativar a definição de metas em seus canais.

1. Navegue até um dos canais do AEM Screens**. **As etapas a seguir demonstram como ativar a definição de metas usando o **DataDrivenRetail** criado em um Canal do AEM Screens.

1. Selecione o canal **DataDrivenRetail** e clique em **Propriedades** na barra de ações.

   ![screen_shot_2019-05-01at43332pm](assets/screen_shot_2019-05-01at43332pm.png)

1. Selecione a guia **Personalização** para configurar as configurações do ContextHub.

   1. Selecione o Caminho **do** ContextHub como **libs** &gt; **configurações** &gt; **configurações** de nuvem &gt; **padrão** **** ****&gt; Configurações doContextHube clique em Selecionar.

   1. Selecione o Caminho **dos** segmentos como **conf** &gt; **We.Retail** &gt; **configurações** &gt; **wcm** **** ****&gt;segmentos e clique emSelect.

   1. Clique em **Salvar e fechar**.
   >[!NOTE]
   Use o ContextHub e o caminho Segmentos, onde você salvou inicialmente suas configurações e segmentos do hub de contexto.

   ![screen_shot_2019-05-01at44030pm](assets/screen_shot_2019-05-01at44030pm.png)

1. Navegue e selecione **DataDrivenRetail** em **DataDrivenAssets** &gt; **Canais** e clique em **Editar** na barra de ações.

   >[!NOTE]
   Se você configurou tudo corretamente, verá a opção **Definição de metas** na lista suspensa do editor, como mostrado na figura abaixo.

   ![screen_shot_2019-05-01at44231pm](assets/screen_shot_2019-05-01at44231pm.png)

   >[!NOTE]
   Depois de configurar as configurações do ContextHub para o seu canal, siga as etapas anteriores de 1 a 4, para os outros três canais de sequência também se desejar seguir todos os casos de uso abaixo.

## Saiba mais: Casos de uso de exemplo {#learn-more-example-use-cases}

Depois de configurar o ContextHub para seu projeto do AEM Screens, você pode seguir os diferentes Casos de uso para entender como os ativos acionados por dados desempenham um papel vital em diferentes setores:

1. **[Ativação direcionada para inventário de varejo](retail-inventory-activation.md)**
1. **[Ativação da temperatura do centro de viagens](local-temperature-activation.md)**
1. **[Ativação da Reserva de Hospitalidade](hospitality-reservation-activation.md)**
