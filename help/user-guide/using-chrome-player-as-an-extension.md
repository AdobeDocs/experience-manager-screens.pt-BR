---
title: Utilização do Chrome Player como uma extensão
description: Saiba mais sobre como instalar o reprodutor do Chrome como uma extensão de navegador do AEM Screens.
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: 53d5bd81-0853-47b0-9798-01d8fd5612e6
source-git-commit: ef74265eadf5972eae7451b7725946d8b014c198
workflow-type: tm+mt
source-wordcount: '453'
ht-degree: 0%

---

# Utilização do Chrome player como uma extensão {#using-chrome-player}

O ChromeOS player pode ser instalado como um plug-in do navegador Chrome no modo de desenvolvedor, sem exigir um dispositivo Chrome player real.

>[!CAUTION]
>
> É recomendado usar o reprodutor do Chrome como uma extensão para solução de problemas, a fim de obter demonstrações rápidas, depuração e solução de problemas do cliente. Não use esse mecanismo para implantações de produção que exigiriam o modo de quiosque e o gerenciamento central.

Siga esta página para obter informações sobre como instalar o reprodutor do Chrome como uma extensão do navegador.

1. Clique em [aqui](https://download.macromedia.com/screens/) para baixar o reprodutor Chrome mais recente.

1. Descompacte-o e salve-o no disco.

1. Abra o navegador Chrome, clique no menu de 3 pontos e clique em **Mais ferramentas** de **Extensões** no canto superior direito ou navegue diretamente para `chrome://extensions`.

1. Ligue o **Desenvolvedor** no canto superior direito.

1. Clique em **Carregar desempacotado** no canto superior esquerdo e carregue o reprodutor do Chrome descompactado.

1. Verifique o plug-in do reprodutor do AEM Screens Chrome se ele estiver disponível na lista de extensões.

1. Abra uma nova guia e clique no ícone Aplicativos no canto superior esquerdo ou navegue diretamente para `chrome://apps`.

1. Clique em **Plug-in AEM Screens** para que você possa iniciar o reprodutor do Chrome.

   >[!NOTE]
   >
   > Por padrão, o reprodutor é iniciado no modo de tela cheia. Pressione **Esc** para sair do modo de tela cheia.


## Dicas avançadas de depuração {#advanced-debugging-tips}

1. Quando o reprodutor tiver baixado o conteúdo localmente, você poderá navegar pelo conteúdo baixado localmente acessando `http://localhost:24502`.

   >[!NOTE]
   >
   > Se o URL mencionado acima não funcionar, significa que o reprodutor não recebeu uma exibição ou o conteúdo não foi baixado com sucesso. Verifique a guia Rede da configuração JSON do reprodutor para ver se o reprodutor obtém os detalhes corretos e se há problemas de rede no download.

1. Clique com o botão direito do mouse e inspecione três camadas do reprodutor Chrome.
   **Depurar conteúdo**: Clique com o botão direito do mouse e inspecione o conteúdo para depurar o conteúdo em execução (deve haver um único item chamado &quot;Inspect&quot; no menu de contexto)

   **Depurar firmware**: abra a interface do administrador e clique com o botão direito do mouse e inspecione para depurar o código do firmware (player). (Deve haver uma opção para inspecionar e inspecionar a página de plano de fundo e simular uma reinicialização do navegador.)

   **Depurar página de plano de fundo**: abra a interface do administrador e clique com o botão direito do mouse e inspecione a página de plano de fundo (para serviços em segundo plano, como o servidor http).

## Atualização da extensão do player {#upgrading-player}

Siga as etapas abaixo para atualizar a extensão do reprodutor se uma nova versão do reprodutor for lançada. Você também pode seguir as instruções abaixo para testar cenários de atualização:

1. Fechar todas as instâncias do Chrome e do player em execução
1. Renomear a pasta antiga com arquivos do player
1. Extraia o novo zip no mesmo local da pasta antiga
1. Inicie o Chrome e navegue até `chrome://extensions`
1. Verifique o ícone do reprodutor e clique no botão atualizar ou recarregar
