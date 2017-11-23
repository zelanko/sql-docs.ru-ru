---
title: "dbo.syssessions (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-tables
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- dbo.syssessions_TSQL
- dbo.syssessions
- syssessions_TSQL
- syssessions
dev_langs: TSQL
helpviewer_keywords: syssessions system table
ms.assetid: 187819b6-c7f4-4a26-b74c-0a89e96695cf
caps.latest.revision: "14"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 140d81eef1b0f6b745e5f889b7889c265820405c
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="dbosyssessions-transact-sql"></a>dbo.syssessions (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  При каждом запуске агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] создается новый сеанс. С помощью сеансов агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] сохраняет состояние заданий при непредвиденном перезапуске или остановке службы агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Каждая строка **syssessions** таблица содержит сведения об одном сеансе. Используйте **sysjobactivity** таблицу, чтобы просмотреть состояние задания в конце каждого сеанса.  
  
 Эта таблица хранится в **msdb** базы данных.  
  
||  
|-|  
|**Область применения**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (с[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [текущей версии](http://go.microsoft.com/fwlink/p/?LinkId=299658)).|  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**session_id**|**int**|Идентификатор сеанса агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**agent_start_date**|**datetime**|Дата и время запуска службы агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для этого сеанса.|  
  
## <a name="remarks"></a>Замечания  
 Только пользователи, являющиеся членами из **sysadmin** предопределенной роли сервера можно получить доступ к этой таблице.  
  
## <a name="see-also"></a>См. также:  
 [dbo.sysjobactivity &#40; Transact-SQL &#41;](../../relational-databases/system-tables/dbo-sysjobactivity-transact-sql.md)  
  
  
