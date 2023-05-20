---
title: Configurações da AEM Platform
seo-title: AEM Platform Configurations
description: A página descreve as configurações da plataforma AEM
seo-description: The page describes AEM Platform Configurations
exl-id: cfe1769b-4da2-430d-a7b1-10dbcaf9f51b
source-git-commit: 707833ddd8ab2573abcac4e9a77ec88778624435
workflow-type: tm+mt
source-wordcount: '513'
ht-degree: 21%

---

# Configurações da AEM Platform  {#platform-configurations}

>[!NOTE]
>
>Uma parte interessada típica dessa atividade é um Implementador de AEM.

Siga as seções abaixo para definir as configurações da plataforma AEM e começar a usar o AEM Screens.

## Configurações do servidor {#server-configurations}

Para definir as configurações do servidor, consulte [Configurações do servidor](https://helpx.adobe.com/experience-manager/6-5/screens/using/configuring-screens-introduction.html#ServerConfiguration).

## Autor-Publicação {#author-publish}

Para configurar a publicação do autor, consulte [Configuração do Author e Publish no AEM Screens](https://helpx.adobe.com/br/experience-manager/6-5/screens/using/author-and-publish.html)

>[!NOTE]
>
>Se houver apenas um autor e uma publicação, basta seguir as etapas em **Configuração de agentes de replicação no autor** na página [Configuração de autor e publicação no AEM Screens](https://helpx.adobe.com/br/experience-manager/6-5/screens/using/author-and-publish.html).

## Configurações do Dispatcher {#dispatcher-configurations}

O Dispatcher é a ferramenta de balanceamento de carga e/ou cache do Adobe Experience Manager. Usar o Dispatcher do AEM também ajuda a proteger seu servidor AEM contra ataques. Portanto, você pode aumentar a segurança da sua instância do AEM usando o Dispatcher em conjunto com um servidor da Web de classe empresarial.

Consulte **[Configurações do Dispatcher para o AEM Screens](https://helpx.adobe.com/experience-manager/6-5/screens/using/dispatcher-configurations-aem-screens.html)** que destaca as diretrizes para configurar o dispatcher para um projeto do AEM Screens.

## Instalação de FFMpeg e representações de vídeo {#installing-ffmpeg}

Instale o FFMpeg seguindo as etapas do sistema operacional apropriado (geralmente o RHEL):

1. Se estiver instalando habilitando EPEL e RPMFusion, você pode instalar todos os codecs do gstreamer para ampliar o suporte para conversões do FFmpeg
1. Se o codec AAC estiver marcado como experimental, as conversões ffmpeg falharão. Para evitar isso, adicione -strict -2 aos perfis de vídeo (/etc/dam/video no AEM 6.3 e movido para /libs/settings/dam/video no AEM 6.4)
   >[!NOTE]
   >
   > Observe que -strict -2 precisa ser os últimos parâmetros da lista de parâmetros. Além disso, no AEM 6.4, é necessário copiar os nós em */libs/settings/dam/video* para */conf/global/settings/dam/video* conforme mencionado no [Representações de vídeo](https://helpx.adobe.com/experience-manager/6-5/screens/using/generating-renditions.html).
1. Verifique se as conversões de vídeo estão ocorrendo e se as representações estão sendo criadas.

## Restrições de senha {#password-restrictions}

A política de senha do AEM precisa ser desativada na instância do AMS. Isso pode ser configurado alternadamente no console da Web usando o serviço de dispositivo do Screens *com.adobe.cq.screens.device.impl.DeviceService*
Consulte **Restrições de senha** seção em[Configuração do Author e Publish no AEM Screens](https://helpx.adobe.com/br/experience-manager/6-5/screens/using/author-and-publish.html)

## Configuração dos ambientes {#setting-up-environments}

Instale e execute as versões mais recentes dos seguintes pacotes para a sua versão do Adobe Experience Manager (AEM):

* AEM Service Pack
* Pacote de recursos do Screens
* AEM Pacote de correções cumulative

Além do que foi descrito acima, identifique todos os pacotes de desenvolvimento (por exemplo, componentes principais do WCM) ou kits de ferramentas de terceiros (por exemplo, SAP Hybris) necessários.
Instale os mesmos pacotes de software em seus ambientes de desenvolvimento locais. Instrua seu cliente a adotar a mesma configuração em todos os servidores de controle de qualidade, Preparo e Produção. Configurações de servidor incompatíveis criarão problemas ao implantar e testar.

>[!NOTE]
>
>Para instalar o Feature Pack mais recente do AEM Screens, consulte [Notas de versão](https://helpx.adobe.com/experience-manager/6-5/screens/user-guide.html?topic=/experience-manager/6-5/screens/morehelp/release-notes.ug.js).

## Configurando ACLs {#setting-up-acls}

A configuração de ACLs explica como segregar projetos para que cada indivíduo ou equipe lide com seu próprio projeto.

Consulte [Configurando ACLs](https://helpx.adobe.com/experience-manager/6-5/screens/using/setting-up-acls.html) para obter mais detalhes.
