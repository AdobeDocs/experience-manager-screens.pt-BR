---
title: Atualização de conteúdo usando o Screens Launch
seo-title: Atualização de conteúdo usando o Screens Launch
description: Os autores de conteúdo podem criar uma versão futura do(s) canal(s), conhecida como Iniciar e definir a data de ativação para esta inicialização permite que o conteúdo seja exibido em dispositivos ou players.
seo-description: Os autores de conteúdo podem criar uma versão futura do(s) canal(s), conhecida como Iniciar e definir a data de ativação para esta inicialização permite que o conteúdo seja exibido em dispositivos ou players.
uuid: fb13117c-b99b-48bd-adb6-040dbd13af16
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: authoring
discoiquuid: 9cd8892b-fe5d-4ad3-9b10-10ff068adba6
docset: aem65
translation-type: tm+mt
source-git-commit: 081db31efda17ac12cdc88f79ed2f4e1fbfc7edf
workflow-type: tm+mt
source-wordcount: '1616'
ht-degree: 0%

---


# Atualização de conteúdo usando o Screens Launch {#launches}

Os autores de conteúdo podem criar uma versão futura do(s) canal(s), conhecida como **Inicialização de telas**, e ainda definir a data de ativação para essa inicialização. Isso permite que o conteúdo seja exibido em dispositivos ou players na data ativa especificada.

Com a ajuda de ***Screens Launch***, os autores podem pré-visualização cada canal na inicialização e devem ser capazes de iniciar uma solicitação de revisão. O grupo de aprovadores receberá uma notificação e poderá aprovar ou rejeitar a solicitação. Quando a data ao vivo é atingida, o conteúdo é reproduzido nos dispositivos.

Por exemplo, se o autor quiser criar versões futuras de c1, c2 (canais), uma inicialização será criada e uma data ativa será definida (por exemplo, 10 de novembro de 8:00 AM). Quaisquer atualizações adicionais no conteúdo são enviadas para revisão.

Uma vez aprovada e na data de ativação (10 de novembro, 8:00 AM), essa inicialização reproduz o conteúdo nos dispositivos ou players.

## Requisitos {#requirements}

Antes de aproveitar o start *Screens Launch* em um projeto da AEM Screens, certifique-se de entender o conceito de Período de carência e sua relevância.

A execução de uma experiência na data de ativação definida no player envolve:

* promoção do lançamento (normalmente leva alguns segundos)

* publicar os recursos para publicar instâncias (normalmente leva alguns minutos, depende do tamanho dos canais ou ativos que precisam ser publicados)

* tempo gasto pela atualização do conteúdo offline para concluir (normalmente leva alguns minutos)

* tempo gasto pelos players para baixar o conteúdo da instância de publicação (normalmente leva minutos dependendo da largura de banda e do tamanho dos ativos que precisam ser baixados)

* diferenças de tempo entre o servidor e o player

### Compreensão do período de carência {#understanding-grace-period}

Para que o player possa start a reprodução do conteúdo na data de ativação definida, é necessário start as atividades anteriores antes da data de ativação.

Se a data ao vivo for *24 de novembro, 9:00 AM* e o período de carência for *24 horas*, a sequência de ações acima será start em (data ao vivo - período de carência), ou seja, 23 de novembro, 9:00 hora do servidor. Isso dá 24 horas de tempo para concluir todas as ações acima mencionadas e o conteúdo chegará aos players. Os players entenderão que este é um conteúdo de inicialização, portanto, o conteúdo não será reproduzido imediatamente, mas os players armazenarão esse conteúdo como uma versão futura e serão reproduzidos em start exatamente na data de ativação definida no fuso horário do player.

Por exemplo, digamos que o servidor esteja no PST e os dispositivos estejam no EST, a diferença de tempo máximo é de 3 horas nesse caso e suponha que a promoção levará 1 minuto e a publicação do autor para publicar leva 10 minutos e o player pode baixar os recursos normalmente em 10 a 15 minutos. Em seguida, período de carência = diferença de tempo (3 horas) + tempo para promover a inicialização (1 min) + tempo para publicar a inicialização (10 min) + tempo para baixar no player (10 a 15 min) + buffer (para ser seguro, digamos 30 min) = 3 horas 56 min = 14160 segundos.

Assim, sempre que agendarmos qualquer lançamento ao vivo, a promoção será start cedo por este deslocamento. Na equação acima, a maioria dos itens não leva muito tempo, podemos usar uma suposição decente para esse deslocamento assim que soubermos a diferença de tempo máxima entre o servidor e qualquer player.

