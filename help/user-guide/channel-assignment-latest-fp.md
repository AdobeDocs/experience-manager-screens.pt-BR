---
title: Atribuição de canais - FP mais recente
seo-title: Atribuição de canais - FP mais recente
description: Siga esta página para saber mais sobre Atribuição de Canais e Programação de anúncios.
translation-type: tm+mt
source-git-commit: 1c6a7342288a5d78dbea91d29ff8e5d6c8fec486
workflow-type: tm+mt
source-wordcount: '895'
ht-degree: 31%

---


# Atribuição de canal {#channel-assignment}

>[!IMPORTANT]
>Esta seção destaca a atribuição de Canais e o agendamento de canais para o AEM 6.5.5 Screens Feature Pack e posterior.

Depois de configurar uma exibição, é necessário atribuir um canal a uma exibição para visualização do conteúdo.

Esta página mostra como atribuir um canal à sua exibição.

>[!NOTE]
>É possível atribuir vários canais a uma exibição.


## Assigning a Channel {#assign-a-channel-new-release}

Siga as seções abaixo para criar um projeto AEM Screens e atribuir um canal a uma tela.

### Criação de um projeto e Canais da AEM Screens {#creating-project}

Siga as etapas abaixo para configurar um projeto e um canal:

1. Crie um projeto da AEM Screens intitulado como **DemoScreens**.

   ![imagem](/help/user-guide/assets/channel-assignment/channel-assign-fp1.png)

   >[!NOTE]
   >Consulte [Criação e gerenciamento de projetos](creating-a-screens-project.md) para saber como criar um projeto da AEM Screens.

1. Crie um canal de sequência chamado **Cafeteria** na pasta **Canais** .

1. Selecione o canal e clique em **Editar** na barra de ações para adicionar conteúdo ao seu canal.

   ![imagem](/help/user-guide/assets/channel-assignment/channel-assign-fp2.png)

   Por exemplo, o canal **Cafeteria** agora exibe as seguintes imagens:

   ![imagem](/help/user-guide/assets/channel-assignment/channel-assign-fp3.png)

1. Crie um local chamado **SanJose** e uma tela como **Sala de espera**.

   ![imagem](/help/user-guide/assets/channel-assignment/channel-assign-fp4.png)

### Atribuindo Canal a uma exibição {#assigning-channel-to-display}

Depois que a configuração do projeto for concluída, será necessário atribuir o canal a uma exibição para visualização do conteúdo.

1. Navegue até a exibição desejada, por exemplo, **DemoScreens** —> **Locais** —> **SanJose** —> **Sala de espera**.

1. Tap/click **Assign Channel** from the action bar.

   ![imagem](/help/user-guide/assets/channel-assignment/channel-assign-fp5.png)

   Ou,

   Toque/clique em **Painel** e clique em **+Atribuir Canal** no painel CANAIS **ATRIBUÍDOS e AGENDAMENTOS** .

   ![imagem](/help/user-guide/assets/channel-assignment/channel-assign-fp6.png)

1. The **Channel Assignment** dialog box opens.

   ![imagem](/help/user-guide/assets/channel-assignment/channel-assign-fp7.png)

1. Na opção **Configurações** , é possível escolher o canal por caminho ou por nome, inserir a função do canal, a prioridade, os eventos suportados e os métodos de interrupção. Além disso, é possível ativar a opção de dica de ferramenta de atração nessa caixa de diálogo.

   ![imagem](/help/user-guide/assets/channel-assignment/channel-assign-fp7.png)

   >[!NOTE]
   >Consulte a seção Propriedades [do](#channel-properties) Canal para saber mais sobre as propriedades do canal.

1. Na opção **Programações** , selecione o Fuso horário **de** referência, a Janela **de** Ativação e a Programação **de** recorrência.

1. Clique em **Salvar** depois de configurar suas preferências.

### Exibição do conteúdo no Chrome Player {#viewing-content-output}

### Como entender as propriedades do Canal da atribuição do Canal {#channel-properties}

### Fazer referência ao canal {#ref-channel}

A opção Fazer referência ao canal permite que você forneça uma referência ao canal desejado, seja por nome ou por caminho do canal.

* **por caminho**: você fornece uma referência explícita usando o caminho absoluto do canal.

* **pelo nome**: Insira o nome do canal que será resolvido para um canal real por contexto. Esse recurso permite que você crie a versão local de um canal para resolver dinamicamente o conteúdo específico da localização. For example, a channel with name *deals of the day*, where the actual content would be different in two cities, but you still have the sane channel role on all the displays.

### Função de canal {#role-channel}

A função de canal define o contexto da exibição. A função é o alvo de várias ações e não depende do canal real que a atende.

### Prioridade {#priority-channel}

A prioridade é usada para ordenar as atribuições, no caso de várias delas corresponderem aos critérios de reprodução. A atribuição com o valor mais alto sempre terá precedência sobre aquelas com valores mais baixos. Por exemplo, se houver dois canais, A e B, em que A tem uma prioridade de 1 e B tem uma prioridade de 2, o canal B será exibido, pois tem uma prioridade mais alta que A.

>[!NOTE]
>A prioridade de um canal é definida como um número (1 para o valor mínimo) na caixa de diálogo **Atribuição de canal**, conforme mencionado acima. Além disso, os canais atribuídos são classificados com base em uma prioridade decrescente.

### Eventos compatíveis {#supported-events-channel}

* **Carga inicial**: carrega o canal quando o player é iniciado. Esse evento pode ser atribuído a vários canais em combinação com o agendamento
* **Tela inativa**: carregado quando a tela está inativa. Esse evento pode ser atribuído a vários canais em combinação com o agendamento
* **Temporizador**: precisa ser definido quando um agendamento é fornecido
* **Interação do usuário**: o player mudará para o canal especificado se houver uma interação de usuário na tela (toque) em um canal inativo e será carregado quando a tela for tocada

### Método de interrupção {#interruption-method-channel}

>[!IMPORTANT]
>
> Esta opção só está disponível com AEM 6.4 Feature Pack 8 ou AEM 6.5 Feature Pack 4.

Como autor de conteúdo, você deve ser capaz de especificar quando um canal é interrompido para que possa optar por interromper o conteúdo não crítico, mas ter a opção de permitir que o conteúdo importante seja reproduzido totalmente antes de interromper a reprodução devido ao agendamento.

Selecione uma das seguintes opções disponíveis para definir o método de interrupção na caixa de diálogo Atribuição **de** Canais:

* **Imediatamente**: sempre que o agendamento é ativado ou uma atualização é recebida, você pode interromper a reprodução e atualizar ou reproduzir imediatamente o novo conteúdo
* **No final do ponto** atual: quando um novo agendamento é ativado ou uma atualização é recebida, você tem a opção de esperar que o item atual na sequência termine a reprodução e somente depois disso você atualiza ou reproduz o novo conteúdo
   >[!NOTE]
   >Esta opção está selecionada por padrão.
* **No final da sequência**: quando uma nova programação é ativada ou uma atualização é recebida, você tem a opção de esperar que a sequência inteira atinja sua extremidade, e logo antes da sequência desejada, você volta ao primeiro elemento, atualiza ou reproduz o novo conteúdo

   >[!NOTE]
   >Usar a segunda ou a terceira opção pode resultar em tempos de programação definidos na atribuição ligeiramente adiados, já que o player aguardará o fim do item ou da sequência (após o tempo especificado) antes de atualizar. O atraso dependerá da duração da reprodução do item.