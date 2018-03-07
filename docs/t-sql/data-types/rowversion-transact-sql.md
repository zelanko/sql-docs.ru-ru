---
title: "rowversion (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 7/22/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|data-types
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: 4a8a9c6a9ea076ec1727bfa5422a3dfbda58386c
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="rowversion-transact-sql"></a>rowversion (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Тип данных, который представляет собой автоматически сформированные уникальные двоичные числа в базе данных. **rowversion** обычно используется в качестве механизма для отметки версий строк таблицы. Размер при хранении составляет 8 байт. **Rowversion** тип данных представляет собой увеличивающееся число и не сохраняет дату или время. Для записи даты или времени, используйте **datetime2** тип данных.
  
## <a name="remarks"></a>Замечания  
Каждая база данных имеет счетчик, который увеличивается при каждой операции вставки или операции обновления, который выполняется на таблицу, содержащую **rowversion** столбца в базе данных. Этот счетчик типа rowversion используется для работы с базами данных. Происходит отслеживание относительного времени базы данных, а не действительного времени, которое может быть связано с часами. Таблица может иметь только один **rowversion** столбца. Каждый раз, создается строка с **rowversion** столбца при изменении или вставке, значение увеличенной rowversion вставляется в **rowversion** столбца. Это свойство позволяет **rowversion** столбца нежелательно использовать в ключе, особенно в первичном ключе. Любое обновление, сделанное в строке, изменяет значение rowversion и значение ключа. Если столбец является первичным ключом, старое значение ключа больше недействительно и внешние ключи, ссылающиеся на старое значение, становятся недействительными. Если на таблицу ссылается динамический курсор, все обновления изменяют положение строк в курсоре. Если столбец является ключом индекса, все обновления в строках данных также приводят к обновлению индекса.  **Rowversion** значение увеличивается с любой инструкции update, даже если значения строк не изменяются. (Например, если значение столбца равно 5, а инструкция update присваивает значение 5, это действие считается обновление несмотря на то, что не изменился и **rowversion** увеличивается.)
  
**Отметка времени** является синонимом **rowversion** тип данных и подчиняется правилам поведения данных синонимы типов. В инструкциях DDL используйте **rowversion** вместо **timestamp** везде, где это возможно. Дополнительные сведения см. в разделе [синонимы типов данных &#40; Transact-SQL &#41; ](../../t-sql/data-types/data-type-synonyms-transact-sql.md).
  
[!INCLUDE[tsql](../../includes/tsql-md.md)] **Timestamp** тип данных отличается от **timestamp** типом данных, определенным в стандарте ISO.
  
> [!NOTE]  
>  **Timestamp** синтаксис является устаревшим. [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
В инструкции CREATE TABLE или ALTER TABLE не нужно указывать имя столбца для **timestamp** тип данных, например:
  
```sql
CREATE TABLE ExampleTable (PriKey int PRIMARY KEY, timestamp);  
```  
  
Если вы не укажете имя столбца, [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] приводит к возникновению ошибки **timestamp** имя столбца, однако **rowversion** синоним не ведут себя следующим образом. При использовании **rowversion**, необходимо указать имя столбца, например:
  
```sql
CREATE TABLE ExampleTable2 (PriKey int PRIMARY KEY, VerCol rowversion) ;  
```  
  
> [!NOTE]  
>  Дублирование **rowversion** значения могут формироваться с помощью инструкции SELECT INTO, в которой **rowversion** столбец находится в списке ВЫБОРА. Мы не рекомендуем использовать **rowversion** таким образом.  
  
Не допускающий значения NULL **rowversion** семантически эквивалентен столбцу **binary(8)** столбца. Допускает значения NULL **rowversion** семантически эквивалентен столбцу **varbinary(8)** столбца.
  
Можно использовать **rowversion** столбец строки, чтобы легко определить, был ли строка инструкции update выполняли для его после последнего прочтения. Если инструкция update выполняли для строки, значение rowversion обновляется. Если не обновить инструкции, выполняли для строки, значение rowversion будет таким же, как если они были получены ранее. Чтобы получить текущее значение rowversion для базы данных, используйте [@@DBTS](../../t-sql/functions/dbts-transact-sql.md).
  
Можно добавить **rowversion** столбца в таблице, чтобы обеспечить целостность базы данных, когда несколько пользователей обновляют строки одновременно. Также может возникнуть необходимость в данных о количестве строк и указании обновленных строк без отправки повторного запроса в таблицу.
  
Например, допустим, что была создана таблица с именем `MyTest`. Заполнить некоторые данные в таблице с помощью следующих [!INCLUDE[tsql](../../includes/tsql-md.md)] инструкции.
  
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
    AND RV = myValue;  
IF (SELECT COUNT(*) FROM @t) = 0  
    BEGIN  
        RAISERROR ('error changing row with myKey = %d'  
            ,16 -- Severity.  
            ,1 -- State   
            ,1) -- myKey that was changed   
    END;  
```  
  
`myValue`— **rowversion** значение столбца для строки, которая указывает время последнего чтения строки. Это значение должно заменяться фактическим **rowversion** значение. Примером фактического **rowversion** значения является 0x00000000000007D3.
  
В транзакцию можно также ввести эти образцы инструкций [!INCLUDE[tsql](../../includes/tsql-md.md)]. При запросе переменной `@t` в области действия транзакции можно получить обновленный столбец `myKey` таблицы без отправки повторного запроса в таблицу `MyTes`.
  
Ниже приведен тот же пример с использованием **timestamp** синтаксис:
  
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
    AND TS = myValue;  
IF (SELECT COUNT(*) FROM @t) = 0  
    BEGIN  
        RAISERROR ('error changing row with myKey = %d'  
            ,16 -- Severity.  
            ,1 -- State   
            ,1) -- myKey that was changed   
    END;  
```  
  
## <a name="see-also"></a>См. также:
[ALTER TABLE (Transact-SQL)](../../t-sql/statements/alter-table-transact-sql.md)  
[Функции CAST и CONVERT (Transact-SQL)](../../t-sql/functions/cast-and-convert-transact-sql.md)  
[CREATE TABLE (Transact-SQL)](../../t-sql/statements/create-table-transact-sql.md)  
[Типы данных (Transact-SQL)](../../t-sql/data-types/data-types-transact-sql.md)  
[DECLARE @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/declare-local-variable-transact-sql.md)  
[DELETE (Transact-SQL)](../../t-sql/statements/delete-transact-sql.md)  
[INSERT (Transact-SQL)](../../t-sql/statements/insert-transact-sql.md)  
[MIN_ACTIVE_ROWVERSION &#40; Transact-SQL &#41;](../../t-sql/functions/min-active-rowversion-transact-sql.md)  
[SET @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/set-local-variable-transact-sql.md)  
[UPDATE (Transact-SQL)](../../t-sql/queries/update-transact-sql.md)
  
  
