---
title: "Изменение схемы темпоральной таблицы с системным управлением версиями | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/28/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-tables"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9dbe5a21-9335-4f8b-85fd-9da83df79946
caps.latest.revision: 13
author: "CarlRabeler"
ms.author: "carlrab"
manager: "jhubbard"
caps.handback.revision: 13
---
# Изменение схемы темпоральной таблицы с системным управлением версиями
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  В этом разделе описывается использование инструкции **ALTER TABLE** , чтобы добавить, изменить или удалить столбец.  
  
## Примеры  
 Ниже приведены примеры изменения схемы темпоральной таблицы.  
  
```  
ALTER TABLE dbo.Department   
   ALTER COLUMN  DeptName varchar(100);   
  
ALTER TABLE dbo.Department   
   ADD WebAddress nvarchar(255) NOT NULL    
   CONSTRAINT DF_WebAddress DEFAULT 'www.mycompany.com';   
  
ALTER TABLE dbo.Department   
   ADD TempColumn INT;   
  
GO   
  
ALTER TABLE dbo.Department   
   DROP COLUMN TempColumn;  
  
/* Setting IsHidden property for period columns.   
Use ALTER COLUMN <period_column> DROP HIDDEN to clear IsHidden flag */  
  
ALTER TABLE dbo.Department   
   ALTER COLUMN SysStartTime ADD HIDDEN;   
  
ALTER TABLE dbo.Department   
   ALTER COLUMN SysEndTime ADD HIDDEN;  
  
```  
  
### Важные замечания  
  
-   Чтобы изменить схему темпоральной таблицы, требуется разрешение**CONTROL** на текущую и прежнюю таблицы.  
  
-   Во время выполнения операции **ALTER TABLE** схема обеих таблиц блокируется системой.  
  
-   Указанные изменения схемы распространяются на прежнюю таблицу соответствующим образом (в зависимости от типа изменений).  
  
-   Чтобы добавить столбец, который не допускает значений NULL, или изменить существующий столбец, который допускает значения NULL, необходимо указать значение по умолчанию для существующих строк. Система создаст дополнительное значение по умолчанию с таким же значением и применит его к прежним таблицам. Добавление **DEFAULT** в непустую таблицу — это операция, связанная с размером данных. Она предоставляется во всех выпусках [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], кроме Enterprise Edition (в этом выпуске это операция с метаданными).  
  
-   Добавление столбцов varchar(max), nvarchar(max), varbinary(max) или XML со значениями по умолчанию — это операция обновления данных, которая будет доступна во всех выпусках [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Новый столбец нельзя добавить в сети, если после добавления будет превышено ограничение размера строки.  
  
-   После добавления в таблицу нового столбца, который не допускает значений NULL, следует отключить ограничение по умолчанию в прежней таблице, так как система автоматически заполняет ее новыми столбцами.  
  
-   Параметр ONLINE (**WITH (ONLINE = ON**) не влияет на **ALTER TABLE ALTER COLUMN** при использовании темпоральной таблицы с системным управлением версиями. Столбец ALTER не выполняется в оперативном режиме независимо от того, какое значение указано для параметра ONLINE.  
  
-   Свойство **IsHidden** для столбцов периода можно изменить с помощью инструкции **ALTER COLUMN** .  
  
-   Прямую инструкцию **ALTER** нельзя использовать для следующих изменений схемы Для таких типов изменений установите **SYSTEM_VERSIONING = OFF**.  
  
    -   добавление вычисляемого столбца;  
  
    -   добавление столбца **IDENTITY** ;  
  
    -   добавление столбца **SPARSE** или изменение существующего столбца на **SPARSE**, если для прежней таблицы заданы значения по умолчанию **DATA_COMPRESSION = PAGE** или **DATA_COMPRESSION = ROW**;  
  
    -   добавление столбца **COLUMN_SET**;  
  
    -   добавление столбца **ROWGUIDCOL** или изменение существующего столбца на **ROWGUIDCOL**.  
  
         В примере ниже показано изменение схемы, для которой требуется параметр **SYSTEM_VERSIONING = OFF** (добавление столбца **IDENTITY**).   
        Обратите внимание, что в этом примере отключена проверка согласованности данных. Эта проверка не требуется, если изменения схемы выполнены в рамках транзакции, так как в течение этого периода не могут произойти другие изменения данных.  
  
        ```  
        BEGIN TRAN   
        ALTER TABLE [dbo].[CompanyLocation] SET (SYSTEM_VERSIONING = OFF);   
        ALTER TABLE [CompanyLocation] ADD Cntr INT IDENTITY (1,1);   
        ALTER TABLE [dbo].[CompanyLocationHistory] ADD Cntr INT NOT NULL DEFAULT 0;   
        ALTER TABLE [dbo].[CompanyLocation]    
        SET    
        (   
        SYSTEM_VERSIONING = ON (HISTORY_TABLE = [dbo].[CompanyLocationHistory])   
        );   
        COMMIT ;  
  
        ```  
  
## Эта статья помогла вам? Мы слушаем  
 Какие сведения вы искали и удалось ли вам их найти? Мы прислушиваемся к вашим отзывам для совершенствования материалов. Отправляйте свои комментарии по адресу [sqlfeedback@microsoft.com](mailto:sqlfeedback@microsoft.com?subject=Your%20feedback%20about%20the%20Changing%20the%20Schema%20of%20a%20System-Versioned%20Temporal%20Table%20page).  
  
## См. также:  
 [Темпоральные таблицы](../../relational-databases/tables/temporal-tables.md)   
 [Приступая к работе c темпоральными таблицами с системным управлением версиями](../../relational-databases/tables/getting-started-with-system-versioned-temporal-tables.md)   
 [Управление хранением данных журнала в темпоральных таблицах с системным управлением версиями](../../relational-databases/tables/manage-retention-of-historical-data-in-system-versioned-temporal-tables.md)   
 [Темпоральные таблицы с системным управлением версиями и таблицы, оптимизированные для памяти](../../relational-databases/tables/system-versioned-temporal-tables-with-memory-optimized-tables.md)   
 [ALTER TABLE (Transact-SQL)](../../t-sql/statements/alter-table-transact-sql.md)   
 [Создание темпоральной таблицы с системным управлением версиями](../../relational-databases/tables/creating-a-system-versioned-temporal-table.md)   
 [Изменение данных в темпоральной таблице с системным управлением версиями](../../relational-databases/tables/modifying-data-in-a-system-versioned-temporal-table.md)   
 [Запрос данных в темпоральной таблице с системным управлением версиями](../../relational-databases/tables/querying-data-in-a-system-versioned-temporal-table.md)   
 [Остановка системного управления версиями в темпоральной таблице с системным управлением версиями](../../relational-databases/tables/stopping-system-versioning-on-a-system-versioned-temporal-table.md)  
  
  