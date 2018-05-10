---
title: Создание темпоральной таблицы с системным управлением версиями | Документация Майкрософт
ms.custom: ''
ms.date: 05/24/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: table-view-index
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 21e6d74f-711f-40e6-a8b7-85f832c5d4b3
caps.latest.revision: 20
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: f7415cfbe4343f9f50de42c26db5444b6582a572
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="creating-a-system-versioned-temporal-table"></a>Создание темпоральной таблицы с системным управлением версиями
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Существует три способа создания темпоральной таблицы с системным управлением версиями в зависимости от того, как указывается таблица журнала:  
  
-   Темпоральная таблица с анонимной таблицей журнала. Укажите схему текущей таблицы, а система сама создаст соответствующую таблицу журнала с автоматически созданным именем.  
  
-   Темпоральная таблица с таблицей журнала по умолчанию. Укажите имя схемы таблицы журнала и имя таблицы, а система создаст таблицу журнала в этой схеме.  
  
-   Темпоральная таблица с пользовательской таблицей журнала, созданной заранее. Создайте таблицу журнала, соответствующую вашим потребностям, а затем укажите эту таблицу во время создания темпоральной таблицы.  
  
## <a name="creating-a-temporal-table-with-an-anonymous-history-table"></a>Создание темпоральной таблицы с анонимной таблицей журнала  
 Темпоральная таблица с "анонимной" таблицей журнала удобна при быстром создании объектов, особенно в прототипах и тестовых средах. Это самый простой способ создания темпоральной таблицы, так как он не требует указания параметров в предложении **SYSTEM_VERSIONING** . В приведенном ниже примере таблица создается с включенным системным управлением версиями без задания имени таблицы журнала.  
  
```  
CREATE TABLE Department   
(    
     DeptID int NOT NULL PRIMARY KEY CLUSTERED  
   , DeptName varchar(50) NOT NULL  
   , ManagerID INT  NULL  
   , ParentDeptID int NULL  
   , SysStartTime datetime2 GENERATED ALWAYS AS ROW START NOT NULL  
   , SysEndTime datetime2 GENERATED ALWAYS AS ROW END NOT NULL  
   , PERIOD FOR SYSTEM_TIME (SysStartTime,SysEndTime)     
)    
WITH (SYSTEM_VERSIONING = ON)   
;  
```  
  
### <a name="important-remarks"></a>Важные замечания  
  
-   Для темпоральной таблицы с системным управлением версиями должен быть определен первичный ключ и ровно один параметр **PERIOD FOR SYSTEM_TIME** с двумя столбцами datetime2, объявленными как **GENERATED ALWAYS AS ROW START / END**  
  
-   Столбцы **PERIOD** всегда считаются не поддерживающими значение NULL, даже если допустимость значения NULL не указана. Если столбцы  **PERIOD** определены явно как допускающие значение NULL, инструкция **CREATE TABLE** завершится с ошибкой.  
  
-   Таблица журнала должна быть всегда согласована по схеме с текущей или темпоральной таблицей. Это касается числа столбцов, имен столбцов, порядка и типов данных.  
  
-   Анонимная таблица журнала автоматически создается в одной схеме с текущей или темпоральной таблицей.  
  
-   Имя анонимной таблицы журнала имеет следующий формат: *MSSQL_TemporalHistoryFor_<ИД_объекта_текущей_темпоральной_таблицы>_[suffix]*. Суффикс является необязательным и добавляется только в том случае, если первая часть имени таблицы не является уникальной.  
  
-   Таблица журнала создается как таблица rowstore. Если возможно, применяется сжатие PAGE. В противном случае таблица журнала остается без сжатия. Некоторые табличные конфигурации, например "Разреженные столбцы", не разрешают сжатие.  
  
-   Для таблицы журнала с автоматически создаваемым именем в формате *IX_<history_table_name>* создается кластеризованный индекс по умолчанию. Кластеризованный индекс содержит столбцы **PERIOD** (конец, начало).  
  
-   Сведения о создании текущей таблицы с оптимизацией для памяти см. в разделе [Темпоральные таблицы с системным управлением версиями и таблицы, оптимизированные для памяти](../../relational-databases/tables/system-versioned-temporal-tables-with-memory-optimized-tables.md).  
  
