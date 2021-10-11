---
title: Atualização de conteúdo usando o Screens Launch
seo-title: Content Update using Screens Launch
description: Os autores de conteúdo podem criar versões futuras do(s) canal(s), conhecido como Launch , e outras configurações de data de ativação para esse lançamento permitirão que o conteúdo seja ativado em dispositivos ou players.
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

Os autores de conteúdo podem criar versões futuras do(s) canal(s), conhecido como **Screens Launch**, e definir ainda mais a data de ativação para esta inicialização. Isso permite que o conteúdo seja exibido em dispositivos ou reprodutores na data de ativação especificada.

Com a ajuda do ***Screens Launch***, os autores podem visualizar cada canal na inicialização e devem ser capazes de iniciar uma solicitação para revisão. O grupo de aprovadores receberá uma notificação e poderá aprovar ou rejeitar a solicitação. Quando a data de ativação é atingida, o conteúdo é reproduzido nos dispositivos.

Por exemplo, se o autor quiser criar versões futuras de c1, c2 (canais), uma inicialização será criada e uma data em tempo real será definida (por exemplo, 10 de novembro, às 8:00). Quaisquer atualizações adicionais no conteúdo são enviadas para revisão.

Uma vez aprovado e na data de ativação (10 de novembro, 8:00 AM), esse lançamento reproduzirá o conteúdo nos dispositivos ou reprodutores.

## Requisitos {#requirements}

Antes de começar a aproveitar o *Screens Launch* em um projeto do AEM Screens, compreenda o conceito do período de carência e sua relevância.

A execução de uma experiência na data de ativação definida no reprodutor envolve:

* promoção do lançamento (normalmente leva alguns segundos)

* publicar os recursos para publicar instâncias (normalmente leva alguns minutos, depende do tamanho dos canais ou ativos que precisam ser publicados)

* tempo gasto pela atualização do conteúdo offline para concluir (normalmente leva alguns minutos)

* tempo gasto pelos players para baixar o conteúdo da instância de publicação (normalmente leva minutos dependendo da largura de banda e do tamanho dos ativos que precisam ser baixados)

* qualquer diferença de tempo do servidor e do reprodutor

### Compreensão do período de carência {#understanding-grace-period}

Para que o reprodutor possa iniciar a reprodução do conteúdo na data de ativação definida, é necessário iniciar as atividades anteriores antes da data de ativação.

Se a data de ativação for *24 de novembro, 9:00 AM* e o período de carência for *24 horas*, a sequência de ações acima será iniciada em (data de ativação - período de carência), ou seja, 23 de novembro, 9:00 AM no horário do servidor. Isso dá 24 horas para concluir todas as ações mencionadas acima e o conteúdo chegará aos players. Os players compreenderão que esse é um conteúdo de lançamento, portanto, o conteúdo não será reproduzido imediatamente, mas os players armazenarão esse conteúdo como uma versão futura e começarão a reproduzir exatamente na data de ativação definida no fuso horário do reprodutor.

Por exemplo, digamos que o servidor esteja no PST e os dispositivos estejam no EST, a diferença de tempo máximo é de 3 horas nesse caso e suponha que a promoção levará 1 min e a publicação do autor para a publicação leva 10 min e o reprodutor pode baixar os recursos normalmente em 10 a 15 min. Em seguida, período de carência = diferença de tempo (3 horas) + tempo para promover a inicialização (1 min) + tempo para publicar a inicialização (10 min) + tempo para download no player (10-15 min) + buffer (para ser seguro, digamos 30 min) = 3 horas 56 min = 14160 segundos.

Assim, sempre que agendarmos qualquer lançamento ao vivo, a promoção começará cedo por esse deslocamento. Na equação acima, a maioria dos itens não leva muito tempo, podemos usar uma suposição decente para esse deslocamento assim que soubermos a diferença máxima de tempo entre o servidor e qualquer reprodutor.

>[!NOTE]
>
>Pronto para uso, o período de carência do Screens Launch é definido como 24 horas, o que significa que, quando definirmos a data de ativação para qualquer lançamento dos recursos em */content/screens*, a promoção começará com esse deslocamento.

### Atualização do período de carência pronto para uso {#updating-out-of-the-box-grace-period}

