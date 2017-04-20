---
title: "Поддерживаемые функции для модулей, скомпилированных в собственном коде T-SQL | Документация Майкрософт"
ms.custom: 
ms.date: 12/16/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine-imoltp
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 05515013-28b5-4ccf-9a54-ae861448945b
caps.latest.revision: 44
author: MightyPen
ms.author: genemi
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 16f09bada7bbf3ae964ecfa09aa33208aa2f3acf
ms.lasthandoff: 04/11/2017

---
# <a name="supported-features-for-natively-compiled-t-sql-modules"></a>Поддерживаемые функции для модулей, скомпилированных в собственном коде T-SQL
[!INCLUDE[tsql-appliesto-ss2014-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2014-asdb-xxxx-xxx-md.md)]


  В этом разделе содержится список компонентов контактной зоны T-SQL и поддерживаемых функций в тексте модулей, скомпилированных в собственном коде T-SQL, например хранимых процедур ([CREATE PROCEDURE (Transact-SQL)](../../t-sql/statements/create-procedure-transact-sql.md)), скалярных определяемых пользователем функций, встроенных функций с табличными значениями и триггеров.  

 Дополнительные сведения о поддерживаемых функциях в определении исходных модулей см. в разделе [Поддерживаемые конструкции DDL для модулей, скомпилированных в собственном коде T-SQL](../../relational-databases/in-memory-oltp/supported-ddl-for-natively-compiled-t-sql-modules.md).  

