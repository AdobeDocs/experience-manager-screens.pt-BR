---
title: Serviço de notificações do AEM Screens
seo-title: Serviço de notificações do AEM Screens
description: Siga esta página para saber mais sobre como monitorar a atividade do dispositivo.
seo-description: Siga esta página para saber mais sobre como monitorar a atividade do dispositivo.
uuid: 9843219d-ed39-4e4f-bef4-e500528ff9f1
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: 8879e510-4f0e-46da-87d2-77c5aaacb26e
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# Serviço de notificações do AEM Screens{#aem-screens-notifications-service}

<!--removed from metadata: admitteddomains: @adobe.com;@caesars.com-->

***O serviço*** de notificações do AEM Screens descreve o recurso no qual você pode monitorar a atividade do dispositivo.

Esta seção aborda os seguintes tópicos:

* **Visão geral**
* **Configuração de configurações de email**
* **Notificação por email**
* **Exemplo de caso de uso**

>[!CAUTION]
>
>Esta funcionalidade do AEM Screens só estará disponível se você tiver instalado o AEM 6.3.2 Feature Pack 3 ou o AEM 6.4.1 Screens Pack 1.
>
>Para obter acesso a esse Feature Pack, você deve entrar em contato com o Suporte da Adobe e solicitar acesso. Com as devidas permissões, você pode baixá-lo em Compartilhamento de pacotes.

## Visão geral {#overview}

***O serviço*** de notificações do AEM Screens permite que os administradores recebam um email se um reprodutor de telas do AEM não fizer ping por um período de tempo configurável.

Esse serviço pode ser configurado no console da Web OSGi.

## Configuração de configurações de email {#configuring-email-settings}

Siga as etapas abaixo para definir as configurações de notificação por email:

1. Abra a Configuração **do console da Web do** Adobe Experience Manager.
1. Abra o Serviço **de Monitoramento de Email do Dispositivo do** Screens.

   ![screen_shot_2018-04-26at44602pm](assets/screen_shot_2018-04-26at44602pm.png)

1. Defina os seguintes campos para definir suas configurações para o email:

   **Caminho** dos dispositivosInsira o caminho para os projetos de telas que deseja monitorar. O caminho normalmente é `/home/users/screens/<Name of your project>`.

   Por exemplo, se o seu projeto for **We.Retail**, você usará o caminho do projeto como ***/home/users/screens/we-retail***.

   >[!NOTE]
   >
   >Especifique o caminho do projeto, onde os usuários do dispositivo estão localizados.

   **Frequência** de agendamento Especifique um horário (por exemplo, 17:00 ou 17:00) ou frequência em horas (por exemplo, 1) no qual este monitor deve enviar emails.

   **Tempo limite** de pingEspecifica o intervalo em minutos após o qual um dispositivo deve ser considerado inacessível.

   **Servidor** SMTP Especifica o Servidor SMTP usado para enviar emails.

   **Porta** SMTP Insira a porta SMTP.

   **Usar TLS** Transport Layer Security (TLS) permite usar uma comunicação segura com o Servidor SMTP.

   É recomendável usar o TLS para conexão segura com servidores de e-mail corporativos. Consulte o administrador de e-mail para obter os valores apropriados.

   **nome de usuário** Especifique o nome de usuário para enviar emails.

   **senha** Especifique a senha para enviar emails.

   **Destinatário** Especifique o endereço de email do destinatário.

   >[!NOTE]
   >
   >Você pode digitar apenas um endereço de email. Para enviar um email em massa, crie um grupo ou uma lista de distribuição com os usuários relevantes.

1. Clique em **Salvar** para configurar a atividade do monitor por meio de um email para seu dispositivo AEM Screens.

## Email Notification {#email-notification}

Depois de definir a configuração para suas notificações por email, você receberá uma notificação por email que conterá o link para o dispositivo real relatado de inatividade.

Acessar esse link o levará diretamente para o painel do dispositivo.

Os emails só serão enviados se houver pelo menos um dispositivo que não tenha feito ping para o tempo limite de ping fornecido e ainda não esteja fazendo ping no momento da geração do email.

###  Casos de uso de exemplo {#example-use-cases}

O exemplo a seguir descreve alguns cenários para referência, para configurar as propriedades do Screens Device Email Monitoring Service.

**Cenário 1**:

Se você definir a frequência de programação como 1:00 am e o tempo limite de ping como 60, se o dispositivo Screens não fizer ping entre 12:00 pm e 13:00 pm, você receberá uma notificação por email confirmando a inatividade do dispositivo.

**Cenário 2**:

Se você definir a frequência de programação como 1 e o tempo limite de ping como 60, se o dispositivo do Screens não fizer ping entre uma vez em qualquer horário específico do dia, você receberá uma notificação por email confirmando a inatividade do dispositivo.