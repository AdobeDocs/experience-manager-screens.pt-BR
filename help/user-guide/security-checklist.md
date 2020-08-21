---
title: Lista de verificação de segurança
seo-title: Lista de verificação de segurança
description: A página descreve a Lista de verificação de segurança
seo-description: A página descreve a Lista de verificação de segurança
translation-type: tm+mt
source-git-commit: ccc1baa0b57cb1311855065433aabf627814d16a
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 0%

---


# Lista de verificação de segurança do AEM Screens  {#security-checklist}

A página de Lista de verificação de segurança do AEM Screens descreve as principais áreas de segurança com uma lista de verificação de perguntas e considerações.

## Tabela da lista de verificação {#checklist-table}

| **Área de segurança** | **Lista de verificação** | **Sim/Não/NA** |
|---|---|---|
| **Atualizações de software do AEM e do Screens** | ***a.*** *O pacote de serviços mais recente do Adobe Experience Manager (AEM) foi aplicado?* <br>***b.*** *O AEM Screens Feature Pack mais recente foi aplicado?*<br>***c.*** *Você está usando o software AEM Screens Player mais recente disponível em Downloads[](https://download.macromedia.com/screens/)do AEM Screens Player?* |
| **Segurança física** | ***a.*** *Desabilitou todas as portas desnecessárias?* <br>***b.*** *Você tem cabos e hardware protegidos?*<br>***c.*** *Você está usando algum container, se aplicável?* |
| **Segurança de rede** | ***a.*** *Você está usando uma sub-rede isolada para seus dispositivos de sinalização?* <br>***b.*** *A sub-rede isolada permite acesso aos pontos de extremidade necessários, incluindo o AEM, o Adobe Analytics ou outros serviços necessários?*<br>***c.*** *Você protegeu seu Wi-Fi usando as práticas recomendadas da empresa?* <br>***d.*** *Se você estiver usando a reprodução sincronizada, terá permitido o TCP 24503 para WebSocket somente nos dispositivos mestre?*<br>***e.*** *Você desbloqueou o intervalo de endereços IP dos dispositivos do player para que somente os dispositivos autorizados possam acessar o serviço de registro no autor?* |
| **Segurança do sistema operacional** | ***a.*** *Você atualizou para a versão mais recente do sistema operacional e aplicou todas as correções de segurança necessárias?* <br>***b.*** *Desabilitou todos os serviços desnecessários e removeu aplicativos desnecessários?*<br>***c.*** *Você inscreveu o dispositivo no gerenciamento de dispositivos para aplicar políticas corporativas?* <br>***d.*** *Você bloqueou o dispositivo para quiosque de aplicativo único (player)?*<br>***e.*** *Você tem um SOP (Standard Operating Procedures, procedimento operacional padrão) em vigor para instalar atualizações de segurança do SO ao longo do tempo?*<br>***f.*** *Você seguiu as práticas recomendadas de segurança para o sistema operacional em uso, como software antimalware, usuário não administrativo?* |
| **Segurança de aplicativos** | ***a.*** *Desabilitou a interface do usuário do administrador, o Comutador de Canais e a interface do usuário da Atividade para produção?* <br>***b.*** *Você minimizou o nível de log para produção?*<br>***c.*** *Você está usando https para conexão com o AEM?* <br>***d.*** *Você está usando um certificado assinado pela CA ou um PKI corporativo? (não certificados autoassinados)*<br>***e.*** *Você está usando TLS e não SSL v3?*<br>***f.*** *Você está validando o token de registro no dispositivo e no AEM ao se registrar?*<br> ***g.*** *Você classificou os dados que estão sendo usados e que nenhuma PII ou PHI existe no dispositivo?*<br> ***h.*** *Você classificou os dados que estão sendo usados e que não há informações pessoais identificáveis (PII) ou informações de saúde protegida (PHI) no dispositivo?*<br> ***i.*** *Você configurou o monitoramento de e-mails e possui um SOP em vigor para responder a e-mails de monitoramento e dispositivos que não fazem ping?* |
| **Controle de acesso** | ***a.*** *Você tem um Controle de acesso baseado em função (RBAC) identificado e gerenciado internamente?* <br>***b.*** *Você seguiu o princípio do menor privilégio ao fornecer acesso a autores, administradores e players usando as práticas recomendadas da Adobe?* |

### Download da Lista de Verificação de Segurança {#download-checklist}

Para baixar a lista de verificação de segurança do AEM Screens, clique [aqui](/help/user-guide/assets/AEMScreens-SecurityChecklist.pdf).
