---
title: Assurance de teste e qualidade
description: Saiba mais sobre testes e controle de qualidade para o AEM Screens no Guia de práticas recomendadas.
exl-id: cc3bfb88-1341-43f8-b247-6a41f1d1a963
TQID: https://experienceleague.adobe.com/So83gHv7n21zhdoCdWHVf0yswyQuSr1hLWmCA7uHSiE
product_v2:
  - id: a27b4747-2f72-4fb7-9936-be5d11dd2c4a
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
topic_v2:
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
source-git-commit: d4664dd5678eaccabe656398c437dca264d4675e
workflow-type: tm+mt
source-wordcount: 376
ht-degree: 0%

---

# Assurance de teste e qualidade {#testing-quality}

>[!IMPORTANT]
>Esse conteúdo é válido para o AEM no local/AMS (AEM 6.5LTS e AEM 6.5). Para ver o conteúdo do AEM as a Cloud Service Screens, consulte o [guia do AEM as a Cloud Service](https://experienceleague.adobe.com/pt-br/docs/experience-manager-cloud-service/content/screens-as-cloud-service/overview/introduction).

>[!NOTE]
>Uma parte interessada típica dessa atividade é um Integrador de áudio e vídeo.

À medida que você se aproximar da implantação da rede de sinalização digital, crie um plano de Teste e Controle de qualidade que aborde cada elemento da rede, incluindo todos os componentes de hardware, todos os componentes de software e todos os componentes de rede.
Na fase inicial, todos os sistemas de teste devem ser construídos e totalmente testados.

Uma lista de verificação deve ser criada para identificar todos os KPIs definidos anteriormente e medir os resultados em relação a eles.

>[!NOTE]
>
>Esta fase também deve ser usada como uma ferramenta para criar uma instalação e um guia do usuário. Ambos podem ser enviados posteriormente com o equipamento e mantidos no local para referência futura.

Devem ser considerados os seguintes elementos:

## &#x200B;1. Considerações mecânicas {#mechanical-considerations}

Recomendam-se as seguintes considerações mecânicas:

* montagem do monitor
* montagem do reprodutor
* ventilação
* anexos periféricos
* gerenciamento de cabos
* rede do dispositivo

## &#x200B;2. Considerações sobre software {#software-considerations}

As seguintes considerações de software são recomendadas:

* registro do dispositivo
* publicação de mídia
* reprodução
* dependências do banco de dados (definidas anteriormente)


## &#x200B;3. Considerações sobre o gerenciamento de dispositivos {#device-management-considerations}

O AEM Screens inclui um módulo do Centro de controle de dispositivos que permite o gerenciamento de endpoints de aplicativos do Screens Player.

Refere-se a qualquer dispositivo de hardware *player* que tenha o aplicativo Screens player instalado e esteja registrado em uma instância do AEM.
Esse módulo permite:

1. Monitorar logs de erros de aplicativos de reprodução
1. Gerenciar capturas de tela remotas
1. Gerenciar downloads de conteúdo
1. Gerenciar problemas de reinicialização do aplicativo

Para saber mais detalhes sobre o ***Centro de Controle de Dispositivo***, consulte o [Centro de Controle de Dispositivo](https://experienceleague.adobe.com/pt-br/docs/experience-manager-screens/user-guide/troubleshooting/monitoring-screens) no **Guia do Usuário do AEM Screens**.

>[!CAUTION]
>
>Não use o Centro de controle de dispositivos para:
>
>* Instalar novas versões do aplicativo de reprodução
>* Monitorar recursos no nível do sistema
>* Solução de problemas de erros no nível do sistema
>* Permitir intervenção de área de trabalho remota


>[!NOTE]
>
> A Adobe recomenda que plataformas dedicadas de gerenciamento de dispositivos de terceiros sejam usadas para todas as implantações.

A plataforma específica escolhida depende de vários fatores, incluindo o ***sistema operacional de destino***, os ***requisitos do projeto*** e o ***número de pontos de extremidade***.

Veja a seguir alguns exemplos:

* Gerenciamento de dispositivos do Google Chrome
* TeamViewer
* AirWatch
* `42Gears`
* Middleware do integrador de áudio e vídeo proprietário
