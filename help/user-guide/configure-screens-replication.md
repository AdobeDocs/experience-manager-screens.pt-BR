---
title: Configurar o agente de replicação do Screens
description: Siga esta página para obter informações sobre como configurar o Screens Replication Agent.
role: Developer
level: Intermediate
source-git-commit: 9f0beddf87d9f5473fdedc292d3c24e96b85cdd4
workflow-type: tm+mt
source-wordcount: '249'
ht-degree: 6%

---


# Configurando o agente de replicação do Screens {#configuring-screens-replication-agent}

Esta seção descreve como configurar o agente de replicação do Screens.

## Ativar usuários e atualizar a senha {#enable-users}

Siga as etapas abaixo:

1. Navegue até a instância de AEM.

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
   >Você deve inserir **administrador** em **Sua senha** campo.

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

## Atualizando o Agente de Replicação do Screens {#replicate-agent}

Siga a seção abaixo para atualizar as configurações no agente de Replicação do Screens:

1. Navegue até a instância de AEM.

1. Clique nas ferramentas —> **Implantação** —> **Replicação**.

   ![imagem](/help/user-guide/assets/screens-replication/screens-replication1a.png)
