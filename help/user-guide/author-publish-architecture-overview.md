---
title: Visão geral da arquitetura de criação e publicação
description: A arquitetura do AEM Screens se assemelha à arquitetura AEM Sites tradicional. O conteúdo é criado em uma instância de autor do AEM e, em seguida, replicado para várias instâncias de publicação.
content-type: reference
topic-tags: administering
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
docset: aem65
feature: Administering Screens
role: Admin, Developer
level: Intermediate
exl-id: ba23eb8e-bbde-4a6e-8cfb-ae98176ed890
source-git-commit: dcaaa1c7ab0a55cecce70f593ed4fded8468130b
workflow-type: tm+mt
source-wordcount: '987'
ht-degree: 0%

---

# Visão geral da arquitetura de criação e publicação {#author-and-publish-architectural-overview}

Esta página destaca os seguintes tópicos:

* **Introdução aos Servidores de Publicação**
* **Visão geral da arquitetura**
* **Processo de registro**

## Pré-requisitos {#prerequisites}

Antes de começar com servidores de criação e servidores de publicação, você deve ter conhecimento prévio sobre:

* **Topologia do AEM**
* **Criando e gerenciando o projeto do AEM Screens**
* **Processo de registro do dispositivo**

>[!NOTE]
>
>Essa funcionalidade do AEM Screens só estará disponível se você tiver instalado o AEM 6.4 Screens Feature Pack 2. Para obter acesso a este Feature Pack, entre em contato com o Suporte da Adobe e solicite acesso. Depois de obter permissão, baixe-a em Compartilhamento de pacotes.

## Introdução {#introduction}

A arquitetura do AEM Screens se assemelha à arquitetura AEM Sites tradicional. O conteúdo é criado em uma instância de autor do AEM e, em seguida, replicado para várias instâncias de publicação. Os dispositivos no AEM Screens agora podem se conectar a um farm de publicação do AEM por meio de um balanceador de carga. Várias instâncias de publicação do AEM podem ser adicionadas para continuar a dimensionar o farm de publicação.

*Por exemplo*, um Autor de Conteúdo do AEM Screens emite um comando no sistema de criação para um dispositivo específico. Esse dispositivo está configurado para interagir com um farm de publicação. Ou interaja com um Autor de conteúdo do AEM Screens que obtém informações sobre dispositivos configurados para interagir com farms de publicação.

O diagrama a seguir ilustra o ambiente de criação e o ambiente de publicação.

![screen_shot_2019-03-04at30236pm](assets/screen_shot_2019-03-04at30236pm.png)

## Design de arquitetura {#architectural-design}

Há cinco componentes de arquitetura que facilitam essa solução:

* ***Replicando o conteúdo*** do autor para a publicação para exibição por dispositivos

* ***Reverter*** replicando conteúdo binário do ambiente de publicação (recebido de dispositivos) para o ambiente de criação.
* ***Enviando*** comandos do autor para publicar por meio de APIs REST específicas.
* ***Mensagens*** entre instâncias de publicação para sincronizar atualizações e comandos de informações do dispositivo.
* ***Sondagem*** feita pelo autor das instâncias de publicação para obter informações do dispositivo por meio de APIs REST específicas.

### Replicação (encaminhamento) de conteúdo e configurações {#replication-forward-of-content-and-configurations}

Os agentes de replicação padrão são usados para replicar o conteúdo do canal do AEM Screens, as configurações de local e as configurações de dispositivo. Essa funcionalidade permite que os autores atualizem o conteúdo de um canal e, opcionalmente, passem por algum tipo de fluxo de trabalho de aprovação antes de publicar atualizações de canal. Um agente de replicação deve ser criado para cada instância de publicação no farm de publicação.

O diagrama a seguir ilustra o processo de replicação:

![screen_shot_2019-03-04at33935pm](assets/screen_shot_2019-03-04at33935pm.png)

>[!NOTE]
>
>Um agente de replicação deve ser criado para cada instância de publicação no farm de publicação.

### Comandos e agentes de replicação do Screens {#screens-replication-agents-and-commands}

Agentes de replicação personalizados específicos do Screens são criados para enviar comandos da instância do autor para o dispositivo AEM Screens. As instâncias de publicação do AEM servem como um intermediário para encaminhar esses comandos para o dispositivo.

