---
title: Lista de verificação de segurança para telas AEM
seo-title: Lista de verificação de segurança para telas AEM
description: A página descreve a Lista de verificação de segurança para o AEM Screens
seo-description: A página descreve a Lista de verificação de segurança para o AEM Screens
translation-type: tm+mt
source-git-commit: dd1198dbfb502287ae72c3ccef297606aef069a2
workflow-type: tm+mt
source-wordcount: '473'
ht-degree: 1%

---


# Considerações sobre segurança do sistema para o AEM Screens {#security-checklist}

>[!IMPORTANT]
>Este é um recurso interno do Git.

Esta página destaca as considerações de segurança do sistema para telas AEM.


## White paper for AEM Screens Security {#white-paper}

Esta seção descreve o white paper. (Anexo pendente do White Paper)


## Perguntas frequentes sobre segurança do AEM Screens {#faqs-screens}

As Perguntas frequentes a seguir pressupõem uma arquitetura de player autenticada e registrada usando HTTPS como protocolo de comunicação entre o player e o servidor AEM.

### Perguntas frequentes 1 {#faq1}

O tráfego do player pode ser redirecionado para um servidor mal-intencionado e instruído a baixar e reproduzir conteúdo de mídia mal-intencionado?

**Resposta**

Não é possível porque a conexão HTTPs identifica ambas as extremidades da conexão e a criptografa. Se você tentar ficar no meio e interceptá-lo, você verá somente o conteúdo criptografado e, se tentar representar o servidor, o player o recusará porque seu certificado é diferente.


### Perguntas frequentes 2 {#faq2}

Devo usar HTTP ou HTTPs?

**Resposta**

Use HTTPs. Isto é uma obrigação se você está preocupado com a segurança. Com HTTPs, a comunicação é criptografada entre o player e o servidor, e interceptar o conteúdo ou modificá-lo será praticamente impossível.


### Perguntas frequentes 3 {#faq3}

Em um download de conteúdo, há algum tipo de assinatura do conteúdo ou hash?

**Resposta**

Todos os ativos são assinados (SHA) pelo servidor e depois validados pelo player para o mesmo hash para garantir a integridade.
Se o hash não corresponder, tentamos revalidar 3 vezes. Após 3 tentativas, consideramos o comando download inválido.


### Perguntas frequentes 4 {#faq4}

O AEM Server é seguro?

**Resposta**

Ans 4. Supondo que você esteja no AMS, cuidaremos de toda a segurança do servidor usando os mesmos recursos que Sites ou Assets.


### Perguntas frequentes 5 {#faq5}

O dispositivo é seguro?

**Resposta**

Um player fisicamente comprometido pode, teoricamente, ser manipulado para reproduzir qualquer conteúdo. Você também poderia conectar o player e conectar um pente USB/HDMI.

Portanto, é recomendável colocar os dispositivos fora do alcance, de preferência em um container seguro, com cabeamento preso também. Desabilite também quaisquer portas IR-remotas.

Se o SO do dispositivo não for atualizado regularmente, o SO poderá ser deixado exposto a buracos de segurança e permitir ataques remotos na rede.
>[!NOTE]
>É recomendável instrumentar os dispositivos com recursos adequados de atualização e controle remotos (desktop remoto, solução MDM etc.). Também é recomendável usar uma rede privada, não exposta à WIFI pública, por exemplo.


### Perguntas frequentes 6 {#faq6}

Como um hacker tentaria comprometer um jogador?

**Resposta**

A única maneira de comprometer um dispositivo de player é:

1. comprometer o DNS para representar o servidor no nome do host, e
1. compromisso
   1. o lado do servidor de certificados para representar o servidor
   1. e representar o lado do cliente do certificado

>[!IMPORTANT]
>Mesmo se um dispositivo estiver comprometido, você ainda poderá revogar facilmente suas credenciais para que ele não possa mais se conectar ao AEM.





