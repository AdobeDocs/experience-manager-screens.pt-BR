---
title: Integração do Adobe Analytics com o AEM Screens
seo-title: Integração do Adobe Analytics com o AEM Screens
description: Siga esta página para saber mais sobre a integração do AEM Screens com o Adobe Analytics pronta para uso e fornecer uma prova de reprodução.
seo-description: Siga esta página para saber mais sobre a integração do AEM Screens com o Adobe Analytics pronta para uso e fornecer uma prova de reprodução.
uuid: 80d61af7-bf4d-46ca-a026-99a666c2e1a0
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
discoiquuid: b1a0e00e-0368-42c9-8bcd-5f00b4d0990c
docset: aem65
feature: Administração do Screens
role: Admin, Developer
level: Intermediate
exl-id: 92c8c42b-7c1e-4d4a-8662-18c99666e9c6
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '704'
ht-degree: 0%

---

# Integração do Adobe Analytics com o AEM Screens {#adobe-analytics-integration-with-aem-screens}

>[!CAUTION]
>
>Essa funcionalidade do AEM Screens só estará disponível se você tiver instalado a versão mínima do AEM 6.4.2 Feature Pack 2 ou AEM 6.3.3 Feature Pack 4.

>[!NOTE]
>
>Para obter acesso a um desses Pacotes de recursos, entre em contato com o Suporte do Adobe e solicite acesso. Você pode baixar o pacote de recursos mais recente do AEM Screens no [Portal de distribuição de software](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html) usando sua Adobe ID.

Esta seção aborda os seguintes tópicos:

* **Visão geral**
* **Detalhes da arquitetura**
* **Configuração das propriedades**

## Visão geral {#overview}

***O AEM*** Screens utiliza o Adobe Analytics e, com isso, você pode alcançar algo único no mercado - análises entre canais que ajudam a correlacionar o conteúdo mostrado no local com outras fontes de dados.

O AEM Screens fornece uma integração pronta para uso com o Adobe Analytics e fornece uma prova de reprodução.

Esta seção descreve a seguinte funcionalidade envolvida com a conexão de um projeto do AEM Screens com o Adobe Analytics:

* Permite relatórios de prova de reprodução por dispositivo
* Permite relatórios de prova de reprodução por ativo
* Garante que todos os eventos do player sejam capturados e com carimbo de data e hora
* Garante que todos os eventos do player sejam armazenados localmente se a reprodução não estiver conectada a uma rede
* Permite a criação de loops de comentários que rastreiam eventos de reprodução ao longo do tempo
* Permite que o sistema modifique conteúdo e layouts com base em critérios de sucesso definidos pelo autor de conteúdo

A integração do Adobe Analytics com o AEM Screens aplica as seguintes *metas*:

* Ativar o ROI das implementações de sinalização digital
* Integrar o Analytics como base para a ativação futura de coletar e analisar informações de uso

## Detalhes da arquitetura {#architectural-details}

Um cliente da AEM Screens deseja entender qual conteúdo foi exibido em que momento e por quanto tempo (agregado). Esse é um recurso comum da solução de sinalização. Em vez de criar nossa própria análise, a AEM Screens aproveitará o Adobe Analytics e, com isso, podemos alcançar algo único no mercado - análises entre canais que ajudam a correlacionar o conteúdo mostrado na localização com outras fontes de dados.

O diagrama de arquitetura a seguir explica a Integração do Adobe Analytics com o AEM Screens:

![screen_shot_2018-09-12at85611am](assets/screen_shot_2018-09-12at85611am.png)

## Ativação do Adobe Analytics no AEM Screens {#enabling-adobe-analytics-in-aem-screens}

As configurações do Adobe Analytics podem ser definidas no console OSGi.

Navegue até **Configuração do Adobe Experience Manager Web Console** para configurar o Adobe Analytics para AEM Screens, conforme mostrado na figura abaixo:

![screen_shot_2018-09-04at25550pm](assets/screen_shot_2018-09-04at25550pm.png)

## Análise do Screens: Fluxo de ativação {#screens-analytics-enablement-flow}

>[!CAUTION]
>
>Antes de configurar as propriedades, entre em contato com o Gerente de relacionamento do Adobe para criar um tíquete para obter uma **Chave da API do Analytics** e **Projeto do Analytics** para uso com o AEM Screens.

![]()

### Configuração das propriedades {#configuring-the-properties}

>[!CAUTION]
>
>Antes de configurar as propriedades, entre em contato com o Gerente de relacionamento do Adobe para criar um tíquete para obter uma **Chave da API do Analytics** e **Projeto do Analytics** para uso com o AEM Screens.

A tabela a seguir destaca as propriedades com sua descrição para configurar o Adobe Analytics para AEM Screens:

<table>
 <tbody>
  <tr>
   <td><strong>Propriedade</strong></td>
   <td><strong>Descrição</strong></td>
  </tr>
  <tr>
   <td><strong>URL do Analytics</strong></td>
   <td>URL para publicar dados de análise do reprodutor. <br>
   Para desenvolvimento/estágio</em>  - https://cc-api-data-stage.adobe.io/ingest/<br /> <em>Para produção</em>  - https://cc-api-data.adobe.io/ingest/</em><br /> <br /></td>
  </tr>
  <tr>
   <td><strong>Chave da API do Analytics</strong></td>
   <td>Chave da API para autenticar no servidor do Adobe Analytics (fornecida pelo Gerente de contas).</td>
  </tr>
  <tr>
   <td><strong>Projeto do Analytics</strong></td>
   <td>Projeto do AEM Screens configurado em sua análise para receber dados (fornecido pelo Gerente de contas).</td>
  </tr>
  <tr>
   <td><strong>Autor</strong></td>
   <td><p>Ambiente de preparo ou produção (escolha Estágio ou Produção).</p></td>
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

#### Usar o Adobe Analytics Service no AEM Screens {#using-adobe-analytics-service-in-aem-screens}

Esse cenário chama a API do Analytics por meio de chamadas REST de um serviço de análise nos componentes principais de tela de firmware e instrumento para criar e enviar explicitamente eventos específicos a um caso de uso específico, permitindo a extensibilidade em que qualquer mensagem personalizada pode ser enviada para o Analytics a partir de um canal desenvolvido personalizado.

Os eventos do Analytics são armazenados offline no indexedDB e, posteriormente, são fragmentados e enviados para a nuvem.

>[!NOTE]
>
>Para saber mais sobre o ***Sequenciamento*** e ***Modelo de Dados Padrão para Eventos***, consulte **[Configuração do Adobe Analytics para AEM Screens](configuring-adobe-analytics-aem-screens.md)**.
