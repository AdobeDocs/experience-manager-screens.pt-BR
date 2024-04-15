---
title: Configuração de instâncias de Autor e Publicação no AEM Screens
description: Saiba como configurar uma instância do Autor e uma instância de Publicação para o AEM Screens.
exl-id: 5aef5f35-d946-4bf8-a2a8-c3ed532b7eef
source-git-commit: 3b44fd920dd6c98ecc0e2b45bf95b81685647c0f
workflow-type: tm+mt
source-wordcount: '1923'
ht-degree: 0%

---


# Configuração de instâncias de Autor e Publicação no AEM Screens {#configuring-author-and-publish-in-aem-screens}

Esta página destaca os seguintes tópicos:

* **Configuração de instâncias de Autor e Publicação**
* **Configuração da topologia de publicação**
* **Gerenciar publicação: entregar atualizações de conteúdo de autor para publicação para dispositivo**

## Pré-requisitos {#prerequisites}

Antes de começar a usar servidores de Autor e Publicação, você deve ter conhecimento prévio sobre:

* **Topologia do AEM**
* **Criação e gerenciamento de projetos do AEM Screens**
* **Processo de registro do dispositivo**

>[!NOTE]
>
>Essa funcionalidade do AEM Screens só estará disponível se você tiver instalado o AEM 6.4 Screens Feature Pack 2. Para obter acesso a este Feature Pack, entre em contato com o Suporte da Adobe e solicite acesso. Depois de obter permissão, você pode baixá-lo do Compartilhamento de pacotes.

