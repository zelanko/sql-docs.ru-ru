---
title: "Проверка руководств плана после обновления | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-plan-guides"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "структуры планов [SQL Server], проверка после обновления"
ms.assetid: a55ebd88-6f58-454d-b1c4-991b88add522
caps.latest.revision: 6
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 6
---
# Проверка руководств плана после обновления
  Рекомендуется переоценить и протестировать определения структур планов при обновлении приложения для работы с новым выпуском [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Требования к настройке производительности и поведение сопоставления структур планов могут меняться. Хотя недопустимая структура плана не приведет к сбою при выполнении запроса, план будет скомпилирован без использования структуры, что не рекомендуется. После обновления базы данных до версии [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] рекомендуется выполнить следующие действия.  
  
-   Проверьте существующие структуры планов с помощью функции [sys.fn_validate_plan_guide](../../relational-databases/system-functions/sys-fn-validate-plan-guide-transact-sql.md).  
  
-   Используйте расширенные события, чтобы проверить наличие планов без структуры за определенное время с помощью события [Plan Guide Unsuccessful](../../relational-databases/event-classes/plan-guide-unsuccessful-event-class.md) .  
  
  