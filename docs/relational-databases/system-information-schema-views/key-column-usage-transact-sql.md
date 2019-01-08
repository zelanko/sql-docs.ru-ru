---
title: KEY_COLUMN_USAGE (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- KEY_COLUMN_USAGE_TSQL
- KEY_COLUMN_USAGE
dev_langs:
- TSQL
helpviewer_keywords:
- INFORMATION_SCHEMA.KEY_COLUMN_USAGE view
- KEY_COLUMN_USAGE view
ms.assetid: ec1e18c2-63a1-4d2b-ba9a-c13857403782
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 5f68c5e5671e31b166e82970e59c265334ed3188
ms.sourcegitcommit: 37310da0565c2792aae43b3855bd3948fd13e044
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/18/2018
ms.locfileid: "53588909"
---
# <a name="keycolumnusage-transact-sql"></a>KEY_COLUMN_USAGE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Возвращает одну строку для каждого столбца, ограниченного как ключ в текущей базе данных. Это представление информационной схемы возвращает сведения об объектах, на которые у текущего пользователя есть разрешения.  
  
 Чтобы получить сведения из этих представлений, укажите полное имя **INFORMATION_SCHEMA.** _view_name_.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**CONSTRAINT_CATALOG**|**nvarchar (** 128 **)**|Квалификатор ограничения.|  
|**CONSTRAINT_SCHEMA**|**nvarchar (** 128 **)**|Имя схемы, содержащей ограничение.<br /><br /> <strong>\*\* Важные \* \*</strong>  не используйте представления INFORMATION_SCHEMA, чтобы определить схему объекта. Единственный надежный способ найти схему объекта — направить запрос к представлению каталога sys.objects.|  
|**CONSTRAINT_NAME**|**nvarchar (** 128 **)**|Имя ограничения.|  
|**ЗНАЧЕНИЯМ TABLE_CATALOG**|**nvarchar (** 128 **)**|Квалификатор таблицы.|  
|**TABLE_SCHEMA**|**nvarchar (** 128 **)**|Имя схемы, содержащей таблицу.<br /><br /> <strong>\*\* Важные \* \*</strong>  не используйте представления INFORMATION_SCHEMA, чтобы определить схему объекта. Единственный надежный способ найти схему объекта — направить запрос к представлению каталога sys.objects.|  
|**ИМЯ_ТАБЛИЦЫ**|**nvarchar (** 128 **)**|Имя таблицы.|  
|**COLUMN_NAME**|**nvarchar (** 128 **)**|Имя столбца.|  
|**ORDINAL_POSITION**|**int**|Порядковая позиция столбца.|  
  
## <a name="see-also"></a>См. также  
 [Системные представления &#40;Transact-SQL&#41;](https://msdn.microsoft.com/library/35a6161d-7f43-4e00-bcd3-3091f2015e90)   
 [Представления информационной схемы &#40;Transact-SQL&#41;](~/relational-databases/system-information-schema-views/system-information-schema-views-transact-sql.md)   
 [sys.columns (Transact-SQL)](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md)   
 [sys.indexes (Transact-SQL)](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)   
 [sys.objects (Transact-SQL)](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)   
 [sys.foreign_keys &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-foreign-keys-transact-sql.md)   
 [sys.key_constraints &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-key-constraints-transact-sql.md)  
  
  
