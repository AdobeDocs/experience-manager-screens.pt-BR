---
title: Trabalhar com o AEM Screens Player
seo-title: Trabalhar com o Player do Screens
description: Siga esta página para saber mais sobre o Player do Screens. Ela também explica a Interface do usuário do administrador e o Seletor de canal.
seo-description: Siga esta página para saber mais sobre o Player do Screens. Ela também explica a Interface do usuário do administrador e o Seletor de canal.
uuid: 93e113ea-fbef-4757-982b-b7dc52fc76a7
contentOwner: jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: 4ad51b5e-c628-4440-9f2e-41d17cb10bc3
feature: Administering Screens
role: Administrator
level: Intermediate
translation-type: tm+mt
source-git-commit: 9d36c0ebc985b815ab41d3f3ef44baefa22db915
workflow-type: tm+mt
source-wordcount: '1070'
ht-degree: 42%

---


# Trabalhar com o AEM Screens Player {#working-with-aem-screens-player}

Você pode gerenciar o conteúdo do canal e outras configurações no Player do AEM Screens.

>[!NOTE]
>
>Pressione ***Ctrl+Cmd+F*** para sair do modo de tela cheia do Player do AEM Screens para OS X.

Depois que você atribui um canal a uma exibição, o Player do AEM Screens exibe o conteúdo. Você pode definir as configurações do seu player usando as preferências da interface do usuário do administrador (no painel) ou no próprio player.

## Uso do painel Dispositivos {#using-the-device-dashboard}

Você pode configurar as preferências do seu dispositivo no painel Dispositivos, acessível na sua instância de criação do AEM.

1. Navegue até o painel Dispositivos do seu projeto, por exemplo, ***Testar projeto*** —> ***Dispositivos***.

   Selecione **Dispositivos** e **Gerenciador de Dispositivos** na barra de ações.

   ![chlimage_1-66](assets/chlimage_1-66.png)

1. Clique no dispositivo para abrir o painel Dispositivos.

   ![chlimage_1-67](assets/chlimage_1-67.png)

1. Verifique o painel **PREFERÊNCIAS**. Você pode habilitar/desabilitar o **Interface do usuário do administrador** e o **Seletor de canal** para o seu player a partir dessas duas opções.

   ![chlimage_1-68](assets/chlimage_1-68.png)

### A Interface do usuário do administrador {#the-admin-ui}

Ativar a **Interface do usuário do administrador** no painel de preferências permite que o usuário abra as configurações do administrador no Player do Screens. Além disso, se você desativar essa opção no painel Dispositivos, o usuário não poderá abrir a interface do usuário do administrador.

Para exibir a interface do usuário do administrador no player do Screens, pressione e segure no canto superior esquerdo para abrir o menu Admin, no player do AEM Screens ativado para toque ou com o uso de um mouse. Ele mostra informações após a conclusão do registro e o carregamento dos canais.

>[!NOTE]
>
>Além disso, você pode visualizar o tempo de atividade do aplicativo Player do AEM Screens para verificar seu status de integridade.

![chlimage_1-3](assets/chlimage_1-3.gif)

#### Acessar as opções do menu de configuração {#configuration-options}

Você pode atualizar suas configurações, se selecionar a opção **Configuration** no menu lateral, conforme mostrado na figura abaixo:

![screen_shot_2018-10-15at101257am](assets/screen_shot_2018-10-15at101257am.png)

O menu Configuração permite modificar as seguintes configurações:

* Redefina **Firmware**, **Preferências** ou **Para fábrica** desta caixa de diálogo.

* Especifique o número máximo de arquivos de log a serem mantidos para um reprodutor AEM Screens em **Nº Máx. de arquivos de log a serem mantidos**.

* Ative ou desative **Admin Menu**, **Channel Switcher** e **Activity UI** para o player do Screens.

   Se a **Interface do usuário de atividade** estiver ativada no menu **Configuração**, o player do AEM Screens exibirá as *notificações de atividade do player* no canto superior direito do player, conforme mostrado na figura abaixo.

   ![imagem](/help/user-guide/assets/activity_ui.png)

>[!NOTE]
>
>A opção **Atualizar firmware** só funciona no cordova, como players Android.

>[!NOTE]
>
>Recomenda-se que a **Interface do usuário do administrador** seja desativada em Implantações de produção.

#### Acessar as opções do menu da Cache de conteúdo {#content-cache-options}

Você pode limpar o cache de canais e aplicativos da Interface do usuário do administrador no player do AEM Screens.

Selecione **Cache de conteúdo** no painel lateral para atualizar o cache.

![screen_shot_2018-10-15at105717am](assets/screen_shot_2018-10-15at105717am.png)

### O Seletor de canal {#the-channel-switcher}

Habilitar o **Seletor de canal** no painel de preferências permite que o usuário abra a seleção/as configurações do canal no Player do Screens.

Além disso, se você desativar essa opção no painel Dispositivos, o usuário não poderá controlar as preferências de canal no Player do Screens.

Você pode alternar e controlar as configurações do seu canal no Player do Screens.

Para exibir o seletor de canais do player, pressione e segure no canto inferior esquerdo para abrir o seletor de canais, que permite trocar canais e usar outros recursos.

![chlimage_1-69](assets/chlimage_1-69.png)

>[!NOTE]
>
>Você também pode ativar ou desativar o menu do administrador e o seletor de canais para o player no player do Screens.
>
>(Consulte *Alterar as preferências do player do Screens*, conforme mencionado na seção abaixo).