Esse fluxo de trabalho permite que os autores continuem a gerenciar o dispositivo, como o, enviem atualizações de dispositivo e tirem capturas de tela do ambiente do autor. Os agentes de replicação do AEM Screens têm uma configuração de transporte personalizada, como agentes de replicação padrão.

### Mensagens entre instâncias de publicação {#messaging-between-publish-instances}

Muitas vezes, um comando só deve ser enviado para um dispositivo uma única vez. No entanto, em uma arquitetura de publicação com balanceamento de carga, a instância de publicação à qual o dispositivo está se conectando é desconhecida.

Portanto, a instância do autor envia a mensagem para todas as instâncias de Publicação. No entanto, apenas uma única mensagem deve ser retransmitida para o dispositivo. Para garantir o envio correto de mensagens, a comunicação deve ocorrer entre as instâncias de publicação. Esta comunicação é obtida usando a *Artemis do Apache AtiveMQ*. Cada instância de publicação é colocada em uma Topologia acoplada livremente usando o serviço de descoberta do Sling com base em Oak. O AtiveMQ é configurado para que cada instância de publicação possa se comunicar e criar uma única fila de mensagens. O dispositivo AEM Screens pesquisa o farm de publicação do AEM por meio do balanceador de carga e seleciona o comando na parte superior da fila.

### Replicação reversa {#reverse-replication}

Geralmente, seguindo um comando, é esperado algum tipo de resposta do dispositivo Screens para ser encaminhado à instância do autor. Para obter esta AEM, é usada a ***Replicação reversa***.

* Crie um agente de replicação reversa para cada instância de publicação, semelhante aos agentes de replicação padrão e aos agentes de replicação do AEM Screens.
* Uma configuração de iniciador de fluxo de trabalho escuta os nós modificados na instância de publicação do AEM e, por sua vez, aciona um fluxo de trabalho para colocar a resposta do dispositivo na caixa de saída da instância de publicação do AEM.
* Uma replicação reversa nesse contexto é usada apenas para dados binários (como arquivos de log e capturas de tela) fornecidos pelos dispositivos. A pesquisa de dados não binários é recuperada.
* A pesquisa de replicação reversa da instância do autor do AEM recupera a resposta e a salva na instância do autor.

### Sondagem de instâncias de publicação {#polling-of-publish-instances}

As instâncias do autor devem ser capazes de sondar os dispositivos para obter um heartbeat e saber o status de integridade de um dispositivo conectado.

Os dispositivos executam ping no balanceador de carga e são roteados para uma instância de publicação. O status do dispositivo é exposto pela instância de publicação do AEM por meio de uma API de publicação fornecida em **api/screens-dcc/devices/static** para todos os dispositivos ativos e **api/screens-dcc/devices/&lt;device_id>/status.json** para um único dispositivo.

A instância do autor pesquisa todas as instâncias de publicação e mescla as respostas de status do dispositivo em um único status. O trabalho agendado que sonda o autor é `com.adobe.cq.screens.impl.jobs.DistributedDevicesStatiUpdateJob` e pode ser configurado com base em uma expressão CRON.

## Registro {#registration}

O registro continua a se originar na instância do autor do AEM. O dispositivo AEM Screens é apontado para a instância do autor e o registro é concluído.

Depois que um dispositivo é registrado no ambiente de criação do AEM, a configuração do dispositivo e as atribuições de canal/agendamento são replicadas para as instâncias de publicação do AEM. A configuração do dispositivo AEM Screens é atualizada para apontar para o balanceador de carga na frente do farm de publicação do AEM. Essa organização deve ser uma configuração única. Depois que o dispositivo Screens for conectado com êxito ao ambiente de publicação, ele poderá continuar a receber comandos originários do ambiente de criação. Não deve haver necessidade de conectar o dispositivo AEM Screens diretamente ao ambiente de criação do AEM.

![screen_shot_2019-02-25at15218pm](assets/screen_shot_2019-02-25at15218pm.png)

### Próximas etapas {#the-next-steps}

Quando você entender o design arquitetônico da configuração do autor e publicação no AEM Screens, consulte [Configurando autor e publicação para o AEM Screens](author-and-publish.md) para obter mais detalhes.
