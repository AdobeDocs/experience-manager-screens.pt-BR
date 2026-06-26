---
title: Configurações da plataforma AEM
description: A página descreve as configurações da plataforma AEM
exl-id: cfe1769b-4da2-430d-a7b1-10dbcaf9f51b
TQID: https://experienceleague.adobe.com/qsJ-vj45WoTXXdBU5zsNQYoB7g4HnNTLwwfFSBL-wwI
product_v2: id: a27b4747-2f72-4fb7-9936-be5d11dd2c4aid: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554
topic_v2: id: d095671a-1355-40aa-8b5f-06c33c68080b
source-git-commit: 6ffdfa02d948d50b544f6fa5164dc6dca8bff638
workflow-type: tm+mt
source-wordcount: 592
ht-degree: 4%

---

# Configurações da plataforma AEM {#platform-configurations}

>[!IMPORTANT]
>Esse conteúdo é válido para o AEM no local/AMS (AEM 6.5LTS e AEM 6.5). Para ver o conteúdo do AEM as a Cloud Service Screens, consulte o [guia do AEM as a Cloud Service](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/screens-as-cloud-service/overview/introduction).

>[!NOTE]
>
>Uma parte interessada típica dessa atividade é um Implementador do AEM.

Comece a usar o AEM Screens seguindo as seções abaixo para definir as configurações da plataforma AEM

## Configurações do servidor {#server-configurations}

Para definir as configurações do servidor, consulte [Configurações do Servidor](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/administering/configuring-screens-introduction#ServerConfiguration).

## Autor-Publicação {#author-publish}

Consulte [Configurando Autor e Publicação no AEM Screens](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/administering/author-publish/author-and-publish).

>[!NOTE]
>
>Se houver apenas um Autor e uma Publicação, você só poderá seguir as etapas em **Configuração de Agentes de Replicação no Autor** na [Configuração de Autor e Publicação na página do AEM Screens](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/administering/author-publish/author-and-publish).

## Configurações do Dispatcher {#dispatcher-configurations}

O Dispatcher é a ferramenta de balanceamento de carga e cache do Adobe Experience Manager. Usar o Dispatcher do AEM também ajuda a proteger seu servidor AEM contra ataques. Portanto, você pode aumentar a segurança da sua instância do AEM usando o Dispatcher com um servidor Web de classe empresarial.

Consulte **[Configurações do Dispatcher para AEM Screens](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/administering/dispatcher-configurations-aem-screens)**, que destaca as diretrizes para configurar o Dispatcher para um projeto do AEM Screens.

## Instalação de FFMpeg e representações de vídeo {#installing-ffmpeg}

Instale o FFMpeg seguindo as etapas do sistema operacional apropriado (geralmente o RHEL):

1. Se estiver instalando habilitando EPEL e RPMFusion, você pode instalar todos os codecs do gstreamer para ampliar o suporte para conversões do FFmpeg
1. Se o codec AAC estiver marcado como experimental, as conversões ffmpeg falharão. Para evitar esse problema, adicione `-strict -2` aos perfis de vídeo (`/etc/dam/video` no AEM 6.3 e movido para `/libs/settings/dam/video in AEM 6.4`)

   >[!NOTE]
   >
   >O `-strict -2` deve ser o último parâmetro da lista de parâmetros. Além disso, no AEM 6.4, copie os nós em */libs/settings/dam/video* para */conf/global/settings/dam/video* como mencionado em [Representações de vídeo](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/authoring/product-features/generating-renditions).
1. Verifique se as conversões de vídeo estão ocorrendo e se as representações estão sendo criadas.

## Restrições de senha {#password-restrictions}

A política de senha do AEM deve ser desativada na instância do AMS. Ele também pode ser configurado alternadamente no console da Web usando o serviço de dispositivo do Screens *com.adobe.cq.screens.device.impl.DeviceService*
Consulte a seção **Restrições de Senha** em[Configurando Autor e Publicação no AEM Screens](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/administering/author-publish/author-and-publish)

## Configuração dos ambientes {#setting-up-environments}

Instale e execute as versões mais recentes dos seguintes pacotes para a sua versão do Adobe Experience Manager (AEM):

* AEM Service Pack
* Pacote de recursos do Screens
* AEM Cumulative Fix Pack

Além do exposto acima, identifique quaisquer pacotes de desenvolvimento (por exemplo, WCM Core
componentes) ou kits de ferramentas de terceiros (por exemplo, SAP Hybris) necessários.Instale os mesmos pacotes de software no ambiente de desenvolvimento local. Instrua seu cliente a adotar a mesma configuração em todos os servidores de controle de qualidade, Preparo e Produção. Configurações de servidor incompatíveis criam problemas ao implantar e testar.

>[!NOTE]
>
>Para instalar o Feature Pack mais recente do AEM Screens, consulte as [Notas de Versão](https://experienceleague.adobe.com/pt-br/docs/experience-manager-screens/user-guide/aem-screens-introduction).

## Configurando ACLs {#setting-up-acls}

A configuração de ACLs explica como segregar projetos para que cada indivíduo ou equipe lide com seu próprio projeto.

Consulte [Configurando ACLs](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/administering/setting-up-acls) para obter mais detalhes.

