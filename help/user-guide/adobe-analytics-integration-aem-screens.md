---
title: Integração da Adobe Analytics com a AEM Screens
seo-title: Integração da Adobe Analytics com a AEM Screens
description: Siga esta página para saber mais sobre a integração imediata do AEM Screens com o Adobe Analytics e fornecer uma prova do jogo.
seo-description: Siga esta página para saber mais sobre a integração imediata do AEM Screens com o Adobe Analytics e fornecer uma prova do jogo.
uuid: 80d61af7-bf4d-46ca-a026-99a666c2e1a0
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
discoiquuid: b1a0e00e-0368-42c9-8bcd-5f00b4d0990c
docset: aem65
translation-type: tm+mt
source-git-commit: 2a3bbdd283f983cbdb5f21b606f508603385e041
workflow-type: tm+mt
source-wordcount: '684'
ht-degree: 2%

---


# Integração do Adobe Analytics com o AEM Screens {#adobe-analytics-integration-with-aem-screens}

>[!CAUTION]
>
>Esta funcionalidade do AEM Screens só estará disponível se você tiver instalado AEM 6.4.2 Feature Pack 2 e AEM 6.3.3 Feature Pack 4.

>[!NOTE]
>
>Para obter acesso a qualquer um desses Pacotes de recursos, entre em contato com o Suporte ao Adobe e solicite acesso. Com as devidas permissões, você pode baixá-lo em Compartilhamento de pacotes.

Esta seção aborda os seguintes tópicos:

* **Visão geral**
* **Detalhes da arquitetura**
* **Configuração das propriedades**

## Visão geral {#overview}

***AEM*** Screenstiram a Adobe Analytics e, com isso, você pode alcançar algo único no mercado - análises entre canais que ajudam a correlacionar o conteúdo mostrado no local com outras fontes de dados.

A AEM Screens oferece uma integração pronta para uso com a Adobe Analytics e oferece uma prova.

Esta seção descreve a seguinte funcionalidade envolvida na conexão de um projeto da AEM Screens com a Adobe Analytics:

* Permite prova de relatórios por dispositivo
* Permite a prova do relatórios play por ativo
* Garante que todos os eventos do player sejam capturados e com carimbo de data e hora
* Garante que todos os eventos do player sejam armazenados localmente se a reprodução não estiver conectada a uma rede
* Permite criar loops de feedback que rastreiam eventos de play ao longo do tempo
* Permite que o sistema modifique conteúdo e layouts com base em critérios de sucesso definidos pelo autor do conteúdo

Assim, a integração da Adobe Analytics com a AEM Screens impõe os seguintes *objetivos*:

* Ativar o ROI das implementações de sinalização digital
* Integrar o Analytics como base para a futura ativação de coletar e analisar informações de uso

## Detalhes da arquitetura {#architectural-details}

Os clientes da AEM Screens querem entender qual conteúdo foi exibido em que hora e por quanto tempo (agregado). Essa é a capacidade comum da solução de sinalização. Em vez de criar nossa própria análise, a AEM Screens aproveitará a Adobe Analytics e, com isso, podemos alcançar algo único no mercado - análises entre canais que ajudam a correlacionar o conteúdo mostrado no local com outras fontes de dados.

O diagrama de arquitetura a seguir explica a integração do Adobe Analytics com o AEM Screens:

![screen_shot_2018-09-12at85611am](assets/screen_shot_2018-09-12at85611am.png)

## Habilitar Adobe Analytics no AEM Screens {#enabling-adobe-analytics-in-aem-screens}

As configurações do Adobe Analytics podem ser configuradas no console OSGi.

Navegue até **Configuração do Adobe Experience Manager Web Console** para configurar o Adobe Analytics para AEM Screens, conforme mostrado na figura abaixo:

![screen_shot_2018-09-04at25550pm](assets/screen_shot_2018-09-04at25550pm.png)

## Análises de telas: Fluxo de ativação {#screens-analytics-enablement-flow}

>[!CAUTION]
>
>Antes de configurar as propriedades, entre em contato com seu Gerente de relacionamentos de Adobe para criar um ticket para obter uma **Chave de API do Analytics** e **Projeto do Analytics** para uso com a AEM Screens.

![]()

### Configuração das propriedades {#configuring-the-properties}

>[!CAUTION]
>
>Antes de configurar as propriedades, entre em contato com seu Gerente de relacionamentos de Adobe para criar um ticket para obter uma **Chave de API do Analytics** e **Projeto do Analytics** para uso com a AEM Screens.

A tabela a seguir destaca as propriedades com sua descrição para configurar o Adobe Analytics para AEM Screens:

<table>
 <tbody>
  <tr>
   <td><strong>Propriedade</strong></td>
   <td><strong>Descrição</strong></td>
  </tr>
  <tr>
   <td><strong>URL do Analytics</strong></td>
   <td>URL para publicar dados de análise do player. <br>
   Para desenvolvimento/estágio</em>  - https://cc-api-data-stage.adobe.io/ingest/<br /> <em>For Production</em>  - https://cc-api-data.adobe.io/ingest/</em><br /> <br /></td>
  </tr>
  <tr>
   <td><strong>Chave da API do Analytics</strong></td>
   <td>Chave da API para autenticação no servidor Adobe Analytics (fornecida pelo Gerenciador de contas).</td>
  </tr>
  <tr>
   <td><strong>Projeto do Analytics</strong></td>
   <td>Projeto da AEM Screens configurado em sua análise para receber dados (fornecido pelo Gerente de contas).</td>
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
>Por padrão, a **Frequência de envio do Analytics** é de 15 minutos.

#### Uso do Adobe Analytics Service no AEM Screens {#using-adobe-analytics-service-in-aem-screens}

Esse cenário chama a API do Analytics por meio de chamadas REST de um serviço de análise no firmware e nos componentes principais das telas de instrumentos para criar e enviar explicitamente eventos específicos para um caso de uso específico e permitir a extensibilidade em que qualquer mensagem personalizada pode ser enviada ao Analytics a partir de um canal desenvolvido personalizado.

Os eventos do Analytics são armazenados offline no indexedDB e posteriormente são separados e enviados para a nuvem.

>[!NOTE]
>
>Para saber mais sobre o ***Sequenciamento*** e o ***Modelo de Dados Padrão para Eventos***, consulte **[Configuração do Adobe Analytics para AEM Screens](configuring-adobe-analytics-aem-screens.md)**.

