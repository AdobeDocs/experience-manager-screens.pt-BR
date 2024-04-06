---
title: Configuração do ContextHub no AEM Screens
description: Saiba mais sobre o ContextHub no mecanismo de direcionamento para que você possa definir o armazenamento de dados para a alteração de conteúdo do acionador de dados.
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: developing
content-type: reference
docset: aem65
feature: Developing Screens
role: Developer
level: Intermediate
exl-id: 04072107-d6be-4030-bb79-1f1a7609f37e
source-git-commit: 2b865165793b1c0f90f1351518e41096a57ea2ff
workflow-type: tm+mt
source-wordcount: '1453'
ht-degree: 1%

---

# Configuração do ContextHub no AEM Screens {#configuring-contexthub-in-aem-screens}

Esta seção enfatiza a criação e o gerenciamento de alterações de ativos orientados por dados usando um armazenamento de dados.

## Termos principais {#key-terms}

Antes de entrar nos detalhes de criação e gerenciamento de canais orientados por inventário no seu projeto do AEM Screens, aprenda alguns dos termos principais para os diferentes cenários.

**Marca** - Sua descrição de projeto de alto nível.

**Área** - O nome do seu projeto do AEM Screens, como Sinalização de anúncio digital

**Atividade** - Define as regras de categoria, como Orientado a Inventário, Orientado ao Clima ou Orientado à Disponibilidade do Departamento.

**Público** - Define a regra.

**Segmento** - A versão do ativo a ser reproduzido para a regra especificada. Por exemplo, se a temperatura estiver abaixo de 50 graus Fahrenheit, a tela exibe uma imagem de uma bebida quente, caso contrário, uma bebida fria.

O diagrama a seguir fornece uma representação visual de como as Configurações do ContextHub coincidem com a Atividade, o Público-alvo e os Canais.

![screen_shot_2019-05-29at53729pm](assets/screen_shot_2019-05-29at53729pm.png)

## Pré-condições {#preconditions}

Antes de começar a configurar as Configurações do Context Hub para um projeto do AEM Screens, você deve configurar o Google Sheets (para fins de demonstração).

