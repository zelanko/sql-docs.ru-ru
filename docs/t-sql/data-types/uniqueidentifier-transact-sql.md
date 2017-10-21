---
title: "uniqueidentifier (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 7/23/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
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
caps.latest.revision: 39
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: d9a995f7d29fe91e14affa9266a9bce73acc9010
ms.openlocfilehash: 1450aa86e3f47ef27be5acd5b5410fe40dd5983e
ms.contentlocale: ru-ru
ms.lasthandoff: 09/27/2017

---
# <a name="uniqueidentifier-transact-sql"></a>uniqueidentifier (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-asdw-pdw-_md](../../includes/tsql-appliesto-ss2008-asdb-asdw-pdw-md.md)]

16-байтовый идентификатор GUID.
  
## <a name="remarks"></a>Замечания  
Столбец или локальную переменную **uniqueidentifier** типа данных можно инициализировать значение одним из следующих способов:
-   При помощи функции NEWID.  
-   Путем преобразования из строковой константы в форме *xxxxxxxx*-*xxxx*-*xxxx*-*xxxx* - *xxxxxxxxxxxx*, в котором каждый *x* представляет собой шестнадцатеричную цифру в диапазоне 0-9 или a-f. Например, 6F9619FF-8B86-D011-B42D-00C04FC964FF является допустимым **uniqueidentifier** значение.  
  
Операторы сравнения можно использовать с **uniqueidentifier** значения. однако их упорядочивание реализовано без использования поразрядного сравнения. Только операции, которые могут выполняться к **uniqueidentifier** значение — это сравнения (=, <>, \<, >, \<=, > =) и проверки на значение NULL (IS NULL и IS NOT NULL). Никакие другие арифметические операторы не поддерживаются. Все ограничения и свойства столбцов, за исключением ИДЕНТИФИКАТОРОВ, можно использовать на **uniqueidentifier** тип данных.
  
Репликация слиянием и репликация транзакций с обновляемыми подписками пользуются **uniqueidentifier** столбцы для обеспечения уникальной идентификации строк в нескольких копиях таблицы.
  
## <a name="converting-uniqueidentifier-data"></a>Преобразование данных uniqueidentifier  
**Uniqueidentifier** тип считается преобразовании символьного выражения в символьный тип и поэтому является распространяются правила усечения при преобразовании в символьный тип. Это значит, что при преобразовании символьного выражения в символьный тип данных другой длины значения, слишком длинные для нового типа данных, усекаются. См. подраздел «Примеры» ниже.
  
## <a name="limitations-and-restrictions"></a>ограничения

Эти средства и компоненты не поддерживают `uniqueidentifier` тип данных:
- PolyBase
- [Средство загрузке dwloader](https://msdn.microsoft.com/sql/analytics-platform-system/dwloader) для параллельного хранилища данных

## <a name="examples"></a>Примеры  
В следующем примере значение `uniqueidentifier` преобразуется в тип данных `char`.
  
```sql
DECLARE @myid uniqueidentifier = NEWID();  
SELECT CONVERT(char(255), @myid) AS 'char';  
```  
  
Следующий пример показывает усечение данных, когда значение является слишком длинным для преобразования в заданный тип данных. Поскольку **uniqueidentifier** ограничен 36 символов, символов, в которых превышает длину, усекаются.
  
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
  
## <a name="see-also"></a>См. также:
[ALTER TABLE (Transact-SQL)](../../t-sql/statements/alter-table-transact-sql.md)  
[Функции CAST и CONVERT (Transact-SQL)](../../t-sql/functions/cast-and-convert-transact-sql.md)  
[CREATE TABLE (Transact-SQL)](../../t-sql/statements/create-table-transact-sql.md)  
[Типы данных (Transact-SQL)](../../t-sql/data-types/data-types-transact-sql.md)  
[DECLARE @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/declare-local-variable-transact-sql.md)  
[NEWID &#40; Transact-SQL &#41;](../../t-sql/functions/newid-transact-sql.md)  
[NEWSEQUENTIALID &#40; Transact-SQL &#41; ](../../t-sql/functions/newsequentialid-transact-sql.md) 
 [ЗАДАТЬ @local_variable &#40; Transact-SQL &#41;](../../t-sql/language-elements/set-local-variable-transact-sql.md)  
[Updatable Subscriptions for Transactional Replication](../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md)
  
  

