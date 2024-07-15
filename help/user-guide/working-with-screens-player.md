---
title: Trabalhar com o AEM Screens Player
description: Saiba mais sobre como trabalhar com o AEM Screens Player, a interface do Administrador e o alternador de canais.
contentOwner: jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: 4faac090-ad8a-4d7e-a502-6fb63f6b2761
source-git-commit: a89aec16bb36ecbde8e417069e9ed852363acd82
workflow-type: tm+mt
source-wordcount: '1067'
ht-degree: 0%

---

# Trabalhar com o AEM Screens Player

É possível gerenciar o conteúdo do canal e outras configurações no AEM Screens Player.

>[!NOTE]
>
>Pressione ***Ctrl+Cmd+F*** para sair do modo de tela cheia do OS X AEM Screens Player.

Depois de atribuir um canal a uma exibição, o AEM Screens Player exibe o conteúdo. Você pode definir as configurações do reprodutor usando as preferências da interface do administrador (no painel) ou a partir do próprio reprodutor.

## Uso do painel de dispositivos {#using-the-device-dashboard}

Você pode configurar as preferências para o seu dispositivo no painel Dispositivo, acessível por meio da instância de criação do AEM.

1. Navegue até o painel do dispositivo no seu projeto, por exemplo, ***Testar projeto*** > ***Dispositivos***.

   Clique em **Dispositivos** e **Gerenciador de Dispositivos** na barra de ações.

   ![chlimage_1-66](assets/chlimage_1-66.png)

1. Clique no dispositivo para abrir o painel de dispositivos.

   ![chlimage_1-67](assets/chlimage_1-67.png)

1. Verifique o painel **PREFERÊNCIAS**. Você pode habilitar ou desabilitar a **Interface do Administrador** e a **Alternadora de Canais** para o seu reprodutor a partir dessas duas opções.

   ![chlimage_1-68](assets/chlimage_1-68.png)

### A interface do usuário do administrador {#the-admin-ui}

Habilitar a **Interface do usuário do administrador** no painel de preferências permite que o usuário abra as configurações do administrador no Screens Player. Além disso, se você desativar essa opção no painel do dispositivo, o usuário não poderá abrir a interface de usuário do administrador no reprodutor.

Para exibir a interface do administrador no Screens Player, pressione o canto superior esquerdo para abrir o menu Admin, no AEM Screens Player habilitado para toque ou usando o mouse. As informações são exibidas após a conclusão do registro e do carregamento dos canais.

>[!NOTE]
>
>Além disso, você pode exibir o tempo de atividade do aplicativo AEM Screens Player para verificar o status de integridade do aplicativo.

![chlimage_1-3](assets/chlimage_1-3.gif)

#### Acessando as Opções do Menu de Configuração {#configuration-options}

Você pode atualizar suas configurações se clicar na opção **Configuração** no menu lateral, como mostrado na figura abaixo:

![screen_shot_2018-10-15at101257am](assets/screen_shot_2018-10-15at101257am.png)

O menu Configuration permite modificar as seguintes configurações:

* Redefinir **Firmware**, **Preferências** ou **Para Fábrica** nesta caixa de diálogo.

* Especifique o número máximo de arquivos de log que deseja manter para um AEM Screens Player em **Nº máx. de arquivos de log a serem mantidos**.

* Habilite ou desabilite o **Menu de Administração**, o **Alternador de Canal** e a **Interface do Usuário da Atividade** para o Screens Player.

  Se a **Interface do usuário da atividade** estiver habilitada no menu **Configuração**, o AEM Screens Player exibirá as *notificações de atividade do player* no canto superior direito do player, como mostrado na figura abaixo.

  ![imagem](/help/user-guide/assets/activity_ui.png)

>[!NOTE]
>
>A opção **Atualizar firmware** funciona somente no Cordova, como em players Android™.

>[!NOTE]
>
>É recomendável que a **Interface do usuário do administrador** seja desabilitada nas Implantações de Produção.

#### Acessando as Opções de Menu do Cache de Conteúdo {#content-cache-options}

Você pode limpar o cache de canais e aplicativos na interface do usuário do Administrador no AEM Screens Player.

Clique no **Cache de Conteúdo** no painel lateral para poder atualizar o cache.

![screen_shot_2018-10-15at105717am](assets/screen_shot_2018-10-15at105717am.png)

### O seletor de canais {#the-channel-switcher}

Habilitar o **Alternador de canais** no painel de preferências permite que o usuário abra as configurações de seleção de canais no Screens Player.

Além disso, se você desativar essa opção no painel do dispositivo, o usuário não poderá controlar as preferências de canal no Screens Player.

Você pode alternar e controlar as configurações do seu canal no Screens Player.

Para ver o alternador de canal do reprodutor, pressione o canto inferior esquerdo para abrir o alternador de canal que permite alternar canais e outros recursos.

![chlimage_1-69](assets/chlimage_1-69.png)

