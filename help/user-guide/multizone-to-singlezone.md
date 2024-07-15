---
title: Caso de uso de transições de MultiZone para SingleZone
description: Siga esta página para que você possa saber mais sobre o caso de uso de transições de MultiZone para SingleZone.
contentOwner: Jyotika Syal
feature: Authoring Screens
role: Developer, User
level: Intermediate
exl-id: 15632f31-1e92-40e5-b567-8705e27bdc93
source-git-commit: cdff56f0807f6d5fea4a4b1d545aecb1e80245bb
workflow-type: tm+mt
source-wordcount: '404'
ht-degree: 1%

---

# Transição de várias regiões para uma única região {#multizone-to-singlezone-use-case}

## Descrição do caso de uso {#use-case-description}

Esta seção descreve um exemplo de caso de uso que enfatiza como configurar um canal de layout de várias zonas que se alterna com um canal de layout de zona única. O canal multizona tem ativos de imagem/vídeo de sequenciamento e mostra como você pode configurar um projeto que se alterna de multizona para zona única e vice-versa.

### Pré-condições {#preconditions}

Antes de iniciar este caso de uso, verifique se você sabe como:

* **[Criar e Gerenciar Canais](managing-channels.md)**
* **[Criar e Gerenciar Locais](managing-locations.md)**
* **[Criar e Gerenciar Agendamentos](managing-schedules.md)**
* **[Registro do dispositivo](device-registration.md)**

### Atores principais {#primary-actors}

Autores de conteúdo

## Configuração do projeto {#setting-up-the-project}

Siga as etapas abaixo para configurar um projeto:

1. Crie um projeto do AEM Screens chamado **TakeoverLoop**, conforme mostrado abaixo.

   ![ativo](assets/mz-to-sz1.png)


1. **Criando um Canal do Screens de Várias Zonas**

   1. Clique na pasta **Canais**, clique em **Criar** na barra de ações e abra o assistente para que você possa criar um canal.
   1. Clique em **Canal de tela dividida em L à esquerda** no assistente e crie o canal intitulado como **MultiZoneLayout**.
   1. Adicione conteúdo ao canal. Arraste e solte os ativos em cada uma das zonas. O exemplo a seguir mostra um canal **MultiZoneLayout** composto por um vídeo, uma imagem e um banner de texto (em uma sequência incorporada), como mostrado abaixo.

   ![ativo](assets/mz-to-sz2.png)

   >[!NOTE]
   >
   >Para saber mais sobre como criar um layout de várias zonas no seu canal, consulte [Layout de várias zonas](multi-zone-layout-aem-screens.md).


1. Crie outro canal chamado **TakeoverChannel** para sua pasta **Channels**.

   ![ativo](assets/mz-to-sz3.png)

1. Clique em **Editar** na barra de ações para poder adicionar conteúdo a este canal. Adicione um componente **Canal** e um ativo de imagem que você deseja alternar para este canal, como mostrado na figura abaixo:

   ![ativo](assets/mz-to-sz4.png)

1. Abra as configurações do componente Canal e aponte-o para o canal **MultiZoneLayout** criado na *etapa 2*.

   ![ativo](assets/mz-to-sz5.png)

1. Defina a duração do campo **Sequência** para **10000 milissegundos**.

   ![ativo](assets/mz-to-sz6.png)

1. Da mesma forma, abra as configurações da Imagem (ativo adicionado) e defina sua duração do campo **Sequência** para **3000 milissegundos**.

   ![ativo](assets/mz-to-sz7.png)

## Verificação da visualização {#checking-the-preview}

Você pode exibir a saída desejada do reprodutor ou simplesmente selecionando **Visualizar** no editor.

A saída demonstra como um layout de várias zonas é reproduzido por *10000 milissegundos*. Em seguida, ele muda para um layout de zona única com duração de reprodução de *3000 milissegundos*. E finalmente, ele muda de volta para o layout multizona.

>[!VIDEO](https://video.tv.adobe.com/v/30366)

>[!NOTE]
>
>Você pode personalizar a transição de canal (do layout de várias zonas para uma única zona ou vice-versa), de acordo com suas necessidades.
