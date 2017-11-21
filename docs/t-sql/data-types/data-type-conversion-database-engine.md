---
title: "Тип данных преобразования (компонент Database Engine) | Документы Microsoft"
ms.custom: 
ms.date: 7/23/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|data-types
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- CAST function
- converting data types [SQL Server]
- CONVERT function
- data types [SQL Server], converting
- implicit data type conversions
- explicit data type conversions [SQL Server]
- converting data types [SQL Server], about converting data types
ms.assetid: ffacf45e-a488-48d0-9bb0-dcc7fd365299
caps.latest.revision: 37
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: c0ed7f8e0e681de9f962e3eb963c0af315a0c25c
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="data-type-conversion-database-engine"></a>Преобразование типов данных (ядро СУБД)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Преобразование типов данных происходит в следующих случаях:
-   При перемещении, сравнении или объединении данных одного объекта с данными другого объекта эти данные могут преобразовываться из одного типа в другой.  
-   Когда данные из [!INCLUDE[tsql](../../includes/tsql-md.md)] столбец результатов, код возврата или выходных параметров перемещается в переменной программы, данные должны быть преобразованы из [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] системного типа данных в тип данных переменной.  
  
При взаимных преобразованиях переменных приложения и столбцов результирующих наборов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], кодов возврата, параметров и маркеров параметров поддерживаемые преобразования типов данных определяются API базы данных.
  
## <a name="implicit-and-explicit-conversion"></a>Явные и неявные преобразования
Преобразование типов данных бывает явным и неявным.
  
Неявное преобразование скрыто от пользователя. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] автоматически преобразует данные из одного типа в другой. Например, если **smallint** сравнивается с **int**, **smallint** неявно преобразуется в **int** до сравнения продолжается.
  
**GETDATE()** неявно преобразуется в стиль даты 0. **SYSDATETIME()** неявно преобразуется в стиль даты 21.
  
Явное преобразование выполняется с помощью функций CAST и CONVERT.
  
[CAST и CONVERT](../../t-sql/functions/cast-and-convert-transact-sql.md) преобразуют значение (локальную переменную, столбец или другое выражение) из одного типа в другой. Например, приведенная ниже функция `CAST` преобразует числовое значение `$157.27` в строку символов `'157.27'`:
  
```sql
CAST ( $157.27 AS VARCHAR(10) )  
```  
  
Если программный код [!INCLUDE[tsql](../../includes/tsql-md.md)] должен соответствовать требованиям ISO, используйте функцию CAST вместо CONVERT. Использование функции CONVERT вместо CAST дает преимущество в дополнительной функциональности.
  
На следующей иллюстрации показаны все явные и неявные преобразования типов данных, допустимые для системных типов данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. К ним относятся **xml**, **bigint**, и **sql_variant**. Нет неявного преобразования на назначение на основе **sql_variant** тип данных, но существует неявное преобразование в **sql_variant**.
  
![Таблица преобразования типов данных](../../t-sql/data-types/media/lrdatahd.png "таблица преобразования типов данных")
  
