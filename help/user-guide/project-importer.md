---
title: Novo Importador de Projeto do Arquivo
seo-title: Novo Importador de Projeto do Arquivo
description: Essa funcionalidade permite importar em massa um conjunto de locais de uma planilha CSV/XLS para o projeto do AEM Screens.
seo-description: Essa funcionalidade permite importar em massa um conjunto de locais de uma planilha CSV/XLS para o projeto do AEM Screens.
uuid: e1ad76ae-6925-4d72-80ce-8343a76125ce
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: administering
discoiquuid: f1df8d05-bb61-4bc9-aea1-c6af9e3519b4
docset: aem65
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# Novo Importador de Projeto do Arquivo {#new-project-importer-from-file}

Esta seção descreve uma funcionalidade para importar em massa um conjunto de locais de uma planilha CSV/XLS para seu projeto do AEM Screens.

## Introdução {#introduction}

Ao configurar um projeto do AEM Screens, pela primeira vez em sua organização, você também precisa criar todos os locais. Se o seu projeto envolve um grande número de locais, ele resulta em uma tarefa tediosa que envolve muito clique e espera na interface do usuário.

O objetivo deste recurso é reduzir o tempo necessário para configurar o projeto e, assim, resolver problemas de orçamento.

Ao permitir que o autor forneça uma planilha como um arquivo de entrada e permitir que o sistema crie automaticamente a árvore de localização no back-end, este recurso:

* *atinge desempenho muito melhor do que clicar manualmente na interface do usuário*
* *permite que o cliente exporte os locais que possui de seu próprio sistema e importe-os facilmente diretamente no AEM*

Isso economiza tempo e dinheiro durante a configuração inicial do projeto ou ao estender as telas AEM existentes para novos locais.

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
| ***[./jcr:title]{string*}** | O nome do modelo a ser usado (ou seja, o local para *telas/núcleo/modelos/local*) |
| ***template {string}*** | Título opcional a ser usado para a página |
| ***[./jcr:description]{string}*** | Descrição opcional a ser usada para a página |

O arquivo da planilha (CSV/XLS) requer as seguintes colunas:

* **path {string}** O caminho para o local a ser importado, onde a raiz do caminho é a pasta de localização do projeto (ou seja, */foo* será importado para */content/screens/&lt;project&gt;/location/foo*)

* **modelo {string}** O modelo a ser usado para o novo local, por enquanto, o único valor permitido é "location", mas isso será estendido para todos os modelos de Tela no futuro ("display", "sequencechannel, e assim por diante)
* [**./*] {string}** Qualquer propriedade opcional a ser definida no local (isto é, ./jcr:title, ./jcr:description, ./foo, ./barra). A versão atual não permite filtragem no momento

>[!NOTE]
>
>Qualquer coluna que não corresponda às condições acima será simplesmente ignorada. Por exemplo, se você tiver outra coluna definida no arquivo da planilha (CSV/XLS) que não seja **caminho**,**modelo**,**título** e **descrição** no arquivo, esses campos serão ignorados e o Importador **de** projeto não validará esses campos adicionais para importar seu projeto para o projeto do AEM Screens.

## Usando o Importador de projetos {#using-project-importer}

A seção a seguir descreve como o Importador de projeto é usado em um projeto do AEM Screens.

>[!CAUTION]
>
>Limitações:
>
>* Arquivos que não sejam CSV/XLS/XLSX não são suportados na versão atual.
>* Não existe filtragem das propriedades para arquivos importados e nada que comece com "./" será importado.
>



### Pré-requisitos {#prerequisites}

* Criar um novo projeto chamado **DemoProjectImport**

* Use um arquivo CSV ou Excel de amostra que você precisa importar.

Para fins de demonstração, você pode baixar um arquivo do Excel na seção abaixo.

[Obter arquivo](assets/minimal-file.xls)

### Importação do arquivo com os campos mínimos obrigatórios {#importing-the-file-with-minimum-required-fields}

Siga as etapas abaixo para importar um arquivo para a pasta de locais com o mínimo de campos obrigatórios:

>[!NOTE]
>
>O exemplo a seguir mostra os quatro campos mínimos necessários para importar seu projeto:

![screen_shot_2019-05-14at21523pm](assets/screen_shot_2019-05-14at21523pm.png)

1. Navegue até o projeto do AEM Screens (**DemoProjectImport**).

   ![screen_shot_2019-05-12at52651am](assets/screen_shot_2019-05-12at52651am.png)

1. Selecione o projeto,** DemoProjectImporter **—&gt;** Criar **—&gt;** Importar locais** na barra lateral.

   ![screen_shot_2019-05-12at52433am](assets/screen_shot_2019-05-12at52433am.png)

1. O assistente **Importar** é aberto. Selecione o arquivo que você tem para o seu projeto com locais ou selecione o arquivo (arquivo ***mínimo.xls***) que você baixou da seção *Pré-requisitos* .

   Depois de selecionar o arquivo, clique em **Avançar**.

   ![screen_shot_2019-05-15at113718am](assets/screen_shot_2019-05-15at113718am.png)

1. Verifique o conteúdo do arquivo (locais) no assistente de importação e clique em **Importar**.

   ![screen_shot_2019-05-12at53131am](assets/screen_shot_2019-05-12at53131am.png)

1. Como resultado, agora você poderá visualizar todos os locais importados para o seu projeto.

   ![screen_shot_2019-05-12at53450am](assets/screen_shot_2019-05-12at53450am.png)

