---
title: Caso de uso de transições de MultiZone para SingleZone
description: Siga esta página para saber mais sobre o caso de uso de Transições de MultiZone para SingleZone.
seo-description: MultiZone to SingleZone Transitions use case.
contentOwner: Jyotika Syal
feature: Authoring Screens
role: Developer, User
level: Intermediate
exl-id: 15632f31-1e92-40e5-b567-8705e27bdc93
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '395'
ht-degree: 3%

---

# Transição de várias regiões para uma única região {#multizone-to-singlezone-use-case}


## Descrição do caso de uso {#use-case-description}

Esta seção descreve um exemplo de caso de uso que enfatiza como configurar um canal de layout de várias zonas que se alterna com um canal de layout de uma única zona. O canal de várias zonas tem ativos de imagem/vídeo de sequenciamento e mostra como você pode configurar projetos que se alternam de várias zonas para uma única zona e vice-versa.

### Pré-condições {#preconditions}

Antes de iniciar este caso de uso, verifique se você sabe como:

* **[Criar e gerenciar canais](managing-channels.md)**
* **[Criar e Gerenciar Locais](managing-locations.md)**
* **[Criar e gerenciar cronogramas](managing-schedules.md)**
* **[Registro do dispositivo](device-registration.md)**

### Atores principais {#primary-actors}

Autores de conteúdo

## Configuração do projeto {#setting-up-the-project}

Siga as etapas abaixo para configurar um projeto:

1. Crie um projeto do AEM Screens chamado como **LoopTomada**, conforme mostrado abaixo.

   ![ativo](assets/mz-to-sz1.png)


1. **Criação de um canal de telas de várias zonas**

   1. Selecione o **Canais** e clique em **Criar** na barra de ações para abrir o assistente e criar um canal.
   1. Selecionar **Canal de tela dividida em barra à esquerda** do assistente e crie o canal chamado de **MultiZoneLayout**.
   1. Adicione conteúdo ao canal. Arraste e solte os ativos em cada uma das zonas. O exemplo a seguir mostra uma **MultiZoneLayout** canal composto por um vídeo, uma imagem e um banner de texto (em uma sequência incorporada), conforme mostrado abaixo.

   ![ativo](assets/mz-to-sz2.png)

   >[!NOTE]
   >
   >Para saber mais sobre como criar um layout de várias zonas no seu canal, consulte [Layout de várias zonas](multi-zone-layout-aem-screens.md).


1. Crie outro canal chamado como **Canal de aquisição** ao seu **Canais** pasta.

   ![ativo](assets/mz-to-sz3.png)

1. Clique em **Editar** na barra de ações para adicionar conteúdo a este canal. Adicionar um **Canal** e um ativo de imagem para o qual você deseja alternar, para esse canal, como mostrado na figura abaixo:

   ![ativo](assets/mz-to-sz4.png)

1. Abra as configurações do componente Canal e aponte para **MultiZoneLayout** canal que você criou em *etapa 2*.

   ![ativo](assets/mz-to-sz5.png)

1. Defina a duração a partir de **Sequência** campo para **10000 ms**.

   ![ativo](assets/mz-to-sz6.png)

1. Da mesma forma, abra as configurações para a Imagem (ativo adicionado) e defina sua duração no **Sequência** campo para **3000 ms**.

   ![ativo](assets/mz-to-sz7.png)

## Verificação da visualização {#checking-the-preview}

Você pode visualizar a saída desejada do reprodutor ou apenas clicando no ícone **Visualizar** do editor.

A saída demonstrará como um layout de várias zonas é reproduzido para *10000 ms* e alterna para o layout de zona única com duração de reprodução de *3000 ms* e, em seguida, volta para o layout multizona.

>[!VIDEO](https://video.tv.adobe.com/v/30366)

>[!NOTE]
>
>Você pode personalizar a transição de canal (do layout de várias zonas para uma única zona ou vice-versa), de acordo com seus requisitos.
