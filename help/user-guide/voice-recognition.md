---
title: Reconhecimento de voz no AEM Screens
description: Saiba mais sobre o reconhecimento de voz e como usá-lo no AEM Screens.
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 6cf0aa9f-7bac-403f-a113-51727c1f5374
source-git-commit: fff2df02661fc3fb3098be40e090b8bc6925bcc2
workflow-type: tm+mt
source-wordcount: '1088'
ht-degree: 2%

---

# Reconhecimento de voz no AEM Screens {#voice-recognition}

>[!IMPORTANT]
>
>**Informações importantes sobre privacidade**
>
>Ao usar o recurso de reconhecimento de voz, siga todas as diretrizes legais e éticas aplicáveis à sua região (incluindo, mas não limitado a, fornecer um aviso visível aos usuários finais de que o reprodutor está usando o Reconhecimento de voz). O Adobe não recebe, armazena ou processa qualquer informação relacionada à voz. Os players do AEM Screens usam a API de fala da Web padrão incorporada ao mecanismo de navegação. Nos bastidores, essa API envia uma forma de onda de sua fala para os servidores da Google para conversão de fala em texto e esse texto é comparado pelo reprodutor com as palavras-chave configuradas.
>
>Consulte [White paper de privacidade do Google sobre a API de fala na Web](https://www.google.com/chrome/privacy/whitepaper.html#speech) para obter mais detalhes.


O recurso de reconhecimento de voz permite a alteração de conteúdo em um canal do AEM Screens orientado por interação de voz.

Um autor de conteúdo pode configurar uma exibição para ser ativada por voz. O objetivo desse recurso é permitir que os clientes usem a fala como um método de interação com suas telas. Alguns casos de uso semelhantes incluem encontrar recomendações de produtos em lojas, solicitar itens de menu em lanchonetes e restaurantes. Esse recurso aumenta a acessibilidade para os usuários e pode melhorar muito a experiência do cliente.

>[!NOTE]
>O hardware do player deve suportar entrada de voz, como um microfone.

## Implementando o reconhecimento de voz {#implementing}

>[!IMPORTANT]
> O recurso de reconhecimento de voz está disponível apenas no Chrome OS e em players Windows.

Para implementar o reconhecimento de voz em seu projeto do AEM Screens, ative o reconhecimento de voz para a Exibição e associe cada canal a uma tag exclusiva para acionar uma transição de canal.

A seção a seguir descreve como ativar e usar o recurso de reconhecimento de voz em um projeto do AEM Screens.

## Exibição de conteúdo em tela cheia ou no Switch de canal de tela dividida {#sequence-channel}

Antes de usar o recurso de reconhecimento de voz, verifique se você tem um projeto e um canal com conteúdo configurado para o seu projeto.

1. O exemplo a seguir mostra um projeto de demonstração chamado **VoiceDemo** e três canais de sequência **Principal**, **ColdDrinks**, e **HotDrinks**, conforme mostrado na figura abaixo.

   ![imagem](assets/voice-recognition/vr-1.png)

   >[!NOTE]
   >
   >Para saber como criar um canal ou adicionar conteúdo a um canal, consulte [Criação e gerenciamento de canais](/help/user-guide/managing-channels.md)

   Ou,

   Você pode criar três canais de sequência **Principal**, **ColdDrinks**, e **HotDrinks** e mais um canal de Telas divididas 1x2 **SplitScreen** conforme mostrado na figura abaixo.

   ![imagem](assets/voice-recognition/vr-emb-1.png)

1. Navegue até cada um dos canais e adicione o conteúdo. Por exemplo, navegue até **VoiceDemo** > **Canais** > **Principal** e clique no canal. Clique em **Editar** na barra de ação, em seguida, adicione o conteúdo (imagens/vídeos) de acordo com sua necessidade. Da mesma forma, adicione conteúdo a ambos **ColdDrinks** e a variável **HotDrinks** canal.

   Os canais agora contêm ativos (imagens), como mostrado nas figuras abaixo.

   **Principal**:

   ![imagem](assets/voice-recognition/vr-4.png)

   **ColdDrinks**:

   ![imagem](assets/voice-recognition/vr-3.png)

   **HotDrinks**:

   ![imagem](assets/voice-recognition/vr-2.png)

   Se você tiver adicionado o canal de Telas divididas ao seu projeto, navegue até **SplitScreen** e arraste e solte duas sequências incorporadas e adicione caminhos a ambas as **ColdDrinks** e **HotDrinks** como mostrado na figura abaixo.
   ![imagem](assets/voice-recognition/vr-emb-6.png)


### Configuração de tags para canais {#setting-tags}

Após adicionar o conteúdo aos canais, navegue até cada um deles e adicione as tags apropriadas para acionar o reconhecimento de voz.

Siga as etapas abaixo para adicionar tags ao seu canal:

1. Navegue até cada um dos canais e adicione o conteúdo. Por exemplo, navegue até **VoiceDemo** > **Canais** > **Principal** e clique no canal.

1. Clique em **Propriedades** na barra de ações.

   ![imagem](assets/voice-recognition/vr-5.png)

1. Navegue até a **Noções básicas** e clique em uma tag existente na guia **Tags** ou crie um.

   Você pode criar uma tag digitando um novo nome para ela e pressionando `return` conforme mostrado na figura abaixo:

   ![imagem](assets/voice-recognition/vr-6.png)

   Ou,

   Você também pode criar tags da instância do AEM antecipadamente para o seu projeto e clicar nelas. Depois de seguir as etapas explicadas em [Criação de tags](#creating-tags), você pode clicar na tag do local e adicioná-la ao canal, como mostrado na figura abaixo:

   ![imagem](assets/voice-recognition/vr-tag1.png)

1. Da mesma forma, adicione a tag intitulada como **quente** para o **HotDrinks** canal.

1. Se você estiver usando um canal de Telas divididas, adicione ambas as tags (**quente** e **frio**) para o **SplitScreen** propriedades do canal, conforme mostrado na figura abaixo.

   ![imagem](assets/voice-recognition/vr-emb-7.png)

1. Clique em **Salvar e fechar** quando terminar.


### Criação de tags {#creating-tags}

Siga as etapas abaixo para criar tags:

1. Navegue até a instância do AEM.

1. Clique no ícone Ferramentas > **Marcação**.
   ![imagem](assets/voice-recognition/vr-7.png)

1. Clique em **Criar** > **Criar namespace**.
   ![imagem](assets/voice-recognition/vr-tag3.png)

1. Insira o nome do projeto, por exemplo, **VoiceDemo** e clique em **Criar**.

1. Clique em **VoiceDemo** projeto e clique em **Criar tag** na barra de ações.
   ![imagem](assets/voice-recognition/vr-tag4.png)

1. Insira o nome da tag e clique em **Enviar**.
   ![imagem](assets/voice-recognition/vr-tag5.png)

Agora, você pode usar essas tags no seu projeto do AEM Screens.

### Atribuição de canal a uma exibição e Ativação do reconhecimento de voz {#channel-assignment}

1. Criar uma exibição no **Localizações** conforme mostrado na figura abaixo.

   ![imagem](assets/voice-recognition/vr-loc.png)

   >[!NOTE]
   >Para saber como atribuir um canal a uma exibição, consulte [Criando e Gerenciando Exibições](/help/user-guide/managing-displays.md).

1. Atribuir os canais **Principal**, **ColdDrinks**, e **HotDrinks** ao seu **ExibiçãoLobby**. Além disso, se você estiver usando a variável **SplitScreen** canal do seu projeto, atribua essa ferramenta à exibição.

   >[!NOTE]
   >Se você tiver criado um canal de tela dividida, atribua a **SplitScreen** canal também ao seu vídeo.

1. Defina as seguintes propriedades para cada canal, ao atribuir o canal.

   | **Nome do canal** | **Prioridade** | **Eventos suportados** |
   |---|---|---|
   | Principal | 2 | Carga inicial, tela ociosa, temporizador |
   | HotDrinks | 1 | Interação do usuário |
   | ColdDrinks | 1 | Interação do usuário |
   | SplitScreen | 1 | Interação do usuário |

   >[!NOTE]
   >
   >Para saber como atribuir um canal a uma exibição, consulte [Criando e Gerenciando Exibições](/help/user-guide/managing-displays.md).

1. Depois de atribuir canais a uma exibição, navegue até o **ExibiçãoLobby** e clique na tela. Clique em **Propriedades** na barra de ações.

1. Navegue até a **Exibir** e ativar **Voz habilitada** opção em **Conteúdo**.

   ![imagem](assets/voice-recognition/vr-disp.png)

   >[!IMPORTANT]
   >É obrigatório ativar o recurso de reconhecimento de voz na exibição.

### Exibição de conteúdo no Chrome Player {#viewing-content}

Quando as etapas anteriores forem concluídas, você poderá registrar seu dispositivo Chrome para exibir a saída.

>[!NOTE]
>Consulte [Registro do dispositivo](device-registration.md).

**Saída desejada para o canal de sequência**

A variável **Principal** o canal está reproduzindo seu conteúdo, mas quando você usa palavras com palavras-chave **quente** como *Gostaria de uma bebida quente*, o canal começa a reproduzir o conteúdo do **HotDrinks** canal.

Da mesma forma, se você usar uma palavra com uma palavra-chave **frio** como *Eu gostaria de ter algo frio*, o canal começa a reproduzir o conteúdo do **ColdDrinks** canal.

**Saída desejada para o canal de Telas divididas**

A variável **Principal** o canal está reproduzindo seu conteúdo. No entanto, quando você usa palavras com palavras-chave **quente** e **frio** em conjunto, como *Gostaria de ver o cardápio de bebidas quentes e frias*, o canal reproduzirá o conteúdo do **SplitScreen** canal. Se você disser *voltar ao menu principal*, ele reverte para a variável **Principal** canal.
