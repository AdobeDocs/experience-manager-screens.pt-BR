---
title: Uso de MDM ou EMM para provisionamento em massa do Android Player
seo-title: Provisionamento em massa do reprodutor Android usando EMM ou MDM
description: Siga esta página para saber mais sobre o provisionamento em massa do Android Player usando EMM ou MDM
translation-type: tm+mt
source-git-commit: 56432654d0895b892223677c8a03f10181864271
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 0%

---


# Provisionamento em massa do reprodutor Android usando o Enterprise Mobility Management {#bulk-provisioning}

Ao implantar o reprodutor Android em massa, torna-se entediante registrar manualmente cada reprodutor no AEM. É altamente recomendável usar uma solução EMM (Enterprise Mobility Management) como VMWare Airwatch, MobileIron ou Samsung Knox para provisionar e gerenciar remotamente sua implantação. O AEM Screens Android player é compatível com o EMM AppConfig padrão do setor para permitir provisionamento remoto.

## Implementação do provisionamento em massa do Android Player usando o Enterprise Mobility Management {#implementation}

Siga as etapas abaixo para permitir o provisionamento em massa no Android Player:

1. Certifique-se de que o dispositivo Android seja compatível com os serviços do Google Play.
1. Registre seus dispositivos Android player com sua solução EMM favorita compatível com o AppConfig.
1. Faça logon no console do EMM e extraia o aplicativo AEM Screens Player do Google Play.
1. Selecione a configuração gerenciada (ou a opção relacionada).
1. Agora, você deve ver uma lista de opções do player que podem ser configuradas (como servidor e código de registro em massa).
1. Configure esses parâmetros, salve e implante a política nos dispositivos.

   >[!NOTE]
   >Os dispositivos devem receber o aplicativo junto com a configuração e apontar para o servidor AEM correto com a configuração selecionada. Se você optar por configurar o código de registro em massa e mantê-lo igual ao configurado no AEM, o reprodutor deverá ser capaz de se registrar automaticamente. Se você tiver configurado uma exibição padrão, ela também poderá baixar e mostrar algum conteúdo padrão (que poderá ser alterado posteriormente de acordo com sua conveniência).

Além disso, verifique com seu fornecedor de EMM o suporte ao AppConfig. Os mais populares, como [VMWare Airwatch](https://docs.samsungknox.com/admin/uem/vm-configure-appconfig.htm), [Mobile Iron](https://docs.samsungknox.com/admin/uem/mobileiron2-configure-appconfig.htm), [SOTI](https://docs.samsungknox.com/admin/uem/soti-configure-appconfig.htm), [Blackberry UEM](https://docs.samsungknox.com/admin/uem/bb-configure-appconfig.htm), [IBM Maas360](https://docs.samsungknox.com/admin/uem/ibm-configure-appconfig.htm) e [Samsung Knox 1/> suporte esse padrão do setor.](https://docs.samsungknox.com/admin/uem/km-configure-appconfig.htm)


