---
title: Teste e garantia da qualidade
seo-title: Teste e garantia de qualidade para AEM Screens
description: A página descreve o Guia de teste e garantia de qualidade para práticas recomendadas do AEM Screens
seo-description: A página descreve o Guia de teste e garantia de qualidade para práticas recomendadas do AEM Screens
source-git-commit: 4611dd40153ccd09d3a0796093157cd09a8e5b80
workflow-type: tm+mt
source-wordcount: '361'
ht-degree: 2%

---


# Teste e garantia da qualidade {#testing-quality}

>[!NOTE]
>A parte interessada típica dessa atividade é um Integrador de A/V.

À medida que nos aproximamos da implantação real da rede de sinalização digital, devemos criar um plano de teste e controle de qualidade que aborde todos os elementos da rede, incluindo todos os componentes de hardware, todos os componentes de software e todos os componentes de rede.
Nesta fase, devem ser construídos e totalmente testados sistemas de ensaio completos.

Deve ser criada uma lista de verificação que identifique todos os KPIs definidos anteriormente e meça o delivery em relação a eles.

>[!NOTE]
>
>Esta fase também deve ser usada como ferramenta para criar um guia de instalação e de usuário que possa ser enviado posteriormente com o equipamento e mantido no local para referência futura.

Devem ser considerados os seguintes elementos:

## 1. Considerações Mecânicas {#mechanical-considerations}

Recomenda-se o seguinte critério mecânico:

* montagem da tela
* montagem do reprodutor
* ventilação
* anexos periféricos
* gerenciamento de cabos
* rede de dispositivos

## 2. Considerações sobre software {#software-considerations}

As considerações de software a seguir são recomendadas:

* registro do dispositivo
* publicação de mídia
* reprodução
* dependências do banco de dados (definidas anteriormente)


## 3. Considerações sobre o gerenciamento de dispositivos {#device-management-considerations}

O AEM Screens inclui um módulo do Device Control Center que permite o gerenciamento de pontos finais do aplicativo do player do Screens.

Refere-se a qualquer dispositivo de hardware *player* que tenha o aplicativo do player do Screens instalado e esteja registrado em uma instância de AEM.
Esse módulo permite:

1. Monitorar registros de erros do aplicativo do player
1. Gerenciar capturas de tela remota
1. Gerenciar downloads de conteúdo
1. Gerenciar problemas de reinicialização do aplicativo

Para saber mais detalhes sobre o ***Device Control Center***, consulte [Troubleshooting Device Control Center](https://helpx.adobe.com/experience-manager/6-5/screens/using/monitoring-screens.html) em **AEM Screens User Guide**.

>[!CAUTION]
>
> Você não deve usar o Device Control Center para:
> 1. Instalar novas versões do aplicativo do reprodutor
> 1. Monitorar recursos no nível do sistema
> 1. Solução de problemas de erros no nível do sistema
> 1. Permitir intervenção remota de ambiente de trabalho



>[!NOTE]
>
> O Adobe recomenda que as plataformas dedicadas de gerenciamento de dispositivos de terceiros sejam usadas para todas as implantações.

A plataforma específica escolhida depende de vários fatores, incluindo o ***sistema operacional de destino***, ***requisitos do projeto*** e ***número de pontos finais***.

São poucos os exemplos:

* Gerenciamento de dispositivos do Google Chrome
* TeamViewer
* AirWatch
* 42Artes
* Middleware proprietário do AV Integrator
