---
title: Funções e responsabilidades do projeto AEM Screens
description: Saiba mais sobre as funções e responsabilidades do projeto AEM Screens.
exl-id: 9377625b-529a-4b46-89d9-f526de398639
source-git-commit: dcaaa1c7ab0a55cecce70f593ed4fded8468130b
workflow-type: tm+mt
source-wordcount: '1254'
ht-degree: 0%

---

# Funções e responsabilidades do projeto {#roles-responsibilities}

Como um implementador de AEM experiente, provavelmente você já viu funções conhecidas como *Autores*, *Desenvolvedores* e *Técnicos de TI*.

Em um projeto AEM Screens típico, as funções são refinadas, pois cada uma serve a um propósito importante no projeto.

O diagrama a seguir mostra as funções que você pode esperar em todo o guia.

![](/help/assets/project-roles-revised.png)

>[!NOTE]
>
> Muitas dessas funções podem ser internas ou terceirizadas, dependendo de como cada projeto é configurado.

## Definição de Funções {#roles}

A seção a seguir fornece uma visão geral do público-alvo:

### Adobe {#adobe-audience}

A Adobe inclui recursos da Adobe Managed Services, como o CSE (Customer Success Engineer, Engenheiro especializado na fidelização de clientes) e o Suporte da Adobe.

### Implementadores do AEM {#aem-implementors}

Os implementadores do AEM são responsáveis por executar tarefas de desenvolvimento e integração para desenvolver a experiência do usuário, modelos personalizados e integrações de back-end para o AEM.

Os recursos personalizados necessários para lidar com parâmetros UX (experiência do usuário) do cliente final também são capturados e entregues por meio desse processo.

Os implementadores da AEM normalmente implantarão a funcionalidade personalizada em fases ao longo do tempo nos locais. Por exemplo, eles podem primeiro estabelecer suporte para a reprodução de vídeo em loop básico ou conteúdo gráfico estático. A próxima fase inclui a capacidade de oferecer suporte à reprodução de conteúdo localizado por meio de modelos dinâmicos e tags de metadados. Outras fases incorporam suporte a elementos interativos por meio de telas sensíveis ao toque, sensores, acionadores dinâmicos etc.

### Integradores de áudio e vídeo {#av-integrators}

O integrador de áudio-vídeo é o fornecedor-parceiro de hardware. Eles são a parte que lida com design de varejo e preparação de sites, incluindo aquisição, configuração e implantação de hardware. Normalmente, é um terceiro contratado que tem acesso a um NOC (Network Operations Center, centro de operações de rede). Muitas vezes, o Integrador de áudio e vídeo é o proprietário do projeto devido ao seu envolvimento contínuo após o lançamento.

Um Integrador de áudio e vídeo é responsável por realizar a detecção com os clientes finais para definir os requisitos, determinando o escopo do projeto para projetar, criar e gerenciar com eficácia as implantações em torno do hardware de sinalização digital.

>[!NOTE]
>
> Você deve ter um Integrador de áudio e vídeo como parte de sua implantação do AEM Screens.

#### Considerar parceiro de hardware {#selecting-hardware-partner}

É fundamental clicar no parceiro de hardware correto. Devem ser consideradas as seguintes questões:

1. Quais são os termos do Service level agreement?

1. O que é cobertura global?

1. É um suporte 24 horas?

1. Como os dispositivos são gerenciados?

1. Quais são os sistemas ativos de monitoramento e aviso?

### Estratégicos de negócios {#business-strategist}

Os Business Strategists representam os tomadores de decisão na empresa. Essa função está altamente envolvida nos estágios de descoberta e requisitos e é o principal impulsionador do projeto.

São eles que definem requisitos e configuram métricas de KPI. A estratégia de negócios pode ser a seguinte:

* Marketing ou
* Gerente de vendas Criativas do Digital Strategy Manager / Gerenciamento de conteúdo.

