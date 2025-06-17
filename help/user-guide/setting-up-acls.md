---
title: Configurando ACLs
description: Saiba como segregar projetos usando Listas de controle de acesso (ACLs) para que cada indivíduo ou equipe lide com seu próprio projeto.
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: b40bcc9f-307c-422c-8abb-5c15965772d4
source-git-commit: dcaaa1c7ab0a55cecce70f593ed4fded8468130b
workflow-type: tm+mt
source-wordcount: '497'
ht-degree: 2%

---

# Configurando Listas de Controle de Acesso (ACLs) {#setting-up-acls}

A seção a seguir explica como segregar projetos usando Listas de controle de acesso (ACLs), para que cada indivíduo ou equipe lide com seu próprio projeto.

Como administrador do AEM, você deseja garantir que os membros da equipe de um projeto não interfiram em outros projetos. Cada usuário recebe funções específicas de acordo com os requisitos do projeto.

## Configuração de permissões {#setting-up-permissions}

As etapas a seguir resumem o procedimento para configurar ACLs para um projeto:

1. Faça logon no AEM e navegue até **Ferramentas** > **Segurança**.

   ![screen_shot_2018-02-16at10156pm](assets/screen_shot_2018-02-16at10156pm.png)

1. Clique em **Grupos** e insira uma ID (por exemplo, Acme).

   Como alternativa, use este link, `http://localhost:4502/libs/granite/security/content/groupadmin.html`.

   Em seguida, clique em **Salvar**.

   ![screen_shot_2018-02-16at12648pm](assets/screen_shot_2018-02-16at12648pm.png)

1. Clique em **Colaboradores** na lista e clique duas vezes nela.

   ![screen_shot_2018-02-18at33938pm](assets/screen_shot_2018-02-18at33938pm.png)

1. Adicione o **Acme** (projeto criado) a **Adicionar membros ao grupo**. Clique em **Salvar**.

   ![screen_shot_2018-02-18at35630pm](assets/screen_shot_2018-02-18at35630pm.png)

   >[!NOTE]
   >
   >Se você quiser que os membros da equipe do projeto registrem players (o que envolve criar um usuário para cada player), localize os administradores de usuários do grupo e adicione o grupo ACME aos administradores de usuários

1. Adicione todos os usuários que estão trabalhando no projeto **Acme** ao grupo **Acme**.

   ![screen_shot_2018-02-18at41320pm](assets/screen_shot_2018-02-18at41320pm.png)

1. Configure as permissões para o grupo **Acme** usando este `(http://localhost:4502/useradmin)`.

   Clique no grupo **Acme** e clique em **permissões**.

   ![screen_shot_2018-02-18at41534pm](assets/screen_shot_2018-02-18at41534pm.png)

### Permissões {#permissions}

A tabela a seguir resume o caminho com as permissões no nível do projeto:

| **Caminho** | **Permissão** | **Descrição** |
|---|---|---|
| `/apps/<project>` | LER | Fornecer acesso aos arquivos do projeto, se aplicável. |
| `/content/dam/<project>` | TODAS | Forneça acesso para armazenar os ativos do projeto, como imagens ou vídeos, no DAM. |
| `/content/screens/<project>` | TODAS | Remove o acesso a todos os outros projetos em /content/screens. |
| `/content/screens/svc` | LER | Forneça acesso ao serviço de registro. |
| `/libs/screens` | LER | Forneça acesso ao DCC. |
| `/var/contentsync/content/screens/` | TODAS | Ajuda a atualizar o conteúdo offline do projeto. |

>[!NOTE]
>
>Às vezes, você pode separar as funções do autor (como gerenciar ativos e criar canais) das funções de administrador (como registrar players). Nesse cenário, crie dois grupos e adicione o grupo do autor aos colaboradores e o grupo de administradores aos colaboradores e administradores de usuários.

### Criação de grupos {#creating-groups}

A criação de um projeto também deve criar grupos de usuários padrão com um conjunto básico de permissões atribuídas. Estenda as permissões para as funções típicas definidas no AEM Screens.

Por exemplo, você pode criar os seguintes grupos específicos de projeto:

* Administradores de projetos do Screens
* Operadores de projeto do Screens (registre players e gerencie locais e dispositivos)
* Usuários de projeto do Screens (trabalham com canais, agendamentos e atribuições de canal)

A tabela a seguir resume os grupos com descrição e permissões para um projeto do AEM Screens:

<table>
 <tbody>
  <tr>
   <td><strong>Nome do grupo</strong></td>
   <td><strong>Descrição</strong></td>
   <td><strong>Permissões</strong></td>
  </tr>
  <tr>
   <td>Administradores do Screens<br /> <em><code>screens-admins</code></em></td>
   <td>Acesso de nível administrativo para recursos do AEM Screens</td>
   <td>
    <ul>
     <li>Membro de contribuidores</li>
     <li>Membro DE administradores-usuários</li>
     <li>ALL /content/screens</li>
     <li>ALL /content/dam</li>
     <li>ALL /content/experience-fragments</li>
     <li>ALL /etc/design/screens</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Usuários do Screens<br /> <em><code>screens-users</code></em></td>
   <td>Criar e atualizar canais e agendamentos e atribuir a locais na AEM Screens</td>
   <td>
    <ul>
     <li>Membro de contribuidores</li>
     <li><code>&lt;project&gt; /content/screens</code></li>
     <li><code>&lt;project&gt; /content/dam</code></li>
     <li><code>&lt;project&gt; /content/experience-fragments</code></li>
    </ul> </td>
  </tr>
  <tr>
   <td>Operadores do Screens<br /> <em><code>screens-operators</code></em></td>
   <td>Criar e atualizar estrutura de localização e registrar players no AEM Screens</td>
   <td>
    <ul>
     <li>Membro de contribuidores</li>
     <li><code>jcr:all /home/users/screens</code></li>
     <li><code>jcr:all /home/groups/screens</code></li>
     <li><code>&lt;project&gt; /content/screens</code></li>
    </ul> </td>
  </tr>
  <tr>
   <td>Screens Players<br /> <em><code>screens-&lt;project&gt;-devices</code></em></td>
   <td>Todos os players e todos os players/dispositivos são membros dos colaboradores automaticamente.</td>
   <td><p> Membro de contribuidores</p> </td>
  </tr>
 </tbody>
</table>
