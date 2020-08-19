---
description: sys.dm_exec_cached_plan_dependent_objects (Transact-SQL)
title: sys. dm_exec_cached_plan_dependent_objects (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
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
author: CarlRabeler
ms.author: carlrab
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 4d69d1e26e5cfb6a7352f92851527b69954a7261
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88447686"
---
# <a name="sysdm_exec_cached_plan_dependent_objects-transact-sql"></a>sys.dm_exec_cached_plan_dependent_objects (Transact-SQL)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  Возвращает строку для каждого плана выполнения [!INCLUDE[tsql](../../includes/tsql-md.md)], плана выполнения среды CLR и связанного с планом курсора.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
sys.dm_exec_cached_plan_dependent_objects(plan_handle)  
```  
  
## <a name="arguments"></a>Аргументы  
*plan_handle*  
Токен, однозначно определяющий план выполнения запроса для пакета, который был выполнен, а его план находится в кэше планов. *plan_handle* имеет тип **varbinary (64)**.   

*Plan_handle* можно получить из следующих объектов DMO:  
  
-   [sys.dm_exec_cached_plans (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-exec-cached-plans-transact-sql.md)  
  
-   [sys.dm_exec_query_stats (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-stats-transact-sql.md)  
  
-   [sys.dm_exec_requests (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)  

-   [sys. dm_exec_procedure_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-procedure-stats-transact-sql.md)  

-   [sys. dm_exec_trigger_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-trigger-stats-transact-sql.md)  
  
## <a name="table-returned"></a>Возвращаемая таблица  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**usecounts**|**int**|Число раз, когда был использован контекст выполнения или курсор.<br /><br /> Столбец не может содержать значение NULL.|  
|**memory_object_address**|**varbinary(8)**|Адрес контекста выполнения или курсора в памяти.<br /><br /> Столбец не может содержать значение NULL.|  
|**cacheobjtype**|**nvarchar(50)**|Тип объекта кэша планов. Столбец не может содержать значение NULL. Возможные значения.<br /><br /> Исполняемый план.<br /><br /> Скомпилированная функция CLR.<br /><br /> Скомпилированная процедура CLR.<br /><br /> Курсор|  
  
## <a name="permissions"></a>Разрешения  
 Необходимо разрешение `VIEW SERVER STATE` на сервере.  
  
## <a name="physical-joins"></a>Физические соединения  
 ![Диаграмма связей](../../relational-databases/system-dynamic-management-views/media/dm-dependent-objects.gif "Диаграмма связей")  
  
## <a name="relationship-cardinalities"></a>Количество элементов связей  
  
|От|Кому|Включено|Связь|  
|----------|--------|--------|------------------|  
|**dm_exec_cached_plan_dependent_objects**|**dm_os_memory_objects**|**memory_object_address**|Один к одному|  
  
## <a name="see-also"></a>См. также:  
 [Динамические административные представления и функции, связанные с выполнением &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md)   
 [Динамические административные представления и функции (Transact-SQL)](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [sys.sysкачеобжектс &#40;Transact-SQL&#41;](../../relational-databases/system-compatibility-views/sys-syscacheobjects-transact-sql.md)  
  
  
