---
title: Поддерживаемые конструкции в хранимых процедурах, скомпилированных в собственном виде | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 05515013-28b5-4ccf-9a54-ae861448945b
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b4fd1a406848006739b83c1b8a0886d5c2d4bdfa
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "63155718"
---
# <a name="supported-constructs-in-natively-compiled-stored-procedures"></a>Поддерживаемые конструкции для хранимых процедур, скомпилированных в собственном коде
  Этот раздел содержит список поддерживаемых функций для хранимых процедур, скомпилированных в собственном виде ([Создание процедуры &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-procedure-transact-sql)):  
  
-   [Возможности программирования в хранимых процедурах, скомпилированных в собственном коде](#pncsp)  
  
-   [Поддерживаемые операторы](#so)  
  
-   [Встроенные функции в хранимых процедурах, скомпилированных в собственном коде](#bfncsp)  
  
-   [Контактная зона запросов в хранимых процедурах, скомпилированных в собственном коде](#qsancsp)  
  
-   [Аудит](#auditing)  
  
-   [Таблица, запрос и указания по соединению](#tqh)  
  
-   [Ограничения на сортировку](#los)  
  
 Сведения о типах данных, поддерживаемых в скомпилированных в собственном коде хранимых процедурах, см. в разделе [Supported Data Types](supported-data-types-for-in-memory-oltp.md).  
  
 Полные сведения о неподдерживаемых конструкциях и о том, как обойти некоторые неподдерживаемые функции в хранимых процедурах, скомпилированных в собственном коде, см. в разделе [Migration Issues for Natively Compiled Stored Procedures](migration-issues-for-natively-compiled-stored-procedures.md). Дополнительные сведения о неподдерживаемых компонентах см. в разделе [Конструкции языка Transact-SQL, неподдерживаемые в In-Memory OLTP](transact-sql-constructs-not-supported-by-in-memory-oltp.md).  
  
##  <a name="pncsp"></a>Программирование в хранимых процедурах, скомпилированных в собственном режиме  
 Поддерживаются следующие конструкции:  
  
-   BEGIN ATOMIC (на внешнем уровне хранимой процедуры), LANGUAGE, ISOLATION LEVEL, DATEFORMAT и DATEFIRST.  
  
-   Объявление переменной как NULL или NOT NULL. Если переменная объявлена как NOT NULL, то объявление должно иметь инициализатор. Если переменная не объявлена как NOT NULL, инициализатор не обязателен.  
  
-   IF и WHILE  
  
-   INSERT/UPDATE/DELETE  
  
     Вложенные запросы не поддерживаются. В предложениях WHERE и HAVING предложения AND и BETWEEN поддерживаются; OR, NOT и IN не поддерживаются.  
  
-   Оптимизированные для памяти табличные типы и табличные переменные.  
  
-   RETURN  
  
-   SELECT  
  
-   SET  
  
-   TRY/CATCH/THROW  
  
     Чтобы улучшить производительность, используйте один блок TRY/CATCH для всей хранимой процедуры, скомпилированной в собственном коде.  
  
##  <a name="so"></a>Поддерживаемые операторы  
 Поддерживаются следующие операторы.  
  
-   [Операторы сравнения &#40;&#41;Transact-SQL](/sql/t-sql/language-elements/comparison-operators-transact-sql) (например, >, \<, >= и <=) поддерживаются в условных выражениях (если, while).  
  
-   Унарные операторы (+, -).  
  
-   Двоичные операторы (*,/, +, -, % (остаток от деления)).  
  
     Оператор плюс (+) поддерживается как для чисел, так и в строках.  
  
-   Логические операторы (AND, OR, NOT). Операторы OR и NOT поддерживаются в инструкциях IF и WHILE, но не в предложениях WHERE или HAVING.  
  
-   Битовые операторы ~, &, |, и ^  
  
##  <a name="bfncsp"></a>Встроенные функции в хранимых процедурах, скомпилированных в собственном виде  
 Следующие функции поддерживаются в ограничениях по умолчанию для оптимизированных для памяти таблиц и в хранимых процедурах, скомпилированных в собственном коде.  
  
-   Математические функции: ACOS, ASIN, ATAN, ATN2, COS, COT, DEGREES, EXP, LOG, LOG10, PI, POWER, RADIANS, RAND, SIN, SQRT, SQUARE и TAN  
  
-   Функции даты: CURRENT_TIMESTAMP, DATEADD, DATEDIFF, DATEFROMPARTS, DATEPART, DATETIME2FROMPARTS, DATETIMEFROMPARTS, DAY, EOMONTH, GETDATE, GETUTCDATE, MONTH, SMALLDATETIMEFROMPARTS, SYSDATETIME, SYSUTCDATETIME и YEAR.  
  
-   Строковые функции: LEN, LTRIM, RTRIM и SUBSTRING  
  
-   Функция идентификации: SCOPE_IDENTITY  
  
-   NULL-функции: ISNULL  
  
-   Функции уникальных идентификаторов: NEWID и NEWSEQUENTIALID  
  
-   Функции ошибок: ERROR_LINE, ERROR_MESSAGE, ERROR_NUMBER, ERROR_PROCEDURE, ERROR_SEVERITY и ERROR_STATE  
  
-   Преобразования: CAST и CONVERT. Не поддерживаются преобразования между символьными строками в Юникоде и отличными от Юникода (n(var)char и (var)char).  
  
-   Системные функции: @@rowcount. Инструкции в хранимых процедурах, скомпилированных в собственном коде, обновляют @@rowcount, и вы можете использовать @@rowcount в таких процедурах для определения числа строк, затронутых последней инструкцией, выполненной в пределах этой хранимой процедуры. Но @@rowcount сбрасывается до 0 в начале и в конце выполнения каждой хранимой процедуры, скомпилированной в собственном коде.  
  
##  <a name="qsancsp"></a>Контактная зона запроса в скомпилированных в собственном режиме хранимых процедурах  
 Поддерживаются следующие конструкции:  
  
-   BETWEEN  
  
-   Псевдонимы имен столбцов (с помощью синтаксиса AS или =).  
  
-   CROSS JOIN и INNER JOIN поддерживаются только с запросами SELECT.  
  
-   Выражения поддерживаются в списке SELECT, [где &#40;предложение&#41;Transact-SQL](/sql/t-sql/queries/where-transact-sql) , если они используют поддерживаемый оператор. Список поддерживаемых в настоящее время операторов см. в разделе [Supported Operators](#so) .  
  
-   Предикат фильтра IS [NOT] NULL  
  
-   ИЗ \<оптимизированной для памяти таблицы>  
  
-   Поддерживается [группирование &#40;&#41;Transact-SQL](/sql/t-sql/queries/select-group-by-transact-sql) , а также агрегатные функции AVG, COUNT, COUNT_BIG, min, Max и Sum. Функции MIN и MAX не поддерживаются для типов nvarchar, char, varchar, varchar, varbinary и binary. [Предложение order by &#40;&#41;Transact-SQL](/sql/t-sql/queries/select-order-by-clause-transact-sql) поддерживается в инструкции [Group By &#40;transact-SQL&#41;](/sql/t-sql/queries/select-group-by-transact-sql) если выражение в списке ORDER BY отображается в списке Group By. Например, GROUP BY a + b ORDER BY a + b поддерживается; GROUP BY a, b ORDER BY a + b не поддерживается.  
  
-   HAVING, с соблюдением тех же ограничений, как в предложении WHERE.  
  
-   INSERT VALUES (по одной строке на каждую инструкцию) и SELECT INSERT  
  
-   УПОРЯДОЧИТЬ по <sup>1</sup>  
  
-   Предикаты без ссылки на столбец.  
  
-   DELETE, SELECT и UPDATE  
  
-   ПЕРВЫЕ <sup>1</sup>  
  
-   Присвоение переменных в списке предложения SELECT.  
  
-   ГДЕ... ПЕРЕТАСКИВАНИ  
  
 <sup>1</sup> ORDER BY и Top поддерживаются в хранимых процедурах, скомпилированных в собственном режиме, с некоторыми ограничениями.  
  
-   Не поддерживается `DISTINCT` в предложениях `SELECT` и `ORDER BY`.  
  
-   Не поддерживаются `WITH TIES` и `PERCENT` в предложении `TOP`.  
  
-   
  `TOP` совместно с `ORDER BY` не поддерживает более 8192 строк при использовании константы в предложении `TOP`. Это ограничение может быть понижено в случае, если запрос содержит соединения или агрегатные функции. (Например, с одним соединением (двумя таблицами) ограничение составляет 4 096 строк. С двумя соединениями (тремя таблицами) ограничение равно 2 730 строкам.)  
  
     Результаты более 8 192 можно получить, сохраняя в переменной несколько строк.  
  
    ```sql  
    DECLARE @v INT = 9000  
    SELECT TOP (@v) ... FROM ... ORDER BY ...  
    ```  
  
 Однако константа в предложении `TOP` обеспечивает лучшую производительность, чем при использовании переменной.  
  
 Эти ограничения не применяются к интерпретированному доступу [!INCLUDE[tsql](../../includes/tsql-md.md)] к оптимизированным для памяти таблицам.  
  
##  <a name="auditing"></a>Проведение  
 Аудит на уровне процедуры поддерживается для хранимых процедур, скомпилированных в собственном коде. Аудит уровня инструкций не поддерживается.  
  
 Дополнительные сведения об аудите см. в разделе [Создание спецификация аудита для сервера и базы данных](../security/auditing/create-a-server-audit-and-database-audit-specification.md).  
  
##  <a name="tqh"></a>Таблицы, запросы и указания по соединению  
 Поддерживаются следующие конструкции:  
  
-   Табличные указания INDEX, FORCESCAN и FORCESEEK в синтаксисе табличных указаний или в [предложении OPTION (Transact-SQL)](/sql/t-sql/queries/option-clause-transact-sql) запроса.  
  
-   FORCE ORDER  
  
-   INNER LOOP JOIN  
  
-   OPTIMIZE FOR  
  
 Дополнительные сведения см. в разделе [указания &#40;Transact-SQL&#41;](/sql/t-sql/queries/hints-transact-sql).  
  
##  <a name="los"></a>Ограничения на сортировку  
 В запросе с использованием [TOP (Transact-SQL)](/sql/t-sql/queries/top-transact-sql) и [предложения ORDER BY (Transact-SQL)](/sql/t-sql/queries/select-order-by-clause-transact-sql) можно сортировать более 8 000 строк. Без [предложения ORDER BY (Transact-SQL)](/sql/t-sql/queries/select-order-by-clause-transact-sql)[TOP (Transact-SQL)](/sql/t-sql/queries/top-transact-sql) позволяет сортировать не более 8 000 строк (меньше, если есть соединения).  
  
 Если в запросе используется как оператор [TOP (Transact-SQL)](/sql/t-sql/queries/top-transact-sql), так и [предложение ORDER BY (Transact-SQL)](/sql/t-sql/queries/select-order-by-clause-transact-sql), для оператора TOP можно указать не более 8192 строк. Если строк будет больше, чем 8192, вы получите такое сообщение об ошибке: **сообщение 41398, уровень 16, состояние 1, процедура *\<имя_процедуры>*, строка *\<номер_строки>*. Оператор TOP может возвратить не более 8192 строк; запрошенное число: *\<число>*.**  
  
 Если отсутствует предложение TOP, то можно отсортировать любое количество строк с помощью предложения ORDER BY.  
  
 Если не используется предложение ORDER BY, то можно использовать любое целочисленное значение с оператором TOP.  
  
 Пример для оператора TOP с числом значений 8192: компиляция  
  
```sql  
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
  
```sql  
CREATE PROCEDURE testTop  
WITH EXECUTE AS OWNER, SCHEMABINDING, NATIVE_COMPILATION  
  AS  
  BEGIN ATOMIC WITH (TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = N'us_english')  
    SELECT TOP 8193 ShoppingCartId, CreatedDate, TotalPrice FROM dbo.ShoppingCart  
    ORDER BY ShoppingCartId DESC  
  END;  
GO  
```  
  
 Ограничение в 8192 строки применяется только к `TOP N` , где `N` является константой, как показано в предыдущих примерах.  Если нужно, чтобы `N` было больше 8192, можно присвоить это значение переменной и использовать ее с оператором `TOP`.  
  
 Пример использования переменной: компиляция  
  
```sql  
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
  
 **Ограничения на возвращаемые строки:** Существует два случая, когда это может привести к сокращению числа строк, которые могут быть возвращены оператором TOP:  
  
-   Использование соединений в запросе.  Влияние соединений на ограничения зависит от плана запроса.  
  
-   Использование агрегатных функций или ссылки на агрегатные функции в предложении ORDER BY.  
  
 Формула для вычисления наименьшего поддерживаемого значения N в предложении TOP N выглядит следующим образом: `N = floor ( 65536 / number_of_tables * 8 + total_size+of+aggs )`.  
  
## <a name="see-also"></a>См. также:  
 [Скомпилированные в собственном код хранимые процедуры](natively-compiled-stored-procedures.md)   
 [Проблемы миграции, связанные с хранимыми процедурами, скомпилированными в собственном коде](migration-issues-for-natively-compiled-stored-procedures.md)  
  
  
