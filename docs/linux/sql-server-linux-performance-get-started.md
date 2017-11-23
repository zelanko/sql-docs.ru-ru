---
title: "Начало работы с функциями производительности SQL Server для Linux | Документы Microsoft"
description: "В этом разделе содержатся вводные производительности компонентов SQL Server для Linux пользователей, незнакомых с SQL Server. Многие из этих примеров работать на всех платформах, но в контексте данной статьи является Linux."
author: rothja
ms.author: jroth
manager: jhubbard
ms.date: 03/17/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: linux
ms.suite: sql
ms.technology: database-engine
ms.assetid: 60036d26-4797-4872-9a9e-3552841c61be
ms.custom: 
ms.workload: Inactive
ms.openlocfilehash: 07e274f33decd59287571017d8103961334f9df4
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="walkthrough-for-the-performance-features-of-sql-server-on-linux"></a>Пошаговое руководство для повышения производительности SQL Server в Linux

Если вы являетесь пользователем Linux, новые для SQL Server, следующие задачи описывают некоторые средства производительности. Это не уникальным или уникальным для Linux, а также дает общее представление областей для дальнейшего анализа. В каждом примере ссылка предоставляется документации глубины для этой области.

> [!NOTE]
> В следующих примерах используется образец базы данных AdventureWorks. Инструкции о том, как получить и установить этот образец базы данных см. в разделе [восстановление базы данных SQL Server из Windows, Linux](sql-server-linux-migrate-restore-database.md).

## <a name="create-a-columnstore-index"></a>создать индекс columnstore
Индекс columnstore — это технология хранения и запрашивания больших хранилищ данных в формате данных в один столбец, называемого columnstore.  

1. Добавьте индекс Columnstore в таблице SalesOrderDetail, выполнив ниже T-SQL:

   ```sql
   CREATE NONCLUSTERED COLUMNSTORE INDEX [IX_SalesOrderDetail_ColumnStore]
      ON Sales.SalesOrderDetail
      (UnitPrice, OrderQty, ProductID)
   GO
   ```

2. Выполните следующий запрос, который будет использовать индекс Columnstore для поиска в таблице:

   ```sql
   SELECT ProductID, SUM(UnitPrice) SumUnitPrice, AVG(UnitPrice) AvgUnitPrice,
      SUM(OrderQty) SumOrderQty, AVG(OrderQty) AvgOrderQty
   FROM Sales.SalesOrderDetail
      GROUP BY ProductID
      ORDER BY ProductID
   ```

3. Убедитесь, что индекс Columnstore был использован с путем поиска object_id для индекса Columnstore и подтверждения того, что он отображается в статистику использования для таблицы SalesOrderDetail:

   ```sql
   SELECT * FROM sys.indexes WHERE name = 'IX_SalesOrderDetail_ColumnStore'
   GO

   SELECT * 
   FROM sys.dm_db_index_usage_stats
      WHERE database_id = DB_ID('AdventureWorks')
      AND object_id = OBJECT_ID('AdventureWorks.Sales.SalesOrderDetail');
   ```
   
## <a name="use-in-memory-oltp"></a>Использование In-Memory OLTP
SQL Server предоставляет функции выполнения OLTP в памяти, позволяющие значительно повысить производительность приложений систем.  В этом разделе руководства по оценке поможет выполнить шаги для создания оптимизированной для памяти таблице, хранящейся в памяти и скомпилированными в собственном коде хранимой процедуры, доступ к таблице без необходимости компиляции или интерпретации.

### <a name="configure-database-for-in-memory-oltp"></a>Настройка базы данных для In-Memory OLTP
1. Рекомендуется установить уровень совместимости не менее 130 для использования OLTP в памяти базы данных.  Используйте приведенный ниже запрос для проверки текущий уровень совместимости базы данных AdventureWorks:  

   ```sql
   USE AdventureWorks
   GO
   SELECT d.compatibility_level
   FROM sys.databases as d
     WHERE d.name = Db_Name();
   GO
   ```
   
   При необходимости обновите уровень до 130:

   ```sql
   ALTER DATABASE CURRENT
   SET COMPATIBILITY_LEVEL = 130;
   GO
   ```

2. Если в транзакции участвует дисковой таблицы и таблицы, оптимизированные для памяти, его основные, оптимизированных для памяти часть транзакции выполнялась на уровень изоляции транзакции с именем моментального СНИМКА.  Чтобы гарантированно обеспечить этот уровень для оптимизированных для памяти таблиц в межконтейнерной транзакции, выполните следующее:

   ```sql
   ALTER DATABASE CURRENT SET MEMORY_OPTIMIZED_ELEVATE_TO_SNAPSHOT=ON
   GO
   ```

3. Перед созданием оптимизированной для памяти таблицы, необходимо сначала создать файловую ГРУППУ оптимизированной памяти и контейнер для файлов данных:

   ```sql
   ALTER DATABASE AdventureWorks ADD FILEGROUP AdventureWorks_mod CONTAINS memory_optimized_data
   GO  
   ALTER DATABASE AdventureWorks ADD FILE (NAME='AdventureWorks_mod', FILENAME='/var/opt/mssql/data/AdventureWorks_mod') TO FILEGROUP AdventureWorks_mod
   GO
   ```

