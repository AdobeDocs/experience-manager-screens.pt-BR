---
title: Abordagem recomendada
description: Saiba mais sobre a abordagem recomendada em um projeto do AEM Screens.
exl-id: 28aacffa-e9c9-4ccb-8038-720bb3e02a3f
TQID: https://experienceleague.adobe.com/r0WE0DQZx3dtGGlNaX9DUX3ckvu2ZdseJLy8-sDJZXQ
product_v2: id: a27b4747-2f72-4fb7-9936-be5d11dd2c4aid: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2: id: ae478996-b206-4712-9b0c-dc78a2644453id: f18e6c98-d21a-4444-b84b-f327ce464de4
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554
topic_v2: id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87cid: fc314d1d-7cb9-4a38-8dbd-8f9b6478f40d
source-git-commit: d4664dd5678eaccabe656398c437dca264d4675e
workflow-type: tm+mt
source-wordcount: 482
ht-degree: 0%

---

# Abordagem recomendada {#recommended-approach}

>[!IMPORTANT]
>Esse conteúdo é válido para o AEM no local/AMS (AEM 6.5LTS e AEM 6.5). Para ver o conteúdo do AEM as a Cloud Service Screens, consulte o [guia do AEM as a Cloud Service](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/screens-as-cloud-service/overview/introduction).

A prática recomendada é considerar qualquer projeto AEM Screens de nível empresarial como um empreendimento de longo prazo. É provável que o projeto tenha uma duração de um ou mais anos, especialmente se a solução permitir uma interação complexa do usuário ou for implantada em vários dispositivos e locais.

## Diretrizes para o desenvolvimento de uma estratégia de sinalização digital {#signage-strategy}

Consulte as poucas recomendações antes de desenvolver e implantar um projeto de sinalização digital:

* **Controle de Escopo**:
Se a solução desejada for ambiciosa, é recomendável dividir os resultados em fases distintas para controlar o escopo do projeto.

* **Casos de uso definidos**:
As fases do projeto devem fornecer casos de uso bem definidos com critérios de sucesso claramente identificados.

* **Entregas Incrementais**:
Concentre-se em fornecer recursos de forma incremental.

* **Estimando o resultado desejado**:
Comece com os recursos prontos para uso do AEM Screens antes de criar componentes e integrações personalizados. Sempre faça um brainstorming se o resultado desejado puder ser atingido usando os componentes e recursos que acompanham o AEM Screens por padrão.

* **Definindo pilotos, implantações e POCs**:
Desenvolva uma Prova de Conceito (POCs) e adapte-a conforme necessário por meio de um piloto e uma implantação.

* **Estratégia predefinindo conteúdo**:
Estabelecer uma estratégia de conteúdo, incluindo metas de curto e longo prazo. Além disso, alinhe as metas da marca/KPIs com as melhorias de recursos.

  >[!NOTE]
  >
  > Os custos iniciais geralmente são mais altos em um projeto AEM Screens devido à necessidade de investir em hardware, dispositivos fixos e designs de site. Portanto, manter as soluções de conteúdo inicial mais simples pode ajudar a gerenciar as expectativas de orçamento.

* **Estimativa de Entregas em Larga Escala**:
Se a solução for fornecida em grande escala, implante os componentes do aplicativo em locais piloto selecionados cuidadosamente para uso de avaliação. Enviar para novos locais e dispositivos à medida que o aplicativo passar na validação.

  >[!NOTE]
  >
  > Comece a coletar análises durante o piloto para que as equipes de negócios possam validar o sucesso da solução em relação às métricas específicas que estão tentando alcançar. Conhecer o desempenho do piloto ajuda a equipe de negócios a determinar as melhorias que devem ser feitas.

* **Dividindo Entregas em tarefas mensuráveis**:
Dividir a entrega de recursos em tarefas mensuráveis permite feedback, fornece metas mais alcançáveis e reduz os riscos gerais do projeto.

* **Desenvolvendo um roteiro**:
Se o seu cliente quiser um produto rico em recursos, forneça uma parte da funcionalidade planejada no início do projeto e programe outros recursos para as fases futuras. Um primeiro produto com muitos recursos traz mais riscos e é mais difícil de validar com o cliente.

* **Noções básicas sobre o escopo das integrações personalizadas**:
Componentes interativos com interação na tela de toque, sensor de movimento ou RFID exigem um desenvolvimento personalizado significativo no método de implementação. Uma apresentação de slides, anúncio de vídeo ou menu estático pode ser fornecido como conteúdo gráfico ou HTML em um canal do Screens.
