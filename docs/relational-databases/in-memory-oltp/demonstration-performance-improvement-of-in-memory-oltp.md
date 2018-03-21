---
title: "Демонстрация повышения производительности для выполняющейся в памяти OLTP | Документация Майкрософт"
ms.custom: 
ms.date: 08/19/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: in-memory-oltp
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine-imoltp
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c6def45d-d2d4-4d24-8068-fab4cd94d8cc
caps.latest.revision: 
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 9f221ee5c9da668b2327196fae73406a7a473bfd
ms.sourcegitcommit: 0d904c23663cebafc48609671156c5ccd8521315
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2018
---
# <a name="demonstration-performance-improvement-of-in-memory-oltp"></a>Демонстрация. Улучшение производительности выполняющейся в памяти OLTP
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

  Пример кода в этом разделе демонстрирует повышение производительности оптимизированных для памяти таблиц. Повышение производительности наблюдается, когда доступ к данным в оптимизированных для памяти таблицах осуществляется из традиционного интерпретированного [!INCLUDE[tsql](../../includes/tsql-md.md)]. Улучшение производительности будет даже заметнее, если доступ к данным в оптимизированной для памяти таблице выполняется из хранимой процедуры, скомпилированной в собственном коде (NCSProc).  
 
Чтобы ознакомиться с более подробной демонстрацией преимуществ выполняющейся в памяти OLTP в отношении производительности, см. [демонстрацию производительность выполняющейся в памяти OLTP версии 1.0](https://github.com/Microsoft/sql-server-samples/releases/tag/in-memory-oltp-demo-v1.0). 
  
 Пример кода, представленный в этой статье, является однопоточным и не позволяет воспользоваться преимуществами параллелизма выполняющейся в памяти OLTP. Рабочая нагрузка, которая использует параллелизм, получит более заметное повышение производительности. В этом примере кода показан только один аспект улучшения производительности — эффективность доступа к данным для вставки.  
  
 Улучшение производительности, обеспечиваемое оптимизированными для памяти таблицами, полностью реализуется, когда доступ к данным в этих таблицах осуществляется из NCSProc.  
  
## <a name="code-example"></a>Пример кода  
 В следующих подразделах описывается каждый шаг.  
  
### <a name="step-1a-prerequisite-if-using-includessnoversionincludesssnoversion-mdmd"></a>Шаг 1a. Предварительные требования при использовании [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
 Описанные здесь действия применяются, только если используется [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Они не применяются, если используется [!INCLUDE[ssSDSFull](../../includes/sssdsfull-md.md)]. Выполните следующие действия.  
  
1.  Подключитесь к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]с помощью среды SQL Server Management Studio, используя SSMS.exe. Можно также использовать любое другое аналогичное средство.  
  
2.  Вручную создайте каталог с именем **C:\data\\\**. Пример кода Transact SQL предполагает, что каталог уже существует.  
  
3.  Запустите короткий код T-SQL, чтобы создать базу данных и соответствующую оптимизированную для памяти файловую группу.  
  
```sql  
go  
CREATE DATABASE imoltp;    --  Transact-SQL  
go  
  
ALTER DATABASE imoltp ADD FILEGROUP [imoltp_mod]  
    CONTAINS MEMORY_OPTIMIZED_DATA;  
  
ALTER DATABASE imoltp ADD FILE  
    (name = [imoltp_dir], filename= 'c:\data\imoltp_dir')  
    TO FILEGROUP imoltp_mod;  
go  
  
USE imoltp;  
go  
```  
  
### <a name="step-1b-prerequisite-if-using-includesssdsfullincludessssdsfull-mdmd"></a>Шаг 1b. Предварительные требования при использовании [!INCLUDE[ssSDSFull](../../includes/sssdsfull-md.md)]  
 Описанные здесь действия применяются только в случае использования [!INCLUDE[ssSDSFull](../../includes/sssdsfull-md.md)]. Выполните следующие действия.  
  
1.  Выберите существующую тестовую базу данных, которая будет использоваться для примера кода.  
  
2.  При необходимости создайте тестовую базу данных на [портале Azure](http://portal.azure.com) с именем **imoltp**.  
  
 Инструкции по созданию базы данных на портале Azure см. в [руководстве по началу работы с базами данных SQL Azure](http://azure.microsoft.com/documentation/articles/sql-database-get-started).  
  
### <a name="step-2-create-memory-optimized-tables-and-ncsproc"></a>Шаг 2. Создание оптимизированных для памяти таблиц и NCSProc  
 На этом шаге создаются оптимизированные для памяти таблицы и хранимая процедура, скомпилированная в собственном коде (NCSProc). Выполните следующие действия.  
  
1.  Подключитесь к новой базе данных с помощью SSMS.exe.  
  
2.  Запустите следующий код T-SQL в базе данных.  
  
```sql  
go  
DROP PROCEDURE IF EXISTS ncsp;  
DROP TABLE IF EXISTS sql;  
DROP TABLE IF EXISTS hash_i;  
DROP TABLE IF EXISTS hash_c;  
go  
  
CREATE TABLE [dbo].[sql] (  
  c1 INT NOT NULL PRIMARY KEY,  
  c2 NCHAR(48) NOT NULL  
);  
go  
  
CREATE TABLE [dbo].[hash_i] (  
  c1 INT NOT NULL PRIMARY KEY NONCLUSTERED HASH WITH (BUCKET_COUNT=1000000),  
  c2 NCHAR(48) NOT NULL  
) WITH (MEMORY_OPTIMIZED=ON, DURABILITY = SCHEMA_AND_DATA);  
go  
  
CREATE TABLE [dbo].[hash_c] (  
  c1 INT NOT NULL PRIMARY KEY NONCLUSTERED HASH WITH (BUCKET_COUNT=1000000),  
  c2 NCHAR(48) NOT NULL  
) WITH (MEMORY_OPTIMIZED=ON, DURABILITY = SCHEMA_AND_DATA);  
go  
  
CREATE PROCEDURE ncsp  
    @rowcount INT,  
    @c NCHAR(48)  
  WITH NATIVE_COMPILATION, SCHEMABINDING, EXECUTE AS OWNER  
  AS   
  BEGIN ATOMIC   
  WITH (TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = N'us_english')  
  DECLARE @i INT = 1;  
  WHILE @i <= @rowcount  
  BEGIN;  
    INSERT INTO [dbo].[hash_c] VALUES (@i, @c);  
    SET @i += 1;  
  END;  
END;  
go  
```  
  
### <a name="step-3-run-the-code"></a>Шаг 3. Запуск кода  
 Затем можно выполнить запросы, которые продемонстрируют производительность оптимизированных для памяти таблиц. Выполните следующие действия.  
  
1.  Запустите приведенный ниже код T-SQL в базе данных с помощью SSMS.exe.  
  
     Игнорируйте данные о скорости или другие данные производительности, которые формируются при первом запуске. Во время первого запуска выполняется несколько одноразовых операций, например начальное выделение памяти.  
  
2.  Повторно запустите приведенный ниже код T-SQL в базе данных с помощью SSMS.exe.  
  
```sql  
go  
SET STATISTICS TIME OFF;  
SET NOCOUNT ON;  
  
-- Inserts, one at a time.  
  
DECLARE @starttime DATETIME2 = sysdatetime();  
DECLARE @timems INT;  
DECLARE @i INT = 1;  
DECLARE @rowcount INT = 100000;  
DECLARE @c NCHAR(48) = N'12345678901234567890123456789012345678';  
  
-- Harddrive-based table and interpreted Transact-SQL.  
  
BEGIN TRAN;  
  WHILE @i <= @rowcount  
  BEGIN;  
    INSERT INTO [dbo].[sql] VALUES (@i, @c);  
    SET @i += 1;  
  END;  
COMMIT;  
  
SET @timems = datediff(ms, @starttime, sysdatetime());  
SELECT 'A: Disk-based table and interpreted Transact-SQL: '  
    + cast(@timems AS VARCHAR(10)) + ' ms';  
  
-- Interop Hash.  
  
SET @i = 1;  
SET @starttime = sysdatetime();  
  
BEGIN TRAN;  
  WHILE @i <= @rowcount  
    BEGIN;  
      INSERT INTO [dbo].[hash_i] VALUES (@i, @c);  
      SET @i += 1;  
    END;  
COMMIT;  
  
SET @timems = datediff(ms, @starttime, sysdatetime());  
SELECT 'B: memory-optimized table with hash index and interpreted Transact-SQL: '  
    + cast(@timems as VARCHAR(10)) + ' ms';  
  
-- Compiled Hash.  
  
SET @starttime = sysdatetime();  
  
EXECUTE ncsp @rowcount, @c;  
  
SET @timems = datediff(ms, @starttime, sysdatetime());  
SELECT 'C: memory-optimized table with hash index and native SP:'  
    + cast(@timems as varchar(10)) + ' ms';  
go  
  
DELETE sql;  
DELETE hash_i;  
DELETE hash_c;  
go  
```  
  
 Ниже приведены статистические данные о времени вывода, сформированные при выполнении второго тестового запуска.  
  
```sql  
10453 ms , A: Disk-based table and interpreted Transact-SQL.  
5626 ms , B: memory-optimized table with hash index and interpreted Transact-SQL.  
3937 ms , C: memory-optimized table with hash index and native SP.  
```  
  
## <a name="see-also"></a>См. также:  
 [Выполняющаяся в памяти OLTP (оптимизация в памяти)](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
