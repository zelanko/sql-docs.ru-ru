---
title: Создание оптимизированной для памяти темпоральной таблицы с системным управлением версиями | Документация Майкрософт
ms.custom: ''
ms.date: 05/05/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
ms.assetid: 1c1fc682-bf5b-4096-a0ff-3235d71c205a
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: cbe9e25c3a931e4c32481ac53d7ba93ac130c299
ms.sourcegitcommit: 0a4879dad09c6c42ad1ff717e4512cfea46820e9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/27/2019
ms.locfileid: "67412866"
---
# <a name="creating-a-memory-optimized-system-versioned-temporal-table"></a>Создание оптимизированной для памяти темпоральной таблицы с системным управлением версиями

[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

Подобно созданию таблицы журнала на диске, можно создать темпоральную таблицу, оптимизированную для памяти, несколькими способами.

> [!NOTE]
> Для создания оптимизированных для памяти таблиц необходимо сначала создать [файловую группу с оптимизированной памятью](../../relational-databases/in-memory-oltp/the-memory-optimized-filegroup.md).

Темпоральная таблица с таблицей журнала по умолчанию удобна в тех случаях, когда вы хотите контролировать именование, но при этом автоматически создать таблицу журнала с конфигурацией по умолчанию. В приведенном ниже примере новая оптимизированная для памяти темпоральная таблица с системным управлением версиями связывается с новой таблицей журнала на диске.

```sql
CREATE SCHEMA History
GO
CREATE TABLE dbo.Department
   (  
      DepartmentNumber char(10) NOT NULL PRIMARY KEY NONCLUSTERED,
      DepartmentName varchar(50) NOT NULL,
      ManagerID int NULL,
      ParentDepartmentNumber char(10) NULL,
      SysStartTime datetime2 GENERATED ALWAYS AS ROW START HIDDEN NOT NULL,
      SysEndTime datetime2 GENERATED ALWAYS AS ROW END HIDDEN NOT NULL,
      PERIOD FOR SYSTEM_TIME (SysStartTime,SysEndTime)
   )
WITH
   (
       MEMORY_OPTIMIZED = ON, DURABILITY = SCHEMA_AND_DATA,
          SYSTEM_VERSIONING = ON ( HISTORY_TABLE = History.DepartmentHistory )
    );
```

Создание темпоральной таблицы, связанной с существующей таблицей журнала, полезно, если вам нужно добавить системное управление версиями с использованием существующей таблицы, например, если требуется перенести пользовательское темпоральное решение в решение со встроенной поддержкой. В приведенном ниже примере создается новая темпоральная таблица, связанная с существующей таблицей журнала.

```sql
--Existing table
CREATE TABLE Department_History
   (
      DepartmentNumber char(10) NOT NULL,
      DepartmentName varchar(50) NOT NULL,
      ManagerID int NULL,
      ParentDepartmentNumber char(10) NULL,
      SysStartTime datetime2 NOT NULL, SysEndTime datetime2 NOT NULL
   )
;
--Temporal table
CREATE TABLE Department
   (
      DepartmentNumber char(10) NOT NULL PRIMARY KEY NONCLUSTERED,
      DepartmentName varchar(50) NOT NULL,
      ManagerID INT NULL,
      ParentDepartmentNumber char(10) NULL,
      SysStartTime datetime2 GENERATED ALWAYS AS ROW START HIDDEN NOT NULL,
      SysEndTime datetime2 GENERATED ALWAYS AS ROW END HIDDEN NOT NULL,
      PERIOD FOR SYSTEM_TIME (SysStartTime,SysEndTime)
   )
WITH
   (
      SYSTEM_VERSIONING = ON
         (  
            HISTORY_TABLE = dbo.Department_History
            , DATA_CONSISTENCY_CHECK = ON
         )  
      , MEMORY_OPTIMIZED = ON
      , DURABILITY = SCHEMA_AND_DATA
   )
;
```

## <a name="see"></a>См.

- [Темпоральные таблицы с системным управлением версиями и таблицы, оптимизированные для памяти](../../relational-databases/tables/system-versioned-temporal-tables-with-memory-optimized-tables.md)
- [Работа с оптимизированными для памяти темпоральными таблицами с системным управлением версиями](../../relational-databases/tables/working-with-memory-optimized-system-versioned-temporal-tables.md)
- [Мониторинг оптимизированных для памяти темпоральных таблиц с системным управлением версиями](../../relational-databases/tables/monitoring-memory-optimized-system-versioned-temporal-tables.md)
- [Вопросы производительности оптимизированных для памяти темпоральных таблиц с системным управлением версиями](../../relational-databases/tables/memory-optimized-system-versioned-temporal-tables-performance.md)
- [Темпоральные таблицы](../../relational-databases/tables/temporal-tables.md)
- [Проверка согласованности системной темпоральной таблицы](../../relational-databases/tables/temporal-table-system-consistency-checks.md)
- [Управление хранением данных журнала в темпоральных таблицах с системным управлением версиями](../../relational-databases/tables/manage-retention-of-historical-data-in-system-versioned-temporal-tables.md)
- [Представления и функции метаданных для временной таблицы](../../relational-databases/tables/temporal-table-metadata-views-and-functions.md)
