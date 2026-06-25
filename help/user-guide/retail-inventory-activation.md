---
title: Ativação Direcionada de Estoque de Varejo
description: Saiba mais sobre este caso de uso do AEM Screens que mostra o estoque de estoque de varejo para três camisetas coloridas diferentes.
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: use-case-examples
docset: aem65
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 926f529b-f3cf-471d-83b4-6ccb628cf160
TQID: https://experienceleague.adobe.com/RVv6pOsJlK-uDu7AfobsDvpYlKQJ6nj4Q0cKSbTlBv4
product_v2: id: a27b4747-2f72-4fb7-9936-be5d11dd2c4aid: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2: id: a5fd0e22-1a77-4f49-a6af-7a57fff19aedid: eb3ad9f8-54a2-45f3-abb1-d3976415a718
subfeature_v2: id: f5973e90-a5a3-4b84-8602-ee120d4ce9b1
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2: id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2: id: e0eb8757-182f-49f3-94a4-1587d16f5094id: ff2b9b37-92e0-45fc-b853-379d44c08c89
source-git-commit: d4664dd5678eaccabe656398c437dca264d4675e
workflow-type: tm+mt
source-wordcount: 636
ht-degree: 0%

---

# Ativação Direcionada de Estoque de Varejo {#retail-inventory-targeted-activation}

>[!IMPORTANT]
>Esse conteúdo é válido para o AEM no local/AMS (AEM 6.5LTS e AEM 6.5). Para ver o conteúdo do AEM as a Cloud Service Screens, consulte o [guia do AEM as a Cloud Service](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/screens-as-cloud-service/overview/introduction).

O caso de uso a seguir demonstra três imagens diferentes com base nos valores na sua Planilha do Google.

## Descrição {#description}

Este caso de uso mostra o estoque de estoque de estoque de varejo para três camisetas coloridas diferentes. Dependendo do número de camisetas disponíveis em estoque gravadas no Google Sheets, a imagem (camiseta vermelha, verde ou azul) com o número mais alto será exibida.

O suéter Vermelho, Verde ou Azul é exibido com base no valor mais alto do número de suéteres disponíveis.

## Pré-condições {#preconditions}

Antes de começar a implementar a ativação de direcionamento de estoque de varejo, saiba como configurar o ***Armazenamento de dados***, a ***Segmentação de público*** e a ***Habilitar o direcionamento para Canais*** em um projeto do AEM Screens.

Consulte [Configurando o ContextHub no AEM Screens](configuring-context-hub.md) para obter informações detalhadas.

## Fluxo básico {#basic-flow}

Siga as etapas abaixo para implementar o caso de uso de Ativação de Inventário de Varejo:

1. **Preenchendo as Planilhas Google**

   1. Navegue até a Folha de Google ContextHubDemo.
   1. Adicione três colunas (vermelha, verde e azul) com valores correspondentes para três sweatshirts diferentes.

   ![screen_shot_2019-05-06at101755am](assets/screen_shot_2019-05-06at101755am.png)

1. **Configurando os Públicos de acordo com os requisitos**

   1. Navegue até os segmentos no seu público-alvo (Consulte ***Etapa 2: Configuração da segmentação de público-alvo*** na página **[Configuração do ContextHub no AEM Screens](configuring-context-hub.md)** para obter mais detalhes).

   1. Adicione três novos segmentos **Para_Vermelho**, **Para_Verde** e **Para_Azul**.

   1. Clique em **For_Red** e em **Editar** na barra de ações.

   1. Arraste e solte a **Comparação: Propriedade - Propriedade** no editor.
   1. Clique no ícone **Configuração**.
   1. Clique em **googlesheets/value/1/2** no menu suspenso em **Nome da Primeira Propriedade**.
   1. Clique no **Operador** e como **maior que** no menu suspenso.
   1. Clique em **Tipo de Dados** e como **número**.
   1. Clique em **googlesheets/value/1/1** na lista suspensa em **Nome da segunda propriedade**.
   1. Arraste e solte **outra Comparação: Propriedade - Propriedade** no editor e clique no ícone **Configuração**.
   1. Clique em **googlesheets/value/1/2** no menu suspenso em **Nome da Primeira Propriedade**.
   1. Clique no **Operador** e como **maior que** no menu suspenso.
   1. Clique em **Tipo de Dados** e como **número**.
   1. Clique em **googlesheets/value/1/0** na lista suspensa em **Nome da segunda propriedade**.

   ![screen_shot_2019-05-06at102600am](assets/screen_shot_2019-05-06at102600am.png)

   Da mesma forma, edite e adicione regras de propriedade de comparação ao segmento **For_Blue**, conforme mostrado na figura abaixo:

   ![screen_shot_2019-05-06at103728am](assets/screen_shot_2019-05-06at103728am.png)

   Da mesma forma, edite e adicione regras de propriedade de comparação ao segmento **For_Green**, conforme mostrado na figura abaixo:

   ![screen_shot_2019-05-06at103418am](assets/screen_shot_2019-05-06at103418am.png)

   >[!NOTE]
   >
   >Observe que para os segmentos **For_Green** e **For_Green**, os dados não podem ser resolvidos no editor, pois somente a primeira comparação é válida a partir de agora, de acordo com os valores na Planilha do Google.

1. Navegue e clique no canal **DataDrivenRetail** (um canal de sequência).
1. Clique em **Editar** na barra de ações.

   ![screen_shot_2019-05-06at104257am](assets/screen_shot_2019-05-06at104257am.png)

   >[!CAUTION]
   >
   >Você já deve ter configurado suas **Configurações do** ContextHub **** usando a guia **Propriedades** > **Personalization** do canal.

   ![screen_shot_2019-05-06at105214am](assets/screen_shot_2019-05-06at105214am.png)

   >[!NOTE]
   >
   >Clique na **Marca** e na **Área** para que as atividades sejam listadas corretamente quando você iniciar o processo de Direcionamento.

1. **Adicionando uma imagem padrão**

   1. Adicione uma imagem padrão ao canal e clique em **Direcionamento**.
   1. Clique em **Marca** e na **Atividade** no menu suspenso e clique em **Iniciar o Direcionamento**.
   1. Clique em **Iniciar o direcionamento**.

   ![screen_shot_2019-05-06at121253pm](assets/screen_shot_2019-05-06at121253pm.png)

   >[!NOTE]
   >
   >Antes de começar o direcionamento, adicione os segmentos (**For_Green**, **For_Red** e **For_Blue**) selecionando **+ Adicionar direcionamento de experiência** no painel lateral, como mostrado na figura abaixo.

   ![screen_shot_2019-05-06at123554pm](assets/screen_shot_2019-05-06at123554pm.png)

1. Adicione as imagens a todos os três cenários diferentes, conforme mostrado abaixo.

   ![direcionamento_de_varejo](assets/retail_targeting.gif)

1. **Verificando a Visualização**

   1. Clique em **Visualizar.** Além disso, abra a Planilha do Google e atualize o valor.
   1. Altere o valor de todas as três colunas diferentes. Observe as atualizações de imagem de exibição de acordo com o valor mais alto no inventário.

   ![resultado_varejo](assets/retail_result.gif)
