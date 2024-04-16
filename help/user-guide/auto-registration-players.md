---
title: Registro automático de players
description: Siga esta página para que você possa saber mais sobre o Registro automático de players com AMS/telas no local.
feature: Administering Screens, Players
role: Admin
level: Intermediate
exl-id: 28449523-a44d-4260-9771-f1987686cbb6
source-git-commit: fff2df02661fc3fb3098be40e090b8bc6925bcc2
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 0%

---

# Registro automático de players {#auto-registration}

Registrar em massa milhares de jogadores manualmente pode se tornar complicado e adiciona tempo e custo. Para simplificar esse processo, o recurso de registro em massa permite especificar uma chave pré-compartilhada no AEM que pode ser provisionada em um reprodutor por meio de um arquivo de configuração ou uma solução de Gerenciamento de dispositivo móvel (MDM).

## Implementação do registro automático de players {#bulk-registering-implementation}

Siga as etapas abaixo para implementar o registro automático de jogadores:

1. Faça logon na instância AEM, clique no projeto AEM Screens e clique em **Propriedades** na barra de ações.
1. Clique em **Avançado** para que você possa exibir a **Registro do dispositivo** seção.

1. Especificar um código de registro automático em **Código de registro em massa** e uma exibição padrão opcional no **Atribuição de exibição padrão** para atribuir ao reprodutor que é registrado automaticamente.

   >[!NOTE]
   >Insira um código de sua escolha e clique em uma exibição padrão, se necessário.

   ![imagem](/help/user-guide/assets/auto-registration/auto-register1.png)
1. Provisione seus players com o URL do servidor e o código de registro apropriados usando um arquivo MDM ou JSON de configuração.

   >[!NOTE]
   >Consulte a página de implementação do reprodutor específico do seu sistema operacional (SO) para obter mais detalhes. Você também pode usar a interface do administrador para inserir o código de registro.

1. Se a variável `registrationKey` O atributo corresponde ao configurado no AEM, o reprodutor se registra automaticamente e, se uma exibição padrão estiver configurada, o conteúdo é baixado e reproduzido.

   ![imagem](/help/user-guide/assets/auto-registration/auto-register2.png)

## Práticas recomendadas de segurança {#security-best-practices}

Siga a seção abaixo para considerar algumas das práticas recomendadas para segurança:

* Certifique-se de que o código de registro não esteja comprometido - Configure o código no AEM logo antes de iniciar o registro em massa e, quando terminar, limpe esse campo e salve no AEM.

* Você pode configurar o caminho `/bin/screens/registration` para ser acessível somente a partir de intervalos IP conhecidos, se possível.

* Considere usar um MDM para provisionar o reprodutor com a configuração.

* Sempre usar `HTTPS` e não `HTTP` para comunicação do reprodutor com AEM.

  >[!NOTE]
  >Atualmente, a atribuição de exibição padrão funciona apenas para registro em massa e não para registro manual sem um código de registro.