>[!IMPORTANT]
>
>Se quiser usar mais de uma instância de publicação com o Dispatcher, atualize o Dispatcher. Consulte [Ativar sessões adesivas](dispatcher-configurations-aem-screens.md#enable-sticky-session).

## Configuração de instâncias de Autor e Publicação {#configuring-author-and-publish-instances}

>[!NOTE]
>
>Para saber mais sobre a visão geral da arquitetura Autor e publicação e como o conteúdo é criado em uma instância de autor do AEM e, em seguida, reproduzido de forma encaminhada para várias instâncias de Publicação, consulte [Visão geral da arquitetura de criação e publicação](author-publish-architecture-overview.md).

A seção a seguir explica como configurar agentes de replicação na topologia Autor e Publicação.

Você pode configurar um exemplo simples, em que você hospeda um Autor e duas instâncias de Publicação:

* Autor > localhost:4502
* Publicar 1 (pub1) > localhost:4503
* Publicar 2 (pub2) > localhost:4504

## Configuração dos agentes de replicação no autor {#setting-replication-agents}

Para criar agentes de replicação, saiba como criar um agente de replicação padrão.

Há três agentes de replicação necessários para o Screens:

1. **Agente de replicação padrão ***(especificado como*** Agente de replicação padrão**)
1. **Agente de replicação do Screens**
1. **Reverter agente de replicação**

### Etapa 1: Criação de um Agente de Replicação Default {#step-creating-a-default-replication-agent}

Siga as etapas abaixo para criar um agente de replicação padrão:

1. Navegue até sua instância do AEM > ícone de martelo > **Operações** > **Configuração**.

   ![screen_shot_2019-02-25at24621pm](assets/screen_shot_2019-02-25at24621pm.png)

1. Selecione o **Replicação** na árvore de navegação esquerda.

   ![screen_shot_2019-02-25at24715pm](assets/screen_shot_2019-02-25at24715pm.png)

1. Selecione o **Agentes sobre o autor** do **Replicação** e selecione **Novo** para criar um novo agente de replicação padrão.

   ![screen_shot_2019-02-25at25400pm](assets/screen_shot_2019-02-25at25400pm.png)

1. Insira o **Título** e **Nome** para criar o agente de replicação, selecione **Criar**.

   ![screen_shot_2019-02-25at25737pm](assets/screen_shot_2019-02-25at25737pm.png)

1. Clique com o botão direito no agente de replicação e selecione **Abertura** para editar as configurações.

   ![screen_shot_2019-02-25at30018pm](assets/screen_shot_2019-02-25at30018pm.png)

1. Selecione **Editar**.

1. No **Configurações do agente** , insira os detalhes.

   >[!NOTE]
   >
   >O usuário deve verificar **Ativado** para habilitar o agente de replicação. Marque esta opção em Default, Screens e Reverse Replication Agents.

   ![screen_shot_2019-02-25at30134pm](assets/screen_shot_2019-02-25at30134pm.png)

1. Navegue até a **Transporte** e insira o **URI**, **Usuário**, e **Senha**.

   ![screen_shot_2019-03-04at34955pm](assets/screen_shot_2019-03-04at34955pm.png)

   >[!NOTE]
   >
   >Você também pode copiar e renomear um agente de replicação padrão existente.


#### Criação de agentes de replicação padrão  {#creating-standard-replication-agents}

1. Criar agente de replicação padrão para pub1 (o agente padrão pronto para uso já deve estar configurado). Por exemplo, *`https://<hostname>:4503/bin/receive?sling:authRequestLogin=1`*
1. Criar agente de replicação padrão para pub2. Você pode copiar o agente de replicação para pub1 e atualizar o transporte a ser usado para pub2 alterando a porta na configuração de transporte. Por exemplo, *`https://<hostname>:4504/bin/receive?sling:authRequestLogin=1`*.

#### Criação de agentes de replicação do Screens {#creating-screens-replication-agents}

1. Crie um agente de replicação AEM Screens para pub1. Pronto para uso, há um agente de replicação do Screens chamado que aponta para a porta 4503. Ative-o.
1. Crie um agente de replicação AEM Screens para pub2. Copie o Agente de replicação do Screens para pub1 e altere a porta para apontar para 4504 para pub2.

   >[!NOTE]
   >Para saber como configurar agentes de replicação do Screens, consulte [Configuração do agente de replicação do Screens](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/administering/configure-screens-replication).

#### Criação de agentes de replicação reversa do Screens {#creating-screens-reverse-replication-agents}

1. Crie um agente de replicação reversa para pub1.
1. Crie um agente de replicação reversa para pub2. Você pode copiar o agente de replicação reversa para pub1 e atualizar o transporte a ser usado para pub2 alterando a porta na configuração de transporte.

## Configuração da topologia de publicação {#setting-up-publish-topology}

### Etapa 1: Configurar A Descoberta Baseada No Apache Sling Oak {#step-configure-apache-sling-oak-based-discovery}

Configurar a descoberta baseada no Apache Sling Oak para todas as instâncias de publicação na topologia

Para cada instância de publicação:

1. Navegue até `https://<host>:<port>/system/console/configMgr`
1. Selecionar **Serviço de descoberta baseado no Apache Sling Oak** Configuração.
1. Atualizar URLs do conector de Topologia: adicione URLs de todas as instâncias de Publicação participantes que sejam:
   * `https://publish:4503/libs/sling/topology/connector`
   * `https://publish:4504/libs/sling/topology/connector`
1. **Conector de topologia `Whitelist` Lista**: adapte-se a IPs ou sub-redes que abrangem todas as instâncias de publicação. Certifique-se `whitelist` o IP/nome do host de todas as instâncias Publish sem o número da porta.

1. Ativar **Interrupção automática de loops locais**

A configuração deve ser idêntica para cada instância de publicação, e o loop local de interrupção automática impede um loop infinito.

#### Etapa 2: Verificar Topologia de Publicação {#step-verify-publish-topology}

Em qualquer uma das instâncias de Publicação, navegue até `https://:/system/console/topology`. Você deve ver cada instância de publicação representada na topologia em **Conectores de topologia de saída**.

#### Etapa 3: Configurar Cluster Artemis do AtiveMQ {#step-setup-activemq-artemis-cluster}

Essa etapa permite criar uma senha criptografada para o cluster AtiveMQ Artemis.
O usuário do cluster e a senha de todas as instâncias de Publicação na topologia devem ser idênticos. A senha da configuração do AtiveMQ Artemis deve ser criptografada. Como cada instância tem sua própria chave de criptografia, é necessário usar o Suporte de criptografia para criar uma cadeia de caracteres de senha criptografada. Em seguida, a senha criptografada pode ser usada na configuração OSGi para AtiveMQ.

Em cada instância de publicação:

1. No console OSGi, navegue até **MAIN** > **Suporte a criptografia** (`https://<host>:<port>/system/console/crypto`).
1. Digite a senha de texto sem formatação desejada (a mesma para todas as instâncias) em **Texto sem formatação**
1. Selecionar **Protect**.
1. Copiar o valor **Texto protegido** no bloco de notas ou no editor de texto. Esse valor pode ser usado na configuração do OSGi para AtiveMQ.

Como cada instância de Publicação, por padrão, tem chaves de criptografia exclusivas, execute essa etapa em cada instância de pub e salve a chave exclusiva para a próxima configuração.

>[!NOTE]
>
>A senha deve começar e terminar com chaves. Por exemplo:
>`{1ec346330f1c26b5c48255084c3b7272a5e85260322edd59119828d1fa0a610e}`

#### Etapa 4: Ativar Cluster Artemis AtiveMQ {#step-activate-activemq-artemis-cluster}

Em cada instância de publicação:

1. Navegue até o gerenciador de configurações do OSGi `https://<host>:<port>/system/console/configMgr`
1. Selecionar **Provedor JMS Apache AtiveMQ Artemis** Configuração
1. Atualize o seguinte:

   * ***Senha do cluster***: usar valor criptografado da etapa anterior por respectiva instância
   * ***Temas***: `{name: 'commands', address: 'com.adobe.cq.screens.commands', maxConsumers: 50}`

#### Verificar Cluster Artemis do AtiveMQ {#verify-activemq-artemis-cluster}

Siga as etapas abaixo em cada instância de publicação:

1. Navegue até o Console OSGi > Principal > AtiveMQ Artemis `https://localhost:4505/system/console/mq`.
1. Verifique e marque para exibir as portas de outras instâncias em Informações de Cluster > Topologia > nós=2, membros=2.
1. Enviar uma Mensagem de Teste (parte superior da tela em Informações do Agente)
1. Informe as seguintes alterações nos campos:

   1. **Destino**: /com.adobe.cq.screens/devTestTopic
   1. **Texto**: Olá, mundo
   1. Exibir o `error.log` de cada instância para que você possa ver se a mensagem foi enviada e recebida no cluster.

>[!NOTE]
>
>A navegação para o console OSGi pode levar alguns segundos após salvar a configuração na etapa anterior. Você também pode verificar o error.log para obter mais detalhes.

Como exemplo, a imagem a seguir é exibida na configuração bem-sucedida do Servidor AtiveMQ Artemis.

Se você não vir a seguinte configuração de */system/console/mq* e navegue até */system/console/mq* e selecione **Restart** para reiniciar o broker.

![image-2018-06-18-18-14-55-449](assets/image-2018-06-18-18-14-55-449.png)

#### Remover requisito de cabeçalho do referenciador {#remove-referrer-header-requirement}

Siga as etapas em cada instância de publicação:

1. Navegue até a **Console OSGi** > **Gerenciador de configurações**
1. Selecionar **Filtro referenciador do Apache Sling**
1. Atualizar configuração e **marque Permitir vazio**

### Configuração da instância de autor e publicação {#configuring-author-and-publish-instance}

Depois de configurar a topologia de publicação, configure as instâncias Autor e Publicar para exibir os resultados práticos da implementação:

>[!NOTE]
>
>**Pré-requisitos**
>
>Para começar a usar este exemplo, crie um projeto do AEM Screens e, em seguida, crie um local, exibição e canal em seu projeto. Adicione conteúdo ao canal e atribua o canal a uma exibição.

#### Etapa 1: iniciar um AEM Screens Player (dispositivo)

1. Inicie uma janela separada do navegador.
1. Ir para o reprodutor do Screens usando o *navegador da web*, ou seja,`https://localhost:4502/content/mobileapps/cq-screens-player/firmware.html` ou inicie o aplicativo AEM Screens. Ao abrir o dispositivo, observe o estado do dispositivo como não registrado.

>[!NOTE]
>
>É possível abrir um reprodutor do AEM Screens usando o aplicativo AEM Screens baixado ou o navegador da Web.

#### Etapa 2: Registrar um dispositivo no autor {#step-registering-a-device-on-author}

1. Ir para `https://localhost:4502/screens.html/content/screens/we-retail` ou selecione o projeto e navegue até Dispositivos > Gerenciador de dispositivos.
1. Selecionar **Registrar dispositivo**.
1. Selecionar **Registro do dispositivo**.
1. Selecione o dispositivo que deseja registrar e selecione **Registrar dispositivo**.
1. Verifique o código de registro e selecione **Validar**.
1. Insira um título para o dispositivo e selecione **Registrar**.

#### Etapa 3: atribuição do dispositivo a ser exibido {#step-assigning-the-device-to-display}

1. Selecionar **Atribuir exibição** na caixa de diálogo da etapa anterior.
1. Selecione o caminho de exibição para seu canal na **Localizações** pasta.
1. Selecionar **Atribuir**.
1. Selecionar **Concluir** para concluir o processo, e agora o dispositivo é atribuído.

Verifique o reprodutor e observe o conteúdo que você adicionou ao canal.

#### Etapa 4: publicação da configuração do dispositivo para publicar instâncias {#step-publishing-device-configuration-to-publish-instances}

**Verificando o dispositivo**

Siga as etapas abaixo para replicar o usuário do dispositivo:

1. Navegue até a página de administrador do usuário. Por exemplo, `https://localhost:4502/useradmin`.
1. Procure por **`screens-devices-master`** grupo.
1. Clique com o botão direito no grupo e selecione **Ativar**.

>[!CAUTION]
>
>Não ative author-publish-screens-service, pois ele é um usuário do sistema usado pela Tarefa do Autor.

Você também pode ativar o dispositivo no Console de Gerenciamento de Dispositivos. Siga as etapas abaixo:

1. Navegue até o projeto do Screens > **Dispositivos**.
1. Selecionar **Gerenciador de dispositivos** na barra de ações.
1. Selecione o dispositivo e **Ativar** na barra de ações, como mostrado na figura abaixo.

![screen_shot_2019-02-21at11036am](assets/screen_shot_2019-02-21at111036am.png)

>[!NOTE]
>
>Como alternativa, após ativar o dispositivo, você também pode editar ou atualizar o URL do servidor. Selecionar **Editar URL do servidor** na barra de ação, como mostrado na figura abaixo, suas alterações se propagam para o AEM Screens player.

![screen_shot_2019-02-21at105527am](assets/screen_shot_2019-02-21at105527am.png)

### Lista de verificação de publicação {#publishing-check-list}

Os pontos a seguir resumem a Lista de verificação de publicação:

* *Usuário de dispositivo do Screens* - É armazenado como um usuário do AEM e ativado no **Ferramentas** > **Segurança** > **Usuários**. O usuário recebe o prefixo &quot;screens&quot; com uma longa sequência serializada.

* *Projeto* - O projeto AEM Screens.
* *Localização* - Local ao qual o dispositivo está conectado.
* *Canais* - um ou mais canais que estão sendo exibidos no local
* *Agendar* - se estiver usando um agendamento, verifique se ele foi publicado
* *Local, cronogramas e pasta de canal* - se os recursos correspondentes estiverem dentro de uma pasta.

Siga as etapas abaixo para verificar o comportamento de criação e publicação:

1. Atualize parte do conteúdo do canal na instância do Autor.
1. Executar **Gerenciar publicação** para publicar novas alterações em todas as instâncias de Publicação.
1. Pressione **Ativar** para ativar o dispositivo de **Gerenciador de dispositivos**.
1. **Editar URL** do URL da instância do autor para um dos URL das instâncias de publicação.
1. Verifique se o conteúdo do canal atualizado é exibido no reprodutor do AEM Screens.
1. Repita essas etapas usando uma instância de publicação diferente.


#### Etapa 5: apontar a instância do dispositivo para publicar no Painel de administração {#step-pointing-the-device-to-publish-instance-in-the-admin-panel}

1. Exiba a interface do administrador no reprodutor do Screens e pressione por muito tempo o canto superior esquerdo para abrir o menu Administrador, no reprodutor do AEM Screens habilitado para toque ou usando o mouse.
1. Selecione o **Configuração** no painel lateral.
1. Alterar instância do autor para Publicar instância no **Servidor**.

Visualize as alterações no seu reprodutor do AEM Screens.

Como alternativa, você também pode atualizar/editar o URL do servidor no console de gerenciamento de dispositivos usando as seguintes etapas:

1. Navegue até o projeto do AEM Screens e selecione a **Dispositivos** pasta.
1. Selecionar **Gerenciador de dispositivos** na barra de ações.
1. Selecione o dispositivo e **Editar URL do servidor** na barra de ação, como mostrado na figura abaixo, e suas alterações serão propagadas para o reprodutor do AEM Screens.

![screen_shot_2019-02-07at31028pm](assets/screen_shot_2019-02-07at31028pm.png)

A variável **Gerenciar publicação** O recurso permite que você forneça atualizações de conteúdo do Autor para a Publicação no dispositivo. Você pode publicar/desfazer a publicação de conteúdo para todo o projeto do AEM Screens ou apenas para um de seus canais, locais, dispositivos, aplicativos ou um agendamento. Para saber mais sobre esse recurso, consulte [Atualização de conteúdo sob demanda](on-demand-content.md).

## Dicas de solução de problemas {#troubleshoot-tips}

Siga a seção abaixo para obter respostas a perguntas frequentes relacionadas à configuração do Author/Publish.

### Como adicionar um redirecionamento de https para http após o registro e a atribuição iniciais? {#add-redirect}

**Solução**
Definir como Habilitar `Proxy/Load Balancer Connection in the Jetty configuration` para `true`.

### Como atualizar conteúdo offline e problemas de download do player com ativos fora do `/content/dam/projects/<project>`? {#update-offline-content}

**Solução**
Conceder permissões de leitura para o usuário em massa offline-update-screens-service e `screens-devices-master` grupo para todos `/content/dam` ou os ativos específicos que deseja usar, se quiser ser mais restritivo.

### Como resolver erros do Agente de replicação do Screens? {#replication-agent}

**Solução**
Verifique se você não marcou a opção Use for reverse replication (Usar para replicação reversa) na configuração do agente. O Agente de replicação do Screens não pode ser usado como um agente de replicação reversa e o escopo desse recurso é encaminhar comandos do dispositivo do Autor para a Publicação.