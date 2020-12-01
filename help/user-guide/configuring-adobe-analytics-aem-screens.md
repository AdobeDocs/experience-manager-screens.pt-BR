---
title: Configuração do Adobe Analytics com o AEM Screens
seo-title: Configuração do Adobe Analytics com o AEM Screens
description: 'Siga esta seção para saber mais sobre como sequenciar e enviar eventos personalizados usando o Adobe Analytics offline '
seo-description: 'Siga esta seção para saber mais sobre como sequenciar e enviar eventos personalizados usando o Adobe Analytics offline '
uuid: e685e553-c05b-4db4-8fa5-9ef45268b094
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: developing
discoiquuid: 3cec9266-4032-46b9-9c75-16da64bfea7d
docset: aem65
translation-type: tm+mt
source-git-commit: 2a3bbdd283f983cbdb5f21b606f508603385e041
workflow-type: tm+mt
source-wordcount: '694'
ht-degree: 11%

---


# Configuração do Adobe Analytics com AEM Screens {#configuring-adobe-analytics-with-aem-screens}

>[!CAUTION]
>
>Esta funcionalidade do AEM Screens só estará disponível se você tiver instalado AEM 6.4.2 Feature Pack 2 e AEM 6.3.3 Feature Pack 4.
>
>Para obter acesso a qualquer um desses Pacotes de recursos, entre em contato com o Suporte ao Adobe e solicite acesso. Com as devidas permissões, você pode baixá-lo em Compartilhamento de pacotes.

Esta seção aborda os seguintes tópicos:

* **Sequenciamento no Adobe Analytics com AEM Screens**
* **Envio de Eventos personalizados usando o Adobe Analytics offline**

## Sequenciamento no Adobe Analytics com AEM Screens {#sequencing-in-adobe-analytics-with-aem-screens}

Os start ***sequenciando process*** com o serviço de armazenamento de dados que ativa o serviço Adobe Analytics. O conteúdo do canal envia eventos Adobe Analytics com folha de pagamento, ou seja, a captura de teste de dados para E/S do Windows e os eventos de permanência são acionados. Os eventos são salvos no banco de dados de índice e são posteriormente colocados no repositório de objetos. Com base no agendamento, o administrador define, corta os dados do repositório de objetos e os transfere ainda mais no repositório de segmentos. Ele tenta enviar a quantidade máxima de dados, quando conectado.

### Diagrama de Sequência {#sequencing-diagram}

O diagrama de sequência a seguir explica a integração do Adobe Analytics com o AEM Screens:

![analytics_chunking](assets/analytics_chunking.png)

## Envio de Eventos personalizados usando o Adobe Analytics offline {#sending-custom-events-using-offline-adobe-analytics}

A tabela a seguir resume o modelo de dados padrão para eventos. Ele lista todos os campos enviados para a Adobe Analytics:

