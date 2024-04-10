---
title: Configuração do Adobe Analytics com AEM Screens
description: Saiba mais sobre sequenciamento e envio de eventos personalizados usando o Adobe Analytics offline.
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: developing
docset: aem65
feature: Administering Screens
role: Admin, Developer
level: Intermediate
exl-id: 4ecc1fb1-2437-449a-a085-66b2a85f4053
source-git-commit: c142830a37461a36baae15f543bd43b0ae8a62a7
workflow-type: tm+mt
source-wordcount: '614'
ht-degree: 10%

---

# Configuração do Adobe Analytics com AEM Screens {#configuring-adobe-analytics-with-aem-screens}

<!-- OBSOLETE NOTE>
>[!CAUTION]
>
>This AEM Screens functionality is only available if you have installed AEM 6.4.2 Feature Pack 2 and AEM 6.3.3 Feature Pack 4.
>
>To get access to either of these Feature Packs, you must contact Adobe Support and request access. Once you have permissions, download it from Package Share. -->

Esta seção abrange os seguintes tópicos:

* **Sequenciamento no Adobe Analytics com AEM Screens**
* **Envio De Eventos Personalizados Usando Adobe Analytics Offline**

## Sequenciamento no Adobe Analytics com AEM Screens {#sequencing-in-adobe-analytics-with-aem-screens}

A variável ***processo de sequenciamento*** começa com o serviço de armazenamento de dados que ativa o serviço Adobe Analytics. O conteúdo do canal envia eventos do Adobe Analytics com folha de pagamento, ou seja, a captura do teste de dados para o Windows I/O e os eventos de permanência são acionados. Os eventos são salvos no banco de dados de índice e são colocados no armazenamento de objetos. Com base no agendamento que o administrador define, ele corta os dados do armazenamento de objetos e os transfere posteriormente no armazenamento de partes. Ele tenta enviar a quantidade máxima de dados quando conectado.

### Diagrama de Sequenciamento {#sequencing-diagram}

O diagrama de sequenciamento a seguir explica a integração do Adobe Analytics com o AEM Screens:

![analytics_chunking](assets/analytics_chunking.png)

## Envio De Eventos Personalizados Usando Adobe Analytics Offline {#sending-custom-events-using-offline-adobe-analytics}

A tabela a seguir resume o modelo de dados padrão para eventos. Ele lista todos os campos enviados para o Adobe Analytics:

