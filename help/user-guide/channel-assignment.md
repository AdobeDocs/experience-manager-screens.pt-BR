---
title: Atribuição de canal
description: Saiba mais sobre Atribuição de canal e faixa horária.
feature: Authoring Screens, Channel Assignment
role: Admin, Developer
level: Intermediate
exl-id: 6ed86bfc-38c7-4ced-b472-db2a362585c5
source-git-commit: dcaaa1c7ab0a55cecce70f593ed4fded8468130b
workflow-type: tm+mt
source-wordcount: '1180'
ht-degree: 2%

---

# Atribuição de canal {#channel-assignment}

>[!IMPORTANT]
>Esta seção destaca a Atribuição de canal e a programação de canais para pacotes de recursos anteriores à versão AEM 6.5.5 Screens.

Ao configurar uma exibição, atribua um canal a uma exibição para visualizar seu conteúdo.

Esta página mostra como atribuir um canal à exibição.

>[!NOTE]
>É possível atribuir vários canais a uma exibição.

## Atribuição de um canal {#assign-a-channel}

Siga as etapas abaixo para atribuir um canal a uma exibição:

1. Navegue até a exibição necessária, por exemplo, **DemoProject** > **Locations** > **SanJose** > **StoreDisplay**.

   ![imagem](assets/screen_shot_2018-08-23at25359pm.png)

