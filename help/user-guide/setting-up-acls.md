---
title: Configuração de ACLs
seo-title: Configuração de ACLs
description: Siga esta página para saber como segregar projetos usando ACLs para que cada indivíduo ou equipe gerencie seu próprio projeto.
seo-description: Siga esta página para saber como segregar projetos usando ACLs para que cada indivíduo ou equipe gerencie seu próprio projeto.
uuid: d5609bd9-3f13-4f11-ad4f-23c2ac3aa8fc
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
discoiquuid: 64e4d6ae-3fd3-41ec-84e1-cc2cac7b2519
feature: Administração do Screens
role: Admin
level: Intermediate
exl-id: b40bcc9f-307c-422c-8abb-5c15965772d4
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '561'
ht-degree: 1%

---

# Configuração de ACLs {#setting-up-acls}

A seção a seguir explica como segregar projetos usando ACLs para que cada indivíduo ou equipe gerencie seu próprio projeto.

Como administrador de AEM, você deseja garantir que os membros da equipe de um projeto não interfiram com outros projetos e que cada um dos usuários receba funções específicas de acordo com os requisitos do projeto.

## Configurar permissões {#setting-up-permissions}

As etapas a seguir resumem o procedimento para configurar ACLs para um projeto:

1. Faça logon no AEM e navegue até **Ferramentas** > **Segurança**.

   ![screen_shot_2018-02-16at10156pm](assets/screen_shot_2018-02-16at10156pm.png)

1. Clique em **Groups** e insira uma ID (por exemplo, Acme).

   Como alternativa, use este link, `http://localhost:4502/libs/granite/security/content/groupadmin.html`.

   Em seguida, clique em **Salvar**.

   ![screen_shot_2018-02-16at12648pm](assets/screen_shot_2018-02-16at12648pm.png)

1. Selecione **Contributors** na lista e clique duas vezes nela.

   ![screen_shot_2018-02-18at33938pm](assets/screen_shot_2018-02-18at33938pm.png)

1. Adicione o **Acme** (projeto criado por você) a **Adicionar Membros ao Grupo**. Clique em **Salvar**.

   ![screen_shot_2018-02-18at35630pm](assets/screen_shot_2018-02-18at35630pm.png)

   >[!NOTE]
   >
   >Se desejar que os membros da equipe do projeto registrem os reprodutores (o que envolve a criação de um usuário para cada reprodutor), localize os usuários-administradores do grupo e adicione o grupo ACME aos usuários-administradores

1. Adicione todos os usuários que trabalharão no Projeto **Acme** ao grupo **Acme**.

   ![screen_shot_2018-02-18at41320pm](assets/screen_shot_2018-02-18at41320pm.png)

1. Configure as permissões do grupo **Acme** usando este `(http://localhost:4502/useradmin)`.

   Selecione o grupo **Acme** e clique em **permissions**.

   ![screen_shot_2018-02-18at41534pm](assets/screen_shot_2018-02-18at41534pm.png)

### Permissões {#permissions}

A tabela a seguir resume o caminho com as permissões no nível do projeto:

| **Caminho** | **Permissão** | **Descrição** |
|---|---|---|
| `/apps/<project>` | LER | Fornece acesso aos arquivos do projeto (se aplicável) |
| `/content/dam/<project>` | TODAS | Fornece acesso para armazenar os ativos dos projetos, como imagens ou vídeo no DAM |
| `/content/screens/<project>` | TODAS | Remove o acesso a todos os outros projetos em /content/screens |
| `/content/screens/svc` | LER | Fornece acesso ao serviço de registro |
| `/libs/screens` | LER | Fornece acesso ao DCC |
| `/var/contentsync/content/screens/` | TODAS | Permite atualizar o conteúdo offline para o projeto |

>[!NOTE]
>
>Em alguns casos, é possível separar as funções de autor (como gerenciar ativos e criar canais) das funções de administrador (como registrar players). Nesse cenário, crie dois grupos e adicione o grupo de autores aos colaboradores e o grupo de administradores aos contribuidores e aos usuários-administradores.

### Criação de grupos {#creating-groups}

A criação de um novo projeto também deve criar grupos de usuários padrão com um conjunto básico de permissões atribuídas. Você deve estender as permissões para as funções típicas que temos para o AEM Screens.

Por exemplo, você pode criar os seguintes grupos específicos de projeto:

* Administradores de projeto do Screens
* Operadores de projeto do Screens (registre reprodutores e gerencie locais e dispositivos)
* Usuários do projeto do Screens (trabalhar com canais, agendamentos e atribuições de canal)

A tabela a seguir resume os grupos com descrição e permissões para um projeto do AEM Screens:

<table>
 <tbody>
  <tr>
   <td><strong>Nome do grupo</strong></td>
   <td><strong>Descrição</strong></td>
   <td><strong>Permissões</strong></td>
  </tr>
  <tr>
   <td>Administradores do Screens<br /> <em>screens-admins</em></td>
   <td>Acesso de nível administrativo aos recursos do AEM Screens</td>
   <td>
    <ul>
     <li>Membro Dos Contribuintes</li>
     <li>Membro de usuários-administradores</li>
     <li>TODOS /content/screens</li>
     <li>ALL /content/dam</li>
     <li>TODOS os /content/experience-fragments</li>
     <li>ALL /etc/design/screens</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Usuários do Screens<br /> <em>usuários-telas</em></td>
   <td>Criar e atualizar canais e programações e atribuir ao local no AEM Screens</td>
   <td>
    <ul>
     <li>Membro Dos Contribuintes</li>
     <li>&lt;project&gt; /content/screens</li>
     <li>&lt;project&gt; /content/dam</li>
     <li>&lt;project&gt; /content/experience-fragments</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Operadores de telas<br /> <em>operadores de telas</em></td>
   <td>Criar e atualizar estrutura de localização e registrar players no AEM Screens</td>
   <td>
    <ul>
     <li>Membro Dos Contribuintes</li>
     <li>jcr:all /home/users/screens</li>
     <li>jcr:all /home/groups/screens</li>
     <li>&lt;project&gt; /content/screens</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Players do Screens<br /> <em>screens-&lt;project&gt;-devices</em></td>
   <td>Agrupa todos os players e todos dispositivos que são membros dos colaboradores automaticamente.</td>
   <td><p> Membro de contribuidores</p> </td>
  </tr>
 </tbody>
</table>