<table>
 <tbody>
  <tr>
   <td><strong>Seção</strong></td> 
   <td><strong>Rótulo da propriedade</strong></td> 
   <td><strong>Nome/chave da propriedade</strong></td> 
   <td><strong>Obrigatório</strong></td> 
   <td><strong>Tipo de dados</strong></td> 
   <td><strong>Tipo de propriedade</strong><br /> </td> 
   <td><strong>Descrição</strong></td> 
  </tr>
  <tr>
   <td><strong><em>Núcleo/Evento</em></strong></td> 
   <td>GUID do Evento</td> 
   <td>event.guid</td> 
   <td>recomendado</td> 
   <td>string</td> 
   <td>UUID</td> 
   <td>Identificador exclusivo que identifica a instância de um evento</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Data e hora da coleta do evento</td> 
   <td>event.coll_dts</td> 
   <td>opcional</td> 
   <td>string</td> 
   <td>carimbo de data e hora - UTC</td> 
   <td>Data e hora da coleta</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Data e hora do evento (início)</td> 
   <td>event.dts_start</td> 
   <td>recomendado</td> 
   <td>string</td> 
   <td>carimbo de data e hora - UTC</td> 
   <td>Data e hora de início do evento, se você não tiver especificado essa data, a hora do evento será considerada como a hora em que foi recebida pelo servidor</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Data e hora do evento (fim)</td> 
   <td>event.dts_end</td> 
   <td>opcional</td> 
   <td>string</td> 
   <td>carimbo de data e hora - UTC</td> 
   <td>Data e hora de conclusão do evento</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Fluxo de trabalho</td> 
   <td>event.workflow</td> 
   <td>recomendado</td> 
   <td>string</td> 
   <td> </td> 
   <td>Nome do fluxo de trabalho (Telas)</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Categoria DMe principal</td> 
   <td>event.category</td> 
   <td>obrigatório</td> 
   <td>string</td> 
   <td> </td> 
   <td>Categoria principal (DESKTOP, DISPOSITIVO MÓVEL, WEB, PROCESSO, SDK, SERVIÇO, ECOSSISTEMA) - Agrupamento de tipos de evento - <strong>Player enviado</strong></td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Subcategoria</td> 
   <td>event.subcategory</td> 
   <td>recomendado</td> 
   <td>string</td> 
   <td> </td> 
   <td>Subcategoria - Seção de um fluxo de trabalho, ou Área de uma tela e assim por diante. (Arquivos recentes, arquivos CC, criações móveis e assim por diante.)</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Tipo de evento/ação</td> 
   <td>event.type</td> 
   <td>obrigatório</td> 
   <td>string</td> 
   <td> </td> 
   <td>Tipo de evento (renderização, clique, pinça, zoom) - Ação do usuário principal</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Subtipo</td> 
   <td>event.subtype</td> 
   <td>recomendado</td> 
   <td>string</td> 
   <td> </td> 
   <td>Subtipo de evento (criar, atualizar, excluir, publicar etc.) - Mais detalhes da ação do usuário</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Offline</td> 
   <td>event.offline</td> 
   <td>opcional</td> 
   <td>booleano</td> 
   <td> </td> 
   <td>O evento foi gerado enquanto a ação estava offline/online (true/false)</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Agente do usuário</td> 
   <td>event.user_agent</td> 
   <td>recomendado (propriedades da web)</td> 
   <td>string</td> 
   <td> </td> 
   <td>Agente do usuário</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Idioma/Local</td> 
   <td>event.language</td> 
   <td>recomendado</td> 
   <td>string</td> 
   <td> </td> 
   <td>A localidade do usuário é uma string baseada nas convenções de marcação de idioma do RFC 3066 (por exemplo, en-US, fr-FR ou es-ES)</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>GUID do dispositivo</td> 
   <td>event.device_guid</td> 
   <td>opcional</td> 
   <td>string<br /> </td> 
   <td>UUID</td> 
   <td>Identifica o GUID do dispositivo (por exemplo, ID da máquina ou hash do endereço IP + máscara de sub-rede + ID da rede + agente do usuário) - Aqui o nome de usuário do reprodutor gerado no momento do registro é enviado.</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Contagem</td> 
   <td>event.count</td> 
   <td>opcional</td> 
   <td>número</td> 
   <td> </td> 
   <td>Número de vezes que o evento ocorreu - A duração do vídeo é enviada</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Valor</td> 
   <td>event.value</td> 
   <td>opcional</td> 
   <td>string</td> 
   <td> </td> 
   <td>Valor do evento (por exemplo, configurações ativadas/desativadas)</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Pagename</td> 
   <td>event.pagename</td> 
   <td>obrigatório para AA</td> 
   <td>string</td> 
   <td> </td> 
   <td>Suporte do Adobe Analytics para Nome de página personalizado</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>URL</td> 
   <td>event.url</td> 
   <td>opcional</td> 
   <td>string</td> 
   <td> </td> 
   <td>URL da propriedade da web ou esquema móvel - deve incluir URL totalmente qualificado</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Código de erro</td> 
   <td>event.error_code</td> 
   <td> </td> 
   <td>string</td> 
   <td> </td> 
   <td>Código de falha</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Tipo de erro</td> 
   <td>event.error_type</td> 
   <td> </td> 
   <td>string</td> 
   <td> </td> 
   <td>Tipo de falha</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Descrição do erro</td> 
   <td>event.error_description</td> 
   <td> </td> 
   <td>string</td> 
   <td> </td> 
   <td>Descrição da falha<br /> </td> 
  </tr>
  <tr>
   <td><strong><em>Origem/Produto originário</em></strong></td> 
   <td>Nome</td> 
   <td>source.name</td> 
   <td>obrigatório</td> 
   <td>string</td> 
   <td> </td> 
   <td>Nome do aplicativo (AEM Screens)</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Versão</td> 
   <td>source.version</td> 
   <td>obrigatório</td> 
   <td>string</td> 
   <td> </td> 
   <td>Versão do firmware</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Platform</td> 
   <td>source.platform</td> 
   <td>obrigatório</td> 
   <td>string</td> 
   <td> </td> 
   <td>navigator.platform</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Device</td> 
   <td>source.device</td> 
   <td>obrigatório com exceções</td> 
   <td>string</td> 
   <td> </td> 
   <td>Nome do player</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Versão do sistema operacional</td> 
   <td>source.os_version</td> 
   <td>obrigatório com exceções</td> 
   <td>string</td> 
   <td> </td> 
   <td>Versão do S/O</td> 
  </tr>
  <tr>
   <td><strong><em>Conteúdo</em></strong></td> 
   <td>Ação</td> 
   <td>content.action</td> 
   <td>obrigatório</td> 
   <td>string</td> 
   <td> </td> 
   <td>O URL para o ativo, incluindo a representação que foi reproduzida</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Tipo MIME</td> 
   <td>content.mimetype</td> 
   <td>opcional</td> 
   <td>string</td> 
   <td> </td> 
   <td>Tipo MIME do conteúdo</td> 
  </tr>
  <tr>
   <td><strong><em>Transação</em></strong></td> 
   <td>Número da transação</td> 
   <td>trn.number</td> 
   <td>obrigatório</td> 
   <td>string</td> 
   <td>UUID</td> 
   <td>Identificador exclusivo que prefere aderir ao UUID v4</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Descrição do produto</td> 
   <td>trn.product</td> 
   <td>obrigatório</td> 
   <td>string</td> 
   <td> </td> 
   <td>O URL para o ativo (excluindo a representação)</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Quantidade</td> 
   <td>trn.quantity</td> 
   <td>obrigatório</td> 
   <td>string</td> 
   <td> </td> 
   <td>A duração da reprodução</td> 
  </tr>
 </tbody>
</table>