Esta seção explica como atualizar um período de carência pronto para uso para 10 minutos.

1. Navegue até CRXDE Lite e então até `/libs/system/config.author/com.adobe.cq.wcm.launches.impl.LaunchesEventHandler.config`.
2. Clique com o botão direito do mouse e copie o arquivo.
3. Navegue até `/apps/system/config` e clique com o botão direito do mouse e cole.
4. Clique duas vezes em `/apps/system/config/com.adobe.cq.wcm.launches.impl.LaunchesEventHandler.config` para abrir o arquivo no editor no CRXDE Lite. Ele deve mostrar o período de carência do caminho */content/screens/* como **86400**. Altere esse valor para **600**.

Agora, o conteúdo no arquivo de texto deve ser semelhante a:

```java
launches.eventhandler.launch.promotion.graceperiod=[ \
   "/content/screens(/.*):600", \
   ]
```

Como você definiu o Período de carência como 10 minutos no exemplo anterior, ao definir a data de ativação para qualquer lançamento dos recursos em */content/screens*, a promoção começará com esse deslocamento.

Por exemplo, se a data de ativação for definida como 24 de novembro, 9:00 AM e o período de carência for de 600 segundos, o trabalho de promoção será iniciado em 24 de novembro às 8:50 AM.

## Uso do Screens Launch {#using-launches}

Esta seção demonstra como implementar o Screens Launch no seu projeto do AEM Screens.

### Criação de uma inicialização do Screens {#creating-a-launch}

Siga as etapas abaixo para implementar a funcionalidade do Screens Launch no seu projeto do AEM Screens:

1. Crie um canal de sequência em seu projeto AEM Screens, por exemplo **LaunchesDemo** —> **Channels** —> **FutureLaunch**, conforme mostrado abaixo.

   >[!CAUTION]
   >
   >Você deve criar um lançamento a partir de um canal pré-existente no seu projeto do AEM Screens.

   ![Imagem](/help/user-guide/assets/launches-images/launches-11.png)

1. Selecione o canal **FutureLaunch** e clique em **Create Launch** na barra de ações.

   ![Imagem](/help/user-guide/assets/launches-images/launches-12.png)

1. O assistente **Criar lançamento** é aberto. Você pode selecionar o canal que já está visível no assistente ou clicar em **+ Adicionar Canais** para adicionar o canal para o qual deseja criar o lançamento.

1. Clique em **Próximo** no assistente **Criar lançamento**. A opção **Include subpages** é selecionada por padrão.

   ![imagem](/help/user-guide/assets/launches-images/launches-d.png)

   >[!NOTE]
   >Você pode usar a opção **+ Adicionar Canais** para adicionar outro canal para o qual deseja criar a inicialização.

   Para usar a opção **Adicionar Canais**, navegue até o canal para o qual deseja criar a inicialização e clique em **Selecionar**.

   A opção **Selecionar** será desativada se tentar selecionar vários canais ou uma pasta para adicionar a inicialização.

   ![imagem](/help/user-guide/assets/launches-images/launches-14.png)

   Depois de selecionar o canal/canais, clique em **Next**.


1. Insira o **Título do lançamento** como **SummerPromotions** e não é necessário definir a **Data do lançamento**, conforme mostrado na figura abaixo. Clique em **Criar**.

   >[!NOTE]
   >
   >*Habilitar ou* marcar a opção  **Herdar dados ativos da página de origem** permite que os canais sejam criados como cópias em tempo real no lançamento. Se alguma alteração for feita no canal original, essas alterações serão automaticamente aplicadas aos canais de inicialização.
   >
   >
   >*Desativar ou* **desmarcarHerdar** dados online de página de origem permite que os canais sejam copiados sem qualquer relação dinâmica na inicialização. Portanto, se alguma alteração for feita no canal original, essas alterações não serão aplicadas aos canais de lançamento.

   ![Imagem](/help/user-guide/assets/launches-images/launches-c.png)

   >[!NOTE]
   >
   >É possível definir a data de lançamento ao vivo nesta etapa ou configurá-la posteriormente durante a edição das propriedades do lançamento, uma vez que já tenha sido criada.

   **Noções básicas sobre o escopo de promoção do Launch**

   * **Promover lançamento** completo: Todos os canais do lançamento são promovidos na data de ativação definida.
   * **Promover páginas** modificadas: Somente os recursos de lançamento modificados serão promovidos. É recomendável usar essa opção quando a revisão de inicialização não for necessária.
   * **Promover páginas** aprovadas: Essa opção requer que o workflow de aprovação de lançamento seja executado nos canais de lançamento. Somente as páginas aprovadas serão promovidas na data de ativação definida.

      >[!CAUTION]
      >
      >A data de ativação respeita o fuso horário do reprodutor/dispositivo, em vez do do servidor.

