---
title: Atribuição de canal
description: Saiba mais sobre Atribuição de canal e faixa horária.
feature: Authoring Screens, Channel Assignment
role: Admin, Developer
level: Intermediate
exl-id: 6ed86bfc-38c7-4ced-b472-db2a362585c5
source-git-commit: b65e59473e175e7c1b31fba900bb7e47eff3a263
workflow-type: tm+mt
source-wordcount: '1174'
ht-degree: 2%

---

# Atribuição de canal {#channel-assignment}

>[!IMPORTANT]
>Esta seção destaca a atribuição de canais e a programação de canais para Pacotes de recursos anteriores à versão AEM 6.5.5 Screens.

Ao configurar uma exibição, atribua um canal a uma exibição para visualizar seu conteúdo.

Esta página mostra como atribuir um canal à exibição.

>[!NOTE]
>É possível atribuir vários canais a uma exibição.

## Atribuição de um canal {#assign-a-channel}

Siga as etapas abaixo para atribuir um canal a uma exibição:

1. Navegue até a exibição necessária, por exemplo, **DemoProject** > **Localizações** > **San Jose** > **StoreDisplay**.

   ![imagem](assets/screen_shot_2018-08-23at25359pm.png)

1. Selecionar **Atribuir canal** na barra de ações.

   ou,

   Selecionar **Painel** e selecione **+Atribuir canal** do **CANAIS ATRIBUÍDOS** para que você possa abrir o **Atribuição de canal** caixa de diálogo.

   ![imagem](/help/user-guide/assets/channel-assign1.png)

   É possível configurar as propriedades na lista suspensa **Atribuição de canal** caixa de diálogo na seção abaixo. Consulte [Propriedades do canal](#channel-properties) para obter mais informações sobre as propriedades do canal.

## Noções básicas sobre as propriedades de canal na atribuição de canal {#channel-properties}

### Canal de referência {#ref-channel}

O canal de referência permite fornecer uma referência ao canal desejado, por nome de canal ou por caminho de canal.

* **por caminho** - Você fornece uma referência explícita usando o caminho absoluto do canal.

* **por nome** - Insira o nome do canal que é resolvido para um canal real por contexto. Esse recurso permite criar uma versão local de um canal para resolver dinamicamente o conteúdo específico do local. Por exemplo, um canal com nome *ofertas do dia*, onde o conteúdo real seria diferente em duas cidades, mas você ainda tem a função de canal segura em todas as exibições.

### Função do canal {#role-channel}

A função do canal define o contexto da exibição. A função é direcionada por várias ações e é independente do canal real que desempenha a função.

### Prioridade {#priority-channel}

A prioridade é usada para ordenar as atribuições caso várias correspondam aos critérios de reprodução. Aquele com o valor mais alto sempre tem prioridade sobre valores mais baixos. Por exemplo, se houver dois canais A e B. A tem uma prioridade 1 e B tem uma prioridade 2, então o canal B é exibido, pois tem uma prioridade mais alta que A.

>[!NOTE]
>A prioridade de um canal é definida como um número (1 para o mínimo) na variável **Atribuição de canal** como mencionado acima. Além disso, os canais atribuídos são classificados com base na prioridade decrescente.

### Eventos suportados {#supported-events-channel}

* **Carga inicial** - Carrega o canal quando o reprodutor é iniciado. Ele pode ser atribuído a vários canais com um agendamento.
* **Tela inativa** - Carrega quando a tela está ociosa. Ele pode ser atribuído a vários canais com um agendamento.
* **Temporizador** - Deve ser definido quando um agendamento é fornecido.
* **Interação do usuário** - O reprodutor alterna para o canal especificado se houver uma interação do usuário na tela (toque) em um canal ocioso e é carregado quando a tela é tocada.

### Método de interrupção {#interruption-method-channel}

>[!IMPORTANT]
>
> Essa opção só está disponível com <!--AEM 6.4 Feature Pack 8 or -->Pacote de recursos 4 do AEM 6.5.

Como autor de conteúdo, especifique quando um canal é interrompido para que você possa optar por cortar conteúdo não crítico, mas, opcionalmente, permitir que conteúdo importante seja reproduzido antes de interromper sua reprodução por causa do agendamento.

Selecione uma das seguintes opções que estão disponíveis para definir o método de interrupção no **Atribuição de canal** caixa de diálogo:

* **Imediatamente** - Sempre que a programação for ativada ou uma atualização for recebida, você pode interromper a reprodução e atualizar ou reproduzir imediatamente o novo conteúdo.
* **No fim do item atual** - Quando uma nova programação é ativada ou uma atualização é recebida, você pode aguardar até que o item atual na sequência termine a reprodução. Somente depois disso é possível atualizar ou reproduzir o novo conteúdo.

  >[!NOTE]
  >Essa opção é selecionada por padrão.
* **No final da sequência** - Quando um novo agendamento é ativado ou uma atualização é recebida, você pode aguardar até que toda a sequência chegue ao fim. Em seguida, logo antes da sequência desejada, você pode voltar para o primeiro elemento, atualizar ou reproduzir o novo conteúdo.

  >[!NOTE]
  >O uso da segunda ou da terceira opção pode fazer com que os horários de programação definidos na atribuição sejam ligeiramente adiados. O motivo é que o reprodutor aguarda o final do item ou da sequência (após o tempo especificado) antes de atualizar. O atraso depende da duração da reprodução do item.

### Programação {#schedule-channel}

Schedule permite fornecer uma descrição em texto quando o canal deve ser exibido. Também permite definir uma data de início (**ativo desde**) e uma data final (**ativo até**) para que o canal seja exibido.

**Mostrar dica de ferramenta da atração**

Mostrar dica de ferramenta da atração define se a dica de ferramenta da atração (&quot;*Toque em qualquer lugar para começar*&quot;) deve ser exibido ou não enquanto o canal estiver em execução.

### DayParting {#dayparting}

Agendamentos quando combinados com **DayParting**, permite definir um agendamento global com vários canais sendo executados em horários específicos do dia e reutilizar essa configuração para todas as exibições de uma só vez.

DayParting refere-se à divisão de um dia em intervalos de tempo e especificação de qual conteúdo é reproduzido no horário desejado. O AEM Screens permite agendar canais em termos de Divisão de dia em um dia, semana ou mês, de acordo com o requisito.

Os exemplos a seguir explicam a divisão de dia em canais em três cenários diferentes:

#### Reprodução de conteúdo em um único dia dividido em vários intervalos de tempo {#playing-content-on-a-single-day-divided-into-multiple-time-slots}

Este exemplo mostra como um restaurante usa o DayParting para exibir seu café da manhã, almoço e menu de jantar.

Aqui, você divide cada dia em três intervalos de tempo diferentes para que o conteúdo do canal seja reproduzido de acordo com o horário especificado do dia:

| **Canal** | **Função** | **Prioridade** | **Agendar** |
|---|---|---|---|
| Menu_A | Café da manhã |  | Depois das 6:00 e antes das 11:00 |
| Menu_B | Almoço |  | Depois das 11:00 e antes das 15:00 |
| Menu_C | Jantar |  | Depois das 15:00 e antes das 20:00 |

#### Reproduzir conteúdo em um dia da semana específico {#playing-content-on-a-particular-day-of-the-week}

Este exemplo mostra o dayParting realizado em um cassino onde o evento ao vivo ocorre todos os finais de semana das 20:00 às 22:00 e os especiais estão disponíveis para o menu de jantar após as 22:00 até às 13:00.

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

Aqui, você cria DayParting por mês, para que o conteúdo do canal seja reproduzido de acordo com os meses do ano especificados.

| **Canal** | **Função** | **Prioridade** | **Agendar** |
|---|---|---|---|
| ColeçãoDeVerão | Verão |  | 1 de junho de 2017 - 31 de agosto de 2017 |
| FallCollection | Outono |  | 1 de setembro de 2017 - 30 de outubro de 2017 |

>[!NOTE]
>
>Além disso, é possível definir ***Prioridade*** para cada um dos canais. Por exemplo, se dois canais forem definidos para o mesmo dia e hora ou para o mesmo mês, o canal com prioridade mais alta será reproduzido primeiro. O valor mínimo de prioridade pode ser definido como 0.

#### Reprodução de conteúdo para canais com a mesma prioridade {#playing-content-for-channels-with-same-priority}

Este exemplo mostra o DayParting para uma loja que exibe sua coleção de inverno com o mesmo agendamento no mês de dezembro. Mas como o Canal B tem prioridade definida como 2, durante essa semana; o canal B reproduz seu conteúdo em vez do Canal A.

| **Canal** | **Função** | **Prioridade** | **Agendar** |
|---|---|---|---|
| A | Inverno | 1 | 1 de dezembro de 2017 - 31 de dezembro de 2017 |
| B | Natal | 2 | 24 de dezembro de 2017 - 31 de dezembro de 2017 |


>[!NOTE]
>
> Para saber mais sobre DayParting, consulte as seções abaixo:
>
>* [Lidar com a recorrência em ativos](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/authoring/product-features/asset-level-scheduling)
>* [Lidar com a recorrência de ativos em um canal](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/authoring/product-features/channel-level-activation)
