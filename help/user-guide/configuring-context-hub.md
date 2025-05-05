---
title: Configuração do ContextHub no AEM Screens
description: Saiba mais sobre o ContextHub no mecanismo de direcionamento para que você possa definir um armazenamento de dados para a alteração de conteúdo do acionador de dados.
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: developing
content-type: reference
docset: aem65
feature: Developing Screens
role: Developer
level: Intermediate
exl-id: 04072107-d6be-4030-bb79-1f1a7609f37e
source-git-commit: 8dde26d36847fb496aed6d4bf9732233116b5ea6
workflow-type: tm+mt
source-wordcount: '1450'
ht-degree: 1%

---

# Configuração do ContextHub no AEM Screens {#configuring-contexthub-in-aem-screens}

Esta seção enfatiza a criação e o gerenciamento de alterações de ativos orientados por dados usando um armazenamento de dados.

## Termos principais {#key-terms}

Antes de entrar nos detalhes de criação e gerenciamento de canais orientados por inventário no seu projeto do AEM Screens, aprenda alguns dos termos principais para os diferentes cenários.

**Marca** - Sua descrição de projeto de alto nível.

**Área** - O nome do seu projeto do AEM Screens, como Sinalização Digital de Anúncio

**Atividade** - Define as regras de categoria, como Orientado a Inventário, Orientado ao Clima ou Orientado à Disponibilidade do Departamento.

**Público-alvo** - Define a regra.

**Segmento** - A versão de um ativo para reproduzir para a regra especificada. Por exemplo, se a temperatura estiver abaixo de 50 graus Fahrenheit, a tela exibe uma imagem de uma bebida quente, caso contrário, uma bebida fria.

O diagrama a seguir fornece uma representação visual de como as configurações do ContextHub coincidem com a Atividade, o Público-alvo e os Canais.

![screen_shot_2019-05-29at53729pm](assets/screen_shot_2019-05-29at53729pm.png)

## Pré-condições {#preconditions}

Antes de começar a definir as configurações do ContextHub para um projeto do AEM Screens, configure o Google Sheets (para fins de demonstração).

