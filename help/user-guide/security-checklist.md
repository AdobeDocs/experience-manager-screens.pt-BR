---
title: Lista de verificação de segurança
description: Saiba mais sobre as principais áreas de segurança do AEM Screens com uma lista de verificação de perguntas e considerações.
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: 3d2835c8-d844-46fd-b35a-30feaced9dd8
source-git-commit: 2a51258ffe7b969962378dcd0558bd001b616ba1
workflow-type: tm+mt
source-wordcount: '479'
ht-degree: 0%

---

# Lista de verificação de segurança do AEM Screens {#security-checklist}

A página Lista de verificação de segurança do AEM Screens descreve as principais áreas de segurança com uma lista de verificação de perguntas e considerações.

## Tabela da lista de verificação {#checklist-table}

| **Área de Segurança** | **Lista de verificação** | **Sim/Não/NA** |
|---|---|---|
| **Atualizações do AEM e do Screens** | **a.** *O service pack mais recente do Adobe Experience Manager (AEM) foi aplicado?* <br>**b.** *O Pacote de Recursos mais recente do AEM Screens foi aplicado?* <br>**c.** *Você está usando o software AEM Screens Player mais recente disponível em [Downloads do AEM Screens Player](https://download.macromedia.com/screens/)?* |
| **Segurança Física** | **a.** *Você desabilitou todas as portas desnecessárias?* <br>**b.** *Você protegeu o cabeamento e o hardware?* <br>**c.** *Você está usando algum contêiner, se aplicável?* |
| **Segurança de rede** | **a.** *Você está usando uma sub-rede isolada para seus dispositivos de sinalização?* <br>**b.** *A sub-rede isolada permite acesso aos pontos de extremidade necessários, incluindo AEM, Adobe Analytics ou outros serviços necessários?* <br>**c.** *Você protegeu seu Wi-Fi usando as práticas recomendadas da empresa?* <br>**d.** *Se estiver usando reprodução sincronizada, você permitiu o TCP 24503 para WebSocket somente nos dispositivos primários?* <br>**e.** *Você desbloqueou o intervalo de endereços IP dos dispositivos de reprodução para que somente dispositivos autorizados possam acessar o serviço de registro na instância de criação?* |
| **Segurança do Sistema Operacional** | **a.** *Você atualizou para a versão mais recente do sistema operacional e aplicou todos os patches de segurança necessários?* <br>**b.** *Você desabilitou todos os serviços desnecessários e removeu aplicativos desnecessários?* <br>**c.** *Você inscreveu o dispositivo no gerenciamento de dispositivos para aplicar políticas corporativas?* <br>**d.** *Você bloqueou o dispositivo para um único quiosque de aplicativos (player)?* <br>**e.** *Você tem um SOP (Standard Operating Procedures) em vigor para instalar atualizações de segurança de SO ao longo do tempo?*<br>**f.***Você seguiu as práticas recomendadas de segurança para o sistema operacional em uso, como software antimalware e usuário não administrativo?* |
| **Segurança de aplicativos** | **a.** *Você desabilitou a IU do Administrador, o Alternador de Canais e a IU da Atividade para produção?* <br>**b.** *Você minimizou o nível de log para produção?* <br>**c.** *Você está usando https para se conectar ao AEM?* <br>**d.** *Você está usando um certificado assinado pela CA ou um PKI corporativo? (certificados não autoassinados)*<br>**e.***Você está usando TLS e não SSL v3?*<br>**f.** *Você está validando o token de registro no dispositivo e o AEM durante o registro?*<br> **g.** *Você classificou os dados que estão sendo usados e que não há PII ou PHI no dispositivo?*<br> **h.** *Você classificou os dados que estão sendo usados e que não existem informações pessoais identificáveis (PII) ou informações de saúde protegidas (PHI) no dispositivo?*<br> **i.** *Você configurou o monitoramento de Emails? Você tem um SOP em vigor para responder ao monitoramento de emails e manipulação de dispositivos sem ping?* |
| **Controle de acesso** | **a.** *Você tem um RBAC (controle de acesso com base em função) identificado e gerenciado internamente?* <br>**b.** *Você seguiu o princípio do privilégio mínimo ao fornecer acesso a autores, administradores e jogadores usando as práticas recomendadas do Adobe?* |

### Fazendo download da lista de verificação de segurança {#download-checklist}

Para baixar a lista de verificação de segurança do AEM Screens, clique [aqui](/help/user-guide/assets/AEMScreens-SecurityChecklist.pdf).
