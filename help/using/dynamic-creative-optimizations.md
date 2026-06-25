---
title: Data Triggers
description: Saiba mais sobre acionadores de dados na AEM Screens.
exl-id: 23c4268e-48be-4c84-b5eb-c96152b166f7
TQID: https://experienceleague.adobe.com/oeJ7C6Rt8-Z9sFnEP1S1tn0VW4PuiKkXkeDYaz8Vd4s
product_v2:
  - id: a27b4747-2f72-4fb7-9936-be5d11dd2c4a
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2:
  - id: eb3ad9f8-54a2-45f3-abb1-d3976415a718
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
topic_v2:
  - id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
source-git-commit: d4664dd5678eaccabe656398c437dca264d4675e
workflow-type: tm+mt
source-wordcount: 307
ht-degree: 0%

---

# Otimizações dinâmicas do Creative {#dynamic-creative}

>[!IMPORTANT]
>Esse conteúdo é válido para o AEM no local/AMS (AEM 6.5LTS e AEM 6.5). Para ver o conteúdo do AEM as a Cloud Service Screens, consulte o [guia do AEM as a Cloud Service](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/screens-as-cloud-service/overview/introduction).

>[!NOTE]
>
>Uma parte interessada típica dessa atividade é um Implementador do AEM.

O **Dynamic Creative Optimization**, ou DCO, é usado para criar experiências de sinalização digital que refletem as circunstâncias exclusivas de qualquer local em um determinado momento e para qualquer usuário.

Esse uso também é conhecido como nivelamento de conteúdo no lado do cliente.

O raciocínio é garantir que cada dispositivo de reprodução ou ponto final possa usar conjuntos de dados para determinar o melhor conteúdo a ser reproduzido automaticamente com base em vários fatores diferentes.

Essa funcionalidade elimina a necessidade de intervenção humana constante durante a criação de conteúdo. Também ajuda a reduzir o custo total de propriedade para operar a rede e torna as experiências digitais mais relevantes, mais contextuais e mais eficazes.

Por exemplo:

* usando o nível de inventário atual dos produtos de recursos
* temperatura exterior ou tempo
* a presença de uma campanha publicitária em mídia local
* tráfego da web e até eventos locais, como quando um cliente pega um produto para examiná-lo

Todos esses exemplos e muito mais podem ser usados para fornecer um nível mais alto de contexto e personalização.

Ter uma estratégia de merchandising visual que inclui DCO pode aumentar drasticamente a audiência na rede.

Há dois tipos principais de acionadores de dados:

* **Acionadores de Dados Locais**: esses acionadores de dados são locais no dispositivo. Por exemplo, se você tocou a tela, é ativado um sensor que aciona um ativo de dados local ou um switch de canal.
* **Acionadores de Dados Remotos**: envolviam uma troca de canal ou uma troca de ativo acionada por dados com base em valores retornados por uma API de Serviço Web.
