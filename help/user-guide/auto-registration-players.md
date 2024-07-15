---
title: Registro automático de players
description: Siga esta página para saber mais sobre o registro automático de players com AMS/On-Prem Screens.
feature: Administering Screens, Players
role: Admin
level: Intermediate
exl-id: 28449523-a44d-4260-9771-f1987686cbb6
source-git-commit: 873e6ff8b506416bce8660f5eb2cbea75227a9c8
workflow-type: tm+mt
source-wordcount: '340'
ht-degree: 0%

---

# Registro automático de players {#auto-registration}

Registrar em massa milhares de jogadores manualmente pode se tornar complicado e adiciona tempo e custo. Para simplificar esse processo, o recurso de registro em massa permite especificar uma chave pré-compartilhada no AEM que pode ser provisionada em um reprodutor por meio de um arquivo de configuração ou uma solução de Gerenciamento de dispositivo móvel (MDM).

## Implementação do registro automático de players {#bulk-registering-implementation}

Siga as etapas abaixo para implementar o registro automático de jogadores:

1. Faça logon na instância do AEM, clique no projeto do AEM Screens e em **Propriedades** na barra de ações.
1. Clique na guia **Avançado** para exibir a seção **Registro do dispositivo**.

1. Especifique um código de registro automático no campo **Código de registro em massa**. Em seguida, um vídeo padrão opcional na **Atribuição de exibição padrão** para atribuir ao player que é registrado automaticamente.

   >[!NOTE]
   >Insira um código de sua escolha e clique em uma exibição padrão, se necessário.

   ![imagem](/help/user-guide/assets/auto-registration/auto-register1.png)
1. Provisione seus players com o URL do servidor e o código de registro apropriados usando um arquivo MDM ou JSON de configuração.

   >[!NOTE]
   >Consulte a página de implementação do reprodutor específico do seu sistema operacional (SO) para obter mais detalhes. Você também pode usar a interface do administrador para inserir o código de registro.

1. Se o atributo `registrationKey` corresponder ao configurado no AEM, o reprodutor será automaticamente registrado e, se uma exibição padrão estiver configurada, o conteúdo será baixado e reproduzido.

   ![imagem](/help/user-guide/assets/auto-registration/auto-register2.png)

## Práticas recomendadas de segurança {#security-best-practices}

Siga a seção abaixo para considerar algumas das práticas recomendadas para segurança:

* Certifique-se de que o código de registro não esteja comprometido - Configure o código no AEM logo antes de iniciar o registro em massa e, quando terminar, limpe esse campo e salve no AEM.

* Você pode configurar o caminho `/bin/screens/registration` de forma que ele seja acessível somente a partir de intervalos IP conhecidos, se possível.

* Considere usar um MDM para provisionar o reprodutor com a configuração.

* Sempre use `HTTPS` e não `HTTP` para comunicação do player com AEM.

  >[!NOTE]
  >Atualmente, a atribuição de exibição padrão funciona apenas para registro em massa. Isso não funciona para registro manual quando um código de registro não está disponível.
