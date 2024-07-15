---
title: Teste e garantia da qualidade
description: Saiba mais sobre testes e controle de qualidade para o AEM Screens no Guia de práticas recomendadas.
exl-id: cc3bfb88-1341-43f8-b247-6a41f1d1a963
source-git-commit: 2a51258ffe7b969962378dcd0558bd001b616ba1
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 0%

---

# Teste e garantia da qualidade {#testing-quality}

>[!NOTE]
>Uma parte interessada típica dessa atividade é um Integrador de áudio e vídeo.

À medida que você se aproximar da implantação da rede de sinalização digital, crie um plano de Teste e Controle de qualidade que aborde cada elemento da rede, incluindo todos os componentes de hardware, todos os componentes de software e todos os componentes de rede.
Na fase inicial, todos os sistemas de teste devem ser construídos e totalmente testados.

Uma lista de verificação deve ser criada para identificar todos os KPIs definidos anteriormente e medir os resultados em relação a eles.

>[!NOTE]
>
>Esta fase também deve ser usada como uma ferramenta para criar uma instalação e um guia do usuário. Ambos podem ser enviados posteriormente com o equipamento e mantidos no local para referência futura.

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

O AEM Screens inclui um módulo do Centro de controle de dispositivos que permite o gerenciamento de endpoints de aplicativos do Screens Player.

Refere-se a qualquer dispositivo de hardware *player* que tenha o aplicativo Screens player instalado e esteja registrado para uma instância do AEM.
Esse módulo permite:

1. Monitorar logs de erros de aplicativos de reprodução
1. Gerenciar capturas de tela remotas
1. Gerenciar downloads de conteúdo
1. Gerenciar problemas de reinicialização do aplicativo

Para saber mais detalhes sobre o ***Centro de Controle de Dispositivo***, consulte o [Centro de Controle de Dispositivo](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/troubleshooting/monitoring-screens) no **Guia do Usuário do AEM Screens**.

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
