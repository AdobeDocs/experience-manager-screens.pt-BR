---
title: Visão geral da arquitetura de criação e publicação
seo-title: Author and Publish Architectural Overview
description: A arquitetura do AEM Screens se assemelha a uma arquitetura AEM Sites tradicional. O conteúdo é criado em uma instância de autor do AEM e, em seguida, replicado para várias instâncias de publicação. Siga esta página para saber mais sobre a visão geral da arquitetura de criação e publicação.
seo-description: AEM Screens architecture resembles a traditional AEM Sites architecture. Content is authored on an AEM author instance and then forward-replicated to multiple publish instances. Follow this page to learn more on author and publish architectural overview.
uuid: 19bac3de-8938-4339-82f0-6ccb932b6684
content-type: reference
topic-tags: administering
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
discoiquuid: 112404de-5a5a-4b37-b87c-d02029933c8a
docset: aem65
feature: Administering Screens
role: Admin, Developer
level: Intermediate
exl-id: ba23eb8e-bbde-4a6e-8cfb-ae98176ed890
source-git-commit: 299018986ae58ecbdb51a30413222a9682fffc76
workflow-type: tm+mt
source-wordcount: '983'
ht-degree: 0%

---

# Visão geral da arquitetura de criação e publicação {#author-and-publish-architectural-overview}

Esta página destaca os seguintes tópicos:

* **Introdução aos servidores de publicação**
* **Visão geral da arquitetura**
* **Processo de registro**

## Pré-requisitos {#prerequisites}

Antes de começar a usar os servidores de criação e publicação, você deve ter conhecimento prévio sobre:

* **Topologia do AEM**
* **Criação e gerenciamento de projetos do AEM Screens**
* **Processo de registro do dispositivo**

>[!NOTE]
>
>Essa funcionalidade do AEM Screens só estará disponível se você tiver instalado o AEM 6.4 Screens Feature Pack 2. Para obter acesso a este Feature Pack, entre em contato com o Suporte do Adobe e solicite acesso. Depois de ter permissões, você pode baixá-las do Compartilhamento de pacotes.

## Introdução {#introduction}

A arquitetura do AEM Screens se assemelha a uma arquitetura AEM Sites tradicional. O conteúdo é criado em uma instância de autor do AEM e, em seguida, replicado para várias instâncias de publicação. Os dispositivos AEM Screens agora podem se conectar a um farm de publicação AEM por meio do balanceador de carga. Várias instâncias de publicação do AEM podem ser adicionadas para continuar a dimensionar o farm de publicação.

*Por exemplo*, um autor de conteúdo do AEM Screens emite um comando no sistema de criação para um dispositivo específico configurado para interagir com um farm de publicação ou um autor de conteúdo do AEM Screens que obtém informações sobre dispositivos configurados para interagir com farms de publicação.

O diagrama a seguir ilustra os ambientes do autor e de publicação.

![screen_shot_2019-03-04at30236pm](assets/screen_shot_2019-03-04at30236pm.png)

## Design de arquitetura {#architectural-design}

Há cinco componentes de arquitetura que facilitam essa solução:

* ***Replicação de conteúdo*** do autor para publicar para exibição por dispositivos

* ***Reverter*** replicação de conteúdo binário de publicação (recebido de dispositivos) para autor
* ***Enviando*** comandos do autor para publicar por meio de REST APIs específicas
* ***Mensagens*** entre instâncias de publicação para sincronizar atualizações e comandos de informações do dispositivo
* ***Sondagem*** pelo autor de instâncias de publicação para obter informações do dispositivo por meio de APIs REST específicas

### Replicação (encaminhamento) de conteúdo e configurações  {#replication-forward-of-content-and-configurations}

Os agentes de replicação padrão são usados para replicar o conteúdo do canal de telas, as configurações de local e as configurações de dispositivo. Isso permite que os autores atualizem o conteúdo de um canal e, opcionalmente, passem por algum tipo de fluxo de trabalho de aprovação antes de publicar atualizações de canal. Um agente de replicação precisa ser criado para cada instância de publicação no farm de publicação.

O diagrama a seguir ilustra o processo de replicação:

![screen_shot_2019-03-04at33935pm](assets/screen_shot_2019-03-04at33935pm.png)

>[!NOTE]
>
>Um agente de replicação precisa ser criado para cada instância de publicação no farm de publicação.

