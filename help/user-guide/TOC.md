---
cloud: Experience Cloud
product: experience manager
audience: end-user
user-guide-title: Ajuda do Adobe Experience Manager Screens
breadcrumb-title: Guia do AEM Screens
user-guide-description: Saiba como usar uma Solução de sinalização digital que permite publicar experiências e interações digitais dinâmicas e interativas.
feature-set: Experience Manager Screens
feature: Content
role: User
source-git-commit: 1e8beb9dfaf579250138d4a41eeec88cc81f2d39
workflow-type: tm+mt
source-wordcount: '518'
ht-degree: 7%

---


# Guia do usuário do AEM Screens {#user-guide}

+ [Introdução ao Screens](aem-screens-introduction.md)
+ Visão geral e Guia de início rápido {#overview}
   + [Guia de início rápido](kickstart-for-aem-screens.md)
   + [Guia de práticas recomendadas do Screens](https://experienceleague.adobe.com/en/docs/experience-manager-screens/using/about-guide)
   + [Termos principais](screens-glossary.md)
+ Noções básicas de rede de sinalização digital {#digital-signage-network}
   + [Parte 1: Funções e Responsabilidades do Projeto](project-roles-responsibilities.md)
   + [Parte 2: Considerações quanto ao escopo dos projetos](project-considerations.md)
   + [Parte 3: Testes, POCs, pilotos e implantações](testing-pocs-pilots-rollouts.md)
   + [Parte 4: Gerenciamento e implantação de projetos](project-management-and-deployment.md)
   + [Parte 5: Considerações sobre suporte](support-considerations.md)
+ Configuração e administração {#administering}
   + [Configurações do servidor do Screens](configuring-screens-introduction.md)
   + [Definição das configurações do Dispatcher](dispatcher-configurations-aem-screens.md)
   + [Instalar o reprodutor do Screens](installing-screens-player.md)
   + [Conectar o reprodutor do Screens](working-with-screens-player.md)
   + [Registro do dispositivo](device-registration.md)
   + [Configurando ACLs](setting-up-acls.md)
   + [Lista de verificação de segurança do AEM Screens](security-checklist.md)
   + [Transição do ContentSync para o SmartSync](smartsync.md)
   + [Novo importador de projeto do arquivo](project-importer.md)
   + [Replicação dos acionadores de dados para os servidores de publicação](replicating-data-triggers.md)
   + [Configuração dos agentes de replicação do Screens](configure-screens-replication.md)
   + Considerações específicas do cliente {#installing-client}
      + [Chrome OS Player](implementing-chrome-os-player.md)
      + [Utilização do Chrome Player como uma extensão para solução de problemas](using-chrome-player-as-an-extension.md)
      + [Android](implementing-android-player.md)
      + [Windows Player](implementing-windows-player.md)
      + [Tizen Player](tizen-player.md)
      + [Cloud Player](implementing-cloud-player.md)
      + [Registro automático de players](auto-registration-players.md)
      + [Usar o controle remoto](implementing-remote-control.md)
   + Publicação do autor {#author-publish}
      + [Autor - Publicar visão geral da arquitetura](author-publish-architecture-overview.md)
      + [Configuração do Author e Publish](author-and-publish.md)
   + Integração do Analytics com o AEM Screens {#analytics-integration}
      + [Integração do Adobe Analytics](adobe-analytics-integration-aem-screens.md)
      + [Configuração do Adobe Analytics com AEM Screens](configuring-adobe-analytics-aem-screens.md)
+ Criação e exemplos de caso de uso {#authoring}
   + Configuração de um projeto do Screens {#setting-up-projects}
      + [Criação e gerenciamento de projetos](creating-a-screens-project.md)
      + [Criação e gerenciamento de canais](managing-channels.md)
      + [Criando e Gerenciando Exibições](managing-displays.md)
      + [Criação e Gerenciamento de Locais](managing-locations.md)
      + [Criação e Gerenciamento de Agendamentos](managing-schedules.md)
      + [Gerenciando dispositivos](managing-devices.md)
      + Atribuição de canais {#assigning-channels}
         + [Atribuição de canal](channel-assignment-latest-fp.md)
         + [Atribuição de canal: pacotes de recursos AEM Screens mais antigos](channel-assignment.md)
   + Uso dos recursos principais do produto {#product-features}
      + [Sobreposição de texto](text-overlay.md)
      + [Atualização offline em massa](bulk-offline-update.md)
      + [Serviço de notificações do AEM Screens](screens-notifications-service.md)
      + [Uso de Fragmentos de experiência](experience-fragments-in-screens.md)
      + [Ativação em nível de ativo](asset-level-scheduling.md)
      + [Ativação em Nível de Canal](channel-level-activation.md)
      + [Criação e gerenciamento de uma Live Copy](managing-livecopy.md)
      + [Criação de um fluxo de trabalho de preenchimento de vídeo](creating-a-video-padding-workflow.md)
      + [Adicionar componentes a um canal](adding-components-to-a-channel.md)
      + [Sequências incorporadas](embedded-sequences.md)
      + [Layout de várias zonas](multi-zone-layout-aem-screens.md)
      + [Representações de vídeo](generating-renditions.md)
      + [Sequência incorporada dinâmica](dynamic-embedded-sequences.md)
      + [Duração da reprodução de imagem em massa no nível do canal](channel-level-image-playback.md)
      + [Sincronização de comando](using-command-sync.md)
      + [Criação com acionadores de dados](authoring-data-triggers.md)
      + [Reconhecimento de voz](voice-recognition.md)
      + [Relatório de atribuição de conteúdo](content-assignment-report.md)
      + [Suporte a miniaturas para vídeos](thumbnail-support.md)
      + [Uso de representações adaptáveis no AEM Screens](using-adaptive-renditions.md)
   + Gerenciamento de atualizações de conteúdo {#content-updates}
      + [Atualização de conteúdo sob demanda](on-demand-content.md)
      + [Atualização de conteúdo como serviço](content-update-as-a-service.md)
      + [Atualização de conteúdo usando o Screens Launch](launches.md)
   + Exemplos de caso de uso {#use-case-examples}
      + [Canais de emergência](emergency-channel.md)
      + [Ativação da temperatura do centro de viagens](local-temperature-activation.md)
      + [Ativação de Reserva de Hospitalidade](hospitality-reservation-activation.md)
      + [Ativação Direcionada de Estoque de Varejo](retail-inventory-activation.md)
      + [Aplicar transições](applying-transitions.md)
      + [Transições de várias zonas para uma única zona](multizone-to-singlezone.md)
      + [Canal de tomada a cargo de uso único](single-use-takeover-channel.md)
      + [Canal de Assunção de Uso Perpétuo](perpetual-takeover-channel.md)
+ Recursos do desenvolvedor e da API {#developing}
   + [APIs REST](rest-api.md)
   + [Desenvolvimento de um componente personalizado para o AEM Screens](developing-custom-component-tutorial-develop.md)
   + [Canais offline](offline-channels.md)
   + [Extensão de um componente do AEM Screens](extending-component-tutorial-develop.md)
   + [Criar componentes](creating-components.md)
   + [Incorporação de um aplicativo REACT usando o editor SPA AEM e integração com o AEM Screens Analytics](embedding-react-app.md)
   + [Configuração do ContextHub no AEM Screens](configuring-context-hub.md)
   + [Criação de modelos personalizados para layouts de várias zonas](creating-custom-templates-multizone-layouts.md)
   + [Aplicação de marca e estilo personalizados a sobreposições de texto](custom-branding-text-overlays.md)
   + [Representações adaptáveis: visão geral e configurações da arquitetura](/help/user-guide/adaptive-renditions.md)
+ Solução de problemas e perguntas frequentes {#troubleshooting}
   + [Perguntas frequentes sobre o AEM Screens](aem-screens-faqs.md)
   + [Solução de problemas do Centro de controle de dispositivos](monitoring-screens.md)
   + [Configuração de reprodução de vídeo](troubleshoot-videos.md)
+ Notas de versão {#release-notes}
   + [Notas de versão do Pacote de recursos 202401](release-notes-fp-202401.md)
   + [Notas de versão do Pacote de recursos 20240116](release-notes-fp-20240116.md)
   + [Notas de versão do Pacote de recursos 20240215](release-notes-fp-20240215.md)
   + [Notas de versão do Pacote de recursos 202204](release-notes-fp-202204.md)
   + [Notas de versão do Pacote de recursos 202203](release-notes-fp-202203.md)
   + [Notas de versão do Pacote de recursos 202112](release-notes-fp-202112.md)
   + [Notas de versão do Pacote de recursos 202109](release-notes-fp-202109.md)
   + [Notas de versão do Pacote de recursos 202105](release-notes-fp-202105.md)
   + [Notas de versão do Pacote de recursos 202103](release-notes-fp-202103.md)
   + [Notas de versão do Pacote de recursos 202011](release-notes-fp-202011.md)
   + [Notas de versão do Pacote de recursos 202008](release-notes-fp-202008.md)
   + [Notas de versão do Pacote de recursos 202004](release-notes-fp-202004.md)
   + [Notas de versão do Pacote de recursos 202001](release-notes-fp-202001.md)
   + [Notas de versão do Pacote de recursos 201909](release-notes-fp-201909.md)
   + [Notas de versão do Pacote de recursos 201907](release-notes-fp-201907.md)
   + [Notas de versão do Pacote de recursos 201905](screens-release-notes-fp-201905.md)
   + [Notas de versão do Pacote de recursos 201812](release-notes-fp-201812.md)
   + [Notas de versão do Pacote de recursos 201809](screens-release-notes.md)
