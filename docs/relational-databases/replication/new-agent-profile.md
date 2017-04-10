---
title: "Создать профиль агента | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.rep.profiles.newperfprofile.f1"
helpviewer_keywords: 
  - "диалоговое окно «Создать профиль агента»"
ms.assetid: ebf59330-a421-45a5-9020-0484a96852bc
caps.latest.revision: 21
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 21
---
# Создать профиль агента
  Диалоговое окно **Создать профиль агента** позволяет создать новый профиль. Новые профили всегда основываются на существующих, но их можно изменить для соответствия требованиям приложения. После создания профиля его можно применить к текущим и будущим заданиям агента в диалоговом окне **Профили агента** . Можно изменить значения параметров агента в \<**AgentProfileName > свойства** диалоговое окно.  
  
## Параметры  
 **Название**  
 Введите имя профиля.  
  
 **Описание**  
 Введите описание профиля.  
  
 **Параметр**  
 Параметры агента, включенные в профиль. Профиль, на котором основан новый профиль, не обязательно указывает значения всех параметров. Для просмотра всех допустимых для данного агента параметров снимите флажок **Показывать только параметры, используемые в этом профиле** . Описание каждого параметра см. в разделах:  
  
-   [Агент моментальных снимков репликации](../../relational-databases/replication/agents/replication-snapshot-agent.md)  
  
-   [Агент чтения журнала репликации](../../relational-databases/replication/agents/replication-log-reader-agent.md)  
  
-   [Агент распространения репликации](../../relational-databases/replication/agents/replication-distribution-agent.md)  
  
-   [Агент слияния репликации](../../relational-databases/replication/agents/replication-merge-agent.md)  
  
-   [Агент чтения очереди репликации](../../relational-databases/replication/agents/replication-queue-reader-agent.md)  
  
 **Значение по умолчанию**  
 Значение по умолчанию для каждого параметра агента.  
  
 **Значение**  
 Значение, указанное для параметра в профиле, на котором основан новый профиль. Измените это поле, чтобы внести изменения в значения параметров.  
  
 **Показывать только параметры, используемые в этом профиле**  
 Снимите флажок, чтобы отобразить все корректные параметры для данного агента.  
  
## См. также:  
 [Работа с профилями агента репликации](../../relational-databases/replication/agents/work-with-replication-agent-profiles.md)   
 [Обзор агентов репликации](../../relational-databases/replication/agents/replication-agents-overview.md)   
 [Профили агента репликации](../../relational-databases/replication/agents/replication-agent-profiles.md)  
  
  