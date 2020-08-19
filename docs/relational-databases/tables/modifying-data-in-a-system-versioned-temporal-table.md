---
description: Изменение данных в темпоральной таблице с системным управлением версиями
title: Изменение данных в темпоральной таблице с системным управлением версиями | Документация Майкрософт
ms.custom: ''
ms.date: 03/28/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
ms.assetid: 5f398470-c531-47b5-84d5-7c67c27df6e5
author: CarlRabeler
ms.author: carlrab
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 654648ba7206c3d5ce01a715a0ee24eae2d3212b
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88419008"
---
# <a name="modifying-data-in-a-system-versioned-temporal-table"></a>Изменение данных в темпоральной таблице с системным управлением версиями

[!INCLUDE [sqlserver2016-asdb-asdbmi](../../includes/applies-to-version/sqlserver2016-asdb-asdbmi.md)]

Данные в темпоральной таблице с системным управлением версиями изменяются с помощью инструкций DML. Но нужно помнить об одном важном отличии: данные в столбце периода нельзя изменять напрямую. Когда данные изменяются, они версионируются (предыдущая версия каждой измененной строки добавляется в таблицу журнала). При удалении данных используется логическое удаление — из текущей таблицы строка перемещается в таблицу журнала (строка не удаляется безвозвратно).

## <a name="inserting-data"></a>Добавление данных

При добавлении новых данных необходимо учитывать столбцы периодов ( **PERIOD** ), если они не скрыты ( **HIDDEN**). С темпоральными таблицами с системным управлением версиями также можно использовать переключение секций.

### <a name="insert-new-data-with-visible-period-columns"></a>Добавление новых данных с видимыми столбцами периодов

Чтобы принять в расчет новые столбцы **PERIOD** , создать инструкцию **INSERT** при наличии видимых столбцов **PERIOD** можно так:

- При указании списка столбцов в инструкции **INSERT** столбцы **PERIOD** можно опустить, так как система создает для них значения автоматически.

  ```sql
  -- Insert with column list and without period columns
  INSERT INTO [dbo].[Department]
    (  [DeptID]
          , [DeptName]
          , [ManagerID]
          ,[ParentDeptID]
    )
       VALUES
         (  10
         , 'Marketing'
         , 101
         , 1
         ) ;
   ```

- Если в инструкции**INSERT** вы все же указываете столбцы **PERIOD** в списке столбцов, в качестве их значения необходимо указать **DEFAULT**.

  ```sql
  INSERT INTO [dbo].[Department]
    (  [DeptID]
          , [DeptName]
          , [ManagerID]
          , [ParentDeptID]
          , SysStartTime
          , SysEndTime
    )
       VALUES
         (  11
          , 'Sales'
          , 101
          , 1
          , default
          , default) ;
   ```

- Если вы не указываете в инструкции **INSERT** список столбцов, укажите для столбцов **PERIOD** значение **DEFAULT** .

  ```sql
    -- Insert without column list and DEFAULT values for period columns
    INSERT INTO [dbo].[Department]
    VALUES(12, 'Production', 101, 1, default, default);

  ```

### <a name="insert-data-into-a-table-with-hidden-period-columns"></a>Добавление данных в таблицу со скрытыми столбцами периодов

Если столбцы **PERIOD** скрыты, вам нужно указать значения только для видимых столбцов (при условии, что вы добавляете данные, не указывая список столбцов). В инструкции **INSERT** не нужно учитывать новые столбцы **PERIOD** . Это гарантирует, что устаревшие приложения будут и дальше работать после включения системного управления версиями в таблицах, для которых версионирование может пойти на пользу.

