---
title: Serviço de notificações da AEM Screens
seo-title: Serviço de notificações da AEM Screens
description: Siga esta página para saber mais sobre como monitorar a atividade do dispositivo.
seo-description: Siga esta página para saber mais sobre como monitorar a atividade do dispositivo.
uuid: 9843219d-ed39-4e4f-bef4-e500528ff9f1
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: 8879e510-4f0e-46da-87d2-77c5aaacb26e
feature: Telas de criação
role: Administrador, Desenvolvedor
level: Intermediário
translation-type: tm+mt
source-git-commit: 89c70e64ce1409888800af7c7edfbf92ab4b2c68
workflow-type: tm+mt
source-wordcount: '561'
ht-degree: 5%

---


# Serviço de notificações do AEM Screens{#aem-screens-notifications-service}

<!--removed from metadata: admitteddomains: @adobe.com;@caesars.com-->

***AEM Screens Notifications Service***, descreve o recurso no qual você pode monitorar a atividade do dispositivo.

Esta seção aborda os seguintes tópicos:

* **Visão geral**
* **Definição das configurações de email**
* **Notificação por email**
* **Exemplo de caso de uso**

>[!CAUTION]
>
>Essa funcionalidade do AEM Screens só estará disponível se você tiver instalado AEM 6.3.2 Feature Pack 3 ou AEM 6.4.1 Screens Feature Pack 1.
>
>Para obter acesso a esse Feature Pack, você deve entrar em contato com o Suporte da Adobe e solicitar acesso. Com as devidas permissões, você pode baixá-lo em Compartilhamento de pacotes.

## Visão geral {#overview}

***AEM Screens Notifications Service***, permite que os administradores recebam um email se um reprodutor de telas de AEM não fizer ping por um período de tempo configurável.

Esse serviço pode ser configurado no console da Web OSGi.

## Definição das configurações de email {#configuring-email-settings}

Siga as etapas abaixo para definir as configurações de notificação por email:

1. Abra **Configuração do Console Web do Adobe Experience Manager**.
1. Abra **Serviço de Monitoramento de Email do Dispositivo do Screens**.

   ![screen_shot_2018-04-26at44602pm](assets/screen_shot_2018-04-26at44602pm.png)

1. Defina os seguintes campos para definir as configurações do email:

   **Caminho dos dispositivosInsira o caminho para os projetos do Screens que você deseja monitorar.** Normalmente, o caminho é `/home/users/screens/<Name of your project>`.

   Por exemplo, se seu projeto for **We.Retail**, você usará o caminho do projeto como ***/home/users/screens/we-retail***.

   >[!NOTE]
   >
   >Especifique o caminho do projeto, onde os usuários do dispositivo estão localizados.

   **Agendar** frequênciaEspecifique uma hora (por exemplo, 17:00 ou 17:00) ou frequência em horas (por exemplo, 1) em que esse monitor deve enviar emails.

   **Tempo** limite do pingEspecifica o intervalo em minutos após o qual um dispositivo deve ser considerado inacessível.

   **Servidor SMTP** Especifica o Servidor SMTP usado para enviar emails.

   **Porta SMTPnta a porta SMTP.** 

   **Usar o TLST (** Transport Layer Security) permite usar uma comunicação segura com o Servidor SMTP.

   É recomendável usar TLS para conexão segura com servidores de email corporativos. Verifique com seu administrador de email se há valores apropriados.

   **** nome de usuárioEspecifique o nome de usuário para enviar emails.

   **** senhaEspecifique a senha para enviar emails.

   **** RecipientEspecifique o endereço de email do recipient.

   >[!NOTE]
   >
   >Você pode inserir somente um endereço de email. Para enviar um email em massa, crie uma lista de grupo ou distribuição com os usuários relevantes.

1. Clique em **Save** para configurar a atividade do monitor por meio de um email para seu dispositivo AEM Screens.

## Notificação por email {#email-notification}

Depois de definir a configuração das notificações por email, você receberá uma notificação por email contendo o link para o dispositivo real relatado de inatividade.

Acessar esse link o direcionará diretamente para o painel do dispositivo.

Os emails só serão enviados se houver pelo menos um dispositivo que não tenha pingado pelo tempo limite de ping fornecido e ainda não tenha ping no momento da geração do email.

### Exemplo de casos de uso {#example-use-cases}

O exemplo a seguir descreve alguns cenários para referência, para configurar as propriedades do Screens Device Email Monitoring Service.

**Cenário 1**:

Se você definir a frequência de agendamento como 1:00 e o tempo limite de ping como 60, se o dispositivo Screens não fizer ping entre 12:00 e 13:00 horas, você receberá uma notificação por email confirmando a inatividade do dispositivo.

**Cenário 2**:

Se você definir a frequência de agendamento como 1 e o tempo limite de ping como 60, se o dispositivo Screens não fizer ping entre uma vez em um horário específico do dia, você receberá uma notificação por email confirmando a inatividade do dispositivo.
