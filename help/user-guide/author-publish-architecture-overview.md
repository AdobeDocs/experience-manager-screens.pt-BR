---
title: Visão geral da arquitetura de autor e publicação
seo-title: Visão geral da arquitetura de autor e publicação
description: A arquitetura AEM Screens se parece com uma arquitetura AEM Sites tradicional. O conteúdo é criado em uma instância do autor AEM e, em seguida, replicado para várias instâncias de publicação. Siga esta página para saber mais sobre a visão geral da arquitetura do autor e da publicação.
seo-description: A arquitetura AEM Screens se parece com uma arquitetura AEM Sites tradicional. O conteúdo é criado em uma instância do autor AEM e, em seguida, replicado para várias instâncias de publicação. Siga esta página para saber mais sobre a visão geral da arquitetura do autor e da publicação.
uuid: 19bac3de-8938-4339-82f0-6ccb932b6684
content-type: reference
topic-tags: administering
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
discoiquuid: 112404de-5a5a-4b37-b87c-d02029933c8a
docset: aem65
translation-type: tm+mt
source-git-commit: 2a3bbdd283f983cbdb5f21b606f508603385e041
workflow-type: tm+mt
source-wordcount: '1026'
ht-degree: 3%

---


# Visão geral da arquitetura de autor e publicação {#author-and-publish-architectural-overview}

Esta página destaca os seguintes tópicos:

* **Introdução aos servidores de publicação**
* **Visão geral da arquitetura**
* **Processo de registro**

## Pré-requisitos {#prerequisites}

Antes de começar a usar os servidores de autor e publicação, você deve ter conhecimento prévio de:

* **Topologia AEM**
* **Criação e gerenciamento do AEM Screens Project**
* **Processo de registro do dispositivo**

>[!NOTE]
>
>Esta funcionalidade do AEM Screens só estará disponível se você tiver instalado AEM 6.4 Screens Pack 2. Para obter acesso a esse Feature Pack, você deve entrar em contato com o Suporte da Adobe e solicitar acesso. Com as devidas permissões, você pode baixá-lo em Compartilhamento de pacotes.

## Introdução {#introduction}

A arquitetura AEM Screens se parece com uma arquitetura AEM Sites tradicional. O conteúdo é criado em uma instância do autor AEM e, em seguida, replicado para várias instâncias de publicação. Dispositivos AEM Screens agora podem se conectar a um farm de publicação AEM por meio do balanceador de carga. Várias instâncias de publicação de AEM podem ser adicionadas para continuar a dimensionar o farm de publicação.

*Por exemplo*, um autor de conteúdo da AEM Screens emite um comando no sistema de criação para um dispositivo específico configurado para interagir com um farm de publicação ou um autor de conteúdo da AEM Screens que obtém informações sobre dispositivos configurados para interagir com farm de publicação.

O diagrama a seguir ilustra os ambientes de autor e publicação.

![screen_shot_2019-03-04at30236pm](assets/screen_shot_2019-03-04at30236pm.png)

## Design arquitetônico {#architectural-design}

Há cinco componentes arquitetônicos, facilitando esta solução:

* ***Replicação de*** conteúdo do autor para publicação para exibição por dispositivos

* ***Reverserduplicação de conteúdo binário de publicação (recebido de dispositivos) para autor*** 
* ****** Envio de comandos do autor para publicação por meio de REST APIs específicas
* ****** Mensagens entre instâncias de publicação para sincronizar atualizações e comandos de informações do dispositivo
* ***Pesquisar*** pelo autor das instâncias de publicação para obter informações do dispositivo por meio de REST APIs específicas

### Replicação (Encaminhamento) de Conteúdo e Configurações {#replication-forward-of-content-and-configurations}

Os agentes de replicação padrão são usados para replicar telas o conteúdo do canal, as configurações de localização e as configurações do dispositivo. Isso permite que os autores atualizem o conteúdo de um canal e, opcionalmente, passem por algum tipo de fluxo de trabalho de aprovação antes de publicarem atualizações de canais. É necessário criar um agente de replicação para cada instância de publicação no farm de publicação.

O diagrama a seguir ilustra o processo de replicação:

![screen_shot_2019-03-04at33935pm](assets/screen_shot_2019-03-04at33935pm.png)

>[!NOTE]
>
>É necessário criar um agente de replicação para cada instância de publicação no farm de publicação.

