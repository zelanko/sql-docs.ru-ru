---
title: sys.dm_clr_tasks (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
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
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: b1386f34ad1ae82229729e9db696c95176c43aa9
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62742080"
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
 [Динамические административные представления, связанные с среда CLR &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/common-language-runtime-related-dynamic-management-views-transact-sql.md)  
  
  

