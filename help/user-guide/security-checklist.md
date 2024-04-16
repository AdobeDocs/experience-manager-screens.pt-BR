---
title: Lista de verificação de segurança
description: Saiba mais sobre as principais áreas de segurança do AEM Screens com uma lista de verificação de perguntas e considerações.
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: 3d2835c8-d844-46fd-b35a-30feaced9dd8
source-git-commit: fff2df02661fc3fb3098be40e090b8bc6925bcc2
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 0%

---

# Lista de verificação de segurança do AEM Screens  {#security-checklist}

A página Lista de verificação de segurança do AEM Screens descreve as principais áreas de segurança com uma lista de verificação de perguntas e considerações.

## Tabela da lista de verificação {#checklist-table}

| **Área de Segurança** | **Lista de verificação** | **Sim/Não/ND** |
|---|---|---|
| **Atualizações de software do AEM e do Screens** | **a)** *O service pack mais recente do Adobe Experience Manager (AEM) foi aplicado?* <br>**b)** *O Pacote de recursos mais recente do AEM Screens foi aplicado?* <br>**c)** *Você está usando o software AEM Screens Player mais recente disponível na [Downloads do AEM Screens Player](https://download.macromedia.com/screens/)?* |
| **Segurança física** | **a)** *Você desativou todas as portas desnecessárias?* <br>**b)** *Você tem cabeamento e hardware seguros?* <br>**c)** *Você está usando algum contêiner, se aplicável?* |
| **Segurança de rede** | **a)** *Você está usando uma sub-rede isolada para seus dispositivos de sinalização?* <br>**b)** *A sub-rede isolada permite acesso aos endpoints necessários, incluindo AEM, Adobe Analytics ou outros serviços necessários?* <br>**c)** *Você protegeu seu Wi-Fi usando as práticas recomendadas da empresa?* <br>**d)** *Se estiver usando reprodução sincronizada, você permitiu o TCP 24503 para WebSocket somente nos dispositivos primários?* <br>**e.** *Você desbloqueou o intervalo de endereços IP dos dispositivos de reprodução para que somente dispositivos autorizados possam acessar o serviço de registro na instância de criação?* |
| **Segurança do sistema operacional** | **a)** *Você atualizou para a versão mais recente do sistema operacional e aplicou todos os patches de segurança necessários?* <br>**b)** *Você desativou todos os serviços desnecessários e removeu aplicativos desnecessários?* <br>**c)** *Você inscreveu o dispositivo no gerenciamento de dispositivos para aplicar as políticas corporativas?* <br>**d)** *Você bloqueou o dispositivo para um único quiosque de aplicativo (player)?* <br>**e.** *Você possui um Procedimento Operacional Padrão (SOP) em vigor para instalar atualizações de segurança do SO ao longo do tempo?*<br>**f)***Você seguiu as práticas recomendadas de segurança para o sistema operacional em uso, como software antimalware e usuário não administrativo?* |
| **Segurança de aplicativos** | **a)** *Você desativou a interface do administrador, o alternador de canal e a interface de atividade para produção?* <br>**b)** *Você minimizou o nível de log para produção?* <br>**c)** *Você está usando https para se conectar ao AEM?* <br>**d)** *Você está usando um certificado assinado pela CA ou uma PKI corporativa? (certificados não autoassinados)*<br>**e.***Você está usando TLS e não SSL v3?*<br>**f)** *Você está validando o token de registro no dispositivo e no AEM durante o registro?*<br> **g)** *Você classificou os dados que estão sendo usados e que não há PII ou PHI no dispositivo?*<br> **h)** *Você classificou os dados que estão sendo usados e que não há informações pessoais identificáveis (PII) ou informações de saúde protegidas (PHI) no dispositivo?*<br> **i)** *Você configurou o monitoramento de e-mails e possui um SOP em vigor para responder ao monitoramento de e-mails e lidar com dispositivos sem ping?* |
| **Controle de acesso** | **a)** *Você tem um controle de acesso baseado em função (RBAC) identificado e gerenciado internamente?* <br>**b)** *Você seguiu o princípio do menor privilégio ao fornecer acesso a autores, administradores e players usando as práticas recomendadas do Adobe?* |

### Fazendo download da lista de verificação de segurança {#download-checklist}

Para baixar a Lista de verificação de segurança do AEM Screens, clique em [aqui](/help/user-guide/assets/AEMScreens-SecurityChecklist.pdf).