>[!NOTE]
>
>O período de carência para Inicialização de telas é definido como 24 horas, o que significa que quando definimos a data de ativação para qualquer inicialização dos recursos em */content/screens*, a promoção será start com esse deslocamento.

### Atualizando período de carência {#updating-out-of-the-box-grace-period} predefinido

Esta seção explica como você pode atualizar um Período de carência predefinido para 10 minutos.

1. Navegue até CRXDE Lite e depois para `/libs/system/config.author/com.adobe.cq.wcm.launches.impl.LaunchesEventHandler.config`.
2. Clique com o botão direito do mouse e copie o arquivo.
3. Navegue até `/apps/system/config` e clique com o botão direito do mouse e cole.
4. Clique no duplo em `/apps/system/config/com.adobe.cq.wcm.launches.impl.LaunchesEventHandler.config` para abrir o arquivo no editor no CRXDE Lite. Ele deve mostrar o período de carência do caminho */content/screens/* como **86400**. Altere esse valor para **600**.

Agora, o conteúdo no arquivo de texto deve ser semelhante a:

```java
launches.eventhandler.launch.promotion.graceperiod=[ \
   "/content/screens(/.*):600", \
   ]
```

Como você definiu o Período de carência como 10 minutos no exemplo anterior, quando você define a data de ativação para qualquer inicialização dos recursos em */content/screens*, a promoção será start com esse deslocamento.

Por exemplo, se a data de ativação for definida como 24 de novembro, 9:00 da manhã e o período de carência for de 600 segundos, o trabalho promocional será start em 24 de novembro às 8:50 da manhã.

## Usando o Screens Launch {#using-launches}

Esta seção demonstra como implementar o Screens Launch no seu projeto da AEM Screens.

### Criando uma inicialização de telas {#creating-a-launch}

Siga as etapas abaixo para implementar a funcionalidade Screens Launch no seu projeto da AEM Screens:

1. Crie um canal de sequência em seu projeto AEM Screens, por exemplo **InicializaçõesDemo** —> **Canais** —> **FutureLaunch**, conforme mostrado abaixo.

   >[!CAUTION]
   >
   >Você deve criar uma inicialização a partir de um canal pré-existente no seu projeto AEM Screens.

   ![Imagem](/help/user-guide/assets/launches-images/launches-11.png)

1. Selecione o canal **FutureLaunch** e clique em **Criar lançamento** na barra de ações.

   ![Imagem](/help/user-guide/assets/launches-images/launches-12.png)

1. O assistente **Criar inicialização** é aberto. Você pode selecionar o canal que já está visível no assistente ou clicar em **+ Adicionar Canais** para adicionar o canal para o qual deseja criar a inicialização.

1. Clique em **Próximo** no assistente **Criar inicialização**. A opção **Incluir subpáginas** está selecionada por padrão.

   ![imagem](/help/user-guide/assets/launches-images/launches-d.png)

   >[!NOTE]
   >Você pode usar a opção **+ Adicionar Canais** para adicionar outro canal para o qual deseja criar a inicialização.

   Para usar a opção **Adicionar Canais**, navegue até o canal para o qual deseja criar a inicialização e clique em **Selecionar**.

   A opção **Select** será desativada se tentar selecionar vários canais ou uma pasta para adicionar a inicialização.

   ![imagem](/help/user-guide/assets/launches-images/launches-14.png)

   Depois de selecionar o(s) canal(s), clique em **Avançar**.


1. Insira **Título de lançamento** como **SummerPromotions** e não é necessário definir **Data de lançamento**, conforme mostrado na figura abaixo. Clique em **Criar**.

   >[!NOTE]
   >
   >*Habilitar ou* marcar a opção  **Herdar** dados ao vivo da página de origem permite que os canais sejam criados como cópias ao vivo na inicialização. Se qualquer alteração for feita no canal original, essas alterações serão automaticamente aplicadas aos canais de inicialização.
   >
   >
   >*Desabilitar ou* **desmarcarHerdar** dados ao vivo da página de origem permite que os canais sejam copiados sem nenhuma relação ao vivo na inicialização. Portanto, se forem feitas alterações no canal original, essas alterações não serão aplicadas aos canais de lançamento.

   ![Imagem](/help/user-guide/assets/launches-images/launches-c.png)

   >[!NOTE]
   >
   >É possível definir a data de ativação em tempo real nesta etapa ou configurá-la posteriormente ao editar as propriedades da inicialização depois que ela já tiver sido criada.

   **Entendendo o escopo de promoção do lançamento**

   * **Promover o lançamento** completo: Todos os canais do lançamento são promovidos na data de ativação definida.
   * **Promover páginas** modificadas: Só serão promovidos os recursos de lançamento modificados. É recomendável usar essa opção quando a revisão de inicialização não for necessária.
   * **Promover páginas** aprovadas: Essa opção requer que o fluxo de trabalho de aprovação de inicialização seja executado nos canais de inicialização. Somente as páginas aprovadas serão promovidas na data de ativação definida.

      >[!CAUTION]
      >
      >A data de lançamento respeita o fuso horário do player/dispositivo em vez do do servidor.

