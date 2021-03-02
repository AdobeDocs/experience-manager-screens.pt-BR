---
title: Registro em massa de jogadores
seo-title: Registro em massa de jogadores
description: Siga esta página para saber mais sobre o Registro em massa de players com AMS/Telas no local.
translation-type: tm+mt
source-git-commit: a00c761297b80239b741e68ef6f2ac611d3559f2
workflow-type: tm+mt
source-wordcount: '328'
ht-degree: 0%

---


# Registro em massa de jogadores {#bulk-registration}

O registro em massa de milhares de jogadores manualmente pode se tornar muito complicado e aumenta o tempo e o custo. Para simplificar esse processo, o recurso de registro em massa permite especificar uma chave pré-compartilhada no AEM que pode ser provisionada em um reprodutor por meio de um arquivo de configuração ou uma solução de Gerenciamento de dispositivos móveis (MDM).

## Implementando o registro em massa de players {#bulk-registering-implementation}

Siga as etapas abaixo para implementar o registro em massa de players:

1. Faça logon na instância do AEM e selecione o projeto do AEM Screens, clique em propriedades e na guia Advanced .
1. Você deve ver uma seção de registro em massa onde pode especificar um código de registro em massa e uma exibição padrão opcional para atribuir ao reprodutor que está registrado em massa
1. Digite um código de sua escolha e selecione uma exibição padrão se necessário
1. Provisione os reprodutores com o URL do servidor e o código de registro adequados usando um arquivo MDM ou JSON de configuração. Consulte a página de implementação do reprodutor específico para seu sistema operacional para obter detalhes exatos. Você também pode usar a interface do usuário do administrador para inserir o código de registro.
1. Se o atributo `registrationKey` corresponder ao configurado no AEM, o reprodutor se registrará automaticamente e, se uma exibição padrão for configurada, esse conteúdo será baixado e reproduzido.

## Práticas recomendadas de segurança {#security-best-practices}

Siga a seção abaixo para considerar algumas das práticas recomendadas para Segurança:

* Para garantir que o código de registro não seja comprometido, configure o código no AEM antes de iniciar o registro em massa e, quando concluído, limpe esse campo e salve no AEM.

* Você pode configurar que o caminho `/bin/screens/`registro só possa ser acessado a partir de intervalos IP conhecidos, se possível.

* Considere o uso de um MDM para provisionar o reprodutor com a configuração.

* Sempre use `HTTPS` e não `HTTP` para comunicação do player com o AEM.

   >[!NOTE]
   >Atualmente, a atribuição de exibição padrão só funciona para registro em massa e não para registro manual sem um código de registro.