---
title: Начало работы с функциями повышения производительности в SQL Server на Linux
description: В этой статье приводятся общие сведения о функциях повышения производительности SQL Server для пользователей Linux, не знакомых с SQL Server. Многие из этих примеров могут работать на всех платформах, однако в первую очередь эта статья ориентирована на Linux.
author: VanMSFT
ms.author: vanto
ms.date: 03/17/2017
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.assetid: 60036d26-4797-4872-9a9e-3552841c61be
ms.openlocfilehash: fe60b00654d93c6362a8671318a4b7b88ae90a5f
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "67896165"
---
# <a name="walkthrough-for-the-performance-features-of-sql-server-on-linux"></a>Пошаговое руководство по функциям повышения производительности в SQL Server на Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Если вы работаете с Linux и еще не знакомы с SQL Server, ознакомьтесь со следующими задачами, которые демонстрируют некоторые функции повышения производительности. Они не являются уникальными для Linux и лишь задают общие направления для дальнейшего изучения. В каждом примере приводится ссылка на подробную документацию по соответствующей теме.

> [!NOTE]
> Ниже приводятся примеры базы данных AdventureWorks. Инструкции по получению и установке этого образца базы данных см. в статье [Восстановление базы данных SQL Server из Windows в Linux](sql-server-linux-migrate-restore-database.md).

## <a name="create-a-columnstore-index"></a>создать индекс columnstore
Индекс columnstore — это технология хранения и запроса больших объемов данных с использованием формата хранения данных в столбцах, называемого columnstore.  

1. Добавьте индекс columnstore в таблицу SalesOrderDetail. Для этого выполните следующие команды Transact-SQL:

   ```sql
   CREATE NONCLUSTERED COLUMNSTORE INDEX [IX_SalesOrderDetail_ColumnStore]
      ON Sales.SalesOrderDetail
      (UnitPrice, OrderQty, ProductID)
   GO
   ```

2. Выполните следующий запрос, который использует индекс columnstore для сканирования таблицы:

   ```sql
   SELECT ProductID, SUM(UnitPrice) SumUnitPrice, AVG(UnitPrice) AvgUnitPrice,
      SUM(OrderQty) SumOrderQty, AVG(OrderQty) AvgOrderQty
   FROM Sales.SalesOrderDetail
      GROUP BY ProductID
      ORDER BY ProductID
   ```

3. Убедитесь, что использовался индекс columnstore. Для этого проверьте значение object_id для индекса columnstore и убедитесь, что оно появляется в статистике использования таблицы SalesOrderDetail:

   ```sql
   SELECT * FROM sys.indexes WHERE name = 'IX_SalesOrderDetail_ColumnStore'
   GO

   SELECT * 
   FROM sys.dm_db_index_usage_stats
      WHERE database_id = DB_ID('AdventureWorks')
      AND object_id = OBJECT_ID('AdventureWorks.Sales.SalesOrderDetail');
   ```
   
## <a name="use-in-memory-oltp"></a>Использование выполняющейся в памяти OLTP
SQL Server позволяет использовать функции выполняющейся в памяти OLTP, позволяющие значительно повысить производительность систем приложений.  В этом разделе ознакомительного руководства приводятся пошаговые инструкции по созданию оптимизированной для памяти таблицы, хранящейся в памяти, а также скомпилированной в собственном коде хранимой процедуры, которая осуществляет доступ к таблице без необходимости компиляции или интерпретации.

### <a name="configure-database-for-in-memory-oltp"></a>Настройка базы данных для выполняющейся в памяти OLTP
1. Для использования выполняющейся в памяти OLTP рекомендуется задавать для базы данных уровень совместимости не ниже 130.  Используйте следующий запрос для проверки текущего уровня совместимости AdventureWorks:  

   ```sql
   USE AdventureWorks
   GO
   SELECT d.compatibility_level
   FROM sys.databases as d
     WHERE d.name = Db_Name();
   GO
   ```
   
   При необходимости установите уровень 130:

   ```sql
   ALTER DATABASE CURRENT
   SET COMPATIBILITY_LEVEL = 130;
   GO
   ```

2. В транзакции, которая задействует размещенные на диске и оптимизированные для памяти таблицы, очень важно обеспечить, чтобы оптимизированная для памяти часть транзакции выполнялась на уровне изоляции транзакции, который называется "моментальный снимок".  Чтобы гарантированно обеспечить этот уровень для оптимизированных для памяти таблиц в межконтейнерной транзакции, выполните следующую команду:

   ```sql
   ALTER DATABASE CURRENT SET MEMORY_OPTIMIZED_ELEVATE_TO_SNAPSHOT=ON
   GO
   ```

3. Прежде чем создать таблицу, оптимизированную для памяти, необходимо сначала создать оптимизированную для памяти файловую группу и контейнер для файлов данных:

   ```sql
   ALTER DATABASE AdventureWorks ADD FILEGROUP AdventureWorks_mod CONTAINS memory_optimized_data
   GO  
   ALTER DATABASE AdventureWorks ADD FILE (NAME='AdventureWorks_mod', FILENAME='/var/opt/mssql/data/AdventureWorks_mod') TO FILEGROUP AdventureWorks_mod
   GO
   ```

