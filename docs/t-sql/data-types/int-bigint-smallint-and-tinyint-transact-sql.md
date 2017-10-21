---
title: "int, bigint, smallint и tinyint (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 9/8/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- bigint_TSQL
- smallint
- bigint
- smallint_TSQL
- tinyint_TSQL
- int_TSQL
- int
- tinyint
dev_langs:
- TSQL
helpviewer_keywords:
- exact numeric data [SQL Server]
- numeric data
- tinyint data type
- int data type
- smallint data type
ms.assetid: 9bda5b0b-2380-4931-a1c8-f362fdefa99b
caps.latest.revision: 28
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 46ac51971b07b38b73ef18d8a953674fc77b4b17
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="int-bigint-smallint-and-tinyint-transact-sql"></a>int, bigint, smallint и tinyint (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Типы точных числовых данных, использующие целые значения. Для экономии места в базе данных, используйте наименьший тип данных, надежно может содержать все возможные значения. Например так как ни один живет быть более 255 лет tinyint будет достаточно для возраста лиц. Однако поскольку здания может быть более 255 лет tinyint не будет достаточно для возраста зданий.
  
|Тип данных|Диапазон|Память|  
|---|---|---|
|**bigint**|от -2^63 (-9 223 372 036 854 775 808) до 2^63-1 (9 223 372 036 854 775 807)|8 байт|  
|**int**|от -2^31 (-2 147 483 648) до 2^31-1 (2 147 483 647)|4 байта|  
|**smallint**|от -2^15 (-32 768) до 2^15-1 (32 767)|2 байта|  
|**tinyint**|От 0 до 255|1 байт|  
  
## <a name="remarks"></a>Замечания  
**Int** тип данных является основным типом целочисленных данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. **Bigint** тип данных предназначен для использования, когда целочисленные значения могут превышать диапазон, поддерживаемый **int** тип данных.
  
**bigint** располагается между **smallmoney** и **int** в таблице приоритетов типов данных.
  
Функции возвращают **bigint** только в том случае, если выражение параметра имеет **bigint** тип данных. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]не выполняет автоматического продвижения других целочисленных типов данных (**tinyint**, **smallint**, и **int**) для **bigint**.
  
> [!CAUTION]  
>  При использовании +, -, \*, /, или % арифметические операторы, которые выполняют неявное или явное преобразование из **int**, **smallint**, **tinyint**, или ** bigint** постоянных значений **float**, **реальные**, **десятичное** или **числовое** типы данных, правила [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] применяется при вычислении, тип данных и точности результатов выражения различаются в зависимости от того, является ли запрос автоматической параметризации или нет.  
>   
>  Поэтому одинаковые выражения в различных запросах могут иногда возвращать различные результаты. При отсутствии в запросе автоматической параметризации, константа сначала преобразуется в **числовое**, с точностью достаточен для хранения значения константы, перед преобразованием в указанный тип данных. Например, константа 1 преобразуется в **numeric (1, 0)**, а константа 250 — в **numeric (3, 0)**.  
>   
>  При запросе автоматической параметризации константа всегда преобразуется **numeric (10, 0)** перед преобразованием в данные конечного типа. При использовании оператора «/» могут различаться как точность, так и само значение результата. Например, результат автопараметризованного запроса, включающего в себя выражение `SELECT CAST (1.0 / 7 AS float)`, отличается от значения результат того же запроса, который не является автоматической параметризации, так как результаты запроса автоматической параметризации, усекаются в **numeric (10, 0)** тип данных.  
  
## <a name="converting-integer-data"></a>Преобразование целочисленных данных
При неявном преобразовании данных типа integer в данные типа character, если число слишком большое для символьного поля, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] вставляет символ с кодом ASCII 42 — звездочку (*).
  
Целочисленные константы, превышающие 2 147 483 647, преобразуются в **десятичное** тип данных, не **bigint** тип данных. В следующем примере показано, что при превышении порогового значения, тип данных результата переключается с **int** для **десятичное**.
  
```sql
SELECT 2147483647 / 2 AS Result1, 2147483649 / 2 AS Result2 ;  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
Result1      Result2  
1073741823   1073741824.500000  
```  
  
## <a name="examples"></a>Примеры  
В следующем примере создается таблица, использующая **bigint**, **int**, **smallint**, и **tinyint** типов данных. Значения вставляются в каждый столбец и возвращаются в инструкции SELECT.
  
```sql
CREATE TABLE dbo.MyTable  
(  
  MyBigIntColumn bigint  
,MyIntColumn  int
,MySmallIntColumn smallint
,MyTinyIntColumn tinyint
);  
  
GO  
  
INSERT INTO dbo.MyTable VALUES (9223372036854775807, 2147483647,32767,255);  
 GO  
SELECT MyBigIntColumn, MyIntColumn, MySmallIntColumn, MyTinyIntColumn  
FROM dbo.MyTable;  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
MyBigIntColumn       MyIntColumn MySmallIntColumn MyTinyIntColumn  
-------------------- ----------- ---------------- ---------------  
9223372036854775807  2147483647  32767            255  
  
(1 row(s) affected)  
```  
  
## <a name="see-also"></a>См. также:
[ALTER TABLE (Transact-SQL)](../../t-sql/statements/alter-table-transact-sql.md)  
[Функции CAST и CONVERT (Transact-SQL)](../../t-sql/functions/cast-and-convert-transact-sql.md)  
[CREATE TABLE (Transact-SQL)](../../t-sql/statements/create-table-transact-sql.md)  
[DECLARE @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/declare-local-variable-transact-sql.md)  
[SET @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/set-local-variable-transact-sql.md)  
[sys.types &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-types-transact-sql.md)
  
  

