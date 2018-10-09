---
title: rowversion (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 7/22/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- timestamp_TSQL
- timestamp
dev_langs:
- TSQL
helpviewer_keywords:
- rowversion data type
- size [SQL Server], rowversion
- row version-stamping [SQL Server]
- rowversion columns
- version-stamping table rows
- unique rowversion numbers
- unique timestamp numbers
- timestamp data type
- timestamp columns
- size [SQL Server], timestamp
ms.assetid: 65c9cf0e-3e8a-45f8-87b3-3460d96afb0b
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 4591593408a6cbafb2f6a64b790403fd72cb97b4
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47807062"
---
# <a name="rowversion-transact-sql"></a>rowversion (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Тип данных, который представляет собой автоматически сформированные уникальные двоичные числа в базе данных. Тип данных **rowversion** используется в основном в качестве механизма для отметки версий строк таблицы. Размер при хранении составляет 8 байт. Тип данных **rowversion** представляет собой увеличивающееся число, которое не сохраняет дату или время. Для записи даты или времени используйте тип данных **datetime2**.
  
## <a name="remarks"></a>Remarks  
Каждая база данных имеет счетчик, который увеличивается при каждой операции вставки или обновления в таблице, содержащей столбец типа **rowversion** в базе данных. Этот счетчик типа rowversion используется для работы с базами данных. Происходит отслеживание относительного времени базы данных, а не действительного времени, которое может быть связано с часами. В таблице может быть только один столбец типа **rowversion**. Каждый раз при изменении или вставке строки, содержащей столбец типа **rowversion**, увеличенное значение rowversion вставляется в столбец типа **rowversion**. Из-за этого свойства столбец типа **rowversion** нежелательно использовать в качестве ключа, особенно первичного. Любое обновление, сделанное в строке, изменяет значение rowversion и значение ключа. Если столбец является первичным ключом, старое значение ключа больше недействительно и внешние ключи, ссылающиеся на старое значение, становятся недействительными. Если на таблицу ссылается динамический курсор, все обновления изменяют положение строк в курсоре. Если столбец является ключом индекса, все обновления в строках данных также приводят к обновлению индекса.  Значение **rowversion** увеличивается при каждом выполнении инструкции обновления, даже если значения в строке не изменяются. (Например, если значение в столбце равно 5 и инструкция обновления задает значение 5, это действие считается обновлением, несмотря на отсутствие изменений и значение **rowversion** увеличивается.)
  
Тип данных **timestamp** является синонимом типа данных **rowversion** и подчиняется правилам поведения синонимов типов данных. В инструкциях на языке описания данных DDL по возможности используйте **rowversion** вместо **timestamp**. Дополнительные сведения см. в статье [Синонимы типов данных (Transact-SQL)](../../t-sql/data-types/data-type-synonyms-transact-sql.md).
  
Тип данных [!INCLUDE[tsql](../../includes/tsql-md.md)] **timestamp** отличается от типа данных **timestamp**, определенного в стандарте ISO.
  
> [!NOTE]  
>  Синтаксис **timestamp** является нерекомендуемым. [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
В инструкции CREATE TABLE или ALTER TABLE необязательно указывать имя столбца с типом данных **timestamp**. Рассмотрим пример.
  
```sql
CREATE TABLE ExampleTable (PriKey int PRIMARY KEY, timestamp);  
```  
  
Если имя столбца не указать, [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] формирует имя столбца типа **timestamp**. Синоним **rowversion** не подчиняется этому правилу. При использовании типа данных **rowversion** указание имени столбца обязательно.
  
```sql
CREATE TABLE ExampleTable2 (PriKey int PRIMARY KEY, VerCol rowversion) ;  
```  
  
> [!NOTE]  
>  При использовании инструкции SELECT INTO, в которой столбец типа **rowversion** находится в списке SELECT, могут быть сформированы повторяющиеся значения **rowversion**. Использовать тип данных **rowversion** таким образом не рекомендуется.  
  
Столбец типа **rowversion**, который не может принимать значение NULL, семантически эквивалентен столбцу типа **binary(8)**. Столбец типа **rowversion**, который может принимать значение NULL, семантически эквивалентен столбцу типа **varbinary(8)**.
  
С помощью столбца **rowversion** можно легко определить, выполнялась ли инструкция обновления применительно к строке с момента ее последнего считывания. При выполнении инструкции обновления применительно к строке значение rowversion изменяется. Если для строки не выполнялись инструкции обновления, значение rowversion будет таким же, как и при предыдущем считывании. Чтобы получить текущее значение rowversion для базы данных, используйте функцию [@@DBTS](../../t-sql/functions/dbts-transact-sql.md).
  
Столбец **rowversion** можно добавить в таблицу, чтобы обеспечить целостность базы данных в случаях одновременного обновления строк несколькими пользователями. Также может возникнуть необходимость в данных о количестве строк и указании обновленных строк без отправки повторного запроса в таблицу.
  
Например, допустим, что была создана таблица с именем `MyTest`. Таблица заполняется данными при выполнении следующих инструкций [!INCLUDE[tsql](../../includes/tsql-md.md)].
  
```sql
CREATE TABLE MyTest (myKey int PRIMARY KEY  
    ,myValue int, RV rowversion);  
GO   
INSERT INTO MyTest (myKey, myValue) VALUES (1, 0);  
GO   
INSERT INTO MyTest (myKey, myValue) VALUES (2, 0);  
GO  
```  
  
После этого можно использовать следующие инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)] для управления оптимистичным параллелизмом таблицы `MyTest` при обновлении таблицы.
  
