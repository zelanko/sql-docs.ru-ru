---
title: "Выбор строк для миграции с использованием функции фильтров (база данных Stretch) | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "06/27/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.service: "sql-server-stretch-database"
ms.suite: ""
ms.technology: 
  - "dbe-stretch"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "база данных Stretch, предикаты"
  - "предикаты для базы данных Stretch"
  - "база данных Stretch, встроенные функции с табличным значением"
  - "встроенные функции с табличным значением для базы данных Stretch"
ms.assetid: 090890ee-7620-4a08-8e15-d2fbc71dd12f
caps.latest.revision: 43
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 42
---
# Выбор строк для миграции с использованием функции фильтров (база данных Stretch)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Если холодные данные хранятся в отдельной таблице, можно настроить базу данных Stretch, чтобы перенести эту таблицу целиком. С другой стороны, если таблица содержит горячие и холодные данные, строки для миграции можно выбирать с помощью предиката фильтра. Этот предикат фильтра является встроенной функцией с табличным значением. В этом разделе описывается создание встроенной функции с табличным значением для выбора строк для миграции.  
  
> [!IMPORTANT] Если указать плохо оптимизированную функцию фильтров, перенос данных будет выполняться медленно. База данных Stretch применяет функцию фильтров к таблице с помощью оператора CROSS APPLY.  
  
 Если функция фильтров не указана, переносится вся таблица.  
  
 При запуске мастера включения растяжения для базы данных можно перенести таблицу полностью или указать простую функцию фильтров в мастере. Если вы хотите использовать другой тип функции фильтров, чтобы выбрать строки для переноса, выполните одно из следующих действий.  
  
-   Закройте мастер и выполните инструкцию ALTER TABLE, чтобы включить растяжение для таблицы и указать функцию фильтров.  
  
-   Выполните инструкцию ALTER TABLE, чтобы указать функцию фильтров после выхода из мастера.  
  
 Далее в этом разделе описывается синтаксис инструкций ALTER TABLE для добавления функции.  
  
## Основные требования для функции фильтров  
 Встроенная функция с табличным значением, необходимая для предиката фильтра базы данных Stretch, выглядит как показано в следующем примере.  
  
```tsql  
CREATE FUNCTION dbo.fn_stretchpredicate(@column1 datatype1, @column2 datatype2 [, ...n])  
RETURNS TABLE  
WITH SCHEMABINDING   
AS   
RETURN  SELECT 1 AS is_eligible  
        WHERE <predicate>  
```  
  
 Параметры для этой функции должны быть идентификаторами столбцов из таблицы.  
  
 Привязка схемы необходима, чтобы не допустить удаления или изменения столбцов, используемых функцией фильтров.  
  
### Возвращаемое значение  
 Если функция возвращает непустой результат, строка может быть перенесена. В противном случае, то есть если функция не возвращает результат, строка не подходит для миграции.  
  
### Условия  
 &lt;*Предикат*&gt; может содержать одно или несколько условий, объединенных с помощью логического оператора AND.  
  
```  
<predicate> ::= <condition> [ AND <condition> ] [ ...n ]  
```  
  
 Каждое условие в свою очередь может содержать одно простое условие или несколько простых условий, объединенных с помощью логического оператора OR.  
  
```  
<condition> ::= <primitive_condition> [ OR <primitive_condition> ] [ ...n ]  
```  
  
### Простые условия  
 Простое условие может выполнить одно из следующих сравнений.  
  
```  
<primitive_condition> ::=   
{  
<function_parameter> <comparison_operator> constant  
| <function_parameter> { IS NULL | IS NOT NULL }  
| <function_parameter> IN ( constant [ ,...n ] )  
}  
  
```  
  
