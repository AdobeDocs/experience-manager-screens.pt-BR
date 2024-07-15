---
title: Configurar agentes de replicação do Screens
description: Saiba como configurar agentes de replicação do Screens.
role: Developer
level: Intermediate
exl-id: 40877547-5027-41eb-8d66-d4a2d7b9af70
source-git-commit: cdff56f0807f6d5fea4a4b1d545aecb1e80245bb
workflow-type: tm+mt
source-wordcount: '465'
ht-degree: 4%

---

# Configuração dos agentes de replicação do Screens {#configuring-screens-replication-agent}

Esta página descreve como configurar os Agentes de Replicação do Screens.

## Objetivo {#objective}

O Agente de Replicação do Screens é responsável por trazer dados de comandos como *user*, *password*, *rebootSchedule*, *maxNumberOfLogFilesToKeep*, e muitos outros valores desse tipo, de publicação para autor. É essencial configurar esse agente para que o autor possa mostrar o ping do dispositivo.

>[!NOTE]
>Para saber mais sobre os Agentes de Replicação do Screens, consulte [Comandos e Agentes de Replicação do Screens](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/administering/author-publish/author-publish-architecture-overview#screens-replication-agents-and-commands).

Conclua ambas as seções se desejar concluir a configuração do Screens Replication Agent:

1. [Habilitar usuários e atualizar a senha](#enable-users)
1. [Atualizando configurações do Agente de replicação Screens](#replicate-agent)

## Habilitar usuários e atualizar a senha {#enable-users}

Siga as etapas abaixo para habilitar usuários e atualizar a senha para `screens-receiver-user`:

>[!NOTE]
>Por motivos de segurança, é recomendável evitar o uso da senha de administrador para `screens-receiver-user`.

1. Navegue até a instância do autor do AEM.

1. Clique em Ferramentas > **Segurança** > **Usuários**.

   ![imagem](/help/user-guide/assets/screens-replication/screens-replication1.png)

1. Pesquisar por **`screens-receiver-user`**.

1. Clique em **`screens-receiver-user`** e em **Habilitar** na barra de ações.

   ![imagem](/help/user-guide/assets/screens-replication/screens-replication2.png)

1. Clique em **OK** para confirmar.

   ![imagem](/help/user-guide/assets/screens-replication/screens-replication3.png)

   Ao habilitar o usuário, você verá **`screens-receiver-user`** como **Habilitado** no campo **Status**.

   ![imagem](/help/user-guide/assets/screens-replication/screens-replication4.png)

1. Clique em **`screens-receiver-user`** e em **Propriedades** na barra de ações.

   ![imagem](/help/user-guide/assets/screens-replication/screens-replication5.png)

1. Clique em **Alterar senha** em **Configurações da conta** na guia **Detalhes**, conforme mostrado na figura abaixo.

   ![imagem](/help/user-guide/assets/screens-replication/screens-replication6.png)

1. Digite uma nova senha na caixa de diálogo **Alterar Senha** e clique em **Salvar**.

   >[!NOTE]
   >Insira a senha do usuário administrador existente no campo **Sua senha**.

   ![imagem](/help/user-guide/assets/screens-replication/screens-replication7.png)

1. Clique em **Salvar e fechar**.

1. Clique em **`screens-receiver-user`** e em **Ativar** na barra de ações.

   ![imagem](/help/user-guide/assets/screens-replication/screens-replication8.png)

1. Clique em **OK** para confirmar.

   ![imagem](/help/user-guide/assets/screens-replication/screens-replication9.png)

1. Clique em **`screens-receiver-user`** e em **Desabilitar** na barra de ações.

   >[!IMPORTANT]
   > Desabilitar **`screens-receiver-user`** desabilita somente este usuário da instância de Criação e todos os usuários na instância de Publicação permanecem ativos. Não clique em **Desativar** na barra de ações, pois a desativação também remove o usuário das instâncias de Publicação.

   ![imagem](/help/user-guide/assets/screens-replication/screens-replication10.png)

1. Clique em **OK** para confirmar.

## Atualizando configurações do Agente de replicação Screens {#replicate-agent}

Siga a seção abaixo para atualizar as configurações no Agente de replicação do AEM Screens:

>[!IMPORTANT]
>Conclua as etapas a seguir em TODOS os agentes de replicação do AEM Screens existentes.

1. Navegue até a instância do AEM.
1. Clique em Ferramentas > **Implantação** > **Replicação**.

   ![imagem](/help/user-guide/assets/screens-replication/screens-replication1a.png)

1. Clique em **Agentes no autor**.

   ![imagem](/help/user-guide/assets/screens-replication/screens-replication1b.png)

1. Pesquise por todos os agentes de replicação do AEM Screens no autor e clique no link, conforme mostrado na figura abaixo.

   >[!NOTE]
   >Procure todos os agentes de replicação da AEM Screens. O nome do Agente de replicação Screens inclui a letra **S** no título.

   ![imagem](/help/user-guide/assets/screens-replication/screens-replication1c.png)

1. Clique em **Editar**.

   ![imagem](/help/user-guide/assets/screens-replication/screens-replication1d.png)

1. Verifique **Habilitado** na guia **Configurações**.

   ![imagem](/help/user-guide/assets/screens-replication/screens-replication1e.png)

1. Navegue até a guia **Transporte** da caixa de diálogo **Configurações do Agente**, atualize o **Usuário** para **`screens-receiver-user`** e insira a mesma senha definida anteriormente na etapa (8) de [Habilitando Usuários e Atualizando a Senha](#enable-users).

   ![imagem](/help/user-guide/assets/screens-replication/screens-replication1-f.png)

1. Clique em **OK**.

1. Após concluir as etapas anteriores, clique em **Testar Conexão** para verificar a conexão.

   ![imagem](/help/user-guide/assets/screens-replication/screens-replication1g.png)

   Se a verificação da conexão for bem-sucedida, você concluiu a configuração do Screens Replication Agent.
