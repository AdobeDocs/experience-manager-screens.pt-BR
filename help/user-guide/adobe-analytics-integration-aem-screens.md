---
title: Integração do Adobe Analytics com AEM Screens
seo-title: Integração do Adobe Analytics com AEM Screens
description: Siga esta página para saber mais sobre a integração imediata de AEM Screens com a Adobe Analytics e fornecer uma prova.
seo-description: Siga esta página para saber mais sobre a integração imediata de AEM Screens com a Adobe Analytics e fornecer uma prova.
uuid: 80d61af7-bf4d-46ca-a026-99a666c2e1a0
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
discoiquuid: b1a0e00e-0368-42c9-8bcd-5f00b4d0990c
docset: aem65
translation-type: tm+mt
source-git-commit: f25176be89424059b8c51296969f069687328536
workflow-type: tm+mt
source-wordcount: '684'
ht-degree: 2%

---


# Integração do Adobe Analytics com AEM Screens {#adobe-analytics-integration-with-aem-screens}

>[!CAUTION]
>
>Esta funcionalidade de AEM Screens só estará disponível se você tiver instalado o AEM 6.4.2 Feature Pack 2 e o AEM 6.3.3 Feature Pack 4.

>[!NOTE]
>
>Para obter acesso a qualquer um desses Pacotes de recursos, entre em contato com o Suporte da Adobe e solicite acesso. Com as devidas permissões, você pode baixá-lo em Compartilhamento de pacotes.

Esta seção aborda os seguintes tópicos:

* **Visão geral**
* **Detalhes da arquitetura**
* **Configuração das propriedades**

## Visão geral {#overview}

***Os AEM Screens*** aproveitam o Adobe Analytics e, com isso, você pode alcançar algo único no mercado - análises entre canais que ajudam a correlacionar o conteúdo mostrado no local com outras fontes de dados.

O AEM Screens fornece uma integração pronta para uso com o Adobe Analytics e oferece uma prova.

Esta seção descreve a seguinte funcionalidade envolvida na conexão de um projeto de AEM Screens com a Adobe Analytics:

* Permite prova de relatórios por dispositivo
* Permite a prova do relatórios play por ativo
* Garante que todos os eventos do player sejam capturados e com carimbo de data e hora
* Garante que todos os eventos do player sejam armazenados localmente se a reprodução não estiver conectada a uma rede
* Permite criar loops de feedback que rastreiam eventos de play ao longo do tempo
* Permite que o sistema modifique conteúdo e layouts com base em critérios de sucesso definidos pelo autor do conteúdo

Assim, a integração do Adobe Analytics com AEM Screens impõe os seguintes *objetivos*:

* Ativar o ROI das implementações de sinalização digital
* Integrar a Analytics como base para a futura ativação da coleta e análise de informações de uso

## Detalhes da arquitetura {#architectural-details}

Os clientes de um AEM Screens desejam entender qual conteúdo foi exibido em que hora e por quanto tempo (agregado). Essa é a capacidade comum da solução de sinalização. Em vez de criar nossa própria análise, os AEM Screens aproveitarão a Adobe Analytics e, com isso, podemos alcançar algo único no mercado - análises entre canais que ajudam a correlacionar o conteúdo mostrado no local com outras fontes de dados.

O diagrama de arquitetura a seguir explica a integração do Adobe Analytics com AEM Screens:

![screen_shot_2018-09-12at85611am](assets/screen_shot_2018-09-12at85611am.png)

## Ativação do Adobe Analytics em AEM Screens {#enabling-adobe-analytics-in-aem-screens}

As configurações do Adobe Analytics podem ser configuradas no console OSGi.

Navegue até Configuração **do console da Web do** Adobe Experience Manager para configurar o Adobe Analytics para AEM Screens, como mostrado na figura abaixo:

![screen_shot_2018-09-04at25550pm](assets/screen_shot_2018-09-04at25550pm.png)

## Screens Analytics: Fluxo de ativação {#screens-analytics-enablement-flow}

>[!CAUTION]
>
>Antes de configurar as propriedades, entre em contato com seu Gerente de relacionamento da Adobe para criar um ticket para obter uma chave **da API do** Analytics e um projeto **do** Analytics para uso com AEM Screens.

![]()

### Configuração das propriedades {#configuring-the-properties}

>[!CAUTION]
>
>Antes de configurar as propriedades, entre em contato com seu Gerente de relacionamento da Adobe para criar um ticket para obter uma chave **da API do** Analytics e um projeto **do** Analytics para uso com AEM Screens.

A tabela a seguir destaca as propriedades com sua descrição para configurar o Adobe Analytics para AEM Screens:

<table>
 <tbody>
  <tr>
   <td><strong>Propriedade</strong></td>
   <td><strong>Descrição</strong></td>
  </tr>
  <tr>
   <td><strong>URL Analytics</strong></td>
   <td>URL para publicar dados de análise do player. <br>
   Para desenvolvimento/estágio</em> - https://cc-api-data-stage.adobe.io/ingest/<br /> <em>For Production</em> - https://cc-api-data.adobe.io/ingest/</em><br /> <br /></td>
  </tr>
  <tr>
   <td><strong>Chave de API do Analytics</strong></td>
   <td>Chave da API para autenticação no servidor Adobe Analytics (fornecida pelo Gerenciador de contas).</td>
  </tr>
  <tr>
   <td><strong>Projeto Analytics</strong></td>
   <td>Projeto de AEM Screens configurado em sua análise para receber dados (fornecido pelo Gerente de contas).</td>
  </tr>
  <tr>
   <td><strong>Autor</strong></td>
   <td><p>Estágio ou ambiente de produção (escolha Estágio ou Produção).</p></td>
  </tr>
  <tr>
   <td><strong>Frequência de envio do Analytics</strong></td>
   <td>Frequência em minutos para enviar dados de análise dos players. Por padrão, é definido como 15 minutos.</td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>Por padrão, a Frequência **de envio do** Analytics é de 15 minutos.

#### Uso do Adobe Analytics Service em AEM Screens {#using-adobe-analytics-service-in-aem-screens}

Esse cenário chama a API do Analytics por meio de chamadas REST de um serviço de análise no firmware e nos componentes de núcleo de telas de instrumentos para criar e enviar explicitamente eventos específicos para um caso de uso específico e permitir a extensibilidade em que qualquer mensagem personalizada pode ser enviada para a Analytics a partir de um canal desenvolvido personalizado.

Os eventos Analytics são armazenados offline no indexedDB e depois são separados e enviados para a nuvem.

>[!NOTE]
>
>Para saber mais sobre o ***Sequenciamento*** e o Modelo de Dados ***Padrão para Eventos***, consulte **[Configuração do Adobe Analytics para AEM Screens](configuring-adobe-analytics-aem-screens.md)**.

