---
title: Преобразование типов данных (ядро СУБД) | Документы Майкрософт
ms.custom: ''
ms.date: 07/23/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
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
author: MikeRayMSFT
ms.author: mikeray
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: c129998db40a64507b119b8392abcb56cc119a8b
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68001685"
---
# <a name="data-type-conversion-database-engine"></a>Преобразование типов данных (ядро СУБД)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Преобразование типов данных происходит в следующих случаях:
-   При перемещении, сравнении или объединении данных одного объекта с данными другого объекта эти данные могут преобразовываться из одного типа в другой.  
-   При передаче в переменную программы данных из результирующего столбца [!INCLUDE[tsql](../../includes/tsql-md.md)], кода возврата или параметра вывода эти данные должны преобразовываться из системного типа данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в тип данных переменной.  
  
При взаимных преобразованиях переменных приложения и столбцов результирующих наборов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], кодов возврата, параметров и маркеров параметров поддерживаемые преобразования типов данных определяются API базы данных.
  
## <a name="implicit-and-explicit-conversion"></a>Явное и неявное преобразование
Преобразование типов данных бывает явным и неявным.
  
Неявное преобразование скрыто от пользователя. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] автоматически преобразует данные из одного типа в другой. Например, если **smallint** сравнивается с **int**, то перед сравнением **smallint** неявно преобразуется в **int**.
  
**GETDATE()** выполняет неявное преобразование в стиль даты 0. **SYSDATETIME()** выполняет неявное преобразование в стиль даты 21.
  
Явное преобразование выполняется с помощью функций CAST и CONVERT.
  
Функции [CAST и CONVERT](../../t-sql/functions/cast-and-convert-transact-sql.md) преобразуют значение (локальную переменную, столбец или выражение) из одного типа данных в другой. Например, приведенная ниже функция `CAST` преобразует числовое значение `$157.27` в строку символов `'157.27'`:
  
```sql
CAST ( $157.27 AS VARCHAR(10) )  
```  
  
Если программный код [!INCLUDE[tsql](../../includes/tsql-md.md)] должен соответствовать требованиям ISO, используйте функцию CAST вместо CONVERT. Использование функции CONVERT вместо CAST дает преимущество в дополнительной функциональности.
  
На следующей иллюстрации показаны все явные и неявные преобразования типов данных, допустимые для системных типов данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Это могут быть типы **xml**, **bigint** и **sql_variant**. При присваивании неявного преобразования из типа **sql_variant** не происходит, но неявное преобразование в тип **sql_variant** производится.
  
![Таблица преобразования типов данных](../../t-sql/data-types/media/lrdatahd.png "Таблица преобразования типов данных")
  
