---
title: Uso do Chrome Player como uma extensão
seo-title: Uso do Chrome Player como uma extensão
description: Siga esta página para saber mais sobre a instalação do chrome player como uma extensão de navegador.
seo-description: 'null'
feature: Administering Screens
role: Administrator
level: Intermediate
translation-type: tm+mt
source-git-commit: 9d36c0ebc985b815ab41d3f3ef44baefa22db915
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 0%

---


# Uso do Chrome Player como uma extensão {#using-chrome-player}

O player do ChromeOS pode ser instalado como plug-in do navegador Chrome no modo de desenvolvedor sem precisar do dispositivo do player do Chrome.

>[!CAUTION]
>
> É recomendável usar o Chrome Player como extensão para solução de problemas em demonstrações rápidas, depuração e também para solucionar problemas do cliente. Esse mecanismo não deve ser usado para implantações de produção que precisariam do modo quiosque e do gerenciamento central.

Siga esta página para saber mais sobre a instalação do chrome player como uma extensão de navegador.

1. Clique [aqui](https://download.macromedia.com/screens/) para baixar o Player mais recente do Chrome.

1. Descompacte-o e salve-o no disco.

1. Abra o navegador Chrome e clique no menu de 3 pontos e selecione **Mais ferramentas** de **Extensões**, localizado no canto superior direito ou navegue diretamente para `chrome://extensions`.

1. Ative o modo **Desenvolvedor** no canto superior direito.

1. Clique em **Carregar descompactado** do canto superior esquerdo e carregue o Chrome Player descompactado.

1. Verifique o plug-in do AEM Screens Chrome Player, se estiver disponível na lista de extensões.

1. Abra uma nova guia e clique no ícone Aplicativos no canto superior esquerdo ou navegue diretamente para `chrome://apps`.

1. Clique em **AEM Screens Plugin** para iniciar o Chrome Player.
   >[!NOTE]
   >
   > Por padrão, o reprodutor é iniciado no modo de tela cheia. Pressione **esc** para sair do modo de tela cheia.


## Dicas de depuração avançadas {#advanced-debugging-tips}

1. Depois que o reprodutor tiver baixado o conteúdo localmente, você poderá navegar pelo conteúdo baixado localmente acessando `http://localhost:24502`.

   >[!NOTE]
   >
   > Se o URL mencionado acima não funcionar, significa que o player não recebe uma exibição ou o conteúdo não foi baixado com êxito. Verifique a guia de rede do JSON de configuração do reprodutor para ver se os detalhes corretos são obtidos pelo reprodutor e se há problemas de rede no download.

1. Você pode clicar com o botão direito do mouse e inspecionar três camadas do player do Chrome
   **Depurar conteúdo**: Clique com o botão direito do mouse e inspecione o conteúdo para depurar o conteúdo em execução (Deve haver um único item chamado &quot;Inspect&quot; no menu de contexto)

   **Firmware** de depuração: Abra a interface do administrador e clique com o botão direito do mouse e inspecione para depurar o código do firmware (reprodutor) (Deve haver uma opção para inspecionar e inspecionar a página em segundo plano e simular a reinicialização do navegador)

   **Página** de fundo de depuração: Abra a interface do administrador e clique com o botão direito do mouse e inspecione a página em segundo plano (para serviços em segundo plano, como o servidor http)

## Atualização da extensão do reprodutor {#upgrading-player}

Siga as etapas abaixo para atualizar a extensão do reprodutor se uma nova versão do reprodutor for lançada. Você também pode seguir as instruções abaixo para testar cenários de atualização:

1. Fechar qualquer instância do Chrome e do player em execução
1. Renomeie a pasta antiga com arquivos do reprodutor
1. Extraia o novo zip no mesmo local da pasta antiga
1. Inicie o Chrome e navegue até `chrome://extensions`
1. Verifique o ícone do reprodutor e clique no botão atualizar ou recarregar