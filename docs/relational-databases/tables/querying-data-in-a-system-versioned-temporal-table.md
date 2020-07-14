---
title: Запрос данных в темпоральной таблице с системным управлением версиями | Документация Майкрософт
ms.custom: ''
ms.date: 03/28/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
ms.assetid: 2d358c2e-ebd8-4eb3-9bff-cfa598a39125
author: CarlRabeler
ms.author: carlrab
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 2ed4bcd1fb72c25520e935879305ff1c7d894707
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/06/2020
ms.locfileid: "86002332"
---
# <a name="querying-data-in-a-system-versioned-temporal-table"></a>Запрос данных в темпоральной таблице с системным управлением версиями

[!INCLUDE [sqlserver2016-asdb-asdbmi-asa](../../includes/applies-to-version/sqlserver2016-asdb-asdbmi-asa.md)]

Если требуется получить новейшее (актуальное) состояние данных в темпоральной таблице, можно отправить запрос точно так же, как и в нетемпоральной таблице. Если столбцы PERIOD не скрыты, их значения отобразятся в запросе SELECT \* . Если столбцы **PERIOD** указаны как скрытые, их значения не отобразятся в запросе SELECT \*. Если столбцы **PERIOD** скрыты, следует специально указать столбцы **PERIOD** в предложении SELECT, чтобы вернуть значения этих столбцов.

Для выполнения всех видов анализа на основе времени следует использовать новое предложение **FOR SYSTEM_TIME** с четырьмя вложенными предложениями для темпоральных таблиц, чтобы запрашивать данные в текущих и прошлых таблицах. Дополнительные сведения об этих предложениях см. в разделах [Темпоральные таблицы](../../relational-databases/tables/temporal-tables.md) и [FROM (Transact-SQL)](../../t-sql/queries/from-transact-sql.md).

- AS OF <date_time>
- FROM <start_date_time> TO <end_date_time>
- BETWEEN <start_date_time> AND <end_date_time>
- CONTAINED IN (<start_date_time>, <end_date_time>)
- ALL

Предложение**FOR SYSTEM_TIME** можно указывать независимо для каждой таблицы в запросе. Его можно использовать в обобщенных табличных выражениях, функциях с табличными значениями и хранимых процедурах. При использовании псевдонима таблицы с темпоральной таблицей предложение **FOR SYSTEM_TIME** должно быть задано между именем темпоральной таблицы и псевдонимом (см. второй пример в разделе "Запрос на определенное время с использованием вложенного предложения AS OF" ниже).

## <a name="query-for-a-specific-time-using-the-as-of-sub-clause"></a>Запрос на определенное время с использованием вложенного предложения AS OF

Используйте вложенное предложение **AS OF**, если необходимо восстановить состояние данных на любой момент времени в прошлом. Данные можно восстановить с точностью типа datetime2, который указан в определениях столбцов **PERIOD** .

Вложенное предложение **AS OF** можно использовать с константными литералами или с переменными, что позволяет динамически указывать условие времени. Указанные значения интерпретируются как время в формате UTC.

В первом примере возвращается состояние таблицы dbo.Department на (AS OF) определенную дату в прошлом.

```sql
/*State of entire table AS OF specific date in the past*/
SELECT [DeptID], [DeptName], [SysStartTime],[SysEndTime]
FROM [dbo].[Department]
FOR SYSTEM_TIME AS OF '2015-09-01 T10:00:00.7230011' ;
```

Во втором примере сравниваются значения в интервале между двумя моментами времени для подмножества строк.

```sql
DECLARE @ADayAgo datetime2
SET @ADayAgo = DATEADD (day, -1, sysutcdatetime())
/*Comparison between two points in time for subset of rows*/
SELECT D_1_Ago.[DeptID], D.[DeptID],
D_1_Ago.[DeptName], D.[DeptName],
D_1_Ago.[SysStartTime], D.[SysStartTime],
D_1_Ago.[SysEndTime], D.[SysEndTime]
FROM [dbo].[Department] FOR SYSTEM_TIME AS OF @ADayAgo AS D_1_Ago
JOIN [Department] AS D ON D_1_Ago.[DeptID] = [D].[DeptID]
AND D_1_Ago.[DeptID] BETWEEN 1 and 5 ;
```

### <a name="using-views-with-as-of-sub-clause-in-temporal-queries"></a>Использование представлений с вложенным предложением AS OF в темпоральных запросах

Использование представлений весьма полезно в сценариях, где требуется сложный анализ на момент времени. Распространенный пример — создание бизнес-отчета сегодня со значениями за предыдущий месяц.

