---
title: Reconhecimento de voz no AEM Screens
description: Saiba mais sobre o reconhecimento de voz e como usá-lo no AEM Screens.
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 6cf0aa9f-7bac-403f-a113-51727c1f5374
source-git-commit: 6720e20f5254e869bde814bd167730e426d0f8fe
workflow-type: tm+mt
source-wordcount: '1092'
ht-degree: 2%

---

# Reconhecimento de voz no AEM Screens {#voice-recognition}

>[!IMPORTANT]
>
>**Informações importantes sobre privacidade**
>
>Ao usar o recurso de reconhecimento de voz, siga todas as diretrizes legais e éticas aplicáveis à sua região. Essas diretrizes incluem, mas não se limitam a, fornecer um aviso visível aos usuários finais de que o reprodutor está usando reconhecimento de voz). O Adobe não recebe, armazena ou processa qualquer informação relacionada à voz. Os players do AEM Screens usam a API de fala da Web padrão incorporada ao mecanismo de navegação. Nos bastidores, essa API envia uma forma de onda de sua fala para os servidores da Google para conversão de fala em texto. O reprodutor corresponde o texto com as palavras-chave configuradas.
>
>Consulte o [White-paper de Privacidade da Google sobre a API de fala na Web](https://www.google.com/chrome/privacy/whitepaper.html#speech) para obter mais detalhes.


O recurso de reconhecimento de voz permite a alteração de conteúdo em um canal do AEM Screens orientado por interação de voz.

Um Autor de conteúdo pode configurar uma exibição para ser ativada por voz. O objetivo desse recurso é permitir que os clientes usem a fala como um método de interação com suas telas. Alguns casos de uso semelhantes incluem encontrar recomendações de produtos em lojas, solicitar itens de menu em lanchonetes e restaurantes. Esse recurso aumenta a acessibilidade para os usuários e pode melhorar muito a experiência do cliente.

>[!NOTE]
>O hardware do player deve suportar entrada de voz, como um microfone.

## Implementando o reconhecimento de voz {#implementing}

>[!IMPORTANT]
> O recurso de reconhecimento de voz está disponível apenas no SO Chrome e em players Windows.

Para implementar o reconhecimento de voz em seu projeto do AEM Screens, ative o reconhecimento de voz para a Exibição e associe cada canal a uma tag exclusiva para acionar uma transição de canal.

A seção a seguir descreve como ativar e usar o recurso de reconhecimento de voz em um projeto do AEM Screens.

## Exibição de conteúdo em tela cheia ou no Switch de canal de tela dividida {#sequence-channel}

Antes de usar um recurso de reconhecimento de voz, verifique se você tem um projeto e um canal com conteúdo configurado para o seu projeto.

1. O exemplo a seguir mostra um projeto de demonstração chamado **VoiceDemo** e três canais de sequência **Main**, **ColdDrinks** e **HotDrinks**, como mostrado na figura abaixo.

   ![imagem](assets/voice-recognition/vr-1.png)

   >[!NOTE]
   >
   >Para saber como criar um canal ou adicionar conteúdo a um canal, consulte [Criação e Gerenciamento de Canais](/help/user-guide/managing-channels.md)

   Ou,

   Você pode criar três canais de sequência **Principal**, **ColdDrinks** e **HotDrinks**, e mais um canal Screens dividido 1x2 **SplitScreen**, conforme mostrado na figura abaixo.

   ![imagem](assets/voice-recognition/vr-emb-1.png)

1. Navegue até cada um dos canais e adicione o conteúdo. Por exemplo, navegue até **VoiceDemo** > **Canais** > **Principal** e clique no canal. Clique em **Editar** na barra de ações e, em seguida, adicione o conteúdo (imagens/vídeos) de acordo com sua necessidade. Da mesma forma, adicione conteúdo aos canais **ColdDrinks** e **HotDrinks**.

   Os canais agora contêm ativos (imagens), como mostrado nas figuras abaixo.

   **Principal**:

   ![imagem](assets/voice-recognition/vr-4.png)

   **Refrigerantes**:

   ![imagem](assets/voice-recognition/vr-3.png)

   **HotDrinks**:

   ![imagem](assets/voice-recognition/vr-2.png)

   Se você adicionou o canal de Divisão do Screens ao seu projeto, navegue até **SplitScreen** e arraste e solte duas sequências inseridas. Adicione caminhos aos canais **ColdDrinks** e **HotDrinks** conforme mostrado na figura abaixo.
   ![imagem](assets/voice-recognition/vr-emb-6.png)


### Configuração de tags para canais {#setting-tags}

Após adicionar o conteúdo aos canais, navegue até cada um deles e adicione as tags apropriadas para acionar o reconhecimento de voz.

Siga as etapas abaixo para adicionar tags ao seu canal:

1. Navegue até cada um dos canais e adicione o conteúdo. Por exemplo, navegue até **VoiceDemo** > **Canais** > **Principal** e clique no canal.

1. Clique em **Propriedades** na barra de ações.

   ![imagem](assets/voice-recognition/vr-5.png)

1. Navegue até a guia **Noções básicas** e clique em uma marca existente no campo **Marcas** ou crie uma.

   Você pode criar uma tag digitando um novo nome para a tag e pressionando a tecla `return`, como mostrado na figura abaixo:

   ![imagem](assets/voice-recognition/vr-6.png)

   Ou,

   Você também pode criar tags da instância do AEM antecipadamente para o seu projeto e selecioná-las. Depois de seguir as etapas explicadas em [Criando Tags](#creating-tags), você pode clicar na tag do local e adicioná-la ao canal, conforme mostrado na figura abaixo:

   ![imagem](assets/voice-recognition/vr-tag1.png)

1. Da mesma forma, adicione uma tag denominada **hot** ao canal **HotDrinks**.

1. Se você estiver usando um canal de Screens Dividido, adicione as marcas (**hot** e **cold**) às propriedades de canal **SplitScreen**, conforme mostrado na figura abaixo.

   ![imagem](assets/voice-recognition/vr-emb-7.png)

1. Clique em **Salvar e fechar** depois de concluído.


### Criação de tags {#creating-tags}

Siga as etapas abaixo para criar tags:

1. Navegue até a instância do AEM.

1. Clique no ícone de ferramentas > **Marcação**.
   ![imagem](assets/voice-recognition/vr-7.png)

1. Clique em **Criar** > **Criar Namespace**.
   ![imagem](assets/voice-recognition/vr-tag3.png)

1. Insira o nome do seu projeto, por exemplo, **VoiceDemo** e clique em **Criar**.

1. Clique no projeto **VoiceDemo** e clique em **Criar Marca** na barra de ações.
   ![imagem](assets/voice-recognition/vr-tag4.png)

1. Insira o nome da sua marca e clique em **Enviar**.
   ![imagem](assets/voice-recognition/vr-tag5.png)

Agora, você pode usar essas tags no seu projeto do AEM Screens.

### Atribuição de canal a uma exibição e Ativação do reconhecimento de voz {#channel-assignment}

1. Crie uma exibição na pasta **Locais**, conforme mostrado na figura abaixo.

   ![imagem](assets/voice-recognition/vr-loc.png)

   >[!NOTE]
   >Para saber como atribuir um canal a uma exibição, consulte [Criação e Gerenciamento de Exibições](/help/user-guide/managing-displays.md).

1. Atribua os canais **Principal**, **ColdDrinks** e **HotDrinks** à sua **LobbyDisplay**. Além disso, se você estiver usando o canal **SplitScreen** para o seu projeto, certifique-se de atribuir isso à exibição.

   >[!NOTE]
   >Se você tiver criado um canal de tela dividida, atribua o canal **SplitScreen** à exibição.

1. Defina as seguintes propriedades para cada canal, ao atribuir o canal.

   | **Nome do canal** | **Prioridade** | **Eventos com Suporte** |
   |---|---|---|
   | Principal | 2 | Carga inicial, tela ociosa, temporizador |
   | HotDrinks | 1 | Interação do usuário |
   | ColdDrinks | 1 | Interação do usuário |
   | SplitScreen | 1 | Interação do usuário |

   >[!NOTE]
   >
   >Para saber como atribuir um canal a uma exibição, consulte [Criação e Gerenciamento de Exibições](/help/user-guide/managing-displays.md).

1. Após atribuir canais a uma exibição, navegue até **LobbyDisplay** e clique na exibição. Clique em **Propriedades** na barra de ações.

1. Navegue até a guia **Exibição** e habilite a opção **Voz habilitada** em **Conteúdo**.

   ![imagem](assets/voice-recognition/vr-disp.png)

   >[!IMPORTANT]
   >É obrigatório ativar o recurso de reconhecimento de voz na exibição.

### Visualização de conteúdo no Chrome Player {#viewing-content}

Quando as etapas anteriores forem concluídas, você poderá registrar seu dispositivo Chrome para exibir a saída.

>[!NOTE]
>Consulte [Registro de Dispositivo](device-registration.md).

**Saída desejada para o canal de sequência**

O canal **Principal** está reproduzindo seu conteúdo. No entanto, quando você usa palavras com a palavra-chave **hot**, como *Gostaria de tomar um drinque quente*, o canal começa a reproduzir o conteúdo do canal **HotDrinks**.

Da mesma forma, se você usar uma palavra com a palavra-chave **cold**, como *Gostaria de fazer algo frio*, o canal começará a reproduzir o conteúdo do canal **ColdDrinks**.

**Saída Desejada para o Canal Dividido do Screens**

O canal **Principal** está reproduzindo seu conteúdo. No entanto, quando você usa palavras com a palavra-chave **hot** e **cold** juntas, como *Eu gostaria de ver o menu de bebidas quentes e frias*, o canal reproduz o conteúdo do canal **SplitScreen**. Se você retornar *ao menu principal*, ele será revertido para o canal **Principal**.