### Screens Replication Agents and Commands {#screens-replication-agents-and-commands}

Os agentes de replicação específicos do Screens personalizados são criados para enviar comandos da instância Autor para o dispositivo AEM Screens. As instâncias de publicação de AEM servem como intermediário para encaminhar esses comandos para o dispositivo.

Isso permite que os autores continuem a gerenciar o dispositivo, como enviar atualizações do dispositivo e tirar capturas de tela do ambiente do autor. Os agentes de replicação AEM Screens têm uma configuração de transporte personalizada, como agentes de replicação padrão.

### Mensagens entre instâncias de publicação {#messaging-between-publish-instances}

Em muitos casos, um comando deve ser enviado apenas para um dispositivo uma única vez. No entanto, em uma arquitetura de publicação com balanceamento de carga, não se sabe a qual instância de publicação o dispositivo está se conectando.

Portanto, a instância do autor envia a mensagem para todas as instâncias de Publicação. No entanto, somente uma única mensagem deve ser retransmitida ao dispositivo. Para garantir mensagens corretas, é necessário fazer alguma comunicação entre as instâncias de publicação. Isso é obtido usando *Apache AtiveMQ Artemis*. Cada instância de publicação é colocada em uma Topologia amplamente acoplada usando o serviço de descoberta Sling baseado em Oak e o AtiveMQ é configurado para que cada instância de publicação possa se comunicar e criar uma única fila de mensagens. O dispositivo Screens pesquisa o farm de publicação por meio do balanceador de carga e seleciona o comando na parte superior da fila.

### Replicação reversa {#reverse-replication}

Em muitos casos, após um comando, espera-se que algum tipo de resposta do dispositivo Screens seja encaminhada para a instância Autor. Para alcançar esse AEM, ***Replicação reversa*** é usada.

* Crie um agente de replicação reversa para cada instância de publicação, como os agentes de replicação padrão e os agentes de replicação de telas.
* Uma configuração de inicializador de fluxo de trabalho escuta os nós modificados na instância de publicação e, por sua vez, aciona um fluxo de trabalho para colocar a resposta do Dispositivo na caixa de saída da instância de Publicação.
* Uma replicação reversa neste contexto é usada apenas para dados binários (como arquivos de registro e capturas de tela) fornecidos pelos dispositivos. Os dados não binários são recuperados por pesquisa.
* A replicação reversa pesquisada da instância do autor AEM recupera a resposta e a salva na instância do autor.

### Pesquisa de instâncias de publicação {#polling-of-publish-instances}

A instância do autor precisa ser capaz de sondar os dispositivos para obter uma pulsação e saber o status de funcionamento de um dispositivo conectado.

Os dispositivos tocando no balanceador de carga e são roteados para uma instância de publicação. O status do dispositivo é então exposto pela instância de publicação por meio de uma API de publicação fornecida em **api/screens-dcc/devices/static** para todos os dispositivos ativos e **api/screens-dcc/devices/&lt;device_id>/status.json** para um único dispositivo.

A instância do autor pesquisa todas as instâncias de publicação e mescla as respostas de status do dispositivo em um único status. O trabalho agendado que chama o autor é `com.adobe.cq.screens.impl.jobs.DistributedDevicesStatiUpdateJob` e pode ser configurado com base em uma expressão cron.

## Registro {#registration}

O registro continua a ser originário da instância do autor AEM. O dispositivo AEM Screens é apontado para a instância do autor e o registro é concluído.

Depois que um dispositivo é registrado no ambiente do autor, a configuração do dispositivo e as atribuições de canal/agendamento são replicadas para as instâncias de publicação AEM. A configuração do dispositivo AEM Screens é atualizada para apontar para o Balanceador de carga na frente do farm de publicação AEM. Essa configuração deve ser única, uma vez que o Dispositivo de telas é conectado com êxito ao ambiente de publicação, ele pode continuar recebendo comandos provenientes do ambiente do autor e não deve ser necessário conectar o dispositivo de telas diretamente ao ambiente do autor.

![screen_shot_2019-02-25at15218pm](assets/screen_shot_2019-02-25at15218pm.png)

### Próximas etapas {#the-next-steps}

Depois de entender o design arquitetônico do autor e publicar a configuração no AEM Screens, consulte [Configuração do autor e publicação no AEM Screens](author-and-publish.md) para obter mais detalhes.
