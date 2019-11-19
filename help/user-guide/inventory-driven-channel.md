---
title: Canal orientado por inventário
seo-title: Canal orientado por inventário
description: 'null'
seo-description: 'null'
page-status-flag: never-activated
uuid: a7e7aa08-8f9e-4458-bdce-225cf29a6da4
contentOwner: jsyal
discoiquuid: 9989ef4c-9fdd-4bf2-9f7c-0c74a9cc4e7f
docset: aem65
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# Canal orientado por inventário{#inventory-driven-channel}

## Introdução aos canais direcionados ao inventário {#getting-started-with-inventory-driven-channels}

Esta seção descreve um exemplo de caso de uso que enfatiza a criação e o gerenciamento de uma alteração de ativo orientada por dados usando o Google Sheets.

### Condições prévias {#preconditions}

Antes de iniciar este caso de uso, certifique-se de saber como:

* **[Criar e gerenciar canais](managing-channels.md)**
* **[Criar e gerenciar locais](managing-locations.md)**
* **[Criar e gerenciar programações](managing-schedules.md)**
* **[Registro do dispositivo](device-registration.md)**

### Principais intervenientes {#primary-actors}

Autores de conteúdo

### Terminologias {#terminolgies}

Siga os termos abaixo que desempenham um papel significativo na compreensão e configuração do projeto nos diferentes casos de uso:

**Atividade** Atividade refere-se à categoria.

**Principal do projeto de área**

**Local do público** -alvo dos dados

**Marca** de marca

**O Segmento** se refere a um contêiner de ativos que você está tentando direcionar.

### Fluxo básico: Configuração do projeto {#basic-flow-setting-up-the-project}

>[!NOTE]
>
>**Pré-requisito:**
>
>Antes de detalhar a configuração e o uso de alterações de ativos orientadas por dados em seu projeto, certifique-se de criar um projeto do AEM Screens com um canal de sequência. Para fins de demonstração, o projeto intitulado **DataDrivenAsset** é criado e os canais de sequência chamados **DataDrivenRestaurant**, **DataDrivenTextOverlay**, **DataDrivenWeather** e **DataDrivenRetail** são adicionados ao projeto, como mostra a figura abaixo.
>
>Criar quatro canais diferentes é apenas para fins de demonstração e mostrar quatro casos diferentes de uso em canais diferentes. Se quiser seguir apenas um caso de uso como seu requisito, sinta-se à vontade para criar apenas um canal de sequência.

![screen_shot_2019-05-01at42043pm](assets/screen_shot_2019-05-01at42043pm.png)

Siga as seções abaixo para criar um projeto de amostra sobre a criação e o gerenciamento de uma alteração de ativo orientada por dados usando as planilhas do Google em um projeto do AEM Screens:

## Etapa 1: Configurando o Banco de Dados {#step-setting-up-database}

