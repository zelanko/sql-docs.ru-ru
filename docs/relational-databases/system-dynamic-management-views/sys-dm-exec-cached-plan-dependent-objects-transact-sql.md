---
title: sys.dm_exec_cached_plan_dependent_objects (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/16/2017
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
- sys.dm_exec_cached_plan_dependent_objects
- dm_exec_cached_plan_dependent_objects_TSQL
- sys.dm_exec_cached_plan_dependent_objects_TSQL
- dm_exec_cached_plan_dependent_objects
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_exec_cached_plan_dependent_objects dynamic management function
ms.assetid: 9b6cf5f7-b267-44fb-aac8-f49c9aa10cc1
caps.latest.revision: 19
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: e9303dd028cdc979e978e05ea87afe7718a566ba
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="sysdmexeccachedplandependentobjects-transact-sql"></a>sys.dm_exec_cached_plan_dependent_objects (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Возвращает строку для каждого плана выполнения [!INCLUDE[tsql](../../includes/tsql-md.md)], плана выполнения среды CLR и связанного с планом курсора.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
dm_exec_cached_plan_dependent_objects(plan_handle)  
```  
  
## <a name="arguments"></a>Аргументы  
 *plan_handle*  
 Уникально идентифицирует план выполнения запросов для выполненного пакета, план которого хранится в кэше планов. *plan_handle* — **varbinary(64)**. *Plan_handle* можно получить из следующих объектов DMO:  
  
-   [sys.dm_exec_cached_plans &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-cached-plans-transact-sql.md)  
  
-   [sys.dm_exec_query_stats (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-stats-transact-sql.md)  
  
-   [sys.dm_exec_requests (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)  
  
## <a name="table-returned"></a>Возвращаемая таблица  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**usecounts**|**int**|Число раз, когда был использован контекст выполнения или курсор.<br /><br /> Столбец не может содержать значение NULL.|  
|**memory_object_address**|**varbinary(8)**|Адрес контекста выполнения или курсора в памяти.<br /><br /> Столбец не может содержать значение NULL.|  
|**cacheobjtype**|**nvarchar(50)**|Тип объекта кэша планов. Столбец не может содержать значение NULL. Возможные значения.<br /><br /> Исполняемый план.<br /><br /> Скомпилированная функция CLR.<br /><br /> Скомпилированная процедура CLR.<br /><br /> Курсор|  
  
## <a name="permissions"></a>Разрешения  
 необходимо разрешение VIEW SERVER STATE на сервере.  
  
## <a name="physical-joins"></a>Физические соединения  
 ![Диаграмма связей](../../relational-databases/system-dynamic-management-views/media/dm-dependent-objects.gif "Диаграмма связей")  
  
## <a name="relationship-cardinalities"></a>Количество элементов связей  
  
|От|Чтобы|В|Связь|  
|----------|--------|--------|------------------|  
|**dm_exec_cached_plan_dependent_objects**|**dm_os_memory_objects**|**memory_object_address**|Один к одному|  
  
## <a name="see-also"></a>См. также  
 [Динамические административные представления и функции, связанные с выполнением &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md)   
 [Динамические административные представления и функции (Transact-SQL)](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [sys.syscacheobjects &#40;Transact-SQL&#41;](../../relational-databases/system-compatibility-views/sys-syscacheobjects-transact-sql.md)  
  
  
