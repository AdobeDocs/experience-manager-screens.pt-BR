---
title: Caso de uso de transições de várias zonas para uma única zona
description: Siga esta página para saber mais sobre o caso de uso de Transições de várias zonas para uma única zona.
seo-description: Caso de uso de Transições de MultiZone para SingleZone.
contentOwner: Jyotika Syal
feature: Authoring Screens
role: Developer, Business Practitioner
level: Intermediate
translation-type: tm+mt
source-git-commit: 89c70e64ce1409888800af7c7edfbf92ab4b2c68
workflow-type: tm+mt
source-wordcount: '407'
ht-degree: 3%

---


# Transição de várias zonas para uma única zona {#multizone-to-singlezone-use-case}


## Descrição do caso de uso {#use-case-description}

Esta seção descreve um exemplo de caso de uso que enfatiza como configurar um canal de layout de várias zonas que alterne com um canal de layout de uma única zona. O canal de várias zonas tem ativos de imagem/vídeo em sequência e mostra como você pode configurar projetos que alternam de várias zonas para uma única zona e vice-versa.

### Pré-condições {#preconditions}

Antes de iniciar este caso de uso, certifique-se de entender como:

* **[Criar e gerenciar canais](managing-channels.md)**
* **[Criar e gerenciar locais](managing-locations.md)**
* **[Criar e gerenciar agendamentos](managing-schedules.md)**
* **[Registro do dispositivo](device-registration.md)**

### Atores Primários {#primary-actors}

Autores de conteúdo

## Configurando o projeto {#setting-up-the-project}

Siga as etapas abaixo para configurar um projeto:

1. Crie um Projeto do AEM Screens chamado como **TakeoverLoop**, conforme mostrado abaixo.

   ![ativo](assets/mz-to-sz1.png)


1. **Criação de um canal de telas de várias zonas**

   1. Selecione a pasta **Channels** e clique em **Create** na barra de ações para abrir o assistente para criar um canal.
   1. Selecione **Canal de tela dividida da barra esquerda** no assistente e crie o canal chamado de **MultiZoneLayout**.
   1. Adicione conteúdo ao canal. Arraste e solte os ativos em cada uma das zonas. O exemplo a seguir mostra um canal **MultiZoneLayout** composto por um vídeo, uma imagem e um banner de texto (em uma sequência incorporada), conforme mostrado abaixo.

   ![ativo](assets/mz-to-sz2.png)

   >[!NOTE]
   >
   >Para saber mais sobre como criar um layout de várias zonas no seu canal, consulte [Layout de várias zonas](multi-zone-layout-aem-screens.md).


1. Crie outro canal chamado **TakeoverChannel** para sua pasta **Channels**.

   ![ativo](assets/mz-to-sz3.png)

1. Clique em **Editar** na barra de ações para adicionar conteúdo a este canal. Adicione um componente **Canal** e um ativo de imagem para o qual você deseja alternar, a este canal, conforme mostrado na figura abaixo:

   ![ativo](assets/mz-to-sz4.png)

1. Abra as configurações do componente Canal e aponte-o para o canal **MultiZoneLayout** criado em *etapa 2*.

   ![ativo](assets/mz-to-sz5.png)

1. Defina a duração do campo **Sequence** para **10000 ms**.

   ![ativo](assets/mz-to-sz6.png)

1. Da mesma forma, abra as configurações da Imagem (ativo adicionado) e defina sua duração do campo **Sequence** para **3000 ms**.

   ![ativo](assets/mz-to-sz7.png)

## Verificando a Visualização {#checking-the-preview}

Você pode exibir o resultado desejado do reprodutor ou apenas clicando em **Preview** no editor.

A saída demonstrará como um layout de várias zonas é reproduzido para *10000 ms* e, em seguida, alterna para o layout de uma única zona com duração de reprodução de *3000 ms* e, em seguida, alterna de volta para o layout de várias zonas.

>[!VIDEO](https://video.tv.adobe.com/v/30366)

>[!NOTE]
>
>Você pode personalizar a transição do canal (de várias zonas para o layout de uma única zona ou vice-versa), de acordo com suas necessidades.