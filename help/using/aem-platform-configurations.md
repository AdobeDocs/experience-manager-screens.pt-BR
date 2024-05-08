---
title: Configurações da plataforma AEM
description: A página descreve as configurações da plataforma AEM
exl-id: cfe1769b-4da2-430d-a7b1-10dbcaf9f51b
source-git-commit: ef74265eadf5972eae7451b7725946d8b014c198
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 3%

---

# Configurações da plataforma AEM  {#platform-configurations}

>[!NOTE]
>
>Uma parte interessada típica dessa atividade é um Implementador de AEM.

Comece a usar o AEM Screens seguindo as seções abaixo para definir as configurações da plataforma AEM

## Configurações do servidor {#server-configurations}

Para definir as configurações do servidor, consulte [Configurações do servidor](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/administering/configuring-screens-introduction#ServerConfiguration).

## Autor-Publicação {#author-publish}

Consulte [Configuração do Author e Publish no AEM Screens](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/administering/author-publish/author-and-publish).

>[!NOTE]
>
>Se houver apenas um Autor e uma Publicação, siga apenas as etapas em **Configuração dos agentes de replicação no autor** in [Configuração do Author e Publish no AEM Screens](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/administering/author-publish/author-and-publish) página.

## Configurações do Dispatcher {#dispatcher-configurations}

O Dispatcher é a ferramenta de balanceamento de carga e cache do Adobe Experience Manager. Usar o Dispatcher do AEM também ajuda a proteger seu servidor AEM contra ataques. Portanto, você pode aumentar a segurança da instância do AEM usando o Dispatcher com um servidor Web de classe empresarial.

Consulte **[Configurações do Dispatcher para o AEM Screens](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/administering/dispatcher-configurations-aem-screens)** que destaca as diretrizes para configurar o Dispatcher para um projeto do AEM Screens.

## Instalação de FFMpeg e representações de vídeo {#installing-ffmpeg}

Instale o FFMpeg seguindo as etapas do sistema operacional apropriado (geralmente o RHEL):

1. Se estiver instalando habilitando EPEL e RPMFusion, você pode instalar todos os codecs do gstreamer para ampliar o suporte para conversões do FFmpeg
1. Se o codec AAC estiver marcado como experimental, as conversões ffmpeg falharão. Para evitar isso, adicione `-strict -2` aos perfis de vídeo (/etc/dam/video no AEM 6.3 e movido para /libs/settings/dam/video no AEM 6.4)

   >[!NOTE]
   >
   >A variável `-strict -2` deve ser o último parâmetro na lista de parâmetros. Além disso, no AEM 6.4, copie os nós em */libs/settings/dam/video* para */conf/global/settings/dam/video* conforme mencionado no [Representações de vídeo](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/authoring/product-features/generating-renditions).
1. Verifique se as conversões de vídeo estão ocorrendo e se as representações estão sendo criadas.

## Restrições de senha {#password-restrictions}

A política de senha do AEM deve ser desativada na instância do AMS. Isso pode ser configurado alternadamente no console da Web usando o serviço de dispositivo do Screens *com.adobe.cq.screens.device.impl.DeviceService*
Consulte **Restrições de senha** seção em[Configuração do Author e Publish no AEM Screens](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/administering/author-publish/author-and-publish)

## Configuração dos ambientes {#setting-up-environments}

Instale e execute as versões mais recentes dos seguintes pacotes para a sua versão do Adobe Experience Manager (AEM):

* Pacote de serviços do AEM
* Pacote de recursos do Screens
* AEM Cumulative Fix Pack

Além do que foi descrito acima, identifique todos os pacotes de desenvolvimento (por exemplo, componentes principais do WCM) ou kits de ferramentas de terceiros (por exemplo, SAP Hybris) necessários.
Instale os mesmos pacotes de software no ambiente de desenvolvimento local. Instrua seu cliente a adotar a mesma configuração em todos os servidores de controle de qualidade, Preparo e Produção. Configurações de servidor incompatíveis criam problemas ao implantar e testar.

>[!NOTE]
>
>Para instalar o Feature Pack mais recente do AEM Screens, consulte [Notas de versão](https://experienceleague.adobe.com/br/docs/experience-manager-screens/user-guide/aem-screens-introduction).

## Configurando ACLs {#setting-up-acls}

A configuração de ACLs explica como segregar projetos para que cada indivíduo ou equipe lide com seu próprio projeto.

Consulte [Configurando ACLs](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/administering/setting-up-acls) para obter mais detalhes.