-   Сравнение параметра функции с константным выражением. Например, `@column1 < 1000`.  
  
     Ниже приведен пример, в котором проверяется, меньше ли значение столбца *date*, чем 01.01.2016.  
  
    ```tsql  
    CREATE FUNCTION dbo.fn_stretchpredicate(@column1 datetime)  
    RETURNS TABLE  
    WITH SCHEMABINDING   
    AS   
    RETURN  SELECT 1 AS is_eligible  
            WHERE @column1 < CONVERT(datetime, '1/1/2016', 101)  
    GO  
  
    ALTER TABLE stretch_table_name SET ( REMOTE_DATA_ARCHIVE = ON (  
        FILTER_PREDICATE = dbo.fn_stretchpredicate(date),  
        MIGRATION_STATE = OUTBOUND  
    ) )  
  
    ```  
  
-   Применяйте оператор IS NULL или IS NOT NULL к параметру функции.  
  
-   Используйте оператор IN для сравнения параметра функции со списком значений констант.  
  
     Ниже приведен пример, в котором проверяется, соответствует ли значение столбца *shipment_status* одному из значений `IN (N'Completed', N'Returned', N'Cancelled')`.  
  
    ```tsql  
    CREATE FUNCTION dbo.fn_stretchpredicate(@column1 nvarchar(15))  
    RETURNS TABLE  
    WITH SCHEMABINDING   
    AS   
    RETURN  SELECT 1 AS is_eligible  
            WHERE @column1 IN (N'Completed', N'Returned', N'Cancelled')  
    GO  
  
    ALTER TABLE table1 SET ( REMOTE_DATA_ARCHIVE = ON (  
        FILTER_PREDICATE = dbo.fn_stretchpredicate(shipment_status),  
        MIGRATION_STATE = OUTBOUND  
    ) )  
  
    ```  
  
### Операторы сравнения  
 Поддерживаются следующие операторы сравнения.  
  
 `<, <=, >, >=, =, <>, !=, !<, !>`  
  
```  
<comparison_operator> ::= { < | <= | > | >= | = | <> | != | !< | !> }  
```  
  
### Константные выражения  
 Константы, используемые в функции фильтров, могут быть любым детерминированным выражением, которое может вычисляться при определении функции. Константные выражения могут содержать следующее.  
  
-   Литералы. Например, `N’abc’, 123`.  
  
-   Алгебраические выражения. Например, `123 + 456`.  
  
-   Детерминированные функции. Например, `SQRT(900)`.  
  
-   Детерминированные преобразования, использующие CAST или CONVERT. Например, `CONVERT(datetime, '1/1/2016', 101)`.  
  
### Прочие выражения  
 Вы можете использовать операторы BETWEEN и NOT BETWEEN, если полученная функция соответствует описанным здесь правилам после замены операторов BETWEEN и NOT BETWEEN эквивалентными выражениями AND и OR.  
  
 Нельзя использовать вложенные запросы или недетерминированные функции, такие как RAND() или GETDATE().  
  
## Добавление функции фильтров в таблицу  
 Добавьте функцию фильтров в таблицу путем выполнения инструкции **ALTER TABLE** и указания существующей встроенной функции с табличным значением в качестве значения параметра **FILTER_PREDICATE**. Например:  
  
```tsql  
ALTER TABLE stretch_table_name SET ( REMOTE_DATA_ARCHIVE = ON (  
    FILTER_PREDICATE = dbo.fn_stretchpredicate(column1, column2),  
    MIGRATION_STATE = <desired_migration_state>  
) )  
  
```  
  
 После привязки функции к таблице в качестве предиката становятся истинными следующие моменты.  
  
-   При следующей миграции данных переносятся только те строки, для которых функция возвращает непустое значение.  
  
-   Столбцы, используемые функцией, становятся привязанными к схеме. Эти столбцы невозможно изменить, пока таблица использует эту функцию как свой предикат фильтра.  
  
 Нельзя удалить встроенную функцию с табличным значением, пока таблица использует эту функцию как свой предикат фильтра. 

