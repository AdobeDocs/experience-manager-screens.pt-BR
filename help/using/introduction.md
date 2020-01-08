---
title: Introdução ao [!UICONTROL AEM Screens]
seo-title: Guia de práticas recomendadas para projetos do [!UICONTROL AEM Screens]
description: Esta página é uma seção de introdução ao AEM Screens
seo-description: Esta página fornece uma introdução ao AEM Screens
translation-type: tm+mt
source-git-commit: 8a80ea5c79bfd9890211bd7e0d958ab0d4c2d4b6

---


# Introdução ao AEM Screens {#introduction}

O **AEM (Adobe Experience Manager) Screens** é uma Solução de sinalização digital que permite criar, publicar e reproduzir experiências digitais dinâmicas e interativas envolvendo diferentes tipos de telas no local, em conjunto com uma estratégia abrangente de marketing digital omnicanal.

O AEM Screens permite criar:

* **placas de menu digitais dedicadas**
* **recomendações de produto**
* **imagens de fundo do estilo de vida**

Além disso, o Screens fornece várias aplicações exclusivas para clientes e funcionários com base no domínio em que são implantados, como:

* **exibições interativas**
* **wayfinding**
* **marcas**
* **adicionar ambiência ao ambiente**

Criar e gerenciar uma rede de sinalização digital usando o AEM Screens é simples e intuitivo. Um aplicativo de reprodução hospeda os canais de conteúdo criados para o AEM Screens por clientes ou parceiros de implementação. Os *locais* gerenciam uma hierarquia de localização predefinida e contêm exibições. Cada *exibição* tem um painel que mostra diferentes dispositivos e telas conectados. O conteúdo do AEM Screens é gerenciado em *canais*. O *AEM Screens Player* renderiza o conteúdo presente nos canais em exibições.



>[!NOTE]
>
>Para saber mais detalhes sobre os diferentes recursos no desenvolvimento e gerenciamento de um projeto do AEM Screens, consulte o **[Guia do usuário do AEM Screens](https://helpx.adobe.com/experience-manager/6-5/screens/user-guide.html)**.

## AEM Sites versus AEM Screens {#aem-sites-screens}

> [!NOTE]
>
> Se a equipe de implementação tiver experiência em trabalhar com as aplicações do AEM Sites, é importante entender a diferença entre o AEM Sites e o AEM Screens.

O AEM Screens fornece uma plataforma unificada de criação/reprodução para implantar conteúdo em dispositivos de sinalização digital em espaços públicos. Embora o autor da experiência deva se esforçar para manter a consistência na Web e nos canais no local, há algumas diferenças que devem ser observadas.

* **Tempo de permanência**: normalmente, as páginas da Web são criadas para fornecer uma grande variedade de informações que podem ser consumidas por um período de tempo relativamente mais longo. Por outro lado, as experiências digitais no local devem antecipar as necessidades do visualizador e fornecer orientações claras e concisas sobre como e por que o usuário deve se envolver. Isso resulta em experiências mais direcionadas, com curadoria e contextuais.

* **Distância de exibição**: as distâncias de exibição geralmente são maiores ou mais distantes do que a distância de exibição típica que os usuários experimentam em um site. Como resultado, o tamanho do texto normalmente deve ser maior e o espaçamento entre o texto, as imagens e outros conteúdos complementares deve ser testado com base no tamanho e no posicionamento previstos da tela no espaço físico.

* **Persistência**: o estado conectado do dispositivo de reprodução nunca deve influenciar se as experiências digitais são ou não entregues ao usuário. O dispositivo de reprodução deve ser criado de modo que uma ou mais experiências sempre persistam e possam ser entregues, independentemente do estado conectado do dispositivo de reprodução.

* **Segmentação do loop de mídia**: configurar cada dispositivo de reprodução para ter seu próprio segmento de loop garante que o conteúdo localizado possa ser facilmente criado, publicado e reproduzido dentro da experiência digital geral. Os ativos de mídia contidos nos canais de sequência incorporados são adicionados ao segmento de loop anterior e oferecem a oportunidade de direcionar um segmento de loop de mídia para cada agrupamento de local.

* **Experiências interativas**: um aplicativo de quiosque habilitado para toque pode ser criado e entregue em um canal do Screens, usando o AEM e o editor SPA. É uma prática recomendada aplicar propriedades consistentes de design de omnicanal, um temporizador de inatividade para redefinir a experiência e um call to action claro para quais tarefas o aplicativo pode executar. A página de aterrissagem deve consistir em elementos digitais principais, criados para transmitir valor, atrair o usuário para a tela e solicitar que o usuário se envolva.

O AEM Screens fornece uma estrutura para implantar conteúdo em dispositivos físicos. O conteúdo é atribuído a Canais no Screens, que podem conter conteúdo de mídia ou aplicativos de tela sensível ao toque. Dentro dessa estrutura, um aplicativo do AEM Sites pode ser entregue como conteúdo por meio de um canal.

Antes de ser solto em um Canal no Screens, um AEM Sites deve ser formatado para uso nas dimensões do dispositivo de exibição para o qual está destinado.

> [!NOTE]
>
> Muitos componentes do AEM Sites não são compatíveis com o AEM Screens. O AEM Screens é fornecido com muitos de seus próprios componentes prontos para uso, permitindo criar experiências digitais sem a necessidade de personalização. Se os requisitos do projeto permitirem, use a funcionalidade integrada do AEM Screens, quando possível.