1. Você verá que sua inicialização foi criada. Você pode clicar em **Abrir** para visualização das páginas no editor ou clicar em **Concluído** para navegar de volta ao seu projeto.

   ![screen_shot_2019-06-25at20355pm](assets/screen_shot_2019-06-25at20355pm.png)

   Clicar em **Done** permite que você navegue de volta para o canal **FutureLaunch**.

   ![Imagem](/help/user-guide/assets/launches-images/launches-16.png)


### Editar as propriedades de inicialização para definir a data e o escopo ativos {#editing-the-launch-properties-to-set-the-live-date-and-scope}

Depois que a inicialização for criada, você poderá atualizar as propriedades, como data ativa, título de inicialização e escopo de promoção usando **Propriedades de inicialização**.

* **Data** de lançamento: refere-se à data de ativação, ou seja, a data ou a hora em que o conteúdo será reproduzido no player do Screens, de acordo com o fuso horário do player.
* **Production Ready (Pronto** para produção), permite que os canais sejam publicados após promovê-los; isso é ativado, portanto, não é necessário alterar isso.
* **Escopo**, decide quais canais serão promovidos durante a promoção do lançamento.


Siga as etapas abaixo para editar as propriedades de inicialização:

1. Navegue até o canal **FutureLaunch**, *(que é a inicialização pendente)* e selecione o canal, conforme mostrado na figura abaixo.

   ![imagem](/help/user-guide/assets/launches-images/launches-17.png)

1. Clique em **Painel** na barra de ações e você verá o painel **PENDING LAUNCHES** do painel do canal.

   ![imagem](/help/user-guide/assets/launches-images/launches-18.png)

1. Selecione a inicialização e clique em **Iniciar propriedades** no painel **INICIALIZAÇÕES PENDENTES**.

   ![imagem](/help/user-guide/assets/launches-images/launches-19.png)

### Editando a inicialização de telas para adicionar ou remover Canais {#editing-the-screens-launch-to-add-or-remove-channels}

Depois de criar a inicialização, você pode adicionar ou remover canais à inicialização existente usando a opção **Editar inicialização**.

Quando terminar, clique em **Salvar** para navegar de volta para o canal **FutureLaunch**.

### Promover a inicialização das telas manualmente{#promote-the-screens-launch-manually}

Você pode promover a inicialização manualmente usando a opção **Promover lançamento** do painel **PENDING LAUNCHES**.

Você pode escolher os recursos que deseja promover como parte dessa promoção manual no **Assistente de promoção de inicialização**.

![imagem](/help/user-guide/assets/launches-images/launches-e.png)

1. Você pode ativar ou desativar a opção para excluir a inicialização após a produção.
1. Você pode definir o **Escopo** da inicialização, com as seguintes opções:
   1. **Promover o lançamento** completo: Todos os canais do lançamento são promovidos na data de ativação definida.
   1. **Promover páginas** modificadas: Só serão promovidos os recursos de lançamento modificados. É recomendável usar essa opção quando a revisão de inicialização não for necessária.
   1. **Promover páginas** aprovadas: Essa opção requer que o fluxo de trabalho de aprovação de inicialização seja executado nos canais de inicialização. Somente as páginas aprovadas serão promovidas na data de ativação definida.
   1. **Promover a página** atual: Essa opção exige que o fluxo de trabalho de aprovação de inicialização seja executado somente para a página atual.
1. Clique em **Próximo** no assistente **Promover lançamento**.
1. Clique em **Promover** para promover a inicialização.

### Excluindo a inicialização de telas {#deleting-the-screens-launch}

Você pode excluir a inicialização usando a opção **Excluir inicialização** do painel **INICIALIZAÇÕES PENDENTES**.

>[!CAUTION]
>
>Essa ação também excluirá todos os descendentes (inicializações aninhadas).