>[!IMPORTANT]
>
>O Google Sheets é usado no exemplo a seguir como um sistema de banco de dados de amostra de onde os valores são buscados e é exclusivamente para fins educacionais. A Adobe não endossa o uso do Google Sheets em ambientes de produção.
>
>Para obter mais informações, consulte [Obter chave de API](https://developers.google.com/maps/documentation/javascript/get-api-key) na documentação do Google.

## Etapa 1: configuração de um armazenamento de dados {#step-setting-up-a-data-store}

Você pode configurar o armazenamento de dados como um evento de E/S local ou como um evento de banco de dados local.

O exemplo de acionadores de dados a seguir mostra um evento de banco de dados local que configura um armazenamento de dados, como uma planilha do Excel que permite usar as configurações do ContextHub e o caminho de segmentos para o canal do AEM Screens.

Depois de configurar o `google` planilha corretamente, conforme mostrado no exemplo abaixo:

![imagem](/help/user-guide/assets/context-hub/context-hub1.png)

A validação a seguir é o que você vê ao verificar sua conexão inserindo os dois valores, `*google sheet ID*` e `*API key*` no formato abaixo:

`https://sheets.googleapis.com/v4/spreadsheets/<your sheet id>/values/Sheet1?key=<your API key>`

![imagem](/help/user-guide/assets/context-hub/context-hub2.png)

>[!NOTE]
>
>O exemplo específico abaixo mostra as google sheets como um armazenamento de dados que aciona uma alteração de ativo se o valor for maior que 100 ou menor que 50.

## Etapa 2: definição das configurações de armazenamento {#step-setting-store-configurations}

1. **Navegar até o ContextHub**

   Navegue até a instância do AEM e clique no ícone Ferramentas na barra lateral esquerda. Clique em **Sites** > **ContextHub**, conforme mostrado na figura abaixo.

   ![imagem](/help/user-guide/assets/context-hub/context-hub3.png)

1. **Criação de uma configuração de armazenamento do ContextHub**

   1. Navegue até o contêiner de configuração intitulado como **telas**.

   1. Selecionar **Criar** > **Criar contêiner de configuração** e insira o título como **ContextHubDemo**.

      ![imagem](/help/user-guide/assets/context-hub/context-hub4.png)

   1. **Navegar** para **ContextHubDemo** > **Criar** **Configuração do ContentHub** e clique em **Salvar**.

      >[!NOTE]
      > Depois de selecionar **Salvar**, você está no **Configuração do ContextHub** tela.

   1. No **Configuração do ContextHub** , selecione **Criar** > **Configuração de armazenamento do ContentHub**

   ![imagem](/help/user-guide/assets/context-hub/context-hub5.png)

   >[!CAUTION]
   >
   >Como parte do Pacote de recursos 4 ou 8 do AEM AEM 6.5, os clientes devem atualizar `/conf/screens/settings/cloudsettings` para `sling:Folder`.
   >
   >Siga as etapas abaixo:
   >
   >1. Navegue até o CRXDE Lite e, em seguida, até `/conf/screens/settings/cloudsettings`.
   >1. Verificar se `cloudsettings jcr:primaryType` está em `sling:Folder`. Se a variável `jcr:primaryType` não está em `sling:folder`, prossiga para as próximas etapas.
   >1. Clique com o botão direito do mouse `/conf/screens/settings` e criar um nó com *name* as **cloudsettings1** e *Tipo* as **sling:Folder** e salve as alterações.
   >1. Mover todos os nós para baixo `/conf/screens/settings/cloudsettings` para `cloudsettings1`.
   >1. Excluir `cloudsettings` e salve.
   >1. Renomear `cloudsettings1` para `cloudsettings` e salve.
   >1. Observe que `/conf/screens/settings/cloudsettings` tem `jcr:primaryType` as `sling:Folder`.
   >
   >Siga estas etapas em Autor e publicação antes ou depois da atualização.

   1. Insira o **Título** as **Planilhas Google**, **Nome do armazenamento** as **googlesheets**, e **Tipo de armazenamento** as **contexthub.generic-jsonp** e clique em **Próxima**.

      >[!CAUTION]
      >Se estiver usando o Adobe Experience Manager (AEM) 6.4, insira o **Título da configuração** as **googlesheets** e a variável **Tipo de armazenamento** as **contexthub.generic-jsonp**.

      ![imagem](/help/user-guide/assets/context-hub/context-hub6.png)

   1. Insira sua configuração json específica. Por exemplo, você pode usar o seguinte json para fins de demonstração e selecionar **Salvar**. Você verá a configuração da loja intitulada como **Planilhas Google** na configuração do ContextHub.

      >[!IMPORTANT]
      >Substitua o código pelo seu `*<Sheet ID>*` e `*<API Key>*`, que você buscou ao configurar o Google Sheets.

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
      >No código de amostra acima, **pollInterval** define a frequência com que os valores são atualizados (em milissegundos).
      >
      >Substitua o código pelo seu `*<Sheet ID>*` e `*<API Key>*`, que você buscou ao configurar o Google Sheets.

      >[!CAUTION]
      >
      >Se você criar as configurações de armazenamento do Google Sheets fora da pasta global (por exemplo, em sua própria pasta de projeto), o direcionamento não funcionará imediatamente.

1. **Configurar a segmentação de loja**

   1. Navegue até **Configuração de armazenamento do ContentHub** e crie outra configuração de armazenamento no contêiner de configuração do AEM Screens e defina o **Título** as **segmentação-contexthub**, **Nome do armazenamento** as **segmentação** e **Tipo de armazenamento** as **aem.segmentation**.

      ![imagem](/help/user-guide/assets/context-hub/context-hub7.png)

   1. Clique em **Próxima** e depois **Salvar**.

      >[!NOTE]
      >Ignore o processo de definição do json e deixe-o em branco.


## Etapa 3: Configuração de segmentos no Audience {#setting-up-audience}

1. **Criação de segmentos em públicos**

   1. Navegue da instância do AEM para **Personalização** > **Públicos-alvo** > **telas**.

   1. Clique em **Criar** > **Criar segmento do Context Hub.** A variável **Novo segmento do ContextHub** é aberta.

   1. Insira o **Título** as `**Higherthan50**` e clique em **Criar**. Da mesma forma, crie outro segmento intitulado como `**Lowerthan50**`.

      ![imagem](/help/user-guide/assets/context-hub/context-hub11.png)

   1. Selecionar o segmento `**Higherthan50**` e clique em **Propriedades** na barra de ações.
      ![imagem](/help/user-guide/assets/context-hub/context-hub12.png)

   1. Selecione o **Personalização** na guia **Propriedades do segmento**. Defina o **Caminho do ContextHub** para `/conf/screens/settings/cloudsettings/ContextHubDemo/contexthub configurations` e **Caminho de segmentos** para `/conf/screens/settings/wcm/segments` e clique em **Salvar**, conforme mostrado na figura abaixo.

   ![imagem](/help/user-guide/assets/context-hub/context-hub13.png)

   1. Da mesma forma, defina o **Caminho do ContextHub** e **Caminho de segmentos** para `**Lowerthan50**` segmento também.

## Etapa 4: configuração da marca e da área {#setting-brand-area}

Siga as etapas abaixo para criar uma marca em suas atividades e áreas sob a marca:

1. **Criação de uma marca nas atividades**

   1. Navegue da instância do AEM para **Personalização** > **Atividades**.

   1. Selecionar **Criar** > **Criar marca**.

   1. Selecionar **Marca** do **Criar página** e clique em **Próxima**.

   1. Insira o **Título** as **ScreensBrand** e clique em **Criar**. Sua marca agora é criada conforme mostrado abaixo.

      ![imagem](/help/user-guide/assets/context-hub/context-hub8.png)


      >[!CAUTION]
      >
      >Problema conhecido:
      >Para adicionar uma área, remova a principal do URL, como
      >`http://localhost:4502/libs/cq/personalization/touch-ui/content/v2/activities.html/content/campaigns/screensbrand/master`.

1. **Criar uma área na sua marca**

   Siga as etapas abaixo para criar uma área na marca:

   1. Selecionar **Criar** e depois **Criar área**.

      ![imagem](/help/user-guide/assets/context-hub/context-hub9.png)

   1. Selecionar **Área** do **Criar página** e selecione **Próxima**.

   1. Insira o **Título** as **ScreensValue** e selecione **Criar**.
Uma área é criada na sua marca.

## Etapa 5: Criação de segmentos em uma atividade {#step-setting-up-audience-segmentation}

Depois de configurar um armazenamento de dados e definir sua atividade (marca e área), siga as etapas abaixo para criar segmentos em sua atividade.

1. **Criação de segmentos em atividades**

   1. Navegue da instância do AEM para **Personalização** > **Atividades** > **ScreensBrand** >**ScreensValue**.

   1. Selecionar **Criar** > **Criar atividade.** A variável **Configurar o Assistente de atividade** é aberto.

   1. Insira o **Título** as **ValueCheck50** e **Nome** as **valuecheck50**. Selecione o **Mecanismo de direcionamento** as **ContextHub (AEM)** no menu suspenso e selecione **Próxima**.

      ![imagem](/help/user-guide/assets/context-hub/context-hub14.png)

   1. Selecionar **Adicionar experiência** do `**Configure Activity**` assistente.

   1. No **Públicos-alvo**, selecione o `**Higherthan50**` e selecione **Adicionar experiência** e insira o **Título** as `**higherthan50**` **Nome** as `**higherthan50**`. Selecionar **Ok**.

   1. No **Públicos-alvo**, selecione o `**Lowerthan50**` e selecione **Adicionar experiência** e insira o **Título** as `**lowerthan50**` **Nome** as `**lowerthan50**`. Selecionar **Ok**.

   ![imagem](/help/user-guide/assets/context-hub/context-hub15.png)

   1. Selecionar **Próxima** e depois **Salvar**. `**ValueCheck50**` A atividade de foi criada e configurada.

      ![imagem](/help/user-guide/assets/context-hub/context-hub16.png)

## Etapa 5: Edição de segmentos em públicos{#editing-audience-segmentation}

1. **Edição de segmentos**

   1. Navegue da instância do AEM para **Personalização** > **Públicos-alvo** > **telas**.

   1. Selecionar o segmento `**Higherthan50**`e selecione **Editar** na barra de ações.

   1. Arraste e solte a **Comparação: Propriedade- Valor** ao editor.

   1. Clique no ícone da chave inglesa para abrir o **Comparando uma propriedade com o valor** caixa de diálogo.

   1. Selecionar **googlesheets/value/1/0** no menu suspenso em **Nome da propriedade**.

      >[!NOTE]
      > A variável **googlesheets/value/1/0** refere-se à linha 2 e à coluna conforme preenchido em `google` folhas na figura abaixo:

      ![imagem](/help/user-guide/assets/context-hub/context-hub17.png)

   1. Selecione o **Operador** as **maior que** no menu suspenso.

   1. Insira o **Valor** as **70**.

      >[!NOTE]
      >
      >O AEM valida seus dados da Planilha do Google mostrando seu segmento como verde.

      ![imagem](/help/user-guide/assets/context-hub/context-hub18.png)

   Da mesma forma, edite os valores de propriedade para `**Lowerthan50**`.

   1. Arraste e solte a **Comparação: Propriedade- Valor** ao editor.

   1. Selecione o ícone da chave inglesa.

   1. No **Comparando uma propriedade com o valor** caixa de diálogo, selecione **googlesheets/value/1/0** no menu suspenso em **Nome da propriedade**.

   1. Selecione o **Operador** as **menor que** no menu suspenso.

   1. Insira o **Valor** as **50**.


## Ativação do direcionamento em canais {#step-enabling-targeting-in-channels}

Siga as etapas abaixo para ativar o direcionamento em seus canais.

1. Navegue até um dos canais do AEM Screens. As etapas a seguir demonstram como habilitar o direcionamento usando **DataDrivenChannel** criado em um Canal AEM Screens.

1. Selecionar o canal **TargetChannel** e clique em **Propriedades** na barra de ações.

   ![imagem](/help/user-guide/assets/context-hub/context-hub19.png)

1. Selecione o **Personalização** para poder definir as configurações do ContextHub.

   1. Defina o **Caminho do ContextHub** para `/conf/screens/settings/wcm/segments` e **Caminho de segmentos** para `/conf/screens/settings/wcm/segments`.
   1. Definir marca como **ScreensBrand** na lista suspensa e **Definir Referência da Área** para **ScreensValue**.

   1. Clique em **Salvar e fechar**.

      >[!NOTE]
      >
      >Use o ContextHub e o caminho Segmentos, onde você salvou inicialmente as configurações e os segmentos do seu hub de contexto.

      ![imagem](/help/user-guide/assets/context-hub/context-hub20New.png)

   1. Navegue e selecione o **TargetChannel** canal e clique em **Editar** na barra de ações.

      >[!NOTE]
      >
      >Se você configurou tudo corretamente, verá **Direcionamento** no menu suspenso do editor, como mostrado na figura abaixo.

      ![imagem](/help/user-guide/assets/context-hub/context-hub21.png)

## Saiba Mais: Exemplo De Casos De Uso {#learn-more-example-use-cases}

Depois de configurar o ContextHub para seu projeto do AEM Screens, você pode seguir os diferentes Casos de uso para entender como os ativos acionados por dados desempenham um papel vital em diferentes setores:

1. **[Ativação Direcionada de Estoque de Varejo](retail-inventory-activation.md)**
1. **[Ativação da temperatura do centro de viagens](local-temperature-activation.md)**
1. **[Ativação de Reserva de Hospitalidade](hospitality-reservation-activation.md)**