## <a name="data-type-conversion-behaviors"></a>Поведение преобразования типов данных
Некоторые виды явного и неявного преобразования типов данных не поддерживаются при преобразовании типа данных одного объекта [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в тип данных другого объекта. Например **nchar** значение не может быть преобразовано **изображения** значение. **Nchar** можно преобразовать в **двоичных** с помощью явного преобразования к неявному преобразованию к **двоичных** не поддерживается. Тем не менее **nchar** могут явно или неявно преобразовываться в **nvarchar**.
  
В следующих подразделах приведено описание процесса преобразования следующих типов данных:
  
 - [binary и varbinary (Transact-SQL)](../../t-sql/data-types/binary-and-varbinary-transact-sql.md)  
 - [datetime2 &#40;Transact-SQL&#41;](../../t-sql/data-types/datetime2-transact-sql.md)  
 - [Money и smallmoney &#40; Transact-SQL &#41;](../../t-sql/data-types/money-and-smallmoney-transact-sql.md)  
 - [бит &#40; Transact-SQL &#41;](../../t-sql/data-types/bit-transact-sql.md)  
 - [datetimeoffset (Transact-SQL)](../../t-sql/data-types/datetimeoffset-transact-sql.md)  
 - [smalldatetime &#40; Transact-SQL &#41;](../../t-sql/data-types/smalldatetime-transact-sql.md)  
 - [char и varchar (Transact-SQL)](../../t-sql/data-types/char-and-varchar-transact-sql.md)  
 - [Decimal и numeric &#40; Transact-SQL &#41;](../../t-sql/data-types/decimal-and-numeric-transact-sql.md)  
 - [sql_variant (Transact-SQL)](../../t-sql/data-types/sql-variant-transact-sql.md)  
 - [date &#40;Transact-SQL&#41;](../../t-sql/data-types/date-transact-sql.md)  
 - [&#40; float и real Transact-SQL &#41;](../../t-sql/data-types/float-and-real-transact-sql.md)  
 - [раз &#40; Transact-SQL &#41;](../../t-sql/data-types/time-transact-sql.md)  
 - [DateTime &#40; Transact-SQL &#41;](../../t-sql/data-types/datetime-transact-sql.md)  
 - [int, bigint, smallint и tinyint &#40; Transact-SQL &#41;](../../t-sql/data-types/int-bigint-smallint-and-tinyint-transact-sql.md)  
 - [uniqueidentifier &#40; Transact-SQL &#41;](../../t-sql/data-types/uniqueidentifier-transact-sql.md)  
  
###  <a name="converting-data-types-by-using-ole-automation-stored-procedures"></a>Преобразование типов данных с помощью хранимых процедур OLE-автоматизации  
Поскольку [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] использует типы данных [!INCLUDE[tsql](../../includes/tsql-md.md)], а OLE-автоматизация — типы данных [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)], хранимым процедурам OLE-автоматизации приходится преобразовывать данные, которыми они обмениваются.
  
В следующей таблице описываются преобразования типов данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в типы данных [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)].
  
|Тип данных SQL Server|Тип данных Visual Basic|  
|--------------------------|----------------------------|  
|**char**, **varchar**, **текст**, **nvarchar**, **ntext**|**Строковые значения**|  
|**десятичное число**, **числовой**|**Строковые значения**|  
|**bit**|**Логическое значение**|  
|**двоичный**, **varbinary**, **изображения**|Одномерный массив **Byte()** массива|  
|**int**|**Long**|  
|**smallint**|**Целочисленный**|  
|**tinyint**|**Байт**|  
|**float**|**Double**|  
|**real**|**Один**|  
|**money**, **smallmoney**|**Измерение валют**|  
|**DateTime**, **smalldatetime**|**Дата**|  
|Все значения NULL|**Variant** присваивается значение Null|  
  
Все одиночные [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] значения преобразуются в один [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] значение, за исключением элемента **двоичных**, **varbinary**, и **изображения** значения. Эти значения преобразуются в одномерные **Byte()** массива в [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]. Этот массив имеет диапазон от **байт (**0, чтобы *длина*1**)** где *длина* число байтов в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  **двоичный**, **varbinary**, или **изображения** значения.
  
Ниже приведена таблица преобразования типов данных [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] в типы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].
  
|Тип данных Visual Basic|Тип данных SQL Server|  
|----------------------------|--------------------------|  
|**Длинное**, **целое**, **байтов**, **логическое**, **объекта**|**int**|  
|**Двойные**, **один**|**float**|  
|**Измерение валют**|**money**|  
|**Дата**|**datetime**|  
|**Строка** длиной 4000 символов или меньше|**varchar**/**nvarchar**|  
|**Строка** с более чем 4 000 символов|**текст**/**ntext**|  
|Одномерный массив **Byte()** массива размером 8 000 байт или меньше|**varbinary**|  
|Одномерный массив **Byte()** массива размером более 8 000 байт.|**image**|  
  
## <a name="see-also"></a>См. также:
[Хранимые процедуры OLE-автоматизации (Transact-SQL)](../../relational-databases/system-stored-procedures/ole-automation-stored-procedures-transact-sql.md)  
[Функции CAST и CONVERT (Transact-SQL)](../../t-sql/functions/cast-and-convert-transact-sql.md)  
[Типы данных (Transact-SQL)](../../t-sql/data-types/data-types-transact-sql.md)  
[COLLATE &#40; Transact-SQL &#41;](http://msdn.microsoft.com/library/4ba6b7d8-114a-4f4e-bb38-fe5697add4e9)
  
  