A equipe de Criação e Gerenciamento de conteúdo trabalha em conjunto com a equipe de Estratégia e transforma as necessidades em experiências do cliente. Eles orientam o design geral de UX e preparam conteúdos que complementam a marca.

O gerenciamento de criação e conteúdo pode ser o seguinte:

* Agência Creative ou,
* Gerente de marca

### Gerentes de projeto {#project-managers}

Os gerentes de projeto normalmente gerenciam toda a implantação da sua implantação do AEM Screens. Um gerente de projeto é a pessoa responsável por toda a implementação do projeto designado. Eles executam responsabilidades importantes, como definir cronogramas e lidar com as necessidades da equipe. Elas também afetam as comunicações, enfrentando desafios e garantindo que as metas sejam atingidas.

>[!NOTE]
>
>Para saber mais detalhes sobre as diferentes funções e responsabilidades e o público-alvo de um projeto de sinalização digital, visite **[Funções e responsabilidades do projeto](https://experienceleague.adobe.com/pt-br/docs/experience-manager-screens/user-guide/digital-signage-network/project-roles-responsibilities)**.


## Estágios do Projeto {#project-stages}

Para oferecer suporte a uma implantação bem-sucedida da sinalização digital, é comum segmentar o projeto em três estágios. Esses estágios geralmente são chamados de **Dias**. Não são dias literais, mas designações para cada fase importante do projeto.

1. O primeiro estágio é chamado de *Dia Zero*. Este estágio inclui todos os esforços de pré-vendas e detecção necessários para definir o escopo do projeto.
1. O segundo estágio, *Primeiro Dia*, se refere a todas as atividades incluídas no esforço de implantação.
1. O terceiro e último estágio é *Dia Dois*. Refere-se a todas as operações em andamento e aos elementos de suporte como parte da solução total.

>[!NOTE]
>
>Embora este guia enfatize principalmente o *Primeiro Dia* e o *Segundo Dia*, é necessário prestar atenção aos três estágios para executar um projeto de sinalização digital bem-sucedido.
>
>Para saber mais sobre a pré-produção, a iniciação e a progressão do projeto, assista a um vídeo sobre **[Gerenciamento e Implantação de Projetos](https://experienceleague.adobe.com/pt-br/docs/experience-manager-screens/user-guide/digital-signage-network/project-management-and-deployment)**.

## Gráfico RACI {#raci-chart}

Veja a seguir um exemplo de gráfico RACI usando as definições de função.

>[!NOTE]
>
>Não é necessário seguir o gráfico exatamente. Em vez disso, ele tem como objetivo fornecer um exemplo de tarefas e considerações comuns em um projeto do AEM Screens.

### Definições de RACI {#raci-definitions}

* **Responsável**: faz o trabalho para concluir a tarefa.

* **Responsável**: os representantes trabalham e são os últimos a revisar a tarefa antes que ela seja concluída.

* **Consultado**: analisa a tarefa ou a entrega para fornecer entrada.

* **Informado**: mantido informado sobre o progresso da tarefa, mas não está envolvido nos detalhes da entrega.

Este é um exemplo de gráfico RACI usando as definições de função e fornece um exemplo de tarefas e considerações comuns em um projeto AEM Screens.

A tabela a seguir resume o **Dia Zero: Considerações sobre Pré-vendas**:

| **Fase** | **Integrador de áudio e vídeo** | **Implementador do AEM** | **Estratégia comercial** | **Gerenciamento de conteúdo** |
|---|---|---|---|---|
| Formação de Equipe e Seleção de Fornecedor | I | I | RA | RA |
| Acordo sobre Funções e Responsabilidades | RA | RA | RA | RA |
| Alinhamento em metas estratégicas | IC | I | RA | RA |
| Necessidades de relatórios e identificação do ROI | I | C | RA | C |
| Visitas ao site e requisitos de hardware | RA | I | C | C |
| Definição do processo de suporte | C | I | RA | I |
| Definir Escopo do Trabalho e Plano de Projeto | RA | RA | C | C |

A tabela a seguir resume o **Primeiro Dia: Implementação de Projeto (Design de Aplicativo)**:

| **Fase** | **Integrador de áudio e vídeo** | **Implementador do AEM** | **Estratégia comercial** | **Gerenciamento de conteúdo** |
|---|---|---|---|---|
| Acordo sobre Funções e Responsabilidades | RA | RA | RA | RA |
| Alinhamento com o plano e o agendamento do projeto | RA | RA | C | C |
| Avaliar os ambientes de servidor atuais | I | RA | I | I |
| Requisitos de design de UX | I | RA | C | RA |
| Validação dos requisitos técnicos | I | RA | RA | C |
| Projeto de arquitetura | I | RA | I | I |
| Validar a estrutura de dados com design da interface do usuário | I | RA | C | C |
| Desenvolvimento de aplicativos | RA | RA | RA | RA |
| Configuração de projeto do AEM Screens | I | RA | C | I |
| Implementação do Analytics | I | RA | C | - |
| Teste e implantação | RA | C | RA | I |
| Configuração do servidor | I | RA | I | I |
| Plano de atualização de conteúdo | I | RA | C | C |
| Plano de transição do piloto para a produção | RA | RA | I | I |
| Transferência de conhecimento | RA | RA | I | I |

A tabela a seguir resume o **Primeiro Dia: Implementação do Projeto (Disponibilidade do Retail)**:

| **Fase** | **Integrador de áudio e vídeo** | **Implementador do AEM** | **Estratégia comercial** | **Gerenciamento de conteúdo** |
|---|---|---|---|---|
| Solicitação e armazenamento de hardware | RA | I | I | I |
| Agendamento de integração de varejo | I | I | C | RA |
| Preparando Teste de Aceitação do Usuário | I | C | RA |   |
| Configuração de hardware em massa | RA | I | C | I |
| Contrato de suporte pós-lançamento | RA | C | RA | C |

A tabela a seguir resume o **Primeiro Dia: Primeiro Dia: Implementação de Projeto (Hardware)**:

| **Fase** | **Integrador de áudio e vídeo** | **Implementador do AEM** | **Estratégia comercial** | **Gerenciamento de conteúdo** |
|---|---|---|---|---|
| Acordo sobre Funções e Responsabilidades | RA | RA | RA | RA |
| O projeto de varejo inclui operações de fiação | - | - | - | - |
| Seleção do hardware do player | RAC | - | - | - |
| Gerenciamento de dispositivos do principal | RA | I | - | - |
| Ordenação, armazenamento e configuração do dispositivo | RA | IC | I | - |
| Definição do processo de suporte | RA | I | RA | C |

>[!NOTE]
>
>As funções são alteradas durante o segundo dia (suporte pós-inicialização).

* **Autor**: Gerenciamento de Conteúdo + Estratégia

* **Desenvolvedor**: normalmente é um membro da equipe de implementação do AEM Screens ou é transferido para uma equipe interna de desenvolvimento

* **Técnico**: contratado pelo Integrador de Áudio-Vídeo ou faz parte da mesma empresa.

A tabela a seguir resume o **Gráfico RACI de Suporte de Pós-Inicialização**:

| **Fase** | **Autor** | **Desenvolvedor** | **Técnico** |
|---|---|---|---|
| *Segundo Dia: Suporte Pós-Inicialização* |
| Acordo sobre Funções e Responsabilidades | RA | RA | RA |
| Suporte de nível 1 | I | I | RA |
| Suporte de nível 2 | I | C | RA |
| Suporte de nível 3 | I | RA | C |
| Atualização de conteúdo | RA | I | I |
| Avaliar o sucesso do UX e identificar áreas de aprimoramento | RA | C | I |