### <a name="create-a-memory-optimized-table"></a>Создание оптимизированной для памяти таблицы
Оптимизированные для памяти таблицы размещаются преимущественно в основной памяти. Благодаря этому не приходится считывать данные с диска в буферы памяти.  Чтобы создать оптимизированную для памяти таблицу, используйте предложение MEMORY_OPTIMIZED = ON.

1. Выполните следующий запрос, чтобы создать оптимизированную для памяти таблицу dbo.ShoppingCart.  По умолчанию для обеспечения устойчивости данные будут сохраняться на диске (обратите внимание, что в целях обеспечения устойчивости может быть настроено сохранение только схемы). 

   ```sql
   CREATE TABLE dbo.ShoppingCart ( 
   ShoppingCartId INT IDENTITY(1,1) PRIMARY KEY NONCLUSTERED,
   UserId INT NOT NULL INDEX ix_UserId NONCLUSTERED HASH WITH (BUCKET_COUNT=1000000), 
   CreatedDate DATETIME2 NOT NULL, 
   TotalPrice MONEY
   ) WITH (MEMORY_OPTIMIZED=ON) 
   GO
   ```

2. Вставьте в таблицу несколько записей:

   ```sql
   INSERT dbo.ShoppingCart VALUES (8798, SYSDATETIME(), NULL) 
   INSERT dbo.ShoppingCart VALUES (23, SYSDATETIME(), 45.4) 
   INSERT dbo.ShoppingCart VALUES (80, SYSDATETIME(), NULL) 
   INSERT dbo.ShoppingCart VALUES (342, SYSDATETIME(), 65.4) 
   ```

### <a name="natively-compiled-stored-procedure"></a>Скомпилированная в собственном коде хранимая процедура
SQL Server поддерживает скомпилированные в собственном коде хранимые процедуры, которые обращаются к таблицам, оптимизированным для памяти. Инструкции T-SQL компилируются в машинный код и сохраняются в виде собственных библиотек DLL, благодаря чему обеспечивается более быстрый доступ к данным и повышение эффективности выполнения запросов по сравнению с традиционным T-SQL.   Хранимые процедуры, которые отмечены как NATIVE_COMPILATION, компилируются в собственном коде. 

1. Выполните следующий скрипт, чтобы создать скомпилированную в собственном коде хранимую процедуру, которая вставляет большое количество записей в таблицу ShoppingCart:


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
2. Вставка 1 000 000 строк:

   ```sql
   EXEC usp_InsertSampleCarts 1000000 
   ```

3. Проверка успешной вставки строк:

   ```sql
   SELECT COUNT(*) FROM dbo.ShoppingCart 
   ```

### <a name="learn-more-about-in-memory-oltp"></a>Дополнительные сведения о выполняющейся в памяти OLTP
Дополнительные сведения о выполняющейся в памяти OLTP см. в следующих разделах:

- [Краткое руководство 1. Технологии выполнения OLTP в памяти для повышения производительности службы Transact-SQL](../relational-databases/in-memory-oltp/survey-of-initial-areas-in-in-memory-oltp.md)
- [Миграция в In-Memory OLTP](../relational-databases/in-memory-oltp/migrating-to-in-memory-oltp.md)
- [Улучшение производительности временной таблицы и табличной переменной с помощью оптимизации памяти](../relational-databases/in-memory-oltp/faster-temp-table-and-table-variable-by-using-memory-optimization.md)
- [Мониторинг и устранение неполадок с использованием памяти](../relational-databases/in-memory-oltp/monitor-and-troubleshoot-memory-usage.md)
- [In-Memory OLTP (оптимизация в памяти)](../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)

## <a name="use-query-store"></a>Использование хранилища запросов
В хранилище запросов сохраняются подробные сведения о производительности запросов, планов выполнения и статистики времени выполнения.

Хранилище запросов по умолчанию неактивно и может быть включено с помощью инструкции ALTER DATABASE:

   ```sql
   ALTER DATABASE AdventureWorks SET QUERY_STORE = ON;
   ```

Выполните следующий запрос, который возвращает сведения о запросах и планах в хранилище запросов: 

   ```sql
   SELECT Txt.query_text_id, Txt.query_sql_text, Pl.plan_id, Qry.*
   FROM sys.query_store_plan AS Pl
      JOIN sys.query_store_query AS Qry
         ON Pl.query_id = Qry.query_id
      JOIN sys.query_store_query_text AS Txt
         ON Qry.query_text_id = Txt.query_text_id ;
   ```

## <a name="query-dynamic-management-views"></a>Запрос динамических административных представлений
Динамические административные представления возвращают данные о состоянии сервера, которые могут использоваться для мониторинга работоспособности экземпляра сервера, диагностики проблем и настройки производительности.

Запрос динамического административного представления статистики dm_os_wait:

   ```sql
   SELECT wait_type, wait_time_ms
   FROM sys.dm_os_wait_stats;
   ```