Как правило, у клиентов имеется нормализованная модель базы данных, которая включает в себя множество таблиц со связями по внешнему ключу. Ответить на вопрос, как данные из этой нормализованной модели выглядели в определенный момент в прошлом, весьма непросто, так как все таблицы изменяются независимо друг от друга, каждая в собственном ритме.

В этом случае лучше всего создать представление и применить вложенное предложение **AS OF** ко всему представлению. Такой подход позволяет отделить моделирование уровня доступа к данным от анализа на момент времени, так как SQL Server будет применять предложение **AS OF** прозрачно ко всем темпоральным таблицам, участвующим в определении представления. Кроме того, можно объединить темпоральные и нетемпоральные таблицы в одном представлении, и предложение **AS OF** будет применено только к темпоральным таблицам. Если представление не ссылается хотя бы на одну темпоральную таблицу, применение к нему предложений темпоральных запросов завершится ошибкой.

```sql
/* Create view that joins three temporal tables: Department, CompanyLocation, LocationDepartments */
CREATE VIEW [dbo].[vw_GetOrgChart]
AS
SELECT
    [CompanyLocation].LocID
   , [CompanyLocation].LocName
   , [CompanyLocation].City
   , [Department].DeptID
   , [Department].DeptName
FROM [dbo].[CompanyLocation]
LEFT JOIN [dbo].[LocationDepartments]
   ON [CompanyLocation].LocID = LocationDepartments.LocID
LEFT JOIN [dbo].[Department]
   ON LocationDepartments.DeptID = [Department].DeptID ;
GO
/* Querying view AS OF */
SELECT * FROM [vw_GetOrgChart]
FOR SYSTEM_TIME AS OF '2015-09-01 T10:00:00.7230011' ;
```

## <a name="query-for-changes-to-specific-rows-over-time"></a>Запрос изменений в определенных строках со временем

Темпоральные вложенные предложения **FROM...TO**, **BETWEEN...AND** и **CONTAINED IN** полезны, когда требуется выполнить аудит данных, т. е. получить все прошлые изменения определенной строки в текущей таблице.

Первые два вложенных предложения возвращают версии строки, пересекающиеся с указанным периодом (т. е. те, которые были начаты до этого периода и завершены после него), тогда как CONTAINED IN возвращает только те, которые существовали в пределах указанного периода.

> [!IMPORTANT]
> Если вы ищете только версии строки, не являющиеся текущими, рекомендуется выполнить запрос непосредственно к прежней таблице, так как это обеспечивает оптимальную производительность запросов. Используйте **ALL** , когда необходимо запросить текущие и прошлые данные без каких-либо ограничений.

```sql
/* Query using BETWEEN...AND sub-clause*/
SELECT
     [DeptID]
   , [DeptName]
   , [SysStartTime]
   , [SysEndTime]
   , IIF (YEAR(SysEndTime) = 9999, 1, 0) AS IsActual
FROM [dbo].[Department]
FOR SYSTEM_TIME BETWEEN '2015-01-01' AND '2015-12-31'
WHERE DeptId = 1
ORDER BY SysStartTime DESC;

/* Query using CONTAINED IN sub-clause */
SELECT [DeptID], [DeptName], [SysStartTime],[SysEndTime]
FROM [dbo].[Department]
FOR SYSTEM_TIME CONTAINED IN ('2015-04-01', '2015-09-25')
WHERE DeptId = 1
ORDER BY SysStartTime DESC ;

/* Query using ALL sub-clause */
SELECT
     [DeptID]
   , [DeptName]
   , [SysStartTime]
   , [SysEndTime]
   , IIF (YEAR(SysEndTime) = 9999, 1, 0) AS IsActual
FROM [dbo].[Department] FOR SYSTEM_TIME ALL
ORDER BY [DeptID], [SysStartTime] Desc
```

## <a name="next-steps"></a>Дальнейшие действия

- [Темпоральные таблицы](../../relational-databases/tables/temporal-tables.md)
- [FROM (Transact-SQL)](../../t-sql/queries/from-transact-sql.md)
- [Создание темпоральной таблицы с системным управлением версиями](../../relational-databases/tables/creating-a-system-versioned-temporal-table.md)
- [Изменение данных в темпоральной таблице с системным управлением версиями](../../relational-databases/tables/modifying-data-in-a-system-versioned-temporal-table.md)
- [Изменение схемы темпоральной таблицы с системным управлением версиями](../../relational-databases/tables/changing-the-schema-of-a-system-versioned-temporal-table.md)
- [Остановка системного управления версиями в темпоральной таблице с системным управлением версиями](../../relational-databases/tables/stopping-system-versioning-on-a-system-versioned-temporal-table.md)
