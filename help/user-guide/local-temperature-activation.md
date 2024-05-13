---
title: Ativação da temperatura do centro de viagens
description: Usando o AEM Screens, saiba como este caso de uso demonstra o uso da ativação da temperatura local do centro de viagem com base nos valores preenchidos nas Planilhas Google.
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: use-case-examples
docset: aem65
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 2ec2891f-0fbe-4812-b3c4-ff160ead36b8
source-git-commit: 1cf90de7892d051b2b94b4dd57de7135269b1ee8
workflow-type: tm+mt
source-wordcount: '444'
ht-degree: 0%

---

# Ativação da temperatura do centro de viagens {#travel-center-temperature-activation}

O caso de uso a seguir demonstra o uso da ativação da temperatura local do centro de viagem com base nos valores preenchidos nas Planilhas Google.

## Descrição {#description}

Para esse caso de uso, se o valor no Google Sheets for menor que 50, uma imagem com bebidas quentes será exibida. Se o valor for maior ou igual a 50, uma imagem com bebidas frias será exibida. Se houver algum outro valor ou nenhum valor, o reprodutor exibirá uma imagem padrão.

## Pré-condições {#preconditions}

Antes de começar a implementar a ativação da temperatura local do centro de viagens, saiba como configurar ***Armazenamento de dados***, ***Segmentação de público*** e ***Ativar o direcionamento para canais*** em um projeto do AEM Screens.

Consulte [Configuração do ContextHub no AEM Screens](configuring-context-hub.md) para obter informações detalhadas.

## Fluxo básico {#basic-flow}

Siga as etapas abaixo para implementar o caso de uso de Ativação de temperatura local do centro de viagem:

1. **Preencher as planilhas do Google**

   1. Navegue até a Folha de Google ContextHubDemo.
   1. Adicionar uma coluna com **`Heading1`** com o valor correspondente de temperatura.

   ![screen_shot_2019-05-08at112911am](assets/screen_shot_2019-05-08at112911am.png)

1. **Configuração dos segmentos em Públicos-alvo de acordo com os requisitos**

   1. Navegue até os segmentos no seu público-alvo (Consulte ***Etapa 2: Configuração da segmentação de público*** in **[Configuração do ContextHub no AEM Screens](configuring-context-hub.md)** para obter mais detalhes).

   1. Clique em **Folhas A1 1** e clique em **Editar**.

   1. Clique na propriedade de comparação e clique no ícone de configuração.
   1. Clique em **googlesheets/value/1/0** no menu suspenso em **Nome da propriedade**

   1. Clique em **Operador** as **maior que ou igual** no menu suspenso

   1. Insira o **Valor** as **50**

   1. Da mesma forma, selecione o **Folhas A1 2** e clique em **Editar**.

   1. Clique em **Propriedade de comparação - Valor** e selecione o ícone de configuração.
   1. Clique em **googlesheets/value/1/0** no menu suspenso em **Nome da propriedade**

   1. Clique em **Operador** as **menor que** no menu suspenso

   1. Insira o **Valor** as **50**

1. Navegue e selecione seu canal () e clique em **Editar** na barra de ações. No exemplo a seguir, **DataDrivenWeather**, um canal sequencial é usado para mostrar a funcionalidade.

   >[!NOTE]
   >
   >Seu canal já deve ter uma imagem padrão e os Públicos-alvo devem ser pré-configurados conforme descrito em [Configuração do ContextHub no AEM Screens](configuring-context-hub.md).

   ![screen_shot_2019-05-08at113022am](assets/screen_shot_2019-05-08at113022am.png)

   >[!CAUTION]
   >
   >Seu **ContextHub** **Configurações** uso do canal **Propriedades** > **Personalização** já deve estar configurada.

   ![screen_shot_2019-05-08at114106am](assets/screen_shot_2019-05-08at114106am.png)

1. Clique em **Direcionamento** no editor e clique em **Marca** e a variável **Atividade** no menu suspenso e clique em **Iniciar o direcionamento**.

   ![new_activity3](assets/new_activity3.gif)

1. **Verificação da visualização**

   1. Clique em **Visualizar.** Além disso, abra a Planilha do Google e atualize o valor.
   1. Altere o valor para menos de 50. Você pode ver uma imagem de uma bebida fria. Se o valor no Google Sheets for 50 ou superior, você deverá ver uma imagem de uma bebida quente.

   ![resultado3](assets/result3.gif)
