---
title: Especificações do dispositivo
description: Saiba mais sobre as especificações do dispositivo relacionadas ao AEM Screens.
exl-id: c2e521b3-89f5-4537-a751-0bfa031286c4
TQID: https://experienceleague.adobe.com/nRZXWarHxFk1wgwR5YLLNcxx3OKs-fWKq1U9uB7yeBw
product_v2:
  - id: a27b4747-2f72-4fb7-9936-be5d11dd2c4a
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
source-git-commit: d4664dd5678eaccabe656398c437dca264d4675e
workflow-type: tm+mt
source-wordcount: 258
ht-degree: 0%

---

# Configurações do dispositivo {#device-configurations}

>[!IMPORTANT]
>Esse conteúdo é válido para o AEM no local/AMS (AEM 6.5LTS e AEM 6.5). Para ver o conteúdo do AEM as a Cloud Service Screens, consulte o [guia do AEM as a Cloud Service](https://experienceleague.adobe.com/pt-br/docs/experience-manager-cloud-service/content/screens-as-cloud-service/overview/introduction).

>[!NOTE]
>
>Uma parte interessada típica dessa atividade é um Integrador de áudio e vídeo.

Com base nas informações coletadas durante o *Dia Zero*, confirme as seguintes informações antes de iniciar o desenvolvimento:

* Qual é a orientação, as dimensões e a resolução das telas usadas?

* Quantas telas estão sendo instaladas por local e em qual configuração?

* Que software e sistema operacional devem ser instalados nos dispositivos de vídeo?

* É necessária uma conexão com a Internet nos reprodutores para sincronizar as telas com os servidores do AEM?

* Quando o conteúdo dos reprodutores é atualizado?

* Se estiver executando vídeos, compreenda as especificações do seu dispositivo, para que o conteúdo seja exibido corretamente.

* Com base nas considerações ambientais acima, o armazenamento em estado sólido ou em disco rígido é mais apropriado?

* Determine qual capacidade de armazenamento você precisa e quais são seus requisitos de desempenho de armazenamento? Alguns exemplos:
   * Você tem considerações especiais sobre armazenamento (várias unidades, dispositivos de inicialização versus armazenamento em massa)?
   * Quais são seus requisitos de capacidade de RAM?


>[!NOTE]
>
>Também é importante validar as especificações do hardware selecionado para garantir que ele possa dar suporte ao aplicativo que está sendo desenvolvido. Por exemplo, se o aplicativo tiver a intenção de executar cinco vídeos de alta definição ao mesmo tempo, o hardware suporta esse recurso?