-   [Контактная зона запросов в собственных модулях](#qsancsp)  

-   [Изменение данных](#dml)  

-   [Язык управления потоком](#cof)  

-   [Поддерживаемые операторы](#so)  

-   [Встроенные функции в модулях, скомпилированных в собственном коде](#bfncsp)  

-   [Аудит](../../relational-databases/in-memory-oltp/supported-features-for-natively-compiled-t-sql-modules.md#auditing)  

-   [Табличные указания и указания запросов](../../relational-databases/in-memory-oltp/supported-features-for-natively-compiled-t-sql-modules.md#tqh)  

-   [Ограничения на сортировку](../../relational-databases/in-memory-oltp/supported-features-for-natively-compiled-t-sql-modules.md#los)  

 Полные сведения о неподдерживаемых конструкциях и о том, как обойти некоторые неподдерживаемые функции в модулях, скомпилированных в собственном коде, см. в разделе [Migration Issues for Natively Compiled Stored Procedures](../../relational-databases/in-memory-oltp/migration-issues-for-natively-compiled-stored-procedures.md). Дополнительные сведения о неподдерживаемых компонентах см. в разделе [Конструкции языка Transact-SQL, неподдерживаемые в In-Memory OLTP](../../relational-databases/in-memory-oltp/transact-sql-constructs-not-supported-by-in-memory-oltp.md).  

##  <a name="qsancsp"></a> Контактная зона запросов в собственных модулях  

Здесь приведены поддерживаемые конструкции запросов.  

Предложение SELECT:  

-   псевдонимы имен и столбцов (с помощью синтаксиса AS или =);  

-   скалярные вложенные запросы;  

-   предложение TOP*;  

-   SELECT DISTINCT  

              DISTINCT aggregates are not supported.  

-   UNION и UNION ALL

-   присвоение значений переменных.  

Предложение FROM:  

-   FROM \<оптимизированная_для_памяти_таблица_или_табличная_переменная>  

-   FROM \<скомпилированные_в_собственном_коде_встроенные_функции_с_табличными_значениями>  

-   LEFT OUTER JOIN, RIGHT OUTER JOIN, CROSS JOIN и INNER JOIN;  

-   вложенные запросы `[AS] table_alias`. Дополнительные сведения см. в разделе [FROM (Transact-SQL)](../../t-sql/queries/from-transact-sql.md).  

Предложение WHERE:  

-   Предикат фильтра IS [NOT] NULL  

-   AND, OR, NOT, IN, EXISTS, BETWEEN;  


Предложение[GROUP BY](../../t-sql/queries/select-group-by-transact-sql.md) :

- поддерживается вместе с агрегатными функциями AVG, COUNT, COUNT_BIG, MIN, MAX и SUM.  

- Функции MIN и MAX не поддерживаются для типов nvarchar, char, varchar, varchar, varbinary и binary.  

Предложение[ORDER BY](../../t-sql/queries/select-order-by-clause-transact-sql.md) :


- **DISTINCT** не поддерживается в предложении **ORDER BY** .


- Поддерживается с [GROUP BY (Transact-SQL)](../../t-sql/queries/select-group-by-transact-sql.md), если выражение в списке ORDER BY появляется дословно в списке GROUP BY.
  - Например, GROUP BY a + b ORDER BY a + b поддерживается; GROUP BY a, b ORDER BY a + b не поддерживается.  


Предложение HAVING:

- С соблюдением тех же ограничений, что и в предложении WHERE.


#### <a name="order-by-and-top-are-supported-in-natively-compiled-modules-with-some-restrictions"></a>Предложения ORDER BY и TOP поддерживаются в модулях, скомпилированных в собственном коде, с некоторыми ограничениями


- Не поддерживаются **WITH TIES** и **PERCENT** в предложении **TOP** .


- **DISTINCT** не поддерживается в предложении **ORDER BY** .  


- **TOP** совместно с **ORDER BY** не поддерживает более 8192 строк при использовании константы в предложении **TOP** .
  - Это ограничение может быть понижено в случае, если запрос содержит соединения или агрегатные функции. (Например, с одним соединением (двумя таблицами) ограничение составляет 4 096 строк. С двумя соединениями (тремя таблицами) ограничение равно 2 730 строкам.)  
  - Результаты более 8 192 можно получить, сохраняя в переменной несколько строк.  

```tsql
DECLARE @v INT = 9000;
SELECT TOP (@v) … FROM … ORDER BY …
```

Однако константа в предложении **TOP** обеспечивает лучшую производительность, чем при использовании переменной.  

В [!INCLUDE[tsql](../../includes/tsql-md.md)] , скомпилированном в собственном коде, эти ограничения не применяются к интерпретированному доступу [!INCLUDE[tsql](../../includes/tsql-md.md)] оптимизированных для памяти таблиц.  


##  <a name="dml"></a> Изменение данных  

Поддерживаются следующие инструкции DML:  

-   INSERT VALUES (по одной строке на каждую инструкцию) и INSERT...; SELECT  

-   UPDATE  

-   DELETE  

-   предложение WHERE поддерживается вместе с инструкциями UPDATE и DELETE.  

##  <a name="cof"></a> Язык управления потоком  
 Поддерживаются следующие конструкции языка управления потоком:  

-   [IF...ELSE &#40;Transact-SQL&#41;](../../t-sql/language-elements/if-else-transact-sql.md)  

-   [WHILE &#40;Transact-SQL&#41;](../../t-sql/language-elements/while-transact-sql.md)  

-   [RETURN &#40;Transact-SQL&#41;](../../t-sql/language-elements/return-transact-sql.md)  

-   [DECLARE @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/declare-local-variable-transact-sql.md) может использовать все [поддерживаемые типы данных для выполняющейся в памяти OLTP](../../relational-databases/in-memory-oltp/supported-data-types-for-in-memory-oltp.md), а также оптимизированные для памяти типы таблиц. Переменные могут быть объявлены как NULL или NOT NULL;  

-   [SET @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/set-local-variable-transact-sql.md)  

-   [TRY...CATCH &#40;Transact-SQL&#41;](../../t-sql/language-elements/try-catch-transact-sql.md)  

               To achieve optimal performance, use a single TRY/CATCH block for an entire natively compiled T-SQL module.  

-   [THROW &#40;Transact-SQL&#41;](../../t-sql/language-elements/throw-transact-sql.md)  

-   BEGIN ATOMIC (на внешнем уровне хранимой процедуры). Дополнительные сведения см. в разделе [Atomic Blocks](../../relational-databases/in-memory-oltp/atomic-blocks-in-native-procedures.md).  

##  <a name="so"></a> Поддерживаемые операторы  
 Поддерживаются следующие операторы.  

-   [Операторы сравнения (Transact-SQL)](../../t-sql/language-elements/comparison-operators-transact-sql.md) (например, >, \<, >= и <=)  

-   Унарные операторы (+, -).  

-   Двоичные операторы (*,/, +, -, % (остаток от деления)).  

               The plus operator (+) is supported on both numbers and strings.  

-   Логические операторы (AND, OR, NOT).  

-   Битовые операторы ~, &, |, и ^  

-   APPLY, оператор
    - **Applies to:** [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] CTP 1.1.  
      Начиная с версии [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] CTP 1.1 оператор APPLY поддерживается в модулях, скомпилированных в собственном коде.

##  <a name="bfncsp"></a> Встроенные функции в модулях, скомпилированных в собственном коде  
 В ограничениях таблиц, оптимизированных для памяти, и в модулях, скомпилированных в собственном коде T-SQL, поддерживаются следующие функции.  

-   Все [математические функции (Transact-SQL)](../../t-sql/functions/mathematical-functions-transact-sql.md)  

-   Функции для работы с датами: CURRENT_TIMESTAMP, DATEADD, DATEDIFF, DATEFROMPARTS, DATEPART, DATETIME2FROMPARTS, DATETIMEFROMPARTS, DAY, EOMONTH, GETDATE, GETUTCDATE, MONTH, SMALLDATETIMEFROMPARTS, SYSDATETIME, SYSUTCDATETIME и YEAR.  

-   Строковые функции: LEN, LTRIM, RTRIM и SUBSTRING.  
    - **Applies to:** [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] CTP 1.1.  
      Начиная с версии [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] CTP 1.1 также поддерживаются следующие встроенные функции: TRIM, TRANSLATE и CONCAT_WS.  

-   Функции идентификации: SCOPE_IDENTITY.  

-   NULL-функции: ISNULL  

-   Функции уникальных идентификаторов: NEWID и NEWSEQUENTIALID  

-   Функции JSON  
    - **Applies to:** [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] CTP 1.1.  
      Начиная с версии [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] CTP 1.1 функции JSON поддерживаются в модулях, скомпилированных в собственном коде.

-   Функции обработки ошибок: ERROR_LINE, ERROR_MESSAGE, ERROR_NUMBER, ERROR_PROCEDURE, ERROR_SEVERITY и ERROR_STATE.  

-   Системные функции: @@rowcount. Инструкции в хранимых процедурах, скомпилированных в собственном коде, обновляют @@rowcount, и вы можете использовать @@rowcount в таких процедурах для определения числа строк, затронутых последней инструкцией, выполненной в пределах этой хранимой процедуры. Но @@rowcount сбрасывается до 0 в начале и в конце выполнения каждой хранимой процедуры, скомпилированной в собственном коде.  

-   Функции безопасности: IS_MEMBER({'group' | 'role'}), IS_ROLEMEMBER ('role' [, 'database_principal']), IS_SRVROLEMEMBER ('role' [, 'login']), ORIGINAL_LOGIN(), SESSION_USER, CURRENT_USER, SUSER_ID(['login']), SUSER_SID(['login'] [, Param2]), SUSER_SNAME([server_user_sid]), SYSTEM_USER, SUSER_NAME, USER, USER_ID(['user']), USER_NAME([id]), CONTEXT_INFO().

-   Выполнение собственных модулей может быть вложенным.

##  <a name="auditing"></a> Аудит  
 Аудит на уровне процедуры поддерживается для хранимых процедур, скомпилированных в собственном коде.  

 Дополнительные сведения об аудите см. в разделе [Create a Server Audit and Database Audit Specification](../../relational-databases/security/auditing/create-a-server-audit-and-database-audit-specification.md).  

##  <a name="tqh"></a> Табличные указания и указания запросов  
 Поддерживаются следующие конструкции:  

-   Табличные указания INDEX, FORCESCAN и FORCESEEK в синтаксисе табличных указаний или в [предложении OPTION (Transact-SQL)](../../t-sql/queries/option-clause-transact-sql.md) запроса. Дополнительные сведения см. в разделе [Табличные указания (Transact-SQL)](../../t-sql/queries/hints-transact-sql-table.md).  

-   FORCE ORDER  

-   указание LOOP JOIN;  

-   OPTIMIZE FOR  

 Дополнительные сведения см. в разделе [Указания запросов (Transact-SQL)](../../t-sql/queries/hints-transact-sql-query.md).  

##  <a name="los"></a> Ограничения на сортировку  
 В запросе с использованием [TOP (Transact-SQL)](../../t-sql/queries/top-transact-sql.md) и [предложения ORDER BY (Transact-SQL)](../../t-sql/queries/select-order-by-clause-transact-sql.md) можно сортировать более 8 000 строк. Без [предложения ORDER BY (Transact-SQL)](../../t-sql/queries/select-order-by-clause-transact-sql.md) [TOP (Transact-SQL)](../../t-sql/queries/top-transact-sql.md) позволяет сортировать не более 8 000 строк (меньше, если есть соединения).  

 Если в запросе используется как оператор [TOP (Transact-SQL)](../../t-sql/queries/top-transact-sql.md), так и [предложение ORDER BY (Transact-SQL)](../../t-sql/queries/select-order-by-clause-transact-sql.md), для оператора TOP можно указать не более 8192 строк. Если строк будет больше, чем 8192, вы получите такое сообщение об ошибке: **сообщение 41398, уровень 16, состояние 1, процедура *\<имя_процедуры>*, строка *\<номер_строки>*. Оператор TOP может возвратить не более 8192 строк; запрошенное число: *\<число>*.**  

 Если отсутствует предложение TOP, то можно отсортировать любое количество строк с помощью предложения ORDER BY.  

 Если не используется предложение ORDER BY, то можно использовать любое целочисленное значение с оператором TOP.  

 Пример для оператора TOP с числом значений 8192: компиляция  

```tsql  
CREATE PROCEDURE testTop  
WITH EXECUTE AS OWNER, SCHEMABINDING, NATIVE_COMPILATION  
  AS  
  BEGIN ATOMIC WITH (TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = N'us_english')  
    SELECT TOP 8192 ShoppingCartId, CreatedDate, TotalPrice FROM dbo.ShoppingCart  
    ORDER BY ShoppingCartId DESC  
  END;  
GO  
```

 Пример для оператора TOP с числом значений > 8192: сбой компиляции.  

```tsql  
CREATE PROCEDURE testTop  
WITH EXECUTE AS OWNER, SCHEMABINDING, NATIVE_COMPILATION  
  AS  
  BEGIN ATOMIC WITH (TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = N'us_english')  
    SELECT TOP 8193 ShoppingCartId, CreatedDate, TotalPrice FROM dbo.ShoppingCart  
    ORDER BY ShoppingCartId DESC  
  END;  
GO  
```

 Ограничение в 8192 строки применяется только к `TOP N`, где `N` является константой, как показано в предыдущих примерах.  Если нужно, чтобы `N` было больше 8192, можно присвоить это значение переменной и использовать ее с оператором `TOP`.  

 Пример использования переменной: компиляция  

```tsql  
CREATE PROCEDURE testTop  
WITH EXECUTE AS OWNER, SCHEMABINDING, NATIVE_COMPILATION  
  AS  
  BEGIN ATOMIC WITH (TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = N'us_english')  
    DECLARE @v int = 8193   
    SELECT TOP (@v) ShoppingCartId, CreatedDate, TotalPrice FROM dbo.ShoppingCart  
    ORDER BY ShoppingCartId DESC  
  END;  
GO  
```

 **Ограничения возвращаемых строк:** существует два варианта, когда возможно уменьшение числа строк, возвращаемых оператором TOP:  

-   Использование соединений в запросе.  Влияние соединений на ограничения зависит от плана запроса.  

-   Использование агрегатных функций или ссылки на агрегатные функции в предложении ORDER BY.  

 Формула для вычисления наименьшего поддерживаемого значения N в предложении TOP N выглядит следующим образом: `N = floor ( 65536 / number_of_tables * 8 + total_size+of+aggs )`.  

## <a name="see-also"></a>См. также  
 [Скомпилированные в собственном коде хранимые процедуры](../../relational-databases/in-memory-oltp/natively-compiled-stored-procedures.md)   
 [Проблемы миграции, связанные с хранимыми процедурами, скомпилированными в собственном коде](../../relational-databases/in-memory-oltp/migration-issues-for-natively-compiled-stored-procedures.md)  



