---
title: "Проверка структур плана после обновления | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: performance
ms.reviewer: 
ms.suite: sql
ms.technology: dbe-plan-guides
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: plan guides [SQL Server], validating after upgrade
ms.assetid: a55ebd88-6f58-454d-b1c4-991b88add522
caps.latest.revision: "6"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 65957d9b31988917506edecec87c1f069a1aeca6
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="validate-plan-guides-after-upgrade"></a>Проверка руководств плана после обновления
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] Рекомендуется переоценить и протестировать определения структур планов при обновлении приложения до нового выпуска [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Требования к настройке производительности и поведение сопоставления структур планов могут меняться. Хотя недопустимая структура плана не приведет к сбою при выполнении запроса, план будет скомпилирован без использования структуры, что не рекомендуется. После обновления базы данных до версии [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]рекомендуется выполнить следующие действия.  
  
-   Проверьте существующие структуры планов с помощью функции [sys.fn_validate_plan_guide](../../relational-databases/system-functions/sys-fn-validate-plan-guide-transact-sql.md) .  
  
-   Используйте расширенные события, чтобы проверить наличие планов без структуры за определенное время с помощью события [Plan Guide Unsuccessful](../../relational-databases/event-classes/plan-guide-unsuccessful-event-class.md) .  
  
  