1. Clique em **Atribuir canal** na barra de ações.

   ou,

   Clique em **Painel** e em **+Atribuir Canal** no painel **CANAIS ATRIBUÍDOS** para que você possa abrir a caixa de diálogo **Atribuição de Canal**.

   ![imagem](/help/user-guide/assets/channel-assign1.png)

   Você pode configurar as propriedades da caixa de diálogo **Atribuição de canal** na seção abaixo. Consulte a seção [Propriedades do canal](#channel-properties) para obter mais informações sobre as propriedades do canal.

## Noções básicas sobre as propriedades de canal na atribuição de canal {#channel-properties}

### Canal de referência {#ref-channel}

Um canal de referência permite fornecer uma referência ao canal desejado, por nome de canal ou por caminho de canal.

* **por caminho** - Você fornece uma referência explícita usando o caminho absoluto do canal.

* **por nome** - Você insere o nome do canal que é resolvido para um canal real por contexto. Esse recurso permite criar uma versão local de um canal para que você possa resolver dinamicamente o conteúdo específico do local. Por exemplo, um canal com o nome *ofertas do dia*, em que o conteúdo real seria diferente em duas cidades, mas você ainda tem a função de canal seguro em todas as exibições.

### Função do canal {#role-channel}

A função do canal define o contexto da exibição. A função é direcionada a várias ações e é independente do canal real que cumpre a função.

### Prioridade {#priority-channel}

A prioridade é usada para ordenar as atribuições caso várias correspondam aos critérios de reprodução. Aquele com o valor mais alto sempre tem prioridade sobre valores mais baixos. Por exemplo, se houver dois canais A e B. A tem uma prioridade 1 e B tem uma prioridade 2, então o canal B é exibido, pois tem uma prioridade mais alta que A.

>[!NOTE]
>A prioridade de um canal é definida como um número (1 para o mínimo) na caixa de diálogo **Atribuição de canal**, conforme mencionado acima. Além disso, os canais atribuídos são classificados com base na prioridade decrescente.

### Eventos suportados {#supported-events-channel}

* **Carregamento inicial** - carrega o canal quando o reprodutor é iniciado. Ele pode ser atribuído a vários canais com um agendamento.
* **Tela Inativa** - Carrega quando a tela está inativa. Ele pode ser atribuído a vários canais com um agendamento.
* **Timer** - Deve ser definido quando um agendamento é fornecido.
* **Interação do usuário** - O reprodutor alterna para o canal especificado se houver uma interação do usuário na tela (toque) em um canal ocioso e é carregado quando a tela é tocada.

### Método de interrupção {#interruption-method-channel}

>[!IMPORTANT]
>
> Esta opção só está disponível com o <!--AEM 6.4 Feature Pack 8 or -->Pacote de Recursos 4 do AEM 6.5.

Como um Autor de conteúdo, especifique quando um canal é interrompido. Isso permite cortar conteúdo não crítico se desejado, mas, opcionalmente, permitir a reprodução de conteúdo importante antes de interromper a reprodução por causa do agendamento.

Clique em uma das opções disponíveis a seguir para definir o método de interrupção na caixa de diálogo **Atribuição de canal**:

* **Imediatamente** - Sempre que o agendamento for ativado ou uma atualização for recebida, você pode interromper a reprodução e atualizar ou reproduzir o novo conteúdo imediatamente.
* **No final do item atual** - Quando um novo agendamento é ativado ou uma atualização é recebida, você pode aguardar o término da reprodução do item atual na sequência. Somente depois disso é possível atualizar ou reproduzir o novo conteúdo.

  >[!NOTE]
  >Essa opção é selecionada por padrão.
* **No final da sequência** - Quando um novo agendamento é ativado ou uma atualização é recebida, você pode aguardar até que toda a sequência atinja seu final. Em seguida, logo antes da sequência desejada, você pode voltar para o primeiro elemento, atualizar ou reproduzir o novo conteúdo.

  >[!NOTE]
  >O uso da segunda ou da terceira opção pode fazer com que os horários de programação definidos na atribuição sejam ligeiramente adiados. O motivo é que o reprodutor aguarda o final do item ou da sequência (após o tempo especificado) antes de atualizar. O atraso depende da duração da reprodução do item.

### Programação {#schedule-channel}

Schedule permite fornecer uma descrição em texto quando o canal deve ser exibido. Também permite definir uma data de início (**ativo desde**) e uma data de término (**ativo até**) para o canal a ser exibido.

**Mostrar dica de ferramenta da atração**

Mostrar dica de ferramenta de atração define se a dica de ferramenta de atração (&quot;*Toque em qualquer lugar para começar*&quot;) deve ser exibida ou não enquanto o canal está em execução.

### DayParting {#dayparting}

O agendamento, quando combinado com **DayParting**, permite que você defina um agendamento global com vários canais em execução em horários específicos do dia e reutilize essa configuração para todas as suas exibições de uma só vez.

DayParting é conhecido como dividir um dia em intervalos de tempo e especificar qual conteúdo é reproduzido na hora desejada. O AEM Screens permite agendar canais em termos de Divisão de dia em um dia, semana ou mês, de acordo com o requisito.

Os exemplos a seguir explicam a divisão de dia em canais em três cenários diferentes:

#### Reprodução de conteúdo em um único dia dividido em vários intervalos de tempo {#playing-content-on-a-single-day-divided-into-multiple-time-slots}

Este exemplo mostra como um restaurante usa o DayParting para exibir seu café da manhã, almoço e menu de jantar.

Aqui, você divide cada dia em três intervalos de tempo diferentes para que o conteúdo do canal seja reproduzido de acordo com o horário especificado do dia:

| **Canal** | **Função** | **Prioridade** | **Agenda** |
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
   <td>21 de outubro de 2017 - 22 de outubro de 2017 <br /> depois das 22:00 antes das 1:00</td>
  </tr>
 </tbody>
</table>

#### Reproduzindo conteúdo por um mês/meses específicos {#playing-content-for-a-particular-month-months}

Este exemplo mostra o DayParting para uma loja que exibe sua coleção de verão dos meses de junho a agosto e a coleção do outono de setembro até o final de outubro.

Aqui, você cria DayParting por mês, para que o conteúdo do canal seja reproduzido de acordo com os meses do ano especificados.

| **Canal** | **Função** | **Prioridade** | **Agenda** |
|---|---|---|---|
| ColeçãoDeVerão | Verão |  | 1 de junho de 2017 - 31 de agosto de 2017 |
| FallCollection | Outono |  | 1 de setembro de 2017 - 30 de outubro de 2017 |

>[!NOTE]
>
>Além disso, você pode definir a ***Prioridade*** para cada um dos canais. Por exemplo, se dois canais forem definidos para o mesmo dia e hora ou para o mesmo mês, o canal com prioridade mais alta será reproduzido primeiro. O valor mínimo de prioridade pode ser definido como 0.

#### Reprodução de conteúdo para canais com a mesma prioridade {#playing-content-for-channels-with-same-priority}

Este exemplo mostra o DayParting para uma loja que exibe sua coleção de inverno com o mesmo agendamento no mês de dezembro. Mas como o canal B tem a prioridade definida como 2, durante essa semana; o canal B reproduz o conteúdo em vez do canal A.

| **Canal** | **Função** | **Prioridade** | **Agenda** |
|---|---|---|---|
| A | Inverno | 1 | 1 de dezembro de 2017 - 31 de dezembro de 2017 |
| B | Natal | 2 | 24 de dezembro de 2017 - 31 de dezembro de 2017 |


>[!NOTE]
>
> Para saber mais sobre DayParting, consulte as seções abaixo:
>
>* [Manipulando recorrência no Assets](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/authoring/product-features/asset-level-scheduling)
>* [Manipulando a recorrência da Assets em um canal](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/authoring/product-features/channel-level-activation)
