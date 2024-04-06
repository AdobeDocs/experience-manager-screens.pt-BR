---
title: Atribuição de canal
seo-title: Channel Assignment
description: Siga esta página para saber mais sobre Atribuição de canal e Divisão de dia.
feature: Authoring Screens, Channel Assignment
role: Admin, Developer
level: Intermediate
exl-id: 6ed86bfc-38c7-4ced-b472-db2a362585c5
source-git-commit: 299018986ae58ecbdb51a30413222a9682fffc76
workflow-type: tm+mt
source-wordcount: '1233'
ht-degree: 3%

---

# Atribuição de canal {#channel-assignment}

>[!IMPORTANT]
>Esta seção destaca a atribuição de canais e a programação de canais para Pacotes de recursos anteriores à versão AEM 6.5.5 Screens.

Depois de configurar uma exibição, você deve atribuir um canal a uma exibição para visualizar seu conteúdo.

Esta página mostra como atribuir um canal à exibição.

>[!NOTE]
>É possível atribuir vários canais a uma exibição.

## Atribuição de um canal {#assign-a-channel}

Siga as etapas abaixo para atribuir um canal a uma exibição:

1. Navegue até a exibição necessária, por exemplo, **DemoProject** > **Localizações** > **San Jose** > **StoreDisplay**.

   ![imagem](assets/screen_shot_2018-08-23at25359pm.png)

