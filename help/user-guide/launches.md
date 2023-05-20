---
title: Atualização de conteúdo usando o Screens Launch
seo-title: Content Update using Screens Launch
description: Os autores de conteúdo podem criar versões futuras do(s) canal(is), conhecidas como Inicialização, e definir ainda mais a data de ativação para esta inicialização permite que o conteúdo fique ativo em dispositivos ou players.
seo-description: Content authors can create future version of the channel(s), known as Launch and further setting live date for this launch allows content to be live in devices or players.
uuid: fb13117c-b99b-48bd-adb6-040dbd13af16
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: authoring
discoiquuid: 9cd8892b-fe5d-4ad3-9b10-10ff068adba6
docset: aem65
feature: Authoring Screens, Launches
role: Admin, Developer
level: Intermediate
exl-id: b610e5dd-e0c6-45e6-bf9b-27be2054bc8f
source-git-commit: 2cc613454d0d20a42871858e3d754e1b0e161dc3
workflow-type: tm+mt
source-wordcount: '1580'
ht-degree: 0%

---

# Atualização de conteúdo usando o Screens Launch {#launches}

Os autores de conteúdo podem criar versões futuras do(s) canal(is), conhecidas como **Screens Launch** e defina ainda mais a data de ativação para este lançamento. Isso permite que o conteúdo fique ativo em dispositivos ou players na data de ativação especificada.

Com a ajuda de ***Screens Launch***, os autores podem visualizar cada canal no lançamento e devem ser capazes de iniciar uma solicitação de revisão. O grupo de aprovadores receberá uma notificação e poderá aprovar ou rejeitar a solicitação. Quando a data de ativação é atingida, o conteúdo é reproduzido nos dispositivos.

Por exemplo, se o autor quiser criar versões futuras de c1, c2 (canais), uma inicialização será criada e uma data de ativação será definida (por exemplo, 10 de novembro às 8h). Quaisquer outras atualizações no conteúdo são enviadas para revisão.

Depois de aprovado e na data de ativação (10 de novembro, às 8h), esse lançamento reproduzirá o conteúdo nos dispositivos ou players.

## Requisitos {#requirements}

Antes de começar a aproveitar *Screens Launch* em um projeto do AEM Screens, compreenda o conceito de período de carência e sua relevância.

A execução de uma experiência na data de ativação definida no reprodutor envolve:

* promoção do lançamento (normalmente leva alguns segundos)

* a publicação dos recursos para publicar instâncias (geralmente leva alguns minutos, depende do tamanho dos canais ou ativos que precisam ser publicados)

* tempo gasto pela atualização do conteúdo offline para ser concluída (normalmente leva alguns minutos)

* tempo gasto pelos reprodutores para baixar o conteúdo da instância de publicação (normalmente leva minutos, dependendo da largura de banda e do tamanho dos ativos que precisam ser baixados)

* quaisquer diferenças de tempo entre o servidor e o reprodutor

### Entendendo o período de carência {#understanding-grace-period}

Para que o reprodutor possa começar a reproduzir o conteúdo na data de ativação definida, precisamos iniciar as atividades anteriores à data de ativação.

Se a data de ativação for *24 de novembro, 9h* e o período de carência é *24 horas*, a sequência de ações acima será iniciada em (data de ativação - período de carência), ou seja, 23 de novembro, 9h, hora do servidor. Isso dá 24 horas de tempo para concluir todas as ações mencionadas acima e o conteúdo chegará aos players. Os jogadores entenderão que se trata de um conteúdo de lançamento, portanto, o conteúdo não será reproduzido imediatamente, mas os jogadores armazenarão esse conteúdo como uma versão futura e começarão a reproduzir exatamente na data definida de ativação no fuso horário do player.

Por exemplo, digamos que o servidor esteja em PST e os dispositivos estejam em EST, a diferença máxima de tempo é de 3 horas nesse caso e suponha que a promoção levará 1 min, e a publicação do autor para a publicação levará 10 min, e o player poderá baixar os recursos normalmente em 10-15 min. Então, período de carência = diferença de tempo (3 horas) + tempo para promover o lançamento (1 min) + tempo para publicar o lançamento (10 min) + tempo para baixar no player (10-15 min) + buffer (para estar seguro, diga 30 min) = 3 horas 56 min = 14160 segundos.

