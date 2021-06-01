---
title: Funções e responsabilidades do projeto AEM Screens
seo-title: Funções e responsabilidades do projeto AEM Screens
description: A página descreve as funções e responsabilidades do projeto do AEM Screens
seo-description: A página descreve as funções e responsabilidades do projeto do AEM Screens
source-git-commit: 4611dd40153ccd09d3a0796093157cd09a8e5b80
workflow-type: tm+mt
source-wordcount: '1263'
ht-degree: 11%

---


# Funções e responsabilidades do projeto {#roles-responsibilities}

Como um implementador de AEM experiente, provavelmente você já viu funções conhecidas como *Autores*, *Desenvolvedores* e *TI/Técnicos*.

Em um projeto típico do AEM Screens, as funções são mais refinadas, pois cada uma delas tem um propósito importante no projeto.

O diagrama abaixo mostra as funções que referiremos em todo o guia.

![](/help/assets/project-roles-revised.png)

>[!NOTE]
>
> Muitas dessas funções podem ser internas ou terceirizadas, dependendo de como cada projeto é criado.

## Definindo Funções {#roles}

A seção a seguir fornece uma visão geral sobre o público-alvo:

### Adobe {#adobe-audience}

O Adobe inclui recursos do Adobe Managed Services, como o CSE (Customer Success Engineer) e o Adobe Support.

### Implementadores do AEM {#aem-implementors}

AEM Os implementadores são responsáveis por executar tarefas de desenvolvimento e integração para desenvolver a experiência do usuário, modelos personalizados e integrações de back-end para AEM.

Os recursos personalizados necessários para endereçar parâmetros UX (Experiência do Usuário) do cliente final também são capturados e entregues por meio desse processo.

AEM Implementadores normalmente implantarão a funcionalidade personalizada em fases ao longo do tempo para locais. Por exemplo, eles podem primeiro estabelecer suporte para reprodução de vídeo básico em loop ou conteúdo gráfico estático. A próxima fase pode incluir a ativação da capacidade de suportar a reprodução de conteúdo localizado por meio de modelos dinâmicos e tags de metadados, com fases adicionais incorporando o suporte a elementos interativos por meio de telas de toque, sensores, acionadores dinâmicos e assim por diante.

### Integradores de AV {#av-integrators}

O Integrador de A/V é o fornecedor/parceiro de hardware. Essa é a parte que lida com design de varejo e preparação do site, incluindo aquisição de hardware, configuração e implantação. Normalmente, é um terceiro contratado que tem acesso a um NOC (Network Operations Center, centro de operações de rede). Em muitos casos, o Integrador de A/V é o proprietário do projeto devido ao seu envolvimento contínuo após o lançamento.

Um Integrador de AV é responsável pela realização de descobertas com clientes finais para definir os requisitos determinantes do escopo do projeto para projetar, criar e gerenciar efetivamente as implantações em hardware de sinalização digital.

#### Considerando o Parceiro de Hardware {#selecting-hardware-partner}

É fundamental selecionar o Parceiro de hardware correto. Devem ser consideradas as seguintes questões:

1. Quais são os termos do contrato de nível de serviço?

1. O que é a cobertura Global?

1. É um suporte de 24 horas?

1. Como os dispositivos serão gerenciados?

1. Quais são os sistemas ativos de acompanhamento e de alerta?

### Estrategistas de negócios {#business-strategist}

Os Estrategistas de negócios representam os tomadores de decisão da empresa. Esse papel está muito envolvido nas etapas de descoberta e requisitos e é o principal motor do projeto.

São eles que definem os requisitos e configuram as métricas de KPI. A estratégia de negócios pode ser a seguinte:

* Comercialização ou
* Gerente de vendas: criações do gerente de estratégia digital/gerenciamento de conteúdo.

A equipe de criação e gerenciamento de conteúdo trabalha em conjunto com a equipe de estratégia e transforma os requisitos em experiências do cliente. Eles orientam o design de UX geral e preparam o conteúdo que complementa a marca.

Os anúncios e o gerenciamento de conteúdo podem ser os seguintes:

* Agência de criação ou
* Gerenciador de marca

### Gerentes de projeto {#project-managers}

Gerentes de projeto geralmente gerenciam toda a implantação da sua implantação do AEM Screens. Um gerente de projeto é a pessoa-ponto de toda a implementação do projeto designado e desempenha grandes responsabilidades, como definir prazos, lidar com necessidades e comunicações da equipe, enfrentar desafios e garantir que os objetivos sejam atingidos.