>[!CAUTION]
>
>O Google Sheets é usado no seguinte sistema de banco de dados de exemplo a partir do qual os valores são obtidos e é usado exclusivamente para fins educacionais. A Adobe não endossa o uso do Google Sheets para ambientes de produção.
>
>Para obter mais informações, consulte [Obter chave](https://developers.google.com/maps/documentation/javascript/get-api-key) da API na documentação do Google.

1. Faça logon no Google Docs.

   >[!NOTE]
   >
   >Você deve ter uma conta no Google Drive antes de criar uma nova planilha do Google.

1. Iniciar uma nova planilha em branco. Adicione conteúdo à sua planilha do Google e salve-a. Para fins de demonstração, o Google Sheet é nomeado como **ContextHubDemo**.
1. Clique em **Compartilhar** no canto superior direito do Google Sheet para abrir a caixa de diálogo **Compartilhar com outros** . Clique na opção **Avançado** e altere as configurações para **Ligado - qualquer pessoa com o link**, conforme mostrado na figura abaixo.

   Esta etapa permite acessar valores na planilha do Google.

   ![screen_shot_2019-04-22at115829am](assets/screen_shot_2019-04-22at115829am.png)

1. Ao clicar em **Salvar** na etapa anterior, você receberá o link para a planilha do Google. Salve o clique para referências futuras e clique em **Concluído**.

   ![screen_shot_2019-04-22at120242pm](assets/screen_shot_2019-04-22at120242pm.png)

>[!CAUTION]
>
>O Google Sheets é usado no exemplo a seguir para fins educacionais. A Adobe não endossa o uso do Google Sheets para ambientes de produção.

## Etapa 2: Ativação das APIs REST do Google Sheets {#step-enabling-the-google-sheets-rest-apis}

Depois de configurar seu Google Sheet, é necessário ativar a API REST do Google Sheet para acessar os valores.

Para saber como ativar as REST APIs para Google Sheets, consulte a documentação das APIs do Google.

1. Navegue até Console [da API do](https://console.developers.google.com/apis/credentials)Google. Click **CREATE** to create a new project.

   ![screen_shot_2019-04-22at125028pm](assets/screen_shot_2019-04-22at125028pm.png)

1. Insira o Nome **do** projeto como **AssetChange** e clique em **CRIAR**.
1. Depois de criar o projeto, configure a chave da API. Clique em **Criar credenciais** e selecione **chave da API **para gerar a chave da API para seu projeto. Salve a chave da API para referências futuras.

   >[!NOTE]
   >
   >Este projeto de demonstração usa a chave gratuita da API do Google. Você pode consultar os preços e as restrições no site do Google **Obter chave** da API para obter mais informações.

### Verificando a configuração das planilhas do Google {#verifying-the-setup-of-google-sheets}

```
Verify the data in your Google Sheets using the steps below
```

[https://sheets.googleapis.com/v4/spreadsheets/](https://sheets.googleapis.com/v4/spreadsheets/)&lt;id da planilha&gt;/values/Sheet1?key=&lt;sua chave da API&gt;

Por exemplo:

Se o link** Google Sheets** for *o seguinte:*

`https://docs.google.com/spreadsheets/d/1Ksd125lAsDd0_wnMWgLNUiEpKOUPaok7xfh64s-VO7M/edit?usp=sharing`, em seguida, a variável

**A ID** da planilha é: `1Ksd125lAsDd0_wnMWgLNUiEpKOUPaok7xfh64s-VO7M`

**A chave** da API é: `AIzaSyAfoANOeLkFCCyohjL8cOdJLhrhGefqEy8`

Adicionando ambos os valores na sintaxe acima:

`https://sheets.googleapis.com/v4/spreadsheets/1Ksd125lAsDd0_wnMWgLNUiEpKOUPaok7xfh64s-VO7M/values/Sheet1?key=AIzaSyAfoANOeLkFCCyohjL8cOdJLhrhGefqEy8`

Agora você pode visualizar seus dados na planilha.

## Etapa 2: Configurar o AEM para buscar o conteúdo das planilhas do Google {#step-configuring-aem-to-fetch-the-content-of-the-google-sheets}

A seção a seguir descreve como configurar o Adobe Experience Manager (AEM) para buscar conteúdo das planilhas do Google.

1. Navegue até a instância do AEM e clique no ícone de ferramentas na barra lateral esquerda. Clique em **Sites** —&gt; **ContextHub**, como mostrado na figura abaixo.

   ![screen_shot_2019-04-22at53222pm](assets/screen_shot_2019-04-22at53222pm.png)

1. **Criar uma nova configuração de armazenamento do ContextHub**

   1. Navegue até **global** &gt; **padrão** &gt; Configuração **do** ContextHub.

   1. Clique em** Criar &gt; Contêiner de configuração **e insira o título como** ContextHubDemo**.

   1. **** Navegue **até** ContextHubDemo **&gt; Configuração da loja** do ContentHub... para abrir o assistente **Configurar**
   1. Insira o **Título** como **Google Sheets**, **Store Name** como **googlesheets** e **Store Type** **como contexthub.generic-jsonp**
   1. Clique em **Avançar**
   1. Digite sua configuração json específica. Por exemplo, você pode usar o json a seguir para fins de demonstração.
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
   >Substitua o código por sua *&lt;ID da planilha&gt;* e *&lt;chave da API&gt;*, obtidos da **Etapa 1: Configurando o banco de dados.**

   >[!CAUTION]
   Se você criar suas configurações de armazenamento do Google Sheets fora da pasta herdada (por exemplo, na sua própria pasta de projeto), o direcionamento não funcionará da caixa.
   Caso deseje configurar as configurações de armazenamento do Google Sheets fora da pasta herdada global, defina o Nome **da** loja como **segmentação** e Tipo **de** armazenamento como **aem.segmentation**. Além disso, é necessário ignorar o processo de definição do json, conforme definido acima.

1. **Criação de uma marca nas atividades**

   1. Navegue da instância do AEM para **Personalização** &gt; **Atividades**

   1. Clique** Criar* &gt; **Criar marca**

   1. Select **Brand** from the **Create Page** wizard and click **Next**

   1. Enter the **Title** as **ContextHubDemo** and click **Create**. Sua marca foi criada conforme mostrado abaixo.
   ![screen_shot_2019-05-05at44305pm](assets/screen_shot_2019-05-05at44305pm.png)

1. 

>[!CAUTION]
Problema conhecido:
Para adicionar uma área, remova o mestre do URL, como
[https://localhost:4502/libs/cq/personalization/touch-ui/content/v2/activities.html/content/campaigns/contexthubdemo/master](https://localhost:4502/libs/cq/personalization/touch-ui/content/v2/activities.html/content/campaigns/contexthubdemo/master)

1. Criação de uma área em sua marca**

   1. Clique em **Criar** &gt; **Criar área**

   1. Select **Area** from the** Create Page** wizard and click Next

   1. Enter the **Title** as **GoogleSheets** and click **Create**. Sua área será criada em sua atividade.

1. **Criação de segmentos em públicos-alvo**

   1. Navegue da instância do AEM para **Personalização** &gt; **Públicos** &gt; **We.Retail**.
   1. Clique em **Criar** &gt; **Criar segmento** do Context Hub. Será aberta a nova caixa de diálogo Segmento do ContextHub.
   1. Enter the **Title** as **SheetA1 1** and click **Create**. Da mesma forma, crie outro segmento chamado **SheetA2 2**.

1. **Editar os segmentos**

   1. Selecione as **planilhas de segmentos A1 1** (criadas na etapa 5) e clique em **Editar** na barra de ações.

   1. Arraste e solte a **Comparação: Propriedade - componente de valor** para o editor.
   1. Clique no ícone de chave para abrir a caixa de diálogo **Comparação de uma propriedade com valor** .
   1. Selecione **googlesheets/value/1/0** no menu suspenso em Nome **da** propriedade.

   1. Selecione o **Operador** como **Igual **no menu suspenso.

   1. Informe o **Valor** como **1**.
   >[!NOTE]
   O AEM valida seus dados do Google Sheet mostrando seu segmento como verde.

   ![screen_shot_2019-04-23at20142pm](assets/screen_shot_2019-04-23at20142pm.png)

   Da mesma forma, edite os valores de propriedade para as **planilhas A1 2**.

   1. Arraste e solte a **Comparação: Propriedade - componente de valor** para o editor.
   1. Clique no ícone de chave para abrir a caixa de diálogo **Comparação de uma propriedade com valor** .
   1. Selecione **googlesheets/value/1/0** no menu suspenso em Nome **da** propriedade.

   1. Selecione o **Operador** como **Igual **no menu suspenso.

   1. Informe o **Valor** como **2**.
   >[!NOTE]
   As regras aplicadas nas etapas anteriores são apenas um exemplo de como você configura segmentos para implementar os seguintes casos de uso.

## Etapa 3: Configuração das configurações do Context Hub no Canal do AEM Screens {#step-setting-up-context-hub-configurations-in-aem-screens-channel}

Siga as etapas abaixo para configurar as configurações do ContextHub e o caminho dos segmentos para o canal do AEM Screens.

1. Navegue até um dos canais do AEM Screens (**DataDrivenRetail**) criados, como pré-requisito.
1. Selecione o canal (**DataDrivenRetail**) e clique em **Propriedades** na barra de ações.

   ![screen_shot_2019-05-01at43332pm](assets/screen_shot_2019-05-01at43332pm.png)

1. Selecione a guia **Personalização** para configurar as configurações do ContextHub.

   1. Selecione o Caminho **do** ContextHub como **libs** &gt; **configurações** &gt; **configurações** de nuvem &gt; **padrão** **** ****&gt; Configurações doContextHube clique em Selecionar.

   1. Selecione o Caminho **dos** segmentos como **conf** &gt; **We.Retail **&gt; **configurações** &gt; **wcm** &gt; **segmentos** **** e clique emSelect.

   1. Clique em **Salvar e fechar**.
   >[!NOTE]
   Use o ContextHub e o caminho Segmentos, onde você salvou inicialmente suas configurações e segmentos do hub de contexto.

   ![screen_shot_2019-05-01at44030pm](assets/screen_shot_2019-05-01at44030pm.png)

   >[!NOTE]
   Se você não selecionar a **Marca** em Configuração **de** definição de metas na caixa de diálogo acima, será necessário selecionar a Marca e a Atividade ao iniciar o processo de Definição de metas.

1. Navegue e selecione **DataDrivenRetail** em **DataDrivenAssets** &gt; **Canais **e clique em **Editar** na barra de ações.

   >[!NOTE]
   Se você configurou tudo corretamente, verá a opção **Definição de metas** na lista suspensa do editor, como mostrado na figura abaixo.

   ![screen_shot_2019-05-01at44231pm](assets/screen_shot_2019-05-01at44231pm.png)

   >[!NOTE]
   Depois de configurar as configurações do ContextHub para o seu canal, siga as etapas anteriores de 1 a 4, para os outros três canais de sequência também se desejar seguir todos os casos de uso abaixo.

## Caso de uso 1: Ativação de inventário de varejo {#use-case-retail-inventory-activation}

O caso de uso a seguir demonstra três imagens diferentes com base nos valores em sua planilha do Google.

### Descrição {#description}

Este caso de uso mostra o estoque de estoque de varejo para três camisas coloridas diferentes. Dependendo do número de camisas disponíveis em estoque que são gravadas nas planilhas do Google, a imagem (camiseta vermelha, verde ou azul) com o maior número é exibida na tela.

Neste caso de uso, o suéter vermelho, verde ou azul será exibido na tela com base no valor mais alto do número de suéteres disponíveis.

### Procedimento {#procedure}

Siga as etapas abaixo para implementar o caso de uso de Ativação de Inventário de Varejo:

1. **Preenchendo as planilhas do Google**

   1. Navegue até a página do Google ContextHubDemo.
   1. Adicione três colunas (Vermelho, Verde e Azul) com valores correspondentes para três camisas diferentes.
   ![screen_shot_2019-05-06at101755am](assets/screen_shot_2019-05-06at101755am.png)

1. **Configurar os públicos-alvo de acordo com os requisitos**

   1. Navegue até os segmentos em seu público-alvo (criado na etapa 5 da seção ***Etapa 2: Configuração do AEM para buscar o conteúdo das planilhas*** do Google).
   1. Adicione três novos segmentos **Para_Vermelho**, **Para_Verde** e **Para_Azul**.

   1. Selecione **For_Red** e clique em **Editar** na barra de ações.

   1. Arraste e solte a **comparação: Propriedade - Propriedade** do editor e clique no ícone de configuração para editar as propriedades.
   1. Selecione **googlesheets/value/1/2** no menu suspenso em **Nome da propriedade**

   1. Selecione o **Operador** como **maior que **no menu suspenso

   1. Selecionar Tipo **de** Dados como **número**

   1. Selecione **googlesheets/value/1/1** no menu suspenso no nome da **segunda propriedade**

   1. Arraste e solte **outra comparação: Propriedade - Propriedade **para o editor e clique no ícone de configuração para editar as propriedades.
   1. Selecione **googlesheets/value/1/2** no menu suspenso em **Nome da propriedade**

   1. Selecione o **Operador** como **maior que **no menu suspenso

   1. Selecionar tipo **de** dados como **número**

   1. Selecione **googlesheets/value/1/0** no menu suspenso no nome da **segunda propriedade**
   ![screen_shot_2019-05-06at102600am](assets/screen_shot_2019-05-06at102600am.png)

   Da mesma forma, edite e adicione regras de propriedade de comparação ao segmento **For_Blue** , conforme mostrado na figura abaixo:

   ![screen_shot_2019-05-06at103728am](assets/screen_shot_2019-05-06at103728am.png)

   Da mesma forma, edite e adicione regras de propriedade de comparação ao segmento ** For_Green **conforme mostrado na figura abaixo:

   ![screen_shot_2019-05-06at103418am](assets/screen_shot_2019-05-06at103418am.png)

   >[!NOTE]
   Você observará que, para segmentos **For_Green** e **For_Green**, os dados não podem ser carregados no editor, já que apenas a primeira comparação é válida de agora em diante, de acordo com os valores na planilha do Google.

1. Navegue e selecione seu **canal DataDrivenRetail **canal (um canal sequencial) e clique em **Editar** na barra de ações.

   ![screen_shot_2019-05-06at104257am](assets/screen_shot_2019-05-06at104257am.png)

   >[!CAUTION]
   Você deve ter configurado suas **Configurações** do **ContextHub** usando a guia **Propriedades** do canal —&gt; **Personalização** .

   ![screen_shot_2019-05-06at105214am](assets/screen_shot_2019-05-06at105214am.png)

   >[!NOTE]
   Se você não adicionar a **Marca** em Configurações **de** definição de metas ao configurar Configurações **do** ContextHub para o seu projeto, como mostrado na imagem acima, é necessário selecionar a **Marca** e a **Atividade** ao iniciar o processo de definição de metas, na próxima etapa.

1. **Adicionar uma imagem padrão**

   1. Adicione uma imagem padrão ao seu canal e clique em **Definição de metas**.
   1. Selecione **Marca** e a **Atividade** no menu suspenso e clique em **Iniciar direcionamento**.

   1. Clique em **Iniciar o direcionamento**.
   ![screen_shot_2019-05-06at121253pm](assets/screen_shot_2019-05-06at121253pm.png)

   >[!NOTE]
   Antes de começar a direcionar, você deve adicionar os segmentos (**For_Green**, **For_Red** e **For_Blue**) clicando em **+ Adicionar direcionamento** de experiência do painel lateral, como mostrado na figura abaixo.

   ![screen_shot_2019-05-06at123554pm](assets/screen_shot_2019-05-06at123554pm.png)

1. Adicione as imagens a todos os três cenários diferentes, conforme mostrado abaixo.

   ![retail_targeting](assets/retail_targeting.gif)

1. **Verificando a visualização**

   1. Clique em **Visualizar.** Além disso, abra seu Google Sheet e atualize seu valor.
   1. Altere o valor de todas as três colunas diferentes e você observará as atualizações de imagem de exibição de acordo com o valor mais alto no inventário.
   ![varejo_resultado](assets/retail_result.gif)

## Caso de uso 2: Ativação do tempo do centro de viagens {#use-case-travel-center-weather-activation}

O caso de uso a seguir demonstra duas imagens diferentes com base nos valores em sua planilha do Google.

### Descrição {#description-1}

Neste caso de uso, se as suas planilhas do Google tiverem Valor menor que 50, uma imagem com bebidas quentes será exibida e se o valor for maior ou igual a 50, a imagem com bebidas frias será exibida. No caso de algum outro valor ou nenhum valor, o player exibirá uma imagem padrão.

### Procedimento {#procedure-1}

Siga as etapas abaixo para implementar o caso de uso de ativação do tempo do centro de viagens para seu projeto do AEM Screens:

1. **Preenchendo as planilhas do Google**

   1. Navegue até a página do Google ContextHubDemo.
   1. Adicione uma coluna com **Cabeçalho1** com valor correspondente para temperatura.
   ![screen_shot_2019-05-08at112911am](assets/screen_shot_2019-05-08at112911am.png)

1. **Configurar os segmentos em Públicos conforme os requisitos**

   1. Navegue até os segmentos em seu público-alvo (criado na etapa 5 da seção ***Etapa 2: Configuração do AEM para buscar o conteúdo das planilhas*** do Google).
   1. Selecione as **planilhas A1 1** e clique em **Editar**.

   1. Selecione a propriedade de comparação e clique no ícone de configuração para editar as propriedades.
   1. Selecione **googlesheets/value/1/0** no menu suspenso no nome **da propriedade**

   1. Selecione o **Operador** como **maior ou igual a **no menu suspenso

   1. Insira o **Valor** como **50**

   1. Da mesma forma, selecione as** Sheets A1 2 **e clique em **Editar**.

   1. Selecione a propriedade de comparação e clique no ícone de configuração para editar as propriedades.
   1. Selecione **googlesheets/value/1/0** no menu suspenso no nome **da propriedade**

   1. Selecione o **Operador** como **menor que **no menu suspenso

   1. Insira o **Valor** como **50**

1. Navegue e selecione seu canal () e clique em **Editar** na barra de ações. No exemplo a seguir, **DataDrivenWeather**, um canal sequencial é usado para mostrar a funcionalidade.

   >[!NOTE]
   Seu canal já deve ter uma imagem padrão e os Públicos devem ser pré-configurados conforme descrito na Etapa (3)

   ![screen_shot_2019-05-08at113022am](assets/screen_shot_2019-05-08at113022am.png)

   >[!CAUTION]
   Você deve ter configurado suas **Configurações** do **ContextHub** usando a guia **Propriedades** do canal —&gt; **Personalização** .

   ![screen_shot_2019-05-08at114106am](assets/screen_shot_2019-05-08at114106am.png)

   >[!NOTE]
   Se você não adicionar a **Marca** em Configurações **de** definição de metas ao configurar Configurações **do** ContextHub para o seu projeto, como mostrado na imagem acima, é necessário selecionar a **Marca** e a **Atividade** ao iniciar o processo de definição de metas, na próxima etapa.

1. Selecione **Definição de metas** no editor e selecione **Marca** e **Atividade** no menu suspenso e clique em **Iniciar definição de metas**.

   >[!NOTE]
   Se você tiver adicionado a **Marca** em Configurações **de** definição de metas ao configurar Configurações **do** ContextHub para o seu projeto, não será necessário selecionar a **Marca** e a **Atividade** nesta etapa.

   ![new_activity3](assets/new_activity3.gif)

1. Verificando a visualização

   1. Clique em **Visualizar.** Além disso, abra seu Google Sheet e atualize seu valor.
   1. Altere o valor para menos de 50, você deve ser capaz de exibir a imagem das bebidas de verão. Se o valor na planilha do Google for 50 ou maior do que deveria ser capaz de visualizar a imagem de uma bebida quente.
   ![result3](assets/result3.gif)

## Caso de uso 3:Ativação da Reserva de Hospitalidade {#use-case-hospitality-reservation-activation}

O caso de uso a seguir demonstra duas imagens diferentes com base nos valores e na fórmula aplicada em sua planilha do Google.

### Descrição {#description-2}

Para este caso de uso, o Google Sheet é preenchido com a porcentagem de reserva em dois restaurantes **Restaurant1** e **Restaurant2**. Uma fórmula é aplicada com base nos valores de Restaurant1 e Restaurant2 e, com base na fórmula, o valor 1 ou 2 é atribuído à Coluna **AdTarget** .

Se o **Restaurante1** &gt; **Restaurante2**, então o valor do **AdTarget** será 1, caso contrário, o valor 2 será atribuído ao **AdTarget** . O Valor 1 gera a opção *Abate* e o Valor 2 resulta na exibição da opção *Tailandês Food* na tela.

### Abordagem processual {#procedural-approach}

Siga as etapas abaixo para implementar o caso de uso de ativação de reserva de hospitalidade para seu projeto do AEM Screens:

1. Preenchendo as planilhas do Google e adicionando a fórmula.

   Por exemplo, aplique a fórmula à terceira coluna **AdTarget**, como mostrado na figura abaixo.

   ![screen_shot_2019-04-29at94132am](assets/screen_shot_2019-04-29at94132am.png)

1. **Configurar os segmentos em Públicos conforme os requisitos**

   1. Navegue até os segmentos em seu público-alvo (criado na etapa 5 da seção ***Etapa 2: Configuração do AEM para buscar o conteúdo das planilhas*** do Google).
   1. Selecione as **planilhas A1 1** e clique em **Editar**.

   1. Selecione a propriedade de comparação e clique no ícone de configuração para editar as propriedades.
   1. Selecione **googlesheets/value/1/2** no menu suspenso no nome **da propriedade**

   1. Selecione o **Operador** como **igual **no menu suspenso

   1. Insira o **Valor** como **1**

   1. Da mesma forma, selecione as** Sheets A1 2 **e clique em **Editar**.

   1. Selecione a propriedade de comparação e clique no ícone de configuração para editar as propriedades.
   1. Selecione **googlesheets/value/1/2** no menu suspenso no nome **da propriedade**

   1. Selecione o **operador** como **2**

1. Navegue e selecione seu canal () e clique em **Editar** na barra de ações. No exemplo a seguir, **DataDrivenRestaurant**, um canal sequencial é usado para mostrar a funcionalidade.

   >[!NOTE]
   Seu canal já deve ter uma imagem padrão e os Públicos devem estar pré-configurados, conforme descrito na Etapa (3).

   ![screen_shot_2019-05-08at14652pm](assets/screen_shot_2019-05-08at14652pm.png)

   >[!CAUTION]
   Você deve ter configurado suas **Configurações** do **ContextHub** usando a guia **Propriedades** do canal —&gt; **Personalização** .

   ![screen_shot_2019-05-08at14903pm](assets/screen_shot_2019-05-08at14903pm.png)

   >[!NOTE]
   Se você não adicionar a **Marca** em Configurações **de** definição de metas ao configurar Configurações **do** ContextHub para o seu projeto, como mostrado na imagem acima, é necessário selecionar a **Marca** e a **Atividade** ao iniciar o processo de definição de metas, na próxima etapa.

1. Selecione **Definição de metas** no editor e selecione **Marca** e **Atividade** no menu suspenso e clique em **Iniciar definição de metas**.
1. Verificando a visualização

   1. Clique em **Visualizar.** Além disso, abra seu Google Sheet e atualize seu valor.
   1. Altere o valor em Restaurant1 &gt; Restaurant2, você deve ser capaz de visualizar uma imagem de bife e Restaurant1 &lt; Restaurant12, você deve ser capaz de visualizar essa imagem de alimento no seu monitor.
   ![result5](assets/result5.gif)

## Caso de uso 4: Sobreposição de texto da placa de menu digital {#use-case-digital-menu-board-text-overlay}

O caso de uso a seguir demonstra um caso de uso da placa de menu digital comum em restaurantes e juntas de fast food.

### Descrição {#description-3}

O caso de uso a seguir descreve o uso da sobreposição de texto em um canal sequencial e como a atualização de valor do preço nas Google Sheets aciona uma atualização no componente de sobreposição de texto.

### Abordagem processual {#procedural-approach-1}

Siga as etapas abaixo para implementar a placa de menu digital com o caso de uso de sobreposição de texto para seu projeto do AEM Screens:

1. **Preenchendo as planilhas do Google**

   1. Navegue até suas planilhas do Google.
   1. Adicione uma coluna com valor de preço para o caso de uso, como mostrado na figura abaixo.
   ![screen_shot_2019-05-05at111344am](assets/screen_shot_2019-05-05at111344am.png)

1. **Adicionar uma imagem ao canal de sequência**

   1. Navegue e selecione seu canal (**DataDrivenAssets** —&gt; **Canais** —&gt; **DataDrivenTextOverlay**).

   1. Clique em **Editar** na barra de ações para abrir o editor.
   1. Arraste e solte uma imagem de torta de maçã no editor.
   ![screen_shot_2019-05-05at112933am](assets/screen_shot_2019-05-05at112933am.png)

1. **Adicionar sobreposição de texto à imagem**

   1. Selecione a imagem no editor e clique em configurar.
   1. Navegue até a guia Sobreposição **** de texto e adicione a sobreposição de texto à imagem. Para obter o valor de suas planilhas do Google, verifique se o valor está entre as salmouras. Por exemplo, o preço é obtido das planilhas do Google e mencionado como **{price}** ao definir a sobreposição de texto.

   1. Navegue até a guia **ContextHub** e configure o valor que deve ser obtido nas planilhas do Google, como mostrado na figura abaixo.
   ![textoverlay_result](assets/textoverlay_result.gif)

1. **Verificando a visualização**

   <!-- Edit text in steps below. wonky-->

   1. Clique em **Visualizar**.  Além disso, abra seu Google Sheet e atualize seu valor.
   1. Altere o item em **Preço** e você observará o valor como usado nas atualizações da sobreposição de texto de acordo, conforme mostrado na figura abaixo.
   ![textoverlay_result-1](assets/textoverlay_result-1.gif)
