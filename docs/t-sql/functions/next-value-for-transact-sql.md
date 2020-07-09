---
title: NEXT VALUE FOR (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 07/19/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- NEXT_VALUE_TSQL
- NEXT
- NEXT VALUE
- NEXT VALUE FOR
- NEXT_TSQL
- NEXT_VALUE_FOR_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- NEXT VALUE FOR function
- sequence number object, NEXT VALUE FOR function
ms.assetid: 92632ed5-9f32-48eb-be28-a5e477ef9076
author: julieMSFT
ms.author: jrasnick
ms.openlocfilehash: e7d813bf74f1779a2f9c04a2f78988cbab121c61
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85784379"
---
# <a name="next-value-for-transact-sql"></a>NEXT VALUE FOR (Transact-SQL)
[!INCLUDE [SQL Server Azure SQL Database ](../../includes/applies-to-version/sql-asdb.md)]

  Формирует номер последовательности из указанного объекта последовательности.  
  
 Полное описание создания и использования последовательностей см. в разделе [Последовательности чисел](../../relational-databases/sequence-numbers/sequence-numbers.md). Используйте [sp_sequence_get_range](../../relational-databases/system-stored-procedures/sp-sequence-get-range-transact-sql.md), чтобы создать резерв диапазона порядковых номеров.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
NEXT VALUE FOR [ database_name . ] [ schema_name . ]  sequence_name  
   [ OVER (<over_order_by_clause>) ]  
```  
  
## <a name="arguments"></a>Аргументы  
 *database_name*  
 Имя базы данных, содержащей объект последовательности.  
  
 *schema_name*  
 Имя схемы, содержащей объект последовательности.  
  
 *sequence_name*  
 Имя последовательности, содержащей объект, который формирует номер.  
  
 *over_order_by_clause*  
 Определяет порядок, в котором значение последовательности присваивается строкам в секции. Дополнительные сведения см. в статье [Предложение OVER (Transact-SQL)](../../t-sql/queries/select-over-clause-transact-sql.md).  
  
## <a name="return-types"></a>Типы возвращаемых данных  
 Возвращает число с использованием типа последовательности.  
  
## <a name="remarks"></a>Remarks  
 Функция **NEXT VALUE FOR** может использоваться в хранимых процедурах и триггерах.  
  
 Когда функция **NEXT VALUE FOR** используется в запросе или ограничении по умолчанию, если один и тот же объект последовательности используется несколько раз либо если один и тот же объект последовательности используется и в инструкции, поставляющей значения, и в выполняемом ограничении по умолчанию, то для всех столбцов, ссылающихся на одну последовательность в пределах строки в результирующем наборе, возвращается одно и то же значение.  
  
 Функция **NEXT VALUE FOR** является недетерминированной и допустима только в тех контекстах, в которых номера из формируемой последовательности правильно определены. Ниже приводятся определения того, как много значений будет использовано для каждого из упоминаемых объектов последовательности в данной инструкции:  
  
-   **SELECT** — для каждого указанного объекта последовательности новое значение формируется один раз для каждой строки результата выполнения инструкции.  
  
-   **INSERT** ... **VALUES** — для каждого указанного объекта последовательности новое значение формируется один раз для каждой вставленной строки в инструкции.  
  
-   **UPDATE** — для каждого указанного объекта последовательности новое значение формируется один раз для каждой строки, обновляемой в инструкции.  
  
-   Процедурные инструкции (**DECLARE**, **SET** и т. д.) — для каждого указанного объекта последовательности новое значение формируется для каждой инструкции.  
  
## <a name="limitations-and-restrictions"></a>Ограничения  
 Функция **NEXT VALUE FOR** не может использоваться в следующих случаях:  
  
-   Если база данных находится в режиме только для чтения.  
  
-   В качестве аргумента функции с табличным значением.  
  
-   В качестве аргумента агрегатной функции.  
  
-   Во вложенных запросах, включающих обобщенные табличные выражения и производные таблицы.  
  
-   В представлениях, определяемых пользователем функциях, вычисляемых столбцах.  
  
-   В инструкциях с операторами **DISTINCT**, **UNION**, **UNION ALL**, **EXCEPT** или **INTERSECT**.  
  
-   В инструкциях с предложением **ORDER BY**, если не используется **NEXT VALUE FOR** ... **OVER** (**ORDER BY** ...).  
  
-   В следующих предложениях: **FETCH**, **OVER**, **OUTPUT**, **ON**, **PIVOT**, **UNPIVOT**, **GROUP BY**, **HAVING**, **COMPUTE**, **COMPUTE BY** или **FOR XML**.  
  
-   В условных выражениях с использованием **CASE**, **CHOOSE**, **COALESCE**, **IIF**, **ISNULL** или **NULLIF**.  
  
-   В предложении **VALUES**, которое не является частью инструкции **INSERT**.  
  
-   В определении проверочного ограничения.  
  
-   В определении правила или объекта "значение по умолчанию". (Может использоваться в ограничении по умолчанию.)  
  
-   Используется по умолчанию в определяемом пользователем типе.  
  
-   В инструкции, в которой используется **TOP** или **OFFSET**, или при установке параметра **ROWCOUNT**.  
  
-   В предложении **WHERE** инструкции.  
  
-   В инструкции **MERGE**. (За исключением случая, когда функция **NEXT VALUE FOR** используется в ограничении по умолчанию в целевой таблице, а ограничение по умолчанию используется в инструкции **CREATE** из инструкции **MERGE**.)  
  
## <a name="using-a-sequence-object-in-a-default-constraint"></a>Использование объекта последовательности в ограничении по умолчанию  
 При использовании функции **NEXT VALUE FOR** в ограничении по умолчанию действуют следующие правила:  
  
-   Один объект последовательности может указываться из ограничений по умолчанию нескольких таблиц.  
  
-   Таблица и объект последовательности должны находиться в одной и той же базе данных.  
  
-   Пользователь, добавляющий ограничение по умолчанию, должен иметь разрешение REFERENCES для объекта последовательности.  
  
-   Объект последовательности, указанный из ограничения по умолчанию, не может быть удален до тех пор, пока не удалено само ограничение по умолчанию.  
  
-   Если один и тот же объект последовательности указан в нескольких ограничениях по умолчанию либо и в инструкции, поставляющей значения, и в выполняемом ограничении по умолчанию, то для всех столбцов в строке возвращается один и тот же номер последовательности.  
  
-   В ссылке на функцию **NEXT VALUE FOR** в ограничении по умолчанию не может быть указано предложение **OVER**.  
  
-   Объект последовательности, указанный в ограничении по умолчанию, может быть изменен.  
  
-   В инструкциях `INSERT ... SELECT` и `INSERT ... EXEC`, где вставляемые данные поступают из запроса с предложением **ORDER BY**, значения, возвращаемые функцией **NEXT VALUE FOR**, будут формироваться в порядке, указанном в предложении **ORDER BY**.  
  
## <a name="using-a-sequence-object-with-an-over-order-by-clause"></a>Использование объекта последовательности с предложением OVER ORDER BY  
 Функция **NEXT VALUE FOR** поддерживает формирование отсортированных значений последовательности при указании предложения **OVER** в вызове **NEXT VALUE FOR**. При использовании предложения **OVER** пользователю гарантированно будут возвращены значения, сформированные в порядке, который определен вложенным предложением **ORDER BY** предложения **OVER**. При использовании функции **NEXT VALUE FOR** в предложении **OVER** действуют следующие дополнительные правила:  
  
-   Если в одной инструкции имеется несколько вызовов функции **NEXT VALUE FOR** для одного и того же генератора последовательности, то все они должны иметь одно и то же определение предложения **OVER**.  
  
-   Если в одной инструкции имеется несколько вызовов функции **NEXT VALUE FOR** для разных генераторов последовательностей, то они могут иметь разные определения предложения **OVER**.  
  
-   В вызовах функции **NEXT VALUE FOR** с предложением **OVER** не поддерживается вложенное предложение **PARTITION BY**.  
  
-   Если во всех вызовах функции **NEXT VALUE FOR** в инструкции **SELECT** указано предложение **OVER**, то предложение **ORDER BY** можно использовать в инструкции **SELECT**.  
  
-   Предложение **OVER** допустимо для функции **NEXT VALUE FOR** только в инструкциях **SELECT** или `INSERT ... SELECT ...`. Использование предложения **OVER** в функции **NEXT VALUE FOR** не допускается в инструкции **UPDATE** или **MERGE**.  
  
-   Если доступ к объекту последовательности в то же самое время производится и из другого процесса, то в возвращаемых номерах могут быть пропуски.  
  
## <a name="metadata"></a>Метаданные  
 Чтобы получить сведения о последовательностях, запросите представление каталога [sys.sequences](../../relational-databases/system-catalog-views/sys-sequences-transact-sql.md).  
  
## <a name="security"></a>Безопасность  
  
### <a name="permissions"></a>Разрешения  
 Требуется разрешение **UPDATE** для объекта последовательности или схемы последовательности. Пример предоставления разрешения см. в примере Е ниже в этом разделе.  
  
### <a name="ownership-chaining"></a>Цепочки владения  
 Объекты последовательностей поддерживают цепочки владения. Если объект последовательности имеет того же владельца, что и вызывающие хранимая процедура, триггер или таблица (имеющая объект последовательности в качестве ограничения по умолчанию), то для объекта последовательности проверка разрешений не требуется. Если у объекта последовательности и вызывающей хранимой процедуры, триггера или таблицы разные владельцы, то для объекта последовательности требуется проверка разрешений.  
  
 Если функция **NEXT VALUE FOR** используется в качестве значения по умолчанию в таблице, то пользователю для вставки данных со значением по умолчанию потребуется разрешение **INSERT** для таблицы и разрешение **UPDATE** для объекта последовательности.  
  
-   Если ограничение по умолчанию имеет того же владельца, что и объект последовательности, то при вызове ограничения по умолчанию проверка разрешений не требуется.  
  
-   Если ограничение по умолчанию и объект последовательности принадлежат разным владельцам, то разрешения для объекта последовательности требуются даже в том случае, когда он вызывается через ограничение по умолчанию.  
  
### <a name="audit"></a>Аудит  
 Для аудита функции **NEXT VALUE FOR** отслеживайте SCHEMA_OBJECT_ACCESS_GROUP.  
  
## <a name="examples"></a>Примеры  
 Примеры создания последовательностей и использования функции **NEXT VALUE FOR** для формирования порядковых номеров см. в разделе [Порядковые номера](../../relational-databases/sequence-numbers/sequence-numbers.md).  
  
 В следующих примерах используется последовательность `CountBy1` в схеме `Test`. Выполните следующую инструкцию, чтобы создать последовательность `Test.CountBy1`. В примерах В и Д используется база данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)], поэтому последовательность `CountBy1` создается в ней.  
  
```  
USE AdventureWorks2012 ;  
GO  
  
CREATE SCHEMA Test;  
GO  
  
CREATE SEQUENCE Test.CountBy1  
    START WITH 1  
    INCREMENT BY 1 ;  
GO  
```  
  
### <a name="a-using-a-sequence-in-a-select-statement"></a>A. Использование последовательности в инструкции SELECT  
 В следующем примере создается последовательность `CountBy1`, которая увеличивается на единицу при каждом обращении.  
  
```  
SELECT NEXT VALUE FOR Test.CountBy1 AS FirstUse;  
SELECT NEXT VALUE FOR Test.CountBy1 AS SecondUse;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
FirstUse  
1  
  
SecondUse  
2
```  
  
### <a name="b-setting-a-variable-to-the-next-sequence-value"></a>Б. Присваивание переменной следующего значения из последовательности  
 Следующий пример показывает три способа присвоить переменной следующее значение последовательности.  
  
```  
DECLARE @myvar1 bigint = NEXT VALUE FOR Test.CountBy1  
DECLARE @myvar2 bigint ;  
DECLARE @myvar3 bigint ;  
SET @myvar2 = NEXT VALUE FOR Test.CountBy1 ;  
SELECT @myvar3 = NEXT VALUE FOR Test.CountBy1 ;  
SELECT @myvar1 AS myvar1, @myvar2 AS myvar2, @myvar3 AS myvar3 ;  
GO  
```  
  
### <a name="c-using-a-sequence-with-a-ranking-window-function"></a>В. Использование последовательности в ранжирующей оконной функции  
  
```  
USE AdventureWorks2012 ;  
GO  
  
SELECT NEXT VALUE FOR Test.CountBy1 OVER (ORDER BY LastName) AS ListNumber,  
    FirstName, LastName  
FROM Person.Contact ;  
GO  
```  
  
### <a name="d-using-the-next-value-for-function-in-the-definition-of-a-default-constraint"></a>Г. Использование функции NEXT VALUE FOR в определении ограничения по умолчанию  
 Использование функции **NEXT VALUE FOR** поддерживается в определении ограничения по умолчанию. Пример использования функции **NEXT VALUE FOR** в инструкции **CREATE TABLE** см. в примере C [Порядковые номера](../../relational-databases/sequence-numbers/sequence-numbers.md). В следующем примере инструкция `ALTER TABLE` добавляет последовательность в качестве значения по умолчанию в текущую таблицу.  
  
```  
CREATE TABLE Test.MyTable  
(  
    IDColumn nvarchar(25) PRIMARY KEY,  
    name varchar(25) NOT NULL  
) ;  
GO  
  
CREATE SEQUENCE Test.CounterSeq  
    AS int  
    START WITH 1  
    INCREMENT BY 1 ;  
GO  
  
ALTER TABLE Test.MyTable  
    ADD   
        DEFAULT N'AdvWorks_' +   
        CAST(NEXT VALUE FOR Test.CounterSeq AS NVARCHAR(20))   
        FOR IDColumn;  
GO  
  
INSERT Test.MyTable (name)  
VALUES ('Larry') ;  
GO  
  
SELECT * FROM Test.MyTable;  
GO  
```  
  
### <a name="e-using-the-next-value-for-function-in-an-insert-statement"></a>Д. Использование функции NEXT VALUE FOR в инструкции INSERT  
 В следующем примере создается таблица `TestTable`, а затем в нее вставляется строка с использованием функции `NEXT VALUE FOR`.  
  
```  
CREATE TABLE Test.TestTable  
     (CounterColumn int PRIMARY KEY,  
    Name nvarchar(25) NOT NULL) ;   
GO  
  
INSERT Test.TestTable (CounterColumn,Name)  
    VALUES (NEXT VALUE FOR Test.CountBy1, 'Syed') ;  
GO  
  
SELECT * FROM Test.TestTable;   
GO  
  
```  
  
### <a name="e-using-the-next-value-for-function-with-select--into"></a>Д. Использование функции NEXT VALUE FOR с SELECT ... INTO  
 В следующем примере инструкция `SELECT ... INTO` создает таблицу `Production.NewLocation` и вставляет в нее строки с использованием функции `NEXT VALUE FOR`.  
  
```  
USE AdventureWorks2012 ;   
GO  
  
SELECT NEXT VALUE FOR Test.CountBy1 AS LocNumber, Name   
    INTO Production.NewLocation  
    FROM Production.Location ;  
GO  
  
SELECT * FROM Production.NewLocation ;  
GO  
```  
  
### <a name="f-granting-permission-to-execute-next-value-for"></a>Е. Предоставление разрешения на выполнение NEXT VALUE FOR  
 В следующем примере пользователю `AdventureWorks\Larry` предоставляется разрешение **UPDATE** для выполнения функции `NEXT VALUE FOR` для последовательности `Test.CounterSeq`.  
  
```  
GRANT UPDATE ON OBJECT::Test.CounterSeq TO [AdventureWorks\Larry] ;  
```  
  
## <a name="see-also"></a>См. также:  
 [CREATE SEQUENCE (Transact-SQL)](../../t-sql/statements/create-sequence-transact-sql.md)   
 [ALTER SEQUENCE (Transact-SQL)](../../t-sql/statements/alter-sequence-transact-sql.md)   
 [Порядковые номера](../../relational-databases/sequence-numbers/sequence-numbers.md)  
  
  
