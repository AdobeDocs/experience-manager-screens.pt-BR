---
title: Atualização de conteúdo usando o Screens Launch
description: Saiba como criar uma versão futura dos canais, conhecida como Launch, e definir uma data de lançamento para tornar o conteúdo ativo em dispositivos ou players.
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: authoring
docset: aem65
feature: Authoring Screens, Launches
role: Admin, Developer
level: Intermediate
exl-id: b610e5dd-e0c6-45e6-bf9b-27be2054bc8f
source-git-commit: 3b44fd920dd6c98ecc0e2b45bf95b81685647c0f
workflow-type: tm+mt
source-wordcount: '1556'
ht-degree: 0%

---

# Atualização de conteúdo usando o Screens Launch {#launches}

Os autores de conteúdo podem criar versões futuras dos canais, conhecidas como **Screens Launch** e defina ainda mais a data de ativação para este lançamento. Isso permite que o conteúdo fique ativo em dispositivos ou players na data de ativação especificada.

Com a ajuda de ***Screens Launch***, os autores podem visualizar cada canal no lançamento e devem ser capazes de iniciar uma solicitação de revisão. O grupo de aprovadores recebe uma notificação e pode aprovar ou rejeitar a solicitação. Quando a data de ativação é atingida, o conteúdo é reproduzido nos dispositivos.

Por exemplo, se o autor desejar criar versões futuras de c1, c2 (canais), uma inicialização será criada e uma data de ativação será definida (por exemplo, 10 de novembro, às 8h). Quaisquer outras atualizações no conteúdo são enviadas para revisão.

Após a aprovação e na data de ativação (10 de novembro, 8:00), esse lançamento reproduz o conteúdo nos dispositivos ou players.

## Requisitos {#requirements}

Antes de começar a usar *Screens Launch* em um projeto do AEM Screens, compreenda o conceito de período de carência e sua relevância.

A execução de uma experiência na data de ativação definida no reprodutor envolve:

* Promoção do lançamento (normalmente leva alguns segundos).

* A publicação dos recursos para publicar instâncias (geralmente leva alguns minutos, depende do tamanho dos canais ou ativos que devem ser publicados).

* Tempo necessário para concluir a atualização do conteúdo offline (normalmente, alguns minutos).

* O tempo gasto pelos reprodutores para baixar o conteúdo da instância de publicação (normalmente leva minutos, dependendo da largura de banda e do tamanho dos ativos que devem ser baixados).

* Diferenças a qualquer momento entre o servidor e o reprodutor.

### Entendendo o período de carência {#understanding-grace-period}

Para que o reprodutor possa começar a reproduzir o conteúdo na data de ativação definida, inicie as atividades anteriores à data de ativação.

Se a data de ativação for *24 de novembro, 9h* e o período de carência é *24 horas*, a sequência de ações acima será iniciada em (data de ativação - período de carência), ou seja, 23 de novembro, às 9h, horário do servidor. Isso dá 24 horas para completar todas as ações acima mencionadas para o conteúdo chegar aos reprodutores. Os players entendem que este é um conteúdo de lançamento. Dessa forma, o conteúdo não é reproduzido imediatamente, mas os players podem armazená-lo como uma versão futura e fazer com que comece a ser reproduzido exatamente na data definida de ativação no fuso horário do player.

Por exemplo, o servidor está em PST e os dispositivos estão em EST. A diferença máxima de tempo é de três horas nesse caso e presume que a promoção leva 1 minuto e a publicação do autor para a publicação leva 10 minutos, e o player pode baixar os recursos normalmente de 10 a 15 minutos. Em seguida, o período de carência = diferença de tempo (três horas):

* Mais tempo para promover o lançamento (1 minuto)
* Mais tempo para publicar o lançamento (10 minutos)
* Mais tempo para baixar no player (10-15 minutos)
* Mais buffer (30 minutos)

Igual a 3 horas e 56 minutos (14160 segundos).

Assim, sempre que você agendar qualquer lançamento em tempo real, a promoção começará antecipadamente por esse deslocamento. Na equação acima, a maioria dos itens não leva muito tempo. Você pode usar uma estimativa decente para esse deslocamento quando souber a diferença de tempo máxima entre o servidor e qualquer jogador.

>[!NOTE]
>
>Pronto para uso, o período de carência do Screens Launch é definido como 24 horas. Isso significa que, ao definir a data de ativação para qualquer lançamento dos recursos em */content/screens*, a promoção começa com esse deslocamento.

