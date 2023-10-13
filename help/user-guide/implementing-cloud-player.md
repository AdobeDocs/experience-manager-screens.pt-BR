---
title: Implementação do Cloud Player
seo-title: Implementing Cloud Player
description: Siga esta página para saber mais sobre a implementação do Cloud Player.
seo-description: Follow  this page to learn about the implementation of the Cloud Player.
uuid: eee84286-fa81-475c-ad6f-db2d6cf1fed5
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
discoiquuid: 1be944f0-02ed-48c6-98bc-504d758ff866
feature: Administering Screens
role: Admin
level: Intermediate
source-git-commit: 718ef76b620accd7096be2e4b7ac53658cb7fce7
workflow-type: tm+mt
source-wordcount: '455'
ht-degree: 0%

---

# Implementação do Cloud Player  {#implementing-cloud-player}

Esta seção descreve como implementar o Cloud Player.

>[!NOTE]
>
>A compatibilidade do Cloud Player exige um navegador moderno com suporte para PWA para garantir desempenho consistente em vários dispositivos.

## Instalação do Cloud Player {#installing-cloud-player}

A instalação do Cloud Player pode variar em plataformas diferentes. Em geral, qualquer plataforma com um navegador moderno pode executar o aplicativo do Cloud Player seguindo estas etapas:

1. Abra o navegador e insira o [URL do Cloud Player](https://player.adobescreens.com) na barra de endereços.
1. O navegador verifica se o Cloud Player pode ser instalado e mostra um ícone de instalação na barra de endereços.

![imagem](/help/user-guide/assets/cloud-player-install.png)

1. Clique no ícone de instalação e no botão de instalação na caixa de diálogo de confirmação. O Cloud Player será instalado como um aplicativo independente no dispositivo e poderá ser iniciado usando um ícone.

### Opção de instalação do Cloud Player {#cloud-player-install-option}

1. A opção de instalação de um PWA também é conhecida como &quot;Adicionar à tela inicial&quot; ou recurso A2HS.  O suporte para a instalação de PWA na Web varia de acordo com o navegador e a plataforma.
1. Cada navegador tem critérios diferentes para verificar se o aplicativo PWA é instalável ou não. Geralmente, o navegador verifica estes (mais detalhes aqui):
   * Se o aplicativo tiver um arquivo JSON de manifesto com as chaves mínimas necessárias para instalar o aplicativo na plataforma, ou seja, nome, ícones, start_url, exibição
   * Se o aplicativo tiver um arquivo do service worker com um ouvinte de eventos de busca.
   * O aplicativo deve ser distribuído por https.
1. A opção Instalar pode estar visível em locais diferentes em navegadores e tipos de dispositivo diferentes. Alguns navegadores podem ocultar o ícone de instalação na barra de menu de opções.

## Cloud Player de provisionamento em massa {#bulk-provisioning}

Para fazer o provisionamento em massa do Cloud Player em vários dispositivos:

1. Escolha uma solução MDM que suporte a execução de um navegador com um URL no modo Quiosque.
1. Você pode aplicar as mesmas configurações a todos os dispositivos seguindo estas etapas:
   1. Hospede config.json em um servidor de modo que seja acessível como: https://&lt;config_server_host>/config.json
   1. Para instalar o Cloud Player e aplicar as configurações hospedadas, use o URL do Cloud Player, como: https://player.adobescreens.com?playerConfigAddress=https://&lt;config_server_host>
   1. O aplicativo Cloud Player procura config.json na raiz do &lt;config_server_host>, analise o config.json para obter as configurações personalizadas e aplicá-las.
   1. Essas configurações serão aplicadas a cada recarregamento do reprodutor.

## Provisionamento em massa no Chrome OS {#bulk-provisioning-chrome}

Para saber mais sobre o provisionamento em massa no Chrome OS, consulte: [Instalar o Cloud Player no Chrome OS](https://main--screens-franklin-documentation--hlxscreens.hlx.page/updates/cloud-player/guides/chromeos-install-cloud-player).

## Configuração necessária em instâncias do AEM {#bulk-provisioning-config-aem}

Com base no tipo de instância AEM, selecione um dos guias a seguir para ativar o CORS b/w AEM e o Cloud Player:
* [AEM no local/AMS](https://main--screens-franklin-documentation--hlxscreens.hlx.live/updates/cloud-player/guides/cors-settings-aem-onpremandams)
* [AEM Cloud Service](https://main--screens-franklin-documentation--hlxscreens.hlx.live/updates/cloud-player/guides/cors-settings-aem-cs)