## <a name="creating-a-temporal-table-with-a-default-history-table"></a>Создание темпоральной таблицы с таблицей журнала по умолчанию  
 Темпоральная таблица с таблицей журнала по умолчанию удобна в тех случаях, когда вы хотите контролировать именование, но при этом автоматически создать таблицу журнала с конфигурацией по умолчанию. В приведенном ниже примере таблица создается с включенным системным управлением версиями и с явно заданным именем таблицы журнала.  
  
```  
CREATE TABLE Department   
(    
     DeptID int NOT NULL PRIMARY KEY CLUSTERED  
   , DeptName varchar(50) NOT NULL  
   , ManagerID INT  NULL  
   , ParentDeptID int NULL  
   , SysStartTime datetime2 GENERATED ALWAYS AS ROW START NOT NULL  
   , SysEndTime datetime2 GENERATED ALWAYS AS ROW END NOT NULL  
   , PERIOD FOR SYSTEM_TIME (SysStartTime, SysEndTime)     
)   
WITH    
   (   
      SYSTEM_VERSIONING = ON (HISTORY_TABLE = dbo.DepartmentHistory)   
   )   
;  
```  
  
### <a name="important-remarks"></a>Важные замечания  
 Таблицы журнала создаются по тем же правилам, которые применяются при создании "анонимной" таблицы журнала, с применением следующих особых правил, касающихся именованных таблиц.  
  
-   Для параметра **HISTORY_TABLE** обязательно использовать имя схемы.  
  
-   Если указанная схема не существует, инструкция **CREATE TABLE** завершится с ошибкой.  
  
