---
title: Configurações da AEM Platform
seo-title: Configurações da AEM Platform
description: A página descreve AEM configurações da plataforma
seo-description: A página descreve AEM configurações da plataforma
source-git-commit: 4611dd40153ccd09d3a0796093157cd09a8e5b80
workflow-type: tm+mt
source-wordcount: '522'
ht-degree: 21%

---

# Configurações da AEM Platform  {#platform-configurations}

>[!NOTE]
>
>A parte interessada típica dessa atividade é um Implementador de AEM.

Siga as seções abaixo para configurar AEM configurações da plataforma e começar a usar o AEM Screens.

## Configurações do servidor {#server-configurations}

Para configurar configurações do servidor, consulte [Configurações do Servidor](https://helpx.adobe.com/experience-manager/6-5/screens/using/configuring-screens-introduction.html#ServerConfiguration).

## Autor-Publicar {#author-publish}

Para configurar a publicação do autor, consulte [Configuração do autor e publicação no AEM Screens](https://helpx.adobe.com/br/experience-manager/6-5/screens/using/author-and-publish.html)

>[!NOTE]
>
>Se houver apenas um autor e uma publicação, basta seguir as etapas em **Configuração de agentes de replicação no autor** na página [Configuração de autor e publicação no AEM Screens](https://helpx.adobe.com/experience-manager/6-5/screens/using/author-and-publish.html).

## Configurações do Dispatcher {#dispatcher-configurations}

O Dispatcher é a ferramenta de balanceamento de carga e/ou cache do Adobe Experience Manager. Usar o Dispatcher do AEM também ajuda a proteger seu servidor AEM contra ataques. Portanto, você pode aumentar a segurança da sua instância do AEM usando o Dispatcher em conjunto com um servidor da Web de classe empresarial.

Consulte **[Configurações do Dispatcher para AEM Screens](https://helpx.adobe.com/experience-manager/6-5/screens/using/dispatcher-configurations-aem-screens.html)** que destaca as diretrizes para configurar o Dispatcher para um projeto do AEM Screens.

## Instalar o FFMpeg e as representações de vídeo {#installing-ffmpeg}

Instale o FFMpeg seguindo as etapas para o SO apropriado (geralmente RHEL):

1. Ao instalar ativando o EPEL e o RPMFusion, você pode instalar todos os codecs gstreamer para ampliar o suporte para conversões FFmpeg
1. Se o codec AAC for marcado como experimental, as conversões ffmpeg falharão. Para evitar isso, adicione -hard -2 aos perfis de vídeo (/etc/dam/video no AEM 6.3 e mova-se para /libs/settings/dam/video no AEM 6.4)
   >[!NOTE]
   >
   > Observe que -hard -2 precisa ser os últimos parâmetros na lista de parâmetros. Além disso, no AEM 6.4, você precisa copiar os nós em */libs/settings/dam/video* para */conf/global/settings/dam/video*, conforme mencionado em [Representações de vídeo](https://helpx.adobe.com/experience-manager/6-5/screens/using/generating-renditions.html).
1. Verifique se as conversões de vídeo estão acontecendo e se as representações estão sendo criadas.

## Restrições de senha {#password-restrictions}

A política de senha do AEM precisa ser desativada na instância do AMS. Isso pode ser configurado alternadamente no console da Web usando o serviço de dispositivo do Screens *com.adobe.cq.screens.device.impl.DeviceService*
Consulte a seção **Restrições de senha** em[Configuração de autor e publicação no AEM Screens](https://helpx.adobe.com/experience-manager/6-5/screens/using/author-and-publish.html)

## Configurar os ambientes {#setting-up-environments}

Instale e execute as versões mais atuais dos seguintes pacotes para sua versão do Adobe Experience Manager (AEM):

* AEM Service Pack
* Pacote de recursos do Screens
* AEM Cumulative Fix Pack

Além do acima, identifique quaisquer pacotes de desenvolvimento (por exemplo, WCM Core
componentes) ou kits de ferramentas de terceiros (por exemplo, SAP Hybris) necessários.
Instale os mesmos pacotes de software nos ambientes de desenvolvimento local. Instrua seu cliente a adotar a mesma configuração em todos os servidores de controle de qualidade, preparo e produção. Configurações de servidor incompatíveis criarão problemas ao implantar e testar.

>[!NOTE]
>
>Para instalar o Feature Pack mais recente para AEM Screens, consulte [Notas de versão](https://helpx.adobe.com/experience-manager/6-5/screens/user-guide.html?topic=/experience-manager/6-5/screens/morehelp/release-notes.ug.js).

## Configurando ACLs {#setting-up-acls}

Configurar ACLs explica como separar projetos para que cada indivíduo ou equipe controle seu próprio projeto.

Consulte [Configurando ACLs](https://helpx.adobe.com/experience-manager/6-5/screens/using/setting-up-acls.html) para obter mais detalhes.
