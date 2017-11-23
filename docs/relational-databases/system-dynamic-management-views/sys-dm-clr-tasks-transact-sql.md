---
title: "sys.dm_clr_tasks (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.dm_clr_tasks
- sys.dm_clr_tasks_TSQL
- dm_clr_tasks
- dm_clr_tasks_TSQL
dev_langs: TSQL
helpviewer_keywords: sys.dm_clr_tasks dynamic management view
ms.assetid: 462b9061-09fa-4858-9707-03d6cc19c769
caps.latest.revision: "21"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 45aad56182dd79b9b5787e78964b23d7469344d0
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmclrtasks-transact-sql"></a>sys.dm_clr_tasks (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Возвращает по одной строке для всех задач среды CLR, выполняющихся в данный момент. Пакет языка [!INCLUDE[tsql](../../includes/tsql-md.md)], который содержит ссылку на процедуру среды CLR, создает отдельную задачу для выполнения всего управляемого кода в пакете. Несколько инструкций пакета, которые требуют выполнения управляемого кода, используют одну и ту же задачу среды CLR. Задача среды CLR отвечает за поддержку объектов и состояний, относящихся к выполнению управляемого кода, а также за обмен данными между экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и средой CLR.  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**task_address**|**varbinary(8)**|Адрес задачи среды CLR.|  
|**sos_task_address**|**varbinary(8)**|Адрес базовой задачи пакета языка [!INCLUDE[tsql](../../includes/tsql-md.md)].|  
|**appdomain_address**|**varbinary(8)**|Адрес домена приложений, в котором выполняется задача.|  
|**состояние**|**nvarchar(128)**|Текущее состояние задачи.|  
|**abort_state**|**nvarchar(128)**|Указывает на состояние прерывания (если выполнение задачи было отменено). Существует несколько состояний, связанных с прерыванием задач.|  
|**type**|**nvarchar(128)**|Тип задачи.|  
|**affinity_count**|**int**|Родственность задачи.|  
|**forced_yield_count**|**int**|Количество раз, когда задача принудительно выдавала результат.|  
  
## <a name="permissions"></a>Permissions  
 На [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] необходимо разрешение VIEW SERVER STATE на сервере.  
  
 На [!INCLUDE[ssSDS](../../includes/sssds-md.md)] уровней Premium необходимо разрешение VIEW DATABASE STATE в базе данных. На [!INCLUDE[ssSDS](../../includes/sssds-md.md)] уровней Standard и Basic требуется [!INCLUDE[ssSDS](../../includes/sssds-md.md)] учетная запись администратора.  
  
## <a name="see-also"></a>См. также:  
 [Динамические административные представления и функции (Transact-SQL)](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Общеязыковая среда выполнения, связанные с динамическим административным представлениям &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/common-language-runtime-related-dynamic-management-views-transact-sql.md)  
  
  

