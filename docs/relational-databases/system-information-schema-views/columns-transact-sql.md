---
title: "СТОЛБЦЫ (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: system-information-schema-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- COLUMNS
- COLUMNS_TSQL
dev_langs: TSQL
helpviewer_keywords:
- COLUMNS view
- INFORMATION_SCHEMA.COLUMNS view
ms.assetid: bbf7ac4a-7444-4351-a590-a9f71e0bc495
caps.latest.revision: "48"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 2190490e4b5bcb7aeaec10086cbef51da955b005
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="columns-transact-sql"></a>COLUMNS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Возвращает одну строку для каждого столбца, доступного для текущего пользователя в текущей базе данных.  
  
 Чтобы получить сведения из этих представлений, укажите полное имя **INFORMATION_SCHEMA***.* *view_name*.  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**ЗНАЧЕНИЯМ TABLE_CATALOG**|**nvarchar (**128**)**|Квалификатор таблицы.|  
|**TABLE_SCHEMA**|**nvarchar (**128**)**|Имя схемы, содержащей таблицу.<br /><br /> **\*\*Важные \* \***  не используйте представления INFORMATION_SCHEMA, чтобы определить схему объекта. Единственный надежный способ найти схему объекта — направить запрос к представлению каталога sys.objects.|  
|**ИМЯ_ТАБЛИЦЫ**|**nvarchar (**128**)**|Имя таблицы.|  
|**COLUMN_NAME**|**nvarchar (**128**)**|Имя столбца.|  
|**ORDINAL_POSITION**|**int**|Идентификационный номер столбца.|  
|**COLUMN_DEFAULT**|**nvarchar (**4000**)**|Значение столбца по умолчанию.|  
|**IS_NULLABLE**|**varchar (**3**)**|Указывает, может ли столбец допускать значение NULL. Если для столбца допустимо значение NULL, этот столбец возвращает значение YES. Иначе возвращается значение NO.|  
|**ТИП ДАННЫХ**|**nvarchar (**128**)**|Тип данных, поддерживаемый системой.|  
|**CHARACTER_MAXIMUM_LENGTH**|**int**|Максимальная длина в символах для двоичных данных, символьных данных или текстовых данных и изображений.<br /><br /> -1 для **xml** и данные типов больших значений. Иначе возвращается значение NULL. Дополнительные сведения см. в разделе [Типы данных (Transact-SQL)](../../t-sql/data-types/data-types-transact-sql.md).|  
|**CHARACTER_OCTET_LENGTH**|**int**|Максимальная длина в байтах для двоичных данных, символьных данных или текстовых данных и изображений.<br /><br /> -1 для **xml** и данные типов больших значений. Иначе возвращается значение NULL.|  
|**NUMERIC_PRECISION**|**tinyint**|Точность приблизительных числовых данных, точных числовых данных, целочисленных данных или денежных данных. Иначе возвращается значение NULL.|  
|**NUMERIC_PRECISION_RADIX**|**smallint**|Основание системы счисления точности приблизительных числовых данных, точных числовых данных, целочисленных данных или денежных данных. Иначе возвращается значение NULL.|  
|**NUMERIC_SCALE**|**int**|Масштаб приблизительных числовых данных, точных числовых данных, целочисленных данных или денежных данных. Иначе возвращается значение NULL.|  
|**DATETIME_PRECISION**|**smallint**|Код подтипа для **datetime** и ISO **интервал** типов данных. Для других типов данных возвращается значение NULL.|  
|**CHARACTER_SET_CATALOG**|**nvarchar (**128**)**|Возвращает **master**. Это указывает базу данных, в которой находится кодировка, если столбец содержит символьные данные или **текст** тип данных. Иначе возвращается значение NULL.|  
|**CHARACTER_SET_SCHEMA**|**nvarchar (**128**)**|Всегда возвращает значение NULL.|  
|**CHARACTER_SET_NAME**|**nvarchar (**128**)**|Возвращает уникальное имя для кодировки, если столбец содержит символьные данные или **текст** тип данных. Иначе возвращается значение NULL.|  
|**COLLATION_CATALOG**|**nvarchar (**128**)**|Всегда возвращает значение NULL.|  
|**COLLATION_SCHEMA**|**nvarchar (**128**)**|Всегда возвращает значение NULL.|  
|**COLLATION_NAME**|**nvarchar (**128**)**|Возвращает уникальное имя для параметров сортировки, если столбец содержит символьные данные или **текст** тип данных. Иначе возвращается значение NULL.|  
|**DOMAIN_CATALOG**|**nvarchar (**128**)**|Если столбец имеет тип данных псевдонима, то этот столбец содержит имя базы данных, в которой был создан определяемый пользователем тип данных. Иначе возвращается значение NULL.|  
|**DOMAIN_SCHEMA**|**nvarchar (**128**)**|Если столбец имеет определяемый пользователем тип данных, то столбец возвращает имя схемы этого типа данных. Иначе возвращается значение NULL.<br /><br /> **\*\*Важные \* \***  не используйте представления INFORMATION_SCHEMA, чтобы определить схему типа данных. Единственный надежный способ найти схему типа — использовать функцию TYPEPROPERTY.|  
|**ИМЯ_ДОМЕНА**|**nvarchar (**128**)**|Если столбец имеет определяемый пользователем тип данных, то столбец является именем этого типа данных. Иначе возвращается значение NULL.|  
  
## <a name="remarks"></a>Замечания  
 **ORDINAL_POSITION** столбец **INFORMATION_SCHEMA. СТОЛБЦЫ** не совместим с битовым шаблоном столбцов, возвращаемых функцией COLUMNS_UPDATED. Чтобы получить битовый шаблон, совместимый с COLUMNS_UPDATED, необходимо сослаться на **ColumnID** свойство системной функции COLUMNPROPERTY при запросе **INFORMATION_SCHEMA. СТОЛБЦЫ** представления. Например:  
  
```  
USE AdventureWorks2012;  
GO  
SELECT TABLE_NAME, COLUMN_NAME, COLUMNPROPERTY(OBJECT_ID(TABLE_SCHEMA + '.' + TABLE_NAME), COLUMN_NAME, 'ColumnID') AS COLUMN_ID  
FROM AdventureWorks2012.INFORMATION_SCHEMA.COLUMNS  
WHERE TABLE_NAME = 'Person';  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [Системные представления &#40; Transact-SQL &#41;](http://msdn.microsoft.com/library/35a6161d-7f43-4e00-bcd3-3091f2015e90)   
 [Представления информационной схемы &#40; Transact-SQL &#41;](~/relational-databases/system-information-schema-views/system-information-schema-views-transact-sql.md)   
 [sys.syscharsets &#40; Transact-SQL &#41;](../../relational-databases/system-compatibility-views/sys-syscharsets-transact-sql.md)   
 [sys.columns (Transact-SQL)](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md)   
 [sys.sql_modules (Transact-SQL)](../../relational-databases/system-catalog-views/sys-sql-modules-transact-sql.md)   
 [sys.configurations (Transact-SQL)](../../relational-databases/system-catalog-views/sys-configurations-transact-sql.md)   
 [sys.Objects &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)   
 [sys.types (Transact-SQL)](../../relational-databases/system-catalog-views/sys-types-transact-sql.md)   
 [Функция COLUMNS_UPDATED &#40; Transact-SQL &#41;](../../t-sql/functions/columns-updated-transact-sql.md)  
  
  
