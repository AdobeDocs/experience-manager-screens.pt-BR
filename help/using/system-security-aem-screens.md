---
title: Lista de verificação de segurança do AEM Screens
description: Saiba mais sobre a lista de verificação de segurança do AEM Screens.
source-git-commit: 873e6ff8b506416bce8660f5eb2cbea75227a9c8
workflow-type: tm+mt
source-wordcount: '460'
ht-degree: 0%

---


# Considerações sobre a segurança do sistema para o AEM Screens {#security-checklist}

>[!IMPORTANT]
>Um recurso interno do Git.

Esta página destaca as Considerações de segurança do sistema para o AEM Screens.


## Informe oficial de segurança da AEM Screens {#white-paper}

Esta seção descreve o white paper. (Anexo em white paper pendente)


## Perguntas frequentes sobre a segurança do AEM Screens {#faqs-screens}

As perguntas frequentes a seguir pressupõem uma arquitetura de player autenticada e registrada. Ele usa HTTPS como o protocolo de comunicação entre o reprodutor e o servidor AEM.

### Perguntas frequentes 1 {#faq1}

O tráfego do player pode ser redirecionado para um servidor mal-intencionado e instruído a baixar e reproduzir conteúdo de mídia mal-intencionado?

**Resposta**

Não é possível porque a conexão HTTPs identifica ambas as extremidades da conexão e a criptografa. Se você tentar estar no meio e interceptá-lo, verá somente o conteúdo criptografado. Se você tentar representar o servidor, o reprodutor o recusará porque o certificado é diferente.


### Perguntas frequentes 2 {#faq2}

Devo usar HTTP ou HTTPs?

**Resposta**

Use HTTPs. Esse protocolo é obrigatório se você estiver preocupado com a segurança. Com HTTPs, a comunicação é criptografada entre o reprodutor e o servidor, e é impossível interceptar ou modificar o conteúdo.


### Perguntas frequentes 3 {#faq3}

Em um download de conteúdo, há algum tipo de assinatura do conteúdo ou hash?

**Resposta**

Todos os ativos são assinados (SHA) pelo servidor. O reprodutor o valida para o mesmo hash a fim de garantir a integridade.
Se o hash não corresponder, o software tentará revalidar três vezes. Após três tentativas, o comando de download é considerado inválido.


### Perguntas frequentes 4 {#faq4}

O servidor AEM é seguro?

**Resposta**

Supondo que você esteja no AMS, o software cuida de toda a segurança do servidor usando os mesmos recursos do Sites ou do Assets.


### Perguntas frequentes 5 {#faq5}

O dispositivo está seguro?

**Resposta**

Um player fisicamente comprometido pode teoricamente ser manipulado para reproduzir qualquer conteúdo. Você também pode desconectar o player e conectar um pen drive USB/HDMI.

Coloque os dispositivos fora de alcance, de preferência em um contêiner seguro, com o cabeamento preso também. Desative também as portas remotas IR.

Se o SO do dispositivo não for atualizado regularmente, o SO pode ficar exposto a brechas de segurança e permitir ataques remotos pela rede.

>[!NOTE]
>
>É recomendável equipar os dispositivos com recursos adequados de atualização e controle remoto (desktop remoto, solução MDM e assim por diante). Também é recomendável usar uma rede privada, não exposta ao WIFI público, por exemplo.


### Perguntas frequentes 6 {#faq6}

Como um hacker tentaria comprometer um jogador?

**Resposta**

A única maneira de comprometer um dispositivo de reprodução é:

1. comprometer o DNS a representar o servidor nesse nome de host e,
1. compromisso
   1. o lado do servidor do certificado para representar o servidor
   1. dispositivo e representar o certificado do lado do cliente

>[!IMPORTANT]
>Mesmo que um dispositivo esteja comprometido, você ainda poderá revogar facilmente suas credenciais para que ele não possa mais se conectar ao AEM.