```sql
DECLARE @t TABLE (myKey int);  
UPDATE MyTest  
SET myValue = 2  
    OUTPUT inserted.myKey INTO @t(myKey)   
WHERE myKey = 1   
    AND RV = myRv;  
IF (SELECT COUNT(*) FROM @t) = 0  
    BEGIN  
        RAISERROR ('error changing row with myKey = %d'  
            ,16 -- Severity.  
            ,1 -- State   
            ,1) -- myKey that was changed   
    END;  
```  
  
`myRv` является значением столбца **rowversion** для строки, которое указывает время последнего считывания строки. Это значение должно заменяться фактическим значением **rowversion**. Примером фактического значения **rowversion** является 0x00000000000007D3.
  
В транзакцию можно также ввести эти образцы инструкций [!INCLUDE[tsql](../../includes/tsql-md.md)]. При запросе переменной `@t` в области действия транзакции можно получить обновленный столбец `myKey` таблицы без отправки повторного запроса в таблицу `MyTes`.
  
Ниже приведен тот же пример с использованием синтаксиса **timestamp**.
  
```sql
CREATE TABLE MyTest2 (myKey int PRIMARY KEY  
    ,myValue int, TS timestamp);  
GO   
INSERT INTO MyTest2 (myKey, myValue) VALUES (1, 0);  
GO   
INSERT INTO MyTest2 (myKey, myValue) VALUES (2, 0);  
GO  
DECLARE @t TABLE (myKey int);  
UPDATE MyTest2  
SET myValue = 2  
    OUTPUT inserted.myKey INTO @t(myKey)   
WHERE myKey = 1   
    AND TS = myTS;  
IF (SELECT COUNT(*) FROM @t) = 0  
    BEGIN  
        RAISERROR ('error changing row with myKey = %d'  
            ,16 -- Severity.  
            ,1 -- State   
            ,1) -- myKey that was changed   
    END;  
```  
  
## <a name="see-also"></a>См. также раздел
[ALTER TABLE (Transact-SQL)](../../t-sql/statements/alter-table-transact-sql.md)  
[Функции CAST и CONVERT (Transact-SQL)](../../t-sql/functions/cast-and-convert-transact-sql.md)  
[CREATE TABLE (Transact-SQL)](../../t-sql/statements/create-table-transact-sql.md)  
[Типы данных (Transact-SQL)](../../t-sql/data-types/data-types-transact-sql.md)  
[DECLARE @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/declare-local-variable-transact-sql.md)  
[DELETE (Transact-SQL)](../../t-sql/statements/delete-transact-sql.md)  
[INSERT (Transact-SQL)](../../t-sql/statements/insert-transact-sql.md)  
[MIN_ACTIVE_ROWVERSION (Transact-SQL)](../../t-sql/functions/min-active-rowversion-transact-sql.md)  
[SET @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/set-local-variable-transact-sql.md)  
[UPDATE (Transact-SQL)](../../t-sql/queries/update-transact-sql.md)
  
  
