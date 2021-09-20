---
title: Notas de versão do Feature Pack 202109
description: Siga esta página para obter informações sobre o AEM Screens Feature Pack 202105 lançado em 23 de setembro de 2021.
feature: Feature Pack
role: Developer
level: Intermediate
index: false
source-git-commit: 060ab6a906597ab8e8789fab6932cec310cc06f5
workflow-type: tm+mt
source-wordcount: '720'
ht-degree: 1%

---

# Notas de versão do Feature Pack 202109 {#release-notes-for-feature-pack}

>[!CAUTION]
>É recomendável atualizar para a versão mais recente do Adobe Experience Manager (AEM). O Screens fornece suporte de manutenção para AEM plataforma do Screens 6.3.

## Disponibilidade {#availability}

A AEM Screens lançou AEM 6.5 Feature Pack 9.

Você pode baixar o pacote de recursos mais recente da versão 6.5.9 do AEM Screens a partir do [Portal de distribuição de software](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html) usando sua Adobe ID. Navegue até a guia **Adobe Experience Manager** e procure por **Screens** para obter o pacote de recursos mais recente intitulado como **AEM 6.5 Screens FP9**.

## Data de lançamento {#release-date}

A data de lançamento do AEM Screens Feature Pack 202109 é 23 de setembro de 2021.

### Novidades {#what-is-new}

* **Suporte a miniaturas para vídeos**

   O suporte a miniaturas de vídeos no agora é compatível com o AEM Screens. Um autor de conteúdo pode definir uma miniatura de vídeos para que a imagem possa ser usada como um espaço reservado e testar corretamente a reprodução e o direcionamento do conteúdo, enquanto o vídeo real está sendo finalizado pela equipe apropriada. A imagem também pode ser usada caso a reprodução do vídeo falhe.
Consulte Suporte de miniaturas para vídeos para obter mais detalhes.

* **Monitoramento básico da reprodução**

   O AEM Screens agora é compatível com o monitoramento básico de reprodução. O reprodutor reportará várias métricas de reprodução a cada ping (o padrão é 30 segundos). Com base nas métricas, ele fornece a capacidade de detectar vários casos de borda (experiência travada, tela em branco, problema de agendamento, etc.). Esse recurso permite que a equipe monitore remotamente se um player estiver reproduzindo conteúdo corretamente, melhora a reatividade em telas em branco ou falha de experiências no campo e diminui o risco de mostrar uma experiência quebrada para o usuário final.
Consulte Monitoramento básico da reprodução para obter mais detalhes.

* **Atualizações do Relatório de atribuição de conteúdo**

* **Suporte para manifesto V3**

   Agora você pode configurar o Dispatcher para a Versão de manifesto v3. Consulte [Configuração do Dispatcher para Versão do Manifesto v3](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/administering/dispatcher-configurations-aem-screens.html?lang=en#configuring-dispatcherv3) para obter mais detalhes.
Além disso, se você estiver usando componentes personalizados como parte de manifestos v3, consulte [Modelo para manipuladores personalizados](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/developing/developing-custom-component-tutorial-develop.html?lang=en#custom-handlers).


### Correções de erros {#bug-fixes}

**Lado do reprodutor**

* Correção de erros de armazenamento em cache de arquivos ao substituir ativos por representações.

* Os players agora só expõem representações de ativos, se o mapeamento de representação estiver presente.

* Agora você pode configurar alertas de atraso com base em logs de partes.

* Aprimore o ping para autenticar novamente se a resposta não for um JSON válido.

* Nomes/funções de canal numéricos causavam tela em branco.

* Baixe representações otimizadas via SmartSync.

* Transforme o mapeamento em uma lista de chaves de representação.

* Remova o acesso a cmd.exe e reg.exe no windows player.

* Limitar chamadas de token csrf.

* Um reprodutor precisa relatar seu último evento de reprodução bem-sucedido.

* Um reprodutor precisa relatar seu status de reprodução.

* O reprodutor não faz o download de Ativos novamente quando o cache `ALL` é limpo.

* Como Administrador do player, agora você pode escolher um nome para o player.

* A remoção da atribuição de canal da exibição não é refletida no reprodutor.

* Se o player for recarregado durante o download da atualização do canal, ele ignorará a atualização.

* O Componente de página incorporada não respeita o evento de toque.

* O provisionamento remoto do Tizen player agora é compatível.

**Lado do servidor**

* O vídeo do Target não está sendo exibido
* Condição de corrida na transmissão de dados de exibição para subsequências.

* A Visualização de canal não funciona para canais que contêm vídeos.

* Modo de visualização que mostra em branco para o canal de tela dividida.

* As miniaturas de vídeo renderizam em branco com representações adaptáveis ativadas.

* Atualize automaticamente o manifesto do canal se a página referenciada estiver publicada.

* Canais JSON não inclui canais personalizados (#942)

* Dispositivos excluídos agora não bloqueiam a fila de replicação do Screens.

* O manifesto não contém conteúdo direcionado nem páginas incorporadas de Sites.

* Novo componente de imagem principal não adicionado ao manifesto do canal.

* O download de representações otimizadas via SmartSync agora é suportado.

* Reproduzir representação otimizada para todos os ativos.

* Adição de suporte para vários tipos de provedores de conteúdo

* A Estratégia de reprodução de sequência incorporada foi interrompida e isso foi corrigido.

* Manifesto offline usando o parâmetro de solicitação `wcmmode` para entrada html, tornando-o inarmazenável em cache.

* Uma sequência incorporada dinâmica vazia às vezes causa tela em branco.

* Um reprodutor precisa relatar seu status de reprodução.

* O vídeo está sendo reproduzido no `Tiny mode` e não é reproduzido como vídeo de tela cheia no dispositivo.

* As senhas OSGi são visíveis como texto simples.


### Players AEM Screens lançados {#released-aem-screens-players}

Os seguintes players do AEM Screens são lançados para o AEM 6.5 Feature Pack 9:

* ChromeOS
* Windows
* Tizen
* Android
* Linux

#### Downloads do AEM Screens Player  {#aem-screens-player-downloads}

Para baixar o reprodutor AEM Screens mais recente e saber mais sobre as correções de erros, consulte **[Downloads do AEM Screens Player](https://download.macromedia.com/screens/index.html)**.