>[!IMPORTANT]
>
>O Google Sheets é usado no exemplo a seguir como um sistema de banco de dados de amostra de onde os valores são buscados e é exclusivamente para fins educacionais. A Adobe não endossa o uso do Google Sheets em ambientes de produção.
>
>Para obter mais informações, consulte [Obter chave de API](https://developers.google.com/maps/documentation/javascript/get-api-key) na documentação da Google.

## Etapa 1: configuração de um armazenamento de dados {#step-setting-up-a-data-store}

Você pode configurar o armazenamento de dados como um evento de E/S local ou como um evento de banco de dados local.

O exemplo de acionadores de dados a seguir mostra um evento de banco de dados local. O evento configura um armazenamento de dados, como uma planilha do Excel que permite usar as configurações do ContextHub e o caminho dos segmentos para o canal do AEM Screens.

Depois de configurar a planilha `google` corretamente, conforme mostrado no exemplo abaixo:

![imagem](/help/user-guide/assets/context-hub/context-hub1.png)

A validação a seguir é o que você vê ao verificar sua conexão inserindo os dois valores, `*google sheet ID*` e `*API key*` no formato abaixo:

`https://sheets.googleapis.com/v4/spreadsheets/<your sheet id>/values/Sheet1?key=<your API key>`

![imagem](/help/user-guide/assets/context-hub/context-hub2.png)

>[!NOTE]
>
>O exemplo específico abaixo mostra as Google Sheets como um armazenamento de dados que aciona uma alteração de ativo se o valor for maior que 100 ou menor que 50.

## Etapa 2: definição das configurações de armazenamento {#step-setting-store-configurations}

1. **Navegando até o ContextHub**

   Navegue até a instância do AEM e clique no ícone de ferramentas na barra lateral esquerda. Clique em **Sites** > **ContextHub**, conforme mostrado na figura abaixo.

   ![imagem](/help/user-guide/assets/context-hub/context-hub3.png)

1. **Criando uma configuração de armazenamento do ContextHub**

   1. Navegue até o contêiner de configuração denominado **telas**.

   1. Clique em **Criar** > **Criar Contêiner de Configuração** e insira o título como **ContextHubDemo**.

      ![imagem](/help/user-guide/assets/context-hub/context-hub4.png)

   1. **Navegue** até **ContextHubDemo** > **Criar** **Configuração do ContentHub** e clique em **Salvar**.

      >[!NOTE]
      > Depois de clicar em **Salvar**, você estará na tela **Configuração do ContextHub**.

   1. Na tela **Configuração do ContextHub**, clique em **Criar** > **Configuração de Armazenamento do ContentHub**

   ![imagem](/help/user-guide/assets/context-hub/context-hub5.png)

   >[!CAUTION]
   >
   >Como parte do AEM 6.5 Feature Pack 4 ou AEM 6.4 Feature Pack 8, os clientes devem atualizar o `/conf/screens/settings/cloudsettings` para `sling:Folder`.
   >
   >Siga as etapas abaixo:
   >
   >1. Navegue até o CRXDE Lite e, em seguida, até `/conf/screens/settings/cloudsettings`.
   >1. Verifique se `cloudsettings jcr:primaryType` está em `sling:Folder`. Se o `jcr:primaryType` não estiver em `sling:folder`, continue com as próximas etapas.
   >1. Clique com o botão direito do mouse em `/conf/screens/settings`, crie um nó com *name* como **`cloudsettings1`** e *Type* como **`sling:Folder`** e salve as alterações.
   >1. Mover todos os nós em `/conf/screens/settings/cloudsettings` para `cloudsettings1`.
   >1. Exclua `cloudsettings` e salve.
   >1. Renomeie `cloudsettings1` como `cloudsettings` e salve.
   >1. Observe que `/conf/screens/settings/cloudsettings` tem `jcr:primaryType` como `sling:Folder`.
   >
   >Siga estas etapas em Autor e Publish antes ou depois da atualização.

   1. Insira o **Título** como **Google Sheets**, **Nome do Repositório** como **`googlesheets`** e **Tipo de Repositório** como **c`ontexthub.generic-jsonp`** e clique em **Avançar**.

      >[!CAUTION]
      >Se você estiver usando o Adobe Experience Manager (AEM) 6.4, insira o **Título da Configuração** como **`googlesheets`** e o **Tipo de Loja** como **c`ontexthub.generic-jsonp`**.

      ![imagem](/help/user-guide/assets/context-hub/context-hub6.png)

   1. Insira sua configuração json específica. Por exemplo, você pode usar o seguinte json para fins de demonstração e clicar em **Salvar**. Você vê a configuração de armazenamento intitulada como **Google Sheets** na configuração do ContextHub.

      >[!IMPORTANT]
      >Substitua o código por `*<Sheet ID>*` e `*<API Key>*`, que você buscou ao configurar o Google Sheets.

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
      >
      >No código de exemplo acima, **pollInterval** define a frequência com que os valores são atualizados (em milissegundos).
      >
      >Substitua o código por seus `*<Sheet ID>*` e `*<API Key>*`, que você buscou ao configurar o Google Sheets.

      >[!CAUTION]
      >
      >Se você criar suas Planilhas do Google para armazenar configurações fora da pasta global (por exemplo, em sua própria pasta de projeto), o direcionamento não funcionará imediatamente.

1. **Configurando a Segmentação de Repositório**

   1. Navegue até **Configuração de armazenamento do ContentHub** e crie outra configuração de armazenamento no contêiner de configuração do AEM Screens e defina o **Título** como **segmentation-contexthub**, **Nome do armazenamento** como **segmentação** e **Tipo de armazenamento** como **aem.segmentation**.

      ![imagem](/help/user-guide/assets/context-hub/context-hub7.png)

   1. Clique em **Avançar** e depois em **Salvar**.

      >[!NOTE]
      >Ignore o processo de definição do json e deixe-o em branco.


## Etapa 3: Configuração de segmentos no Audience {#setting-up-audience}

1. **Criando segmentos em públicos-alvo**

   1. Navegue da sua instância do AEM para **Personalization** > **Públicos-alvo** > **telas**.

   1. Clique em **Criar** > **Criar segmento do ContextHub.** A caixa de diálogo **Novo segmento do ContextHub** é aberta.

   1. Insira o **Título** como `**Higherthan50**` e clique em **Criar**. Da mesma forma, crie outro segmento intitulado como `**Lowerthan50**`.

      ![imagem](/help/user-guide/assets/context-hub/context-hub11.png)

   1. Clique no segmento `**Higherthan50**` e clique em **Propriedades** na barra de ações.

      ![imagem](/help/user-guide/assets/context-hub/context-hub12.png)

   1. Clique na guia **Personalization** em **Propriedades do segmento**. Defina o **Caminho do ContextHub** como `/conf/screens/settings/cloudsettings/ContextHubDemo/contexthub configurations` e **Caminho de Segmentos** como `/conf/screens/settings/wcm/segments` e clique em **Salvar**, conforme mostrado na figura abaixo.

   ![imagem](/help/user-guide/assets/context-hub/context-hub13.png)

   1. Da mesma forma, defina também o **Caminho do ContextHub** e o **Caminho de Segmentos** para o segmento `**Lowerthan50**`.

## Etapa 4: configuração da marca e da área {#setting-brand-area}

Siga as etapas abaixo para criar uma marca em suas atividades e áreas sob a marca:

1. **Criando uma Marca nas Atividades**

   1. Navegue da sua instância do AEM para **Personalization** > **Atividades**.

   1. Clique em **Criar** > **Criar Marca**.

   1. Clique em **Marca** no assistente **Criar Página** e clique em **Avançar**.

   1. Insira o **Título** como **MarcaDaTela** e clique em **Criar**. Sua marca agora é criada conforme mostrado abaixo.

      ![imagem](/help/user-guide/assets/context-hub/context-hub8.png)


      >[!CAUTION]
      >
      >Problema conhecido:
      >Para adicionar uma área, remova a principal do URL, como
      >`http://localhost:4502/libs/cq/personalization/touch-ui/content/v2/activities.html/content/campaigns/screensbrand/master`.

1. **Criando uma Área em sua Marca**

   Siga as etapas abaixo para criar uma área na marca:

   1. Clique em **Criar** e depois em **Criar área**.

      ![imagem](/help/user-guide/assets/context-hub/context-hub9.png)

   1. Clique em **Área** do assistente **Criar Página** e clique em **Avançar**.

   1. Insira o **Title** como **ScreensValue** e clique em **Criar**.
Uma área é criada na sua marca.

## Etapa 5: Criação de segmentos em uma atividade {#step-setting-up-audience-segmentation}

Depois de configurar um armazenamento de dados e definir sua atividade (marca e área), siga as etapas abaixo para criar segmentos em sua atividade.

1. **Criando segmentos em atividades**

   1. Navegue da sua instância do AEM para **Personalization** > **Atividades** > **ScreensBrand** >**ScreensValue**.

   1. Clique em **Criar** > **Criar Atividade.** O **Assistente para Configurar Atividade** é aberto.

   1. Insira o **Título** como **ValueCheck50** e **Nome** como **valuecheck50**. Clique no **Mecanismo de direcionamento** como **ContextHub (AEM)** no menu suspenso e clique em **Avançar**.

      ![imagem](/help/user-guide/assets/context-hub/context-hub14.png)

   1. Clique em **Adicionar experiência** no assistente `**Configure Activity**`.

   1. Nos **Públicos-alvo**, clique em `**Higherthan50**`, clique em **Adicionar Experiência** e insira o **Título** como `**higherthan50**` **Nome** como `**higherthan50**`. Clique em **Ok**.

   1. Nos **Públicos-alvo**, clique em `**Lowerthan50**`, clique em **Adicionar Experiência** e insira o **Título** como `**lowerthan50**` **Nome** como `**lowerthan50**`. Clique em **Ok**.

   ![imagem](/help/user-guide/assets/context-hub/context-hub15.png)

   1. Clique em **Avançar** e depois em **Salvar**. A atividade `**ValueCheck50**` foi criada e configurada.

      ![imagem](/help/user-guide/assets/context-hub/context-hub16.png)

## Etapa 5: Edição de segmentos em públicos{#editing-audience-segmentation}

1. **Editando os Segmentos**

   1. Navegue da sua instância do AEM para **Personalization** > **Públicos-alvo** > **telas**.

   1. Clique no segmento `**Higherthan50**` e em **Editar** na barra de ações.

   1. Arraste e solte o componente **Comparação: Propriedade - Valor** no editor.

   1. Clique no ícone de chave inglesa para abrir a caixa de diálogo **Comparando uma propriedade com o valor**.

   1. Clique em **googlesheets/value/1/0** no menu suspenso em **Nome da propriedade**.

      >[!NOTE]
      > O **googlesheets/value/1/0** faz referência à linha 2 e à coluna conforme preenchido nas planilhas `google` na figura abaixo:

      ![imagem](/help/user-guide/assets/context-hub/context-hub17.png)

   1. Clique no **Operador** como **maior que** no menu suspenso.

   1. Insira o **Valor** como **70**.

      >[!NOTE]
      >
      >O AEM valida seus dados da Planilha do Google mostrando seu segmento como verde.

      ![imagem](/help/user-guide/assets/context-hub/context-hub18.png)

   Da mesma forma, edite os valores de propriedade para `**Lowerthan50**`.

   1. Arraste e solte o componente **Comparação: Propriedade - Valor** no editor.

   1. Clique na chave inglesa.

   1. Na caixa de diálogo **Comparando uma propriedade com o valor**, clique em **googlesheets/value/1/0** no menu suspenso em **Nome da propriedade**.

   1. Clique no **Operador** como **menor que** no menu suspenso.

   1. Insira o **Valor** como **50**.


## Ativação do direcionamento em canais {#step-enabling-targeting-in-channels}

Siga as etapas abaixo para ativar o direcionamento em seus canais.

1. Navegue até um dos canais do AEM Screens. As etapas a seguir demonstram como habilitar o direcionamento usando o **DataDrivenChannel** criado em um canal do AEM Screens.

1. Clique no canal **TargetChannel** e clique em **Propriedades** na barra de ações.

   ![imagem](/help/user-guide/assets/context-hub/context-hub19.png)

1. Clique na guia **Personalization** para definir as configurações do ContextHub.

   1. Defina o **Caminho do ContextHub** como `/conf/screens/settings/wcm/segments` e o **Caminho de Segmentos** como `/conf/screens/settings/wcm/segments`.
   1. Defina a marca como **ScreensBrand** a partir da lista suspensa e **Defina a Referência de Área** como **ScreensValue**.

   1. Clique em **Salvar e fechar**.

      >[!NOTE]
      >
      >Use o ContextHub e o caminho Segmentos, onde você salvou inicialmente as configurações e os segmentos do ContextHub.

      ![imagem](/help/user-guide/assets/context-hub/context-hub20New.png)

   1. Navegue e clique no canal **TargetChannel** e clique em **Editar** na barra de ações.

      >[!NOTE]
      >
      >Se você configurou tudo corretamente, verá a opção **Direcionamento** no menu suspenso do editor, como mostrado na figura abaixo.

      ![imagem](/help/user-guide/assets/context-hub/context-hub21.png)

## Saiba Mais: Exemplo De Casos De Uso {#learn-more-example-use-cases}

Depois de configurar o ContextHub para seu projeto do AEM Screens, você pode seguir os diferentes Casos de uso para entender como os ativos acionados por dados desempenham um papel vital em diferentes setores:

1. **[Ativação Direcionada para Estoque de Varejo](retail-inventory-activation.md)**
1. **[Ativação da temperatura do centro de viagens](local-temperature-activation.md)**
1. **[Ativação de Reserva de Hospitalidade](hospitality-reservation-activation.md)**
