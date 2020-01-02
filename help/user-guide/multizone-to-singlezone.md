---
title: Caso de uso de transições de MultiZone para SingleZone
description: Siga esta página para saber mais sobre o caso de uso de MultiZone para SingleZone Transitions.
seo-description: Casos de uso de Transições de MultiZone para SingleZone.
contentOwner: Jyotika Syal
translation-type: tm+mt
source-git-commit: 6f770734941635a0cd404986c259022137355af3

---


# Transição de várias zonas para uma única zona {#multizone-to-singlezone-use-case}


## Descrição do caso de uso {#use-case-description}

Esta seção descreve um exemplo de caso de uso que enfatiza como configurar um canal de layout multizona que alterna com um canal de layout de zona única. O canal de várias zonas tem ativos de imagem/vídeo em sequência e mostra como você pode configurar projetos que alternam de várias zonas para uma única zona e vice-versa.

### Condições prévias {#preconditions}

Antes de iniciar este caso de uso, certifique-se de saber como:

* **[Criar e gerenciar canais](managing-channels.md)**
* **[Criar e gerenciar locais](managing-locations.md)**
* **[Criar e gerenciar programações](managing-schedules.md)**
* **[Registro do dispositivo](device-registration.md)**

### Principais intervenientes {#primary-actors}

Autores de conteúdo

## Configuração do projeto {#setting-up-the-project}

Siga as etapas abaixo para configurar um projeto:

1. Crie um projeto do AEM Screens chamado de **TakeoverLoop**, conforme mostrado abaixo.

   ![ativo](assets/mz-to-sz1.png)


1. **Criando um canal de telas de várias zonas**

   1. Selecione a pasta **Canais** e clique em **Criar** na barra de ações para abrir o assistente para criar um canal.
   1. Selecione Canal **de tela dividida da barra** esquerda L no assistente e crie o canal chamado **MultiZoneLayout**.
   1. Adicione conteúdo ao canal. Arraste e solte os ativos em cada uma das zonas. O exemplo a seguir mostra um canal **MultiZoneLayout** composto de um vídeo, uma imagem e um banner de texto (em uma sequência incorporada), como mostrado abaixo.
   ![ativo](assets/mz-to-sz2.png)

   >[!NOTE]
   >
   >Para saber mais sobre como criar um layout de várias zonas no seu canal, consulte Layout [de](multi-zone-layout-aem-screens.md)várias zonas.


1. Crie outro canal chamado **TakeoverChannel** para a pasta **Canais** .

   ![ativo](assets/mz-to-sz3.png)

1. Clique em **Editar** na barra de ações para adicionar conteúdo a este canal. Adicione um componente de **Canal** e um ativo de imagem para o qual você deseja alternar, a este canal, conforme mostrado na figura abaixo:

   ![ativo](assets/mz-to-sz4.png)

1. Abra as configurações do componente Canal e aponte-o para o canal **MultiZoneLayout** criado na *etapa 2*.

   ![ativo](assets/mz-to-sz5.png)

1. Defina a duração do campo **Sequência** como **10000 ms**.

   ![ativo](assets/mz-to-sz6.png)

1. Da mesma forma, abra as configurações para a Imagem (ativo adicionado) e defina sua duração do campo **Sequência** para **3000 ms**.

   ![ativo](assets/mz-to-sz7.png)

## Verificando a visualização {#checking-the-preview}

Você pode exibir a saída desejada do player ou apenas clicando em **Visualizar** no editor.

A saída demonstrará como um layout de várias zonas é reproduzido por *10000 ms* e, em seguida, muda para um layout de zona única com duração de reprodução de *3000 ms* e, em seguida, volta para o layout de várias zonas.

>[!VIDEO](https://video.tv.adobe.com/v/30366)

>[!NOTE]
>
>Você pode personalizar sua transição de canal (de várias zonas para o layout de uma única zona ou vice-versa), conforme suas necessidades.