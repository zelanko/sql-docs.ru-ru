---
title: ПРОЦЕДУРЫ (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- ROUTINES_TSQL
- ROUTINES
dev_langs:
- TSQL
helpviewer_keywords:
- ROUTINES view
- INFORMATION_SCHEMA.ROUTINES view
ms.assetid: c75561b2-c9a1-48a1-9afa-a5896b6454cf
caps.latest.revision: 50
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 00ec03e10cd41e964c9687f04478e05871de5b68
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="routines-transact-sql"></a>ROUTINES (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Возвращает одну строку для каждой хранимой процедуры и функции, к которым текущий пользователь может получить доступ в текущей базе данных. Столбцы, описывающие возвращаемое значение, относятся только к функциям. Для хранимых процедур эти столбцы будут иметь значение NULL.  
  
 Чтобы получить сведения из этих представлений, укажите полное имя INFORMATION_SCHEMA. *view_name*.  
  
> [!NOTE]  
>  Столбец ROUTINE_DEFINITION включает исходные инструкции, создавшие эту функцию или хранимую процедуру. Эти исходные инструкции, вероятно, содержат встроенные символы возврата каретки. Если этот столбец возвращается приложению, которое выводит результаты в текстовом формате, эти встроенные символы в результатах ROUTINE_DEFINITION могут нарушить форматирование общего результирующего набора. Если выбирается столбец ROUTINE_DEFINITION, необходимо учитывать встроенные символы возврата каретки, например возвращая результирующий набор в сетку или выводя результаты ROUTINE_DEFINITION в собственное текстовое поле.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|SPECIFIC_CATALOG|**nvarchar (** 128 **)**|Определенное имя каталога. Это имя совпадает с ROUTINE_CATALOG.|  
|SPECIFIC_SCHEMA|**nvarchar (** 128 **)**|Определенное имя схемы.<br /><br /> **\*\* Важные \* \***  не используйте представления INFORMATION_SCHEMA, чтобы определить схему объекта. Единственный надежный способ найти схему объекта — направить запрос к представлению каталога sys.objects.|  
|SPECIFIC_NAME|**nvarchar (** 128 **)**|Определенное имя каталога. Это имя совпадает с ROUTINE_NAME.|  
|ROUTINE_CATALOG|**nvarchar (** 128 **)**|Имя каталога функции.|  
|ROUTINE_SCHEMA|**nvarchar (** 128 **)**|Имя схемы, содержащей эту функцию.<br /><br /> **\*\* Важные \* \***  не используйте представления INFORMATION_SCHEMA, чтобы определить схему объекта. Единственный надежный способ найти схему объекта — направить запрос к представлению каталога sys.objects.|  
|ROUTINE_NAME|**nvarchar (** 128 **)**|Имя функции.|  
|ROUTINE_TYPE|**nvarchar (** 20 **)**|Возвращает значение PROCEDURE для хранимой процедуры и FUNCTION для функций.|  
|MODULE_CATALOG|**nvarchar (** 128 **)**|NULL. Зарезервировано для последующего использования.|  
|MODULE_SCHEMA|**nvarchar (** 128 **)**|NULL. Зарезервировано для последующего использования.|  
|MODULE_NAME|**nvarchar (** 128 **)**|NULL. Зарезервировано для последующего использования.|  
|UDT_CATALOG|**nvarchar (** 128 **)**|NULL. Зарезервировано для последующего использования.|  
|UDT_SCHEMA|**nvarchar (** 128 **)**|NULL. Зарезервировано для последующего использования.|  
|UDT_NAME|**nvarchar (** 128 **)**|NULL. Зарезервировано для последующего использования.|  
|DATA_TYPE|**nvarchar (** 128 **)**|Тип данных возвращаемого значения функции. Возвращает **таблицы** Если табличную функцию.|  
|CHARACTER_MAXIMUM_LENGTH|**int**|Максимальная длина в символах, если возвращаемый тип символьный.<br /><br /> -1 для **xml** и данные типов больших значений.|  
|CHARACTER_OCTET_LENGTH|**int**|Максимальная длина в байтах, если возвращаемый тип символьный.<br /><br /> -1 для **xml** и данные типов больших значений.|  
|COLLATION_CATALOG|**nvarchar (** 128 **)**|Всегда возвращает значение NULL.|  
|COLLATION_SCHEMA|**nvarchar (** 128 **)**|Всегда возвращает значение NULL.|  
|COLLATION_NAME|**nvarchar (** 128 **)**|Имя параметров сортировки для возвращаемого значения. Для несимвольных типов возвращает значение NULL.|  
|CHARACTER_SET_CATALOG|**nvarchar (** 128 **)**|Всегда возвращает значение NULL.|  
|CHARACTER_SET_SCHEMA|**nvarchar (** 128 **)**|Всегда возвращает значение NULL.|  
|CHARACTER_SET_NAME|**nvarchar (** 128 **)**|Имя кодировки возвращаемого значения. Для несимвольных типов возвращает значение NULL.|  
|NUMERIC_PRECISION|**smallint**|Точность возвращаемого значения. Для нечисловых типов возвращает значение NULL.|  
|NUMERIC_PRECISION_RADIX|**smallint**|Основание системы счисления для точности возвращаемого значения. Для нецифровых типов возвращает значение NULL.|  
|NUMERIC_SCALE|**smallint**|Масштаб возвращаемого значения. Для нецифровых типов возвращает значение NULL.|  
|DATETIME_PRECISION|**smallint**|Точность в долях секунды, если возвращаемое значение имеет тип **datetime**. В противном случае возвращается значение NULL.|  
|INTERVAL_TYPE|**nvarchar (** 30 **)**|NULL. Зарезервировано для последующего использования.|  
|INTERVAL_PRECISION|**smallint**|NULL. Зарезервировано для последующего использования.|  
|TYPE_UDT_CATALOG|**nvarchar (** 128 **)**|NULL. Зарезервировано для последующего использования.|  
|TYPE_UDT_SCHEMA|**nvarchar (** 128 **)**|NULL. Зарезервировано для последующего использования.|  
|TYPE_UDT_NAME|**nvarchar (** 128 **)**|NULL. Зарезервировано для последующего использования.|  
|SCOPE_CATALOG|**nvarchar (** 128 **)**|NULL. Зарезервировано для последующего использования.|  
|SCOPE_SCHEMA|**nvarchar (** 128 **)**|NULL. Зарезервировано для последующего использования.|  
|SCOPE_NAME|**nvarchar (** 128 **)**|NULL. Зарезервировано для последующего использования.|  
|MAXIMUM_CARDINALITY|**bigint**|NULL. Зарезервировано для последующего использования.|  
|DTD_IDENTIFIER|**nvarchar (** 128 **)**|NULL. Зарезервировано для последующего использования.|  
|ROUTINE_BODY|**nvarchar (** 30 **)**|Возвращает значение SQL для функции [!INCLUDE[tsql](../../includes/tsql-md.md)] и EXTERNAL для функции, написанной внешними средствами.<br /><br /> Функции всегда SQL.|  
|ROUTINE_DEFINITION|**nvarchar (** 4000 **)**|Возвращает первые 4 000 символов текста определения функции или хранимой процедуры, если они не зашифрованы. В противном случае возвращается значение NULL.<br /><br /> Чтобы убедиться, что получено полное определение, запрос [OBJECT_DEFINITION](../../t-sql/functions/object-definition-transact-sql.md) функции или в определении столбца [sys.sql_modules](../../relational-databases/system-catalog-views/sys-sql-modules-transact-sql.md) представления каталога.|  
|EXTERNAL_NAME|**nvarchar (** 128 **)**|NULL. Зарезервировано для последующего использования.|  
|EXTERNAL_LANGUAGE|**nvarchar (** 30 **)**|NULL. Зарезервировано для последующего использования.|  
|PARAMETER_STYLE|**nvarchar (** 30 **)**|NULL. Зарезервировано для последующего использования.|  
|IS_DETERMINISTIC|**nvarchar (** 10 **)**|Возвращает «YES», если процедура детерминированная.<br /><br /> Возвращает «NO», если процедура недетерминированная.<br /><br /> Всегда возвращает «NO» для хранимых процедур.|  
|SQL_DATA_ACCESS|**nvarchar (** 30 **)**|Возвращает одно из следующих значений:<br /><br /> NONE = функция не содержит SQL;<br /><br /> CONTAINS = функция может содержать SQL;<br /><br /> READS = функция, возможно, считывает данные SQL;<br /><br /> MODIFIES = функция, возможно, изменяет данные SQL.<br /><br /> Возвращает READS для всех функций и MODIFIES для всех хранимых процедур.|  
|IS_NULL_CALL|**nvarchar (** 10 **)**|Указывает, будет ли вызываться процедура, если один из ее аргументов равен NULL.|  
|SQL_PATH|**nvarchar (** 128 **)**|NULL. Зарезервировано для последующего использования.|  
|SCHEMA_LEVEL_ROUTINE|**nvarchar (** 10 **)**|Возвращает «YES», если это функция уровня схемы, или «NO» в противном случае.<br /><br /> Всегда возвращает «YES».|  
|MAX_DYNAMIC_RESULT_SETS|**smallint**|Максимальное число динамических результирующих наборов, возвращаемых процедурой.<br /><br /> Возвращает 0, если функция.|  
|IS_USER_DEFINED_CAST|**nvarchar (** 10 **)**|Возвращает «YES», если это пользовательская функция приведения, и «NO» в противном случае.<br /><br /> Всегда возвращает NO.|  
|IS_IMPLICITLY_INVOCABLE|**nvarchar (** 10 **)**|Возвращает «YES», если процедуру можно вызвать неявно, и «NO» в противном случае.<br /><br /> Всегда возвращает NO.|  
|CREATED|**datetime**|Время создания процедуры.|  
|LAST_ALTERED|**datetime**|Время последнего изменения функции.|  
  
## <a name="see-also"></a>См. также  
 [Системные представления &#40;Transact-SQL&#41;](http://msdn.microsoft.com/library/35a6161d-7f43-4e00-bcd3-3091f2015e90)   
 [Представления информационной схемы &#40;Transact-SQL&#41;](~/relational-databases/system-information-schema-views/system-information-schema-views-transact-sql.md)   
 [sys.columns (Transact-SQL)](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md)   
 [sys.objects (Transact-SQL)](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)   
 [sys.procedures (Transact-SQL)](../../relational-databases/system-catalog-views/sys-procedures-transact-sql.md)   
 [sys.sql_modules (Transact-SQL)](../../relational-databases/system-catalog-views/sys-sql-modules-transact-sql.md)  
  
  
