---
title: Atualizações de conteúdo usando o Screens Launch
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
source-git-commit: dcaaa1c7ab0a55cecce70f593ed4fded8468130b
workflow-type: tm+mt
source-wordcount: '1568'
ht-degree: 0%

---

# Atualizações de conteúdo usando o Screens Launch {#launches}

Os autores de conteúdo podem criar uma versão futura dos canais e definir ainda mais a data de ativação para esse lançamento. Essa capacidade permite que o conteúdo fique ativo em dispositivos ou players na data de ativação especificada.

Com a ajuda do ***Screens Launch***, os autores podem visualizar cada canal no lançamento e devem poder iniciar uma solicitação de revisão. O grupo de aprovadores recebe uma notificação e pode aprovar ou rejeitar a solicitação. Quando a data de ativação é atingida, o conteúdo é reproduzido nos dispositivos.

Por exemplo, se o autor desejar criar versões futuras de c1, c2 (canais), uma inicialização será criada e uma data de ativação será definida (por exemplo, 10 de novembro, às 8h). Quaisquer outras atualizações no conteúdo são enviadas para revisão.

Após a aprovação e na data de ativação (10 de novembro, 8:00), esse lançamento reproduz o conteúdo nos dispositivos ou players.

## Requisitos {#requirements}

Antes de começar a usar o *Screens Launch* em um projeto do AEM Screens, compreenda o conceito de período de carência e sua relevância.

A execução de uma experiência na data de ativação definida no reprodutor envolve:

* Promoção do lançamento (normalmente leva alguns segundos).

* A publicação dos recursos para publicar instâncias (geralmente leva alguns minutos, depende do tamanho dos canais ou ativos que devem ser publicados).

* Tempo necessário para a conclusão da atualização do conteúdo offline (normalmente, leva alguns minutos).

* O tempo gasto pelos reprodutores para baixar o conteúdo da instância de publicação (normalmente leva minutos, dependendo da largura de banda e do tamanho dos ativos que devem ser baixados).

* Diferenças a qualquer momento entre o servidor e o reprodutor.

### Entendendo o período de carência {#understanding-grace-period}

Para que o reprodutor possa começar a reproduzir o conteúdo na data de ativação definida, inicie as atividades anteriores à data de ativação.

Se a data de ativação for *24 de novembro, 9h* e *24 horas* for o período de carência, a sequência de ações acima iniciará em (data de ativação - período de carência), ou seja, 23 de novembro, 9h horário do servidor. Essa configuração de 24 horas para concluir todas as ações mencionadas acima para que o conteúdo chegue aos reprodutores. Os jogadores entendem que esse período é um conteúdo de lançamento. Dessa forma, o conteúdo não é reproduzido imediatamente, mas os players podem armazená-lo como uma versão futura e fazer com que comece a ser reproduzido exatamente na data definida de ativação no fuso horário do player.

Por exemplo, o servidor está em PST e os dispositivos estão em EST. A diferença máxima de tempo é de três horas. Ele pressupõe que a promoção leva 1 minuto e a publicação do autor para a publicação leva 10 minutos, e o reprodutor pode baixar os recursos normalmente em 10 a 15 minutos. Em seguida, o período de carência = diferença de tempo (três horas):

* Mais tempo para promover o lançamento (1 minuto)
* Mais tempo para publicar o lançamento (10 minutos)
* Mais tempo para baixar no player (10-15 minutos)
* Mais buffer (30 minutos)

Portanto, 3 horas e 56 minutos (14.160 segundos).

Assim, sempre que você agendar qualquer lançamento em tempo real, a promoção começará antecipadamente levando em conta esse deslocamento. Na equação acima, a maioria dos itens não leva muito tempo. Você pode usar uma estimativa decente para este deslocamento quando você sabe a diferença máxima de tempo entre o servidor e qualquer jogador.

>[!NOTE]
>
>Pronto para uso, o período de carência do Screens Launch é definido para 24 horas. Isso significa que quando você define uma data de ativação para qualquer inicialização dos recursos em */content/screens*, a promoção começa com este deslocamento.

### Atualização do período de carência predefinido {#updating-out-of-the-box-grace-period}

Esta seção explica como atualizar um período de carência predefinido para 10 minutos.

