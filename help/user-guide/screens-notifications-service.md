---
title: Serviço de notificações do AEM Screens
seo-title: AEM Screens Notifications Service
description: Siga esta página para saber mais sobre como monitorar a atividade do dispositivo.
seo-description: Follow this page to learn more about how you can monitor device activity.
uuid: 9843219d-ed39-4e4f-bef4-e500528ff9f1
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: 8879e510-4f0e-46da-87d2-77c5aaacb26e
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 205235d7-e621-4134-975c-257ae60939bc
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '539'
ht-degree: 0%

---

# Serviço de notificações do AEM Screens{#aem-screens-notifications-service}

<!--removed from metadata: admitteddomains: @adobe.com;@caesars.com-->

***Serviço de notificações do AEM Screens***, descreve o recurso em que é possível monitorar a atividade do dispositivo.

Esta seção abrange os seguintes tópicos:

* **Visão geral**
* **Definição das configurações de email**
* **Notificação por e-mail**
* **Exemplo de caso de uso**

>[!CAUTION]
>
>Essa funcionalidade do AEM Screens só estará disponível se você tiver instalado o AEM 6.3.2 Feature Pack 3 ou o AEM 6.4.1 Screens Feature Pack 1.
>
>Para obter acesso a este Feature Pack, entre em contato com o Suporte do Adobe e solicite acesso. Depois de ter permissões, você pode baixá-las do Compartilhamento de pacotes.

## Visão geral {#overview}

***Serviço de notificações do AEM Screens***, permite que os administradores recebam um email se um player do AEM Screens não fizer ping por um período configurável.

Esse serviço pode ser configurado no console da Web do OSGi.

## Definição das configurações de email {#configuring-email-settings}

Siga as etapas abaixo para definir as configurações de notificação por email:

1. Abertura **Configuração do console da Web do Adobe Experience Manager**.
1. Abertura **Serviço de monitoramento de email do dispositivo do Screens**.

   ![screen_shot_2018-04-26at44602pm](assets/screen_shot_2018-04-26at44602pm.png)

1. Defina os seguintes campos para definir as configurações para o email:

   **Caminho dos dispositivos** Insira o caminho para o(s) projeto(s) do Screens que você deseja monitorar. Normalmente, o caminho é `/home/users/screens/<Name of your project>`.

   Por exemplo, se o seu projeto for **We.Retail**, você usará o caminho do projeto como ***/home/users/screens/we-retail***.

   >[!NOTE]
   >
   >Especifique o caminho do projeto, onde os usuários do dispositivo estão localizados.

   **Frequência de programação** Especifique uma hora (por exemplo, 17h ou 17h) ou a frequência em horas (por exemplo, 1) em que esse monitor deve enviar emails.

   **Tempo limite de ping** Especifica o intervalo em minutos após o qual um dispositivo deve ser considerado inacessível.

   **Servidor SMTP** Especifica o servidor SMTP usado para enviar emails.

   **Porta SMTP** Insira a porta SMTP.

   **Usar TLS** O protocolo TLS permite usar uma comunicação segura com o servidor SMTP.

   É recomendável usar o TLS para conexão segura com servidores de email corporativos. Verifique com o administrador de email os valores apropriados.

   **nome de usuário** Especifique o nome de usuário para enviar emails.

   **senha** Especifique a senha para enviar emails.

   **Recipient** Especifique o endereço de email do recipient.

   >[!NOTE]
   >
   >Você pode inserir apenas um endereço de email. Para enviar um email em massa, crie um grupo ou lista de distribuição com os usuários relevantes.

1. Clique em **Salvar** para configurar a atividade do monitor por meio de um email para o seu dispositivo AEM Screens.

## Notificação por e-mail {#email-notification}

Depois de definir a configuração das notificações por email, você receberá uma notificação por email contendo o link para o dispositivo real relatado como inativo.

Acessar esse link o levará diretamente ao painel do dispositivo.

Os emails só serão enviados se houver pelo menos um dispositivo que não tenha executado ping para o tempo limite de ping fornecido e ainda não esteja executando o ping no momento da geração do email.

### Exemplo de casos de uso {#example-use-cases}

O exemplo a seguir descreve alguns cenários de referência para configurar as propriedades do Serviço de monitoramento de email do dispositivo do Screens.

**Cenário 1**:

Se você definir a frequência de agendamento como 1:00 e o tempo limite de ping como 60, se o dispositivo Screens não executar ping entre 12:00 e 13:00, você receberá uma notificação por email confirmando a inatividade do dispositivo.

**Cenário 2**:

Se você definir a frequência de agendamento como 1 e o tempo limite de ping como 60, se o dispositivo Screens não fizer ping entre uma vez em nenhum momento específico do dia, você receberá uma notificação por email confirmando a inatividade do dispositivo.
