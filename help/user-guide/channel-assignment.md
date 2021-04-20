---
title: Atribuição de canal
seo-title: Atribuição de canal
description: Siga esta página para saber mais sobre Atribuição de canal e Divisão de dia.
feature: Authoring Screens, Channel Assignment
role: Administrator, Developer
level: Intermediate
translation-type: tm+mt
source-git-commit: 89c70e64ce1409888800af7c7edfbf92ab4b2c68
workflow-type: tm+mt
source-wordcount: '1222'
ht-degree: 42%

---


# Atribuição de canal {#channel-assignment}

>[!IMPORTANT]
>Esta seção destaca a Atribuição de canal e o agendamento de canais para Pacotes de recursos anteriores AEM versão 6.5.5 do Screens.

Depois de configurar uma exibição, é necessário atribuir um canal a uma exibição para visualizar o conteúdo.

Esta página mostra como atribuir um canal à exibição.

>[!NOTE]
>Você pode atribuir vários canais a uma exibição.

## Atribuindo um Canal {#assign-a-channel}

Siga as etapas abaixo para atribuir um canal a uma exibição:

1. Navegue até a exibição necessária, por exemplo, **DemoProject** —> **Localizações** —> **SanJose** —> **StoreDisplay**.

   ![imagem](assets/screen_shot_2018-08-23at25359pm.png)