## <a name="data-type-conversion-behaviors"></a>Поведение преобразования типов данных
Некоторые виды явного и неявного преобразования типов данных не поддерживаются при преобразовании типа данных одного объекта [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в тип данных другого объекта. Например, значение типа **nchar** нельзя преобразовать в значение типа **image**. Тип данных **nchar** можно преобразовать в тип данных **binary** только явно. Неявное преобразование в **binary** не поддерживается. Однако тип данных **nchar** можно преобразовать в тип **nvarchar** как явно, так и неявно.
  
В следующих подразделах приведено описание процесса преобразования следующих типов данных:
  
 - [binary и varbinary (Transact-SQL)](../../t-sql/data-types/binary-and-varbinary-transact-sql.md)  
 - [datetime2 &#40;Transact-SQL&#41;](../../t-sql/data-types/datetime2-transact-sql.md)  
 - [Типы money и smallmoney (Transact-SQL)](../../t-sql/data-types/money-and-smallmoney-transact-sql.md)  
 - [bit (Transact-SQL)](../../t-sql/data-types/bit-transact-sql.md)  
 - [datetimeoffset (Transact-SQL)](../../t-sql/data-types/datetimeoffset-transact-sql.md)  
 - [smalldatetime (Transact-SQL)](../../t-sql/data-types/smalldatetime-transact-sql.md)  
 - [char и varchar (Transact-SQL)](../../t-sql/data-types/char-and-varchar-transact-sql.md)  
 - [decimal и numeric (Transact-SQL)](../../t-sql/data-types/decimal-and-numeric-transact-sql.md)  
 - [sql_variant (Transact-SQL)](../../t-sql/data-types/sql-variant-transact-sql.md)  
 - [date &#40;Transact-SQL&#41;](../../t-sql/data-types/date-transact-sql.md)  
 - [Типы данных float и real (Transact-SQL)](../../t-sql/data-types/float-and-real-transact-sql.md)  
 - [time (Transact-SQL)](../../t-sql/data-types/time-transact-sql.md)  
 - [datetime (Transact-SQL)](../../t-sql/data-types/datetime-transact-sql.md)  
 - [int, bigint, smallint и tinyint (Transact-SQL)](../../t-sql/data-types/int-bigint-smallint-and-tinyint-transact-sql.md)  
 - [uniqueidentifier (Transact-SQL)](../../t-sql/data-types/uniqueidentifier-transact-sql.md)  
  
###  <a name="converting-data-types-by-using-ole-automation-stored-procedures"></a>Преобразование типов данных с помощью хранимых процедур OLE-автоматизации  
Поскольку [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] использует типы данных [!INCLUDE[tsql](../../includes/tsql-md.md)], а OLE-автоматизация — типы данных [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)], хранимым процедурам OLE-автоматизации приходится преобразовывать данные, которыми они обмениваются.
  
В следующей таблице описываются преобразования типов данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в типы данных [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)].
  
|Тип данных SQL Server|Тип данных Visual Basic|  
|--------------------------|----------------------------|  
|**char**, **varchar**, **text**, **nvarchar**, **ntext**|**String**|  
|**decimal**, **numeric**|**String**|  
|**bit**|**Boolean**|  
|**binary**, **varbinary**, **image**|Одномерный массив **Byte()**|  
|**int**|**Long**|  
|**smallint**|**Integer**|  
|**tinyint**|**Byte**|  
|**float**|**Double**|  
|**real**|**Один**|  
|**money**, **smallmoney**|**Измерение валют**|  
|**datetime**, **smalldatetime**|**Дата**|  
|Все значения NULL|**Variant** со значением NULL|  
  
Все одиночные значения [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] преобразуются в одиночные значения [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)], за исключением **binary**, **varbinary** и **image**. В [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] эти значения преобразуются в одномерные массивы **Byte()** . Этот массив имеет диапазон **Byte(** от 0 до _length_ 1 **)** , где *length* — число байтов в значениях [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **binary**, **varbinary** или **image**.
  
Ниже приведена таблица преобразования типов данных [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] в типы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].
  
|Тип данных Visual Basic|Тип данных SQL Server|  
|----------------------------|--------------------------|  
|**Long**, **Integer**, **Byte**, **Boolean**, **Object**|**int**|  
|**Double**, **Single**|**float**|  
|**Измерение валют**|**money**|  
|**Дата**|**datetime**|  
|**String** длиной 4000 символов или меньше|**varchar**/**nvarchar**|  
|**String** длиной более 4000 символов|**text**/**ntext**|  
|Одномерный массив **Byte()** размером 8000 байт или меньше|**varbinary**|  
|Одномерный массив **Byte()** размером более 8000 байт|**image**|  
  
## <a name="see-also"></a>См. также раздел
[Хранимые процедуры OLE-автоматизации (Transact-SQL)](../../relational-databases/system-stored-procedures/ole-automation-stored-procedures-transact-sql.md)  
[Функции CAST и CONVERT (Transact-SQL)](../../t-sql/functions/cast-and-convert-transact-sql.md)  
[Типы данных (Transact-SQL)](../../t-sql/data-types/data-types-transact-sql.md)  
[COLLATE (Transact-SQL)](https://msdn.microsoft.com/library/4ba6b7d8-114a-4f4e-bb38-fe5697add4e9)
  
  