-   Если таблица, заданная параметром **HISTORY_TABLE** , уже существует, она будет проверена на соответствие с вновь созданной темпоральной таблицей с точки зрения [согласованности схемы и согласованности темпоральных данных](http://msdn.microsoft.com/library/dn935015.aspx). Если будет указана недопустимая таблица журнала, инструкция **CREATE TABLE** завершится с ошибкой.  
  
## <a name="creating-a-temporal-table-with-a-user-defined-history-table"></a>Создание темпоральной таблицы с пользовательской таблицей журнала  
 Темпоральная таблица с пользовательской таблицей журнала удобна в тех случаях, когда требуется определить таблицу журнала с особыми параметрами хранения и дополнительными индексами. В следующем примере создается пользовательская таблица журнала со схемой, которая согласована с создаваемой темпоральной таблицей. В этой пользовательской таблице журнала создаются кластеризованный индекс columnstore и дополнительный некластеризованный индекс rowstore (сбалансированное дерево) для уточняющих запросов. После создания этой пользовательской таблицы журнала создается темпоральная таблица с системным управлением версиями, для которой пользовательская таблица журнала указана как таблица журнала по умолчанию.  
  
```  
CREATE TABLE DepartmentHistory   
(    
     DeptID int NOT NULL  
   , DeptName varchar(50) NOT NULL  
   , ManagerID INT  NULL  
   , ParentDeptID int NULL  
   , SysStartTime datetime2 NOT NULL  
   , SysEndTime datetime2 NOT NULL   
);   
GO   
CREATE CLUSTERED COLUMNSTORE INDEX IX_DepartmentHistory   
   ON DepartmentHistory;   
CREATE NONCLUSTERED INDEX IX_DepartmentHistory_ID_PERIOD_COLUMNS   
   ON DepartmentHistory (SysEndTime, SysStartTime, DeptID);   
GO   
CREATE TABLE Department   
(    
    DeptID int NOT NULL PRIMARY KEY CLUSTERED  
   , DeptName varchar(50) NOT NULL  
   , ManagerID INT  NULL  
   , ParentDeptID int NULL  
   , SysStartTime datetime2 GENERATED ALWAYS AS ROW START NOT NULL  
   , SysEndTime datetime2 GENERATED ALWAYS AS ROW END NOT NULL     
   , PERIOD FOR SYSTEM_TIME (SysStartTime,SysEndTime)      
)    
WITH (SYSTEM_VERSIONING = ON (HISTORY_TABLE = dbo.DepartmentHistory))   
;  
```  
  
### <a name="important-remarks"></a>Важные замечания  
  
-   Если планируется выполнять аналитические запросы по данным журнала, в которых используются статистические или ранжирующие функции, настоятельно рекомендуется создать кластеризованный индекс columnstore в качестве первичного индекса, так как он позволяет получить очень хорошее сжатие данных и производительность запросов.  
  
-   Если основной задачей является аудит данных (т. е. поиск изменений данных журнала для одной строки текущей таблицы), рекомендуется создать таблицу журнала rowstore с кластеризованным индексом.  
  
-   Таблица журнала не может иметь первичный ключ, внешние ключи, уникальные индексы, ограничения таблицы или триггеры. Она не может быть настроена для отслеживания измененных данных, отслеживания изменений, репликации транзакций и репликации слиянием.  
  
## <a name="alter-non-temporal-table-to-be-system-versioned-temporal-table"></a>Преобразование нетемпоральной таблицы в темпоральную таблицу с системным управлением версиями  
 Такое преобразование может потребоваться при необходимости включить системное управление версиями с использованием существующей таблицы, например, если нужно перенести пользовательское темпоральное решение в решение со встроенной поддержкой.   
Например, имеется набор таблиц, где управление версиями реализуется с помощью триггеров. Использование темпоральной системы управления версиями проще и дает дополнительные преимущества, а именно:  
  
-   неизменяемый журнал;  
  
-   новый синтаксис запросов, перемещающихся во времени;  
  
-   улучшенная производительность DML;  
  
-   минимальные затраты на обслуживание.  
  
 При преобразовании существующей таблицы рекомендуется использовать предложение **HIDDEN** для скрытия новых столбцов **PERIOD** , чтобы избежать влияния на существующие приложения, которые не предназначены для работы с новыми столбцами.  
  
### <a name="adding-versioning-to-non-temporal-tables"></a>Добавление функции управления версиями в нетемпоральные таблицы  
 Если вы хотите начать отслеживать изменения для нетемпоральной таблицы, которая содержит данные, нужно добавить определение **PERIOD** и при необходимости указать имя для пустой таблицы журнала, которая будет создана SQL Server:  
  
```  
CREATE SCHEMA History;   
GO   
ALTER TABLE InsurancePolicy   
   ADD   
      SysStartTime datetime2(0) GENERATED ALWAYS AS ROW START HIDDEN    
           CONSTRAINT DF_SysStart DEFAULT SYSUTCDATETIME()  
      , SysEndTime datetime2(0) GENERATED ALWAYS AS ROW END HIDDEN    
           CONSTRAINT DF_SysEnd DEFAULT CONVERT(datetime2 (0), '9999-12-31 23:59:59'),   
      PERIOD FOR SYSTEM_TIME (SysStartTime, SysEndTime);   
GO   
ALTER TABLE InsurancePolicy   
   SET (SYSTEM_VERSIONING = ON (HISTORY_TABLE = History.InsurancePolicy))   
;  
```  
  
#### <a name="important-remarks"></a>Важные замечания  
  
-   Добавление в существующую таблицу с данными не допускающих значения NULL столбцов со значениями по умолчанию является операцией, связанной с размером данных, во всех выпусках кроме SQL Server Enterprise Edition (в этом выпуске это операция с метаданными). При наличии большой существующей таблицы журнала с данными в SQL Server Standard Edition добавление столбца со значениями, отличными от NULL, может потребовать значительного времени.  
  
-   Необходимо тщательно выбрать ограничения для столбцов начала и окончания периода:  
  
    -   Значение по умолчанию для столбца начала определяет, начиная с какого момента времени существующие строки должны считаться действительными. Это значение не может быть моментом времени в будущем.  
  
    -   Время окончания должно быть указано как максимальное значение для заданной точности datetime2.  
  
-   При добавлении периода будет выполнена проверка согласованности данных в текущей таблице, чтобы убедиться в том, что значения по умолчанию для столбцов периода являются допустимыми.  
  
-   Если при включении **SYSTEM_VERSIONING**будет указана существующая таблица журнала, проверка согласованности данных будет выполнена и в текущей таблице, и в таблице журнала. Этот шаг можно пропустить, если в качестве дополнительного параметра задать **DATA_CONISTENCY_CHECK = OFF** .  
  
### <a name="migrate-existing-tables-to-built-in-support"></a>Перенос существующих таблиц в решение со встроенной поддержкой  
 В этом примере показано, как выполнить перенос существующего решения на основе триггеров в решение со встроенной темпоральной поддержкой. В этом примере предполагается, что в имеющемся пользовательском решении текущие данные и данные журнала разделены на две отдельные пользовательские таблицы (**ProjectTaskCurrent** и **ProjectTaskHistory**). Если в имеющемся решении используется одна таблица для хранения текущих строк и строк журнала, следует разбить данные на две таблицы до переноса, описанного в этом примере:  
  
```  
/*Drop trigger on future temporal table*/   
DROP TRIGGER ProjectCurrent_OnUpdateDelete;   
/*Make sure that future period columns are non-nullable*/   
ALTER TABLE ProjectTaskCurrent ALTER COLUMN [ValidFrom] datetime2 NOT NULL;   
ALTER TABLE ProjectTaskCurrent ALTER COLUMN [ValidTo] datetime2 NOT NULL;   
ALTER TABLE ProjectTaskHistory ALTER COLUMN [ValidFrom] datetime2 NOT NULL;   
ALTER TABLE ProjectTaskHistory ALTER COLUMN [ValidTo] datetime2 NOT NULL;   
ALTER TABLE ProjectTaskCurrent   
   ADD PERIOD FOR SYSTEM_TIME ([ValidFrom], [ValidTo])   
ALTER TABLE ProjectTaskCurrent   
   SET (SYSTEM_VERSIONING = ON (HISTORY_TABLE = dbo.ProjectTaskHistory, DATA_CONSISTENCY_CHECK = ON))   
;  
```  
  
#### <a name="important-remarks"></a>Важные замечания  
  
-   Ссылка на существующие столбцы в определении **PERIOD** неявно заменяет параметр generated_always_type на **AS_ROW_START** и **AS_ROW_END** для этих столбцов.  
  
-   При добавлении **PERIOD** будет выполнена проверка согласованности данных в текущей таблице, чтобы убедиться в том, что существующие значения для столбцов периода являются допустимыми.  
  
-   Настоятельно рекомендуется присвоить параметру **SYSTEM_VERSIONING** значение **DATA_CONSISTENCY_CHECK = ON** , чтобы принудительно выполнять проверки соответствия существующих данных.  
  
 
## <a name="see-also"></a>См. также:  
 [Темпоральные таблицы](../../relational-databases/tables/temporal-tables.md)   
 [Приступая к работе c темпоральными таблицами с системным управлением версиями](../../relational-databases/tables/getting-started-with-system-versioned-temporal-tables.md)   
 [Управление хранением данных журнала в темпоральных таблицах с системным управлением версиями](../../relational-databases/tables/manage-retention-of-historical-data-in-system-versioned-temporal-tables.md)   
 [Темпоральные таблицы с системным управлением версиями и таблицы, оптимизированные для памяти](../../relational-databases/tables/system-versioned-temporal-tables-with-memory-optimized-tables.md)   
 [CREATE TABLE (Transact-SQL)](../../t-sql/statements/create-table-transact-sql.md)   
 [Изменение данных в темпоральной таблице с системным управлением версиями](../../relational-databases/tables/modifying-data-in-a-system-versioned-temporal-table.md)   
 [Запрос данных в темпоральной таблице с системным управлением версиями](../../relational-databases/tables/querying-data-in-a-system-versioned-temporal-table.md)   
 [Изменение схемы темпоральной таблицы с системным управлением версиями](../../relational-databases/tables/changing-the-schema-of-a-system-versioned-temporal-table.md)   
 [Остановка системного управления версиями в темпоральной таблице с системным управлением версиями](../../relational-databases/tables/stopping-system-versioning-on-a-system-versioned-temporal-table.md)  
  
  
