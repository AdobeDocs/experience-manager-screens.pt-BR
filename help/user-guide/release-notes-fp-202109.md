---
title: Notas de versão do Pacote de recursos 202109
description: Siga esta página para obter informações sobre o Pacote de recursos do AEM Screens 202109 lançado em 23 de setembro de 2021.
feature: Feature Pack
role: Developer
level: Intermediate
exl-id: e1794013-59ce-4ddc-93c0-601668c75cd1
source-git-commit: b56844c66bfa980013b610523842c7ac0c30f44d
workflow-type: tm+mt
source-wordcount: '931'
ht-degree: 2%

---

# Notas de versão do Pacote de recursos 202109 {#release-notes-for-feature-pack}

>[!CAUTION]
>É recomendável atualizar para a versão mais recente do Adobe Experience Manager (AEM). O Screens fornece suporte de manutenção para a plataforma AEM 6.3 Screens.

## Disponibilidade {#availability}

O AEM Screens lançou o AEM 6.5 Feature Pack 9.

Baixe o pacote de recursos mais recente do AEM Screens 6.5.9 na [Portal de distribuição de software](https://experience.adobe.com/#/downloads/content/software-distribution/br/aem.html) usando sua Adobe ID. Navegue até **Adobe Experience Manager** e pesquisar **Screens** para obter o pacote de recursos mais recente intitulado como **AEM 6.5 Screens FP9**.

## Data de lançamento {#release-date}

A data de lançamento do Pacote de recursos do AEM Screens 202109 é 23 de setembro de 2021.

### Novidades {#what-is-new}

* **Suporte a miniaturas para vídeos**

   O Suporte a miniaturas para vídeos agora é compatível com o AEM Screens. Um autor de conteúdo pode definir uma miniatura de vídeos para que a imagem possa ser usada como um espaço reservado e testar corretamente a reprodução e o direcionamento do conteúdo, enquanto o vídeo real está sendo finalizado pela equipe apropriada. A imagem também pode ser usada caso a reprodução do vídeo falhe.
Consulte [Suporte a miniaturas para vídeos](/help/user-guide/thumbnail-support.md) para obter mais detalhes.

* **Monitoramento básico de reprodução**

   O AEM Screens agora é compatível com o monitoramento básico de reprodução. O player agora relatará várias métricas de reprodução a cada ping (o padrão é 30 segundos). Com base nas métricas, ele fornece a capacidade de detectar vários casos de borda (experiência travada, tela em branco, problema de agendamento etc.). Esse recurso permite que a equipe monitore remotamente se um player está reproduzindo conteúdo corretamente, melhora a reatividade para telas em branco ou experiências com falha no campo e diminui o risco de mostrar uma experiência com falha para o usuário final.
Consulte [Monitoramento básico de reprodução](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/administering/installing-screens-player.html?lang=en#playback-monitoring) para obter mais detalhes.

* **Atualizações no Relatório de atribuição de conteúdo**

   O Relatório de atribuição de conteúdo agora está otimizado e aprimorado com experiência aprimorada do usuário. O relatório baixável exibe entidades relacionadas ao player aprimoradas, como locais, exibições e dispositivos em uma guia da planilha e as informações do provedor de conteúdo, como canais e ativos em outra guia.
Consulte [Relatório de atribuição de conteúdo](/help/user-guide/content-assignment-report.md) para obter mais detalhes.

* **Representações adaptáveis**

   As representações adaptáveis permitem que os dispositivos selecionem automaticamente a melhor representação para um dispositivo com base em regras definidas pelo cliente.

   Como um Desenvolvedor do AEM Screens, agora você pode configurar representações de ativos específicas do dispositivo para serem baixadas e reproduzidas automaticamente sem precisar criar todas as variações de conteúdo manualmente. Consulte [Representações adaptáveis: visão geral e configurações da arquitetura](/help/user-guide/adaptive-renditions.md) para obter mais detalhes.

   Além disso, como um Autor de conteúdo do AEM Screens, você pode configurar seus ativos para usar Representações adaptáveis e também migrar seus dispositivos para redes grandes para aproveitar esse recurso em seus canais do AEM Screens. Consulte [Uso de representações adaptáveis no AEM Screens](/help/user-guide/using-adaptive-renditions.md) para obter mais detalhes.

* **Suporte para manifestos V3**

   Agora você pode configurar o Dispatcher para a Versão de manifesto v3. Para ativar o Manifesto v3, é necessário:

   * Limpar todos os trabalhos de conteúdo offline pendentes no autor e na publicação

      * Navegue até crx/de no autor e na publicação

      * Clique em Ferramentas —> Consulta

      * No query use `/jcr:root/var/eventing/jobs/assgined//element(*,slingevent:Job)[\@event.job.topic='screens/offline_content_update']`

      * Isso listará todos os trabalhos de conteúdo offline que estão atualmente em execução ou pendentes na fila

      * Aguarde até que não haja mais trabalhos de conteúdo offline retornados da consulta
   * Desativar ContentSync em `/system/console/configMgr/configMgr/com.adobe.cq.screens.offlinecontent.impl.ContentSyncCacheFeatureFlag`

   * Ativar SmartSync no `/system/console/configMgr/com.adobe.cq.screens.offlinecontent.impl.OfflineContentServiceImpl`

   * Atualizar dispatcher

   * Atualizar componente personalizado


   * Consulte [Configuração do Dispatcher para Versão de Manifesto v3](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/administering/dispatcher-configurations-aem-screens.html?lang=en#configuring-dispatcherv3) para obter mais detalhes.
   * Se você estiver usando componentes personalizados como parte dos manifestos v3, consulte [Modelo para manipuladores personalizados](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/developing/developing-custom-component-tutorial-develop.html?lang=en#custom-handlers).



### Correções de erros {#bug-fixes}

**Lado do player**

* Correção de erros de cache de arquivos substituindo ativos por representações.

* Os players agora só expõem representações de ativos, se o mapeamento de representação estiver presente.

* Ping aprimorado para autenticar novamente se a resposta não for um JSON válido.

* Nomes/funções de canal numérico causaram tela em branco.

* Baixar representações otimizadas via SmartSync.

* Transformou o mapeamento em uma lista de chaves de representação.

* Remoção do acesso ao `cmd.exe` e `reg.exe` no windows player.

* Um reprodutor precisa relatar seu último evento de reprodução bem-sucedido.

* Um reprodutor precisa relatar seu status de reprodução.

* O reprodutor não baixa ativos novamente quando `ALL` O cache é limpo.

* Como Administrador do player, agora você pode escolher um nome de player.

* A remoção da atribuição de canal da exibição não é refletida no reprodutor.

* Se o player for recarregado enquanto a atualização do canal estiver sendo baixada, o player ignorará a atualização.

* O componente de Página incorporado agora respeita o evento de toque.

* O provisionamento remoto do reprodutor Tizen agora é compatível.

**Lado do servidor**

* O vídeo do Target não é exibido
* Condição de corrida na transmissão de dados de exibição para subsequentes.

* A Visualização de canal não funciona para Canais que contêm Vídeos.

* Modo de visualização mostrando em branco para canal de tela dividida.

* As miniaturas de vídeo são renderizadas em branco com representações adaptáveis ativadas.

* Atualizar automaticamente o manifesto do canal se a página referenciada for publicada.

* Os dispositivos excluídos agora não bloqueiam a fila de replicação do Screens.

* O manifesto não continha conteúdo direcionado nem páginas inseridas do Sites. Isso já foi corrigido.

* O novo componente de imagem principal agora é adicionado ao manifesto do canal.

* O download de representações otimizadas via SmartSync agora é suportado.

* Reproduzir representação otimizada para todos os ativos.

* Adição de suporte para vários tipos de provedor de conteúdo

* A Estratégia de reprodução de sequência inserida foi interrompida e isso foi corrigido.

* Manifesto offline usando o parâmetro de solicitação `wcmmode` para entrada html, tornando-a não armazenável em cache.

* Sequência incorporada dinâmica vazia às vezes causava tela em branco.

* O player agora relata seu status de reprodução.

* O vídeo estava sendo reproduzido em `Tiny mode` e não será reproduzido como vídeo em tela cheia no dispositivo, e o problema será corrigido agora.

### Players do AEM Screens lançados {#released-aem-screens-players}

Os seguintes players de AEM Screens são lançados para AEM 6.5 Feature Pack 9:

* ChromeOS
* Windows
* Tizen
* Android
* Linux

#### Downloads do AEM Screens Player  {#aem-screens-player-downloads}

Para baixar o reprodutor AEM Screens mais recente e saber mais sobre as correções de erros, consulte **[Downloads do AEM Screens Player](https://download.macromedia.com/screens/index.html)**.
