---
title: Teste e garantia da qualidade
seo-title: Testing and Quality Assurance for AEM Screens
description: A página descreve o Guia de práticas recomendadas de controle de qualidade e teste do AEM Screens
seo-description: The page describes Testing and Quality Assurance for AEM Screens Best Practices Guide
exl-id: cc3bfb88-1341-43f8-b247-6a41f1d1a963
source-git-commit: 707833ddd8ab2573abcac4e9a77ec88778624435
workflow-type: tm+mt
source-wordcount: '341'
ht-degree: 2%

---

# Teste e garantia da qualidade {#testing-quality}

>[!NOTE]
>Uma parte interessada típica dessa atividade é um Integrador de A/V.

À medida que nos aproximamos da implantação real da rede de sinalização digital, devemos criar um Plano de Teste e Controle de qualidade que atenda a cada elemento da rede, incluindo todos os componentes de hardware, todos os componentes de software e todos os componentes de rede.
Na fase inicial, todos os sistemas de teste devem ser construídos e totalmente testados.

Uma lista de verificação deve ser criada para identificar todos os KPIs definidos anteriormente e medir o produto em relação a eles.

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

O AEM Screens inclui um módulo do Centro de controle de dispositivos que permite o gerenciamento dos pontos de extremidade do aplicativo do reprodutor do Screens.

Refere-se a qualquer *reprodutor* dispositivo de hardware que tem o aplicativo reprodutor do Screens instalado e está registrado em uma instância de AEM.
Esse módulo permite:

1. Monitorar logs de erros de aplicativos de reprodução
1. Gerenciar capturas de tela remotas
1. Gerenciar downloads de conteúdo
1. Gerenciar problemas de reinicialização do aplicativo

Para saber mais detalhes sobre ***Centro de controle de dispositivos***, consulte [Solução de problemas do Centro de controle de dispositivos](https://helpx.adobe.com/experience-manager/6-5/screens/using/monitoring-screens.html) in **Guia do usuário do AEM Screens**.

>[!CAUTION]
>
> Você não deve usar o Centro de controle de dispositivos para:
> 1. Instalar novas versões do aplicativo de reprodução
> 1. Monitorar recursos no nível do sistema
> 1. Solução de problemas de erros no nível do sistema
> 1. Permitir intervenção de área de trabalho remota



>[!NOTE]
>
> A Adobe recomenda que plataformas dedicadas de gerenciamento de dispositivos de terceiros sejam usadas para todas as implantações.

A plataforma específica escolhida depende de vários fatores, incluindo a ***sistema operacional de destino***, ***requisitos do projeto*** e ***número de pontos finais***.

Alguns exemplos são:

* Gerenciamento de dispositivos do Google Chrome
* TeamViewer
* AirWatch
* 42Gears
* Middleware do integrador de AV proprietário
