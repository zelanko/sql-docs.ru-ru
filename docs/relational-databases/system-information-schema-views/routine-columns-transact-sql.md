---
title: ROUTINE_COLUMNS (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.service: ''
ms.component: system-information-schema-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- ROUTINE_COLUMNS_TSQL
- ROUTINE_COLUMNS
dev_langs:
- TSQL
helpviewer_keywords:
- ROUTINE_COLUMNS view
- INFORMATION_SCHEMA.ROUTINE_COLUMNS view
ms.assetid: 91dbc61b-e4c0-4826-976c-b2fce88b7793
caps.latest.revision: 37
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: a6b3feab27f56ad14b8f534799ad092981cc0b32
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="routinecolumns-transact-sql"></a>ROUTINE_COLUMNS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Возвращает по одной строке для каждого столбца, возвращенного функциями с табличным значением к которым может получить доступ текущий пользователь в текущей базе данных.  
  
 Чтобы получить сведения из этого представления, укажите полное имя **INFORMATION_SCHEMA. *** view_name*.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**ЗНАЧЕНИЯМ TABLE_CATALOG**|**nvarchar (**128**)**|Имя каталога или базы данных функции с табличным значением.|  
|**TABLE_SCHEMA**|**nvarchar (**128**)**|Имя схемы, содержащей функцию с табличным значением.<br /><br /> **\*\* Важные \* \***  не используйте представления INFORMATION_SCHEMA, чтобы определить схему объекта. Единственный надежный способ найти схему объекта — направить запрос к представлению каталога sys.objects.|  
|**ИМЯ_ТАБЛИЦЫ**|**nvarchar (**128**)**|Имя функции с табличным значением.|  
|**COLUMN_NAME**|**nvarchar (**128**)**|Имя столбца.|  
|**ORDINAL_POSITION**|**int**|Идентификационный номер столбца.|  
|**COLUMN_DEFAULT**|**nvarchar (**4000**)**|Значение столбца по умолчанию.|  
|**IS_NULLABLE**|**varchar (**3**)**|Если для этого столбца допустимо значение NULL, возвращается значение YES. В противном случае возвращается значение NO.|  
|**ТИП ДАННЫХ**|**nvarchar (**128**)**|Тип данных, поддерживаемый системой.|  
|**CHARACTER_MAXIMUM_LENGTH**|**int**|Максимальная длина в символах для двоичных данных, символьных данных или текстовых данных и изображений.<br /><br /> -1 для **xml** и данные типов больших значений. В противном случае возвращается значение NULL. Дополнительные сведения см. в разделе [Типы данных (Transact-SQL)](../../t-sql/data-types/data-types-transact-sql.md).|  
|**CHARACTER_OCTET_LENGTH**|**int**|Максимальная длина в байтах для двоичных данных, символьных данных или текстовых данных и изображений.<br /><br /> -1 для **xml** и данные типов больших значений. В противном случае возвращается значение NULL.|  
|**NUMERIC_PRECISION**|**tinyint**|Точность приблизительных числовых данных, точных числовых данных, целочисленных данных или денежных данных. В противном случае возвращается значение NULL.|  
|**NUMERIC_PRECISION_RADIX**|**smallint**|Основание системы счисления точности приблизительных числовых данных, точных числовых данных, целочисленных данных или денежных данных. В противном случае возвращается значение NULL.|  
|**NUMERIC_SCALE**|**tinyint**|Масштаб приблизительных числовых данных, точных числовых данных, целочисленных данных или денежных данных. В противном случае возвращается значение NULL.|  
|**DATETIME_PRECISION**|**smallint**|Код подтипа для **datetime** и ISO**целое** типов данных. Для других типов данных возвращается значение NULL.|  
|**CHARACTER_SET_CATALOG**|**varchar (**6**)**|Возвращает **master**. Указывает базу данных, в которой находится кодировка, если столбец содержит символьные данные или **текст** тип данных. В противном случае возвращается значение NULL.|  
|**CHARACTER_SET_SCHEMA**|**varchar (**3**)**|Всегда возвращает значение NULL.|  
|**CHARACTER_SET_NAME**|**nvarchar (**128**)**|Возвращает уникальное имя для кодировки, если столбец содержит символьные данные или **текст** тип данных. В противном случае возвращается значение NULL.|  
|**COLLATION_CATALOG**|**varchar (**6**)**|Всегда возвращает значение NULL.|  
|**COLLATION_SCHEMA**|**varchar (**3**)**|Всегда возвращает значение NULL.|  
|**COLLATION_NAME**|**nvarchar (**128**)**|Возвращает уникальное имя для порядка сортировки, если столбец содержит символьные данные или **текст** тип данных. В противном случае возвращается значение NULL.|  
|**DOMAIN_CATALOG**|**nvarchar (**128**)**|Если столбец имеет тип данных псевдонима, то этот столбец содержит имя базы данных, в которой был создан определяемый пользователем тип данных. В противном случае возвращается значение NULL.|  
|**DOMAIN_SCHEMA**|**nvarchar (**128**)**|Если столбец имеет пользовательский тип данных, этот столбец является именем схемы, содержащей пользовательский тип данных. В противном случае возвращается значение NULL.<br /><br /> **\*\* Важные \* \***  не используйте представления INFORMATION_SCHEMA, чтобы определить схему объекта. Единственный надежный способ найти схему объекта — направить запрос к представлению каталога sys.objects.|  
|**ИМЯ_ДОМЕНА**|**nvarchar (**128**)**|Если столбец имеет определяемый пользователем тип данных, то столбец является именем этого типа данных. В противном случае возвращается значение NULL.|  
  
## <a name="see-also"></a>См. также  
 [Системные представления &#40;Transact-SQL&#41;](http://msdn.microsoft.com/library/35a6161d-7f43-4e00-bcd3-3091f2015e90)   
 [Представления информационной схемы &#40;Transact-SQL&#41;](~/relational-databases/system-information-schema-views/system-information-schema-views-transact-sql.md)   
 [sys.columns (Transact-SQL)](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md)   
 [sys.objects (Transact-SQL)](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)  
  
  