```sql
CREATE TABLE [dbo].[CompanyLocation]
(
     [LocID] [int] IDENTITY(1,1) NOT NULL PRIMARY KEY
   , [LocName] [varchar](50) NOT NULL
   , [City] [varchar](50) NOT NULL
   , [SysStartTime] [datetime2] GENERATED ALWAYS AS ROW START HIDDEN NOT NULL
   , [SysEndTime] [datetime2] GENERATED ALWAYS AS ROW END HIDDEN NOT NULL
   , PERIOD FOR SYSTEM_TIME ([SysStartTime], [SysEndTime])
)
WITH ( SYSTEM_VERSIONING = ON );
GO
INSERT INTO [dbo].[CompanyLocation]
VALUES ('Headquarters', 'New York');

```

### <a name="inserting-data-using-partition-switch"></a>Добавление данных с использованием переключения секций

Если текущая таблица секционирована, переключение секций можно использовать как эффективный механизм загрузки данных в одну или несколько секций одновременно.

Для промежуточной таблицы, которая указана в инструкции **PARTITION SWITCH IN** с темпоральной таблицей с системным управлением версиями, необходимо определить период **SYSTEM_TIME PERIOD** , но промежуточная таблица не обязательно должна быть темпоральной с системным управлением версиями.
Это гарантирует выполнение проверок темпоральной согласованности: 1) во время добавления данных в промежуточную таблицу; 2) во время добавления периода SYSTEM_TIME в предварительно заполненную промежуточную таблицу.

```sql
/*Create staging table with period definition for SWITCH IN temporal table*/
CREATE TABLE [dbo].[Staging_Department_Partition2]
(
     [DeptID] [int] NOT NULL
   , [DeptName] [varchar](50) NOT NULL
   , [ManagerID] [int] NULL
   , [ParentDeptID] [int] NULL
   , [SysStartTime] [datetime2] GENERATED ALWAYS AS ROW START NOT NULL
   , [SysEndTime] [datetime2] GENERATED ALWAYS AS ROW END NOT NULL
   , PERIOD FOR SYSTEM_TIME ( [SysStartTime], [SysEndTime] )
) ON [PRIMARY]

/*Create aligned primary key*/
ALTER TABLE [dbo].[Staging_Department_Partition2]
ADD CONSTRAINT [Staging_Department_Partition2_PK]
   PRIMARY KEY CLUSTERED
   ( [DeptID] ASC )
   ON [PRIMARY]
  
/*
Create and enforce constraints for partition boundaries.
Partition 2 contains rows with DeptID > 100 and DeptID <=200
*/
ALTER TABLE [dbo].[Staging_Department_Partition2]
   WITH CHECK ADD  CONSTRAINT [chk_staging_Department_partition_2]
   CHECK  ([DeptID]>N'100' AND [DeptID]<=N'200')
ALTER TABLE [dbo].[Staging_Department_Partition2]
   CHECK CONSTRAINT [chk_staging_Department_partition_2]

/*Load data into staging table*/
INSERT INTO [dbo].[staging_Department] ([DeptID],[DeptName],[ManagerID],[ParentDeptID])
VALUES (101,'D101',1,NULL)

/*Use PARTITION SWITCH IN to efficiently add data to current table */
ALTER TABLE [Staging_Department]
SWITCH TO [dbo].[Department] PARTITION 2;
```

Если вы попытаетесь переключить секции из таблицы, в которой период не определен, появится сообщение об ошибке: `Msg 13577, Level 16, State 1, Line 25 ALTER TABLE SWITCH statement failed on table 'MyDB.dbo.Staging_Department_2015_09_26' because target table has SYSTEM_TIME PERIOD while source table does not have it.`

## <a name="updating-data"></a>Обновление данных

Данные в текущей таблице изменяются с помощью регулярной инструкции **UPDATE** . Обновлять данные в текущей таблице, используя данные из таблицы журнала, можно в случаях ошибок или сбоев. Однако обновлять столбцы **PERIOD** нельзя. Также нельзя напрямую обновлять данные в таблице журнала, когда **SYSTEM_VERSIONING = ON**.

Чтобы обновить строки из текущей таблицы и таблицы журнала, задайте **SYSTEM_VERSIONING = OFF** . Но в этом случае система не будет вести журнал изменений.