> [!TIP] Чтобы повысить производительность функции фильтров, создайте индекс для столбцов, используемых этой функцией.

 ### Передача имен столбцов функции фильтров
 
 При назначении функции фильтров таблице укажите имена столбцов, переданных в функцию фильтров с помощью однокомпонентного имени. Если при передаче имен столбцов указано трехкомпонентное имя, последующие запросы, адресованные таблице с включенным растяжением, завершатся ошибкой.

Например, если указать трехкомпонентное имя столбца, как показано в следующем примере, инструкция выполнится успешно, но последующие запросы, адресованные таблице, завершатся ошибкой.

```tsql
ALTER TABLE SensorTelemetry 
  SET ( REMOTE_DATA_ARCHIVE = ON (
    FILTER_PREDICATE=dbo.fn_stretchpredicate(dbo.SensorTelemetry.ScanDate),
    MIGRATION_STATE = OUTBOUND )
  )
```

Вместо этого укажите функцию фильтров с однокомпонентным именем столбца, как показано в следующем примере.

```tsql
ALTER TABLE SensorTelemetry 
  SET ( REMOTE_DATA_ARCHIVE = ON  (
    FILTER_PREDICATE=dbo.fn_stretchpredicate(ScanDate),
    MIGRATION_STATE = OUTBOUND )
  )
```
  
## <a name="addafterwiz"></a>Добавление функции фильтров после запуска мастера  
  
