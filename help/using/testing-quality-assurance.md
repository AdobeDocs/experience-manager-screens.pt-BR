---
title: Teste e garantia da qualidade
seo-title: Teste e garantia de qualidade para o AEM Screens
description: A página descreve o Guia de práticas recomendadas de teste e garantia de qualidade para o AEM Screens
seo-description: A página descreve o Guia de práticas recomendadas de teste e garantia de qualidade para o AEM Screens
translation-type: tm+mt
source-git-commit: 12b1cc4f2b359742966c2073d233b0113459e2de

---


# Teste e garantia da qualidade {#testing-quality}

>[!NOTE]
>
>A parte interessada típica desta atividade é um Integrador A/V.

À medida que nos aproximamos da implantação real da rede de sinalização digital, devemos criar um Plano de controle de qualidade e teste que aborde todos os elementos da rede, incluindo todos os componentes de hardware, todos os componentes de software e todos os componentes da rede.
Nesta fase, todos os sistemas de ensaio devem ser construídos e completamente testados.

Deve ser criada uma lista de verificação que identifique todos os KPIs previamente definidos e meça o material para distribuição em relação a eles.

Devem ser considerados os seguintes elementos:

## 1. Considerações mecânicas {#mechanical-considerations}

As seguintes considerações mecânicas são recomendadas:

* montagem da tela
* montagem do player
* ventilação
* anexos periféricos
* gerenciamento de cabos
* rede de dispositivos

## 2. Considerações sobre software {#software-considerations}

As seguintes considerações de software são recomendadas:

* registro do dispositivo
* publicação de mídia
* reprodução
* dependências do banco de dados (definidas anteriormente)

>[!NOTE]
> Essa fase também deve ser usada como uma ferramenta para a criação de um guia de instalação e de usuário que possa ser enviado posteriormente com o equipamento e mantido no local para futura referência.

## 3. Considerações sobre o gerenciamento de dispositivos {#device-management-considerations}


O AEM Screens inclui um módulo do Device Control Center que permite o gerenciamento de pontos finais do aplicativo do player do Screens.

Refere-se a qualquer dispositivo de hardware do *player* que tenha o aplicativo do player do Screens instalado e esteja registrado para uma instância do AEM.
Este módulo permite:

1. Monitorar registros de erros do aplicativo
1. Gerenciar capturas de tela remota
1. Gerenciar downloads de conteúdo
1. Reinicialização do aplicativo

>[!CAUTION]
> VOCÊ NÃO DEVE USAR O Device Control Center PARA:
>
> 1. Instalar novas versões do aplicativo do player
> 1. Monitorar recursos no nível do sistema
> 1. Configurar configurações no nível do sistema
> 1. Permita a intervenção remota da área de trabalho.



>[!NOTE]
> A Adobe recomenda que as plataformas dedicadas de gerenciamento de dispositivos de terceiros sejam usadas para todas as implantações.

A plataforma específica escolhida depende de vários fatores, incluindo o sistema ***operacional de*** destino, os requisitos ***do*** projeto e o ***número de pontos*** finais.

Poucos exemplos são:

* Gerenciamento de dispositivos Google Chrome
* TeamViewer
* AirWatch42
* Ursos
* Soti