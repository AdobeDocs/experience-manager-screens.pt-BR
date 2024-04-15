---
title: Teste e garantia da qualidade
description: Saiba mais sobre testes e controle de qualidade para o AEM Screens no Guia de práticas recomendadas.
exl-id: cc3bfb88-1341-43f8-b247-6a41f1d1a963
source-git-commit: 3c4b37b3b9f268b500562fa4ce3782b7be1e7d74
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 0%

---

# Teste e garantia da qualidade {#testing-quality}

>[!NOTE]
>Uma parte interessada típica dessa atividade é um Integrador de áudio/vídeo.

À medida que você se aproximar da implantação da rede de sinalização digital, crie um plano de Teste e Controle de qualidade que aborde cada elemento da rede, incluindo todos os componentes de hardware, todos os componentes de software e todos os componentes de rede.
Na fase inicial, todos os sistemas de teste devem ser construídos e totalmente testados.

Uma lista de verificação deve ser criada para identificar todos os KPIs definidos anteriormente e medir os resultados em relação a eles.

>[!NOTE]
>
>Essa fase também deve ser usada como uma ferramenta para criar um guia de instalação e usuário que pode ser enviado posteriormente com o equipamento e mantido no local para referência futura.

Devem ser considerados os seguintes elementos:

## 1. Considerações mecânicas {#mechanical-considerations}

Recomendam-se as seguintes considerações mecânicas:

* montagem do monitor
* montagem do reprodutor
* ventilação
* anexos periféricos
* gerenciamento de cabos
* rede do dispositivo

## 2. Considerações sobre software {#software-considerations}

As seguintes considerações de software são recomendadas:

* registro do dispositivo
* publicação de mídia
* reprodução
* dependências do banco de dados (definidas anteriormente)


## 3. Considerações sobre o gerenciamento de dispositivos {#device-management-considerations}

O AEM Screens inclui um módulo do Centro de controle de dispositivos que permite o gerenciamento de pontos de extremidade do aplicativo do reprodutor do Screens.

Refere-se a qualquer *reprodutor* dispositivo de hardware que tem o aplicativo reprodutor do Screens instalado e está registrado em uma instância de AEM.
Esse módulo permite:

1. Monitorar logs de erros de aplicativos de reprodução
1. Gerenciar capturas de tela remotas
1. Gerenciar downloads de conteúdo
1. Gerenciar problemas de reinicialização do aplicativo

Para saber mais detalhes sobre ***Centro de controle de dispositivos***, consulte [Solução de problemas do Centro de controle de dispositivos](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/troubleshooting/monitoring-screens) in **Guia do usuário do AEM Screens**.

>[!CAUTION]
>
>Não use o Centro de Controle do Dispositivo para:
>
>* Instalar novas versões do aplicativo de reprodução
>* Monitorar recursos no nível do sistema
>* Solução de problemas de erros no nível do sistema
>* Permitir intervenção de área de trabalho remota


>[!NOTE]
>
> A Adobe recomenda que plataformas dedicadas de gerenciamento de dispositivos de terceiros sejam usadas para todas as implantações.

A plataforma específica escolhida depende de vários fatores, incluindo o ***sistema operacional de destino***, ***requisitos do projeto***, e ***número de pontos finais***.

Veja a seguir alguns exemplos:

* Gerenciamento de dispositivos do Google Chrome
* TeamViewer
* AirWatch
* `42Gears`
* Middleware do integrador de áudio/vídeo proprietário
