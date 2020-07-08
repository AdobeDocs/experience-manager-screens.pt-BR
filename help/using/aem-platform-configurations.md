---
title: Configurações da AEM Platform
seo-title: Configurações da AEM Platform
description: A página descreve as configurações do AEM Platform
seo-description: A página descreve as configurações do AEM Platform
translation-type: tm+mt
source-git-commit: f25176be89424059b8c51296969f069687328536
workflow-type: tm+mt
source-wordcount: '522'
ht-degree: 21%

---

# Configurações da AEM Platform  {#platform-configurations}

>[!NOTE]
>
>A parte interessada típica desta atividade é um Implementador do AEM.

Siga as seções abaixo para configurar as configurações da plataforma AEM para começar a usar os AEM Screens.

## Configurações do servidor {#server-configurations}

Para configurar as configurações do servidor, consulte Configurações [do](https://helpx.adobe.com/experience-manager/6-5/screens/using/configuring-screens-introduction.html#ServerConfiguration)servidor.

## Autor-Publicar {#author-publish}

Para configurar a publicação do autor, consulte [Configurando o autor e a publicação em AEM Screens](https://helpx.adobe.com/br/experience-manager/6-5/screens/using/author-and-publish.html)

>[!NOTE]
>
>Se houver apenas um autor e uma publicação, basta seguir as etapas em **Configuração de agentes de replicação no autor** na página [Configuração de autor e publicação no AEM Screens](https://helpx.adobe.com/br/experience-manager/6-5/screens/using/author-and-publish.html).

## Configurações do Dispatcher {#dispatcher-configurations}

O Dispatcher é a ferramenta de balanceamento de carga e/ou cache do Adobe Experience Manager. Usar o Dispatcher do AEM também ajuda a proteger seu servidor AEM contra ataques. Portanto, você pode aumentar a segurança da sua instância do AEM usando o Dispatcher em conjunto com um servidor da Web de classe empresarial.

Consulte Configurações da **[Dispatcher para AEM Screens](https://helpx.adobe.com/experience-manager/6-5/screens/using/dispatcher-configurations-aem-screens.html)**que destaca as diretrizes para configurar o dispatcher para um projeto de AEM Screens.

## Instalação de execuções de FFMpeg e vídeo {#installing-ffmpeg}

Instale o FFMpeg seguindo as etapas para o SO apropriado (geralmente RHEL):

1. Se você estiver instalando ao ativar o EPEL e o RPMFusion, poderá instalar todos os codecs gstream para ampliar o suporte para conversões FFmpeg
1. Se o codec AAC estiver marcado como experimental, as conversões de ffmpeg falharão. Para evitar esse acréscimo, adicione -severity -2 aos perfis de vídeo (/etc/dam/video no AEM 6.3 e mova-se para /libs/settings/dam/video no AEM 6.4)
   >[!NOTE]
   >
   > Observe que -severity -2 precisa ser o último parâmetro na lista de parâmetros. Além disso, no AEM 6.4, é necessário copiar os nós em */libs/settings/dam/video* para */conf/global/settings/dam/video* , conforme mencionado nas Representações [de](https://helpx.adobe.com/experience-manager/6-5/screens/using/generating-renditions.html)vídeo.
1. Verifique se as conversões de vídeo estão ocorrendo e se as execuções estão sendo criadas.

## Restrições de senha {#password-restrictions}

A política de senha do AEM precisa ser desabilitada na instância do AMS. Isso pode ser configurado alternadamente no console da Web usando o serviço de dispositivo Screens *com.adobe.cq.screens.device.impl.DeviceService* Consulte a seção Restrições **de** senha[em Configuração de autor e publicação em AEM Screens](https://helpx.adobe.com/br/experience-manager/6-5/screens/using/author-and-publish.html)

## Configuração dos Ambientes {#setting-up-environments}

Instale e execute as versões mais recentes dos seguintes pacotes para sua versão do Adobe Experience Manager (AEM):

* AEM Service Pack
* Pacote de recursos do Screens
* AEM Cumulative Fix Pack

Além do acima, identifique quaisquer pacotes de desenvolvimento (por exemplo, Componentes WCM) ou kits de ferramentas de terceiros (por exemplo, Híbris SAP) necessários.
Instale os mesmos pacotes de software nos ambientes de desenvolvimento local. Instrua seu cliente a adotar a mesma configuração em todos os seus servidores de QA, estágio e produção. Configurações de servidor incompatíveis criarão problemas ao implantar e testar.

>[!NOTE]
>
>Para instalar o Feature Pack mais recente para AEM Screens, consulte as [Notas](https://helpx.adobe.com/experience-manager/6-5/screens/user-guide.html?topic=/experience-manager/6-5/screens/morehelp/release-notes.ug.js)de versão.

## Configuração de ACLs {#setting-up-acls}

Configurar ACLs explica como separar projetos para que cada indivíduo ou equipe gerencie seu próprio projeto.

Refer  to [Setting up ACLs](https://helpx.adobe.com/experience-manager/6-5/screens/using/setting-up-acls.html) for more details.
