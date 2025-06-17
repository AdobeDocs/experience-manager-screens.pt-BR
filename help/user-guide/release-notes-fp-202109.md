---
title: Notas de versão do Pacote de recursos 202109
description: Saiba mais sobre o Pacote de recursos do AEM Screens 202109, lançado em 23 de setembro de 2021.
feature: Feature Pack
role: Developer
level: Intermediate
exl-id: e1794013-59ce-4ddc-93c0-601668c75cd1
source-git-commit: dcaaa1c7ab0a55cecce70f593ed4fded8468130b
workflow-type: tm+mt
source-wordcount: '916'
ht-degree: 1%

---

# Notas de versão do Pacote de recursos 202109 {#release-notes-for-feature-pack}

>[!CAUTION]
>A Adobe recomenda atualizar para a versão mais recente do Adobe Experience Manager (AEM). A AEM Screens fornece suporte de manutenção para a plataforma Screens do AEM 6.3.

## Disponibilidade {#availability}

A AEM Screens lançou o Pacote de recursos 9 do AEM 6.5.

Você pode baixar a Versão mais recente do Feature Pack para o AEM Screens 6.5.9 no [Portal de Distribuição de Software](https://experience.adobe.com/#/downloads/content/software-distribution/br/aem.html) usando sua Adobe ID. Navegue até a guia **Adobe Experience Manager** e procure por **Screens** para obter o Pacote de Recursos mais recente denominado **AEM 6.5 Screens FP9**.

## Data de lançamento {#release-date}

A data de lançamento do Pacote de recursos do AEM Screens 202109 é 23 de setembro de 2021.

### Novidades {#what-is-new}

* **Suporte a miniaturas para vídeos**

  O Suporte a miniaturas para vídeos agora é compatível com o AEM Screens. Um Autor de conteúdo define uma miniatura de vídeos para que a imagem seja usada como um espaço reservado. Eles também testam adequadamente a reprodução e o direcionamento do conteúdo, enquanto a equipe apropriada finaliza o vídeo real. A imagem também pode ser usada caso a reprodução do vídeo falhe.
Consulte [Suporte a miniaturas para vídeos](/help/user-guide/thumbnail-support.md) para obter mais detalhes.

* **Monitoramento básico de reprodução**

  O AEM Screens agora é compatível com o monitoramento básico de reprodução. O player agora relata várias métricas de reprodução a cada ping (o padrão é 30 segundos). Com base nas métricas, ele detecta vários casos de borda (experiência travada, tela em branco, problema de agendamento e assim por diante). Esse recurso permite que a equipe monitore remotamente se um player está reproduzindo conteúdo corretamente e melhora a reatividade para telas em branco ou experiências com falha no campo. Ele também diminui o risco de mostrar uma experiência quebrada ao usuário final.
Consulte [Monitoramento básico de reprodução](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/administering/installing-screens-player#playback-monitoring) para obter mais detalhes.

* **Atualizações ao Relatório de atribuição de conteúdo**

  O Relatório de atribuição de conteúdo agora está otimizado e aprimorado com uma experiência aprimorada do usuário. O relatório baixável exibe entidades melhoradas relacionadas ao player. Essas entidades incluem locais, exibições e dispositivos em uma guia da planilha. Também inclui as informações do provedor de conteúdo, como canais e ativos em outra guia.
Consulte [Relatório de atribuição de conteúdo](/help/user-guide/content-assignment-report.md) para obter mais detalhes.

* **Representações adaptáveis**

  As representações adaptáveis permitem que o dispositivo clique na melhor representação automaticamente para um dispositivo com base em regras definidas pelo cliente.

  Como um Desenvolvedor do AEM Screens, agora você pode configurar representações de ativos específicas do dispositivo para serem baixadas e reproduzidas automaticamente sem precisar criar todas as variações de conteúdo manualmente. Consulte [Representações adaptáveis: visão geral da arquitetura e configurações](/help/user-guide/adaptive-renditions.md) para obter mais detalhes.

  Além disso, como um Autor de conteúdo do AEM Screens, você pode configurar seus ativos para usar Representações adaptáveis. Você também pode migrar seus dispositivos para redes grandes para usar esse recurso em seus canais da AEM Screens. Consulte [Uso de representações adaptáveis no AEM Screens](/help/user-guide/using-adaptive-renditions.md) para obter mais detalhes.

* **Suporte para Manifestos V3**

  Agora você pode configurar o Dispatcher para a Versão de manifesto v3. Para ativar o Manifesto v3, faça o seguinte:

   * Limpe todos os trabalhos de conteúdo offline pendentes no autor e na publicação.

      * Navegue até o CRXDE Lite em Autor e Publicação.

      * Clique em Ferramentas > Consulta.

      * Na consulta, use `/jcr:root/var/eventing/jobs/assgined//element(*,slingevent:Job)[\@event.job.topic='screens/offline_content_update']`.

      * Isso lista todos os trabalhos de conteúdo offline que estão atualmente em execução ou pendentes na fila.

      * Aguarde até que não haja mais trabalhos de conteúdo offline retornados da consulta.

   * Desabilitar ContentSync em `/system/console/configMgr/configMgr/com.adobe.cq.screens.offlinecontent.impl.ContentSyncCacheFeatureFlag`.

   * Habilitar SmartSync em `/system/console/configMgr/com.adobe.cq.screens.offlinecontent.impl.OfflineContentServiceImpl`.

   * Atualize o Dispatcher.

   * Atualize o componente personalizado.


   * Consulte [Configuração do Dispatcher para a Versão de Manifesto v3](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/administering/dispatcher-configurations-aem-screens#configuring-dispatcherv3) para obter mais detalhes.
   * Se você estiver usando componentes personalizados como parte dos manifestos v3, consulte [Modelo para Manipuladores Personalizados](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/developing/developing-custom-component-tutorial-develop#custom-handlers).


### Correções de erros {#bug-fixes}

**Lado do player**

* Correção de erros de cache de arquivos substituindo ativos por representações.

* Os players agora só expõem representações de ativos, se o mapeamento de representação estiver presente.

* Ping aprimorado para autenticar novamente se a resposta não for um JSON válido.

* Nomes/funções de canal numérico causaram tela em branco.

* Baixe representações otimizadas por meio do SmartSync.

* Transformou o mapeamento em uma lista de chaves de representação.

* Remoção do acesso a `cmd.exe` e `reg.exe` no Windows Player.

* Um reprodutor deve relatar seu último evento de reprodução bem-sucedido.

* Um reprodutor deve relatar seu status de reprodução.

* O Player não baixará novamente o Assets quando o Cache `ALL` for limpo.

* Como Administrador do player, agora você pode escolher um nome de player.

* A remoção da atribuição de canal da exibição não é refletida no reprodutor.

* Se o reprodutor for recarregado enquanto a atualização do canal estiver sendo baixada, o reprodutor ignorará a atualização.

* O componente de Página incorporado agora respeita o evento de toque.

* O provisionamento remoto do reprodutor Tizen agora é compatível.

**Lado do servidor**

* O vídeo do Target não é exibido
* Condições de corrida na transmissão de dados de exibição para subsequentes.

* A Visualização de canal não funciona para Canais que contêm Vídeos.

* Modo de visualização mostrando em branco para canal de tela dividida.

* As miniaturas de vídeo são renderizadas em branco com as representações adaptáveis ativadas.

* Atualizar automaticamente o manifesto do canal se a página referenciada for publicada.

* Os dispositivos excluídos agora não bloqueiam a fila de replicação do Screens.

* O manifesto não continha conteúdo direcionado ou páginas inseridas do Sites. Esse erro foi corrigido.

* Um novo componente de imagem principal agora é adicionado ao manifesto do canal.

* O download de representações otimizadas por meio do SmartSync agora é compatível.

* Reproduzir representação otimizada para todos os ativos.

* Adição de suporte para vários tipos de provedor de conteúdo

* A Estratégia de reprodução de sequência integrada foi interrompida e esse erro foi corrigido.

* Manifesto offline usando o parâmetro de solicitação `wcmmode` para entrada html, tornando-o não armazenável em cache.

* Sequência incorporada dinâmica vazia às vezes causava tela em branco.

* O reprodutor agora relata seu status de reprodução.

* O vídeo estava sendo reproduzido em `Tiny mode` e não foi reproduzido como vídeo em tela inteira no dispositivo, e o problema foi corrigido agora.

### Players do AEM Screens lançados

Os seguintes players de AEM Screens foram lançados para o Feature Pack 9 do AEM 6.5:

* ChromeOS
* Windows
* Tizen
* Android™
* Linux®

#### Downloads do AEM Screens Player

Para baixar o AEM Screens Player mais recente e saber mais sobre as correções de erros, consulte **[Downloads do AEM Screens Player](https://download.macromedia.com/screens/index.html)**.
