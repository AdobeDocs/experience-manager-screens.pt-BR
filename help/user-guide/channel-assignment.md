---
title: Atribuição de canal
seo-title: Atribuição de canal
description: Siga esta página para saber mais sobre Atribuição de Canais e Programação de anúncios.
translation-type: tm+mt
source-git-commit: 963262bb4b7b26aa1e9fbf1be2362c7029818789
workflow-type: tm+mt
source-wordcount: '1218'
ht-degree: 45%

---


# Atribuição de canal {#channel-assignment}

>[!IMPORTANT]
>Esta seção destaca a atribuição de Canais e o agendamento de canais para Pacotes de recursos anteriores à versão AEM 6.5.5 Screens.

Depois de configurar uma exibição, é necessário atribuir um canal a uma exibição para visualização do conteúdo.

Esta página mostra como atribuir um canal à sua exibição.

>[!NOTE]
>É possível atribuir vários canais a uma exibição.

## Assigning a Channel {#assign-a-channel}

Siga as etapas abaixo para atribuir um canal a uma exibição:

1. Navegue até a exibição desejada, por exemplo, **DemoProject** —> **Locais** —> **SanJose** —> **StoreDisplay**.

   ![screen_shot_2018-08-23at25359pm](assets/screen_shot_2018-08-23at25359pm.png)

1. Tap/click **Assign Channel** in the action bar

   Ou,

   Tap/click **Dashboard** and click **+Assign Channel** from the **ASSIGNED CHANNNELS** panel to open the **Channel Assignment** dialog box.

   ![imagem](/help/user-guide/assets/channel-assign1.png)

   Você pode configurar as propriedades na caixa de diálogo Atribuição de **Canais** na seção abaixo. Consulte a seção Propriedades [do](#channel-properties) Canal para saber mais sobre as propriedades do canal.


## Como entender as propriedades do Canal da atribuição do Canal {#channel-properties}

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

### Agendamento {#schedule-channel}

o agendamento permite que você forneça uma descrição no texto informando quando o canal deve aparecer. Ele também permite definir uma data de início (**ativo desde**) e uma data de término (**ativo até**) para o canal a ser mostrado.

**Mostrar dica de ferramenta da atração**:

Mostrar dica de ferramenta da atração define se a dica de ferramenta de atração (“*Toque em qualquer lugar para começar*”) deve ser mostrada ou não enquanto o canal está em execução.

### Programação {#dayparting}

Schedules when combined with **Day-parting**, allows you to set a global schedule with multiple channels running at specific times of the day, and re-use that setup for all your displays at once.

A Segmentação de dia refere-se ao processo de dividir um dia em períodos de tempo e especificar qual conteúdo é reproduzido no horário desejado. A AEM Screens permite programar canais em termos de programação de anúncios em um dia, semana ou mês, de acordo com a necessidade.

Os exemplos a seguir explicam a programação em canais em três cenários diferentes:

#### Reprodução do conteúdo em um único dia, dividido em vários períodos de tempo {#playing-content-on-a-single-day-divided-into-multiple-time-slots}

Este exemplo mostra como um Restaurante usa a programação de um dia para mostrar seu menu de café da manhã, almoço e jantar.

Aqui, dividiremos cada dia em três períodos de tempo diferentes, para que o conteúdo do canal seja reproduzido de acordo com o horário do dia especificado:

| **Canal** | **Função** | **Prioridade** | **Agendamento** |
|---|---|---|---|
| Menu_A | Café da manhã |  | após 6:00 e antes de 11:00 |
| Menu_B | Almoço |  | após 11:00 e antes de 15:00 |
| Menu_C | Jantar |  | após 15:00 e antes de 20:00 |

#### Reprodução do conteúdo em um determinado dia da semana {#playing-content-on-a-particular-day-of-the-week}

Este exemplo mostra a segmentação de dia feita em um cassino que apresenta um evento ao vivo todos os finais de semana, das 20h às 22h, e disponibiliza opções especiais para o menu do jantar das 22h à 1h da manhã.

<table>
 <tbody>
  <tr>
   <td><strong>Canal</strong></td>
   <td><strong>Função</strong></td>
   <td><strong>Prioridade</strong></td>
   <td><strong>Agendamento</strong></td>
  </tr>
  <tr>
   <td>LiveConcert</td>
   <td>Final de semana</td>
   <td> </td>
   <td>21 de out de 2017 - 22 de outubro de 2017 <br /> depois das 20:00 antes das 22:00</td>
  </tr>
  <tr>
   <td>JantarEspeciais</td>
   <td>Final de semana</td>
   <td> </td>
   <td>21 de out de 2017 - 22 de outubro de 2017 <br /> depois das 22:00 antes das 13:00</td>
  </tr>
 </tbody>
</table>

#### Reprodução do conteúdo para um ou mais meses específicos {#playing-content-for-a-particular-month-months}

Este exemplo mostra a programação de uma loja que exibe sua coleção de verão dos meses de junho a agosto e a coleção de outono de setembro até o final de outubro.

Aqui, você criará anúncios por mês, para que o conteúdo do canal seja reproduzido conforme os meses especificados do ano.

| **Canal** | **Função** | **Prioridade** | **Agendamento** |
|---|---|---|---|
| SummerCollection | Verão |  | 01 de junho de 2017 - 31 de agosto de 2017 |
| FallCollection | Queda |  | 01 de set de 2017 - 30 de outubro de 2017 |

>[!NOTE]
>
>Além disso, você pode definir uma ***Prioridade*** para cada um dos canais. Por exemplo, se dois canais forem definidos para o mesmo dia e horário ou para o mesmo mês, o canal com prioridade mais alta será reproduzido primeiro. O valor mínimo para a prioridade pode ser definido como 0.

#### Reprodução do conteúdo para canais com a mesma prioridade {#playing-content-for-channels-with-same-priority}

Este exemplo mostra a programação para uma loja que exibe sua coleção de inverno com a mesma programação no mês de dezembro. Porém, como o Canal B tem a prioridade definida como 2, na semana em questão, ele reproduzirá seu conteúdo no lugar do Canal A.

| **Canal** | **Função** | **Prioridade** | **Agendamento** |
|---|---|---|---|
| A | inverno | 1 | 01 de dez de 2017 - 31 de dez de 2017 |
| B | Natal | 2 | 24 de dez de 2017 - 31 de dez de 2017 |


>[!NOTE]
>
> Para saber mais sobre a programação de anúncios, consulte as seções abaixo:
>
>* [Tratamento de recorrência em ativos](https://docs.adobe.com/content/help/en/experience-manager-screens/user-guide/authoring/product-features/asset-level-scheduling.html#handling-recurrence-in-assets)
>* [Tratamento da recorrência de ativos em um Canal](https://docs.adobe.com/content/help/en/experience-manager-screens/user-guide/authoring/product-features/channel-level-activation.html#handling-recurrence-in-assets)