Assim, sempre que programarmos qualquer lançamento em tempo real, a promoção começará antecipadamente por esse deslocamento. Na equação acima, a maioria dos itens não leva muito tempo, podemos usar um palpite decente para esse deslocamento, uma vez que sabemos a diferença máxima de tempo entre o servidor e qualquer jogador.

>[!NOTE]
>
>Pronto para uso, o período de carência do Screens Launch é definido como 24 horas, o que significa que, quando definimos a data de ativação para qualquer lançamento dos recursos em */content/screens*, a promoção começará com esse deslocamento.

### Atualizando Período de Carência pronto para uso {#updating-out-of-the-box-grace-period}

Esta seção explica como você pode atualizar um período de carência predefinido para 10 minutos.

1. Navegue até o CRXDE Lite e, em seguida, até `/libs/system/config.author/com.adobe.cq.wcm.launches.impl.LaunchesEventHandler.config`.
2. Clique com o botão direito e copie o arquivo.
3. Navegue até `/apps/system/config` e clique com o botão direito do mouse e cole.
4. Clique duas vezes em `/apps/system/config/com.adobe.cq.wcm.launches.impl.LaunchesEventHandler.config` para abrir o arquivo no editor no CRXDE Lite. Deve mostrar o período de carência do caminho */content/screens/* as **86400**. Alterar esse valor para **600**.

Agora, o conteúdo no arquivo de texto deve ser semelhante a:

```java
launches.eventhandler.launch.promotion.graceperiod=[ \
   "/content/screens(/.*):600", \
   ]
```

Como você definiu o Período de carência como 10 minutos no exemplo anterior, ao definir a data de ativação para qualquer inicialização dos recursos em */content/screens*, a promoção começará com esse deslocamento.

Por exemplo, se a data de ativação for definida como 24 de novembro, 9h e o período de carência for de 600 segundos, o trabalho de promoção será iniciado em 24 de novembro às 8h50.

## Utilização do Screens Launch {#using-launches}

Esta seção demonstra como implementar o Screens Launch em seu projeto do AEM Screens.

### Criação de uma inicialização do Screens {#creating-a-launch}

Siga as etapas abaixo para implementar a funcionalidade Screens Launch no seu projeto do AEM Screens:

1. Crie um canal de sequência em seu projeto do AEM Screens, por exemplo **LaunchesDemo** —> **Canais** —> **Lançamento futuro**, conforme mostrado abaixo.

   >[!CAUTION]
   >
   >Você deve criar uma inicialização em um canal pré-existente no projeto do AEM Screens.

   ![Imagem](/help/user-guide/assets/launches-images/launches-11.png)

1. Selecionar o canal **Lançamento futuro** e clique em **Criar lançamento** na barra de ações.

   ![Imagem](/help/user-guide/assets/launches-images/launches-12.png)

1. A variável **Criar lançamento** é aberto. Selecione o canal que já está visível no assistente ou clique em **+ Adicionar canais** para adicionar o canal para o qual deseja criar a inicialização.

1. Clique em **Próxima** do **Criar lançamento** assistente. A variável **Incluir subpáginas** for selecionada por padrão.

   ![imagem](/help/user-guide/assets/launches-images/launches-d.png)

   >[!NOTE]
   >Você pode usar **+ Adicionar canais** opção para adicionar outro canal para o qual deseja criar a inicialização.

   Para usar **Adicionar canais** navegue até o canal para o qual deseja criar a inicialização e clique em **Selecionar**.

   A variável **Selecionar** A opção estará desativada se você tentar selecionar vários canais ou uma pasta para adicionar o lançamento.

   ![imagem](/help/user-guide/assets/launches-images/launches-14.png)

   Depois de selecionar o canal/canais, clique em **Próxima**.


