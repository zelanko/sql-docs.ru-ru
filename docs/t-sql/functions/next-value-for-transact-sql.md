---
title: "ЗАТЕМ значение (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 07/19/2016
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
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
caps.latest.revision: 37
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: aab8020fa04b978d7ec1b657fe0a1084123dfb48
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="next-value-for-transact-sql"></a>NEXT VALUE FOR (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  Формирует номер последовательности из указанного объекта последовательности.  
  
 Полное описание создания и использования последовательностей см. в разделе [порядковые номера](../../relational-databases/sequence-numbers/sequence-numbers.md). Используйте [sp_sequence_get_range](../../relational-databases/system-stored-procedures/sp-sequence-get-range-transact-sql.md) для создания резерва диапазона порядковых номеров.  
  
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
 Определяет порядок, в котором значение последовательности присваивается строкам в секции. Дополнительные сведения см. в разделе [предложение OVER &#40; Transact-SQL &#41; ](../../t-sql/queries/select-over-clause-transact-sql.md).  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 Возвращает число с использованием типа последовательности.  
  
## <a name="remarks"></a>Замечания  
 **NEXT VALUE FOR** функция может использоваться в хранимых процедурах и триггерах.  
  
 Когда **NEXT VALUE FOR** функция используется в запросе или ограничении по умолчанию, если один и тот же объект последовательности используется более одного раза или один и тот же объект последовательности используется в инструкции, поставляющей значения и в ограничении по умолчанию в ходе выполнения и то же значение будет возвращаться для всех столбцов, ссылающихся на одну последовательность в пределах строки в результирующем наборе.  
  
 **NEXT VALUE FOR** функция является недетерминированной и допускается только в контекстах, где число формируемых значений последовательности является правильно определенным. Ниже приводятся определения того, как много значений будет использовано для каждого из упоминаемых объектов последовательности в данной инструкции:  
  
-   **ВЫБЕРИТЕ** -для каждого указанного объекта последовательности новое значение формируется один раз для каждой строки результата выполнения инструкции.  
  
-   **ВСТАВИТЬ** ... **ЗНАЧЕНИЯ** -для каждого указанного объекта последовательности новое значение формируется один раз для каждой вставляемой строки в инструкции.  
  
-   **ОБНОВЛЕНИЕ** -для каждого указанного объекта последовательности новое значение формируется для каждой строки, обновляемой инструкцией.  
  
-   Процедурные инструкции (такие как **DECLARE**, **ЗАДАТЬ**, т. д.)-для каждого указанного объекта последовательности новое значение формируется для каждой инструкции.  
  
## <a name="limitations-and-restrictions"></a>Ограничения  
 **NEXT VALUE FOR** функция не может использоваться в следующих ситуациях:  
  
-   Если база данных находится в режиме только для чтения.  
  
-   В качестве аргумента функции с табличным значением.  
  
-   В качестве аргумента агрегатной функции.  
  
-   Во вложенных запросах, включающих обобщенные табличные выражения и производные таблицы.  
  
-   В представлениях, определяемых пользователем функциях, вычисляемых столбцах.  
  
-   В инструкции, использующей **DISTINCT**, **ОБЪЕДИНЕНИЕ**, **UNION ALL**, **EXCEPT** или **INTERSECT** оператор.  
  
-   В инструкции, использующей **ORDER BY** предложение Если **NEXT VALUE FOR** ... **НАД** (**ORDER BY** ...) используется.  
  
-   В следующих предложениях: **ВЫБОРКИ**, **НАД**, **ВЫВОДА**, **ON**, **PIVOT**,  **Отмена СВЕРТЫВАНИЯ**, **GROUP BY**, **HAVING**, **ВЫЧИСЛЕНИЙ**, **COMPUTE BY**, или **FOR XML**.  
  
-   В условные выражения с использованием **случай**, **Выбор**, **COALESCE**, **IIF**, **ISNULL**, или  **Функция NULLIF**.  
  
-   В **значения** предложение, которое не является частью **вставить** инструкции.  
  
-   В определении проверочного ограничения.  
  
-   В определении правила или объекта "значение по умолчанию". (Может использоваться в ограничении по умолчанию.)  
  
-   Используется по умолчанию в определяемом пользователем типе.  
  
-   В инструкции, использующей **ВЕРХНЕЙ**, **СМЕЩЕНИЕ**, или когда **ROWCOUNT** был установлен.  
  
-   В **ГДЕ** предложения FROM инструкции.  
  
-   В **СЛИЯНИЯ** инструкции. (Только если **NEXT VALUE FOR** функция используется в ограничении по умолчанию в целевой таблице, и по умолчанию используется в **создать** инструкция **СЛИЯНИЯ** инструкции.)  
  
## <a name="using-a-sequence-object-in-a-default-constraint"></a>Использование объекта последовательности в ограничении по умолчанию  
 При использовании **NEXT VALUE FOR** функции в ограничении по умолчанию применяются следующие правила:  
  
-   Один объект последовательности может указываться из ограничений по умолчанию нескольких таблиц.  
  
-   Таблица и объект последовательности должны находиться в одной и той же базе данных.  
  
-   Пользователь, добавляющий ограничение по умолчанию, должен иметь разрешение REFERENCES для объекта последовательности.  
  
-   Объект последовательности, указанный из ограничения по умолчанию, не может быть удален до тех пор, пока не удалено само ограничение по умолчанию.  
  
-   Если один и тот же объект последовательности указан в нескольких ограничениях по умолчанию либо и в инструкции, поставляющей значения, и в выполняемом ограничении по умолчанию, то для всех столбцов в строке возвращается один и тот же номер последовательности.  
  
-   Ссылки на **NEXT VALUE FOR** функции в ограничении по умолчанию невозможно указать **НАД** предложения.  
  
-   Объект последовательности, указанный в ограничении по умолчанию, может быть изменен.  
  
-   В случае использования `INSERT … SELECT` или `INSERT … EXEC` инструкции, где вставляемые данные поступают из запроса с помощью **ORDER BY** предложения, значения, возвращаемые функцией **NEXT VALUE FOR** функция будет в порядке, указанном **ORDER BY** предложения.  
  
## <a name="using-a-sequence-object-with-an-over-order-by-clause"></a>Использование объекта последовательности с предложением OVER ORDER BY  
 **NEXT VALUE FOR** функция поддерживает формирование отсортированных значений последовательности, применяя **НАД** предложения **NEXT VALUE FOR** вызова. С помощью **НАД** предложения пользователю гарантированно генерировать будут возвращены значения порядка **НАД** предложением **ORDER B**вложенное предложение Y. Следующие дополнительные правила применяются при использовании **NEXT VALUE FOR** функционировать с **НАД** предложения:  
  
-   Несколько вызовов **NEXT VALUE FOR** функция, тот же генератор последовательностей в одной инструкции должны использовать же **НАД** определение предложения.  
  
-   Несколько вызовов **NEXT VALUE FOR** функции, разных генераторов последовательностей в одной инструкции может иметь разные **НАД** определения предложения.  
  
-   **НАД** с предложением **NEXT VALUE FOR** функция не поддерживает **PARTITION BY** вложенное предложение.  
  
-   Если все вызовы **NEXT VALUE FOR** функционировать в **ВЫБЕРИТЕ** инструкция указывает **НАД** предложение, **ORDER BY** предложение может быть использовано в **ВЫБЕРИТЕ** инструкции.  
  
-   **НАД** предложение допустимо для **NEXT VALUE FOR** работать при использовании в **ВЫБЕРИТЕ** инструкции или `INSERT … SELECT …` инструкции. Использование **НАД** предложение with **NEXT VALUE FOR** функции не допускается в **обновление** или **СЛИЯНИЯ** инструкции.  
  
-   Если доступ к объекту последовательности в то же самое время производится и из другого процесса, то в возвращаемых номерах могут быть пропуски.  
  
## <a name="metadata"></a>Метаданные  
 Сведения о последовательностях, запросите [sys.sequences](../../relational-databases/system-catalog-views/sys-sequences-transact-sql.md) представления каталога.  
  
## <a name="security"></a>безопасность  
  
### <a name="permissions"></a>Permissions  
 Требуется **обновление** разрешение для объекта последовательности или схемы последовательности. Пример предоставления разрешения см. в примере Е ниже в этом разделе.  
  
### <a name="ownership-chaining"></a>Цепочки владения  
 Объекты последовательностей поддерживают цепочки владения. Если объект последовательности имеет того же владельца, что и вызывающие хранимая процедура, триггер или таблица (имеющая объект последовательности в качестве ограничения по умолчанию), то для объекта последовательности проверка разрешений не требуется. Если у объекта последовательности и вызывающей хранимой процедуры, триггера или таблицы разные владельцы, то для объекта последовательности требуется проверка разрешений.  
  
 При **NEXT VALUE FOR** функция используется в качестве значения по умолчанию в таблице, пользователям требуются оба **вставить** разрешение на таблицу, и **обновление** разрешение на объект последовательности , для вставки данных, используя значение по умолчанию.  
  
-   Если ограничение по умолчанию имеет того же владельца, что и объект последовательности, то при вызове ограничения по умолчанию проверка разрешений не требуется.  
  
-   Если ограничение по умолчанию и объект последовательности принадлежат разным владельцам, то разрешения для объекта последовательности требуются даже в том случае, когда он вызывается через ограничение по умолчанию.  
  
### <a name="audit"></a>Аудит  
 Для аудита **NEXT VALUE FOR** функционировать, отслеживайте SCHEMA_OBJECT_ACCESS_GROUP.  
  
## <a name="examples"></a>Примеры  
 Примеры создания последовательностей и использования **NEXT VALUE FOR** функцию для создания порядковых номеров см. в разделе [порядковые номера](../../relational-databases/sequence-numbers/sequence-numbers.md).  
  
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
  
 `FirstUse`  
  
 `1`  
  
 `SecondUse`  
  
 `2`  
  
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
 С помощью **NEXT VALUE FOR** поддерживаемые функции в определении ограничения по умолчанию. Пример использования **NEXT VALUE FOR** в **CREATE TABLE** инструкции, см. пример В[порядковые номера](../../relational-databases/sequence-numbers/sequence-numbers.md). В следующем примере инструкция `ALTER TABLE` добавляет последовательность в качестве значения по умолчанию в текущую таблицу.  
  
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
  
### <a name="e-using-the-next-value-for-function-with-select--into"></a>Д. Использование функции NEXT VALUE FOR с SELECT… INTO  
 В следующем примере используется `SELECT … INTO` инструкцию, чтобы создать таблицу с именем `Production.NewLocation` и использует `NEXT VALUE FOR` функцию для номера каждой строки.  
  
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
 В следующем примере предоставляется **обновление** разрешение для пользователя с именем `AdventureWorks\Larry` разрешение на выполнение `NEXT VALUE FOR` с помощью `Test.CounterSeq` последовательности.  
  
```  
GRANT UPDATE ON OBJECT::Test.CounterSeq TO [AdventureWorks\Larry] ;  
```  
  
## <a name="see-also"></a>См. также:  
 [Создание ПОСЛЕДОВАТЕЛЬНОСТИ &#40; Transact-SQL &#41;](../../t-sql/statements/create-sequence-transact-sql.md)   
 [ALTER ПОСЛЕДОВАТЕЛЬНОСТИ &#40; Transact-SQL &#41;](../../t-sql/statements/alter-sequence-transact-sql.md)   
 [Порядковые номера](../../relational-databases/sequence-numbers/sequence-numbers.md)  
  
  

