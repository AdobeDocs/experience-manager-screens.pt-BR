---
title: Uso do Chrome Player como uma extensão
seo-title: Uso do Chrome Player como uma extensão
description: 'null'
seo-description: 'null'
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# Uso do Chrome Player como uma extensão {#using-chrome-player}

O ChromeOS player pode ser instalado como plug-in do Chrome Browser no modo de desenvolvedor, sem a necessidade de um dispositivo de player de cromo.

>[!CAUTION]
>
> É recomendável usar o Chrome Player como uma extensão para solução de problemas para demos rápidos, depurar e também para solucionar problemas do cliente. Esse mecanismo não deve ser usado para implantações de produção que exijam o modo quiosque e o gerenciamento central.

Siga esta página para saber mais sobre como instalar o player do cromo como uma extensão do navegador.

1. Clique aqui para baixar o Chrome Player mais recente.

1. Descompacte e salve no disco.

1. Abra o navegador Chrome e clique no menu de 3 pontos e selecione **Mais ferramentas** em **extensões** localizadas no canto superior direito ou navegue diretamente para `chrome://extensions`.

1. Ative o modo **Desenvolvedor** no canto superior direito.

1. Clique em **Carregar descompactado** no canto superior esquerdo e carregue o Chrome Player descompactado.

1. Verifique o plug-in do Chrome Player do AEM Screens se estiver disponível na lista de extensões.

1. Abra uma nova guia e clique no ícone Aplicativos no canto superior esquerdo ou navegue diretamente para `chrome://apps`.

1. Clique em Plug-in **AEM Screens** para iniciar o Chrome Player.
   >[!NOTE]
   >
   > Por padrão, o player é iniciado no modo de tela cheia. Pressione **esc** para sair do modo de tela cheia.


## Dicas avançadas de depuração {#advanced-debugging-tips}

1. Depois que o player tiver baixado o conteúdo localmente, você poderá navegar pelo conteúdo baixado localmente indo para `http://localhost:24502`.

   >[!NOTE]
   >
   > Se o URL mencionado acima não funcionar, significa que o player não recebeu uma exibição ou o conteúdo não foi baixado com êxito. Verifique na guia de rede a configuração do player JSON para ver se os detalhes corretos foram obtidos pelo player e se há problemas de rede no download.

1. Você pode clicar com o botão direito do mouse e inspecionar três camadas do player de cromo
   **Depurar conteúdo**: Clique com o botão direito do mouse e inspecione o conteúdo para depurar o conteúdo em execução (Deve haver um único item chamado "Inspecionar" no menu de contexto)

   **Firmware** de depuração: Abra a interface do usuário do administrador e clique com o botão direito do mouse e inspecione-a para depurar o código do firmware (player) (Deve haver uma opção para inspecionar e inspecionar a página em segundo plano e simular a reinicialização do navegador)

   **Página** de fundo de depuração: Abra a interface do usuário do administrador e clique com o botão direito do mouse e inspecione a página em segundo plano (para serviços em segundo plano, como o servidor http)

## Atualização da extensão do player {#upgrading-player}

Siga as etapas abaixo para atualizar a extensão do player se uma nova versão do player for lançada. Você também pode seguir as instruções abaixo para testar os cenários de atualização:

1. Feche todas as instâncias do cromo e do player em execução
1. Renomear a pasta antiga com os arquivos do player
1. Extraia o novo zip no mesmo local da pasta antiga
1. Inicie o Chrome e navegue até `chrome://extensions`
1. Verifique o ícone do player e clique no botão Atualizar ou recarregar