1. Navegue até CRXDE Lite e, em seguida, até `/libs/system/config.author/com.adobe.cq.wcm.launches.impl.LaunchesEventHandler.config`.
1. Clique com o botão direito e copie o arquivo.
1. Navegue até `/apps/system/config` e clique com o botão direito do mouse e cole.
1. Clique duas vezes em `/apps/system/config/com.adobe.cq.wcm.launches.impl.LaunchesEventHandler.config` para abrir o arquivo no editor no CRXDE Lite. Deve mostrar o período de carência para o caminho */content/screens/* como **86400**. Altere esse valor para **600**.

Agora, o conteúdo no arquivo de texto deve ser semelhante a:

```java
launches.eventhandler.launch.promotion.graceperiod=[ \
   "/content/screens(/.*):600", \
   ]
```

Você definiu o período de carência como 10 minutos no exemplo anterior. Portanto, ao definir uma data de ativação para qualquer inicialização dos recursos em */content/screens*, a promoção começa com este deslocamento.

Por exemplo, se a data de ativação estiver definida como 24 de novembro, às 9h e o período de carência for de 600 segundos, o trabalho de promoção iniciará em 24 de novembro às 8h50.

## Uso do Screens Launch {#using-launches}

Esta seção demonstra como implementar o Screens Launch em seu projeto do AEM Screens.

### Criação de uma inicialização do Screens {#creating-a-launch}

Siga as etapas abaixo para implementar a funcionalidade do Screens Launch no seu projeto do AEM Screens:

1. Crie um canal de sequência em seu projeto do AEM Screens, por exemplo **LaunchesDemo** > **Channels** > **FutureLaunch**, como mostrado abaixo.

   >[!CAUTION]
   >
   >Crie um lançamento a partir de um canal pré-existente no projeto do AEM Screens.

   ![Imagem](/help/user-guide/assets/launches-images/launches-11.png)

1. Clique no canal **FutureLaunch** e clique em **Criar inicialização** na barra de ações.

   ![Imagem](/help/user-guide/assets/launches-images/launches-12.png)

1. O assistente **Criar inicialização** é aberto. Você pode clicar no canal que já está visível no assistente ou clicar em **+ Adicionar Canais** para adicionar o canal para o qual deseja criar a inicialização.

1. Clique em **Avançar** no assistente **Criar inicialização**. A opção **Incluir subpáginas** está selecionada por padrão.

   ![imagem](/help/user-guide/assets/launches-images/launches-d.png)

   >[!NOTE]
   >Você pode usar a opção **+ Adicionar Canais** para adicionar outro canal para o qual deseja criar a inicialização.

   Para usar a opção **Adicionar Canais**, navegue até o canal para o qual deseja criar a inicialização e clique em **Selecionar**.

   A opção **Selecionar** será desabilitada se você tentar clicar em vários canais ou em uma pasta para adicionar a inicialização.

   ![imagem](/help/user-guide/assets/launches-images/launches-14.png)

   Depois de clicar no canal/canais, clique em **Avançar**.


1. Insira o **Título da Inicialização** como **SummerPromotions** e não será necessário definir a **Data da Inicialização**, como mostrado na figura abaixo. Clique em **Criar**.

   >[!NOTE]
   >
   >*Habilitar ou verificar* a opção **Herdar dados online da página de origem** permite que os canais sejam criados como cópias online na inicialização. Se alguma alteração for feita no canal original, ela será aplicada automaticamente aos canais de inicialização.
   >
   >
   >*Desabilitar ou desmarcar* **Herdar dados online da página de origem** permite que os canais sejam copiados sem qualquer relação dinâmica na inicialização. Portanto, se alguma alteração for feita no canal original, essas alterações não serão aplicadas aos canais de inicialização.

   ![Imagem](/help/user-guide/assets/launches-images/launches-c.png)

   >[!NOTE]
   >
   >Você pode definir a data de inicialização em tempo real nesta etapa ou pode configurá-la posteriormente, ao editar as propriedades da inicialização, uma vez que ela já tenha sido criada.

   **Noções básicas sobre o escopo de promoção de lançamento**

   * **Promover lançamento completo** - Todos os canais do lançamento são promovidos na data de ativação definida.
   * **Promover páginas modificadas** - Somente os recursos de inicialização modificados são promovidos. Use essa opção quando a revisão da inicialização não for necessária.
   * **Promover páginas aprovadas** - Essa opção requer que o fluxo de trabalho de aprovação da inicialização seja executado nos canais de inicialização. Somente as páginas aprovadas são promovidas na data de ativação definida.

     >[!CAUTION]
     >
     >A data de inicialização respeita o fuso horário do player/dispositivo em vez dos servidores.

