---
title: ТАБЛИЦЫ (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: system-information-schema-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- TABLES_TSQL
- TABLES
dev_langs:
- TSQL
helpviewer_keywords:
- TABLES view
- INFORMATION_SCHEMA.TABLES view
ms.assetid: 723a9e63-8f6e-4d6e-b570-468cfaf03201
caps.latest.revision: 39
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 3e41d96d6376dceb8594851e2ba31244ca1a8b60
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="tables-transact-sql"></a>TABLES (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Возвращает по одной строке для каждой таблицы в текущей базе данных, на которую есть разрешения у пользователя.  
  
 Чтобы получить сведения из этих представлений, укажите полное имя **INFORMATION_SCHEMA. *** view_name*.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**ЗНАЧЕНИЯМ TABLE_CATALOG**|**nvarchar (** 128 **)**|Квалификатор таблицы.|  
|**TABLE_SCHEMA**|**nvarchar (** 128 **)**|Имя схемы, содержащей таблицу.<br /><br /> **\*\* Важные \* \***  не используйте представления INFORMATION_SCHEMA, чтобы определить схему объекта. Единственный надежный способ найти схему объекта — выполнить запрос к представлению каталога sys.objects. Представления INFORMATION_SCHEMA могут быть неполными, поскольку они не обновлены для работы со всеми новыми функциями.|  
|**ИМЯ_ТАБЛИЦЫ**|**sysname**|Имя таблицы.|  
|**TABLE_TYPE**|**varchar (** 10 **)**|Тип таблицы. Может быть VIEW или BASE TABLE.|  
  
## <a name="see-also"></a>См. также  
 [Системные представления &#40;Transact-SQL&#41;](http://msdn.microsoft.com/library/35a6161d-7f43-4e00-bcd3-3091f2015e90)   
 [Представления информационной схемы &#40;Transact-SQL&#41;](~/relational-databases/system-information-schema-views/system-information-schema-views-transact-sql.md)   
 [sys.objects (Transact-SQL)](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)   
 [sys.tables (Transact-SQL)](../../relational-databases/system-catalog-views/sys-tables-transact-sql.md)  
  
  
