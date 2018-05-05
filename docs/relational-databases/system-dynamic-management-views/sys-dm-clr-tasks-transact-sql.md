---
title: sys.dm_clr_tasks (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.service: ''
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_clr_tasks
- sys.dm_clr_tasks_TSQL
- dm_clr_tasks
- dm_clr_tasks_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_clr_tasks dynamic management view
ms.assetid: 462b9061-09fa-4858-9707-03d6cc19c769
caps.latest.revision: 21
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 5ae63389310a8100c75e008e6d4e508d55800424
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="sysdmclrtasks-transact-sql"></a>sys.dm_clr_tasks (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Возвращает по одной строке для всех задач среды CLR, выполняющихся в данный момент. Пакет языка [!INCLUDE[tsql](../../includes/tsql-md.md)], который содержит ссылку на процедуру среды CLR, создает отдельную задачу для выполнения всего управляемого кода в пакете. Несколько инструкций пакета, которые требуют выполнения управляемого кода, используют одну и ту же задачу среды CLR. Задача среды CLR отвечает за поддержку объектов и состояний, относящихся к выполнению управляемого кода, а также за обмен данными между экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и средой CLR.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**task_address**|**varbinary(8)**|Адрес задачи среды CLR.|  
|**sos_task_address**|**varbinary(8)**|Адрес базовой задачи пакета языка [!INCLUDE[tsql](../../includes/tsql-md.md)].|  
|**appdomain_address**|**varbinary(8)**|Адрес домена приложений, в котором выполняется задача.|  
|**state**|**nvarchar(128)**|Текущее состояние задачи.|  
|**abort_state**|**nvarchar(128)**|Указывает на состояние прерывания (если выполнение задачи было отменено). Существует несколько состояний, связанных с прерыванием задач.|  
|**type**|**nvarchar(128)**|Тип задачи.|  
|**affinity_count**|**int**|Родственность задачи.|  
|**forced_yield_count**|**int**|Количество раз, когда задача принудительно выдавала результат.|  
  
## <a name="permissions"></a>Разрешения  

На [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], требуется `VIEW SERVER STATE` разрешение.   
На [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)], требуется `VIEW DATABASE STATE` разрешение в базе данных.   
  
## <a name="see-also"></a>См. также  
 [Динамические административные представления и функции (Transact-SQL)](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Динамические административные представления, связанные с общеязыковой &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/common-language-runtime-related-dynamic-management-views-transact-sql.md)  
  
  

