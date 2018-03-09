---
title: "MSSQLSERVER_10509 | Документация Майкрософт"
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: errors-events
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords: 10509 (Database Engine error)
ms.assetid: e9dd5357-ee3d-420a-9a89-d12ab5404e73
caps.latest.revision: "9"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 1f20d57d41659acbead6597dc10324fedd5410b6
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="mssqlserver10509"></a>MSSQLSERVER_10509
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|10509|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|PG_INVALID_STMT|  
|Текст сообщения|Не удалось создать структуру плана '%.\*ls', поскольку инструкция, указанная параметром **@stmt** или **@statement_start_offset**, содержит синтаксическую ошибку или недопустима для использования в структуре плана. Задайте одну допустимую инструкцию [!INCLUDE[tsql](../../includes/tsql-md.md)] или допустимую начальную позицию инструкции внутри пакета. Допустимую начальную позицию можно запросить из столбца statement_start_offset функции динамического управления sys.dm_exec_query_stats.|  
  
## <a name="explanation"></a>Объяснение  
Инструкция, указанная параметром **@stmt** или **@statement_start_offset**, содержит синтаксическую ошибку или недопустима для использования в структуре плана.  
  
## <a name="user-action"></a>Действие пользователя  
Задайте одну допустимую инструкцию [!INCLUDE[tsql](../../includes/tsql-md.md)] или допустимую начальную позицию инструкции внутри пакета. Допустимую начальную позицию можно запросить из столбца statement_start_offset функции динамического управления sys.dm_exec_query_stats.  
  
## <a name="see-also"></a>См. также:  
[sp_create_plan_guide (Transact-SQL)](~/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql.md)  
[Структуры плана](~/relational-databases/performance/plan-guides.md)  
[sys.dm_exec_query_stats (Transact-SQL)](~/relational-databases/system-dynamic-management-views/sys-dm-exec-query-stats-transact-sql.md)  
[sp_create_plan_guide_from_handle (Transact-SQL)](~/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql.md)  
  