1. Observe que o seu lançamento foi criado. Você pode clicar em **Abrir** para exibir as páginas no editor ou clicar em **Concluído** para navegar de volta para o seu projeto.

   ![screen_shot_2019-06-25at20355pm](assets/screen_shot_2019-06-25at20355pm.png)

   Selecionar **Concluído** permite navegar de volta para o canal do **FutureLaunch**.

   ![Imagem](/help/user-guide/assets/launches-images/launches-16.png)


### Editar as propriedades do Launch para definir a data de ativação e o escopo {#editing-the-launch-properties-to-set-the-live-date-and-scope}

Após a criação da inicialização, você pode atualizar as propriedades, como data de ativação, título da inicialização e escopo da promoção, usando **Propriedades da inicialização**.

* **Data de inicialização** - A data de ativação, ou seja, a data ou a hora em que o conteúdo é reproduzido no Screens Player de acordo com o fuso horário do player.
* **Pronto para produção** - Após a promoção, permite que os canais sejam publicados e o recurso predefinido está habilitado, portanto, não é necessário alterá-lo.
* **Escopo** - Decide quais canais são promovidos durante a promoção de inicialização.

Siga as etapas abaixo para editar as propriedades do lançamento:

1. Navegue até o canal **FutureLaunch** *(a inicialização pendente)* e clique no canal conforme mostrado na figura abaixo.

   ![imagem](/help/user-guide/assets/launches-images/launches-17.png)

1. Clique em **Painel** na barra de ações e você verá o painel **INICIALIZAÇÕES PENDENTES** no painel do canal.

   ![imagem](/help/user-guide/assets/launches-images/launches-18.png)

1. Clique na inicialização e em **Propriedades da inicialização** no painel **INICIALIZAÇÕES PENDENTES**.

   ![imagem](/help/user-guide/assets/launches-images/launches-19.png)

### Edição do Screens Launch para adicionar ou remover canais {#editing-the-screens-launch-to-add-or-remove-channels}

Após criar a inicialização, você pode adicionar ou remover canais para a inicialização existente usando a opção **Editar Inicialização**.

Quando terminar, clique em **Salvar** para voltar para o canal **FutureLaunch**.

### Promover o Screens Launch manualmente{#promote-the-screens-launch-manually}

Você pode promover a inicialização manualmente usando a opção **`Promote Launch`** do painel **LANÇAMENTOS PENDENTES**.

Você pode escolher os recursos que deseja promover como parte desta promoção manual no **Assistente de Promoção do Launch**.

![imagem](/help/user-guide/assets/launches-images/launches-e.png)

1. Você pode ativar ou desativar a opção para excluir o lançamento após a produção.
1. Você pode definir o **Escopo** da inicialização com as seguintes opções:
   * **Promover lançamento completo** - Todos os canais do lançamento são promovidos na data de ativação definida.
   * **Promover páginas modificadas** - Somente os recursos de inicialização modificados são promovidos. Use essa opção quando a revisão da inicialização não for necessária.
   * **Promover páginas aprovadas** - Essa opção requer que o fluxo de trabalho de aprovação da inicialização seja executado nos canais de inicialização. Somente as páginas aprovadas são promovidas na data de ativação definida.
   * **Promover página atual** - Esta opção requer que o fluxo de trabalho de aprovação da inicialização seja executado somente para a página atual.
1. Clique em **Avançar** no assistente **Promover inicialização**.
1. Clique em **Promover** para promover a inicialização.

### Exclusão do Screens Launch

Você pode excluir o lançamento usando a opção **Excluir Lançamento** do painel **LANÇAMENTOS PENDENTES**.

>[!CAUTION]
>
>Essa ação também exclui todos os descendentes (inicializações aninhadas).
