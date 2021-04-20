---
title: Registro automático de jogadores
seo-title: Registro automático de jogadores
description: Siga esta página para saber mais sobre o Registro automático de players com AMS/Telas no local.
feature: Administering Screens, Players
role: Administrator
level: Intermediate
translation-type: tm+mt
source-git-commit: 89c70e64ce1409888800af7c7edfbf92ab4b2c68
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 0%

---


# Registro automático de jogadores {#auto-registration}

O registro em massa de milhares de jogadores manualmente pode se tornar muito complicado e aumenta o tempo e o custo. Para simplificar esse processo, o recurso de registro em massa permite especificar uma chave pré-compartilhada no AEM que pode ser provisionada em um reprodutor por meio de um arquivo de configuração ou de uma solução MDM (Mobile Device Management, gerenciamento de dispositivo móvel).

## Implementando o registro automático de players {#bulk-registering-implementation}

Siga as etapas abaixo para implementar o registro automático de players:

1. Faça logon na instância de AEM, selecione o projeto de telas de AEM e clique em **Propriedades** na barra de ações.
1. Selecione a guia **Advanced** para visualizar a seção **Device registration**.

1. Especifique um código de registro automático no campo **Código de registro em massa** e uma exibição padrão opcional em **Atribuição de exibição padrão** para atribuir ao reprodutor que é registrado automaticamente.
   >[!NOTE]
   >Digite um código de sua escolha e selecione uma exibição padrão, se necessário.

   ![imagem](/help/user-guide/assets/auto-registration/auto-register1.png)
1. Provisione os reprodutores com o URL do servidor e o código de registro adequados usando um arquivo MDM ou JSON de configuração.

   >[!NOTE]
   >Consulte a página de implementação do reprodutor específico do sistema operacional (SO) para obter mais detalhes. Você também pode usar a interface do usuário do administrador para inserir o código de registro.

1. Se o atributo `registrationKey` corresponder ao configurado no AEM, o reprodutor se registrará automaticamente e, se uma exibição padrão for configurada, esse conteúdo será baixado e reproduzido.

   ![imagem](/help/user-guide/assets/auto-registration/auto-register2.png)

## Práticas recomendadas de segurança {#security-best-practices}

Siga a seção abaixo para considerar algumas das práticas recomendadas para Segurança:

* Para garantir que o código de registro não seja comprometido, configure o código em AEM antes de iniciar o registro em massa e, quando concluído, limpe esse campo e salve em AEM.

* Você pode configurar o caminho `/bin/screens/registration` para ser acessível somente a partir de intervalos IP conhecidos, se possível.

* Considere o uso de um MDM para provisionar o reprodutor com a configuração.

* Sempre use `HTTPS` e não `HTTP` para comunicação do player com o AEM.

   >[!NOTE]
   >Atualmente, a atribuição de exibição padrão só funciona para registro em massa e não para registro manual sem um código de registro.