>[!NOTE]
>
>Para saber mais detalhes sobre diferentes funções e responsabilidades e o público-alvo de um projeto de sinalização digital, visite **[Funções e responsabilidades do projeto](https://helpx.adobe.com/experience-manager/6-5/screens/using/project-roles-responsibilities.html)**.


## Estágios do projeto {#project-stages}

Para oferecer suporte a uma implantação bem-sucedida do Digital Signage, é comum segmentar o projeto em três estágios.  Normalmente, esses estágios são chamados de **Days**. Não são dias literais, mas designações para cada grande etapa do projeto.

1. O primeiro estágio é conhecido como *Dia Zero*. Esta etapa inclui todos os esforços de pré-vendas e descoberta necessários para definir totalmente o escopo do projeto.
1. A segunda etapa, *Dia um*, refere-se a todas as atividades incluídas no esforço de implantação.
1. A terceira e última etapa *O segundo dia* refere-se a todas as operações em andamento e a todos os elementos de suporte como parte da solução total.

>[!NOTE]
>
>Embora este guia enfatize principalmente o *Primeiro Dia* e o *Segundo dia*, é necessário prestar atenção aos três estágios para executar um projeto bem-sucedido de sinalização digital.
>
>Siga um vídeo adicional em **[Gerenciamento e implantação do projeto](https://helpx.adobe.com/experience-manager/6-5/screens/using/project-management-and-deployment.html)** para saber mais sobre a pré-produção do projeto, a iniciação do projeto e a progressão do projeto.

## Gráfico RACI {#raci-chart}

Veja a seguir um exemplo de gráfico RACI usando as definições de função.

>[!NOTE]
>
>Este gráfico não deve ser seguido exatamente, mas sim para fornecer um exemplo de tarefas e considerações comuns em um projeto do AEM Screens.

### Definições de RACI {#raci-definitions}

* **Responsável**: Faz o trabalho para concluir a tarefa.

* **Responsável**: Os representantes trabalham e são a última parte a analisar a tarefa antes de ela ser concluída.

* **Consultado**: Revisa a tarefa ou o delivery para fornecer entrada.

* **Informações**: Mantido informado sobre o progresso da tarefa, mas não envolvido nos detalhes do delivery.

A seguir, há um exemplo de gráfico RACI usando as definições de função e fornece um exemplo de tarefas e considerações comuns em um projeto do AEM Screens.

A tabela a seguir resume o **Dia Zero: Considerações pré-vendas**:

| **Fase** | **Integrador A/V** | **Implementador de AEM** | **Estratégia comercial** | **Gerenciamento de conteúdo** |
|---|---|---|---|---|
| Formação de Equipe e Seleção de Fornecedor | I | I | ARM | ARM |
| Acordo sobre Funções e Responsabilidades | ARM | ARM | ARM | ARM |
| Alinhamento em metas estratégicas | CI | I | ARM | ARM |
| Necessidades de relatórios e identificação de ROI | I | C | ARM | C |
| Visita ao site e requisitos de hardware | ARM | I | C | C |
| Definição de Processo de Suporte | C | I | ARM | I |
| Definir Escopo do Plano de Trabalho e Projeto | ARM | ARM | C | C |

A tabela a seguir resume o **Dia um: Implementação do projeto (Design do aplicativo)**:

| **Fase** | **Integrador A/V** | **Implementador de AEM** | **Estratégia comercial** | **Gerenciamento de conteúdo** |
|---|---|---|---|---|
| Acordo sobre Funções e Responsabilidades | ARM | ARM | ARM | ARM |
| Alinhamento no Plano e Programação do Projeto | ARM | ARM | C | C |
| Avaliar os ambientes atuais do servidor | I | ARM | I | I |
| Requisitos de design UX | I | ARM | C | ARM |
| Validação dos requisitos técnicos | I | ARM | ARM | C |
| Design da arquitetura | I | ARM | I | I |
| Validar a estrutura de dados com o design da interface do usuário | I | ARM | C | C |
| Desenvolvimento de aplicativos | ARM | ARM | ARM | ARM |
| Configuração de projeto do AEM Screens | I | ARM | C | I |
| Implementação do Analytics | I | ARM | C | - |
| Teste e implantação | ARM | C | ARM | I |
| Configuração do servidor | I | ARM | I | I |
| Plano de atualização de conteúdo | I | ARM | C | C |
| Plano do piloto para a transição da produção | ARM | ARM | I | I |
| Transferência de conhecimento | ARM | ARM | I | I |

A tabela a seguir resume o **Dia um: Implementação de projeto (disponibilidade de varejo)**:

| **Fase** | **Integrador A/V** | **Implementador de AEM** | **Estratégia comercial** | **Gerenciamento de conteúdo** |
|---|---|---|---|---|
| Pedido e armazenamento de hardware | ARM | I | I | I |
| Programação de integração de varejo | I | I | C | ARM |
| Teste de aceitação do usuário de preparo | I | C | ARM |  |
| Configuração em massa de hardware | ARM | I | C | I |
| Contrato de suporte pós-lançamento | ARM | C | ARM | C |

A tabela a seguir resume o **Dia um: Dia Um: Implementação do projeto (Hardware)**:

| **Fase** | **Integrador A/V** | **Implementador de AEM** | **Estratégia comercial** | **Gerenciamento de conteúdo** |
|---|---|---|---|---|
| Acordo sobre Funções e Responsabilidades | ARM | ARM | ARM | ARM |
| O Design de varejo inclui operações de fiação | - | - | - | - |
| Seleção de hardware do player | RAC | - | - | - |
| Gerenciamento de dispositivos da principal | ARM | I | - | - |
| Pedido e armazenamento e configuração do dispositivo | ARM | CI | I | - |
| Definição de Processo de Suporte | ARM | I | ARM | C |

>[!NOTE]
>
>As funções mudam durante o segundo dia (suporte pós-lançamento).

* **Autor**: Gestão de conteúdo + Estratégia

* **Desenvolvedor**: Normalmente, é um membro da equipe de implementação da AEM Screens ou entrega para a equipe de desenvolvimento interno

* **Técnico**: Contratado pelo integrador de AV ou faz parte da mesma empresa.

A tabela a seguir resume o **Dia Dois: Gráfico RACI de suporte pós-lançamento**:

| **Fase** | **Autor** | **Desenvolvedor** | **Técnico** |
|---|---|---|---|
| *Dia dois: Suporte pós-lançamento* |
| Acordo sobre Funções e Responsabilidades | ARM | ARM | ARM |
| Suporte de nível 1 | I | I | ARM |
| Suporte de nível 2 | I | C | ARM |
| Suporte de nível 3 | I | ARM | C |
| Atualização de conteúdo | ARM | I | I |
| Avaliar o sucesso do UX e identificar áreas de melhorias | ARM | C | I |
