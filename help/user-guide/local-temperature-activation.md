---
title: Ativação da temperatura do centro de viagens
seo-title: Ativação da temperatura do centro de viagens
description: O caso de uso a seguir demonstra o uso da ativação de temperatura local do centro de viagens com base nos valores preenchidos nas planilhas do Google.
seo-description: O caso de uso a seguir demonstra o uso da ativação de temperatura local do centro de viagens com base nos valores preenchidos nas planilhas do Google.
uuid: b35286d2-79be-4c36-b72e-c40ffc1a0ca0
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: use-case-examples
discoiquuid: 9d58b971-4540-4007-968d-2a1d94d1fd38
docset: aem65
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# Ativação da temperatura do centro de viagens {#travel-center-temperature-activation}

O caso de uso a seguir demonstra o uso da ativação de temperatura local do centro de viagens com base nos valores preenchidos nas planilhas do Google.

## Descrição {#description}

Neste caso de uso, se as suas planilhas do Google tiverem Valor menor que 50, uma imagem com bebidas quentes será exibida e se o valor for maior ou igual a 50, a imagem com bebidas frias será exibida. No caso de algum outro valor ou nenhum valor, o player exibirá uma imagem padrão.

## Condições prévias {#preconditions}

Antes de começar a implementar a ativação de temperatura local do centro de viagens, você deve aprender a configurar o ***Data Store***, a Segmentação ***do*** público-alvo e a ***Ativar a definição de metas para canais*** em um projeto do AEM Screens.

Consulte [Configuração do ContextHub no AEM Screens](configuring-context-hub.md) para obter informações detalhadas.

## Fluxo básico {#basic-flow}

Siga as etapas abaixo para implementar o caso de uso de Ativação de temperatura local do Centro de viagens:

1. **Preenchendo as planilhas do Google**

   1. Navegue até a página do Google ContextHubDemo.
   1. Adicione uma coluna com **Cabeçalho1** com valor correspondente para temperatura.
   ![screen_shot_2019-05-08at112911am](assets/screen_shot_2019-05-08at112911am.png)

1. **Configurar os segmentos em Públicos conforme os requisitos**

   1. Navegue até os segmentos em seu público-alvo (Consulte a ***Etapa 2: Configuração da segmentação*** de público-alvo em **[Configuração do ContextHub na página de telas](configuring-context-hub.md)** AEM para obter mais detalhes).

   1. Selecione as **planilhas A1 1** e clique em **Editar**.

   1. Selecione a propriedade de comparação e clique no ícone de configuração para editar as propriedades.
   1. Selecione **googlesheets/value/1/0** no menu suspenso no nome **da propriedade**

   1. Selecione o **Operador** como **maior ou igual a **no menu suspenso

   1. Insira o **Valor** como **50**

   1. Da mesma forma, selecione as** Sheets A1 2 **e clique em **Editar**.

   1. Selecione a Propriedade de **comparação - Valor** e clique no ícone de configuração para editar as propriedades.
   1. Selecione **googlesheets/value/1/0** no menu suspenso no nome **da propriedade**

   1. Selecione o **Operador** como **menor que **no menu suspenso

   1. Insira o **Valor** como **50**

1. Navegue e selecione seu canal () e clique em **Editar** na barra de ações. No exemplo a seguir, **DataDrivenWeather**, um canal sequencial é usado para mostrar a funcionalidade.

   >[!NOTE]
   >
   >Seu canal já deve ter uma imagem padrão e os Públicos-alvo devem ser pré-configurados conforme descrito em [Configuração do ContextHub nas telas](configuring-context-hub.md)do AEM.

   ![screen_shot_2019-05-08at113022am](assets/screen_shot_2019-05-08at113022am.png)

   >[!CAUTION]
   >
   >Você deve ter configurado suas **Configurações** do **ContextHub** usando a guia **Propriedades** do canal —&gt; **Personalização** .

   ![screen_shot_2019-05-08at114106am](assets/screen_shot_2019-05-08at114106am.png)

1. Selecione **Definição de metas** no editor e selecione **Marca** e **Atividade** no menu suspenso e clique em **Iniciar definição de metas**.

   ![new_activity3](assets/new_activity3.gif)

1. **Verificando a visualização**

   1. Clique em **Visualizar.** Além disso, abra seu Google Sheet e atualize seu valor.
   1. Altere o valor para menos de 50, você deve ser capaz de exibir a imagem das bebidas de verão. Se o valor na planilha do Google for 50 ou maior do que deveria ser capaz de visualizar a imagem de uma bebida quente.
   ![result3](assets/result3.gif)

