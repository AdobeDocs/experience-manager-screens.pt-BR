---
title: Configuração de ACLs
seo-title: Configuração de ACLs
description: Siga esta página para saber como separar projetos usando ACLs para que cada indivíduo ou equipe gerencie seu próprio projeto.
seo-description: Siga esta página para saber como separar projetos usando ACLs para que cada indivíduo ou equipe gerencie seu próprio projeto.
uuid: d5609bd9-3f13-4f11-ad4f-23c2ac3aa8fc
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
discoiquuid: 64e4d6ae-3fd3-41ec-84e1-cc2cac7b2519
translation-type: tm+mt
source-git-commit: 8356d5eb9449fd31d293c030620588e47fa6513e

---


# Configuração de ACLs {#setting-up-acls}

A seção a seguir explica como separar projetos usando ACLs para que cada indivíduo ou equipe gerencie seu próprio projeto.

Como administrador do AEM, verifique se os membros da equipe de um projeto não interferem com outros projetos e se cada um dos usuários recebe funções específicas de acordo com os requisitos do projeto.

## Configuração de permissões {#setting-up-permissions}

As etapas a seguir resumem o procedimento para configurar ACLs para um projeto:

1. Faça logon no AEM e navegue até **Ferramentas** > **Segurança**.

   ![screen_shot_2018-02-16at10156pm](assets/screen_shot_2018-02-16at10156pm.png)

1. Clique em **Grupos** e insira uma ID (por exemplo, Acme).

   Como alternativa, use este link `http://localhost:4502/libs/granite/security/content/groupadmin.html`.

   Subsequentemente, clique em **Salvar**.

   ![screen_shot_2018-02-16at12648pm](assets/screen_shot_2018-02-16at12648pm.png)

1. Selecione **Colaboradores** na lista e clique no duplo.

   ![screen_shot_2018-02-18at33938pm](assets/screen_shot_2018-02-18at33938pm.png)

1. Adicione o **Acme** (projeto criado por você) para **Adicionar membros ao grupo**. Clique em **Salvar**.

   ![screen_shot_2018-02-18at35630pm](assets/screen_shot_2018-02-18at35630pm.png)

   >[!NOTE]
   >
   >Se você quiser que os membros da equipe do projeto registrem players (o que envolve a criação de um usuário para cada player), localize os administradores de usuários do grupo e adicione o grupo ACME aos administradores de usuários

1. Adicione todos os usuários que trabalharão no **Acme** Project ao grupo **Acme** .

   ![screen_shot_2018-02-18at41320pm](assets/screen_shot_2018-02-18at41320pm.png)

1. Configure as permissões para o grupo **Acme** usando esta opção `(http://localhost:4502/useradmin)`.

   Selecione o grupo **Acme** e clique nas **permissões**.

   ![screen_shot_2018-02-18at41534pm](assets/screen_shot_2018-02-18at41534pm.png)

### Permissões    {#permissions}

A tabela a seguir resume o caminho com as permissões no nível do projeto:

| **Caminho** | **Permissão** | **Descrição** |
|---|---|---|
| `/apps/<project>` | LEITURA | Fornece acesso aos arquivos do projeto (se aplicável) |
| `/content/dam/<project>` | TODAS | Fornece acesso para armazenar os ativos de projetos, como imagens ou vídeo no DAM |
| `/content/screens/<project>` | TODAS | Remove o acesso a todos os outros projetos em /content/screens |
| `/content/screens/svc` | LEITURA | Fornece acesso ao serviço de registro |
| `/libs/screens` | LEITURA | Fornece acesso ao DCC |
| `/var/contentsync/content/screens/` | TODAS | Permite atualizar conteúdo offline para o projeto |

>[!NOTE]
>
>Em alguns casos, é possível separar as funções do autor (como gerenciar ativos e criar canais) das funções administrativas (como registrar players). Nesse cenário, crie dois grupos e adicione o grupo de autores aos contribuidores e o grupo de administradores aos contribuidores e aos administradores de usuários.

### Criação de grupos {#creating-groups}

A criação de um novo projeto também deve criar grupos de usuários padrão com um conjunto básico de permissões atribuídas. Você deve estender as permissões para as funções típicas que temos para o AEM Screens.

Por exemplo, você pode criar os seguintes grupos específicos do projeto:

* Administradores de projeto do Screens
* Tela Operadores de projeto (registrar players e gerenciar locais e dispositivos)
* Screens Project Users (trabalhar com canais, agendamentos e atribuições de canais)

A tabela a seguir resume os grupos com descrição e permissões para um projeto do AEM Screens:

<table>
 <tbody>
  <tr>
   <td><strong>Nome do grupo</strong></td>
   <td><strong>Descrição</strong></td>
   <td><strong>Permissões   </strong></td>
  </tr>
  <tr>
   <td>Administradores<br /> de telas Administradores de <em>telas</em></td>
   <td>Acesso de nível administrativo para recursos do AEM Screens</td>
   <td>
    <ul>
     <li>Membro Dos Contribuintes</li>
     <li>Membro dos administradores de usuários</li>
     <li>ALL /content/screens</li>
     <li>ALL /content/dam</li>
     <li>TODOS OS /content/experience-fragments</li>
     <li>ALL /etc/design/screens</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Screens Users<br /> <em>screens-users</em></td>
   <td>Criar e atualizar canais e agendamentos e atribuir à localização no AEM Screens</td>
   <td>
    <ul>
     <li>Membro Dos Contribuintes</li>
     <li>&lt;project&gt; /content/screens</li>
     <li>&lt;project&gt; /content/dam</li>
     <li>&lt;project&gt; /content/experience-fragments</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Operadores<br /> de tela operadores de <em>tela</em></td>
   <td>Criar e atualizar a estrutura de localização e registrar players no AEM Screens</td>
   <td>
    <ul>
     <li>Membro Dos Contribuintes</li>
     <li>jcr:all /home/users/screens</li>
     <li>jcr:all /home/groups/screens</li>
     <li>&lt;project&gt; /content/screens</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Screens Players<br /> <em>screens -&lt;project&gt;-devices</em></td>
   <td>Agrupa todos os players e todos os dispositivos são membros dos contribuidores automaticamente.</td>
   <td><p> Membro dos contribuidores</p> </td>
  </tr>
 </tbody>
</table>