### <a name="updating-the-current-table"></a>Обновление текущей таблицы

В этом примере столбец ManagerID обновляется в каждой строке, где DeptID = 10. Столбцы **PERIOD** здесь не указываются.

```sql
UPDATE [dbo].[Department] SET [ManagerID] = 501 WHERE [DeptID] = 10
```

Тем не менее обновить столбец **PERIOD** и таблицу журнала нельзя. В этом примере попытка обновить столбец **PERIOD** приведет к ошибке.

```sql
UPDATE [dbo].[Department]
SET SysStartTime = '2015-09-23 23:48:31.2990175'
WHERE DeptID = 10 ;

Msg 13537, Level 16, State 1, Line 3
Cannot update GENERATED ALWAYS columns in table 'TmpDev.dbo.Department'.
```

### <a name="updating-the-current-table-from-the-history-table"></a>Обновление текущей таблицы из таблицы журнала

С помощью инструкции **UPDATE** строку из текущей таблицы можно обновить до состояния, которое было на определенный момент времени в прошлом (восстановление "последней хорошей версии строки"). В следующем примере показано восстановление значений строк, в которых DeptID = 10. Данные восстанавливаются из таблицы журнала по состоянию на 25.04.2015.

```sql
UPDATE Department
SET DeptName = History.DeptName
FROM Department
FOR SYSTEM_TIME AS OF '2015-04-25' AS History
WHERE History.DeptID = 10
AND Department.DeptID = 10 ;
```

## <a name="deleting-data"></a>Удаление данных

Данные в текущей таблице удаляются с помощью регулярной инструкции **DELETE** . В удаленных строках в столбец периода окончания будет подставлено время начала базовой транзакции. Когда **SYSTEM_VERSIONING = ON**, удалять строки напрямую из таблицы журнала нельзя. Чтобы удалить строки из текущей таблицы и таблицы журнала, задайте **SYSTEM_VERSIONING = OFF** . Но в этом случае система не будет вести журнал изменений. Когда**SWITCH PARTITION IN**, **TRUNCATE** , **SWITCH PARTITION OUT** (для текущей таблицы) и **SWITCH PARTITION IN**(для таблицы журнала) не работают.

## <a name="using-merge-to-modify-data-in-temporal-table"></a>Изменение данных в темпоральной таблице с помощью слияния

Операция**MERGE** имеет такие же ограничения, что и инструкции **INSERT** и **UPDATE** относительно столбцов **PERIOD** .

```sql
CREATE TABLE DepartmentStaging (DeptId INT, DeptName varchar(50));
GO
INSERT INTO DepartmentStaging VALUES (1, 'Company Management');
INSERT INTO DepartmentStaging VALUES (10, 'Science & Research');
INSERT INTO DepartmentStaging VALUES (15, 'Process Management');

MERGE dbo.Department AS target
USING (SELECT DeptId, DeptName FROM DepartmentStaging) AS source (DeptId, DeptName)
ON (target.DeptId = source.DeptId)
WHEN MATCHED THEN
    UPDATE
   SET DeptName = source.DeptName
WHEN NOT MATCHED THEN
   INSERT (DeptName)
   VALUES (source.DeptName);
```

## <a name="next-steps"></a>Дальнейшие действия

- [Темпоральные таблицы](../../relational-databases/tables/temporal-tables.md)
- [Создание темпоральной таблицы с системным управлением версиями](../../relational-databases/tables/creating-a-system-versioned-temporal-table.md)
- [Запрос данных в темпоральной таблице с системным управлением версиями](../../relational-databases/tables/querying-data-in-a-system-versioned-temporal-table.md)
- [Изменение схемы темпоральной таблицы с системным управлением версиями](../../relational-databases/tables/changing-the-schema-of-a-system-versioned-temporal-table.md)
- [Остановка системного управления версиями в темпоральной таблице с системным управлением версиями](../../relational-databases/tables/stopping-system-versioning-on-a-system-versioned-temporal-table.md)