1. Toque/clique **Atribuir canal** na barra de ações

   Ou,

   Toque/clique **Painel** e clique em **+Atribuir canal** do **CANAIS ATRIBUÍDOS** painel para abrir o **Atribuição de canal** caixa de diálogo.

   ![imagem](/help/user-guide/assets/channel-assign1.png)

   É possível configurar as propriedades na lista suspensa **Atribuição de canal** caixa de diálogo na seção abaixo. Consulte [Propriedades do canal](#channel-properties) para saber mais sobre as propriedades do canal.


## Noções básicas sobre as propriedades de canal na atribuição de canal {#channel-properties}

### Canal de referência {#ref-channel}

O canal de referência permite fornecer uma referência ao canal desejado, por nome de canal ou por caminho de canal.

* **por caminho**: você fornece uma referência explícita usando o caminho absoluto do canal.

* **por nome**: digite o nome do canal que será resolvido para um canal real por contexto. Esse recurso permite criar a versão local de um canal para resolver dinamicamente o conteúdo específico do local. Por exemplo, um canal com nome *ofertas do dia*, onde o conteúdo real seria diferente em duas cidades, mas você ainda tem a função de canal segura em todas as exibições.

### Função do canal {#role-channel}

A função do canal define o contexto da exibição. A função é direcionada por várias ações e é independente do canal real que desempenha a função.

### Prioridade {#priority-channel}

A prioridade é usada para ordenar as atribuições caso várias correspondam aos critérios de reprodução. Aquele com o valor mais alto sempre terá precedência sobre os valores mais baixos. Por exemplo, se houver dois canais A e B. A tem uma prioridade 1 e B tem uma prioridade 2, então o canal B é exibido, pois tem uma prioridade mais alta que A.

>[!NOTE]
>A prioridade de um canal é definida como um número (1 para o mínimo) na variável **Atribuição de canal** como mencionado acima. Além disso, os canais atribuídos são classificados com base na prioridade decrescente.

### Eventos suportados {#supported-events-channel}

* **Carga inicial**: carrega o canal quando o reprodutor é iniciado. Ele pode ser atribuído a vários canais em combinação com o agendamento
* **Tela inativa**: carrega quando a tela está ociosa. Ele pode ser atribuído a vários canais em combinação com o agendamento
* **Temporizador**: precisa ser definido quando uma agenda for fornecida
* **Interação do usuário**: o reprodutor alternará para o canal especificado, se houver uma interação do usuário na tela (toque) em um canal ocioso e será carregado quando a tela for tocada

### Método de interrupção {#interruption-method-channel}

>[!IMPORTANT]
>
> Essa opção só está disponível com o Feature Pack 8 para AEM 6.4 ou AEM 6.5 Feature Pack 4.

Como autor de conteúdo, você deve ser capaz de especificar quando um canal é interrompido para que possa optar por cortar conteúdo não crítico, mas ter a opção de permitir que o conteúdo importante seja totalmente reproduzido antes de interromper a reprodução por causa do agendamento.

Selecione uma das seguintes opções que estão disponíveis para definir o método de interrupção no **Atribuição de canal** caixa de diálogo:

* **Imediatamente**: sempre que a programação for ativada ou uma atualização for recebida, você poderá interromper a reprodução e atualizar ou reproduzir o novo conteúdo imediatamente
* **No fim do item atual**: quando um novo agendamento é ativado ou uma atualização é recebida, você tem a opção de esperar até que o item atual na sequência termine a reprodução e, somente depois disso, atualizar ou reproduzir o novo conteúdo
  >[!NOTE]
  >Essa opção é selecionada por padrão.
* **No final da sequência**: quando um novo agendamento é ativado ou uma atualização é recebida, você tem a opção de esperar até que toda a sequência atinja seu fim e, logo antes da sequência desejada, você volta para o primeiro elemento, atualiza ou reproduz o novo conteúdo

  >[!NOTE]
  >Usar a segunda ou terceira opção pode fazer com que os tempos de agendamento definidos na atribuição sejam ligeiramente adiados, pois o reprodutor aguardará o final do item ou da sequência (após o tempo especificado) antes de atualizar. O atraso dependerá da duração da reprodução do item.

### Programação {#schedule-channel}

O agendamento permite fornecer uma descrição em texto quando o canal deve ser exibido. Também permite definir uma data de início (**ativo desde**) e uma data final (**ativo até**) para que o canal seja exibido.

**Mostrar dica de ferramenta da atração**:

Mostrar dica de ferramenta da atração define se a dica de ferramenta da atração (&quot;*Toque em qualquer lugar para começar*&quot;) deve ser exibido ou não enquanto o canal estiver em execução.

### DayParting {#dayparting}

Agendamentos quando combinados com **DayParting**, permite definir um agendamento global com vários canais sendo executados em horários específicos do dia e reutilizar essa configuração para todas as exibições de uma só vez.

DayParting refere-se à divisão de um dia em intervalos de tempo e especificação de qual conteúdo é reproduzido no horário desejado. O AEM Screens permite agendar canais em termos de divisão de dia em um dia, semana ou mês, de acordo com a necessidade.

Os exemplos a seguir explicam a divisão de dia em canais em três cenários diferentes:

#### Reprodução de conteúdo em um único dia dividido em vários intervalos de tempo {#playing-content-on-a-single-day-divided-into-multiple-time-slots}

Este exemplo mostra como um restaurante usa a faixa horária para exibir seu menu de café da manhã, almoço e jantar.

Aqui, dividiremos cada dia em três períodos diferentes, para que o conteúdo do canal seja reproduzido de acordo com o horário especificado do dia:

| **Canal** | **Função** | **Prioridade** | **Agendar** |
|---|---|---|---|
| Menu_A | Café da manhã |  | após 6:00 e antes de 11:00 |
| Menu_B | Almoço |  | após 11:00 e antes de 15:00 |
| Menu_C | Jantar |  | após 15:00 e antes de 20:00 |

#### Reproduzir conteúdo em um dia da semana específico {#playing-content-on-a-particular-day-of-the-week}

Este exemplo mostra o dayParting realizado em um cassino onde o evento ao vivo ocorre todos os finais de semana das 20h às 22h e os especiais estão disponíveis para o menu de jantar após as 22h até às 13h

<table>
 <tbody>
  <tr>
   <td><strong>Canal</strong></td>
   <td><strong>Função</strong></td>
   <td><strong>Prioridade</strong></td>
   <td><strong>Programação</strong></td>
  </tr>
  <tr>
   <td>LiveConcert</td>
   <td>Fim de semana</td>
   <td> </td>
   <td>21 de outubro de 2017 - 22 de outubro de 2017 <br /> depois das 20:00 antes das 22:00</td>
  </tr>
  <tr>
   <td>JantarEspeciais</td>
   <td>Fim de semana</td>
   <td> </td>
   <td>21 de outubro de 2017 - 22 de outubro de 2017 <br /> depois das 22:00 antes da 1:00</td>
  </tr>
 </tbody>
</table>

#### Reproduzindo conteúdo por um mês/meses específicos {#playing-content-for-a-particular-month-months}

Este exemplo mostra o DayParting para uma loja que exibe sua coleção de verão dos meses de junho a agosto e a coleção do outono de setembro até o final de outubro.

Aqui, você criará a divisão de dia por meses, para que o conteúdo do canal seja reproduzido de acordo com os meses do ano especificados.

| **Canal** | **Função** | **Prioridade** | **Agendar** |
|---|---|---|---|
| ColeçãoDeVerão | Verão |  | 1 de junho de 2017 - 31 de agosto de 2017 |
| FallCollection | Outono |  | 1 de setembro de 2017 - 30 de outubro de 2017 |

>[!NOTE]
>
>Além disso, você pode definir ***Prioridade*** para cada um dos canais. Por exemplo, se dois canais forem definidos para o mesmo dia e hora ou para o mesmo mês, o canal com prioridade mais alta será reproduzido primeiro. O valor mínimo de prioridade pode ser definido como 0.

#### Reprodução de conteúdo para canais com a mesma prioridade {#playing-content-for-channels-with-same-priority}

Este exemplo mostra o DayParting de uma loja que exibe sua coleção de inverno com o mesmo agendamento no mês de dezembro. Mas como o Canal B tem prioridade definida como 2, durante essa semana; o canal B reproduz seu conteúdo em vez do Canal A.

| **Canal** | **Função** | **Prioridade** | **Agendar** |
|---|---|---|---|
| A | Inverno | 1 | 1 de dezembro de 2017 - 31 de dezembro de 2017 |
| B | Natal | 2 | 24 de dezembro de 2017 - 31 de dezembro de 2017 |


>[!NOTE]
>
> Para saber mais sobre DayParting, consulte as seções abaixo:
>
>* [Lidar com a recorrência em ativos](https://docs.adobe.com/content/help/en/experience-manager-screens/user-guide/authoring/product-features/asset-level-scheduling.html#handling-recurrence-in-assets)
>* [Lidar com a recorrência de ativos em um canal](https://docs.adobe.com/content/help/en/experience-manager-screens/user-guide/authoring/product-features/channel-level-activation.html#handling-recurrence-in-assets)