### Gerenciamento de preferências do Player do AEM Screens  {#managing-preferences-from-the-aem-screens-player}

Você também pode alterar as configurações da interface do usuário do administrador e do seletor de canal do próprio player.

Siga estas etapas para alterar as preferências do seu Player:

1. Pressione e segure no canto superior esquerdo do canal inativo para abrir o painel do administrador.
1. Navegue até **Configuração** no menu de ação à esquerda.
1. Ative/desative a configuração para **Interface do usuário do administrador** ou **Seletor de canal**.

![screen_shot_2018-10-15at101257am-1](assets/screen_shot_2018-10-15at101257am-1.png)

## Solução de problemas do Player do AEM Screens {#troubleshooting-aem-screens-player}

É possível solucionar vários problemas associados ao Player do AEM Screens (hardware e software):

| **Problemas** | **Recomendações** |
|---|---|
| O armazenamento do reprodutor está cheio | Elimine arquivos desnecessários |
| Rede perdida do reprodutor | Use o cabo Cat-5/Cat-6. Para wifi, reduza a distância do roteador para o dispositivo do player |
| AEM Screens Player travado | É recomendável ter um aplicativo watchdog que garanta que o Player do AEM Screens sempre seja executado |
| Configurações perdidas do AEM Screens Player | Verificar conexão com AEM servidor |
| O AEM Screens Player não inicia automaticamente após a reinicialização/reinicialização do Player | Verificar a pasta inicial do SO ou o procedimento de inicialização |
| O AEM Screens Player mostra conteúdo errado/antigo | Verificar conexão de rede |

### Atualizações para o Player do AEM Screens {#updates-for-aem-screens-player}

Existem dois tipos de atualizações para o Player do AEM Screens:

| **Método** | **Detalhes** | **via Remoto** | **Automatizado** | **0 Tempo de inatividade** |
|---|---|---|---|---|
| Atualização de firmware | Aplicado em Players instalados existentes via comando remoto. Após a atualização, o Player será recarregado automaticamente com o conteúdo existente. | Sim | Personalizado | Quase - 1 a 3 segundos |
| Atualizações do Shell do Player | Este é um novo executável a ser implantado no Player. É necessário fazer uma cópia remota do novo binário no player, interromper a execução atual e iniciar a nova versão. Pode ser necessário fazer um novo download do pré-carregamento dos pacotes. | Sim (via shell remoto) | Personalizado | Não |

## Diretrizes de seleção de hardware para o dispositivo reprodutor {#hardware-selection-guidelines-for-player-device}

A seção a seguir fornece as diretrizes de seleção de hardware para um Projeto do Screens:

* Gerar sempre componentes de nível ***Comercial*** ou ***Industrial*** para o reprodutor do PC e o Painel de Exibição ou Projetor.

* Sempre envolva-se com fornecedores que atendem ao mercado de sinalização digital.
* Considere sempre fatores ambientais como a temperatura ambiente e a humidade relativa.
* Verifique sempre os requisitos de energia e o condicionamento de energia.
* Analise cuidadosamente as necessidades de desempenho e as portas de E/S necessárias para o aplicativo.

A tabela a seguir resume as configurações de hardware com casos de uso típicos de um projeto do AEM Screens:

<table>
 <tbody>
  <tr>
   <td>Configuração do reprodutor</td>
   <td>Processador</td>
   <td>Memória</td>
   <td>SSD de armazenamento</td>
   <td>GPU</td>
   <td>Exibir</td>
   <td>E/S</td>
   <td>Casos de uso típicos</td>
  </tr>
  <tr>
   <td>Básico</td>
   <td>Processador Intel® Atom de núcleo duplo, i3 ou núcleo quádruplo básico</td>
   <td><p>4 GB de memória</p> <p>2 MB de cache</p> </td>
   <td><p>・ChromeOS 32 GB</p> <p>・Windows 128GB</p> </td>
   <td>OnBoard</td>
   <td>1920x1080</td>
   <td>DVI,<br /> Ethernet / Wireless,<br /> 2xUSB</td>
   <td>
    <ul>
     <li>Looping de tela cheia padrão<br /> </li>
     <li>Divisão de dia</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Padrão</td>
   <td>Quad Core, processador Intel® Core i5</td>
   <td><p>8 GB de memória</p> <p>4 MB de cache</p> </td>
   <td>128 GBB</td>
   <td>OnBoard</td>
   <td>3840x2160 (4K)</td>
   <td>DVI, HDMI<br /> Ethernet / Wireless,<br /> 2xUSB</td>
   <td>
    <ul>
     <li>Conteúdo dinâmico de fonte única</li>
     <li>Simples interativo</li>
     <li>1-3 Layouts de zonas</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Avançado </td>
   <td>Quad Core com hiperthreading, processador Intel® Core i7</td>
   <td><p>16 GB de memória</p> <p>8 MB de cache</p> </td>
   <td>256 GB</td>
   <td>GPU de gráficos dedicados</td>
   <td>3840x2160 (4K)</td>
   <td>DVI, HDMI<br /> Ethernet / Wireless,<br /> 4xUSB</td>
   <td>
    <ul>
     <li>4 ou mais zonas de conteúdo, reprodução de vídeo simultâneo</li>
     <li>Multipáginas interativas</li>
     <li>Acionadores de dados de várias fontes</li>
    </ul> </td>
  </tr>
 </tbody>
</table>