### <a name="create-a-memory-optimized-table"></a>Создание таблицы, оптимизированные для памяти
Основным хранилищем для оптимизированных для памяти таблиц является основной памяти и поэтому в отличие от таблиц на диске, данных необязательно для чтения в с диска в буферов памяти.  Чтобы создать таблицу, оптимизированную для памяти, используйте MEMORY_OPTIMIZED = ON предложения.

1. Выполните следующий запрос для создания оптимизированной для памяти таблицы dbo. ShoppingCart.  По умолчанию данные будут сохранены на диске с целью увеличения устойчивости (Обратите внимание, что УСТОЙЧИВОСТЬ можно также задать для сохранения только схема). 

   ```sql
   CREATE TABLE dbo.ShoppingCart ( 
   ShoppingCartId INT IDENTITY(1,1) PRIMARY KEY NONCLUSTERED,
   UserId INT NOT NULL INDEX ix_UserId NONCLUSTERED HASH WITH (BUCKET_COUNT=1000000), 
   CreatedDate DATETIME2 NOT NULL, 
   TotalPrice MONEY
   ) WITH (MEMORY_OPTIMIZED=ON) 
   GO
   ```

2. Вставьте некоторые записи в таблице:

   ```sql
   INSERT dbo.ShoppingCart VALUES (8798, SYSDATETIME(), NULL) 
   INSERT dbo.ShoppingCart VALUES (23, SYSDATETIME(), 45.4) 
   INSERT dbo.ShoppingCart VALUES (80, SYSDATETIME(), NULL) 
   INSERT dbo.ShoppingCart VALUES (342, SYSDATETIME(), 65.4) 
   ```

### <a name="natively-compiled-stored-procedure"></a>Скомпилированные в собственном коде хранимой процедуры
SQL Server поддерживает скомпилированных хранимых процедур, которые обращаются к таблицам, оптимизированным для памяти. Инструкции T-SQL компилируются в машинный код и хранятся в виде собственных библиотек DLL, обеспечивая более быстрый доступ к данным и более эффективное выполнение запросов, чем традиционные T-SQL.   Хранимые процедуры, которые отмечены как NATIVE_COMPILATION, компилируются в собственном коде. 

1. Выполните следующий скрипт для создания скомпилированных в собственном коде хранимую процедуру, которая вставляет большого количества записей в таблице ShoppingCart:


   ```sql
   CREATE PROCEDURE dbo.usp_InsertSampleCarts @InsertCount int 
    WITH NATIVE_COMPILATION, SCHEMABINDING AS 
   BEGIN ATOMIC 
   WITH (TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = N'us_english')

   DECLARE @i int = 0

   WHILE @i < @InsertCount 
    BEGIN 
     INSERT INTO dbo.ShoppingCart VALUES (1, SYSDATETIME() , NULL) 
     SET @i += 1 
    END
   END 
   ```
2. Вставка 1 000 000 строк:

   ```sql
   EXEC usp_InsertSampleCarts 1000000 
   ```

3. Убедитесь, что вставленные строки:

   ```sql
   SELECT COUNT(*) FROM dbo.ShoppingCart 
   ```

### <a name="learn-more-about-in-memory-oltp"></a>Дополнительные сведения об In-Memory OLTP
Дополнительные сведения об In-Memory OLTP см. в следующих разделах:

- [Краткое руководство 1. Технологии выполнения OLTP в памяти для повышения производительности службы Transact-SQL](../relational-databases/in-memory-oltp/survey-of-initial-areas-in-in-memory-oltp.md)
- [Миграция в In-Memory OLTP](../relational-databases/in-memory-oltp/migrating-to-in-memory-oltp.md)
- [Улучшение производительности временной таблицы и табличной переменной с помощью оптимизации памяти](../relational-databases/in-memory-oltp/faster-temp-table-and-table-variable-by-using-memory-optimization.md)
- [Мониторинг и устранение неполадок с использованием памяти](../relational-databases/in-memory-oltp/monitor-and-troubleshoot-memory-usage.md)
- [In-Memory OLTP (оптимизация в памяти)](../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)

## <a name="use-query-store"></a>Использование хранилища запросов
Хранилище запросов собирает сведения о запросах, планы выполнения и статистику выполнения подробные производительности.

Хранилище запросов не активен по умолчанию и может быть включен с помощью инструкции ALTER DATABASE:

   ```sql
   ALTER DATABASE AdventureWorks SET QUERY_STORE = ON;
   ```

Выполните следующий запрос для возврата сведений о запросах и планах в хранилище запросов: 

   ```sql
   SELECT Txt.query_text_id, Txt.query_sql_text, Pl.plan_id, Qry.*
   FROM sys.query_store_plan AS Pl
      JOIN sys.query_store_query AS Qry
         ON Pl.query_id = Qry.query_id
      JOIN sys.query_store_query_text AS Txt
         ON Qry.query_text_id = Txt.query_text_id ;
   ```

## <a name="query-dynamic-management-views"></a>Запрос динамического административного представления
Динамические административные представления возвращают сведения о состоянии сервера, который может использоваться для отслеживания работоспособности экземпляра сервера, диагностики проблем и настройки производительности.

Для запроса к динамическому административному представлению dm_os_wait статистики:

   ```sql
   SELECT wait_type, wait_time_ms
   FROM sys.dm_os_wait_stats;
   ```
