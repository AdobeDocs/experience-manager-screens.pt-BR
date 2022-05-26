---
title: Implementação do controle remoto
seo-title: Impementing the Remote Control
description: Siga esta página para saber mais sobre o recurso de controle remoto do Screens.
seo-description: Follow  this page to learn about using the Screens Remote Control Feature.
uuid: eee84286-fa81-475c-ad6f-db2d6cf1fed5
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
discoiquuid: 1be944f0-02ed-48c6-98bc-504d758ff866
feature: Administering Screens
role: Admin
level: Intermediate
source-git-commit: a256f624c4b647deb4cee7668665ad7b576932e7
workflow-type: tm+mt
source-wordcount: '354'
ht-degree: 0%

---

# Uso do controle remoto do Screens  {#implementing-remote-control}

O recurso de controle remoto facilita o acesso à interface do usuário do administrador, ao seletor de canal ou a recursos como Limpar cache e recarregar. Além disso, ele fornece um método para ver a versão do firmware local e as informações do sistema no player. Isso é especialmente útil porque pode ser difícil conectar um mouse e operar em dispositivos de produção que estão fora do alcance e ainda mais se o reprodutor tiver perdido a conexão com o AEM. Isso também é útil ao usar o RMS da Samsung, pois a diferença de resolução pode tornar muito difícil localizar e abrir a interface do usuário do administrador usando um mouse.

## Combinações Comuns De Teclas De Controle Remoto {#using-common-remote-control}

Em todos os players, você pode usar as seguintes combinações de teclas no Controle Remoto do Screens:

1. Alternar interface do administrador - CTRL + 1
1. Alternar seletor de canal - CTRL + 2
1. Limpar cache - CTRL + ALT + 3
1. Recarregar reprodutor - CTRL + 4

## Ajustar combinações específicas de teclas de controle remoto {#using-tizen-remote-control}

Específico para o Tizen player, você pode usar o controle remoto de hardware ou o software disponível no Samsung RMS para acessar esses recursos:

1. A - Alternar a interface do usuário do administrador
1. B - Alternar seletor de canal
1. C - Limpar cache
1. D - Recarregar reprodutor

## Observações adicionais de uso {#using-additional-remote-control}

1. Com a Interface do usuário do administrador aberta, você pode usar as setas para cima e para baixo para navegar pelas guias e exibir as informações nas guias.
1. Com o seletor de canal aberto, você pode usar as teclas das setas para cima e para baixo para navegar pelos canais e pode pressionar a tecla enter (ou o botão no centro das setas no controle remoto) para trocar de canal.

O diagrama a seguir ilustra o uso de chave em um controle remoto da Samsung:
![imagem](assets/tizen/remote.png)

>[!NOTE]
>Se você definir os valores de configuração do dispositivo de enableAdminUI e/ou enableOSD como false, o controle remoto não alternará a interface do usuário do administrador e o seletor de canal. Você também não poderá usar as teclas de seta para navegar na interface do usuário ou nos canais do administrador. No entanto, ainda é possível limpar o cache e recarregar o player. Você pode desativar o recurso de controle remoto se qualquer combinação de teclado entrar em conflito com seu conteúdo interativo usando este código:

```
require(['util/ScreensDisplay'], function() {window.ScreensDisplay.ignoreRemoteControl = true;}); 
```
