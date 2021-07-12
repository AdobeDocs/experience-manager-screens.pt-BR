---
title: Visão geral da arquitetura de criação e publicação
seo-title: Visão geral da arquitetura de criação e publicação
description: A arquitetura AEM Screens se parece com uma arquitetura AEM Sites tradicional. O conteúdo é criado em uma instância de autor de AEM e depois replicado para várias instâncias de publicação. Siga esta página para saber mais sobre a visão geral da arquitetura do autor e da publicação.
seo-description: A arquitetura AEM Screens se parece com uma arquitetura AEM Sites tradicional. O conteúdo é criado em uma instância de autor de AEM e depois replicado para várias instâncias de publicação. Siga esta página para saber mais sobre a visão geral da arquitetura do autor e da publicação.
uuid: 19bac3de-8938-4339-82f0-6ccb932b6684
content-type: reference
topic-tags: administering
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
discoiquuid: 112404de-5a5a-4b37-b87c-d02029933c8a
docset: aem65
feature: Administração do Screens
role: Admin, Developer
level: Intermediate
exl-id: ba23eb8e-bbde-4a6e-8cfb-ae98176ed890
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '1028'
ht-degree: 3%

---

# Visão geral da arquitetura de criação e publicação {#author-and-publish-architectural-overview}

Esta página destaca os seguintes tópicos:

* **Introdução a servidores de publicação**
* **Visão geral da arquitetura**
* **Processo de registro**

## Pré-requisitos {#prerequisites}

Antes de começar a usar os servidores de criação e publicação, você deve ter conhecimento prévio de:

* **Topologia de AEM**
* **Criação e gerenciamento de projeto do AEM Screens**
* **Processo de registro do dispositivo**

>[!NOTE]
>
>Essa funcionalidade do AEM Screens só estará disponível se você tiver instalado AEM 6.4 Screens Feature Pack 2. Para obter acesso a esse Feature Pack, você deve entrar em contato com o Suporte da Adobe e solicitar acesso. Com as devidas permissões, você pode baixá-lo em Compartilhamento de pacotes.

## Introdução {#introduction}

A arquitetura AEM Screens se parece com uma arquitetura AEM Sites tradicional. O conteúdo é criado em uma instância de autor de AEM e depois replicado para várias instâncias de publicação. Os dispositivos AEM Screens agora podem se conectar a um farm de publicação de AEM por meio do balanceador de carga. Várias instâncias de publicação de AEM podem ser adicionadas para continuar a dimensionar o farm de publicação.

*Por exemplo*, um autor de conteúdo do AEM Screens emite um comando no sistema de criação de um determinado dispositivo configurado para interagir com um farm de publicação ou um autor de conteúdo do AEM Screens que obtém informações sobre dispositivos configurados para interagir com farms de publicação.

O diagrama a seguir ilustra os ambientes de criação e publicação.

![screen_shot_2019-03-04at30236pm](assets/screen_shot_2019-03-04at30236pm.png)

## Design arquitetônico {#architectural-design}

Há cinco componentes arquiteturais, facilitando essa solução:

* ***Replicação de*** conteúdo do autor para publicar para exibição por dispositivos

* ****** Reversereplicação de conteúdo binário da publicação (recebida de dispositivos) para o autor
* ****** Envio de comandos do autor para publicação por meio de APIs REST específicas
* ****** Mensagens entre instâncias de publicação para sincronizar atualizações e comandos de informações do dispositivo
* ****** Consultar o autor das instâncias de publicação para obter informações do dispositivo por meio de APIs REST específicas

### Replicação (encaminhamento) de conteúdo e configurações  {#replication-forward-of-content-and-configurations}

Os agentes de replicação padrão são usados para replicar o conteúdo do canal de telas, as configurações de localização e as configurações do dispositivo. Isso permite que os autores atualizem o conteúdo de um canal e, como opção, passem por algum tipo de fluxo de trabalho de aprovação antes de publicar atualizações de canal. Um agente de replicação precisa ser criado para cada instância de publicação no farm de publicação.

O diagrama a seguir ilustra o processo de replicação:

![screen_shot_2019-03-04at33935pm](assets/screen_shot_2019-03-04at33935pm.png)

>[!NOTE]
>
>Um agente de replicação precisa ser criado para cada instância de publicação no farm de publicação.

