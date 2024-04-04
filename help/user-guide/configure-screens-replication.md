---
title: Configurar os agentes de replicação do Screens
description: Siga esta página para obter informações sobre como configurar os Agentes de replicação do Screens.
role: Developer
level: Intermediate
exl-id: 40877547-5027-41eb-8d66-d4a2d7b9af70
source-git-commit: d1adadbab2cb13626dd8ce70deacced9f55aa4c9
workflow-type: tm+mt
source-wordcount: '498'
ht-degree: 3%

---

# Configuração dos agentes de replicação do Screens {#configuring-screens-replication-agent}

Esta página descreve como configurar os Agentes de replicação do Screens.

## Objetivo {#objective}

O Agente de replicação do Screens é responsável por trazer dados de comandos como, *usuário*, *senha*, *rebootSchedule*, *maxNumberOfLogFilesToKeep* e muitos mais desses valores de publicar para autor. É essencial configurá-lo para que o autor possa mostrar o ping do dispositivo.

>[!NOTE]
>Para saber mais sobre os Agentes de replicação do Screens, consulte [Agentes e comandos de replicação do Screens](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/administering/author-publish/author-publish-architecture-overview.html?lang=en#screens-replication-agents-and-commands).

Você deve concluir ambas as seções para concluir a configuração do Agente de replicação do Screens:

1. [Habilitar usuários e atualizar a senha](#enable-users)
1. [Atualização das configurações do agente de replicação do Screens](#replicate-agent)

## Habilitar usuários e atualizar a senha {#enable-users}

Siga as etapas abaixo para habilitar usuários e atualizar a senha para screens-receiver-user:

>[!NOTE]
>Por motivos de segurança, é recomendável evitar o uso da senha do administrador para screens-receiver-user.

1. Navegue até a instância do autor do AEM.

1. Clique nas ferramentas > **Segurança** > **Usuários**.

   ![imagem](/help/user-guide/assets/screens-replication/screens-replication1.png)

1. Pesquisar por **screens-receiver-user**.

1. Selecione o **screens-receiver-user** e clique em **Ativar** na barra de ações.

   ![imagem](/help/user-guide/assets/screens-replication/screens-replication2.png)

1. Clique em **OK** para confirmar.

   ![imagem](/help/user-guide/assets/screens-replication/screens-replication3.png)

   Após habilitar o usuário, você verá a variável **screens-receiver-user** as **Ativado** no **Status** campo.

   ![imagem](/help/user-guide/assets/screens-replication/screens-replication4.png)

1. Selecione o **screens-receiver-user** e clique em **Propriedades** na barra de ações.

   ![imagem](/help/user-guide/assets/screens-replication/screens-replication5.png)

1. Clique em **Alterar senha** em **Configurações da conta** do **Detalhes** conforme mostrado na figura abaixo.

   ![imagem](/help/user-guide/assets/screens-replication/screens-replication6.png)

1. Digite uma nova senha no campo **Alterar senha** e clique em **Salvar**.

   >[!NOTE]
   >Digite a senha do usuário administrador existente em **Sua senha** campo.

   ![imagem](/help/user-guide/assets/screens-replication/screens-replication7.png)

1. Clique em **Salvar e fechar**.

1. Selecione o **screens-receiver-user** e clique em **Ativar** na barra de ações.

   ![imagem](/help/user-guide/assets/screens-replication/screens-replication8.png)

1. Clique em **OK** para confirmar.

   ![imagem](/help/user-guide/assets/screens-replication/screens-replication9.png)

1. Selecione o **screens-receiver-user** e clique em **Desativar** na barra de ações.

   >[!IMPORTANT]
   > Desativando **screens-receiver-user** desativa somente esse usuário da instância do autor e todos os usuários na instância de publicação ainda permanecem ativos. Não clique em **Desativar** na barra de ações, como a desativação removerá o usuário das instâncias de publicação também.

   ![imagem](/help/user-guide/assets/screens-replication/screens-replication10.png)

1. Clique em **OK** para confirmar.

## Atualização das configurações do agente de replicação do Screens {#replicate-agent}

Siga a seção abaixo para atualizar as configurações no agente de replicação do Screens:

>[!IMPORTANT]
>Você deve concluir as etapas a seguir em TODOS os agentes de replicação de telas existentes.

1. Navegue até a instância do AEM.

1. Clique nas ferramentas > **Implantação** > **Replicação**.

   ![imagem](/help/user-guide/assets/screens-replication/screens-replication1a.png)

1. Clique em **Agentes sobre o autor**.

   ![imagem](/help/user-guide/assets/screens-replication/screens-replication1b.png)

1. Procure todos os agentes de replicação do Screens no autor e clique no link, conforme mostrado na figura abaixo.

   >[!NOTE]
   >Procure todos os agentes de replicação do Screens. O nome do agente de replicação do Screens incluirá uma carta **S** no título.

   ![imagem](/help/user-guide/assets/screens-replication/screens-replication1c.png)

1. Clique em **Editar**.

   ![imagem](/help/user-guide/assets/screens-replication/screens-replication1d.png)

1. Marcar **Ativado** do **Configurações** guia.

   ![imagem](/help/user-guide/assets/screens-replication/screens-replication1e.png)

1. Navegue até **Transporte** na guia **Configurações do agente** e atualize a **Usuário** para **screens-receiver-user** e digite a mesma senha que você definiu antes na etapa (8) de [Habilitar usuários e atualizar a senha](#enable-users).

   ![imagem](/help/user-guide/assets/screens-replication/screens-replication1-f.png)

1. Clique em **OK**.

1. Depois de concluir as etapas anteriores, você pode clicar em **Testar conexão** para verificar a conexão.

   ![imagem](/help/user-guide/assets/screens-replication/screens-replication1g.png)

   Se a verificação da conexão for bem-sucedida, você concluiu a configuração do Agente de replicação do Screens.