### Atualizando Período de Carência pronto para uso {#updating-out-of-the-box-grace-period}

Esta seção explica como você pode atualizar um período de carência predefinido para 10 minutos.

1. Navegue até o CRXDE Lite e, em seguida, até `/libs/system/config.author/com.adobe.cq.wcm.launches.impl.LaunchesEventHandler.config`.
1. Clique com o botão direito e copie o arquivo.
1. Navegue até `/apps/system/config` e clique com o botão direito do mouse e cole.
1. Clique duas vezes `/apps/system/config/com.adobe.cq.wcm.launches.impl.LaunchesEventHandler.config` para que você possa abrir o arquivo no editor no CRXDE Lite. Deve mostrar o período de carência do caminho */content/screens/* as **86400**. Alterar esse valor para **600**.

Agora, o conteúdo no arquivo de texto deve ser semelhante a:

```java
launches.eventhandler.launch.promotion.graceperiod=[ \
   "/content/screens(/.*):600", \
   ]
```

Como você definiu o Período de carência como 10 minutos no exemplo anterior, ao definir a data de ativação para qualquer inicialização dos recursos em */content/screens*, a promoção começa com esse deslocamento.

Por exemplo, se a data de ativação estiver definida como 24 de novembro, 9h e o período de carência for de 600 segundos, o trabalho de promoção iniciará em 24 de novembro às 8h50.

## Utilização do Screens Launch {#using-launches}

Esta seção demonstra como implementar o Screens Launch em seu projeto do AEM Screens.

### Criação de uma inicialização do Screens {#creating-a-launch}

Siga as etapas abaixo para implementar a funcionalidade Screens Launch no seu projeto do AEM Screens:

1. Crie um canal de sequência em seu projeto do AEM Screens, por exemplo **LaunchesDemo** > **Canais** > **Lançamento futuro**, conforme mostrado abaixo.

   >[!CAUTION]
   >
   >Crie um lançamento a partir de um canal pré-existente no projeto do AEM Screens.

   ![Imagem](/help/user-guide/assets/launches-images/launches-11.png)

1. Selecionar o canal **Lançamento futuro** e selecione **Criar lançamento** na barra de ações.

   ![Imagem](/help/user-guide/assets/launches-images/launches-12.png)

1. A variável **Criar lançamento** é aberto. Você pode selecionar o canal que já está visível no assistente ou selecionar **+ Adicionar canais** para adicionar o canal para o qual deseja criar a inicialização.

1. Selecionar **Próxima** do **Criar lançamento** assistente. A variável **Incluir subpáginas** for selecionada por padrão.

   ![imagem](/help/user-guide/assets/launches-images/launches-d.png)

   >[!NOTE]
   >Você pode usar **+ Adicionar canais** opção para adicionar outro canal para o qual deseja criar a inicialização.

   Para usar **Adicionar canais** navegue até o canal para o qual deseja criar a inicialização e selecione **Selecionar**.

   A variável **Selecionar** A opção estará desativada se você tentar selecionar vários canais ou uma pasta para adicionar o lançamento.

   ![imagem](/help/user-guide/assets/launches-images/launches-14.png)

   Depois de selecionar o canal/canais, selecione **Próxima**.


1. Insira o **Título da inicialização** as **SummerPromotions** e você não precisa definir a variável **Data de lançamento**, conforme mostrado na figura abaixo. Selecione **Criar**.

   >[!NOTE]
   >
   >*Ativando ou verificando* a opção **Herdar dados online da página de origem** permite que os canais sejam criados como live copies no lançamento. Se alguma alteração for feita no canal original, ela será aplicada automaticamente aos canais de inicialização.
   >
   >
   >*Desativando ou desmarcando* **Herdar dados online da página de origem** permite que os canais sejam copiados sem qualquer relação dinâmica na inicialização. Portanto, se alguma alteração for feita no canal original, essas alterações não serão aplicadas aos canais de inicialização.

   ![Imagem](/help/user-guide/assets/launches-images/launches-c.png)

   >[!NOTE]
   >
   >Você pode definir a data de inicialização em tempo real nesta etapa ou pode configurá-la posteriormente, ao editar as propriedades da inicialização, uma vez que ela já tenha sido criada.

   **Noções básicas sobre o escopo de promoção do lançamento**

   * **Promover lançamento completo** - Todos os canais do lançamento são promovidos na data de ativação definida.
   * **Promover páginas modificadas** - Somente os recursos modificados do Launch são promovidos. Use essa opção quando a revisão da inicialização não for necessária.
   * **Promover páginas aprovadas** - Essa opção requer que o fluxo de trabalho de aprovação de inicialização seja executado nos canais de inicialização. Somente as páginas aprovadas são promovidas na data de ativação definida.

     >[!CAUTION]
     >
     >A data de lançamento respeita o fuso horário do player/dispositivo em vez do servidor.

