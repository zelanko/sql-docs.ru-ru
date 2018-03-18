---
title: "uniqueidentifier (Transact-SQL) | Документы Майкрософт"
ms.custom: 
ms.date: 12/1/2017
ms.prod: sql-non-specified
ms.prod_service: sql-data-warehouse, database-engine, pdw, sql-database
ms.service: 
ms.component: t-sql|data-types
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- uniqueidentifier
- uniqueidentifier_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- uniqueidentifier data type
- globally unique identifiers [SQL Server]
- GUIDs [SQL Server]
ms.assetid: b026035b-f3d2-4d70-989d-3884b4ca0233
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: 76f7a3c784c0d05e1a6f94da0b33207bfbb1efec
ms.sourcegitcommit: 2208a909ab09af3b79c62e04d3360d4d9ed970a7
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2018
---
# <a name="uniqueidentifier-transact-sql"></a>uniqueidentifier (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-asdb-asdw-pdw-md.md)]

16-байтовый идентификатор GUID.
  
## <a name="remarks"></a>Remarks  
Столбец или локальную переменную типа **uniqueidentifier** можно инициализировать следующими способами:
-   с помощью функции [NEWID](../../t-sql/functions/newid-transact-sql.md) или [NEWSEQUENTIALID](../../t-sql/functions/newsequentialid-transact-sql.md);    
-   путем преобразования из строковой константы в виде *xxxxxxxx*-*xxxx*-*xxxx*-*xxxx*-*xxxxxxxxxxxx*, где каждому *x* соответствует шестнадцатеричная цифра (0–9 или A–F). Например, 6F9619FF-8B86-D011-B42D-00C04FC964FF является допустимым значением **uniqueidentifier**.  
  
Значения **uniqueidentifier** поддерживают операторы сравнения, однако их упорядочивание реализовано без использования поразрядного сравнения. Со значениями **uniqueidentifier** можно выполнять только операции сравнения (=, <>, \<, >, \<=, >=) и проверки значения NULL (IS NULL и IS NOT NULL). Никакие другие арифметические операторы не поддерживаются. К типу данных **uniqueidentifier** можно применять все ограничения и свойства столбцов, за исключением IDENTITY.
  
При репликации слиянием и репликации транзакций с обновляемыми подписками столбцы **uniqueidentifier** используются для уникальной идентификации строк в нескольких копиях таблицы.
  
## <a name="converting-uniqueidentifier-data"></a>Преобразование данных uniqueidentifier  
Тип **uniqueidentifier** считается символьным типом при преобразовании из символьного выражения, поэтому на него распространяются правила усечения при преобразовании в символьный тип. Это значит, что при преобразовании символьного выражения в символьный тип данных другой длины значения, слишком длинные для нового типа данных, усекаются. См. подраздел «Примеры» ниже.
  
## <a name="limitations-and-restrictions"></a>ограничения

Следующие средства и компоненты не поддерживают тип данных `uniqueidentifier`:
- PolyBase
- [Средство загрузки dwloader](https://msdn.microsoft.com/sql/analytics-platform-system/dwloader) для Parallel Data Warehouse

## <a name="examples"></a>Примеры  
В следующем примере значение `uniqueidentifier` преобразуется в тип данных `char`.
  
```sql
DECLARE @myid uniqueidentifier = NEWID();  
SELECT CONVERT(char(255), @myid) AS 'char';  
```  
  
Следующий пример показывает усечение данных, когда значение является слишком длинным для преобразования в заданный тип данных. Так как тип данных **uniqueidentifier** ограничен 36 символами, все символы, выходящие за пределы этой длины, будут усечены.
  
```sql
DECLARE @ID nvarchar(max) = N'0E984725-C51C-4BF4-9960-E1C80E27ABA0wrong';  
SELECT @ID, CONVERT(uniqueidentifier, @ID) AS TruncatedValue;  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
String                                       TruncatedValue  
-------------------------------------------- ------------------------------------  
0E984725-C51C-4BF4-9960-E1C80E27ABA0wrong    0E984725-C51C-4BF4-9960-E1C80E27ABA0  
  
(1 row(s) affected)  
```  
  
## <a name="see-also"></a>См. также раздел
[ALTER TABLE (Transact-SQL)](../../t-sql/statements/alter-table-transact-sql.md)  
[Функции CAST и CONVERT (Transact-SQL)](../../t-sql/functions/cast-and-convert-transact-sql.md)  
[CREATE TABLE (Transact-SQL)](../../t-sql/statements/create-table-transact-sql.md)  
[Типы данных (Transact-SQL)](../../t-sql/data-types/data-types-transact-sql.md)  
[DECLARE @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/declare-local-variable-transact-sql.md)  
[NEWID (Transact-SQL)](../../t-sql/functions/newid-transact-sql.md)  
[NEWSEQUENTIALID (Transact-SQL)](../../t-sql/functions/newsequentialid-transact-sql.md)    
[SET @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/set-local-variable-transact-sql.md)  
[Updatable Subscriptions for Transactional Replication](../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md)
  
  
