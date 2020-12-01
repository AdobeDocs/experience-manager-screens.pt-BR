---
title: Novo Importador de Projeto do Arquivo
seo-title: Novo Importador de Projeto do Arquivo
description: Essa funcionalidade permite importar em massa um conjunto de locais de uma planilha CSV/XLS para seu projeto da AEM Screens.
seo-description: Essa funcionalidade permite importar em massa um conjunto de locais de uma planilha CSV/XLS para seu projeto da AEM Screens.
uuid: e1ad76ae-6925-4d72-80ce-8343a76125ce
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: administering
discoiquuid: f1df8d05-bb61-4bc9-aea1-c6af9e3519b4
docset: aem65
translation-type: tm+mt
source-git-commit: 121aee4c8bf08e30898cc25d274ef4fc6bded5aa
workflow-type: tm+mt
source-wordcount: '698'
ht-degree: 1%

---


# Novo Importador de Projeto do Arquivo {#new-project-importer-from-file}

Esta seção descreve uma funcionalidade para importar em massa um conjunto de locais de uma planilha CSV/XLS para seu projeto AEM Screens.

## Introdução {#introduction}

Ao configurar um projeto da AEM Screens, pela primeira vez em sua organização, é necessário criar todos os locais também. Se o seu projeto envolve um grande número de locais, ele resulta em uma tarefa tediosa que envolve muitos cliques e espera na interface do usuário.

O objetivo deste recurso é reduzir o tempo necessário para configurar o projeto e, assim, resolver problemas de orçamento.

Ao permitir que o autor forneça uma planilha como um arquivo de entrada e permitir que o sistema crie automaticamente a árvore de localização no back-end, este recurso:

* *atinge desempenho muito melhor do que clicar manualmente na interface do usuário*
* *permite que o cliente exporte os locais que ele possui de seu próprio sistema e importe-os diretamente no AEM*

Isso economiza tempo e dinheiro durante a configuração inicial do projeto ou ao estender o AEM Screens existente para novos locais.

## Visão geral da arquitetura {#architectural-overview}

O diagrama a seguir mostra a visão geral da arquitetura do recurso Importador do projeto:

![screen_shot_2019-05-14at20618pm](assets/screen_shot_2019-05-14at20618pm.png)

### Modelo de dados {#data-model}

O modelo de dados do Importador de projetos está descrito abaixo:

>[!NOTE]
>
>A versão atual suporta apenas a importação de locais.

| **Propriedade** | **Descrição** |
|---|---|
| ***path {string*}** | O caminho do recurso para o local |
| ***[./jcr:title] {string*}** | O nome do modelo a ser usado (ou seja, o local para *telas/core/modelos/location*) |
| ***template {string}*** | Título opcional a ser usado para a página |
| ***[./jcr:description] {string}*** | Descrição opcional a ser usada para a página |

O arquivo da planilha (CSV/XLS) requer as seguintes colunas:

* **caminho {cadeia}** O caminho para o local a ser importado, onde a raiz do caminho é a pasta de localização do projeto (isto é,  */* o caminho será importado para  */content/screens/&lt;project>/location/foo*)

* **modelo {string}** O modelo a ser usado para o novo local, por enquanto, o único valor permitido é &quot;location&quot;, mas isso será estendido para todos os modelos de Tela no futuro (&quot;display&quot;, &quot;sequencechannel, e assim por diante)
* **[./*] {string}** Qualquer propriedade opcional a ser definida no local (isto é, ./jcr:title, ./jcr:description, ./foo, ./barra). A versão atual não permite filtragem no momento

>[!NOTE]
>
>Qualquer coluna que não corresponda às condições acima será simplesmente ignorada. Por exemplo, se você tiver outra coluna definida no arquivo da planilha (CSV/XLS) diferente de **path**,**template**,**title**, e **description** no arquivo, esses campos serão ignorados e o **Importador do projeto** não validará esses campos adicionais campos para importar seu projeto para o projeto da AEM Screens.

## Usando o Importador de Projeto {#using-project-importer}

A seção a seguir descreve como o Importador de projeto é usado em um projeto da AEM Screens.

>[!CAUTION]
>
>Limitações:
>
>* Arquivos que não sejam CSV/XLS/XLSX não são suportados na versão atual.
>* Não existe filtragem das propriedades para arquivos importados e nada que comece com &quot;./&quot; será importado.

>



### Pré-requisitos {#prerequisites}

* Crie um novo projeto chamado **DemoProjectImport**

* Use um arquivo CSV ou Excel de amostra que você precisa importar.

Para fins de demonstração, você pode baixar um arquivo do Excel na seção abaixo.

[Obter arquivo](assets/minimal-file.xls)

### Importando o arquivo com os campos mínimos obrigatórios {#importing-the-file-with-minimum-required-fields}

Siga as etapas abaixo para importar um arquivo para a pasta de locais com o mínimo de campos obrigatórios:

>[!NOTE]
>
>O exemplo a seguir mostra os quatro campos mínimos necessários para importar seu projeto:

![screen_shot_2019-05-14at21523pm](assets/screen_shot_2019-05-14at21523pm.png)

1. Navegue até o seu projeto do AEM Screens (**DemoProjectImport**).

   ![screen_shot_2019-05-12at52651am](assets/screen_shot_2019-05-12at52651am.png)

1. Selecione o projeto,** DemoProjectImporter **—>** Criar **—>** Importar locais** na barra lateral.

   ![screen_shot_2019-05-12at52433am](assets/screen_shot_2019-05-12at52433am.png)

1. O assistente **Importar** é aberto. Selecione o arquivo que você tem para o seu projeto com locais ou selecione o arquivo (***Minimum-file.xls***) que você baixou da seção *Pré-requisitos*.

   Depois de selecionar o arquivo, clique em **Próximo**.

   ![screen_shot_2019-05-15at113718am](assets/screen_shot_2019-05-15at113718am.png)

1. Verifique o conteúdo do arquivo (locais) do Assistente de importação e clique em **Importar**.

   ![screen_shot_2019-05-12at53131am](assets/screen_shot_2019-05-12at53131am.png)

1. Como resultado, agora você poderá visualização todos os locais importados para o seu projeto.

   ![screen_shot_2019-05-12at53450am](assets/screen_shot_2019-05-12at53450am.png)

