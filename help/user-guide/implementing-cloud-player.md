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
exl-id: 184168f5-6070-4c33-a2c5-5429061dac75
source-git-commit: 5b64ab8eea274aa85c61311d34b1ce065a5ba601
workflow-type: tm+mt
source-wordcount: '858'
ht-degree: 0%

---

# Implementação do Cloud Player  {#implementing-cloud-player}

Tradicionalmente, a AEM Screens oferece aplicativos de player nativos distintos para várias plataformas, incluindo ChromeOS, Windows, Android e Tizen. No entanto, em resposta às necessidades crescentes de nossos usuários, introduzimos uma solução inovadora: o AEM Screens Cloud Player.

O Cloud Player representa uma diferença significativa de nossos aplicativos nativos anteriores. É um aplicativo web progressivo (PWA) hospedado em um servidor. Essa abordagem transformadora capacita nossos clientes com um player independente de plataforma executado diretamente em um navegador da Web.

Acessar o Cloud Player é tão simples quanto visitar https://player.adobescreens.com. Os usuários podem instalá-lo em seus dispositivos, independentemente da plataforma, e aproveitar experiências de sinalização digital perfeitas. A compatibilidade do Cloud Player depende da presença de um navegador moderno com suporte para PWA, garantindo desempenho consistente em vários dispositivos. Diga adeus às atualizações manuais e olá para um reprodutor que fornece correções e recursos automaticamente, garantindo que você sempre tenha os recursos mais recentes ao seu alcance. Essa mudança para um Cloud Player baseado em PWA marca uma evolução emocionante em nossas ofertas de sinalização digital, tornando-o mais acessível, versátil e fácil de usar do que nunca.

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

>[!NOTE]
>
>### Opção de instalação do Cloud Player {#cloud-player-install-option}
>
1. A opção de instalação de um PWA também é conhecida como &quot;Adicionar à tela inicial&quot; ou recurso A2HS.  O suporte para a instalação de PWA na Web varia de acordo com o navegador e a plataforma.
1. Cada navegador tem critérios diferentes para verificar se o aplicativo PWA é instalável ou não. Geralmente, o navegador verifica estes (mais detalhes aqui):
>
* Se o aplicativo tiver um arquivo JSON de manifesto com as chaves mínimas necessárias para instalar o aplicativo na plataforma, ou seja, nome, ícones, start_url, exibição
* Se o aplicativo tiver um arquivo do service worker com um ouvinte de eventos de busca.
* O aplicativo deve ser distribuído por https.
>
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

>[!NOTE]
>
## Descontinuação de aplicativos do Chrome pelo Google
>
1. Aplicativos Chrome no hardware do Chrome OS:
>
A Google tem descontinuado ativamente os aplicativos do Chrome em favor dos aplicativos PWA, com uma migração planejada até janeiro de 2025. Consequentemente, o aplicativo AEM Screens Player no Chrome OS deixará de funcionar com base na linha do tempo compartilhada. Recomendamos que nossos clientes que atualmente usam o Chrome Player em produção planejem a transição para o Screens Cloud Player.
>
1. Player de extensão do Chrome no Mac, Windows e Linux:
>
Devido ao processo de desativação do Google, a partir do Google Chrome versão 114, o reprodutor de extensão do Screens Chrome não é mais compatível. Recomendamos a transição para nosso Screens Cloud Player para todos os seus requisitos de desenvolvimento e teste.

## Suporte off-line para recuperação de conteúdo externo {#offline-support}

Em vários cenários de uso, os canais podem exigir a recuperação de conteúdo de uma fonte externa (por exemplo, widgets meteorológicos ou Aplicativos de página única integrados ao Commerce) que não podem inerentemente fornecer suporte offline. Para ativar a funcionalidade offline para esses casos de uso específicos, o Cloud Player oferece suporte para cabeçalho personalizado.

O Cloud Player emprega uma estratégia de cache Network First, o que significa que ele tenta buscar conteúdo da rede (em seguida, atualizar o cache com o mais recente), retornando ao conteúdo em cache, se disponível. Para implementar o suporte offline para essa recuperação de conteúdo, o cabeçalho personalizado deve ser incluído na solicitação. Posteriormente, a solicitação com o cabeçalho personalizado será armazenada em cache no reprodutor, facilitando o acesso offline ao conteúdo e mantendo a estratégia de cache Rede primeiro.

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

Seus comentários são muito importantes. Compartilhe seus pensamentos conosco através deste [formulário](https://forms.office.com/r/MQXX9JsuEd).