### Agentes e comandos de replicação do Screens  {#screens-replication-agents-and-commands}

Os agentes de replicação específicos do Custom Screens são criados para enviar comandos da instância do autor para o dispositivo AEM Screens. As instâncias de Publicação do AEM servem como um intermediário para encaminhar esses comandos para o dispositivo.

Isso permite que os autores continuem a gerenciar o dispositivo, como enviar atualizações de dispositivos e capturar tela do ambiente de criação. Os agentes de replicação do AEM Screens têm uma configuração de transporte personalizada, como agentes de replicação padrão.

### Mensagens entre instâncias de publicação  {#messaging-between-publish-instances}

Em muitos casos, um comando só deve ser enviado para um dispositivo uma única vez. No entanto, em uma arquitetura de publicação com balanceamento de carga, é desconhecido a instância de publicação à qual o dispositivo está se conectando.

Portanto, a instância do autor envia a mensagem para todas as instâncias de Publicação. No entanto, apenas uma única mensagem deve ser retransmitida para o dispositivo. Para garantir mensagens corretas, alguma comunicação deve ocorrer entre instâncias de publicação. Isso é feito usando *Apache AtiveMQ Artemis*. Cada instância de publicação é colocada em uma Topologia amplamente acoplada usando o serviço de descoberta Sling baseado em Oak e o AtiveMQ é configurado para que cada instância de publicação possa se comunicar e criar uma única fila de mensagens. O dispositivo Screens pesquisa o farm de publicação por meio do balanceador de carga e seleciona o comando da parte superior da fila.

### Replicação reversa {#reverse-replication}

Em muitos casos, após um comando, espera-se que algum tipo de resposta do dispositivo Screens seja encaminhada para a instância do autor. Para alcançar esse AEM, ***Reverse replication*** é usado.

* Crie um agente de replicação reversa para cada instância de publicação, semelhante aos agentes de replicação padrão e aos agentes de replicação de telas.
* Uma configuração de iniciador de fluxo de trabalho escuta nós modificados na instância de publicação e, por sua vez, aciona um fluxo de trabalho para colocar a resposta do Dispositivo na caixa de saída da instância de publicação.
* Uma replicação reversa nesse contexto é usada apenas para dados binários (como arquivos de log e capturas de tela) fornecidos pelos dispositivos. Dados não binários são recuperados por pesquisa.
* A replicação inversa pesquisada da instância do autor de AEM recupera a resposta e a salva na instância do autor.

### Pesquisa de instâncias de publicação  {#polling-of-publish-instances}

A instância do autor precisa ser capaz de pesquisar os dispositivos para obter uma pulsação e saber o status de integridade de um dispositivo conectado.

Dispositivos ping no balanceador de carga e são roteados para uma instância de publicação. O status do dispositivo é então exposto pela instância de publicação por meio de uma API de publicação servida @ **api/screens-dcc/devices/static** para todos os dispositivos ativos e **api/screens-dcc/devices/&lt;device_id>/status.json** para um único dispositivo.

A instância de autor pesquisa todas as instâncias de publicação e mescla as respostas do status do dispositivo em um único status. O trabalho agendado que pesquisa o autor é `com.adobe.cq.screens.impl.jobs.DistributedDevicesStatiUpdateJob` e pode ser configurado com base em uma expressão cron.

## Registro {#registration}

O registro continua a ser originário da instância do autor do AEM. O Dispositivo AEM Screens é apontado para a instância do autor e o registro é concluído.

Depois que um dispositivo é registrado no ambiente de criação, a configuração do dispositivo e as atribuições de canal/programação são replicadas para as instâncias de publicação do AEM. A configuração do Dispositivo AEM Screens é atualizada para apontar para o Balanceador de carga na frente do farm de publicação do AEM. Essa configuração deve ser única. Depois que o Dispositivo Screens for conectado com êxito ao ambiente de publicação, ele poderá continuar a receber comandos originados do ambiente de criação e não será necessário conectar o dispositivo Screens diretamente ao ambiente de criação.

![screen_shot_2019-02-25at15218pm](assets/screen_shot_2019-02-25at15218pm.png)

### Próximas etapas {#the-next-steps}

Depois de entender o design arquitetônico da configuração de criação e publicação no AEM Screens, consulte [Configuração do autor e publicação para AEM Screens](author-and-publish.md) para obter mais detalhes.
