---
title: Lista de verificação de segurança do AEM Screens
seo-title: Security Checklist for AEM Screens
description: A página descreve a Lista de verificação de segurança do AEM Screens
seo-description: The page describes Security Checklist for AEM Screens
source-git-commit: 54c5a2f2f3f755e4da4028d54042f4bd8f2df369
workflow-type: tm+mt
source-wordcount: '460'
ht-degree: 1%

---


# Considerações sobre a segurança do sistema para o AEM Screens {#security-checklist}

>[!IMPORTANT]
>Este é um recurso interno do Git.

Esta página destaca as Considerações de segurança do sistema para o AEM Screens.


## Informe oficial de segurança da AEM Screens {#white-paper}

Esta seção descreve o white paper. (Anexo em white paper pendente)


## Perguntas frequentes sobre a segurança do AEM Screens {#faqs-screens}

As perguntas frequentes a seguir pressupõem uma arquitetura de player autenticada e registrada que usa HTTPS como o protocolo de comunicação entre o player e o servidor AEM.

### Perguntas frequentes 1 {#faq1}

O tráfego do player pode ser redirecionado para um servidor mal-intencionado e instruído a baixar e reproduzir conteúdo de mídia mal-intencionado?

**Resposta**

Não é possível porque a conexão HTTPs identifica ambas as extremidades da conexão e a criptografa. Se você tentar estar no meio e interceptá-lo, verá apenas conteúdo criptografado e se tentar representar o servidor, o reprodutor o recusará porque seu certificado é diferente.


### Perguntas frequentes 2 {#faq2}

Devo usar HTTP ou HTTPs?

**Resposta**

Use HTTPs. Isso é obrigatório se você estiver preocupado com a segurança. Com HTTPs, a comunicação é criptografada entre reprodutor e servidor, e interceptar o conteúdo ou modificá-lo será praticamente impossível.


### Perguntas frequentes 3 {#faq3}

Em um download de conteúdo, há algum tipo de assinatura do conteúdo ou hash?

**Resposta**

Cada ativo é assinado (SHA) pelo servidor e depois validado pelo reprodutor para o mesmo hash para garantir a integridade.
Se o hash não corresponder, tentamos revalidar 3 vezes. Após 3 tentativas, consideramos o comando de download inválido.


### Perguntas frequentes 4 {#faq4}

O servidor AEM é seguro?

**Resposta**

Ans 4 Supondo que você esteja no AMS, cuidaremos de toda a segurança do servidor usando os mesmos recursos do Sites ou do Assets.


### Perguntas frequentes 5 {#faq5}

O dispositivo está seguro?

**Resposta**

Um player fisicamente comprometido pode teoricamente ser manipulado para reproduzir qualquer conteúdo. Você também pode simplesmente conectar o reprodutor e conectar um pen drive USB/HDMI.

Portanto, é recomendável colocar os dispositivos fora de alcance, de preferência em um contêiner seguro, com o cabeamento também preso. Desative também as portas remotas IR.

Se o SO do dispositivo não for atualizado regularmente, o SO pode ser deixado exposto a brechas de segurança e permitir ataques remotos pela rede.

>[!NOTE]
>
>É recomendável instrumentar os dispositivos com recursos adequados de atualização e controle remotos (desktop remoto, solução MDM etc.). Também é recomendável usar uma rede privada, não exposta ao WIFI público, por exemplo.


### Perguntas frequentes 6 {#faq6}

Como um hacker tentaria comprometer um jogador?

**Resposta**

A única maneira de comprometer um dispositivo de reprodução é:

1. comprometer o DNS a representar o servidor em seu nome de host e,
1. compromisso
   1. o lado do servidor do certificado para representar o servidor
   1. dispositivo e representar o certificado do lado do cliente

>[!IMPORTANT]
>Mesmo que um dispositivo esteja comprometido, você ainda poderá revogar facilmente suas credenciais para que ele não possa mais se conectar ao AEM.