1. Toque/clique em **Atribuir canal** na barra de ações

   Ou,

   Toque/clique em **Painel** e clique em **+Atribuir canal** no painel **CANAIS ATRIBUÍDOS** para abrir a caixa de diálogo **Atribuição de canal**.

   ![imagem](/help/user-guide/assets/channel-assign1.png)

   Você pode configurar as propriedades da caixa de diálogo **Atribuição de canal** na seção abaixo. Consulte a seção [Propriedades do canal](#channel-properties) para saber mais sobre as propriedades do canal.


## Como entender as propriedades do canal na atribuição de canal {#channel-properties}

### Fazer referência ao canal {#ref-channel}

A opção Fazer referência ao canal permite que você forneça uma referência ao canal desejado, seja por nome ou por caminho do canal.

* **por caminho**: você fornece uma referência explícita usando o caminho absoluto do canal.

* **por nome**: Você insere o nome do canal que será resolvido para um canal real por contexto. Esse recurso permite que você crie a versão local de um canal para resolver dinamicamente o conteúdo específico da localização. Por exemplo, um canal com o nome *ofertas do dia*, em que o conteúdo real seria diferente em duas cidades, mas você ainda tem a mesma função de canal em todas as exibições.

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
> Essa opção só está disponível com o AEM 6.4 Feature Pack 8 ou AEM 6.5 Feature Pack 4.

Como autor de conteúdo, você deve ser capaz de especificar quando um canal é interrompido, para que possa optar por cortar conteúdo não crítico, mas ter a opção de permitir que o conteúdo importante seja totalmente reproduzido antes de interromper a reprodução devido ao agendamento.

Selecione uma das seguintes opções disponíveis para definir o método de interrupção na caixa de diálogo **Atribuição de canal**:

* **Imediatamente**: sempre que o cronograma é ativado ou uma atualização é recebida, você pode interromper a reprodução e atualizar imediatamente ou reproduzir o novo conteúdo
* **No final do item** atual: quando uma nova programação é ativada ou uma atualização é recebida, você tem a opção de aguardar a conclusão da reprodução do item atual na sequência e somente depois disso você atualiza ou reproduz o novo conteúdo
   >[!NOTE]
   >Esta opção está selecionada por padrão.
* **No final da sequência**: quando uma nova programação é ativada ou uma atualização é recebida, você tem a opção de esperar que toda a sequência atinja seu fim e, logo antes da sequência desejada, você faz o loop de volta para o primeiro elemento, atualiza ou reproduz o novo conteúdo

   >[!NOTE]
   >O uso da segunda ou terceira opção pode resultar no agendamento de tempos definido na atribuição a serem ligeiramente adiados, pois o reprodutor aguardará o fim do item ou da sequência (após o tempo especificado) antes de atualizar. O atraso dependerá da duração da reprodução do item.

### Programação {#schedule-channel}

o agendamento permite que você forneça uma descrição no texto informando quando o canal deve aparecer. Ele também permite definir uma data de início (**ativo desde**) e uma data de término (**ativo até**) para o canal a ser mostrado.

**Mostrar dica de ferramenta da atração**:

Mostrar dica de ferramenta da atração define se a dica de ferramenta de atração (“*Toque em qualquer lugar para começar*”) deve ser mostrada ou não enquanto o canal está em execução.

### DayParting {#dayparting}

Agendamentos, quando combinados com **DayParting**, permitem definir um agendamento global com vários canais em execução em horários específicos do dia e reutilizar essa configuração para todas as exibições ao mesmo tempo.

A Segmentação de dia refere-se ao processo de dividir um dia em períodos de tempo e especificar qual conteúdo é reproduzido no horário desejado. O AEM Screens permite agendar canais em termos de divisão de dia em um dia, semana ou mês, de acordo com a necessidade.

Os exemplos a seguir explicam a divisão de dias em canais em três cenários diferentes:

#### Reprodução do conteúdo em um único dia, dividido em vários períodos de tempo {#playing-content-on-a-single-day-divided-into-multiple-time-slots}

Este exemplo mostra como um restaurante usa a segmentação de dia para mostrar seu menu de café da manhã, almoço e jantar.

Aqui, dividiremos cada dia em três períodos de tempo diferentes, para que o conteúdo do canal seja reproduzido de acordo com o horário do dia especificado:

| **Canal** | **Função** | **Prioridade** | **Programação** |
|---|---|---|---|
| Menu_A | Café da manhã |  | após 6:00 e antes de 11:00 |
| Menu_B | Almoço |  | após 11:00 e antes de 15:00 |
| Menu_C | Jantar |  | após 15:00 e antes de 20:00 |

#### Reprodução do conteúdo em um determinado dia da semana {#playing-content-on-a-particular-day-of-the-week}

Este exemplo mostra o dayParting alcançado em um casino onde o evento ao vivo ocorre todos os finais de semana, das 20h às 22h, e os especiais estão disponíveis para o menu do jantar depois das 22h até às 13h.

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
   <td>21 de outubro de 2017 - 22 de outubro de 2017 <br /> depois de 22:00 antes de 1:00</td>
  </tr>
 </tbody>
</table>

#### Reprodução do conteúdo para um ou mais meses específicos {#playing-content-for-a-particular-month-months}

Este exemplo mostra o DayParting para uma loja que exibe sua coleção de verão de junho a agosto e a coleção de outono de setembro até o final de outubro.

Aqui, você criará a segmentação de dia por mês, para que o conteúdo do canal seja reproduzido de acordo com os meses especificados do ano.

| **Canal** | **Função** | **Prioridade** | **Programação** |
|---|---|---|---|
| SummerCollection | Verão |  | 01 de junho de 2017 - 31 de agosto de 2017 |
| FallCollection | Queda |  | 01 de setembro de 2017 - 30 de outubro de 2017 |

>[!NOTE]
>
>Além disso, você pode definir uma ***Prioridade*** para cada um dos canais. Por exemplo, se dois canais forem definidos para o mesmo dia e horário ou para o mesmo mês, o canal com prioridade mais alta será reproduzido primeiro. O valor mínimo para a prioridade pode ser definido como 0.

#### Reprodução do conteúdo para canais com a mesma prioridade {#playing-content-for-channels-with-same-priority}

Este exemplo mostra o DayParting para uma loja que exibe sua coleção de inverno com o mesmo agendamento no mês de dezembro. Porém, como o Canal B tem a prioridade definida como 2, na semana em questão, ele reproduzirá seu conteúdo no lugar do Canal A.

| **Canal** | **Função** | **Prioridade** | **Programação** |
|---|---|---|---|
| A | Inverno | 1 | 01 de dezembro de 2017 - 31 de dezembro de 2017 |
| B | Natal | 2 | 24 de dezembro de 2017 - 31 de dezembro de 2017 |


>[!NOTE]
>
> Para saber mais sobre DayParting, consulte as seções abaixo:
>
>* [Lidar com a recorrência em ativos](https://docs.adobe.com/content/help/en/experience-manager-screens/user-guide/authoring/product-features/asset-level-scheduling.html#handling-recurrence-in-assets)
>* [Lidar com a recorrência de ativos em um canal](https://docs.adobe.com/content/help/en/experience-manager-screens/user-guide/authoring/product-features/channel-level-activation.html#handling-recurrence-in-assets)


