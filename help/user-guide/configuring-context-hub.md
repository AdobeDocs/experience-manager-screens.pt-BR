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
source-git-commit: 9b54b153676852742859b704ac9aedf908fceecf
workflow-type: tm+mt
source-wordcount: '1531'
ht-degree: 1%

---


# Configuração do ContextHub no AEM Screens {#configuring-contexthub-in-aem-screens}

Esta seção enfatiza a criação e o gerenciamento de alterações de ativos orientadas por dados usando um armazenamento de dados.

## Termos chave {#key-terms}

Antes de entrarmos nos detalhes da criação e gerenciamento de canais orientados por inventário em seu projeto AEM Screens, você deve saber alguns dos termos principais que são importantes e relevantes para os diferentes cenários.

**** MarcaRefere-se à descrição de seu projeto de alto nível.

**** ÁreaRefere-se ao nome do seu projeto AEM Screens, como a Sinalização de anúncios digitais

**** AtividadeDefine a categoria da regra, como Direcionada ao inventário, Orientada ao tempo, Direcionada à disponibilidade do departamento e assim por diante.

**** Público-alvoDefine a regra.

**** SegmentoRefere-se à versão do ativo a ser reproduzido para a regra específica, como se a temperatura estiver abaixo de 50 graus fahrenheit, então a tela exibe uma imagem de um café quente, caso contrário, uma bebida fria.

O diagrama a seguir fornece uma representação visual de como as Configurações do ContextHub coincidem com Atividade, Audiência e Canais.

![screen_shot_2019-05-29at53729pm](assets/screen_shot_2019-05-29at53729pm.png)

## Pré-condições {#preconditions}

Antes de start a configuração das Configurações do Context Hub para um projeto da AEM Screens, você deve configurar o Google Sheets (para fins de demonstração).

