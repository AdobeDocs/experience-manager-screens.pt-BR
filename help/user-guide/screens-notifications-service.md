---
title: Serviço de notificações do AEM Screens
description: Saiba mais sobre como monitorar a atividade do dispositivo para AEM Screens.
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 205235d7-e621-4134-975c-257ae60939bc
TQID: https://experienceleague.adobe.com/9BVI-WKkjiL-vY57T-GMir-4Dll552q-30LDHF20BxU
product_v2:
  - id: a27b4747-2f72-4fb7-9936-be5d11dd2c4a
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2:
  - id: a5fd0e22-1a77-4f49-a6af-7a57fff19aed
subfeature_v2:
  - id: f5973e90-a5a3-4b84-8602-ee120d4ce9b1
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2:
  - id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dc
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
source-git-commit: d4664dd5678eaccabe656398c437dca264d4675e
workflow-type: tm+mt
source-wordcount: 538
ht-degree: 0%

---

# Serviço de notificações do AEM Screens{#aem-screens-notifications-service}

>[!IMPORTANT]
>Esse conteúdo é válido para o AEM no local/AMS (AEM 6.5LTS e AEM 6.5). Para ver o conteúdo do AEM as a Cloud Service Screens, consulte o [guia do AEM as a Cloud Service](https://experienceleague.adobe.com/pt-br/docs/experience-manager-cloud-service/content/screens-as-cloud-service/overview/introduction).

<!--removed from metadata: admitteddomains: @adobe.com;@caesars.com-->

O ***Serviço de Notificações do AEM Screens*** descreve a atividade do dispositivo de monitoramento.

Esta seção abrange os seguintes tópicos:

* **Visão geral**
* **Definindo Configurações de Email**
* **Notificação por email**
* **Exemplo de caso de uso**

<!-- 
OBSOLETE NOTE>
>[!CAUTION]
>
>This AEM Screens functionality is only available, if you have installed AEM 6.3.2 Feature Pack 3 or AEM 6.4.1 Screens Feature Pack 1.
>
>To get access to this Feature Pack, contact Adobe Support and request access. After you have permissions you can download it from Package Share. 
-->

## Visão geral {#overview}

O ***Serviço de Notificações do AEM Screens*** permite que os administradores recebam um email se um AEM Screens Player não executar ping por um tempo configurável.

Esse serviço pode ser configurado no console da Web do OSGi.

## Definição das configurações de email {#configuring-email-settings}

Siga as etapas abaixo para definir as configurações de notificação por email:

1. Abra A **Configuração Do Console Da Web Do Adobe Experience Manager**.
1. Abra o **Serviço de Monitoramento de Email de Dispositivo do Screens**.

   ![screen_shot_2018-04-26at44602pm](assets/screen_shot_2018-04-26at44602pm.png)

1. Defina os seguintes campos para poder definir as configurações do email:

   **Caminho dos Dispositivos** - Insira o caminho para os Projetos Screens que você deseja monitorar. Normalmente, o caminho é `/home/users/screens/<Name of your project>`.

   Por exemplo, se o seu projeto for **`We.Retail`**, use o caminho do projeto como ***/home/users/screens/we-retail***.

   >[!NOTE]
   >
   >Especifique o caminho do projeto, onde os usuários do dispositivo estão localizados.

   **Frequência de Agendamento** - Especifique uma hora (por exemplo, 17:00 ou 17:00) ou a frequência em horas (por exemplo, 1) em que esse monitor deve enviar emails.

   **Tempo limite de ping** - Este campo especifica o intervalo em minutos após o qual um dispositivo deve ser considerado inacessível.

   **Servidor SMTP** - Especifica o Servidor SMTP que é usado para enviar emails.

   **Porta SMTP** - Insira a Porta SMTP.

   **Usar TLS** - O protocolo TLS permite usar uma comunicação segura com o servidor SMTP.

   A Adobe recomenda que você use o TLS para conexão segura com servidores de email corporativos. Verifique com o administrador de email os valores apropriados.

   **nome de usuário** - Especifique o nome de usuário para enviar emails.

   **senha** - Especifique a senha para enviar emails.

   **Destinatário** - Especifique o endereço de email do destinatário.

   >[!NOTE]
   >
   >Você pode inserir apenas um endereço de email. Para enviar um email em massa, crie um grupo ou lista de distribuição com os usuários relevantes.

1. Clique em **Salvar** para configurar a atividade de monitor por meio de um email para o seu dispositivo AEM Screens.

## Notificação por e-mail {#email-notification}

Após definir a configuração das notificações por email, você receberá uma notificação por email contendo o link para o dispositivo real relatado como inativo.

O acesso a esse link o direciona diretamente para o painel do dispositivo.

Os emails só serão enviados se:

* há pelo menos um dispositivo que não executou ping para o tempo limite de ping determinado e
* O ainda não está fazendo ping no momento da geração do email.

### Exemplo de casos de uso {#example-use-cases}

O exemplo a seguir descreve alguns cenários para referência, para configurar as propriedades do Serviço de monitoramento de email de dispositivo do Screens.

**Cenário 1**

Você definiu a frequência de agendamento como 1:00 A.M. e o tempo limite de ping como 60. Em seguida, se o dispositivo AEM Screens não executar ping entre 12h00 e 11h00, você receberá uma notificação por email confirmando a inatividade do dispositivo.:00:00

**Cenário 2**

Você define a frequência de agendamento como 1 e o tempo limite de ping como 60. Em seguida, se o dispositivo AEM Screens não executar ping de uma vez em nenhum momento específico do dia, você receberá uma notificação por email que confirma a inatividade do dispositivo.
