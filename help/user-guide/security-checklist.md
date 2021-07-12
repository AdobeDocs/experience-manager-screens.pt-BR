---
title: Lista de verificação de segurança
seo-title: Lista de verificação de segurança
description: A página descreve as principais áreas de segurança com uma lista de verificação de perguntas e considerações.
seo-description: A página descreve a Lista de verificação de segurança
feature: Administração do Screens
role: Admin
level: Intermediate
exl-id: 3d2835c8-d844-46fd-b35a-30feaced9dd8
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '488'
ht-degree: 0%

---

# Lista de verificação de segurança do AEM Screens  {#security-checklist}

A página Lista de verificação de segurança do AEM Screens descreve as principais áreas de segurança com uma lista de verificação de perguntas e considerações.

## Tabela da lista de verificação {#checklist-table}

| **Área de segurança** | **Lista de verificação** | **Sim/Não/Não** |
|---|---|---|
| **Atualizações de software do AEM e do Screens** | ***a.*** *O service pack Adobe Experience Manager (AEM) mais recente foi aplicado?* <br>***b.***  *O Pacote de recursos AEM Screens mais recente foi aplicado?* <br>***c.*** *Você está usando o software AEM Screens Player mais recente disponível nos Downloads do  [AEM Screens Player](https://download.macromedia.com/screens/)?* |
| **Segurança física** | ***a.*** *Desabilitou todas as portas desnecessárias?* <br>***b.***  *Você prendeu cabos e hardware?* <br>***c.*** *Você está usando algum contêiner, se aplicável?* |
| **Segurança de rede** | ***a.*** *Você está usando uma sub-rede isolada para seus dispositivos de assinatura?* <br>***b.***  *A sub-rede isolada permite acesso aos endpoints necessários, incluindo AEM, Adobe Analytics ou outros serviços necessários?* <br>***c.*** *Você protegeu seu Wi-Fi usando as práticas recomendadas da empresa?* <br>***d.*** *Se estiver usando a reprodução sincronizada, você permitiu o TCP 24503 para WebSocket somente nos dispositivos principais?* <br>***e.*** *Você desbloqueou o intervalo de endereços IP dos dispositivos do reprodutor para que somente os dispositivos autorizados possam acessar o serviço de registro no autor?* |
| **Segurança do sistema operacional** | ***a.*** *Você atualizou para a versão mais recente do sistema operacional e aplicou todos os patches de segurança necessários?* <br>***b.*** *Desabilitou todos os serviços desnecessários e removeu aplicativos desnecessários?* <br>***c.*** *Você inscreveu o dispositivo no gerenciamento de dispositivos para aplicar políticas corporativas?* <br>***d.*** *Você bloqueou o dispositivo para um único quiosque de aplicativo (reprodutor)?* <br>***e.*** *Você tem um SOP (Standard Operating Procedures, procedimentos operacionais padrão) em vigor para instalar atualizações de segurança do SO ao longo do tempo?*<br>***f.*** *Você seguiu as práticas recomendadas de segurança para o sistema operacional em uso, como software antimalware, usuário não administrativo?* |
| **Segurança de aplicativos** | ***a.*** *Você desabilitou a interface do usuário do administrador, o Seletor de canal e a interface do usuário da atividade para produção?* <br>***b.*** *Você minimizou o nível de log para produção?* <br>***c.*** *Você está usando https para se conectar ao AEM?* <br>***d.*** *Você está usando um certificado assinado pela CA ou um PKI corporativo? (não certificados autoassinados)*<br>***e.*** *Você está usando TLS e não SSL v3?*<br>***f.*** *Você está validando o token de registro no dispositivo e AEM ao se registrar?*<br> ***g.*** *Você classificou os dados que estão sendo usados e que nenhuma PII ou PHI existe no dispositivo?*<br> ***h.*** *Você classificou os dados que estão sendo usados e que nenhuma informação de identificação pessoal (PII) ou informação de saúde protegida (PHI) existe no dispositivo?*<br> ***i.*** *Você configurou o monitoramento de e-mails e possui um SOP em vigor para responder ao monitoramento de e-mails e ao tratamento de dispositivos que não são ping?* |
| **Controle de acesso** | ***a.*** *Você tem um Controle de Acesso Baseado em Função (RBAC) identificado e gerenciado internamente?* <br>***b.*** *Você seguiu o princípio do menor privilégio ao fornecer acesso a autores, administradores e players usando práticas recomendadas do Adobe?* |

### Download da lista de verificação de segurança {#download-checklist}

Para baixar a lista de verificação de segurança do AEM Screens, clique [aqui](/help/user-guide/assets/AEMScreens-SecurityChecklist.pdf).
