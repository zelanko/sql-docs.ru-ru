---
title: "sys.table_types (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- table_types_TSQL
- sys.table_types
- sys.table_types_TSQL
- table_types
dev_langs: TSQL
helpviewer_keywords:
- table types [SQL Server]
- table-valued parameters, sys.table_types
- sys.table_types
- UDTT
ms.assetid: c05fd873-aff2-4a89-9936-a54c2ea09996
caps.latest.revision: "25"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: e9c55e83d67fcd5817575b0b045bb680b0269217
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="systabletypes-transact-sql"></a>sys.table_types (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Отображает свойства определенных пользователем табличных типов в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Табличный тип — это тип, на основании которого могут быть объявлены переменные таблицы или возвращающие табличное значение параметры. Каждый табличный тип имеет **type_table_object_id** — это внешний ключ в [sys.objects](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md) представления каталога. Этот столбец идентификатора можно использовать для запроса различным представлениям каталога, в результате которого аналогичен **object_id** столбца обычной таблицы для определения структуры табличного типа, таких как столбцы и ограничения.    
 
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|*\<унаследованные столбцы >*||Список столбцов, наследуемых этим представлением см. в разделе [sys.types &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-types-transact-sql.md).|  
|**type_table_object_id**|**int**|Идентификационный номер объекта. Является уникальным в пределах базы данных.|  
|**is_memory_optimized**|**bit**|**Область применения**: начиная с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Допустимы следующие значения:<br /><br /> 0 = не оптимизировано для памяти<br /><br /> 1 = оптимизировано для памяти<br /><br /> Значение по умолчанию — 0.<br /><br /> Типы таблиц всегда создаются с DURABILITY = SCHEMA_ONLY. Только схема сохраняется на диске.|  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>См. также:  
 [Представления каталога объектов &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Использование возвращающих табличные значения параметры &#40; компонент Database Engine &#41;](../../relational-databases/tables/use-table-valued-parameters-database-engine.md)   
 [Выполняющаяся в памяти OLTP (оптимизация в памяти)](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
