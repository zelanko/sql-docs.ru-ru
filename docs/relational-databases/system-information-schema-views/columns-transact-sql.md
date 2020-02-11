---
title: СТОЛБЦЫ (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- COLUMNS
- COLUMNS_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- COLUMNS view
- INFORMATION_SCHEMA.COLUMNS view
ms.assetid: bbf7ac4a-7444-4351-a590-a9f71e0bc495
author: CarlRabeler
ms.author: carlrab
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 021e9e66b281a8bbca6d5c9e21e78ffa4069c5c9
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67950791"
---
# <a name="columns-transact-sql"></a>COLUMNS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Возвращает одну строку для каждого столбца, доступного для текущего пользователя в текущей базе данных.  
  
 Чтобы получить сведения из этих представлений, укажите полное имя **INFORMATION_SCHEMA**_. view_name_.  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**TABLE_CATALOG**|**nvarchar (** 128 **)**|Квалификатор таблицы.|  
|**TABLE_SCHEMA**|**nvarchar (** 128 **)**|Имя схемы, содержащей таблицу.<br /><br /> **&#42;&#42; важно &#42;&#42;** Не используйте INFORMATION_SCHEMA представления для определения схемы объекта. Единственный надежный способ найти схему объекта — направить запрос к представлению каталога sys.objects.|  
|**TABLE_NAME**|**nvarchar (** 128 **)**|Имя таблицы.|  
|**COLUMN_NAME**|**nvarchar (** 128 **)**|Имя столбца.|  
|**ORDINAL_POSITION**|**int**|Идентификационный номер столбца.|  
|**COLUMN_DEFAULT**|**nvarchar (** 4000 **)**|Значение столбца по умолчанию.|  
|**IS_NULLABLE**|**varchar (** 3 **)**|Указывает, может ли столбец допускать значение NULL. Если для столбца допустимо значение NULL, этот столбец возвращает значение YES. Иначе возвращается значение NO.|  
|**DATA_TYPE**|**nvarchar (** 128 **)**|Тип данных, поддерживаемый системой.|  
|**CHARACTER_MAXIMUM_LENGTH**|**int**|Максимальная длина в символах для двоичных данных, символьных данных или текстовых данных и изображений.<br /><br /> -1 для данных типа **XML** и больших значений. Иначе возвращается значение NULL. Дополнительные сведения см. в разделе [Типы данных (Transact-SQL)](../../t-sql/data-types/data-types-transact-sql.md).|  
|**CHARACTER_OCTET_LENGTH**|**int**|Максимальная длина в байтах для двоичных данных, символьных данных или текстовых данных и изображений.<br /><br /> -1 для данных типа **XML** и больших значений. Иначе возвращается значение NULL.|  
|**NUMERIC_PRECISION**|**tinyint**|Точность приблизительных числовых данных, точных числовых данных, целочисленных данных или денежных данных. Иначе возвращается значение NULL.|  
|**NUMERIC_PRECISION_RADIX**|**smallint**|Основание системы счисления точности приблизительных числовых данных, точных числовых данных, целочисленных данных или денежных данных. Иначе возвращается значение NULL.|  
|**NUMERIC_SCALE**|**int**|Масштаб приблизительных числовых данных, точных числовых данных, целочисленных данных или денежных данных. Иначе возвращается значение NULL.|  
|**DATETIME_PRECISION**|**smallint**|Код подтипа для типов данных **интервала** **DateTime** и ISO. Для других типов данных возвращается значение NULL.|  
|**CHARACTER_SET_CATALOG**|**nvarchar (** 128 **)**|Возвращает **образец**. Указывает базу данных, в которой находится набор символов, если столбец содержит символьные данные или **текстовый** тип данных. Иначе возвращается значение NULL.|  
|**CHARACTER_SET_SCHEMA**|**nvarchar (** 128 **)**|Всегда возвращает значение NULL.|  
|**CHARACTER_SET_NAME**|**nvarchar (** 128 **)**|Возвращает уникальное имя для набора символов, если этот столбец имеет символьные данные или тип данных **Text** . Иначе возвращается значение NULL.|  
|**COLLATION_CATALOG**|**nvarchar (** 128 **)**|Всегда возвращает значение NULL.|  
|**COLLATION_SCHEMA**|**nvarchar (** 128 **)**|Всегда возвращает значение NULL.|  
|**COLLATION_NAME**|**nvarchar (** 128 **)**|Возвращает уникальное имя для параметров сортировки, если столбец имеет символьные данные или **текстовый** тип данных. Иначе возвращается значение NULL.|  
|**DOMAIN_CATALOG**|**nvarchar (** 128 **)**|Если столбец имеет тип данных псевдонима, то этот столбец содержит имя базы данных, в которой был создан определяемый пользователем тип данных. Иначе возвращается значение NULL.|  
|**DOMAIN_SCHEMA**|**nvarchar (** 128 **)**|Если столбец имеет определяемый пользователем тип данных, то столбец возвращает имя схемы этого типа данных. Иначе возвращается значение NULL.<br /><br /> **&#42;&#42; важно &#42;&#42;** Не используйте INFORMATION_SCHEMA представления для определения схемы типа данных. Единственный надежный способ найти схему типа — использовать функцию TYPEPROPERTY.|  
|**DOMAIN_NAME**|**nvarchar (** 128 **)**|Если столбец имеет определяемый пользователем тип данных, то столбец является именем этого типа данных. Иначе возвращается значение NULL.|  
  
## <a name="remarks"></a>Remarks  
 Столбец **ORDINAL_POSITION** **INFORMATION_SCHEMA. Представление COLUMNs** несовместимо с битовым шаблоном столбцов, возвращаемых функцией COLUMNS_UPDATED. Чтобы получить битовый шаблон, совместимый с COLUMNS_UPDATED, необходимо сослаться на свойство **columnid** системной функции COLUMNPROPERTY при запросе **INFORMATION_SCHEMA. Представление СТОЛБЦОВ** . Пример:  
  
```  
USE AdventureWorks2012;  
GO  
SELECT TABLE_NAME, COLUMN_NAME, COLUMNPROPERTY(OBJECT_ID(TABLE_SCHEMA + '.' + TABLE_NAME), COLUMN_NAME, 'ColumnID') AS COLUMN_ID  
FROM AdventureWorks2012.INFORMATION_SCHEMA.COLUMNS  
WHERE TABLE_NAME = 'Person';  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [Системные представления &#40;&#41;Transact-SQL](https://msdn.microsoft.com/library/35a6161d-7f43-4e00-bcd3-3091f2015e90)   
 [Представления информационной схемы &#40;&#41;Transact-SQL](~/relational-databases/system-information-schema-views/system-information-schema-views-transact-sql.md)   
 [sys. syscharsets &#40;&#41;Transact-SQL](../../relational-databases/system-compatibility-views/sys-syscharsets-transact-sql.md)   
 [sys. Columns &#40;&#41;Transact-SQL](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md)   
 [sys. sql_modules &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-sql-modules-transact-sql.md)   
 [sys. Configurations &#40;&#41;Transact-SQL](../../relational-databases/system-catalog-views/sys-configurations-transact-sql.md)   
 [sys. Objects &#40;&#41;Transact-SQL](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)   
 [sys. types &#40;&#41;Transact-SQL](../../relational-databases/system-catalog-views/sys-types-transact-sql.md)   
 [COLUMNS_UPDATED &#40;Transact-SQL&#41;](../../t-sql/functions/columns-updated-transact-sql.md)  
  
  