1. Você verá que seu lançamento foi criado. Você pode clicar em **Abrir** para exibir as páginas no editor ou clicar em **Concluído** para retornar ao seu projeto.

   ![screen_shot_2019-06-25at20355pm](assets/screen_shot_2019-06-25at20355pm.png)

   Clicar em **Concluído** permite navegar de volta para o canal **FutureLaunch**.

   ![Imagem](/help/user-guide/assets/launches-images/launches-16.png)


### Editar as propriedades do Launch para definir a data e o escopo em tempo real {#editing-the-launch-properties-to-set-the-live-date-and-scope}

Após a criação da inicialização, é possível atualizar as propriedades, como a data de ativação, o título da inicialização e o escopo da promoção usando **Propriedades do Launch**.

* **Data de lançamento**: refere-se à data de ativação, ou seja, a data ou a hora em que o conteúdo será reproduzido no player do Screens, de acordo com o fuso horário do player.
* **Pronto para produção**, permite que os canais sejam publicados depois de promovê-los, isso está ativado e pronto para uso, portanto não é necessário alterar.
* **Escopo**, decide quais canais serão promovidos durante a promoção do lançamento.


Siga as etapas abaixo para editar as propriedades do launch:

1. Navegue até o canal **FutureLaunch**, *(que é o lançamento pendente)* e selecione o canal, conforme mostrado na figura abaixo.

   ![imagem](/help/user-guide/assets/launches-images/launches-17.png)

1. Clique em **Dashboard** na barra de ações e visualize o painel **PENDENTE LAUNCHES** no painel de canais.

   ![imagem](/help/user-guide/assets/launches-images/launches-18.png)

1. Selecione a inicialização e clique em **Iniciar propriedades** no painel **PENDENTE LAUNCHES**.

   ![imagem](/help/user-guide/assets/launches-images/launches-19.png)

### Editar a inicialização do Screens para adicionar ou remover canais  {#editing-the-screens-launch-to-add-or-remove-channels}

Depois de criar o lançamento, você pode adicionar ou remover canais ao lançamento existente usando a opção **Editar lançamento**.

Quando terminar, clique em **Save** para navegar de volta para o canal **FutureLaunch**.

### Promoção do lançamento do Screens manualmente{#promote-the-screens-launch-manually}

É possível promover a inicialização manualmente usando a opção **Promover lançamento** do painel **PENDENTE LAUNCHES**.

Você pode escolher os recursos que deseja promover como parte dessa promoção manual no **Assistente de promoção do lançamento**.

![imagem](/help/user-guide/assets/launches-images/launches-e.png)

1. Você pode ativar ou desativar a opção para excluir a inicialização após a produção.
1. Você pode definir o **Scope** do lançamento, com as seguintes opções:
   1. **Promover lançamento** completo: Todos os canais do lançamento são promovidos na data de ativação definida.
   1. **Promover páginas** modificadas: Somente os recursos de lançamento modificados serão promovidos. É recomendável usar essa opção quando a revisão de inicialização não for necessária.
   1. **Promover páginas** aprovadas: Essa opção requer que o workflow de aprovação de lançamento seja executado nos canais de lançamento. Somente as páginas aprovadas serão promovidas na data de ativação definida.
   1. **Divulgar a página** atual: Essa opção requer que o workflow de aprovação de lançamento seja executado somente para a página atual.
1. Clique em **Next** no assistente **Promover lançamento**.
1. Clique em **Promover** para promover o lançamento.

### Exclusão do Screens Launch {#deleting-the-screens-launch}

É possível excluir a inicialização usando a opção **Delete Launch** do painel **PENDING LAUNCHES**.

>[!CAUTION]
>
>Esta ação também excluirá todos os descendentes (inicializações aninhadas).
