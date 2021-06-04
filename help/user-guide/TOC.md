---
cloud: experience-cloud
product: experience manager
audience: end-user
user-guide-title: Ajuda do Adobe Experience Manager Screens
breadcrumb-title: Guia do AEM Screens
user-guide-description: Saiba como usar uma Solução de sinalização digital que permite a publicação de experiências e interações digitais dinâmicas e interativas.
feature-set: Experience Manager Screens
source-git-commit: 21bb9194d470bc4842a00e20ab3e3d7f517effed
workflow-type: tm+mt
source-wordcount: '445'
ht-degree: 19%

---


# Guia do usuário do AEM Screens {#user-guide}

+ [Introdução ao Screens](aem-screens-introduction.md)
+ Visão geral e Guia do Kickstart {#overview}
   + [Guia do Kickstart](kickstart-for-aem-screens.md)
   + [Guia de práticas recomendadas do Screens](https://docs.adobe.com/content/help/pt-BR/experience-manager-screens/using/about-guide.html)
   + [Termos principais](screens-glossary.md)
+ Noções básicas da rede de sinalização digital {#digital-signage-network}
   + [Parte 1: Funções e responsabilidades do projeto](project-roles-responsibilities.md)
   + [Parte 2: Considerações quanto ao escopo dos projetos](project-considerations.md)
   + [Parte 3: Teste, POCs, pilotos e rotações](testing-pocs-pilots-rollouts.md)
   + [Parte 4: Gerenciamento e implantação do projeto](project-management-and-deployment.md)
   + [Parte 5: Considerações de suporte](support-considerations.md)
+ Configuração e administração {#administering}
   + [Configurações do servidor do Screens](configuring-screens-introduction.md)
   + [Configuração das configurações do Dispatcher](dispatcher-configurations-aem-screens.md)
   + [Instalar o reprodutor do Screens](installing-screens-player.md)
   + [Player do Connecting Screens](working-with-screens-player.md)
   + [Registro do dispositivo](device-registration.md)
   + [Configuração de ACLs](setting-up-acls.md)
   + [Lista de verificação de segurança do AEM Screens](security-checklist.md)
   + [Transição de ContentSync para SmartSync](smartsync.md)
   + [Novo importador de projetos do arquivo](project-importer.md)
   + [Replicação de dados de acionadores para servidores de publicação](replicating-data-triggers.md)
   + Considerações específicas do cliente {#installing-client}
      + [Player do Chrome OS](implementing-chrome-os-player.md)
      + [Uso do Chrome Player como extensão para solução de problemas](using-chrome-player-as-an-extension.md)
      + [Player do Android](implementing-android-player.md)
      + [Windows Player](implementing-windows-player.md)
      + [Tizen Player](tizen-player.md)
      + [Registro automático de jogadores](auto-registration-players.md)
   + Publicar autor {#author-publish}
      + [Visão geral da arquitetura de publicação de autores](author-publish-architecture-overview.md)
      + [Configuração de autor e publicação](author-and-publish.md)
   + Integração do Analytics com o AEM Screens {#analytics-integration}
      + [Integração do Adobe Analytics](adobe-analytics-integration-aem-screens.md)
      + [Configuração do Adobe Analytics com AEM Screens](configuring-adobe-analytics-aem-screens.md)
+ Exemplos de casos de criação e uso {#authoring}
   + Configurar um projeto do Screens {#setting-up-projects}
      + [Criação e gerenciamento de projetos](creating-a-screens-project.md)
      + [Criação e gerenciamento de canais](managing-channels.md)
      + [Criação e gerenciamento de exibições](managing-displays.md)
      + [Criação e gerenciamento de localizações](managing-locations.md)
      + [Criação e gerenciamento de agendamentos](managing-schedules.md)
      + [Gerenciamento de dispositivos](managing-devices.md)
      + Atribuição de canais {#assigning-channels}
         + [Atribuição de canal](channel-assignment-latest-fp.md)
         + [Atribuição de canal: Pacotes de recursos mais antigos do AEM Screens](channel-assignment.md)
   + Uso dos principais recursos do produto {#product-features}
      + [Sobreposição de texto](text-overlay.md)
      + [Atualização Offline em massa](bulk-offline-update.md)
      + [Serviço de notificações da AEM Screens](screens-notifications-service.md)
      + [Uso de Fragmentos de experiência](experience-fragments-in-screens.md)
      + [Ativação no nível do ativo](asset-level-scheduling.md)
      + [Ativação no nível do canal](channel-level-activation.md)
      + [Criação e gerenciamento de uma Live Copy](managing-livecopy.md)
      + [Criação de um fluxo de trabalho de preenchimento de vídeo](creating-a-video-padding-workflow.md)
      + [Adição de componentes a um canal](adding-components-to-a-channel.md)
      + [Sequências incorporadas](embedded-sequences.md)
      + [Layout de várias zonas](multi-zone-layout-aem-screens.md)
      + [Representações de vídeo](generating-renditions.md)
      + [Sequência incorporada dinâmica](dynamic-embedded-sequences.md)
      + [Duração da reprodução de imagem em massa no nível do canal](channel-level-image-playback.md)
      + [Sincronização de comandos](using-command-sync.md)
      + [Criação com acionadores de dados](authoring-data-triggers.md)
      + [Reconhecimento de voz](voice-recognition.md)
      + [Relatório de atribuição de conteúdo](content-assignment-report.md)
   + Gerenciamento de atualizações de conteúdo {#content-updates}
      + [Atualização de conteúdo sob demanda](on-demand-content.md)
      + [Atualização de conteúdo como serviço](content-update-as-a-service.md)
      + [Atualização de conteúdo usando o Screens Launch](launches.md)
   + Exemplos de casos de uso {#use-case-examples}
      + [Canais de emergência](emergency-channel.md)
      + [Ativação da temperatura do centro de viagens](local-temperature-activation.md)
      + [Ativação de Reserva de Hospitalidade](hospitality-reservation-activation.md)
      + [Ativação direcionada para inventário de varejo](retail-inventory-activation.md)
      + [Aplicar transições](applying-transitions.md)
      + [Transições de várias zonas para uma única zona](multizone-to-singlezone.md)
      + [Canal de Tomada a cargo de Uso Único](single-use-takeover-channel.md)
      + [Canal de aquisição de uso pessoal](perpetual-takeover-channel.md)
+ Recursos do desenvolvedor e da API {#developing}
   + [REST APIs](rest-api.md)
   + [Desenvolvimento de um componente personalizado para o AEM Screens](developing-custom-component-tutorial-develop.md)
   + [Canais offline](offline-channels.md)
   + [Extensão de um componente do AEM Screens](extending-component-tutorial-develop.md)
   + [Criar componentes](creating-components.md)
   + [Como incorporar um aplicativo REACT usando AEM Editor e Integração com o AEM Screens Analytics](embedding-react-app.md)
   + [Configuração do ContextHub no AEM Screens](configuring-context-hub.md)
   + [Criação de modelos personalizados para layouts de várias zonas](creating-custom-templates-multizone-layouts.md)
   + [Aplicação de marca personalizada e estilo para sobreposições de texto](custom-branding-text-overlays.md)
+ Solução de problemas e perguntas frequentes {#troubleshooting}
   + [Perguntas frequentes do AEM Screens](aem-screens-faqs.md)
   + [Solução de problemas do Device Control Center](monitoring-screens.md)
   + [Configuração da reprodução de vídeo](troubleshoot-videos.md)
+ Notas de versão {#release-notes}
   + [Notas de versão do Feature Pack 202105](release-notes-fp-202105.md)
   + [Notas de versão do Feature Pack 202103](release-notes-fp-202103.md)
   + [Notas de versão do Feature Pack 202011](release-notes-fp-202011.md)
   + [Notas de versão do Feature Pack 202008](release-notes-fp-202008.md)
   + [Notas de versão do Feature Pack 202004](release-notes-fp-202004.md)
   + [Notas de versão do Feature Pack 202001](release-notes-fp-202001.md)
   + [Notas de versão do Feature Pack 201909](release-notes-fp-201909.md)
   + [Notas de versão do Feature Pack 201907](release-notes-fp-201907.md)
   + [Notas de versão do Feature Pack 201905](screens-release-notes-fp-201905.md)
   + [Notas de versão do Feature Pack 201812](release-notes-fp-201812.md)
   + [Notas de versão do Feature Pack 201809](screens-release-notes.md)