1. Observe que o seu lançamento foi criado. Você pode selecionar **Abertura** para exibir as páginas no editor ou selecione **Concluído** para navegar de volta ao seu projeto.

   ![screen_shot_2019-06-25at20355pm](assets/screen_shot_2019-06-25at20355pm.png)

   Selecionar **Concluído** permitem navegar de volta para o **Lançamento futuro** canal.

   ![Imagem](/help/user-guide/assets/launches-images/launches-16.png)


### Editar as propriedades do Launch para definir a data de ativação e o escopo {#editing-the-launch-properties-to-set-the-live-date-and-scope}

Após a criação da inicialização, é possível atualizar as propriedades, como data de ativação, título da inicialização e escopo da promoção, usando **Propriedades do lançamento**.

* **Data de lançamento** - A data em tempo real, ou seja, a data ou hora em que o conteúdo é reproduzido no reprodutor do Screens de acordo com o fuso horário do reprodutor.
* **Pronto para produção** - Permite que os canais sejam publicados após promovê-los, isso é ativado para pronta utilização, portanto, não é necessário alterá-lo.
* **Escopo** - Decide quais canais são promovidos durante a promoção do lançamento.

Siga as etapas abaixo para editar as propriedades do lançamento:

1. Navegar até o canal **Lançamento futuro** *(a inicialização pendente)* e selecione o canal conforme mostrado na figura abaixo.

   ![imagem](/help/user-guide/assets/launches-images/launches-17.png)

1. Selecionar **Painel** na barra de ações e você verá a **LANÇAMENTOS PENDENTES** no painel do canal.

   ![imagem](/help/user-guide/assets/launches-images/launches-18.png)

1. Selecione o lançamento e **Propriedades do lançamento** do **LANÇAMENTOS PENDENTES** painel.

   ![imagem](/help/user-guide/assets/launches-images/launches-19.png)

### Editar o lançamento do Screens para adicionar ou remover canais  {#editing-the-screens-launch-to-add-or-remove-channels}

Após criar a inicialização, é possível adicionar ou remover canais da inicialização existente usando **Editar lançamento** opção.

Quando terminar, selecione **Salvar** para navegar de volta para **Lançamento futuro** canal.

### Promover o lançamento do Screens manualmente{#promote-the-screens-launch-manually}

É possível promover o lançamento manualmente usando o **`Promote Launch`** opção no **LANÇAMENTOS PENDENTES** painel.

Você pode escolher os recursos que deseja promover como parte dessa promoção manual na **Iniciar assistente de promoção**.

![imagem](/help/user-guide/assets/launches-images/launches-e.png)

1. Você pode ativar ou desativar a opção para excluir o lançamento após a produção.
1. Você pode definir a variável **Escopo** do lançamento com as seguintes opções:
   * **Promover lançamento completo** - Todos os canais do lançamento são promovidos na data de ativação definida.
   * **Promover páginas modificadas** - Somente os recursos modificados do Launch são promovidos. Use essa opção quando a revisão da inicialização não for necessária.
   * **Promover páginas aprovadas** - Essa opção requer que o fluxo de trabalho de aprovação de inicialização seja executado nos canais de inicialização. Somente as páginas aprovadas são promovidas na data de ativação definida.
   * **Divulgar a página atual** - Essa opção exige que o fluxo de trabalho de aprovação da inicialização seja executado somente para a página atual.
1. Selecionar **Próxima** no **Promover lançamento** assistente.
1. Selecionar **Promover** para promover o lançamento.

### Excluir o lançamento do Screens

É possível excluir o lançamento usando **Excluir lançamento** opção no **LANÇAMENTOS PENDENTES** painel.

>[!CAUTION]
>
>Essa ação também exclui todos os descendentes (inicializações aninhadas).
