---
title: sys. dm_pdw_lock_waits (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 8ef966f8-d14e-40d3-9626-3508ada9b8fb
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 29a82daa2857177200bd76b738f92d65f6b26668
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "67899380"
---
# <a name="sysdm_pdw_lock_waits-transact-sql"></a>sys. dm_pdw_lock_waits (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Содержит сведения о запросах, ожидающих блокировки.  
  
|Имя столбца|Тип данных|Описание|Диапазон|  
|-----------------|---------------|-----------------|-----------|  
|wait_id|**bigint**|Расположение запроса в списке ожидания.|порядковый номер, основанный на 0. Оно не является уникальным для всех записей ожидания.|  
|session_id|**nvarchar(32)**|Идентификатор сеанса, в котором произошло состояние ожидания.|См. раздел session_id в [sys. dm_pdw_exec_sessions &#40;&#41;Transact-SQL ](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-sessions-transact-sql.md).|  
|type|**nvarchar(255)**|Тип ожидания, который представляет эта запись.|Возможные значения:<br /><br /> Shared<br /><br /> шаредупдате<br /><br /> ексклусивеупдате<br /><br /> Монопольная блокировка|  
|object_type|**nvarchar(255)**|Тип объекта, на который влияет ожидание.|Возможные значения:<br /><br /> OBJECT<br /><br /> DATABASE<br /><br /> SYSTEM<br /><br /> SCHEMA<br /><br /> APPLICATION|  
|object_name|**nvarchar (386)**|Имя или идентификатор GUID указанного объекта, на который влияет ожидание.|Таблицы и представления отображаются с именами из трех частей.<br /><br /> Индексы и статистика отображаются с именами из четырех частей.<br /><br /> Имена, участники и базы данных являются строковыми именами.|  
|request_id|**nvarchar(32)**|Идентификатор запроса, для которого произошло состояние ожидания.|Идентификатор запроса.<br /><br /> Это идентификатор GUID для запросов загрузки.|  
|request_time|**datetime**|Время запроса блокировки или ресурса.||  
|acquire_time|**datetime**|Время, когда был получен блокировка или ресурс.||  
|state|**nvarchar(50)**|Состояние состояния ожидания.|[!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]|  
|priority|**int**|Приоритет ожидающего элемента.|[!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]|  
  
## <a name="see-also"></a>См. также  
 [Динамические административные представления хранилища данных SQL и параллельного хранилища данных &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