Если требуется использовать функцию, которую невозможно создать в мастере **включения базы данных для растяжения**, можно выполнить инструкцию **ALTER TABLE** и указать функцию после закрытия мастера. Однако прежде чем применять функцию, необходимо остановить выполняемую миграцию данных и вернуть перенесенные данные. (Дополнительные сведения о том, почему это необходимо, см. в разделе [Замена существующей функции фильтров](#replacePredicate).)
  
1. Измените направление миграции и верните уже перенесенные данные. Отменить эту операцию после запуска невозможно. С вас также взимается плата за исходящую передачу данных (вывод) в Azure. Дополнительные сведения см. в разделе [Принципы ценообразования Azure](https://azure.microsoft.com/pricing/details/data-transfers/).  
  
    ```tsql  
    ALTER TABLE <table name>  
        SET ( REMOTE_DATA_ARCHIVE ( MIGRATION_STATE = INBOUND ) ) ;   
    ```  
  
2. Дождитесь завершения миграции. Проверить состояние можно с помощью **монитора базы данных Stretch** в SQL Server Management Studio или запросить представление**sys.dm_db_rda_migration_status**. Дополнительные сведения см. в разделе [Мониторинг переноса данных и устранение неполадок](../../sql-server/stretch-database/monitor-and-troubleshoot-data-migration-stretch-database.md) или [sys.dm_db_rda_migration_status](sys.dm_db_rda_migration_status%20\(Transact-SQL\).md).  
  
3. Создайте функцию фильтров, которую требуется применить к таблице.  
  
4. Добавьте функцию в таблицу и перезапустите перенос данных в Azure.  
  
    ```tsql  
    ALTER TABLE <table name>  
        SET ( REMOTE_DATA_ARCHIVE  
            (           
                FILTER_PREDICATE = <predicate>,  
                MIGRATION_STATE = OUTBOUND  
            )  
            );   
    ```  
  
## Фильтрация строк по дате  
 В следующем примере выполняется перенос строк, в которых столбец **date** содержит значение до 1 января 2016 г.  
  
```tsql  
-- Filter by date  
--  
CREATE FUNCTION dbo.fn_stretch_by_date(@date datetime2)  
RETURNS TABLE  
WITH SCHEMABINDING   
AS   
       RETURN SELECT 1 AS is_eligible WHERE @date < CONVERT(datetime2, '1/1/2016', 101)  
GO  
  
```  
  
## Фильтрация строк по значению в столбце состояния  
 В следующем примере выполняется перенос строк, в которых столбец **status** содержит одно из указанных значений.  
  
```tsql  
-- Filter by status column  
--  
CREATE FUNCTION dbo.fn_stretch_by_status(@status nvarchar(128))  
RETURNS TABLE  
WITH SCHEMABINDING   
AS   
       RETURN SELECT 1 AS is_eligible WHERE @status IN (N'Completed', N'Returned', N'Cancelled')  
GO  
  
```  
  
## Фильтрация строк с помощью скользящего окна  
 Для фильтрации строк с помощью скользящего окна учитывайте следующие требования для функции фильтра.  
  
-   Функция должна быть детерминированной. Таким образом, нельзя создать функцию, которая автоматически пересчитывает скользящее окно с течением времени.  
  
-   Эта функция использует привязку схемы. Поэтому невозможно просто обновлять функцию "на месте" каждый день путем вызова инструкции **ALTER FUNCTION** для перемещения скользящего окна.  
  
 Начните с функции фильтров, как в следующем примере, в котором переносятся строки, где столбец **systemEndTime** содержит значение до 1 января 2016 г.  
  
```tsql  
CREATE FUNCTION dbo.fn_StretchBySystemEndTime20160101(@systemEndTime datetime2)   
RETURNS TABLE   
WITH SCHEMABINDING    
AS    
RETURN SELECT 1 AS is_eligible   
  WHERE @systemEndTime < CONVERT(datetime2, '2016-01-01T00:00:00', 101) ;  
  
```  
  
 Примените функцию фильтров к таблице.  
  
```tsql  
ALTER TABLE <table name>   
SET (   
        REMOTE_DATA_ARCHIVE = ON   
                (   
                        FILTER_PREDICATE = dbo.fn_StretchBySystemEndTime20160101(SysEndTime)  
                                , MIGRATION_STATE = OUTBOUND   
                )  
        )   
;  
  
```  
  
 Если вы хотите обновить скользящее окно, выполните следующие действия.  
  
1.  Создайте новую функцию, которая указывает новое скользящее окно. В следующем примере выбираются даты до 2 января 2016 г. вместо 1 января 2016 г.  
  
2.  Замените предыдущую функцию фильтров на новую путем вызова **ALTER TABLE**, как показано в следующем примере.  
  
3.  При необходимости удалите предыдущую функцию фильтра, которая больше не используется, путем вызова **DROP FUNCTION**. (Этот шаг не показан в примере.)  
  
```tsql  
BEGIN TRAN  
GO  
        /*(1) Create new predicate function definition */  
        CREATE FUNCTION dbo.fn_StretchBySystemEndTime20160102(@systemEndTime datetime2)  
        RETURNS TABLE  
        WITH SCHEMABINDING   
        AS   
        RETURN SELECT 1 AS is_eligible  
               WHERE @systemEndTime < CONVERT(datetime2,'2016-01-02T00:00:00', 101)  
        GO  
  
        /*(2) Set the new function as the filter predicate */  
        ALTER TABLE <table name>  
        SET   
        (  
               REMOTE_DATA_ARCHIVE = ON  
               (  
                       FILTER_PREDICATE = dbo.fn_StretchBySystemEndTime20160102(SysEndTime),  
                       MIGRATION_STATE = OUTBOUND  
               )  
        )   
COMMIT ;  
  
```  
  
## Дополнительные примеры допустимых функций фильтров  
  
-   В следующем примере два простых условия объединяются с помощью логического оператора AND.  
  
    ```tsql  
    CREATE FUNCTION dbo.fn_stretchpredicate((@column1 datetime, @column2 nvarchar(15))  
    RETURNS TABLE  
    WITH SCHEMABINDING   
    AS   
    RETURN  SELECT 1 AS is_eligible  
      WHERE @column1 < N'20150101' AND @column2 IN (N'Completed', N'Returned', N'Cancelled')  
    GO  
  
    ALTER TABLE table1 SET ( REMOTE_DATA_ARCHIVE = ON (  
        FILTER_PREDICATE = dbo.fn_stretchpredicate(date, shipment_status),  
        MIGRATION_STATE = OUTBOUND  
    ) )  
  
    ```  
  
-   В следующем примере используется несколько условий и детерминированное преобразование с CONVERT.  
  
    ```tsql  
    CREATE FUNCTION dbo.fn_stretchpredicate_example1(@column1 datetime, @column2 int, @column3 nvarchar)  
    RETURNS TABLE  
    WITH SCHEMABINDING   
    AS   
    RETURN  SELECT 1 AS is_eligible  
        WHERE @column1 < CONVERT(datetime, '1/1/2015', 101) AND (@column2 < -100 OR @column2 > 100 OR @column2 IS NULL) AND @column3 IN (N'Completed', N'Returned', N'Cancelled')  
    GO  
  
    ```  
  
-   В следующем примере используются математические операторы и функции.  
  
    ```tsql  
    CREATE FUNCTION dbo.fn_stretchpredicate_example2(@column1 float)  
    RETURNS TABLE  
    WITH SCHEMABINDING   
    AS   
    RETURN  SELECT 1 AS is_eligible  
            WHERE @column1 < SQRT(400) + 10  
    GO  
  
    ```  
  
-   В следующем примере используются операторы BETWEEN и NOT BETWEEN. Такое использование допускается, если полученная функция соответствует описанным здесь правилам после замены операторов BETWEEN и NOT BETWEEN эквивалентными выражениями AND и OR.  
  
    ```tsql  
    CREATE FUNCTION dbo.fn_stretchpredicate_example3(@column1 int, @column2 int)  
    RETURNS TABLE  
    WITH SCHEMABINDING   
    AS   
    RETURN  SELECT 1 AS is_eligible  
            WHERE @column1 BETWEEN 0 AND 100  
                AND (@column2 NOT BETWEEN 200 AND 300 OR @column1 = 50)  
    GO  
  
    ```  
  
     Предыдущая функция эквивалентна следующей функции после замены операторов BETWEEN и NOT BETWEEN на соответствующие выражения AND и OR.  
  
    ```tsql  
    CREATE FUNCTION dbo.fn_stretchpredicate_example4(@column1 int, @column2 int)  
    RETURNS TABLE  
    WITH SCHEMABINDING   
    AS   
    RETURN  SELECT 1 AS is_eligible  
            WHERE @column1 >= 0 AND @column1 <= 100 AND (@column2 < 200 OR @column2 > 300 OR @column1 = 50)  
    GO  
  
    ```  
  
## Примеры недопустимых функций фильтров  
  
-   Следующая функция является недопустимой, поскольку содержит недетерминированное преобразование.  
  
    ```tsql  
    CREATE FUNCTION dbo.fn_example5(@column1 datetime)  
    RETURNS TABLE  
    WITH SCHEMABINDING   
    AS   
    RETURN  SELECT 1 AS is_eligible  
            WHERE @column1 < CONVERT(datetime, '1/1/2016')  
    GO  
  
    ```  
  
-   Следующая функция является недопустимой, поскольку содержит вызов недетерминированной функции.  
  
    ```tsql  
    CREATE FUNCTION dbo.fn_example6(@column1 datetime)  
    RETURNS TABLE  
    WITH SCHEMABINDING   
    AS   
    RETURN  SELECT 1 AS is_eligible  
            WHERE @column1 < DATEADD(day, -60, GETDATE())  
    GO  
  
    ```  
  
-   Следующая функция является недопустимой, поскольку содержит вложенный запрос.  
  
    ```tsql  
    CREATE FUNCTION dbo.fn_example7(@column1 int)  
    RETURNS TABLE  
    WITH SCHEMABINDING   
    AS   
    RETURN  SELECT 1 AS is_eligible  
            WHERE @column1 IN (SELECT SupplierID FROM Supplier WHERE Status = 'Defunct')  
    GO  
  
    ```  
  
-   Следующие функции являются недопустимыми, поскольку при определении функции выражения, использующие алгебраические операторы или встроенные функции, должны оцениваться как константы. Нельзя включать ссылки на столбцы в алгебраические выражения или вызовы функций.  
  
    ```tsql  
    CREATE FUNCTION dbo.fn_example8(@column1 int)  
    RETURNS TABLE  
    WITH SCHEMABINDING   
    AS   
    RETURN  SELECT 1 AS is_eligible  
            WHERE @column1 % 2 =  0  
    GO  
  
    CREATE FUNCTION dbo.fn_example9(@column1 int)  
    RETURNS TABLE  
    WITH SCHEMABINDING   
    AS   
    RETURN  SELECT 1 AS is_eligible  
            WHERE SQRT(@column1) = 30  
    GO  
  
    ```  
  
-   Следующая функция является недопустимой, поскольку нарушает описанные здесь правила после замены оператора BETWEEN на эквивалентное выражение AND.  
  
    ```tsql  
    CREATE FUNCTION dbo.fn_example10(@column1 int, @column2 int)  
    RETURNS TABLE  
    WITH SCHEMABINDING  
    AS  
    RETURN  SELECT 1 AS is_eligible  
            WHERE (@column1 BETWEEN 1 AND 200 OR @column1 = 300) AND @column2 > 1000  
    GO  
  
    ```  
  
     Предыдущая функция эквивалентна следующей функции после замены оператора BETWEEN на соответствующее выражение AND. Эта функция является недопустимой, так как простые условия могут использовать только логический оператор OR.  
  
    ```tsql  
    CREATE FUNCTION dbo.fn_example11(@column1 int, @column2 int)  
    RETURNS TABLE  
    WITH SCHEMABINDING   
    AS   
    RETURN  SELECT 1 AS is_eligible  
            WHERE (@column1 >= 1 AND @column1 <= 200 OR @column1 = 300) AND @column2 > 1000  
    GO  
  
    ```  
  
## Как база данных Stretch применяет функцию фильтров  
 База данных Stretch применяет функцию фильтров к таблице и определяет подходящие строки при помощи оператора CROSS APPLY. Например:  
  
```tsql  
SELECT * FROM stretch_table_name CROSS APPLY fn_stretchpredicate(column1, column2)  
```  
  
 Если функция возвращает для строки непустой результат, эта строка подходит для переноса.  
  
## <a name="replacePredicate"></a>Замена существующей функции фильтров  
 Можно заменить ранее заданную функцию фильтров, выполнив инструкцию **ALTER TABLE** снова и указав новое значение для параметра **FILTER_PREDICATE**. Например:  
  
```tsql  
ALTER TABLE stretch_table_name SET ( REMOTE_DATA_ARCHIVE = ON (  
    FILTER_PREDICATE = dbo.fn_stretchpredicate2(column1, column2),  
    MIGRATION_STATE = <desired_migration_state>  
  
```  
  
 Новая встроенная функция с табличным значением имеет следующие требования.  
  
-   Новая функция должна быть менее строгой, чем предыдущая.  
  
-   Все операторы, которые существовали в старой функции, должны существовать и в новой функции.  
  
-   Новая функция не может содержать операторы, которые не существовали в старой функции.  
  
-   Нельзя изменить порядок аргументов оператора.  
  
-   Только константные значения, которые являются частью сравнения `<, <=, >, >=`, можно изменить способом, который делает предикат менее строгим.  
  
### Пример допустимой замены  
 Предположим, что следующая функция является текущей функцией фильтров.  
  
```tsql  
CREATE FUNCTION dbo.fn_stretchpredicate_old(@column1 datetime, @column2 int)  
RETURNS TABLE  
WITH SCHEMABINDING   
AS   
RETURN  SELECT 1 AS is_eligible  
        WHERE @column1 < CONVERT(datetime, '1/1/2016', 101)  
            AND (@column2 < -100 OR @column2 > 100)  
GO  
  
```  
  
 Следующая функция является допустимой заменой, поскольку новая константа даты (указывающая более позднюю дату отсечки) делает функцию менее строгой.  
  
```tsql  
CREATE FUNCTION dbo.fn_stretchpredicate_new(@column1 datetime, @column2 int)  
RETURNS TABLE  
WITH SCHEMABINDING   
AS   
RETURN  SELECT 1 AS is_eligible  
        WHERE @column1 < CONVERT(datetime, '2/1/2016', 101)  
            AND (@column2 < -50 OR @column2 > 50)  
GO  
  
```  
  
### Примеры недопустимых замен  
 Следующая функция не является допустимой заменой, поскольку новая константа даты (указывающая более раннюю дату отсечки) не делает функцию менее строгой.  
  
```tsql  
CREATE FUNCTION dbo.fn_notvalidreplacement_1(@column1 datetime, @column2 int)  
RETURNS TABLE  
WITH SCHEMABINDING   
AS   
RETURN  SELECT 1 AS is_eligible  
        WHERE @column1 < CONVERT(datetime, '1/1/2015', 101)  
            AND (@column2 < -100 OR @column2 > 100)  
GO  
  
```  
  
 Следующая функция не является допустимой заменой, поскольку один из операторов сравнения был удален.  
  
```tsql  
CREATE FUNCTION dbo.fn_notvalidreplacement_2(@column1 datetime, @column2 int)  
RETURNS TABLE  
WITH SCHEMABINDING   
AS   
RETURN  SELECT 1 AS is_eligible  
        WHERE @column1 < CONVERT(datetime, '1/1/2016', 101)  
            AND (@column2 < -50)  
GO  
  
```  
  
 Следующая функция не является допустимой заменой, поскольку новое условие было добавлено с логическим оператором AND.  
  
```tsql  
CREATE FUNCTION dbo.fn_notvalidreplacement_3(@column1 datetime, @column2 int)  
RETURNS TABLE  
WITH SCHEMABINDING   
AS   
RETURN  SELECT 1 AS is_eligible  
        WHERE @column1 < CONVERT(datetime, '1/1/2016', 101)  
            AND (@column2 < -100 OR @column2 > 100)  
            AND (@column2 <> 0)  
GO  
  
```  
  
## Удаление функции фильтров из таблицы  
 Чтобы выполнить миграцию всей таблицы вместо переноса выбранных строк, удалите существующую функцию, присвоив **FILTER_PREDICATE** значение null. Например:  
  
```tsql  
ALTER TABLE stretch_table_name SET ( REMOTE_DATA_ARCHIVE = ON (  
    FILTER_PREDICATE = NULL,  
    MIGRATION_STATE = <desired_migration_state>  
) )  
  
```  
  
 После удаления функции фильтров все строки в таблицы пригодны для миграции. В результате позже нельзя будет указать функцию фильтров для той же таблицы, если сначала не вернуть удаленные данные таблицы из Azure. Это ограничение существует, чтобы избежать ситуации, когда строки, не подходящие для миграции при предоставлении новой функции фильтров, уже перенесены в Azure.  
  
## Проверка функции фильтров, примененной к таблице  
 Чтобы проверить функцию фильтров, примененную к таблице, откройте представление каталога **sys.remote_data_archive_tables** и проверьте значение столбца **filter_predicate**. Если это значение NULL, вся таблица подходит для архивации. Дополнительные сведения см. в разделе [sys.remote_data_archive_tables (Transact-SQL)](../Topic/sys.remote_data_archive_tables%20\(Transact-SQL\).md).  
  
## Заметки о безопасности для функции фильтров  
Учетная запись с нарушениями безопасности, имеющая привилегии db_owner, может выполнять следующие действия.  
  
-   Создавать и применять функцию с табличными значениями, которая потребляет серверные ресурсы в больших объемах или ждет продолжительное время, что приводит к отказу в обслуживании.  
  
-   Создавать и применять функцию с табличными значениями, которая позволяет вывести содержимое таблицы, в отношении которого пользователю было явно отказано в доступе на чтение.  
  
## См. также:  
 [ALTER TABLE (Transact-SQL)](../../t-sql/statements/alter-table-transact-sql.md)  
  
  