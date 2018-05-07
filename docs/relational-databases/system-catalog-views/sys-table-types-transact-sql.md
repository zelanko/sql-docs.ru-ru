---
title: sys.table_types (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- table_types_TSQL
- sys.table_types
- sys.table_types_TSQL
- table_types
dev_langs:
- TSQL
helpviewer_keywords:
- table types [SQL Server]
- table-valued parameters, sys.table_types
- sys.table_types
- UDTT
ms.assetid: c05fd873-aff2-4a89-9936-a54c2ea09996
caps.latest.revision: 25
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: b93b2395aa31d68de287628b512d111ac423bd92
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="systabletypes-transact-sql"></a>sys.table_types (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Отображает свойства определенных пользователем табличных типов в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Табличный тип — это тип, на основании которого могут быть объявлены переменные таблицы или возвращающие табличное значение параметры. Каждый табличный тип имеет **type_table_object_id** — это внешний ключ в [sys.objects](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md) представления каталога. Этот столбец идентификатора можно использовать для запроса различным представлениям каталога, в результате которого аналогичен **object_id** столбца обычной таблицы для определения структуры табличного типа, таких как столбцы и ограничения.    
 
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|*\<Унаследованные столбцы >*||Список столбцов, наследуемых этим представлением см. в разделе [sys.types &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-types-transact-sql.md).|  
|**type_table_object_id**|**int**|Идентификационный номер объекта. Является уникальным в пределах базы данных.|  
|**is_memory_optimized**|**бит**|**Область применения**: начиная с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Допустимы следующие значения:<br /><br /> 0 = не оптимизировано для памяти<br /><br /> 1 = оптимизировано для памяти<br /><br /> Значение по умолчанию — 0.<br /><br /> Типы таблиц всегда создаются с DURABILITY = SCHEMA_ONLY. Только схема сохраняется на диске.|  
  
## <a name="permissions"></a>Разрешения  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>См. также  
 [Представления каталога объектов (Transact-SQL)](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Использование параметров, возвращающих табличные значения (ядро СУБД)](../../relational-databases/tables/use-table-valued-parameters-database-engine.md)   
 [Выполняющаяся в памяти OLTP &#40;оптимизация в памяти&#41;](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
