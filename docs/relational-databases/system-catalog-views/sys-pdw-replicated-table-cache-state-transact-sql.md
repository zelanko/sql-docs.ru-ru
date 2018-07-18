---
title: sys.pdw_replicated_table_cache_state (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 07/03/2017
ms.prod: ''
ms.prod_service: sql-data-warehouse
ms.service: sql-data-warehouse
ms.component: system-objects
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: = azure-sqldw-latest || = sqlallproducts-allversions
ms.openlocfilehash: 8d78a537bb2de2ee880551afd3667f308b49ce83
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2018
ms.locfileid: "37985110"
---
# <a name="syspdwreplicatedtablecachestate-transact-sql"></a>sys.pdw_replicated_table_cache_state (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md.md)]

  Возвращает состояние кэша, связанный с реплицированной таблицы с **object_id**.  
  
|Имя столбца|Тип данных|Описание|Диапазон|  
|-----------------|---------------|-----------------|-----------|  
|object_id|**int**|Идентификатор объекта для таблицы. См. в разделе [sys.objects &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md).<br /><br /> **object_id** является ключом для этого представления.||  
|state|**nvarchar(40)**|Состояние кэша реплицируемой таблицы для этой таблицы.|«NotReady», «Готово»|  
  
## <a name="example"></a>Пример
В этом примере соединяет sys.pdw_replicated_table_cache_state с sys.tables для получения имени таблицы и состояние кэша реплицируемой таблицы.

```sql
SELECT t.[name], p.[object_id], p.[state]
  FROM sys.pdw_replicated_table_cache_state p 
  JOIN sys.tables t ON t.object_id = p.object_id
```



## <a name="next-steps"></a>Следующие шаги  
 Список всех представлений каталога для хранилища данных SQL и Parallel Data Warehouse, см. в разделе [хранилище данных SQL и представления каталога хранилища параллельных данных](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md).   
  
