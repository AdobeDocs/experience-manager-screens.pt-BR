---
title: Novo importador de projetos do arquivo
seo-title: Novo importador de projetos do arquivo
description: Essa funcionalidade permite importar em massa um conjunto de locais de uma planilha CSV/XLS para seu projeto do AEM Screens.
seo-description: Essa funcionalidade permite importar em massa um conjunto de locais de uma planilha CSV/XLS para seu projeto do AEM Screens.
uuid: e1ad76ae-6925-4d72-80ce-8343a76125ce
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: administering
discoiquuid: f1df8d05-bb61-4bc9-aea1-c6af9e3519b4
docset: aem65
feature: Administração do Screens
role: Administrator
level: Intermediate
source-git-commit: 4611dd40153ccd09d3a0796093157cd09a8e5b80
workflow-type: tm+mt
source-wordcount: '700'
ht-degree: 2%

---


# Novo importador de projetos do arquivo {#new-project-importer-from-file}

Esta seção descreve uma funcionalidade de importar em massa um conjunto de locais de uma planilha CSV/XLS para seu projeto do AEM Screens.

## Introdução {#introduction}

Ao configurar um projeto do AEM Screens, pela primeira vez em sua organização, é necessário criar todos os locais também. Se o seu projeto envolve um grande número de locais, ele resulta em uma tarefa entediante que envolve muito clique e espera na interface do usuário.

O objetivo desse recurso é reduzir o tempo necessário para configurar o projeto e, assim, resolver problemas de orçamento.

Ao permitir que o autor forneça uma planilha como um arquivo de entrada e que o sistema crie automaticamente a árvore de localização no back-end, este recurso:

* *atinge muito melhor desempenho do que clicar manualmente na interface do usuário*
* *permite que o cliente exporte os locais que possui de seu próprio sistema e importe-os facilmente diretamente no AEM*

Isso economiza tempo e dinheiro durante a configuração inicial do projeto ou ao estender o AEM Screens existente para novos locais.

## Visão geral da arquitetura {#architectural-overview}

O diagrama a seguir mostra a visão geral da arquitetura do recurso Importador de projetos:

![screen_shot_2019-05-14at20618pm](assets/screen_shot_2019-05-14at20618pm.png)

### Modelo de dados {#data-model}

O modelo de dados para o Importador de projetos está descrito abaixo:

>[!NOTE]
>
>A versão atual suporta apenas a importação de locais.

| **Propriedade** | **Descrição** |
|---|---|
| ***caminho {string*}** | O caminho do recurso para o local |
| ***[./jcr:title] {string*}** | O nome do modelo a ser usado (ou seja, o local para *screens/core/templates/location*) |
| ***modelo {string}*** | Título opcional a ser usado para a página |
| ***[./jcr:description] {string}*** | Descrição opcional a ser usada para a página |

O arquivo da planilha (CSV/XLS) requer as seguintes colunas:

* **caminho {string}** O caminho do local a ser importado, onde a raiz do caminho é a pasta de localização do projeto (ou seja,  */* fooserá importado para  */content/screens/&lt;project>/locations/foo*)

* **modelo {string}** O modelo a ser usado para o novo local, por enquanto, o único valor permitido é &quot;location&quot;, mas isso será estendido para todos os modelos do Screens no futuro (&quot;display&quot;, &quot;sequencechannel, e assim por diante)
* **[./*] {string}** Qualquer propriedade opcional a ser definida no local (ou seja, ./jcr:title, ./jcr:description, ./foo, ./barra). A versão atual não permite filtragem no momento

>[!NOTE]
>
>Qualquer coluna que não corresponda às condições acima será ignorada. Por exemplo, se você tiver qualquer outra coluna definida em seu arquivo de planilha (CSV/XLS) diferente de **path**,**template**,**title**, e **description** em seu arquivo, esses campos serão ignorados e **Importador de projeto** não validará esses campos adicionais campos para importar o projeto para o projeto do AEM Screens.

## Usando o Importador de Projetos {#using-project-importer}

A seção a seguir descreve como o Importador de projeto é usado em um projeto do AEM Screens.

>[!CAUTION]
>
>Limitações:
>
>* Arquivos diferentes das extensões CSV/XLS/XLSX não são suportados na versão atual.
>* Não existe nenhuma filtragem das propriedades para arquivos importados e qualquer coisa que comece com &quot;./&quot; será importado.

>



### Pré-requisitos {#prerequisites}

* Crie um novo projeto chamado **DemoProjectImport**

* Use um arquivo CSV de amostra ou do excel que você precisa importar.

Para fins de demonstração, você pode baixar um arquivo do excel na seção abaixo.

[Obter arquivo](assets/minimal-file.xls)

### Importação do arquivo com os campos mínimos obrigatórios {#importing-the-file-with-minimum-required-fields}

Siga as etapas abaixo para importar um arquivo para a pasta de locais com os campos mínimos necessários:

>[!NOTE]
>
>O exemplo a seguir mostra no mínimo quatro campos necessários para importar o projeto:

![screen_shot_2019-05-14at21523pm](assets/screen_shot_2019-05-14at21523pm.png)

1. Navegue até o projeto do AEM Screens (**DemoProjectImport**).

   ![screen_shot_2019-05-12at52651am](assets/screen_shot_2019-05-12at52651am.png)

1. Selecione o projeto,** DemoProjectImporter **—>** Criar **—>** Importar locais** da barra lateral.

   ![screen_shot_2019-05-12at52433am](assets/screen_shot_2019-05-12at52433am.png)

1. O assistente **Importar** é aberto. Selecione o arquivo que você tem para seu projeto com localizações ou selecione o arquivo (***Minimum-file.xls***) que você baixou na seção *Pré-requisitos*.

   Depois de selecionar o arquivo, clique em **Next**.

   ![screen_shot_2019-05-15at113718am](assets/screen_shot_2019-05-15at113718am.png)

1. Verifique o conteúdo do arquivo (locais) no assistente de Importação e clique em **Importar**.

   ![screen_shot_2019-05-12at53131am](assets/screen_shot_2019-05-12at53131am.png)

1. Como resultado, agora você poderá visualizar todos os locais importados para o seu projeto.

   ![screen_shot_2019-05-12at53450am](assets/screen_shot_2019-05-12at53450am.png)