1. Insira o **Título da inicialização** as **SummerPromotions** e você não precisa definir a variável **Data de lançamento**, conforme mostrado na figura abaixo. Clique em **Criar**.

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

   * **Promover lançamento completo**: todos os canais do lançamento são promovidos na data de ativação definida.
   * **Promover páginas modificadas**: somente os recursos de inicialização modificados serão promovidos. É recomendável usar essa opção quando a revisão do lançamento não for necessária.
   * **Promover páginas aprovadas**: essa opção requer que o fluxo de trabalho de aprovação de inicialização seja executado nos canais de inicialização. Somente as páginas aprovadas serão promovidas na data de ativação definida.

      >[!CAUTION]
      >
      >A data de lançamento respeita o fuso horário do player/dispositivo em vez do servidor.

1. Você verá que o seu lançamento foi criado. Você pode clicar em **Abertura** para exibir as páginas no editor ou clique em **Concluído** para navegar de volta ao seu projeto.

   ![screen_shot_2019-06-25at20355pm](assets/screen_shot_2019-06-25at20355pm.png)

   Clicando **Concluído** O permite navegar de volta para o **Lançamento futuro** canal.

   ![Imagem](/help/user-guide/assets/launches-images/launches-16.png)


### Editar as propriedades do Launch para definir a data de ativação e o escopo {#editing-the-launch-properties-to-set-the-live-date-and-scope}

Após a criação da inicialização, é possível atualizar as propriedades, como data de ativação, título da inicialização e escopo da promoção, usando **Propriedades do lançamento**.

* **Data de lançamento**, refere-se à data de ativação, ou seja, a data ou a hora em que o conteúdo será reproduzido no reprodutor do Screens de acordo com o fuso horário do reprodutor.
* **Pronto para produção**, permite que os canais sejam publicados após promovê-los, isso está ativado para que não seja necessário alterá-lo.
* **Escopo**, decide quais canais serão promovidos durante a promoção do lançamento.


Siga as etapas abaixo para editar as propriedades do lançamento:

1. Navegar até o canal **Lançamento futuro**, *(que é a inicialização pendente)* e selecione o canal, conforme mostrado na figura abaixo.

   ![imagem](/help/user-guide/assets/launches-images/launches-17.png)

1. Clique em **Painel** na barra de ações e você verá a **LANÇAMENTOS PENDENTES** no painel do canal.

   ![imagem](/help/user-guide/assets/launches-images/launches-18.png)

1. Selecione o lançamento e clique em **Propriedades do lançamento** do **LANÇAMENTOS PENDENTES** painel.

   ![imagem](/help/user-guide/assets/launches-images/launches-19.png)

### Editar o lançamento do Screens para adicionar ou remover canais  {#editing-the-screens-launch-to-add-or-remove-channels}

Após criar a inicialização, é possível adicionar ou remover canais da inicialização existente usando **Editar lançamento** opção.

Quando terminar, clique em **Salvar** para navegar de volta para **Lançamento futuro** canal.

### Promover o lançamento do Screens manualmente{#promote-the-screens-launch-manually}

É possível promover o lançamento manualmente usando o **Promover lançamento** opção no **LANÇAMENTOS PENDENTES** painel.

Você pode escolher os recursos que deseja promover como parte dessa promoção manual na **Iniciar assistente de promoção**.

![imagem](/help/user-guide/assets/launches-images/launches-e.png)

1. Você pode ativar ou desativar a opção para excluir o lançamento após a produção.
1. Você pode definir a variável **Escopo** do lançamento, com as seguintes opções:
   1. **Promover lançamento completo**: todos os canais do lançamento são promovidos na data de ativação definida.
   1. **Promover páginas modificadas**: somente os recursos de inicialização modificados serão promovidos. É recomendável usar essa opção quando a revisão do lançamento não for necessária.
   1. **Promover páginas aprovadas**: essa opção requer que o fluxo de trabalho de aprovação de inicialização seja executado nos canais de inicialização. Somente as páginas aprovadas serão promovidas na data de ativação definida.
   1. **Divulgar a página atual**: essa opção requer que o fluxo de trabalho de aprovação da inicialização seja executado somente para a página atual.
1. Clique em **Próxima** no **Promover lançamento** assistente.
1. Clique em **Promover** para promover o lançamento.

### Excluir o lançamento do Screens {#deleting-the-screens-launch}

É possível excluir o lançamento usando **Excluir lançamento** opção no **LANÇAMENTOS PENDENTES** painel.

>[!CAUTION]
>
>Essa ação também excluirá todos os descendentes (inicializações aninhadas).
