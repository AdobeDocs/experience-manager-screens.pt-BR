---
title: Configurar agentes de replicação do Screens
description: Siga esta página para obter informações sobre como configurar os agentes de replicação do Screens.
role: Developer
level: Intermediate
source-git-commit: 46b466d5d05700def4b2c290fa164fbdabae268a
workflow-type: tm+mt
source-wordcount: '507'
ht-degree: 3%

---


# Configurando agentes de replicação do Screens {#configuring-screens-replication-agent}

Esta página descreve como configurar os agentes de replicação do Screens.

## Objetivo {#objective}

O agente de replicação do Screens é responsável por trazer dados de ping como, por exemplo, *usuário*, *senha*, *reotSchedule*, *maxNumberOfLogFilesToKeep* e muito mais valores como, de publicar para criar. É essencial configurar isso para que o autor possa mostrar o ping do dispositivo.

>[!NOTE]
>Para saber mais sobre os agentes de replicação do Screens, consulte [Agentes e comandos de replicação do Screens](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/administering/author-publish/author-publish-architecture-overview.html?lang=en#screens-replication-agents-and-commands).

Você deve concluir ambas as seções para concluir a configuração do Screens Replication Agent:

1. [Ativar usuários e atualizar a senha](#enable-users)
1. [Atualizando configurações do agente de replicação do Screens](#replicate-agent)

## Ativar usuários e atualizar a senha {#enable-users}

Siga as etapas abaixo para habilitar os usuários e atualizar a senha para screens-receipt-user:

>[!NOTE]
>Por motivos de segurança, é recomendável evitar o uso da senha do administrador para screens-receipt-user.

1. Navegue até a instância do autor do AEM.

1. Clique nas ferramentas —> **Segurança** —> **Usuários**.

   ![imagem](/help/user-guide/assets/screens-replication/screens-replication1.png)

1. Procurar por **screens-receipt-user**.

1. Selecione o **screens-receipt-user** e clique em **Habilitar** na barra de ações.

   ![imagem](/help/user-guide/assets/screens-replication/screens-replication2.png)

1. Clique em **OK** para confirmar.

   ![imagem](/help/user-guide/assets/screens-replication/screens-replication3.png)

   Depois de ativar o usuário, você verá a variável **screens-receipt-user** as **Ativado** nos termos do **Status** campo.

   ![imagem](/help/user-guide/assets/screens-replication/screens-replication4.png)

1. Selecione o **screens-receipt-user** e clique em **Propriedades** na barra de ações.

   ![imagem](/help/user-guide/assets/screens-replication/screens-replication5.png)

1. Clique em **Alterar senha** under **Configurações da conta** do **Detalhes** conforme mostrado na figura abaixo.

   ![imagem](/help/user-guide/assets/screens-replication/screens-replication6.png)

1. Digite uma nova senha no **Alterar senha** e clique em **Salvar**.

   >[!NOTE]
   >Você deve inserir a senha de usuário administrador existente em **Sua senha** campo.

   ![imagem](/help/user-guide/assets/screens-replication/screens-replication7.png)

1. Clique em **Salvar e fechar**.

1. Selecione o **screens-receipt-user** e clique em **Ativar** na barra de ações.

   ![imagem](/help/user-guide/assets/screens-replication/screens-replication8.png)

1. Clique em **OK** para confirmar.

   ![imagem](/help/user-guide/assets/screens-replication/screens-replication9.png)

1. Selecione o **screens-receipt-user** e clique em **Desativar** na barra de ações.

   >[!IMPORTANT]
   > Desabilitando **screens-receipt-user** desativa esse usuário somente da instância do autor e todos os usuários na instância de publicação ainda permanecem ativos. Não clicar em **Desativar** na barra de ações, como desativar, removerá o usuário das instâncias de publicação também.

   ![imagem](/help/user-guide/assets/screens-replication/screens-replication10.png)

1. Clique em **OK** para confirmar.

## Atualizando configurações do agente de replicação do Screens {#replicate-agent}

Siga a seção abaixo para atualizar as configurações no agente de Replicação do Screens:

>[!IMPORTANT]
>Você deve concluir as etapas a seguir em TODOS os agentes de replicação de telas existentes.

1. Navegue até a instância de AEM.

1. Clique nas ferramentas —> **Implantação** —> **Replicação**.

   ![imagem](/help/user-guide/assets/screens-replication/screens-replication1a.png)

1. Clique em **Agentes do autor**.

   ![imagem](/help/user-guide/assets/screens-replication/screens-replication1b.png)

1. Procure todos os agentes de Replicação do Screens no autor e clique no link, conforme mostrado na figura abaixo.

   >[!NOTE]
   >Procure todos os agentes de Replicação do Screens. O nome do Agente de Replicação do Screens incluirá uma letra **S** no título.

   ![imagem](/help/user-guide/assets/screens-replication/screens-replication1c.png)

1. Clique em **Editar**.

   ![imagem](/help/user-guide/assets/screens-replication/screens-replication1d.png)

1. Verificar **Ativado** do **Configurações** guia .

   ![imagem](/help/user-guide/assets/screens-replication/screens-replication1e.png)

1. Navegar para **Transportes** na guia do **Configurações do agente** e atualize a caixa de diálogo **Usuário** para **screens-receipt-user** e digite a mesma senha definida anteriormente na etapa 8 de [Ativar usuários e atualizar a senha](#enable-users).

   ![imagem](/help/user-guide/assets/screens-replication/screens-replication1-f.png)

1. Clique em **OK**.

1. Depois de concluir as etapas anteriores, você pode clicar em **Testar conexão** para verificar a conexão.

   ![imagem](/help/user-guide/assets/screens-replication/screens-replication1g.png)

   Se a verificação de conexão for bem-sucedida, você concluiu a configuração do Screens Replication Agent.