>[!IMPORTANT]
>
>O Google Sheets é usado no exemplo a seguir como um sistema de banco de dados de amostra de onde os valores são obtidos e é usado exclusivamente para fins educacionais. O Adobe não endossa o uso das Google Sheets para ambientes de produção.
>
>Para obter mais informações, consulte [Obter chave da API](https://developers.google.com/maps/documentation/javascript/get-api-key) na documentação do Google.

## Etapa 1: Configuração de um armazenamento de dados {#step-setting-up-a-data-store}

Você pode configurar o armazenamento de dados como um evento de E/S local ou como um evento de banco de dados local.

O exemplo de acionadores de dados de nível de ativo a seguir mostra um evento de banco de dados local que configura um armazenamento de dados como uma planilha do Excel que permite usar configurações do ContextHub e caminho de segmentos para o canal AEM Screens.

Depois de configurar a planilha do Google corretamente, por exemplo, como mostrado abaixo:

![imagem](/help/user-guide/assets/context-hub/context-hub1.png)

A seguinte validação é o que você vai visualização ao verificar sua conexão digitando os dois valores, *ID da planilha do google* e *chave da API* no formato abaixo:

`https://sheets.googleapis.com/v4/spreadsheets/<your sheet id>/values/Sheet1?key=<your API key>`

![imagem](/help/user-guide/assets/context-hub/context-hub2.png)

>[!NOTE]
>
>O exemplo específico abaixo mostra as planilhas do google como um armazenamento de dados que acionará a alteração de ativos se o valor for maior que 100 ou menor que 50.

## Etapa 2: Configuração de configurações de armazenamento {#step-setting-store-configurations}

1. **Navegar para o ContextHub**

   Navegue até a instância AEM e clique no ícone de ferramentas na barra lateral esquerda. Clique em **Sites** —> **ContextHub**, conforme mostrado na figura abaixo.

   ![imagem](/help/user-guide/assets/context-hub/context-hub3.png)

1. **Criando uma nova configuração de armazenamento do ContextHub**

   1. Navegue até o container de configuração chamado **screens**.

   1. Clique em **Criar** > **Criar Container de Configuração** e introduza o título como **ContextHubDemo**.

      ![imagem](/help/user-guide/assets/context-hub/context-hub4.png)

   1. **Navegue** até  **ContextHubDemo** >  **** **CreateContentHub** Configuration e clique em  **Salvar**.

      >[!NOTE]
      > Depois de clicar em **Salvar** estará na tela **Configuração do ContextHub**.

   1. Na tela **Configuração do ContextHub**, clique em **Criar** > **Configuração da Loja do ContentHub..**

      ![imagem](/help/user-guide/assets/context-hub/context-hub5.png)

      >[!CAUTION]
      >
      >Como parte do AEM 6.5 Feature Pack 4 ou AEM 6.4 Feature Pack 8, os clientes devem atualizar `/conf/screens/settings/cloudsettings` para `sling:Folder`.
      >
      >Siga as etapas abaixo:
      >
      >1. Navegue até CRXDE Lite e depois para `/conf/screens/settings/cloudsettings`.
      >1. Verifique se `cloudsettings jcr:primaryType` está em `sling:Folder`. Se `jcr:primaryType` não estiver em `sling:folder`, prossiga para as próximas etapas.
      >1. Clique com o botão direito do mouse em `/conf/screens/settings` e crie um novo nó com *name* como **cloudsettings1** e *Type* como **sling:Folder** e salve as alterações.
      >1. Mova todos os nós em `/conf/screens/settings/cloudsettings` para `cloudsettings1`.
      >1. Exclua `cloudsettings` e salve.
      >1. Renomeie `cloudsettings1` para `cloudsettings` e salve.
      >1. Agora você deve observar que /conf/screens/settings/cloudsettings tem `jcr:primaryType` como `sling:Folder`.

      >
      >Você deve seguir essas etapas em autor e publicar antes ou depois da atualização.

   1. Digite **Title** como **Google Sheets**, **Nome da Loja** como **googlesheets**, e **Tipo de Loja** como **contexthub.generic-jsonp&lt;a111/> e clique** Próximo **.**

      >[!CAUTION]
      >Se você estiver usando o Adobe Experience Manager (AEM) 6.4, digite o **Título de configuração** como **folhas de registro** e o **Tipo de loja** como **contexthub.generic-jsonp**.

      ![imagem](/help/user-guide/assets/context-hub/context-hub6.png)

   1. Digite sua configuração json específica. Por exemplo, você pode usar o json a seguir para fins de demonstração e clicar em **Salvar** e verá a configuração da loja intitulada como **Google Sheets** na configuração do ContextHub.

      >[!IMPORTANT]
      >Certifique-se de substituir o código por *&lt;Sheet ID>* e *&lt;API Key>*, que você buscou ao configurar as Google Sheets.

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
      Substitua o código por *&lt;Sheet ID>* e *&lt;API Key>*, que você buscou ao configurar as Google Sheets.

      >[!CAUTION]
      Se você criar suas configurações de armazenamento do Google Sheets fora da pasta global (por exemplo, na sua própria pasta de projeto), a definição de metas não funcionará automaticamente.


1. **Configuração da segmentação da loja**

   1. Navegue até **Configuração de armazenamento do ContentHub.** e crie outra configuração de loja no container de configuração de telas e defina o  **** Titleas  **segmentation-contexthub**,  **Store** Nameas  **** segmentatione  **Store** Typeas  **aem.segmentation**.

      ![imagem](/help/user-guide/assets/context-hub/context-hub7.png)

   1. Clique em **Próximo** e em **Salvar**.

      >[!NOTE]
Você tem que pular o processo de definição do json e deixá-lo em branco.


## Etapa 3: Configurando segmentos na Audiência {#setting-up-audience}

1. **Criação de segmentos no Audiência**

   1. Navegue da instância AEM para **Personalização** > **Audiência** > **ecrãs**.

   1. Clique em **Criar** > **Criar segmento do Context Hub.** A caixa de diálogo  **Novo** segmento do ContextHub é aberta.

   1. Digite **Title** como **Superior a 50** e clique em **Criar**. Da mesma forma, crie outro segmento chamado **Lowerthan50**.

      ![imagem](/help/user-guide/assets/context-hub/context-hub11.png)

   1. Selecione o segmento **Superior a 50** e clique em **Propriedades** na barra de ações.
      ![imagem](/help/user-guide/assets/context-hub/context-hub12.png)

   1. Selecione a guia **Personalização** em **Propriedades do segmento**. Defina **Caminho do ContextHub** como `/conf/screens/settings/cloudsettings/ContextHubDemo/contexthub configurations` e **Caminho dos segmentos** como `/conf/screens/settings/wcm/segments` e clique em **Salvar**, conforme mostrado na figura abaixo.

      ![imagem](/help/user-guide/assets/context-hub/context-hub13.png)

   1. Da mesma forma, defina o **Caminho do ContextHub** e **Caminho dos segmentos** para o segmento **Lowerthan50** também.

## Etapa 4: Configurando a marca e a área {#setting-brand-area}

Siga as etapas abaixo para criar uma marca em suas atividades e área sob a marca:

1. **Criação de uma marca no Atividade**

   1. Navegue da instância AEM para **Personalização** > **Atividade**.

   1. Clique em **Criar** > **Criar marca**.

   1. Selecione **Marca** no assistente **Criar página** e clique em **Próximo**.

   1. Digite **Title** como **ScreensBrand** e clique em **Criar**. Sua marca foi criada conforme mostrado abaixo.

      ![imagem](/help/user-guide/assets/context-hub/context-hub8.png)


      >[!CAUTION]
      Problema conhecido:
Para adicionar uma área, remova o principal do URL, como
      `http://localhost:4502/libs/cq/personalization/touch-ui/content/v2/activities.html/content/campaigns/screensbrand/master`.

1. **Criação de uma área em sua marca**

   Siga as etapas abaixo para criar uma área na marca:

   1. Clique em **Criar** e em **Criar área**.

      ![imagem](/help/user-guide/assets/context-hub/context-hub9.png)

   1. Selecione **Área** no assistente **Criar página** e clique em **Próximo**.

   1. Digite **Title** como **ScreensValue** e clique em **Criar**.
Uma área será criada em sua marca.

## Etapa 5: Criação de segmentos em uma Atividade {#step-setting-up-audience-segmentation}

Depois de configurar um armazenamento de dados e definir sua atividade (marca e área), siga as etapas abaixo para criar segmentos em sua atividade.

1. **Criação de segmentos no Atividade**

   1. Navegue da instância AEM para **Personalização** > **Atividade** > **ScreensBrand** >**ScreensValue**.

   1. Clique em **Criar** > **Criar Atividade.** Os  **Assistentes** Configurar Atividade.

   1. Digite **Title** como **ValueCheck50** e **Name** como **valueCheck50**. Selecione **Mecanismo de definição de metas** como **ContextHub (AEM)** no menu suspenso e clique em **Próximo**.

      ![imagem](/help/user-guide/assets/context-hub/context-hub14.png)

   1. Clique em **Adicionar Experiência** no **Configurar Assistente de Atividade**.

   1. No **Audiência**, selecione o **Superior a 50** e clique em **Adicionar Experiência** e introduza o **Título** como **superior a 50** **Nome** como &lt;a superior a 50 **.** Clique em **Ok**.

   1. No **Audiência**, selecione **Lowerthan50** e clique em **Adicionar Experiência** e introduza o **Título** como **mais baixo que50** **Nome** a12/>menor que50 **.** Clique em **Ok**.

      ![imagem](/help/user-guide/assets/context-hub/context-hub15.png)

   1. Clique em **Próximo** e em **Salvar**. **A** atividade ValueCheck50 agora é criada e configurada.

      ![imagem](/help/user-guide/assets/context-hub/context-hub16.png)

## Etapa 5: Editar os segmentos no Audiência{#editing-audience-segmentation}

1. **Editar os segmentos**

   1. Navegue da instância AEM para **Personalização** > **Audiência** > **ecrãs**.

   1. Selecione o segmento **Superior a 50** e clique em **Editar** na barra de ações.

   1. Arraste e solte a **Comparação: Propriedade - componente Value** para o editor.

   1. Clique no ícone de chave para abrir a caixa de diálogo **Comparar uma propriedade com valor**.

   1. Selecione **googlesheets/value/1/0** no menu suspenso em **Nome da propriedade**.

      >[!NOTE]
As  **googlesheets/value/1/0** referem-se à linha 2 e à coluna, conforme preenchido nas folhas do google na figura abaixo:

      ![imagem](/help/user-guide/assets/context-hub/context-hub17.png)

   1. Selecione **Operador** como **maior-que** no menu suspenso.

   1. Digite **Value** como **70**.

      >[!NOTE]
      O AEM valida seus dados do Google Sheet mostrando seu segmento como verde.

      ![imagem](/help/user-guide/assets/context-hub/context-hub18.png)
   Da mesma forma, edite os valores de propriedade para **Lowerthan50**.

   1. Arraste e solte a **Comparação: Propriedade - componente Value** para o editor.

   1. Clique no ícone de chave para abrir a caixa de diálogo **Comparar uma propriedade com valor**.

   1. Selecione **googlesheets/value/1/0** no menu suspenso em **Nome da propriedade**.

   1. Selecione **Operador** como **menor que** no menu suspenso.

   1. Digite **Value** como **50**.



## Habilitar a definição de metas em Canais {#step-enabling-targeting-in-channels}

Siga as etapas abaixo para ativar a definição de metas em seus canais.

1. Navegue até um dos canais AEM Screens. As etapas a seguir demonstram como ativar a definição de metas usando **DataDrivenChannel** criado em um Canal AEM Screens.

1. Selecione o canal **TargetChannel** e clique em **Propriedades** na barra de ações.

   ![imagem](/help/user-guide/assets/context-hub/context-hub19.png)

1. Selecione a guia **Personalização** para configurar as configurações do ContextHub.

   1. Defina **Caminho do ContextHub** como `/conf/screens/settings/cloudsettings/ContextHubDemo/contexthub configurations` e **Caminho dos segmentos** como `/conf/screens/settings/wcm/segments` e clique em **Guardar**.

   1. Clique em **Salvar e fechar**.

      >[!NOTE]
      Use o ContextHub e o caminho Segmentos, onde você salvou inicialmente suas configurações e segmentos do hub de contexto.

      ![imagem](/help/user-guide/assets/context-hub/context-hub20.png)

   1. Navegue e selecione o canal **TargetChannel** e clique em **Editar** na barra de ações.

      >[!NOTE]
      Se você configurou tudo corretamente, verá a opção **Definição de metas** no menu suspenso do editor, como mostra a figura abaixo.

      ![imagem](/help/user-guide/assets/context-hub/context-hub21.png)

## Saiba mais: Exemplo de casos de uso {#learn-more-example-use-cases}

Depois de configurar o ContextHub para seu projeto AEM Screens, você pode seguir os diferentes Casos de uso para entender como os ativos acionados por dados desempenham um papel vital em diferentes setores:

1. **[Ativação direcionada para inventário de varejo](retail-inventory-activation.md)**
1. **[Ativação de temperatura do centro de viagens](local-temperature-activation.md)**
1. **[Ativação de reserva de hospitalidade](hospitality-reservation-activation.md)**