### Agentes e comandos de replicação do Screens  {#screens-replication-agents-and-commands}

Agentes de replicação específicos do Telas personalizadas são criados para enviar comandos da instância do Autor para o dispositivo AEM Screens. As instâncias de publicação do AEM servem como um intermediário para encaminhar esses comandos para o dispositivo.

Isso permite que os autores continuem a gerenciar o dispositivo, como o, enviem atualizações de dispositivo e tirem capturas de tela do ambiente de criação. Os agentes de replicação do AEM Screens têm uma configuração de transporte personalizada, como agentes de replicação padrão.

### Mensagens entre instâncias de publicação  {#messaging-between-publish-instances}

Em muitos casos, um comando só deve ser enviado para um dispositivo uma única vez. No entanto, em uma arquitetura de publicação com balanceamento de carga, não se sabe a qual instância de publicação o dispositivo está se conectando.

Portanto, a instância do autor envia a mensagem para todas as instâncias de Publicação. No entanto, apenas uma única mensagem deve ser retransmitida para o dispositivo. Para garantir o envio correto de mensagens, alguma comunicação deve ocorrer entre as instâncias de publicação. Isso é feito usando *Artemis do Apache AtiveMQ*. Cada instância de publicação é colocada em uma Topologia acoplada livremente usando o serviço de descoberta do Sling com base no Oak e o AtiveMQ é configurado para que cada instância de publicação possa se comunicar e criar uma única fila de mensagens. O dispositivo do Screens pesquisa o farm de publicação por meio do balanceador de carga e seleciona o comando na parte superior da fila.

### Replicação reversa {#reverse-replication}

Em muitos casos, após um comando, é esperado algum tipo de resposta do dispositivo do Screens para ser encaminhado para a instância do Autor. Para alcançar esse AEM ***Replicação reversa*** é usada.

* Crie um agente de replicação reversa para cada instância de publicação, semelhante aos agentes de replicação padrão e aos agentes de replicação de telas.
* Uma configuração de iniciador de fluxo de trabalho escuta os nós modificados na instância de publicação e, por sua vez, aciona um fluxo de trabalho para colocar a resposta do dispositivo na caixa de saída da instância de publicação.
* Uma replicação reversa nesse contexto é usada apenas para dados binários (como arquivos de log e capturas de tela) fornecidos pelos dispositivos. Os dados não binários são recuperados por sondagem.
* A replicação inversa sondada da instância do autor AEM recupera a resposta e a salva na instância do autor.

### Sondagem de instâncias de publicação  {#polling-of-publish-instances}

A instância do autor precisa sondar os dispositivos para obter um heartbeat e saber o status de integridade de um dispositivo conectado.

Os dispositivos executam ping no balanceador de carga e são roteados para uma instância de publicação. O status do dispositivo é exposto pela instância de publicação por meio de uma API de publicação fornecida @ **api/screens-dcc/devices/static** para todos os dispositivos ativos e **api/screens-dcc/devices/&lt;device_id>/status.json** para um único dispositivo.

A instância do autor pesquisa todas as instâncias de publicação e mescla as respostas de status do dispositivo em um único status. O trabalho agendado que pesquisa o autor é `com.adobe.cq.screens.impl.jobs.DistributedDevicesStatiUpdateJob` e podem ser configuradas com base em uma expressão cron.

## Registro {#registration}

O registro continua a se originar na instância de autor do AEM. O dispositivo AEM Screens é apontado para a instância do autor e o registro é concluído.

Depois que um dispositivo é registrado no ambiente de criação, a configuração do dispositivo e as atribuições de canal/agendamento são replicadas nas instâncias de publicação do AEM. A configuração do dispositivo AEM Screens é atualizada para apontar para o Balanceador de carga na frente do farm de publicação AEM. Essa é uma configuração única. Depois que o dispositivo do Screens é conectado com êxito ao ambiente de publicação, ele pode continuar a receber comandos originários do ambiente de criação e não deve haver necessidade de conectar o dispositivo do Screens diretamente ao ambiente de criação.

![screen_shot_2019-02-25at15218pm](assets/screen_shot_2019-02-25at15218pm.png)

### Próximas etapas {#the-next-steps}

Assim que você entender o design arquitetônico da configuração do autor e publicação no AEM Screens, consulte [Configuração do Author e Publish para o AEM Screens](author-and-publish.md) para obter mais detalhes.