<table>
 <tbody>
  <tr>
   <td><strong>Seção</strong></td> 
   <td><strong>Rótulo da propriedade</strong></td> 
   <td><strong>Nome da propriedade/chave</strong></td> 
   <td><strong>Obrigatório</strong></td> 
   <td><strong>Tipo de dados</strong></td> 
   <td><strong>Tipo de propriedade</strong><br /> </td> 
   <td><strong>Descrição</strong></td> 
  </tr>
  <tr>
   <td><strong><em>Core/Evento</em></strong></td> 
   <td>GUID do evento</td> 
   <td>event.guid</td> 
   <td>recomendado</td> 
   <td>string</td> 
   <td>UUID</td> 
   <td>ID exclusiva que identifica a instância de um evento</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Data e hora da recolha do evento</td> 
   <td>event.coll_dts</td> 
   <td>opcional</td> 
   <td>string</td> 
   <td>carimbo de data e hora - UTC</td> 
   <td>Data da coleção</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Data e hora do evento (start)</td> 
   <td>event.dts_start</td> 
   <td>recomendado</td> 
   <td>string</td> 
   <td>carimbo de data e hora - UTC</td> 
   <td>A data e hora do start do evento, se você NÃO especificar isso, a hora do evento será assumida como a hora em que foi recebido pelo servidor</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Data e hora do evento (fim)</td> 
   <td>event.dts_end</td> 
   <td>opcional</td> 
   <td>string</td> 
   <td>carimbo de data e hora - UTC</td> 
   <td>Hora de conclusão do evento</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Fluxo de trabalho</td> 
   <td>event.workflow</td> 
   <td>recomendado</td> 
   <td>string</td> 
   <td> </td> 
   <td>Nome do fluxo de trabalho (telas)</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Categoria principal do DMe</td> 
   <td>event.category</td> 
   <td>required</td> 
   <td>string</td> 
   <td> </td> 
   <td>Categoria principal (DESKTOP, MOBILE, WEB, PROCESS, SDK, SERVICE, ECOSYSTEM) - Agrupamento de tipos de evento - <strong>Enviamos Player</strong></td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Sub Categoria</td> 
   <td>event.subcategory</td> 
   <td>recomendado</td> 
   <td>string</td> 
   <td> </td> 
   <td>SubCategoria - Seção de um fluxo de trabalho ou Área de uma tela etc. (Arquivos recentes, Arquivos CC, Criações móveis etc.)</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Tipo de evento/ação</td> 
   <td>event.type</td> 
   <td>required</td> 
   <td>string</td> 
   <td> </td> 
   <td>tipo de evento (renderizar, clicar, aproximar, aplicar zoom) - Ação principal do usuário</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Subtipo</td> 
   <td>event.subtype</td> 
   <td>recomendado</td> 
   <td>string</td> 
   <td> </td> 
   <td>Subtipo de evento (criar, atualizar, excluir, publicar etc.) - Detalhes adicionais da ação do usuário</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Offline</td> 
   <td>event.offline</td> 
   <td>opcional</td> 
   <td>boolean</td> 
   <td> </td> 
   <td>O evento foi gerado enquanto a ação estava offline/online (true/false)</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Agente do usuário</td> 
   <td>event.user_agent</td> 
   <td>recomendado (propriedades da Web)</td> 
   <td>string</td> 
   <td> </td> 
   <td>Agente do usuário</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Idioma/Localidade</td> 
   <td>event.language</td> 
   <td>recomendado</td> 
   <td>string</td> 
   <td> </td> 
   <td>A localidade do usuário é uma string com base nas convenções de marcação de idioma da RFC 3066 (por exemplo, en-US, fr-FR ou es-ES)</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>GUID do dispositivo</td> 
   <td>event.device_guid</td> 
   <td>opcional</td> 
   <td>sequência de caracteres<br /> </td> 
   <td>UUID</td> 
   <td>Identifica o GUID do dispositivo (por exemplo, ID da máquina ou hash do endereço IP + máscara de sub-rede + ID da rede + agente do usuário) - Aqui, enviaremos o nome de usuário do player gerado no momento do registro.</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Contagem</td> 
   <td>event.count</td> 
   <td>opcional</td> 
   <td>número</td> 
   <td> </td> 
   <td>Número de vezes que o evento ocorreu - Aqui, enviamos a duração do vídeo</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Valor</td> 
   <td>event.value</td> 
   <td>opcional</td> 
   <td>string</td> 
   <td> </td> 
   <td>Valor do evento (por exemplo, ligar/desligar configurações)</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Pagename</td> 
   <td>event.pagename</td> 
   <td>obrigatório para AA</td> 
   <td>string</td> 
   <td> </td> 
   <td>Suporte da Adobe Analytics para Nome de página personalizado</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>URL</td> 
   <td>event.url</td> 
   <td>opcional</td> 
   <td>string</td> 
   <td> </td> 
   <td>URL da propriedade da Web ou do schema móvel - deve incluir um URL totalmente qualificado</td> 
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
   <td><strong><em>Origem/Produto de origem</em></strong></td> 
   <td>Nome</td> 
   <td>source.name</td> 
   <td>required</td> 
   <td>string</td> 
   <td> </td> 
   <td>Nome do aplicativo (AEM Screens)</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Versão</td> 
   <td>source.version</td> 
   <td>required</td> 
   <td>string</td> 
   <td> </td> 
   <td>Versão do firmware</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Plataforma</td> 
   <td>source.platform</td> 
   <td>required</td> 
   <td>string</td> 
   <td> </td> 
   <td>navigator.platform</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Device</td> 
   <td>source.device</td> 
   <td>obrigatório sem exceções</td> 
   <td>string</td> 
   <td> </td> 
   <td>Nome do player</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Versão do SO</td> 
   <td>source.os_version</td> 
   <td>obrigatório sem exceções</td> 
   <td>string</td> 
   <td> </td> 
   <td>Versão O/S</td> 
  </tr>
  <tr>
   <td><strong><em>Conteúdo</em></strong></td> 
   <td>Ação</td> 
   <td>content.action</td> 
   <td>required</td> 
   <td>string</td> 
   <td> </td> 
   <td>O URL do ativo, incluindo a representação que foi realmente reproduzida</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Tipo Mime</td> 
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
   <td>required</td> 
   <td>string</td> 
   <td>UUID</td> 
   <td>ID exclusiva que, de preferência, adere ao UUID v4</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Descrição do produto</td> 
   <td>trn.product</td> 
   <td>required</td> 
   <td>string</td> 
   <td> </td> 
   <td>O URL para o ativo (exceto representação)</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>Quantidade</td> 
   <td>trn.quantity</td> 
   <td>required</td> 
   <td>string</td> 
   <td> </td> 
   <td>A duração da reprodução</td> 
  </tr>
 </tbody>
</table>

