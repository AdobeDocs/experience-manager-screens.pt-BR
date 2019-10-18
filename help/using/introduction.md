---
title: Introdução ao [!UICONTROL AEM Screens]
seo-title: Guia de práticas recomendadas para projetos do [!UICONTROL AEM Screens]
description: Esta página é uma seção de introdução ao AEM Screens
seo-description: Esta página fornece uma introdução ao AEM Screens
translation-type: tm+mt
source-git-commit: 55999ae9ead7ab8986f4dcb69b0bbaa46933c9ec

---


# Introdução ao AEM Screens {#introduction}

**O AEM (Adobe Experience Manager) Screens** é uma Solução de Sinalização Digital que permite criar, publicar e reproduzir experiências digitais dinâmicas e interativas envolvendo diferentes tipos de telas de exibição no local, em conjunto com uma estratégia abrangente de marketing digital global.

O AEM Screens permite que você crie:

* **placas de menu digitais dedicadas**
* **recomendações de produto**
* **imagens de fundo do estilo de vida**

Além disso, o Screens fornece vários aplicativos exclusivos para clientes e funcionários com base no domínio em que eles são implantados, como:

* **exibições interativas**
* **descoberta**
* **marca**
* **adicionar ambição ao seu ambiente**

Criar e gerenciar uma rede de sinalização digital usando o AEM Screens é simples e intuitivo. Um aplicativo player hospeda canais de conteúdo criados para o AEM Screens por clientes ou parceiros de implementação. *Os locais* gerenciam uma hierarquia de localização predefinida e contêm exibições. Cada *exibição* tem um painel que mostra dispositivos e telas diferentes conectados. O conteúdo para o AEM Screens é gerenciado em *canais*. *O AEM Screens Player* renderiza o conteúdo presente nos canais em exibições.



>[!NOTE]
>
>Para saber mais detalhes sobre os diferentes recursos em um desenvolvimento e gerenciamento de projetos do AEM Screens, consulte o Guia **[do Usuário do](https://helpx.adobe.com/experience-manager/6-5/screens/user-guide.html)** AEM Screens.

## AEM Sites versus AEM Screens {#aem-sites-screens}

> [!NOTE]
>
> Se sua equipe de implementação tiver experiência em trabalhar com aplicativos do AEM Sites, é importante entender a diferença entre os Sites do AEM e as telas do AEM.

O AEM Screens fornece uma plataforma unificada de criação/reprodução para implantar conteúdo em dispositivos de sinalização digital em espaços públicos. Embora o autor da experiência deva se esforçar para manter a consistência na Web e nos canais no local, há algumas diferenças que devem ser observadas.

* **Tempo de interrupção**: Normalmente, as páginas da Web são projetadas para fornecer uma grande variedade de informações que podem ser consumidas por um período de tempo relativamente mais longo. Em contraste, as experiências digitais no local devem antecipar as necessidades do visualizador e fornecer orientações claras e concisas sobre como e por que o usuário deve se envolver. Isso resulta em experiências mais direcionadas, com curadoria e contextuais.

* **Distância** de exibição: As distâncias de visualização são geralmente maiores ou mais distantes do que a distância de visualização típica que os usuários experimentam em um site. Como resultado, o tamanho do texto deve normalmente ser maior e o espaçamento entre o texto, as imagens e outros conteúdos complementares deve ser testado com base no tamanho e posicionamento previstos do ecrã no espaço físico.

* **Persistência**: O estado conectado do dispositivo do player nunca deve poder influenciar se as experiências digitais são ou não entregues ao usuário. O player deve ser projetado para que uma ou mais experiências sempre persistam e possam ser entregues independentemente do estado conectado do dispositivo do player.

* **Segmentação** do ciclo de mídia: Configurar cada dispositivo de player para ter seu próprio segmento de loop garante que o conteúdo localizado possa ser facilmente criado, publicado e reproduzido dentro da experiência digital geral. Os ativos de mídia contidos nos canais de sequência incorporados são adicionados ao segmento de loop anterior e oferecem a oportunidade de direcionar um segmento de loop de mídia para cada agrupamento de local.

* **Experiências** interativas: Um aplicativo de quiosque habilitado para toque pode ser criado e entregue em um canal do Screens usando o AEM e o editor do SPA. É uma prática recomendada aplicar propriedades consistentes de design de canal, um temporizador de inatividade para redefinir a experiência e uma chamada de ação clara para quais tarefas o aplicativo pode executar. A página de aterrissagem deve consistir em elementos digitais chave projetados para transmitir valor, atrair o usuário para a tela e solicitar que o usuário se envolva.

O AEM Screens fornece uma estrutura para implantar conteúdo em dispositivos físicos. O conteúdo é atribuído a Canais no Screens, que podem conter conteúdo de mídia ou aplicativos de tela de toque. Dentro dessa estrutura, um aplicativo do AEM Site pode ser fornecido como conteúdo por meio de um Canal.

Antes de ser solto em um Canal no Screens, um Site do AEM deve ser formatado para uso nas dimensões do dispositivo de exibição para o qual ele se destina.

> [!NOTE]
>
> Muitos componentes do AEM Sites não são compatíveis com o AEM Screens. O AEM Screens vem com muitos de seus próprios componentes prontos para uso, permitindo que você crie experiências digitais sem precisar de personalização. Se os requisitos do projeto permitirem, use a funcionalidade integrada do AEM Screens, onde possível.
