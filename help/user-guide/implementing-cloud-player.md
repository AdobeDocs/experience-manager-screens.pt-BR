---
title: Implementação do Cloud Player
description: Saiba mais sobre a implementação do Cloud Player.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: 184168f5-6070-4c33-a2c5-5429061dac75
source-git-commit: 1343b7d03c2ab8d24198547c5029ff47c54f3e7d
workflow-type: tm+mt
source-wordcount: '854'
ht-degree: 0%

---

# Implementação do Cloud Player {#implementing-cloud-player}

Tradicionalmente, a AEM Screens oferece aplicativos de player nativos distintos para várias plataformas, incluindo ChromeOS, Windows, Android™ e `Tizen`. No entanto, em resposta às crescentes necessidades dos usuários, a Adobe apresentou uma solução inovadora: o AEM Screens Cloud Player.

O Cloud Player representa uma diferença significativa dos aplicativos nativos anteriores da Adobe. É um aplicativo web progressivo (PWA), hospedado em um servidor. Essa abordagem transformadora capacita os clientes com um player independente de plataforma executado diretamente em um navegador da Web.

Acessar o Cloud Player é tão simples quanto visitar `https://player.adobescreens.com`. Os usuários podem instalá-lo em seus dispositivos, independentemente da plataforma, e aproveitar experiências de sinalização digital perfeitas. A compatibilidade do Cloud Player depende da presença de um navegador moderno com suporte para PWA, garantindo desempenho consistente em vários dispositivos. Diga adeus às atualizações manuais e olá para um reprodutor que fornece correções e recursos automaticamente, garantindo que você sempre tenha os recursos mais recentes ao seu alcance. Essa mudança para um Cloud Player baseado no PWA marca uma evolução emocionante nas ofertas de sinalização digital da Adobe, tornando-o mais acessível, versátil e fácil de usar do que nunca.

Esta seção descreve como implementar o Cloud Player.

>[!NOTE]
>
>A compatibilidade do Cloud Player requer um navegador moderno com suporte para PWA para garantir desempenho consistente em vários dispositivos.

## Instalação do Cloud Player {#installing-cloud-player}

A instalação do Cloud Player pode variar em plataformas diferentes. Em geral, qualquer plataforma com um navegador moderno pode executar o aplicativo do Cloud Player seguindo estas etapas:

1. Abra o navegador e insira a [URL do Cloud Player](https://player.adobescreens.com/content/dam/universal-player/firmware.html) na barra de endereços.
1. O navegador verifica se o Cloud Player pode ser instalado e mostra um ícone de instalação na barra de endereços.

   ![imagem](/help/user-guide/assets/cloud-player-install.png)

1. Clique no ícone de instalação e no botão de instalação na caixa de diálogo de confirmação. O Cloud Player é instalado como um aplicativo independente no dispositivo e pode ser iniciado usando um ícone.

>[!NOTE]
>
>### Opção de instalação do Cloud Player {#cloud-player-install-option}
>
>1. A opção de instalação de um PWA também é conhecida como &quot;Adicionar à tela inicial&quot; ou recurso A2HS. O suporte para a instalação de PWAs na Web varia de acordo com o navegador e a plataforma.
>1. Cada navegador tem critérios diferentes para verificar se o aplicativo PWA pode ser instalado ou não. Geralmente, o navegador pode verificar (mais detalhes aqui):
>
>    * Se o aplicativo tiver um arquivo manifest json com o mínimo de chaves necessárias para instalar o aplicativo na plataforma, ou seja, nome, ícones, start_url, exibição
>    * Se o aplicativo tiver um arquivo do service worker com um ouvinte de eventos de busca
>    * O aplicativo deve ser distribuído via https
>
>1. A opção de instalação pode estar visível em locais diferentes em navegadores e tipos de dispositivos diferentes. Alguns navegadores podem ocultar o ícone de instalação na barra de menu de opções.

## Cloud Player de provisionamento em massa {#bulk-provisioning}

Para fazer o provisionamento em massa do Cloud Player em vários dispositivos:

1. Escolha uma solução MDM que suporte a execução de um navegador com um URL no modo Quiosque.
1. Você pode aplicar as mesmas configurações a todos os dispositivos seguindo estas etapas:

   1. Hospede config.json em um servidor de forma que seja acessível como: `https://<config_server_host>/config.json`
   1. Para instalar o Cloud Player e aplicar as configurações hospedadas, use a URL do Cloud Player, como: `https://player.adobescreens.com?playerConfigAddress=https://<config_server_host>`
   1. O aplicativo Cloud Player procura por config.json na raiz do &lt;config_server_host> e analisa o config.json para obter as configurações personalizadas e aplicá-las.
   1. Essas configurações são aplicadas a cada recarregamento do reprodutor.

## Provisionamento em massa no sistema operacional Chrome {#bulk-provisioning-chrome}

Saiba mais sobre o provisionamento em massa no sistema operacional Chrome. Consulte [Instalar o Cloud Player no sistema operacional Chrome](https://main--screens-franklin-documentation--hlxscreens.hlx.live/updates/cloud-player/guides/chromeos-install-cloud-player). <!-- `https://www.adobe.com/go/aem_screens_cloud_player_en` -->

## Configuração necessária em instâncias do AEM {#bulk-provisioning-config-aem}

Com base no tipo de instância do AEM, clique em um dos seguintes guias para ativar o CORS b/w AEM e o Cloud Player:

* [AEM No Local/AMS](https://main--screens-franklin-documentation--hlxscreens.hlx.live/updates/cloud-player/guides/cors-settings-aem-onpremandams) <!-- `https://www.adobe.com/go/aem_screens_cors_ams_en` -->

* [AEM Cloud Service](https://main--screens-franklin-documentation--hlxscreens.hlx.live/updates/cloud-player/guides/cors-settings-aem-cs) <!-- `https://www.adobe.com/go/aem_screens_cors_aemaacs_en` -->


>[!NOTE]
>
>## Descontinuação de aplicativos Chrome pelo Google
>
>1. Aplicativos Chrome no hardware do sistema operacional Chrome:
>
>   O Google tem descontinuado ativamente os aplicativos Chrome em favor dos aplicativos PWA, com uma migração planejada para janeiro de 2025. Portanto, o aplicativo AEM Screens Player no Chrome OS deixa de funcionar com base na linha do tempo compartilhada. A Adobe recomenda que os usuários que atualmente usam o Chrome Player em produção planejem a transição para o Screens Cloud Player.
>
>1. Chrome Extension Player no Mac, Windows e Linux®:
>
>   Devido ao processo de desativação da Google, a partir do Google Chrome versão 114, o Screens Chrome Extension Player não é mais suportado. A Adobe aconselha fazer a transição para o Screens Cloud Player para atender a todos os seus requisitos de desenvolvimento e teste.

## Suporte off-line para recuperação de conteúdo externo {#offline-support}

Em vários cenários de uso, os canais podem exigir a recuperação de conteúdo de uma fonte externa (por exemplo, widgets meteorológicos ou Aplicativos de página única integrados à Commerce) que não podem inerentemente fornecer suporte offline. Para ativar a funcionalidade offline para esses casos de uso específicos, o Cloud Player oferece suporte para cabeçalho personalizado.

O Cloud Player emprega uma estratégia de cache Network First, o que significa que ele tenta buscar conteúdo da rede (em seguida, atualizar o cache com o mais recente), retornando ao conteúdo em cache, se disponível. Para implementar o suporte offline para essa recuperação de conteúdo, o cabeçalho personalizado deve ser incluído na solicitação. Em seguida, a solicitação com o cabeçalho personalizado é armazenada em cache no reprodutor, facilitando o acesso offline ao conteúdo e mantendo a estratégia de cache Rede primeiro.

```
// Sample fetch request with the 'X-Cache-Strategy' header
fetch(externalUrl, {
  headers: {
    'X-Cache-Strategy': 'external-cache'
  }
})
  .then(response => {
    // Handle the response, which may be from the network or cache.
    // Your logic here.
  })
  .catch(error => {
    // Handle any errors that may occur during the fetch operation.
    // Your error handling logic here.
  }); 
```

## Feedback

A Adobe valoriza seus comentários. Compartilhe suas ideias conosco através deste [formulário](https://forms.office.com/pages/responsepage.aspx?id=Wht7-jR7h0OUrtLBeN7O4TFE0b_GjstOj6I1uGs9vLpURVdWWklQQTZZRTFVNEhRVlBWWldMWlJXOC4u).