>[!NOTE]
>
>Você também pode ativar ou desativar o menu de administração e o alternador de canal do reprodutor no Screens Player.
>
>(Consulte *Alterar preferências do Screens Player*, conforme mencionado na seção abaixo).

### Gerenciamento de preferências no AEM Screens Player

Também é possível alterar as configurações da interface do administrador e do alternador de canal no próprio reprodutor.

Para alterar as preferências do Player:

1. Pressione e segure no canto superior esquerdo do canal ocioso para abrir o painel de administração.
1. Navegue até **Configuração** no menu de ação esquerdo.
1. Habilite ou desabilite a configuração para a **Interface do Administrador** ou o **Alternador de Canais**.

![screen_shot_2018-10-15at101257am-1](assets/screen_shot_2018-10-15at101257am-1.png)

## Solução de problemas do AEM Screens Player

Você pode solucionar vários problemas associados ao AEM Screens Player (hardware e software):

| **Problemas** | **Recommendations** |
|---|---|
| O armazenamento do player está cheio | Eliminar arquivos desnecessários |
| O player perdeu a rede | Use o cabo Cat-5 ou Cat-6. Para Wi-Fi, reduza a distância do roteador até o dispositivo de reprodução |
| Falha no AEM Screens Player | É recomendável ter um aplicativo de vigia que garanta que o AEM Screens Player sempre seja executado |
| O AEM Screens Player perdeu as configurações | Verificar conexão com o servidor AEM |
| O AEM Screens Player não é iniciado automaticamente após a reinicialização ou reinicialização do Player | Verifique a pasta de início do SO ou o procedimento de inicialização |
| O AEM Screens Player mostra conteúdo incorreto ou antigo | Verificar conexão de rede |

### Atualizações do AEM Screens Player

Há dois tipos de atualizações para o AEM Screens Player:

| **Método** | **Detalhes** | **por meio de Remoto** | **Automatizado** | **Tempo de inatividade** |
|---|---|---|---|---|
| Atualização de firmware | Aplicado em players instalados existentes por meio de comando remoto. Após a atualização, o Player é recarregado automaticamente com o conteúdo existente. | Sim | Personalizado | Quase - 1-3 segundos |
| Atualizações do shell do player | Um novo executável que é implantado no Player. Essa funcionalidade exige que você copie remotamente o novo binário no reprodutor, interrompa a versão em execução no momento e inicie a nova versão. Pode ser necessário baixar o pré-carregamento dos pacotes novamente. | Sim (por meio de shell remoto) | Personalizado | Não |

## Diretrizes de seleção de hardware para o dispositivo player {#hardware-selection-guidelines-for-player-device}

A seção a seguir fornece as diretrizes de seleção de hardware para um projeto do Screens:

* Sempre adquira componentes de nível ***Comercial*** ou ***Industrial*** para PC Player e Painel de Vídeo ou Projetor.

* Sempre interaja com fornecedores que atendem ao mercado de sinalização digital.
* Sempre considere fatores ambientais como temperatura ambiente e umidade relativa.
* Sempre analise os requisitos de energia e o condicionamento de energia.
* Analise cuidadosamente as necessidades de desempenho e as portas de E/S necessárias para o aplicativo.

A tabela a seguir resume as configurações de hardware com casos de uso típicos de um projeto AEM Screens:

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
   <td>Processador Intel® Atom Dual Core, i3 ou quad core básico</td>
   <td><p>4 GB de memória</p> <p>2 MB de cache</p> </td>
   <td><p>*ChromeOS 32 GB</p> <p>*Windows 128 GB</p> </td>
   <td>OnBoard</td>
   <td>1920 x 1080</td>
   <td>Ethernet DVI<br /> / Wireless<br /> 2xUSB</td>
   <td>
    <ul>
     <li>Looping de Tela Inteira Padrão<br /> </li>
     <li>Divisão de dia</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Padrão</td>
   <td>Processador Intel® Core™ i5 de 4 núcleos</td>
   <td><p>8 GB de memória</p> <p>4 MB de cache</p> </td>
   <td>128 GB</td>
   <td>OnBoard</td>
   <td>3840x2160 (<code>4K</code>)</td>
   <td>DVI, HDMI<br /> Ethernet / wireless,<br /> 2 x USB</td>
   <td>
    <ul>
     <li>Conteúdo dinâmico único do Source</li>
     <li>Interativo simples</li>
     <li>1-3 Layouts de zona</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Avançado </td>
   <td>Quad Core com hyperthreading, processador Intel® Core™ i7</td>
   <td><p>16 GB de memória</p> <p>8 MB de cache</p> </td>
   <td>256 GB</td>
   <td>GPU gráfica dedicada</td>
   <td>3840x2160 (<code>4K</code>)</td>
   <td>DVI, HDMI<br /> Ethernet / wireless,<br /> 4xUSB</td>
   <td>
    <ul>
     <li>4 ou mais zonas de conteúdo, reprodução de vídeo simultânea</li>
     <li>Interativo de várias páginas</li>
     <li>Acionadores de dados de várias Source</li>
    </ul> </td>
  </tr>
 </tbody>
</table>
