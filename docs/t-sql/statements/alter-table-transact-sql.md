---
title: "Инструкция ALTER TABLE (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 08/07/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- WAIT_AT_LOW_PRIORITY
- ABORT_AFTER_WAIT
- ABORT_AFTER_WAIT_TSQL
- ALTER_TABLE_TSQL
- ALTER TABLE
- WAIT_AT_LOW_PRIORITY_TSQL
- ALTER_COLUMN_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- columns [SQL Server], resizing
- changing column size
- MAXDOP index option, ALTER TABLE statement
- table modifications [SQL Server], ALTER TABLE
- ALTER TABLE statement
- modifying tables
- partitioned tables [SQL Server], lock escalation
- resizing columns
- removing columns
- switching partitions
- reassigning partitions
- removing constraints
- triggers [SQL Server], disabling
- columns [SQL Server], adding
- LOCK_ESCALATION option of ALTER TABLE
- constraints [SQL Server], deleting
- constraints [SQL Server], disabling
- triggers [SQL Server], enabling
- re-enabling constraints
- index modifications [SQL Server]
- disabling constraints
- columns [SQL Server], removing
- max degree of parallelism option
- locking [SQL Server], tables
- ONLINE option
- disabling triggers
- constraints [SQL Server], adding
- deleting constraints
- adding constraints
- adding columns
- SWITCH partitions
- partitioned tables [SQL Server], switching
- lock escalation [SQL Server], option of ALTER TABLE
- constraints [SQL Server], enabling
- dropping constraints
- dropping columns
- table changes [SQL Server]
ms.assetid: f1745145-182d-4301-a334-18f799d361d1
caps.latest.revision: 281
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 7cee79406283aa3b75d41b968370f490cb454ea5
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="alter-table-transact-sql"></a>ALTER TABLE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Изменяет определение таблицы путем изменения, добавления или удаления столбцов и ограничений, переназначения и перестраивания секций, а также отключения или включения ограничений и триггеров.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
-- Syntax for SQL Server and Azure SQL Database  
  
ALTER TABLE [ database_name . [ schema_name ] . | schema_name . ] table_name   
{   
    ALTER COLUMN column_name   
    {   
        [ type_schema_name. ] type_name   
            [ (   
                {   
                   precision [ , scale ]   
                 | max   
                 | xml_schema_collection   
                }   
            ) ]   
        [ COLLATE collation_name ]   
        [ NULL | NOT NULL ] [ SPARSE ]  
      | { ADD | DROP }   
          { ROWGUIDCOL | PERSISTED | NOT FOR REPLICATION | SPARSE | HIDDEN }  
      | { ADD | DROP } MASKED [ WITH ( FUNCTION = ' mask_function ') ]  
    }   
    [ WITH ( ONLINE = ON | OFF ) ]  
    | [ WITH { CHECK | NOCHECK } ]  
  
    | ADD   
    {   
        <column_definition>  
      | <computed_column_definition>  
      | <table_constraint>   
      | <column_set_definition>   
    } [ ,...n ]  
      | [ system_start_time_column_name datetime2 GENERATED ALWAYS AS ROW START   
                   [ HIDDEN ] [ NOT NULL ] [ CONSTRAINT constraint_name ] 
           DEFAULT constant_expression [WITH VALUES] ,  
            system_end_time_column_name datetime2 GENERATED ALWAYS AS ROW END   
                   [ HIDDEN ] [ NOT NULL ]  [ CONSTRAINT constraint_name ] 
           DEFAULT constant_expression [WITH VALUES] ,  
         ]  
       PERIOD FOR SYSTEM_TIME ( system_start_time_column_name, system_end_time_column_name )  
    | DROP   
     [ {  
         [ CONSTRAINT ]  [ IF EXISTS ]  
         {   
              constraint_name   
              [ WITH   
               ( <drop_clustered_constraint_option> [ ,...n ] )   
              ]   
          } [ ,...n ]  
          | COLUMN  [ IF EXISTS ]  
          {  
              column_name   
          } [ ,...n ]  
          | PERIOD FOR SYSTEM_TIME  
     } [ ,...n ]  
    | [ WITH { CHECK | NOCHECK } ] { CHECK | NOCHECK } CONSTRAINT   
        { ALL | constraint_name [ ,...n ] }   
  
    | { ENABLE | DISABLE } TRIGGER   
        { ALL | trigger_name [ ,...n ] }  
  
    | { ENABLE | DISABLE } CHANGE_TRACKING   
        [ WITH ( TRACK_COLUMNS_UPDATED = { ON | OFF } ) ]  
  
    | SWITCH [ PARTITION source_partition_number_expression ]  
        TO target_table   
        [ PARTITION target_partition_number_expression ]  
        [ WITH ( <low_lock_priority_wait> ) ]  
    | SET   
        (  
            [ FILESTREAM_ON =   
                { partition_scheme_name | filegroup | "default" | "NULL" } ]  
            | SYSTEM_VERSIONING =   
                  {   
                      OFF   
                  | ON   
                      [ ( HISTORY_TABLE = schema_name . history_table_name   
                          [, DATA_CONSISTENCY_CHECK = { ON | OFF } ] 
                          [, HISTORY_RETENTION_PERIOD = 
                          { 
                               INFINITE | number {DAY | DAYS | WEEK | WEEKS 
                 | MONTH | MONTHS | YEAR | YEARS } 
                          } 
                          ]  
                        )  
                      ]  
                  }  
          )  
    | REBUILD   
      [ [PARTITION = ALL]  
        [ WITH ( <rebuild_option> [ ,...n ] ) ]   
      | [ PARTITION = partition_number   
           [ WITH ( <single_partition_rebuild_option> [ ,...n ] ) ]  
        ]  
      ]  
  
    | <table_option>  
  
    | <filetable_option>  
  
    | <stretch_configuration>  
  
}  
[ ; ]  
  
-- ALTER TABLE options  
  
<column_set_definition> ::=   
    column_set_name XML COLUMN_SET FOR ALL_SPARSE_COLUMNS  
  
<drop_clustered_constraint_option> ::=    
    {   
        MAXDOP = max_degree_of_parallelism  
      | ONLINE = { ON | OFF }  
      | MOVE TO   
         { partition_scheme_name ( column_name ) | filegroup | "default" }  
    }  
<table_option> ::=  
    {  
        SET ( LOCK_ESCALATION = { AUTO | TABLE | DISABLE } )  
    }  
  
<filetable_option> ::=  
    {  
       [ { ENABLE | DISABLE } FILETABLE_NAMESPACE ]  
       [ SET ( FILETABLE_DIRECTORY = directory_name ) ]  
    }  
  
<stretch_configuration> ::=  
    {  
      SET (  
        REMOTE_DATA_ARCHIVE   
        {  
            = ON (  <table_stretch_options>  )  
          | = OFF_WITHOUT_DATA_RECOVERY ( MIGRATION_STATE = PAUSED )  
          | ( <table_stretch_options> [, ...n] )  
        }  
            )  
    }  
  
<table_stretch_options> ::=  
    {  
     [ FILTER_PREDICATE = { null | table_predicate_function } , ]  
       MIGRATION_STATE = { OUTBOUND | INBOUND | PAUSED }  
    }  
  
<single_partition_rebuild__option> ::=  
{  
      SORT_IN_TEMPDB = { ON | OFF }  
    | MAXDOP = max_degree_of_parallelism  
    | DATA_COMPRESSION = { NONE | ROW | PAGE | COLUMNSTORE | COLUMNSTORE_ARCHIVE} }  
    | ONLINE = { ON [( <low_priority_lock_wait> ) ] | OFF }  
}  
  
<low_priority_lock_wait>::=  
{  
    WAIT_AT_LOW_PRIORITY ( MAX_DURATION = <time> [ MINUTES ], 
        ABORT_AFTER_WAIT = { NONE | SELF | BLOCKERS } )   
}  
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
ALTER TABLE [ database_name . [schema_name ] . | schema_name. ] source_table_name   
{  
    ALTER COLUMN column_name  
        {   
            type_name [ ( precision [ , scale ] ) ]   
            [ COLLATE Windows_collation_name ]   
            [ NULL | NOT NULL ]   
        }  
    | ADD { <column_definition> | <column_constraint> FOR column_name} [ ,...n ]  
    | DROP { COLUMN column_name | [CONSTRAINT] constraint_name } [ ,...n ]  
    | REBUILD {  
            [ PARTITION = ALL [ WITH ( <rebuild_option> ) ] ] 
          | [ PARTITION = partition_number [ WITH ( <single_partition_rebuild_option> ] ]
      } 
    | { SPLIT | MERGE } RANGE (boundary_value)  
    | SWITCH [ PARTITION source_partition_number  
        TO target_table_name [ PARTITION target_partition_number ]  
}  
[;]  
  
<column_definition>::=  
{  
    column_name  
    type_name [ ( precision [ , scale ] ) ]   
    [ <column_constraint> ]  
    [ COLLATE Windows_collation_name ]  
    [ NULL | NOT NULL ]  
}  
  
<column_constraint>::=  
    [ CONSTRAINT constraint_name ] DEFAULT constant_expression  

<rebuild_option > ::=   
{  
    DATA_COMPRESSION = { COLUMNSTORE | COLUMNSTORE_ARCHIVE }
        [ ON PARTITIONS ( {<partition_number> [ TO <partition_number>] } [ , ...n ] ) ]   
}

<single_partition_rebuild_option > ::=   
{  
    DATA_COMPRESSION = { COLUMNSTORE | COLUMNSTORE_ARCHIVE }  
}  
```    

   
## <a name="arguments"></a>Аргументы  
 *database_name*  
 Имя базы данных, в которой создана таблица.  
  
 *schema_name*  
 Имя схемы, которой принадлежит таблица.  
  
 *имя_таблицы*  
 Имя таблицы, подлежащей изменению. Если таблицы нет в текущей базе данных или она не содержится в схеме, которой владеет текущий пользователь, то и база данных, и схема должны быть явно указаны.  
  
 ALTER COLUMN  
 Указывает, что именованный столбец подлежит изменению.  
  
 Нельзя изменять следующие столбцы.  
  
-   Столбец с **timestamp** тип данных.  
  
-   Свойство ROWGUIDCOL для таблицы.  
  
-   Вычисляемый столбец или используемый в вычисляемом столбце.  
  
-   Используется в статистике, сформированной инструкцией CREATE STATISTICS, если столбец не принадлежит **varchar**, **nvarchar**, или **varbinary** тип данных, тип данных не изменяется, и новый размер больше старого или равно или при изменении столбца из не null на null. Во-первых, удалите статистику, используя инструкцию DROP STATISTICS. Статистика, автоматически сформированная оптимизатором запросов, автоматически удаляется инструкцией ALTER COLUMN.  
  
-   Используется в ограничении PRIMARY KEY или [FOREIGN KEY] REFERENCES.  
  
-   Используется в ограничениях CHECK или UNIQUE. Однако допустимо изменение длины столбца изменяемой длины, используемого в ограничении CHECK или UNIQUE.  
  
-   Связано с определением по умолчанию. Однако если тип данных не изменен, то длина, точность или масштаб столбца могут быть изменены.  
  
Тип данных **текст**, **ntext** и **изображения** столбцов можно изменить следующими способами:  
  
    -   **текст** для **varchar(max)**, **nvarchar(max)**, или **xml**  
  
    -   **ntext** для **varchar(max)**, **nvarchar(max)**, или **xml**  
  
    -   **изображение** для **varbinary(max)**  
  
Некоторые изменения типов данных могут повлечь за собой изменения в данных. Например, изменение **nchar** или **nvarchar** столбец **char** или **varchar** может вызвать преобразование символов национальных алфавитов. Дополнительные сведения см. в разделе [Функции CAST и CONVERT (Transact-SQL)](../../t-sql/functions/cast-and-convert-transact-sql.md). Снижение точности или масштаба столбца может привести к усечению данных.  
  
     The data type of a column of a partitioned table cannot be changed.  
  
 Тип данных столбцов, включенных в индекс не может изменяться, если столбец не принадлежит **varchar**, **nvarchar**, или **varbinary** тип данных, и новый размер больше или равно более старый размер.  
  
 Столбцы, включенные в ограничение первичного ключа нельзя изменить с помощью **NOT NULL** для **NULL**.  
  
 Если изменяется столбец зашифрован с помощью ШИФРОВАНИЯ с, можно изменить тип данных в совместимый тип данных (такие как INT в BIGINT), но не может изменить любые параметры шифрования.  
  
 *column_name*  
 Имя столбца, который требуется изменить, добавить или удалить. *column_name* не может превышать 128 символов. Для новых столбцов *column_name* может быть опущен для столбцов, созданных с помощью **timestamp** тип данных. Имя **timestamp** используется, если *column_name* указан для **timestamp** столбец типа данных.  
  
 [ *type_schema_name***.** ] *type_name*  
 Новый тип данных для изменяемого столбца либо тип данных для добавляемого столбца. *Функция TYPE_NAME* нельзя указывать для существующих столбцов секционированных таблиц. *Функция TYPE_NAME* может принимать любое из следующих действий:  
  
-   Системным типом данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Псевдонимом типа данных, основанным на системном типе данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Прежде чем псевдонимы типов данных можно будет использовать в определении таблицы, их нужно создать с помощью инструкции CREATE TYPE.  
  
-   Определяемый пользователем тип [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] и схема, к которой он принадлежит. Чтобы определяемые пользователем типы [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] можно было использовать в определении столбца, их сначала нужно создать с помощью инструкции CREATE TYPE.  
  
Ниже приведены критерии для *type_name* изменяемого столбца:  
  
-   Предыдущие типы данных должны быть неявно преобразуемыми в новый тип данных.  
  
-   *Функция TYPE_NAME* не может быть **timestamp**.  
  
-   По умолчанию для аргумента ANSI_NULL инструкции ALTER COLUMN всегда установлено значение ON; если не указано иное, столбец может содержать значения NULL.  
  
-   Аргумент заполнения ANSI_PADDING для инструкции ALTER COLUMN всегда принимает значение ON.  
  
-   Если изменяемый столбец является столбцом идентификаторов *new_data_type* должен быть типом данных, которая поддерживает свойство identity.  
  
-   Текущая установка для аргумента SET ARITHABORT пропускается. Инструкция ALTER TABLE функционирует аналогично случаю, когда для аргумента ARITHABORT установлено значение ON.  
  
> [!NOTE]  
>  Если предложение COLLATE не указывается, то изменение типа данных столбца вызовет изменение параметров сортировки на параметры сортировки базы данных по умолчанию.  
  
 *precision*  
 Точность указанного типа данных. Дополнительные сведения о допустимых значениях точности см. в разделе [точность, масштаб и длина &#40; Transact-SQL &#41; ](../../t-sql/data-types/precision-scale-and-length-transact-sql.md).  
  
 *масштаб*  
 Масштаб указанного типа данных. Дополнительные сведения о допустимых значениях масштаба см. в разделе [точность, масштаб и длина &#40; Transact-SQL &#41; ](../../t-sql/data-types/precision-scale-and-length-transact-sql.md).  
  
 **max**  
 Применяется только к **varchar**, **nvarchar**, и **varbinary** типы данных для хранения 2 ^ 31-1 байт символов, двоичных данных и данных Юникода.  
  
 *xml_schema_collection*  
 **Применяется к**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] и [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].  
  
 Применяется только к **xml** тип данных для связывания схемы XML с типом. Перед вводом **xml** столбца к коллекции схемы коллекции схем сначала должна быть создана в базе данных с помощью [CREATE XML SCHEMA COLLECTION](../../t-sql/statements/create-xml-schema-collection-transact-sql.md).  
  
COLLATE \< *имя_параметров_сортировки* > указывает новые параметры сортировки для изменяемого столбца. Если не указано, столбцу назначаются параметры сортировки, принятые в базе данных по умолчанию. Именем параметров сортировки может быть либо имя параметров сортировки Windows, либо имя параметров сортировки SQL. Список и Дополнительные сведения см. в разделе [имя параметров сортировки Windows &#40; Transact-SQL &#41; ](../../t-sql/statements/windows-collation-name-transact-sql.md) и [SQL Server Collation Name &#40; Transact-SQL &#41; ](../../t-sql/statements/sql-server-collation-name-transact-sql.md).  
  
 Предложение COLLATE можно использовать для изменения параметров сортировки только для столбцов **char**, **varchar**, **nchar**, и **nvarchar** типов данных. Чтобы изменить параметры сортировки столбца пользовательского псевдонима типа данных, необходимо выполнить отдельные инструкции ALTER TABLE, чтобы изменить столбец на системный тип данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], изменить параметры сортировки, а затем снова перевести столбец в псевдоним типа данных.  
  
 Инструкция ALTER COLUMN не может изменить параметры сортировки, если выполняется одно или несколько из следующих условий:  
  
-   Если на изменяемый столбец ссылается ограничение CHECK, ограничение FOREIGN KEY или вычисляемые столбцы.  
  
-   Если на базе столбца создан какой-нибудь индекс, статистика или полнотекстовый индекс. Статистика, автоматически созданная на базе изменяемого столбца, удаляется, если изменяются параметры сортировки столбца.  
  
-   Если связанное со схемой представление или функция ссылаются на столбец.  
  
 Дополнительные сведения см. в разделе [COLLATE (Transact-SQL)](~/t-sql/statements/collations.md).  
  
NULL | NOT NULL  
 Указывает, может ли столбец принимать значения NULL. Столбцы, не допускающие значения NULL, могут быть добавлены инструкцией ALTER TABLE только в том случае, если для них указаны значения по умолчанию или если таблица пуста. Ограничение NOT NULL может быть указано для вычисляемых столбцов только в случае, если одновременно указан параметр PERSISTED. Если новый столбец допускает значения NULL, а значение по умолчанию не задано, то новый столбец содержит значение NULL для каждой строки в таблице. Если новый столбец допускает значение NULL, а определение по умолчанию добавляется с новым столбцом, то инструкция WITH VALUES может использоваться для хранения значений по умолчанию в новом столбце для каждой существующей строки в таблице.  
  
 Если новый столбец не допускает значение NULL и таблица не пуста, то определение DEFAULT должно быть добавлено с новым столбцом. Новый столбец автоматически загружается со значениями по умолчанию в каждой существующей строке нового столбца.  
  
 Значение NULL может указываться в инструкции ALTER COLUMN, чтобы принудить столбец NOT NULL допускать значения NULL, за исключением столбцов в ограничениях PRIMARY KEY. Значение NOT NULL может быть указано в инструкции ALTER COLUMN, только если столбец не содержит значения NULL. Значения NULL следует обновить, присвоив некоторые значения, прежде чем разрешить инструкцию ALTER COLUMN NOT NULL, например:  
  
```  
UPDATE MyTable SET NullCol = N'some_value' WHERE NullCol IS NULL;  
ALTER TABLE MyTable ALTER COLUMN NullCOl NVARCHAR(20) NOT NULL;  
```  
  
 При создании или изменении таблицы инструкцией CREATE TABLE или ALTER TABLE установки базы данных и сеанса изменяются и, возможно, переопределяют разрешение содержать значение NULL для типа данных, используемого в определении столбца. Рекомендуется всегда явно определять невычисляемые столбцы как NULL или NOT NULL.  
  
 Если добавляется столбец определяемого пользователем типа данных, то рекомендуется определить для этого столбца то же состояние допустимости значений NULL, что и в определяемом пользователем типе данных и задать для него значение по умолчанию. Дополнительные сведения см. в разделе [CREATE TABLE (Transact-SQL)](../../t-sql/statements/create-table-transact-sql.md).  
  
> [!NOTE]  
>  Если значение NULL или не указано значение NULL в инструкции ALTER COLUMN *new_data_type* [(*точности* [, *шкалы* ])] также должен быть указан. Если тип данных, точность или масштаб не изменялись, укажите текущие значения столбца.  
  
 [ {ADD | DROP} ROWGUIDCOL ]  
 **Применяется к**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] и [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].  
  
 Указывает свойство ROWGUIDCOL, добавленное к указанному столбцу или удаленное из него. Свойство ROWGUIDCOL указывает, что данный столбец является столбцом идентификатора GUID строки. Только один **uniqueidentifier** столбца в каждой таблице можно определить как столбец ROWGUIDCOL, и свойство ROWGUIDCOL может присваиваться только **uniqueidentifier** столбца. Нельзя присваивать свойство ROWGUIDCOL столбцу определяемого пользователем типа данных.  
  
 Свойство ROWGUIDCOL не обеспечивает уникальности значений, хранимых в столбце, и не формирует автоматически значения для новых строк, вставляемых в таблицу. Для формирования уникальных значений для каждого столбца можно использовать функцию NEWID в инструкциях INSERT или определить функцию NEWID как значение по умолчанию для столбца.  
  
 [ {ADD | DROP} PERSISTED ]  
 Указывает, что свойство PERSISTED добавлено к указанному столбцу или удалено из него. Столбец должен быть вычисляемым столбцом, который задается при помощи детерминированных выражений. Для столбцов, указанных как PERSISTED, компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] физически хранит вычисляемые значения в таблице и обновляет значения при обновлении любого столбца, от которого зависит вычисляемый столбец. Если пометить вычисляемый столбец как PERSISTED, можно создавать индексы по вычисляемым столбцам, которые заданы, являются детерминированными, но не точными выражениями. Дополнительные сведения см. в разделе [Indexes on Computed Columns](../../relational-databases/indexes/indexes-on-computed-columns.md).  
  
 Любой вычисляемый столбец, используемый как столбец секционирования секционированной таблицы, должен быть явно помечен PERSISTED.  
  
 DROP NOT FOR REPLICATION  
 **Применяется к**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] и [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].  
  
 Указывает, что значения в столбцах идентификаторов увеличиваются при выполнении агентами репликации операций по вставке строк. Это предложение может быть указан только в том случае, если *column_name* является столбцом идентификаторов.  
  
 SPARSE  
 Указывает, что столбец является разреженным столбцом. Хранилище разреженных столбцов оптимизируется для значений NULL. Для разреженных столбцов нельзя указать параметр NOT NULL. При преобразовании столбцов из разреженных в неразреженные или из неразреженных в разреженные таблица блокируется на протяжении выполнения команды. Возможно, потребуется использование предложения REBUILD для освобождения пространства. Дополнительные ограничения и Дополнительные сведения о разреженных столбцах см. в разделе [Использование разреженных столбцов](../../relational-databases/tables/use-sparse-columns.md).  
  
 Добавить СКРЫТЫЙ с (ФУНКЦИЯ = " *mask_function* ")  
 **Применяется к**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] и [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].  
  
 Задает маску динамических данных. *mask_function* имя функция маскирования с соответствующими параметрами. Доступны три функции:  
  
-   Default()  
-   Email()  
-   partial()  
-   Random()  
  
 Чтобы удалить маску, используйте `DROP MASKED`. Параметры функции. в разделе [динамической маскировки данных](../../relational-databases/security/dynamic-data-masking.md).  
  
С ПОМОЩЬЮ (ONLINE = ON | OFF) \<к изменению столбца >  
 **Применяется к**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] и [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].  
  
 Позволяет выполнять многие действия по изменению столбцов с сохранением доступности таблицы. По умолчанию — OFF. В интерактивном режиме могут выполняться изменения столбца, связанные с типом данных, длиной или точностью столбца, допустимостью значений NULL, разреженностью и параметрами сортировки.  
  
 Изменение столбца в режиме «в сети» позволяет созданной пользователем и автоматической статистике ссылаться на изменяемый столбец во время операции ALTER COLUMN. Таким образом запросы могут выполняться как обычно. В конце операции автоматическая статистика, которая ссылается на столбец, удаляется, а статистика, созданная пользователем, становится недействительной. Пользователь должен вручную обновить созданную пользователем статистику после завершения операции. Если столбец является частью выражения фильтра для статистика или индексы не удается выполнить операцию изменения столбца.  
  
-   Во время выполнения операции изменения столбца в режиме «в сети» все операции, имеющие зависимость от этого столбца (такие как индексирование, представления и т. д.), будут блокироваться или завершаться с соответствующей ошибкой. Это гарантирует, что при изменении столбца в режиме «в сети» не произойдет сбой из-за зависимостей, возникших во время выполнения операции.  
  
-   Изменение столбца с NOT NULL на NULL не поддерживается, поскольку это операция в режиме «в сети», когда к изменяемому столбцу обращаются по некластеризованным индексам.  
  
-   Изменение в режиме «в сети» не поддерживается, когда на столбец ссылается ограничение CHECK, и операция изменения ограничивает точность столбца (числового или содержащего дату и время).  
  
-   **Low_priority_lock_wait** параметр не может использоваться с сети изменить столбец.  
  
-   ALTER COLUMN … При изменении столбца в режиме "в сети" не поддерживается команда ALTER COLUMN … ADD/DROP PERSISTED.  
  
-   ALTER COLUMN … Изменение столбца в режиме "в сети" не влияет на команду ALTER COLUMN … ADD/DROP ROWGUIDCOL/NOT FOR REPLICATION.  
  
-   Изменение столбца в режиме «в сети» не поддерживает изменение таблицы, в которой включено отслеживание изменений, или которая является издателем репликации слиянием.  
  
-   Изменение столбца в режиме «в сети» не поддерживает изменение с типов данных CLR или на типы данных CLR.  
  
-   Изменение столбца в режиме «в сети» не поддерживает изменение на тип данных XML, который имеет коллекцию схем, отличную от текущей коллекции схем.  
  
-   Изменение столбца в режиме «в сети» не уменьшает ограничения на то, когда столбец может быть изменен. Ссылки из индекса, статистических данных и т. п. могут привести к сбою изменения.  
  
-   Изменение в режиме «в сети» нескольких столбцов одновременно не поддерживается.  
  
-   Через Интернет столбца не оказывает влияния при использовании темпоральной таблицы с системным управлением версиями. Столбец ALTER не выполняется в оперативном режиме независимо от того, какое значение указано для параметра ONLINE.  
  
Изменение столбца в режиме «в сети» имеет такие же требования, ограничения и функциональные возможности, как и перестроение индекса в режиме «в сети». В том числе:  
  
-   Перестроение индекса в режиме «в сети» не поддерживается, если таблица содержит устаревшие столбцы с типом LOB или FILESTREAM, или если таблица имеет индекс columnstore. Эти же ограничения действуют при изменении столбца в режиме «в сети».  
  
-   Для изменения существующего столбца требуется удвоенное выделение пространства — для исходного столбца и для вновь создаваемого скрытого столбца.  
  
-   Стратегия блокировки во время операции изменения столбца в режиме «в сети» использует ту же модель блокировки, что и при перестроении индекса в режиме «в сети».  
  
WITH CHECK | WITH NOCHECK  
 Указывает, удовлетворяют ли данные в таблице недавно добавленному или повторно включенному ограничению FOREIGN KEY или CHECK. Если не указано иное, для новых ограничений предполагается использовать WITH CHECK, а для повторно включенных ограничений — WITH NOCHECK.  
  
 Если проверка новых ограничений CHECK или FOREIGN KEY относительно существующих данных не нужна, используйте WITH NOCHECK. За исключением редких случаев делать этого не рекомендуется. Новое ограничение будет проверяться во всех дальнейших обновлениях данных. Любые нарушения ограничений, подавляемые WITH NOCHECK во время добавления ограничения, могут вызвать сбой будущих обновлений, если они обновляют строки данными, не соответствующими ограничениям.  
  
 Оптимизатор запросов не рассматривает ограничения, которые определены WITH NOCHECK. Такие ограничения не учитываются до тех пор, пока они не будут повторно включены инструкцией `ALTER TABLE table WITH CHECK CHECK CONSTRAINT ALL`.  
  
 ADD  
 Указывает, что добавлены определения столбцов, определений вычисляемого столбца или ограничений таблицы, или столбцы, которые система будет использовать для системы управления версиями.  
  
 PERIOD FOR SYSTEM_TIME (system_start_time_column_name, system_end_time_column_name)  
 **Применяется к**: [!INCLUDE[ssCurrentLong](../../includes/sscurrentlong-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] и [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].  
  
 Задает имена столбцов, система будет использовать для записи период, в течение которого запись остается действительным. Можно указать существующие столбцы или создавать новые столбцы как часть аргумента ADD PERIOD FOR SYSTEM_TIME. Столбцы должны иметь тип данных datetime2 и должен быть определен как NOT NULL. Если столбец периода определяется как значение NULL, возникает ошибка. Можно определить [column_constraint &#40; Transact-SQL &#41; ](../../t-sql/statements/alter-table-column-constraint-transact-sql.md) и/или [задание значений по умолчанию для столбцов](../../relational-databases/tables/specify-default-values-for-columns.md) столбцов system_start_time и system_end_time. См. в примере A в [системы управления версиями](#system_versioning) ниже демонстрируется использование значений по умолчанию для столбца system_end_time примерах.  
  
 Этот аргумент используется в сочетании с аргументом для параметра SYSTEM_VERSIONING значение для включения системы управления версиями в существующую таблицу. Дополнительные сведения см. в разделе [временных таблицах](../../relational-databases/tables/temporal-tables.md) и [Приступая к работе с Темпоральными таблицами в базе данных SQL Azure](https://azure.microsoft.com/documentation/articles/sql-database-temporal-tables/).  
  
 По состоянию на [!INCLUDE[ssCurrentLong](../../includes/sscurrentlong-md.md)], пользователи смогут пометить один или оба столбца периода **HIDDEN** флаг неявно скрыть эти столбцы таким образом, что **ВЫБЕРИТЕ \* FROM**  *\<таблицы >* не возвращает значения для этих столбцов. По умолчанию столбцы period не скрыты. Для использования, скрытые столбцы должны быть явно включены во всех запросах, которые ссылаются непосредственно на временная таблица.  
  
 DROP  
 Указывает, что удален один или несколько определений столбцов, определения вычисляемого столбца или ограничений таблицы, или удалить спецификацию для столбцов, система будет использовать для системы управления версиями.  
  
 ОГРАНИЧЕНИЕ *constraint_name*  
 Указывает, что *constraint_name* удаляется из таблицы. Может быть указано несколько ограничений.  
  
 Определяемые пользователем или предоставляемое системой имя ограничения можно определить с помощью запроса к **sys.check_constraint**, **sys.default_constraints**, **sys.key_constraints**, и **sys.foreign_keys** представления каталога.  
  
 Невозможно удалить ограничение PRIMARY KEY, если в таблице существует XML-индекс.  
  
 СТОЛБЕЦ *column_name*  
 Указывает, что *constraint_name* или *column_name* удаляется из таблицы. Может быть указано несколько столбцов.  
  
 Невозможно удалить столбец, если он:  
  
-   используется в индексе;  
  
-   используется в ограничениях CHECK, FOREIGN KEY, UNIQUE или PRIMARY KEY;  
  
-   связан со значением по умолчанию, определенным ключевым словом DEFAULT, или привязан к объекту «значение по умолчанию»;  
  
-   привязан к правилу.  
  
> [!NOTE]  
>  При удалении столбца место на диске не освобождается. В том случае, если размер строк таблицы приближается к пределу или превышает его, возможен возврат места, занятого на диске удаленным столбцом. Возврат пространства осуществляется путем создания кластеризованного индекса в таблице или перестроения существующего кластеризованного индекса с помощью [ALTER INDEX](../../t-sql/statements/alter-index-transact-sql.md). Сведения о последствиях удаления типов данных LOB разделе [запись в блоге CSS](http://blogs.msdn.com/b/psssql/archive/2012/12/03/how-it-works-gotcha-varchar-max-caused-my-queries-to-be-slower.aspx).  
  
 PERIOD FOR SYSTEM_TIME  
 **Применяется к**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] и [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].  
  
 Удаляет спецификацию для столбцов, система будет использовать для системы управления версиями.  
  
 С \<drop_clustered_constraint_option >  
 Указывает, что установлен один или несколько параметров удаления кластеризованного ограничения.  
  
 MAXDOP = *max_degree_of_parallelism*  
 **Применяется к**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] и [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].  
  
 Переопределяет **максимальная степень параллелизма** параметр конфигурации только во время обработки. Дополнительные сведения см. в разделе [Configure the max degree of parallelism Server Configuration Option](../../database-engine/configure-windows/configure-the-max-degree-of-parallelism-server-configuration-option.md).  
  
 Используйте параметр MAXDOP для ограничения числа процессоров, применяемых при выполнении параллельных планов. Максимальное число процессоров — 64.  
  
 *max_degree_of_parallelism* может принимать одно из следующих значений:  
  
 1  
 Подавляет формирование параллельных планов.  
  
 \>1  
 Ограничивает указанным значением максимальное число процессоров, используемых для параллельных операций с индексами.  
  
 0 (по умолчанию)  
 В зависимости от текущей рабочей нагрузки системы использует реальное или меньшее число процессоров.  
  
 Дополнительные сведения см. в статье [Настройка параллельных операций с индексами](../../relational-databases/indexes/configure-parallel-index-operations.md).  
  
> [!NOTE]  
>  Параллельные операции с индексами доступны не во всех выпусках [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Дополнительные сведения см. в разделе [выпуски и поддерживаемые функции для SQL Server 2016](../../sql-server/editions-and-supported-features-for-sql-server-2016.md).  
  
 ONLINE  **=**  {ON | **OFF** } \<применяемое к drop_clustered_constraint_option >  
 Определяет, будут ли базовые таблицы и связанные индексы доступны для запросов и изменения данных во время операций с индексами. Значение по умолчанию — OFF. REBUILD может выполняться как операция в режиме ONLINE.  
  
 ON  
 Долгосрочные блокировки таблицы не поддерживаются во время операций с индексами. Во время главной фазы операций с индексами только блокировка с намерением совмещаемого доступа (IS) удерживается в исходной таблице. Это обеспечивает продолжение выполнения запросов или обновлений для базовых таблиц и индексов. В начале операции совмещаемая блокировка (S) исходного объекта поддерживается в течение очень короткого времени. Если создается некластеризованный индекс, то в завершение операции на короткое время запрашивается совмещаемая блокировка (S) для источника. Блокировка типа SCH-M (изменение схемы) запрашивается, когда кластеризованный индекс создается или удаляется в режиме в сети и когда происходит перестроение кластеризованного или некластеризованного индекса. При создании индекса для временной локальной таблицы параметр ONLINE не может принимать значение ON. Допустима только однопотоковая операция перестроения кучи.  
  
 Для выполнения инструкции DDL для **КОММУТАТОР** или перестроение индекса в сети, все активные блокирующие транзакции, выполняемые для конкретной таблицы должны быть завершены. При выполнении, **КОММУТАТОР** или операция перестроения не позволяет запустить новую транзакцию и может существенно повлиять на производительность рабочей нагрузки и временно задержать доступ к базовой таблице.  
  
 OFF  
 Блокировки таблиц применяются во время выполнения операций с индексами. Блокировку изменения схемы (Sch-M) в таблице получает операция с индексами вне сети, которая создает, перестраивает или удаляет кластеризованный индекс либо перестраивает или удаляет некластеризованный индекс. Это предотвращает доступ к базовой таблице всех пользователей во время операции. Операция с индексами вне сети, создающая некластеризованный индекс, получает совмещаемую блокировку (S) в таблице. Это запрещает проводить обновления базовой таблицы, но разрешает проводить операции чтения, например инструкции SELECT. Многопотоковые операции перестроения кучи разрешены.  
  
 Дополнительные сведения см. в разделе [как Online операциях с индексом](../../relational-databases/indexes/how-online-index-operations-work.md).  
  
> [!NOTE]  
>  Операции с индексами в сети доступны не во всех выпусках [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Дополнительные сведения см. в разделе [выпуски и поддерживаемые функции для SQL Server 2016](../../sql-server/editions-and-supported-features-for-sql-server-2016.md).  
  
 ПЕРЕМЕСТИТЬ в { *partition_scheme_name***(***column_name* [1**,** ...  *n* ] **)** | *файловой группы* | **»**по умолчанию**»**  }  
 **Применяется к**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] и [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].  
  
 Указывает местоположение для перемещения строк данных, находящихся в настоящее время на конечном уровне кластеризованного индекса. Таблица перемещается на новое место. Этот параметр применяется только ограничениям, образующим кластеризованный индекс.  
  
> [!NOTE]  
>  В этом контексте default не является ключевым словом. Он представляет собой идентификатор файловой группы по умолчанию и должен иметь разделители, например: MOVE TO **»**по умолчанию**»** или MOVE TO **[**по умолчанию**]**. Если **»**по умолчанию**»** указан, параметр QUOTED_IDENTIFIER должен иметь значение ON для текущего сеанса. Это параметр по умолчанию. Дополнительные сведения см. в разделе [SET QUOTED_IDENTIFIER (Transact-SQL)](../../t-sql/statements/set-quoted-identifier-transact-sql.md).  
  
 { CHECK | NOCHECK } CONSTRAINT  
 Указывает, что *constraint_name* включен или отключен. Данный параметр может использоваться только с ограничениями FOREIGN KEY и CHECK. Если указан параметр NOCHECK, то ограничение отключено и будущие вставки или обновления столбца не проверяются относительно условий ограничений. Невозможно отключить ограничения DEFAULT, PRIMARY KEY и UNIQUE.  
  
 ALL  
 Указывает, что все ограничения отключаются при помощи параметра NOCHECK или включаются при помощи параметра CHECK.  
  
 { ENABLE | DISABLE } TRIGGER  
 Указывает, что *имя_триггера* включен или отключен. Отключенный триггер остается определенным для таблицы; однако при выполнении инструкций INSERT, UPDATE или DELETE относительно таблицы действия в триггере не выполняются до тех пор, пока он не будет включен повторно.  
  
 ALL  
 Указывает, что все триггеры в таблице включены или отключены.  
  
 *имя_триггера*  
 Указывает имя триггера, подлежащего включению или отключению.  
  
 { ENABLE | DISABLE } CHANGE_TRACKING  
 **Применяется к**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] и [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].  
  
 Указывает, разрешено или запрещено отслеживание изменений для этой таблицы. По умолчанию отслеживание изменений запрещено.  
  
 Этот параметр доступен только в том случае, если отслеживание изменений разрешено для базы данных. Дополнительные сведения см. в разделе [Параметры ALTER DATABASE SET (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql-set-options.md).  
  
 Чтобы разрешить отслеживание изменений, в таблице должен содержаться первичный ключ.  
  
 С **(** TRACK_COLUMNS_UPDATED  **=**  {ON | **OFF** } **)**  
 **Применяется к**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] и [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].  
  
 Указывает, производит ли компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] отслеживание обновлений столбцов. Значение по умолчанию — OFF.  
  
 SWITCH [СЕКЦИИ *source_partition_number_expression* ] TO [ *имя_схемы***.** ] *target_table* [СЕКЦИИ *target_partition_number_expression* ]  
 **Применяется к**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] и [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].  
  
 Переключает блок данных одним из следующих способов.  
  
-   Переназначает все табличные данные как секцию в уже существующей секционированной таблице.  
  
-   Переключает секции из одной секционированной таблицы в другую.  
  
-   Переназначает все данные одной секции секционированной таблицы в уже существующую несекционированную таблицу.  
  
Если *таблицы* в секционированной таблице, *source_partition_number_expression* должен быть указан. Если *target_table* секционирована, *target_partition_number_expression* должен быть указан. Если происходит переназначение данных таблицы как секции в уже существующую секционированную таблицу или переключение секции с одной секционированной таблицы на другую, то конечная секция уже должна существовать и быть пустой.  
  
 Если происходит переназначение данных одной секции для формирования одиночной таблицы, то уже должна быть создана пустая целевая таблица. И исходная таблица или секция, и целевая таблица или секция должны располагаться в одной файловой группе. Соответствующие индексы или секции индексов также должны располагаться в одной и той же файловой группе. К переключаемым секциям применяются многие дополнительные ограничения. *Таблица* и *target_table* не могут совпадать. *target_table* может быть составным идентификатором.  
  
 *source_partition_number_expression* и *target_partition_number_expression* являются константными выражениями, которые могут ссылаться на переменные и функции. В их число входят переменные определяемого пользователем типа и определяемые пользователем функции. Они не могут ссылаться на выражения языка [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 Секционированная таблица с кластеризованный индекс ведет себя как секционированной куче:  
  
-   Первичный ключ должен включать ключ раздела.  
  
-   Уникальный индекс должен включать ключ раздела.  Обратите внимание, что в том числе в существующий индекс уникального ключа секции можно изменить уникальность.  
  
-   Чтобы переключение секций, все некластеризованные индексы необходимо указать ключ секции.  
  
Для **КОММУТАТОР** ограничения при использовании репликации см. в разделе [реплицировать секционированных таблиц и индексов](../../relational-databases/replication/publish/replicate-partitioned-tables-and-indexes.md).  
  
 Некластеризованные индексы columnstore для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2016 CTP-версия 1 и для базы данных SQL до версии V12 были в формате только для чтения. Некластеризованные индексы columnstore необходимо перестроить, чтобы текущий формат (который может быть обновлено) перед выполнением любых операций СЕКЦИОНИРОВАНИЯ.  
  
 ЗАДАТЬ **(** FILESTREAM_ON = { *partition_scheme_name* | *filestream_filegroup_name* |         **»** по умолчанию**»** | **»**NULL**»** }**)**  
 **Применяется к**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. |  
  
 Указывает местоположения хранения данных FILESTREAM.  
  
 Инструкция ALTER TABLE с предложением SET FILESTREAM_ON будет выполнена успешно только в том случае, если в таблице отсутствуют столбцы FILESTREAM. Добавить столбцы FILESTREAM можно с помощью второй инструкции ALTER TABLE.  
  
 Если *partition_scheme_name* указано, правила для [CREATE TABLE](../../t-sql/statements/create-table-transact-sql.md) применения. Таблица должна быть уже секционирована для строк данных, а схема разделения должна использовать те же функции секционирования и столбцы, что используются в схеме секционирования FILESTREAM.  
  
 *filestream_filegroup_name* указывает имя файловой группы FILESTREAM. В файловой группе должен быть один файл, который определен для файловой группы с помощью [CREATE DATABASE](../../t-sql/statements/create-database-sql-server-transact-sql.md) или [инструкции ALTER DATABASE](../../t-sql/statements/alter-database-transact-sql.md) вызывается инструкция, иначе возникает ошибка.  
  
 **«**по умолчанию**»** указывает файловую группу FILESTREAM с заданным свойством DEFAULT. При отсутствии файловой группы FILESTREAM возникает ошибка.  
  
 **«**NULL**»** указывает, что все ссылки на файловые группы FILESTREAM для таблицы будут удалены. Сначала должны быть удалены все столбцы FILESTREAM. Необходимо использовать инструкцию SET FILESTREAM_ON**=»**NULL**»** для удаления всех данных FILESTREAM, связанных с таблицей.  
  
 ЗАДАТЬ **(** SYSTEM_VERSIONING  **=**  {OFF | ON [(HISTORY_TABLE = schema_name. history_table_name [, DATA_CONSISTENCY_CHECK = { **ON** | OFF}])]} **)**  
 **Применяется к**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] и [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].  
  
 Отключение системы управления версиями таблицы либо включает системы управления версиями таблицы. Чтобы включить систему управления версиями, таблицы, система проверяет соблюдение требования ограничения первичного ключа для системы управления версиями, ограничение на допустимость значений NULL и тип данных. Если не используется аргумент HISTORY_TABLE, система создает новую таблицу журнала сопоставления схему текущей таблицы, создание связи между двумя таблицами и позволяет системе записывается история каждой записи в текущей таблице в таблице журнала. Имя этой таблицы журнала будет `MSSQL_TemporalHistoryFor<primary_table_object_id>`. Если аргумент HISTORY_TABLE используется для создания ссылки и использовать существующую таблицу журнала, связь создается между текущей таблицей и указанной таблицы. При создании ссылки на существующую таблицу журнала вы можете указать необходимость проверки согласованности данных. Проверка согласованности данных гарантирует, что существующие записи не перекрываются. Проверка согласованности данных является проверкой по умолчанию. Дополнительные сведения см. в разделе [Temporal Tables](../../relational-databases/tables/temporal-tables.md).  
  
HISTORY_RETENTION_PERIOD = { **БЕСКОНЕЧНЫЙ** | номер {день | ДНИ | НЕДЕЛЯ |  НЕДЕЛИ | МЕСЯЦ | МЕСЯЦЫ | ГОД | ГОДЫ}} **применяется к**: [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].  

Указывает конечным или infinte хранения для данных журнала в темпоральной таблице. Если не указано, подразумевается бесконечного хранения.
  
 ЗАДАТЬ **(** LOCK_ESCALATION = {АВТОМАТИЧЕСКИ | ТАБЛИЦА | ОТКЛЮЧИТЬ} **)**  
 **Применяется к**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] и [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].  
  
 Указывает разрешенные методы укрупнения блокировки для таблицы.  
  
 AUTO  
 Этот параметр позволяет [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] выбрать гранулярность укрупнения блокировки, подходящую для данной схемы таблицы.  
  
-   В секционированных таблицах допускается укрупнение блокировки до секций. После укрупнения блокировки до уровня секции дальнейшее укрупнение до гранулярности TABLE выполняться не будет.  
  
-   Если таблица не секционирована, то блокировка будет укрупняться до гранулярности TABLE.  
  
TABLE  
 Укрупнение блокировки будет выполняться на уровне гранулярности таблицы независимо от того, секционирована таблица или нет. Значение по умолчанию равно TABLE.  
  
 DISABLE  
 В большинстве случаев предотвращает укрупнение блокировки. Блокировки уровня таблицы запрещены не полностью. Например, при сканировании таблицы, которая не имеет кластеризованного индекса на уровне изоляции SERIALIZABLE, компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] должен установить блокировку таблицы для защиты целостности данных.  
  
 REBUILD  
 Используйте синтаксис REBUILD WITH для перестроения всей таблицы, включая все секции в секционированную таблицу. Если в таблице содержится кластеризованный индекс, то параметр REBUILD перестраивает его. REBUILD может выполняться как операция в режиме ONLINE.  
  
 Используйте синтаксис REBUILD PARTITION для перестроения одной секции в секционированной таблице.  
  
 PARTITION = ALL  
 **Применяется к**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] и [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].  
  
 Перестраивает все секции при изменении настройки сжатия секций.  
  
 REBUILD WITH ( \<rebuild_option >)  
 Все параметры применяются к таблице с кластеризованным индексом. Если в таблице не содержится кластеризованный индекс, то на структуру кучи влияют только определенные параметры.  
  
 Если определенный параметр сжатия не был указан с помощью операции REBUILD, то для секции будет использован текущий параметр сжатия. Чтобы получить текущее значение параметра, запросите **data_compression** столбца в **sys.partitions** представления каталога.  
  
 Полное описание этих параметров перестроения см [index_option &#40; Transact-SQL &#41; ](../../t-sql/statements/alter-table-index-option-transact-sql.md).  
  
 DATA_COMPRESSION  
 **Применяется к**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] и [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].  
  
 Задает режим сжатия данных для указанной таблицы, номера секции или диапазона секций. Существуют следующие параметры выбора.  
  
 NONE  
 Таблица или указанные секции не сжимаются. Это не относится к таблицам columnstore.  
  
 ROW  
 Таблицы или указанные секции сжимаются, используя сжатие строк. Это не относится к таблицам columnstore.  
  
 PAGE  
 Таблицы или указанные секции сжимаются, используя сжатие страниц. Это не относится к таблицам columnstore.  
  
 COLUMNSTORE  
 **Применяется к**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] и [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].  
  
 Применяется только к таблицам columnstore. COLUMNSTORE указывает, что должна быть распакована секция, которая была упакована с помощью параметра COLUMNSTORE_ARCHIVE. При восстановлении данных сжатие будет продолжаться с применением сжатия columnstore, предусмотренного для всех таблиц columnstore.  
  
 COLUMNSTORE_ARCHIVE  
 **Применяется к**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] и [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].  
  
 Применяется только к таблицам columnstore, представляющим собой таблицы, которые хранятся с кластеризованным индексом columnstore. Параметр COLUMNSTORE_ARCHIVE обеспечивает дальнейшее сжатие указанной секции до еще меньшего размера. Это может использоваться для архивации или в других ситуациях, где требуется уменьшение объема пространства и допускается увеличение затрат времени на хранение и извлечение.  
  
 Чтобы перестроить несколько секций, в то же время, в разделе [index_option &#40; Transact-SQL &#41; ](../../t-sql/statements/alter-table-index-option-transact-sql.md). Если в таблице отсутствует кластеризованный индекс, то при изменении сжатия данных выполняется перестроение кучи и некластеризованных индексов. Дополнительные сведения о сжатии см. в разделе [сжатие данных](../../relational-databases/data-compression/data-compression.md).  
  
 ONLINE  **=**  {ON | **OFF** } \<применяемое к single_partition_rebuild_option >  
 Определяет, будут ли отдельная секция базовой таблицы и связанные индексы доступны для запросов и изменения данных во время операций с индексами. Значение по умолчанию — OFF. REBUILD может выполняться как операция в режиме ONLINE.  
  
 ON  
 Долгосрочные блокировки таблицы не поддерживаются во время операций с индексами. Необходимо наличие S-блокировки таблицы в начале перестройки индекса и блокировки Sch-M на таблице в конце перестроения индекса в режиме «в сети». Обе блокировки являются короткими блокировками метаданных, но при этом блокировка изменения схемы (Sch-M) должна ожидать завершения всех блокирующих транзакций. Во время ожидания Sch-M блокирует все другие транзакции, ожидающие за этой блокировкой доступа к одной таблице.  
  
> [!NOTE]  
>  Перестроение индекса в сети можно задать *low_priority_lock_wait* параметров, описанных далее в этом разделе.  
  
 OFF  
 Блокировки таблиц применяются во время выполнения операций с индексами. Это предотвращает доступ к базовой таблице всех пользователей во время операции.  
  
 *имя_набора_столбцов* XML COLUMN_SET FOR ALL_SPARSE_COLUMNS  
 **Применяется к**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] и [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].  
  
 Имя набора столбцов. Набор столбцов представляет собой нетипизированное XML-представление, в котором все разреженные столбцы таблицы объединены в структурированные выходные данные. Набор столбцов не может быть добавлен в таблицу, если в ней содержатся разреженные столбцы. Дополнительные сведения о наборах столбцов см. в разделе [Использование наборов столбцов](../../relational-databases/tables/use-column-sets.md).  
  
 { ENABLE | DISABLE } FILETABLE_NAMESPACE  
 **Область применения**: начиная с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Включает или выключает ограничения для таблицы FileTable, заданные системой. Может использоваться только для таблицы FileTable.  
  
 ЗАДАЙТЕ (FILETABLE_DIRECTORY = *directory_name* )  
 **Область применения**: начиная с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Указывает имя каталога таблицы FileTable, совместимое с Windows. Это имя должно быть уникальным среди всех имен каталогов FileTable в базе данных. Проверка уникальности не учитывает регистр символов независимо от параметров сортировки SQL. Может использоваться только для таблицы FileTable.  
```    
 SET (  
        REMOTE_DATA_ARCHIVE   
        {  
            = ON (  <table_stretch_options> )  
          | = OFF_WITHOUT_DATA_RECOVERY  
          ( MIGRATION_STATE = PAUSED ) | ( <table_stretch_options> [, ...n] )  
        } )  
```    
**Область применения**: [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Включает или отключает базы данных Stretch для таблицы. Дополнительные сведения см. в разделе [Stretch Database](../../sql-server/stretch-database/stretch-database.md).  
  
 **Включение базы данных Stretch для таблицы**  
  
 Если включить растяжение для таблицы, указав `ON`, необходимо также указать `MIGRATION_STATE = OUTBOUND` начинается немедленно, перенос данных или `MIGRATION_STATE = PAUSED` чтобы отложить перенос данных. Значение по умолчанию — `MIGRATION_STATE = OUTBOUND`. Дополнительные сведения о включении растяжения для таблицы см. в разделе [включения базы данных Stretch для таблицы](../../sql-server/stretch-database/enable-stretch-database-for-a-table.md).  
  
 **Предварительные требования**. Прежде чем включать Stretch для таблицы, необходимо включить растяжение на сервере и в базе данных. Дополнительные сведения см. в разделе [Enable Stretch Database for a database](../../sql-server/stretch-database/enable-stretch-database-for-a-database.md).  
  
 **Разрешения**. Включение Stretch для базы данных или таблицы требуются права db_owner. Включение Stretch для таблицы также требуется разрешение ALTER на таблицу.  
  
 **Отключение базы данных Stretch для таблицы**  
  
 При отключении Stretch для таблицы имеется два варианта удаленных данных, уже перенесенные в Azure. Дополнительные сведения см. в разделе [Отключение Stretch Database и возврат удаленных данных](../../sql-server/stretch-database/disable-stretch-database-and-bring-back-remote-data.md).  
  
-   Чтобы отключить базу данных Stretch для таблицы и скопировать удаленные данные из Azure обратно в SQL Server, запустите следующую команду. Эту команду нельзя отменить.  
  
    ```tsql  
ALTER TABLE \<table name>
       SET ( REMOTE_DATA_ARCHIVE ( MIGRATION_STATE = INBOUND ) ) ;  
    ```  
  
     Эта операция предусматривает расходы на передачу данных и не может быть отменена. Дополнительные сведения см. на странице [Сведения о ценах —передача данных](https://azure.microsoft.com/en-us/pricing/details/data-transfers/).  
  
     После копирования всех удаленных данных из Azure в SQL Server база данных Stretch для таблицы будет отключена.  
  
-   Чтобы отключить растяжение для таблицы и отказаться от удаленных данных, выполните следующую команду.  
  
    ```tsql  
ALTER TABLE \<table_name>
       SET ( REMOTE_DATA_ARCHIVE = OFF_WITHOUT_DATA_RECOVERY ( MIGRATION_STATE = PAUSED ) ) ;  
    ```  
  
 Когда вы отключите Stretch Database для таблицы, перенос данных остановится, а результаты запроса больше не будут включать результаты из удаленной таблицы.  
  
 Отключение растягивания удаленной таблицы, не удаляются. Если вы хотите удалить размещенную удаленно таблицу, вам нужно сделать это с помощью портала управления Azure.  
  
[FILTER_PREDICATE = {null | *предикат* }]  
 **Область применения**: [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 При необходимости указывает предикат фильтра для выбора строк для миграции из таблицы, которая содержит исторические и текущие данные. Этот предикат должен вызывать детерминированной встроенной табличной функции. Дополнительные сведения см. в разделе [включения базы данных Stretch для таблицы](../../sql-server/stretch-database/enable-stretch-database-for-a-table.md) и [Выбор строк для миграции, используя функцию фильтрации &#40; База данных Stretch &#41; ](../../sql-server/stretch-database/select-rows-to-migrate-by-using-a-filter-function-stretch-database.md).   
  
> [!IMPORTANT]  
>  Если указать плохо оптимизированный предикат фильтра, перенос данных будет выполняться медленно. Stretch Database применяет предикат фильтра к таблице при помощи оператора CROSS APPLY.  
  
 Если предикат фильтра не указан, переносится вся таблица.  
  
 При указании предикат фильтра, необходимо указать *параметра MIGRATION_STATE*.  
  
 ПАРАМЕТРА MIGRATION_STATE = {ИСХОДЯЩИХ |  ВХОДЯЩИЙ | ПРИОСТАНОВЛЕНО}  
 **Область применения**: [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
-   Укажите `OUTBOUND` для переноса данных из SQL Server в Azure.  
  
-   Укажите `INBOUND` для копирования удаленной данные таблицы из Azure обратно в SQL Server и отключить растяжение для таблицы. Дополнительные сведения см. в разделе [Отключение Stretch Database и возврат удаленных данных](../../sql-server/stretch-database/disable-stretch-database-and-bring-back-remote-data.md).  
  
     Эта операция предусматривает расходы на передачу данных и не может быть отменена.  
  
-   Укажите `PAUSED` чтобы приостанавливать и откладывать переноса данных. Дополнительные сведения см. в разделе [Приостановка и возобновление переноса данных &#40; База данных Stretch &#41; ](../../sql-server/stretch-database/pause-and-resume-data-migration-stretch-database.md).  
  
WAIT_AT_LOW_PRIORITY  
 **Применяется к**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] и [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].  
  
 Перестроение индекса в режиме «в сети» должно ожидать операции блокировки в этой таблице. **WAIT_AT_LOW_PRIORITY** указывает, что операция перестроения индекса в сети будет ожидать блокировки с низким приоритетом, позволяя другим операциям продолжить, время ожидания операции оперативного построения индекса. Пропуск **WAIT AT LOW PRIORITY** параметр эквивалентен WA`IT_AT_LOW_PRIORITY ( MAX_DURATION = 0 minutes, ABORT_AFTER_WAIT = NONE)`.  
  
 MAX_DURATION = *время* [**МИНУТ** ]  
 **Применяется к**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] и [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].  
  
 Время ожидания (целочисленное значение, указанное в минутах), **КОММУТАТОР** или блокировки для операции перестроения индекса в сети будут ожидать с низким приоритетом при выполнении команды DDL. Если операция будет заблокирована для **MAX_DURATION** время один из **ABORT_AFTER_WAIT** будут выполняться действия. **MAX_DURATION** времени всегда находится в минутах и слово **МИНУТ** можно опустить.  
  
 ABORT_AFTER_WAIT = [**NONE** | **SELF** | **ПРЕПЯТСТВИЯ** }]  
 **Применяется к**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] и [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].  
  
 None  
 Продолжить ожидание блокировки с обычным приоритетом.  
  
 SELF  
 Выход **КОММУТАТОР** или операция DDL перестроения индекса в сети, выполняющейся в данный момент без выполнения действий.  
  
 BLOCKERS  
 Остановить все пользовательские транзакции, которые в данный момент блокирующие **КОММУТАТОР** или, чтобы можно было продолжить данную операцию операцию DDL по перестроению индекса в сети.  
  
 Требуется **разрешение ALTER ANY CONNECTION** разрешение.  
  
ЕСЛИ СУЩЕСТВУЕТ  
 **Применяется к**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] через [текущей версии](http://go.microsoft.com/fwlink/p/?LinkId=299658)) и [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].  
  
 Условно удаляет столбец или ограничение, только в том случае, если он уже существует.  
  
## <a name="remarks"></a>Замечания  
 Чтобы добавить новые строки данных, используйте [вставить](../../t-sql/statements/insert-transact-sql.md). Чтобы удалить строки данных, используйте [удаление](../../t-sql/statements/delete-transact-sql.md) или [TRUNCATE TABLE](../../t-sql/statements/truncate-table-transact-sql.md). Чтобы изменить значения в существующих строках, используйте [обновление](../../t-sql/queries/update-transact-sql.md).  
  
 При наличии в кэше процедур каких-либо планов выполнения, ссылающихся на таблицу, инструкция ALTER TABLE помечает их как подлежащие перекомпиляции в их следующем выполнении.  
  
## <a name="changing-the-size-of-a-column"></a>Изменение размера столбца  
 Длину, точность и масштаб столбца можно изменить, указав новый размер для типа данных столбца в предложении ALTER COLUMN. Если в столбце имеются данные, новый размер не может быть меньше максимального размера данных. Кроме того, столбец нельзя определить в индексе, если столбец не принадлежит **varchar**, **nvarchar**, или **varbinary** тип данных и индекс не является результатом ПЕРВИЧНОГО ключа ограничение. См. пример Р.  
  
## <a name="locks-and-alter-table"></a>Блокировки и инструкция ALTER TABLE  
 Изменения, указанные в инструкции ALTER TABLE, воплощаются немедленно. Если для изменений требуется модификация строк таблицы, то инструкция ALTER TABLE обновляет эти строки. Инструкция ALTER TABLE получает блокировку модификации схемы (SCH-M) для таблицы, чтобы убедиться, что в процессе изменения другие соединения не ссылаются даже на метаданные таблицы, за исключением операций с индексами в сети, требующих очень короткой блокировки SCH-M в конце. В операции ALTER TABLE...SWITCH запрашивается блокировка и исходной, и целевой таблиц. Изменения, сделанные в таблице, регистрируются в журнале и полностью обратимы. Изменения, затрагивающие все строки в очень больших таблицах, например удаление столбца или (в некоторых выпусках [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]) добавление столбца NOT NULL со значением по умолчанию, могут занять длительное время и привести к созданию множества записей в журнале. Данные инструкции ALTER TABLE следует выполнять с той же осторожностью, что и любые инструкции INSERT, UPDATE или DELETE, влияющие на множество строк.  
  
### <a name="adding-not-null-columns-as-an-online-operation"></a>Добавление столбцов NOT NULL в качестве операции в сети  
 Начиная с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Enterprise Edition, добавление столбца NOT NULL со значением по умолчанию является операцией в сети, если значение по умолчанию — *константой времени выполнения*. Это значит, что операция выполняется почти мгновенно, независимо от количества строк в таблице. Так происходит потому, что существующие строки в таблице не обновляются в ходе операции. Вместо этого значение по умолчанию сохраняется только в метаданных таблицы, и это значение подставляется по мере необходимости в запросах, обращающихся к этим строкам. Такой режим работы действует автоматически. Для реализации операции в сети достаточно синтаксиса ADD COLUMN. Константа времени выполнения — это выражение, которое имеет одно и то же значение во время выполнения для каждой строки в таблице независимо от ее детерминизма. Например, выражение константы «Временные данные» и системная функция GETUTCDATETIME() являются константами времени выполнения. Функции NEWID() и NEWSEQUENTIALID(), напротив, не являются константами времени выполнения, поскольку для каждой строки в таблице создается уникальное значение. Добавление столбца NOT NULL со значением по умолчанию, которое не является константой времени выполнения, всегда выполняется вне сети, и в течение этой операции накладывается монопольная блокировка (SCH-M).  
  
 Хотя существующие строки ссылаются на значение, хранящееся в метаданных, значение по умолчанию хранится в строке для всех новых строк, которые вставляются без указания другого значения для столбца. Значение по умолчанию, хранящееся в метаданных, перемещается в существующую строку, когда строка обновляется (даже если в инструкции UPDATE не указан фактический столбец), а также когда перестраивается таблица или кластеризованный индекс.  
  
 Столбцы типа **varchar(max)**, **nvarchar(max)**, **varbinary(max)**, **xml**, **текст**, **ntext**, **изображения**, **hierarchyid**, **geometry**, **geography**, или определяемых пользователем ТИПОВ CLR нельзя добавить в операцию в оперативном режиме. Столбец нельзя добавлять в сети, если в результате такой операции максимальный размер строки превысит ограничение в 8060 байт. В этом случае столбец добавляется в рамках операции вне сети.  
  
## <a name="parallel-plan-execution"></a>Выполнение параллельного плана  
 В [!INCLUDE[ssEnterpriseEd11](../../includes/ssenterpriseed11-md.md)] и более поздних версиях число процессоров, применяемых для выполнения одной инструкции ALTER TABLE ADD (на базе индекса) CONSTRAINT или DROP (кластеризованный индекс) CONSTRAINT, определяется с **максимальная степень параллелизма** конфигурации параметр и текущей рабочей нагрузки. Если компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] определяет, что система занята, то перед началом выполнения инструкции степень параллелизма операции автоматически понижается. Можно вручную настроить число процессоров, применяемых для запуска инструкции, указав параметр MAXDOP. Дополнительные сведения см. в разделе [Configure the max degree of parallelism Server Configuration Option](../../database-engine/configure-windows/configure-the-max-degree-of-parallelism-server-configuration-option.md).  
  
## <a name="partitioned-tables"></a>Секционированные таблицы  
 Помимо выполнения операций SWITCH, затрагивающих секционированные таблицы, инструкция ALTER TABLE может использоваться для изменения состояния столбцов, ограничений и триггеров секционированной таблицы точно так же, как она используется для несекционированных таблиц. Однако данная инструкция не может использоваться для изменения способа, которым секционируется сама таблица. Для повторного секционирования секционированной таблицы, используйте [ALTER PARTITION SCHEME](../../t-sql/statements/alter-partition-scheme-transact-sql.md) и [ALTER PARTITION FUNCTION](../../t-sql/statements/alter-partition-function-transact-sql.md). Кроме того, невозможно изменить тип данных столбца секционированной таблицы.  
  
## <a name="restrictions-on-tables-with-schema-bound-views"></a>Ограничения в таблицах с представлениями, привязанными к схемам  
 К инструкциям ALTER TABLE в таблицах с представлениями, привязанными к схемам, применяются те же ограничения, которые применяются в текущем времени для изменения таблиц с простым индексом. Добавление столбца разрешено. Однако удаление или изменение столбца, участвующего в любом из представлений, привязанных к схемам, не разрешается. Если инструкция ALTER TABLE требует изменения столбца, используемого в привязанном к схеме представлении, то происходит сбой инструкции ALTER TABLE и компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] выдает сообщение об ошибке. Дополнительные сведения о привязке схемы и индексированных представлениях см. в разделе [CREATE VIEW &#40; Transact-SQL &#41; ](../../t-sql/statements/create-view-transact-sql.md).  
  
 Создание ссылающегося на таблицы представления, привязанного к схеме, не влияет на добавление или удаление триггеров в базовых таблицах.  
  
## <a name="indexes-and-alter-table"></a>Индексы и инструкция ALTER TABLE  
 При удалении ограничений индексы, создаваемые как часть ограничения, удаляются. Индексы, создаваемые при помощи инструкции CREATE INDEX, должны удаляться при помощи инструкции DROP INDEX. Инструкция ALTER INDEX может использоваться для перестроения индексной части определения ограничения; не следует удалять и вновь добавлять ограничение при помощи инструкции ALTER TABLE.  
  
 Перед удалением столбца необходимо удалить все индексы и ограничения, основанные на столбце.  
  
 После удаления ограничения, создавшего кластеризованный индекс, строки данных, хранившиеся на конечном уровне кластеризованного индекса, хранятся в некластеризованной таблице. Можно удалить кластеризованный индекс и переместить полученную в результате таблицу в другую файловую группу или схему секционирования в одной транзакции, указав параметр MOVE TO. Параметр MOVE TO обладает следующими ограничениями.  
  
-   Параметр MOVE TO недопустим для индексированных представлений и некластеризованных индексов.  
  
-   Схема секционирования или файловая группа уже должна существовать.  
  
-   Если не указан аргумент MOVE TO, то таблица будет размещена в той же схеме секционирования или файловой группе, которая была определена для кластеризованного индекса.  
  
При удалении кластеризованного индекса можно указать ONLINE  **=**  на параметр, так что транзакция DROP INDEX не будет блокировать запросы и изменения базовых данных и связанных некластеризованных индексов.  
  
 ONLINE  **=**  ON имеет следующие ограничения:  
  
-   ONLINE  **=**  ON недопустимо для кластеризованных индексов, которые также отключены. Отключенные индексы должны удаляться при помощи параметра ONLINE  **=**  OFF.  
  
-   Только один индекс может удаляться единовременно.  
  
-   ONLINE  **=**  ON недопустимо для индексированного представления, некластеризованных индексов или индексов в локальных временных таблицах.  
  
-   ONLINE  **=**  ON недопустимо для индексов columnstore.  
  
Для удаления кластеризованного индекса временно требуется место на диске, равное размеру существующего кластеризованного индекса. Это дополнительное пространство освобождается сразу после завершения операции.  
  
> [!NOTE]  
>  Параметры, перечисленные в  *\<drop_clustered_constraint_option >* применяются к кластеризованным индексам таблиц и не может применяться к кластеризованным индексам представлений или некластеризованных индексов.  
  
## <a name="replicating-schema-changes"></a>Репликация изменений схемы  
 По умолчанию при выполнении команды ALTER TABLE для опубликованной таблицы в издателе [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Publisher это изменение распространяется для всех подписчиков [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Эта функция имеет некоторые ограничения и может быть отключена. Дополнительные сведения см. в статье [Внесение изменений в схемы баз данных публикации](../../relational-databases/replication/publish/make-schema-changes-on-publication-databases.md).  
  
## <a name="data-compression"></a>Data Compression  
 В системных таблицах не может быть включено сжатие. Если таблица является кучей, то операция перестроения в режиме ONLINE будет однопотоковой. Используйте режим OFFLINE для выполнения многопотоковых операций перестроения кучи. Дополнительные сведения о сжатии данных см. в разделе[сжатие данных](../../relational-databases/data-compression/data-compression.md).  
  
 Оценить состояние сжатия таблицы, индекса или секции можно с помощью хранимой процедуры [sp_estimate_data_compression_savings](../../relational-databases/system-stored-procedures/sp-estimate-data-compression-savings-transact-sql.md) .  
  
 На секционированные таблицы налагаются следующие ограничения.  
  
-   Если у таблицы есть невыровненные индексы, изменить настройку сжатия отдельной секции невозможно.  
  
-   Инструкция ALTER TABLE \<таблицы > REBUILD PARTITION... производит перестроение указанной секции.  
  
-   Инструкция ALTER TABLE \<таблицы > REBUILD WITH... производит перестроение всех секций.  
  
## <a name="dropping-ntext-columns"></a>Удаление столбцов NTEXT  
 При удалении столбцов NTEXT очистка удаленных данных выполняется как сериализованная операция для всех строк. Это может потребовать значительного времени. При удалении столбца NTEXT в таблице с большим количеством строк сначала задайте в столбце NTEXT значение NULL, а затем удалите столбец. Это можно выполнить с помощью параллельных операций, причем сделать это намного быстрее.  
  
## <a name="online-index-rebuild"></a>Перестроение индексов в режиме «в сети».  
 Для выполнения инструкции DDL для перестроения индекса в режиме «в сети» все активные блокирующие транзакции, выполняемые для конкретной таблицы, должны быть завершены. Если выполняется перестроение индекса в режиме «в сети», то все новые транзакции, готовые к выполнению на данной таблице, блокируются. Хотя продолжительность блокировки для перестроения индекса в режиме «в сети» очень коротка, ожидание завершения всех открытых транзакций на данной таблице и блокировка новых запускаемых транзакций может значительно отразиться на пропускной способности и времени выполнения операции, а также значительно ограничить доступ к базовой таблице. **WAIT_AT_LOW_PRIORITY** параметр позволяет администратору базы данных управлять S-lock и Sch-M блокировками, необходимыми для индекса в сети перестраивает и их можно выбрать один из трех значений. Во всех 3 случаях, если во время ожидания ( `(MAX_DURATION =n [minutes])` ) нет блокирующих действий, то перестроение индекса в режиме «в сети» выполняется немедленно и без ожидания завершения инструкции DDL.  
  
## <a name="compatibility-support"></a>Поддержка совместимости  
 В инструкции ALTER TABLE разрешается использовать только имена таблиц, составленные из двух частей (схема.объект). В [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] при задании имени таблицы в приведенных далее форматах во время компиляции возникает ошибка 117.  
  
-   «сервер.база_данных.схема.таблица»  
  
-   «.база_данных.схема.таблица»  
  
-   «..схема.таблица»  
  
В предыдущих версиях при задании формата «сервер.база_данных.схема.таблица» возникала ошибка 4902. Формат «.база_данных.схема.таблица» или «..схема.таблица» обрабатывался успешно.  
  
 Чтобы устранить эту проблему, используйте четырехкомпонентный префикс.  
  
## <a name="permissions"></a>Permissions  
 Требуется разрешение ALTER на таблицу.  
  
 Разрешения ALTER TABLE применяются к обеим таблицам, затронутым инструкцией ALTER TABLE SWITCH. Любые переключенные данные наследуют защиту целевой таблицы.  
  
 Если какой-либо из столбцов в инструкции ALTER TABLE является определяемым пользователем типом для среды CLR или как псевдоним типа данных, то на этот тип требуется разрешение REFERENCES.  
  
 Добавление столбца, который обновляет строки таблицы требует **обновление** разрешение на таблицу. Например, при добавлении **NOT NULL** столбец со значением по умолчанию или добавление столбца идентификаторов, если таблица не пуста.  
  
##  <a name="Example_Top"></a> Примеры  
  
|Категория|Используемые элементы синтаксиса|  
|--------------|------------------------------|  
|[Добавление столбцов и ограничений](#add)|ADD • PRIMARY KEY с параметрами индекса • разреженные столбцы и наборы столбцов •|  
|[Удаление столбцов и ограничений](#Drop)|DROP|  
|[Изменение определения столбца](#alter_column)|изменение типа данных • изменение размера столбца • параметры сортировки|  
|[Изменение определения таблицы](#alter_table)|DATA_COMPRESSION • SWITCH PARTITION • LOCK ESCALATION • отслеживание изменений|  
|[Отключение и включение ограничений и триггеров](#disable_enable)|CHECK • NO CHECK • ENABLE TRIGGER • DISABLE TRIGGER|  
  
###  <a name="add"></a>Добавление столбцов и ограничений  
 В примерах из этого раздела показано добавление в таблицу столбцов и ограничений.  
  
#### <a name="a-adding-a-new-column"></a>A. Добавление нового столбца  
 Следующий пример показывает добавление столбца, который допускает значения NULL и не имеет значений, предоставленных через определение DEFAULT. В новом столбце в каждой строке будет значение `NULL`.  
  
```  
CREATE TABLE dbo.doc_exa (column_a INT) ;  
GO  
ALTER TABLE dbo.doc_exa ADD column_b VARCHAR(20) NULL ;  
GO  
  
```  
  
#### <a name="b-adding-a-column-with-a-constraint"></a>Б. Добавление столбца с ограничением  
 В следующем примере показано добавление нового столбца с ограничением `UNIQUE`.  
  
```  
CREATE TABLE dbo.doc_exc (column_a INT) ;  
GO  
ALTER TABLE dbo.doc_exc ADD column_b VARCHAR(20) NULL   
    CONSTRAINT exb_unique UNIQUE ;  
GO  
EXEC sp_help doc_exc ;  
GO  
DROP TABLE dbo.doc_exc ;  
GO  
```  
  
#### <a name="c-adding-an-unverified-check-constraint-to-an-existing-column"></a>В. Добавление непроверяемого ограничения CHECK к существующему столбцу  
 В следующем примере к существующему столбцу в таблице добавляется ограничение. Столбец имеет значение, нарушающее это ограничение. Поэтому во избежание проверки ограничения относительно существующих строк, а также для того, чтобы разрешить добавление ограничения, применяется `WITH NOCHECK`.  
  
```  
CREATE TABLE dbo.doc_exd ( column_a INT) ;  
GO  
INSERT INTO dbo.doc_exd VALUES (-1) ;  
GO  
ALTER TABLE dbo.doc_exd WITH NOCHECK   
ADD CONSTRAINT exd_check CHECK (column_a > 1) ;  
GO  
EXEC sp_help doc_exd ;  
GO  
DROP TABLE dbo.doc_exd ;  
GO  
```  
  
#### <a name="d-adding-a-default-constraint-to-an-existing-column"></a>Г. Добавление ограничения DEFAULT к существующему столбцу  
 Следующий пример показывает создание таблицы с двумя столбцами и заполнение значениями первого столбца; в другом столбце остается NULL. В таком случае во второй столбец добавляется ограничение `DEFAULT`. Чтобы проверить применение значения по умолчанию, в первый столбец вставляется другое значение и создается запрос к таблице.  
  
```  
CREATE TABLE dbo.doc_exz ( column_a INT, column_b INT) ;  
GO  
INSERT INTO dbo.doc_exz (column_a)VALUES ( 7 ) ;  
GO  
ALTER TABLE dbo.doc_exz  
ADD CONSTRAINT col_b_def  
DEFAULT 50 FOR column_b ;  
GO  
INSERT INTO dbo.doc_exz (column_a) VALUES ( 10 ) ;  
GO  
SELECT * FROM dbo.doc_exz ;  
GO  
DROP TABLE dbo.doc_exz ;  
GO  
```  
  
#### <a name="e-adding-several-columns-with-constraints"></a>Д. Добавление нескольких столбцов с ограничениями  
 Следующий пример показывает добавление нескольких столбцов с ограничениями, которые определяются с помощью нового столбца. Первый новый столбец имеет свойство `IDENTITY`. Каждая строка таблицы имеет новые добавочные значения в столбце идентификаторов.  
  
```  
CREATE TABLE dbo.doc_exe ( column_a INT CONSTRAINT column_a_un UNIQUE) ;  
GO  
ALTER TABLE dbo.doc_exe ADD   
  
-- Add a PRIMARY KEY identity column.  
column_b INT IDENTITY  
CONSTRAINT column_b_pk PRIMARY KEY,   
  
-- Add a column that references another column in the same table.  
column_c INT NULL    
CONSTRAINT column_c_fk   
REFERENCES doc_exe(column_a),  
  
-- Add a column with a constraint to enforce that   
-- nonnull data is in a valid telephone number format.  
column_d VARCHAR(16) NULL   
CONSTRAINT column_d_chk  
CHECK   
(column_d LIKE '[0-9][0-9][0-9]-[0-9][0-9][0-9][0-9]' OR  
column_d LIKE  
'([0-9][0-9][0-9]) [0-9][0-9][0-9]-[0-9][0-9][0-9][0-9]'),  
  
-- Add a nonnull column with a default.  
column_e DECIMAL(3,3)  
CONSTRAINT column_e_default  
DEFAULT .081 ;  
GO  
EXEC sp_help doc_exe ;  
GO  
DROP TABLE dbo.doc_exe ;  
GO  
```  
  
#### <a name="f-adding-a-nullable-column-with-default-values"></a>Е. Добавление столбца, допускающего значения NULL, со значениями по умолчанию  
 Следующий пример показывает добавление столбца, допускающего значения NULL, с определением `DEFAULT` и использование `WITH VALUES` для предоставления значений каждой строке таблицы. Если аргумент WITH VALUES не используется, то каждая строка в новом столбце имеет значение NULL.  
  
```  
  
CREATE TABLE dbo.doc_exf ( column_a INT) ;  
GO  
INSERT INTO dbo.doc_exf VALUES (1) ;  
GO  
ALTER TABLE dbo.doc_exf   
ADD AddDate smalldatetime NULL  
CONSTRAINT AddDateDflt  
DEFAULT GETDATE() WITH VALUES ;  
GO  
DROP TABLE dbo.doc_exf ;  
GO  
```  
  
#### <a name="g-creating-a-primary-key-constraint-with-index-options"></a>Ж. Создание ограничения PRIMARY KEY с параметрами индекса  
 Следующий пример показывает создание ограничения PRIMARY KEY `PK_TransactionHistoryArchive_TransactionID` и установку параметров `FILLFACTOR`, `ONLINE` и `PAD_INDEX`. Результирующий кластеризованный индекс будет иметь такое же имя, что и ограничение.  
  
**Применяется к**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] и [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].  
  
```  
USE AdventureWorks2012;  
GO  
ALTER TABLE Production.TransactionHistoryArchive WITH NOCHECK   
ADD CONSTRAINT PK_TransactionHistoryArchive_TransactionID PRIMARY KEY CLUSTERED (TransactionID)  
WITH (FILLFACTOR = 75, ONLINE = ON, PAD_INDEX = ON);  
GO  
```  
  
#### <a name="h-adding-a-sparse-column"></a>З. Добавление разреженного столбца  
 В следующих примерах показывается добавление и изменение разреженных столбцов в таблице T1. Код для создания таблицы `T1`:  
  
```  
CREATE TABLE T1  
(C1 int PRIMARY KEY,  
C2 varchar(50) SPARSE NULL,  
C3 int SPARSE NULL,  
C4 int ) ;  
GO  
```  
  
 Чтобы добавить дополнительный разреженный столбец `C5`, выполните следующую инструкцию.  
  
```  
ALTER TABLE T1  
ADD C5 char(100) SPARSE NULL ;  
GO  
```  
  
 Чтобы преобразовать неразреженный столбец `C4` в разреженный, выполните следующую инструкцию.  
  
```  
ALTER TABLE T1  
ALTER COLUMN C4 ADD SPARSE ;  
GO  
```  
  
 Для преобразования `C4` разреженных столбцов в Неразреженный, выполните следующую инструкцию.  
  
```  
ALTER TABLE T1  
ALTER COLUMN C4 DROP SPARSE;  
GO  
```  
  
#### <a name="i-adding-a-column-set"></a>И. Добавление набора столбцов  
 В следующих примерах показано добавление столбца к таблице `T2`. Набор столбцов не может быть добавлен в таблицу, если в ней уже содержатся разреженные столбцы. Код для создания таблицы `T2`:  
  
```  
CREATE TABLE T2  
(C1 int PRIMARY KEY,  
C2 varchar(50) NULL,  
C3 int NULL,  
C4 int ) ;  
GO  
```  
  
 В следующих трех инструкциях добавляется набор столбцов с именем `CS`, после чего изменяются столбцы `C2` и `C3` на `SPARSE`.  
  
```  
ALTER TABLE T2  
ADD CS XML COLUMN_SET FOR ALL_SPARSE_COLUMNS ;  
GO  
  
ALTER TABLE T2  
ALTER COLUMN C2 ADD SPARSE ;   
GO  
  
ALTER TABLE T2  
ALTER COLUMN C3 ADD SPARSE ;  
GO  
```  
  
#### <a name="j-adding-an-encrypted-column"></a>К. Добавление зашифрованного столбца  
 Следующая инструкция добавляет зашифрованный столбец с именем `PromotionCode`.  
  
```  
ALTER TABLE Customers ADD  
    PromotionCode nvarchar(100)   
    ENCRYPTED WITH (COLUMN_ENCRYPTION_KEY = MyCEK,  
    ENCRYPTION_TYPE = RANDOMIZED,  
    ALGORITHM = 'AEAD_AES_256_CBC_HMAC_SHA_256') ;  
```  
  
###  <a name="Drop"></a>Удаление столбцов и ограничений  
 Приведенные в этом разделе примеры демонстрируют удаление столбцов и ограничений.  
  
#### <a name="a-dropping-a-column-or-columns"></a>A. Удаление столбца или столбцов  
 В первом примере для удаления столбца изменяется таблица. Во втором примере удаляется несколько столбцов.  
  
```  
CREATE TABLE dbo.doc_exb   
    (column_a INT  
     ,column_b VARCHAR(20) NULL  
     ,column_c datetime  
     ,column_d int) ;  
GO  
-- Remove a single column.  
ALTER TABLE dbo.doc_exb DROP COLUMN column_b ;  
GO  
-- Remove multiple columns.  
ALTER TABLE dbo.doc_exb DROP COLUMN column_c, column_d;  
  
```  
  
#### <a name="b-dropping-constraints-and-columns"></a>Б. Удаление ограничений и столбцов  
 В первом примере из таблицы удаляется ограничение `UNIQUE`. Во втором примере удаляется 2 ограничения и один столбец.  
  
```  
CREATE TABLE dbo.doc_exc ( column_a int NOT NULL CONSTRAINT my_constraint UNIQUE) ;  
GO  
  
-- Example 1. Remove a single constraint.  
ALTER TABLE dbo.doc_exc DROP my_constraint ;  
GO  
  
DROP TABLE dbo.doc_exc;  
GO  
  
CREATE TABLE dbo.doc_exc ( column_a int    
                          NOT NULL CONSTRAINT my_constraint UNIQUE  
                          ,column_b int   
                          NOT NULL CONSTRAINT my_pk_constraint PRIMARY KEY) ;  
GO  
  
-- Example 2. Remove two constraints and one column  
-- The keyword CONSTRAINT is optional. The keyword COLUMN is required.  
ALTER TABLE dbo.doc_exc   
  
    DROP CONSTRAINT CONSTRAINT my_constraint, my_pk_constraint, COLUMN column_b ;  
GO  
  
```  
  
#### <a name="c-dropping-a-primary-key-constraint-in-the-online-mode"></a>В. Удаление ограничения PRIMARY KEY в режиме ONLINE  
 В следующем примере удаляется ограничение PRIMARY KEY с параметром `ONLINE`, имеющим значение `ON`.  
  
```  
  
ALTER TABLE Production.TransactionHistoryArchive  
DROP CONSTRAINT PK_TransactionHistoryArchive_TransactionID  
WITH (ONLINE = ON);  
GO  
```  
  
#### <a name="d-adding-and-dropping-a-foreign-key-constraint"></a>Г. Добавление и удаление ограничения FOREIGN KEY  
 Следующий пример показывает создание таблицы `ContactBackup`, а затем ее изменение сначала добавлением ограничения `FOREIGN KEY`, ссылающегося на таблицу `Person.Person`, затем удалением ограничения `FOREIGN KEY`.  
  
```  
CREATE TABLE Person.ContactBackup  
    (ContactID int) ;  
GO  
  
ALTER TABLE Person.ContactBackup  
ADD CONSTRAINT FK_ContactBacup_Contact FOREIGN KEY (ContactID)  
    REFERENCES Person.Person (BusinessEntityID) ;  
GO  
  
ALTER TABLE Person.ContactBackup  
DROP CONSTRAINT FK_ContactBacup_Contact ;  
GO  
  
DROP TABLE Person.ContactBackup ;  
```  
  
 ![Значок стрелки, используемый с обратно к верхней](../../analysis-services/instances/media/uparrow16x16.gif "значок стрелки, используемый с обратно к верхней") [примеры](#Example_Top)  
  
###  <a name="alter_column"></a>Изменение определения столбца  
  
#### <a name="a-changing-the-data-type-of-a-column"></a>A. изменение типа данных столбца.  
 В следующем примере столбец таблицы изменяется с `INT` на `DECIMAL`.  
  
```  
CREATE TABLE dbo.doc_exy (column_a INT ) ;  
GO  
INSERT INTO dbo.doc_exy (column_a) VALUES (10) ;  
GO  
ALTER TABLE dbo.doc_exy ALTER COLUMN column_a DECIMAL (5, 2) ;  
GO  
DROP TABLE dbo.doc_exy ;  
GO  
```  
  
#### <a name="b-changing-the-size-of-a-column"></a>Б. Изменение размера столбца  
 В следующем примере увеличивается размер **varchar** столбца и точность и масштаб **десятичное** столбца. Поскольку столбцы содержат данные, их размер можно только увеличить. Также обратите внимание, что столбец `col_a` определяется в уникальном индексе. Размер `col_a` по-прежнему может повыситься, поскольку тип данных **varchar** и индекс не является результатом ограничения PRIMARY KEY.  
  
```  
-- Create a two-column table with a unique index on the varchar column.  
CREATE TABLE dbo.doc_exy ( col_a varchar(5) UNIQUE NOT NULL, col_b decimal (4,2));  
GO  
INSERT INTO dbo.doc_exy VALUES ('Test', 99.99);  
GO  
-- Verify the current column size.  
SELECT name, TYPE_NAME(system_type_id), max_length, precision, scale  
FROM sys.columns WHERE object_id = OBJECT_ID(N'dbo.doc_exy');  
GO  
-- Increase the size of the varchar column.  
ALTER TABLE dbo.doc_exy ALTER COLUMN col_a varchar(25);  
GO  
-- Increase the scale and precision of the decimal column.  
ALTER TABLE dbo.doc_exy ALTER COLUMN col_b decimal (10,4);  
GO  
-- Insert a new row.  
INSERT INTO dbo.doc_exy VALUES ('MyNewColumnSize', 99999.9999) ;  
GO  
-- Verify the current column size.  
SELECT name, TYPE_NAME(system_type_id), max_length, precision, scale  
FROM sys.columns WHERE object_id = OBJECT_ID(N'dbo.doc_exy');  
```  
  
#### <a name="c-changing-column-collation"></a>В. Изменение параметров сортировки столбца  
 В следующем примере демонстрируется изменение параметров сортировки столбца. Сначала создается таблица с параметрами сортировки пользователя по умолчанию.  
  
```  
CREATE TABLE T3  
(C1 int PRIMARY KEY,  
C2 varchar(50) NULL,  
C3 int NULL,  
C4 int ) ;  
GO  
```  
  
 Затем параметры сортировки столбца `C2` изменяются на Latin1_General_BIN. Обратите внимание, что необходимо указать тип данных, хотя он не изменяется.  
  
```  
ALTER TABLE T3  
ALTER COLUMN C2 varchar(50) COLLATE Latin1_General_BIN;  
GO  
  
```  

  
###  <a name="alter_table"></a>Изменение определения таблицы  
 В приведенных в этом разделе примерах показано, как изменить определение таблицы.  
  
#### <a name="a-modifying-a-table-to-change-the-compression"></a>A. Изменение таблицы для изменения режима сжатия  
 В следующем примере изменяется режим сжатия несекционированной таблицы. Куча или кластеризованный индекс будет перестроен. Если таблица является кучей, то все некластеризованные индексы будут перестроены.  
  
```  
ALTER TABLE T1   
REBUILD WITH (DATA_COMPRESSION = PAGE);  
```  
  
 В следующем примере изменяется режим сжатия секционированной таблицы. Инструкция `REBUILD PARTITION = 1` вызывает перестройку только секции с номером `1`.  
  
**Применяется к**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] и [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].  
  
```  
ALTER TABLE PartitionTable1   
REBUILD PARTITION = 1 WITH (DATA_COMPRESSION =  NONE) ;  
GO  
```  
  
Та же операция, использующая следующий альтернативный синтаксис, вызывает повторное построение всех секций в таблице.  
  
**Применяется к**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] и [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].  
  
```  
ALTER TABLE PartitionTable1   
REBUILD PARTITION = ALL   
WITH (DATA_COMPRESSION = PAGE ON PARTITIONS(1) ) ;  
```  
  
 Дополнительные примеры сжатия данных, в разделе [сжатие данных](../../relational-databases/data-compression/data-compression.md).  
  
#### <a name="b-modifying-a-columnstore-table-to-change-archival-compression"></a>Б. Модификация таблицы columnstore для изменения архивного сжатия  
 Следующий пример показывает, как дополнительно сжать секцию таблицы columnstore, применяя дополнительный алгоритм сжатия. Это приводит к дальнейшему уменьшению размера таблицы, но вместе с тем к увеличению затрат времени на сохранение и выборку данных. Это может использоваться для архивации или в тех ситуациях, где требуется уменьшение объема пространства и допускается увеличение затрат времени на сохранение и выборку.  
  
**Применяется к**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] и [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].  
  
```  
ALTER TABLE PartitionTable1   
REBUILD PARTITION = 1 WITH (DATA_COMPRESSION =  COLUMNSTORE_ARCHIVE) ;  
GO  
```  
  
В следующем примере показана распаковка секции таблицы columnstore, которая была упакована с параметром COLUMNSTORE_ARCHIVE. При восстановлении данных сжатие будет продолжаться с применением сжатия columnstore, предусмотренного для всех таблиц columnstore.  
  
**Применяется к**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] и [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].  
  
```  
ALTER TABLE PartitionTable1   
REBUILD PARTITION = 1 WITH (DATA_COMPRESSION =  COLUMNSTORE) ;  
GO  
```  
  
#### <a name="c-switching-partitions-between-tables"></a>В. Переключение секций между таблицами  
 В следующем примере демонстрируется создание секционированной таблицы, исходя из предположения, что схема секционирования `myRangePS1` уже создана в базе данных. Затем создается несекционированная таблица с такой же структурой, что и секционированная таблица, и в той же файловой группе, что и `PARTITION 2` таблицы `PartitionTable`. В таком случае данные `PARTITION 2` таблицы `PartitionTable` переключаются в таблицу `NonPartitionTable`.  
  
```  
CREATE TABLE PartitionTable (col1 int, col2 char(10))  
ON myRangePS1 (col1) ;  
GO  
CREATE TABLE NonPartitionTable (col1 int, col2 char(10))  
ON test2fg ;  
GO  
ALTER TABLE PartitionTable SWITCH PARTITION 2 TO NonPartitionTable ;  
GO  
```  
  
#### <a name="d-allowing-lock-escalation-on-partitioned-tables"></a>Г. Разрешение укрупнения блокировки для секционированных таблиц  
 В следующем примере укрупнение блокировки разрешается на уровне секции в секционированной таблице. Если таблица не секционирована, то блокировка будет укрупняться до уровня TABLE.  
  
**Применяется к**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] и [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].  
  
```  
ALTER TABLE dbo.T1 SET (LOCK_ESCALATION = AUTO);  
GO  
```  
  
#### <a name="e-configuring-change-tracking-on-a-table"></a>Д. Настройка отслеживания изменений для таблицы  
 В следующем примере в таблице `Person.Person` включается отслеживание изменений.  
  
**Применяется к**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] и [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].  
  
```  
USE AdventureWorks2012;  
ALTER TABLE Person.Person  
ENABLE CHANGE_TRACKING;  
```  
  
В следующем примере разрешается отслеживание изменений и отслеживание столбцов, которые обновляются при внесении изменений.  
  
**Область применения**: начиная с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
```  
USE AdventureWorks2012;  
GO  
ALTER TABLE Person.Person  
ENABLE CHANGE_TRACKING  
WITH (TRACK_COLUMNS_UPDATED = ON)  
```  
  
В следующем примере в таблице `Person.Person` отключается отслеживание изменений.  
  
**Применяется к**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] и [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].  
  
```  
USE AdventureWorks2012;  
Go  
ALTER TABLE Person.Person  
DISABLE CHANGE_TRACKING;  
```  

  
###  <a name="disable_enable"></a>Отключение и включение ограничений и триггеров  
  
#### <a name="a-disabling-and-re-enabling-a-constraint"></a>A. Отключение и повторное включение ограничения  
 В следующем примере отключается ограничение на зарплату. Параметр `NOCHECK CONSTRAINT` используется в инструкции `ALTER TABLE` для отключения ограничения и обеспечения возможности вставки, противоречащей указанному ограничению. `CHECK CONSTRAINT` повторно включает ограничение.  
  
```  
CREATE TABLE dbo.cnst_example   
(id INT NOT NULL,  
 name VARCHAR(10) NOT NULL,  
 salary MONEY NOT NULL  
    CONSTRAINT salary_cap CHECK (salary < 100000)  
);  
  
-- Valid inserts  
INSERT INTO dbo.cnst_example VALUES (1,'Joe Brown',65000);  
INSERT INTO dbo.cnst_example VALUES (2,'Mary Smith',75000);  
  
-- This insert violates the constraint.  
INSERT INTO dbo.cnst_example VALUES (3,'Pat Jones',105000);  
  
-- Disable the constraint and try again.  
ALTER TABLE dbo.cnst_example NOCHECK CONSTRAINT salary_cap;  
INSERT INTO dbo.cnst_example VALUES (3,'Pat Jones',105000);  
  
-- Re-enable the constraint and try another insert; this will fail.  
ALTER TABLE dbo.cnst_example CHECK CONSTRAINT salary_cap;  
INSERT INTO dbo.cnst_example VALUES (4,'Eric James',110000) ;  
```  
  
#### <a name="b-disabling-and-re-enabling-a-trigger"></a>Б. Отключение и повторное включение триггера  
 В следующем примере показывается использование параметра `DISABLE TRIGGER` инструкции `ALTER TABLE` для отключения триггера и обеспечения возможности вставки, которая в обычных условиях нарушает триггер. Затем инструкция `ENABLE TRIGGER` используется для повторного включения триггера.  
  
```  
CREATE TABLE dbo.trig_example   
(id INT,   
name VARCHAR(12),  
salary MONEY) ;  
GO  
-- Create the trigger.  
CREATE TRIGGER dbo.trig1 ON dbo.trig_example FOR INSERT  
AS  
IF (SELECT COUNT(*) FROM INSERTED  
WHERE salary > 100000) > 0  
BEGIN  
    print 'TRIG1 Error: you attempted to insert a salary > $100,000'  
    ROLLBACK TRANSACTION  
END ;  
GO  
-- Try an insert that violates the trigger.  
INSERT INTO dbo.trig_example VALUES (1,'Pat Smith',100001) ;  
GO  
-- Disable the trigger.  
ALTER TABLE dbo.trig_example DISABLE TRIGGER trig1 ;  
GO  
-- Try an insert that would typically violate the trigger.  
INSERT INTO dbo.trig_example VALUES (2,'Chuck Jones',100001) ;  
GO  
-- Re-enable the trigger.  
ALTER TABLE dbo.trig_example ENABLE TRIGGER trig1 ;  
GO  
-- Try an insert that violates the trigger.  
INSERT INTO dbo.trig_example VALUES (3,'Mary Booth',100001) ;  
GO  
```  
 
  
### <a name="online-operations"></a>Операции в сети  
  
#### <a name="a-online-index-rebuild-using-low-priority-wait-options"></a>A. Перестроение индекса в режиме «в сети» с помощью параметра «ожидание низких приоритетов».  
 В следующем примере показано, как выполнить перестроение индекса в режиме «в сети», указав параметр «ожидание низких приоритетов».  
  
**Применяется к**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] и [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].  
  
```  
ALTER TABLE T1   
REBUILD WITH   
(  
    PAD_INDEX = ON,  
    ONLINE = ON ( WAIT_AT_LOW_PRIORITY ( MAX_DURATION = 4 MINUTES, 
                                         ABORT_AFTER_WAIT = BLOCKERS ) )  
)  
;  
```  
  
#### <a name="b-online-alter-column"></a>Б. Изменение столбца в режиме «в сети»  
 В следующем примере показано, как выполняется операция изменения столбца с параметром ONLINE.  
  
**Применяется к**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] и [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].  
  
```  
CREATE TABLE dbo.doc_exy (column_a INT ) ;  
GO  
INSERT INTO dbo.doc_exy (column_a) VALUES (10) ;  
GO  
ALTER TABLE dbo.doc_exy   
    ALTER COLUMN column_a DECIMAL (5, 2) WITH (ONLINE = ON);  
GO  
sp_help doc_exy;  
DROP TABLE dbo.doc_exy ;  
GO  
```  
  
##  <a name="system_versioning"></a>Система управления версиями  
 Следующие четыре примера помогут ознакомиться с синтаксис для использования системы управления версиями. Для получения дополнительной помощи см [Приступая к работе с Темпоральными таблицами с системным управлением версиями](../../relational-databases/tables/getting-started-with-system-versioned-temporal-tables.md).  
  
**Применяется к**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] и [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].  
  
### <a name="a-add-system-versioning-to-existing-tables"></a>A. Добавление к существующим таблицам системы управления версиями  
 В следующем примере показано добавление системы управления версиями в существующую таблицу и создайте таблицу журнала в будущем. В этом примере предполагается наличие существующей таблицы называется `InsurancePolicy` с определен первичный ключ. В этом примере заполняются только что созданный столбцы периода для системы управления версиями, используйте значения по умолчанию для времени начала и окончания, поскольку эти значения не может иметь значение null. В этом примере предложение HIDDEN без влияния на существующие приложения, взаимодействие с текущей таблицы.  Она также использует HISTORY_RETENTION_PERIOD, доступный на [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)] только. 
  
```  
--Alter non-temporal table to define periods for system versioning  
ALTER TABLE InsurancePolicy  
ADD PERIOD FOR SYSTEM_TIME (SysStartTime, SysEndTime),   
SysStartTime datetime2 GENERATED ALWAYS AS ROW START HIDDEN NOT NULL 
    DEFAULT GETUTCDATE(),   
SysEndTime datetime2 GENERATED ALWAYS AS ROW END HIDDEN NOT NULL 
    DEFAULT CONVERT(DATETIME2, '9999-12-31 23:59:59.99999999');  
--Enable system versioning with 1 year retention for historical data
ALTER TABLE InsurancePolicy 
SET (SYSTEM_VERSIONING = ON (HISTORY_RETENTION_PERIOD = 1 YEAR));  
```  
  
### <a name="b-migrate-an-existing-solution-to-use-system-versioning"></a>Б. Перенос существующего решения для использования системы управления версиями  
 Приведенный ниже показано, как для переноса системы управления версиями из решения, использующего триггеры для имитации темпоральной поддержкой. Пример предполагает, что имеется существующего решения, использующего `ProjectTaskCurrent` таблицы и `ProjectTaskHistory` столбцы Дата изменения и дату последнего изменения таблицы для его существующего решения, который используется для его периодов, что эти столбцы периодов не используют тип данных datetime2 и что `ProjectTaskCurrent` таблица имеет первичный ключ.  
  
```  
-- Drop existing trigger  
DROP TRIGGER ProjectTaskCurrent_Trigger;  
-- Adjust the schema for current and history table  
-- Change data types for existing period columns  
ALTER TABLE ProjectTaskCurrent ALTER COLUMN [Changed Date] datetime2 NOT NULL;  
ALTER TABLE ProjectTaskCurrent ALTER COLUMN [Revised Date] datetime2 NOT NULL;  
  
ALTER TABLE ProjectTaskHistory ALTER COLUMN [Changed Date] datetime2 NOT NULL;  
ALTER TABLE ProjectTaskHistory ALTER COLUMN [Revised Date] datetime2 NOT NULL;  
  
-- Add SYSTEM_TIME period and set system versioning with linking two existing tables  
-- (a certain set of data checks happen in the background)  
ALTER TABLE ProjectTaskCurrent  
ADD PERIOD FOR SYSTEM_TIME ([Changed Date], [Revised Date])  
  
ALTER TABLE ProjectTaskCurrent  
SET (SYSTEM_VERSIONING = ON (HISTORY_TABLE = dbo.ProjectTaskHistory, DATA_CONSISTENCY_CHECK = ON))  
```  
  
### <a name="c-disabling-and-re-enabling-system-versioning-to-change-table-schema"></a>В. Отключение и повторное включение системы управления версиями для изменения схемы таблицы  
 В этом примере показано, как отключить систему управления версиями на `Department` таблицы, добавьте столбец и повторное включение системы управления версиями. Отключение системы управления версиями требуется, чтобы изменить схему таблицы. Выполните следующие действия в рамках транзакции для предотвращения обновлений к обеим таблицам во время обновления схемы таблицы, что позволяет администратору базы данных для пропуска проверки согласованности данных проверяет при повторном включении системы управления версиями и получить производительности преимуществ. Обратите внимание, что задач, таких как создание статистики, переключение секций или применения сжатия для одной или обеих таблиц не требуется отключение системы управления версиями.  
  
```  
BEGIN TRAN  
/* Takes schema lock on both tables */  
ALTER TABLE Department  
    SET (SYSTEM_VERSIONING = OFF);  
/* expand table schema for temporal table */  
ALTER TABLE Department  
     ADD Col5 int NOT NULL DEFAULT 0;  
/* Expand table schema for history table */  
ALTER TABLE DepartmentHistory  
    ADD Col5 int NOT NULL DEFAULT 0;  
/* Re-establish versioning again  */
ALTER TABLE Department  
    SET (SYSTEM_VERSIONING = ON (HISTORY_TABLE=dbo.DepartmentHistory, 
                                 DATA_CONSISTENCY_CHECK = OFF));  
COMMIT   
```  
  
### <a name="d-removing-system-versioning"></a>Г. Удаление системы управления версиями  
 В этом примере показано, как полностью удалить системы управления версиями из таблица Department и drop `DepartmentHistory` таблицы. При необходимости можно также удалить столбцы периода используются системой для записи сведений о системе управления версиями. Обратите внимание, что либо не удалось удалить `Department` или `DepartmentHistory` таблицы при включенной системе управления версиями.  
  
```  
ALTER TABLE Department  
    SET (SYSTEM_VERSIONING = OFF);  
ALTER TABLE Department  
DROP PEROD FOR SYSTEM_TIME;  
DROP TABLE DepartmentHistory;  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] и[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 В следующих примерах A через C используется в таблице FactResellerSales в [!INCLUDE[ssawPDW](../../includes/ssawpdw-md.md)] базы данных.  
  
### <a name="e-determining-if-a-table-is-partitioned"></a>Д. Определение секционирования таблицы  
 Следующий запрос возвращает одну или несколько строк, если таблица `FactResellerSales` секционирована. Если таблица не секционирована, не возвращается ни одна строка.  
  
```  
SELECT * FROM sys.partitions AS p  
JOIN sys.tables AS t  
    ON  p.object_id = t.object_id  
WHERE p.partition_id IS NOT NULL  
    AND t.name = 'FactResellerSales';  
```  
  
### <a name="f-determining-boundary-values-for-a-partitioned-table"></a>Е. Определение граничных значений для секционированной таблицы  
 Следующий запрос возвращает граничные значения для каждой секции в таблице `FactResellerSales` .  
  
```  
SELECT t.name AS TableName, i.name AS IndexName, p.partition_number, 
    p.partition_id, i.data_space_id, f.function_id, f.type_desc, 
    r.boundary_id, r.value AS BoundaryValue   
FROM sys.tables AS t  
JOIN sys.indexes AS i  
    ON t.object_id = i.object_id  
JOIN sys.partitions AS p  
    ON i.object_id = p.object_id AND i.index_id = p.index_id   
JOIN  sys.partition_schemes AS s   
    ON i.data_space_id = s.data_space_id  
JOIN sys.partition_functions AS f   
    ON s.function_id = f.function_id  
LEFT JOIN sys.partition_range_values AS r   
    ON f.function_id = r.function_id and r.boundary_id = p.partition_number  
WHERE t.name = 'FactResellerSales' AND i.type <= 1  
ORDER BY p.partition_number;  
```  
  
### <a name="g-determining-the-partition-column-for-a-partitioned-table"></a>Ж. Определение столбца секционирования секционированной таблицы  
 Следующий запрос возвращает имя столбца секционирования таблицы. `FactResellerSales`.  
  
```  
SELECT t.object_id AS Object_ID, t.name AS TableName, 
    ic.column_id as PartitioningColumnID, c.name AS PartitioningColumnName   
FROM sys.tables AS t  
JOIN sys.indexes AS i  
    ON t.object_id = i.object_id  
JOIN sys.columns AS c  
    ON t.object_id = c.object_id  
JOIN sys.partition_schemes AS ps  
    ON ps.data_space_id = i.data_space_id  
JOIN sys.index_columns AS ic  
    ON ic.object_id = i.object_id 
    AND ic.index_id = i.index_id AND ic.partition_ordinal > 0  
WHERE t.name = 'FactResellerSales'  
AND i.type <= 1  
AND c.column_id = ic.column_id;  
```  
  
### <a name="h-merging-two-partitions"></a>З. Объединение двух секций  
 Следующий пример выполняет слияние двух секций в таблице.  
  
 `Customer` Таблица имеет следующее определение:  
  
```  
CREATE TABLE Customer (  
    id int NOT NULL,  
    lastName varchar(20),  
    orderCount int,  
    orderDate date)  
WITH   
    ( DISTRIBUTION = HASH(id),  
    PARTITION ( orderCount RANGE LEFT  
    FOR VALUES (1, 5, 10, 25, 50, 100)));  
```  
  
 Следующая команда объединяет границы раздела 10 и 25.  
  
```  
ALTER TABLE Customer MERGE RANGE (10);  
```  
  
 Новые таблицы, является:  
  
```  
CREATE TABLE Customer (  
    id int NOT NULL,  
    lastName varchar(20),  
    orderCount int,  
    orderDate date)  
WITH   
    ( DISTRIBUTION = HASH(id),  
    PARTITION ( orderCount RANGE LEFT  
    FOR VALUES (1, 5, 25, 50, 100)));  
```  
  
### <a name="i-splitting-a-partition"></a>И. Разбиение секции  
 Следующий пример разделяет секции для таблицы.  
  
 `Customer` Таблица содержит следующие DDL:  
  
```  
DROP TABLE Customer;  
  
CREATE TABLE Customer (  
    id int NOT NULL,  
    lastName varchar(20),  
    orderCount int,  
    orderDate date)  
WITH   
    ( DISTRIBUTION = HASH(id),  
    PARTITION ( orderCount RANGE LEFT  
    FOR VALUES (1, 5, 10, 25, 50, 100 )));  
```  
  
 Следующая команда создает новый раздел ограничивается значение 75, от 50 до 100.  
  
```  
ALTER TABLE Customer SPLIT RANGE (75);  
```  
  
 Новые таблицы, является:  
  
```  
CREATE TABLE Customer (  
   id int NOT NULL,  
   lastName varchar(20),  
   orderCount int,  
   orderDate date)  
   WITH DISTRIBUTION = HASH(id),  
   PARTITION ( orderCount (RANGE LEFT  
      FOR VALUES (1, 5, 10, 25, 50, 75, 100 )));  
```  
  
### <a name="j-using-switch-to-move-a-partition-to-a-history-table"></a>К. Перемещение секции в таблицу журнала с помощью КОММУТАТОРА  
 Следующий пример перемещает данные в секции `Orders` таблицы для секции в `OrdersHistory` таблицы.  
  
 `Orders` Таблица содержит следующие DDL:  
  
```  
CREATE TABLE Orders (  
    id INT,  
    city VARCHAR (25),  
    lastUpdateDate DATE,  
    orderDate DATE )  
WITH   
    (DISTRIBUTION = HASH ( id ),  
    PARTITION ( orderDate RANGE RIGHT   
    FOR VALUES ('2004-01-01', '2005-01-01', '2006-01-01', '2007-01-01' )));  
```  
  
 В этом примере `Orders` таблица содержит следующие разделы. Каждая секция содержит данные.  
  
|Секция|Содержит данные?|Границы диапазона|  
|---------------|---------------|--------------------|  
|1|Да|OrderDate < ' 2004-01-01 "|  
|2|Да|"2004-01-01" < = OrderDate < ' 2005-01-01 "|  
|3|Да|"2005-01-01" < = OrderDate < ' 2006-01-01 "|  
|4|Да|"2006-01-01" < = OrderDate < ' 2007-01-01 "|  
|5|Да|' 2007-01-01 "< = OrderDate|  
  
-   Секция 1 (содержит данные): OrderDate < ' 2004-01-01 "  
-   Секции 2 (содержит данные): "2004-01-01" < = OrderDate < ' 2005-01-01 "  
-   Раздел 3 (содержит данные): "2005-01-01" < = OrderDate < ' 2006-01-01 "  
-   Раздел 4 (содержит данные): "2006-01-01" < = OrderDate < ' 2007-01-01 "  
-   Секция 5 (содержит данные): "2007-01-01" < = OrderDate  
  
`OrdersHistory` Таблица имеет следующие DDL, которая имеет одинаковые столбцы и имена столбцов как `Orders` таблицы. Оба этих параметра соответствуют хэш распределенных `id` столбца.  
  
```  
CREATE TABLE OrdersHistory (  
   id INT,  
   city VARCHAR (25),  
   lastUpdateDate DATE,  
   orderDate DATE )  
WITH   
    (DISTRIBUTION = HASH ( id ),  
    PARTITION ( orderDate RANGE RIGHT   
    FOR VALUES ( '2004-01-01' )));  
```  
  
 Несмотря на то, что столбцы и имена столбцов должны быть одинаковыми, границы секций не обязательно должны быть одинаковыми. В этом примере `OrdersHistory` таблица имеет следующие два раздела и пусты обе секции:  
  
-   Секция 1 (без данных): OrderDate < ' 2004-01-01 "  
-   Секции 2 (пусто): "2004-01-01" < = OrderDate  
  
Для предыдущих двух таблиц, следующая команда перемещает все строки с `OrderDate < '2004-01-01'` из `Orders` таблицу `OrdersHistory` таблицы.  
  
```  
ALTER TABLE Orders SWITCH PARTITION 1 TO OrdersHistory PARTITION 1;  
```  
  
 В результате первой секции в `Orders` является пустым и первую секцию в `OrdersHistory` содержит данные. Теперь таблицы отображаются следующим образом:  
  
 `Orders`Таблица  
  
-   Секция 1 (пусто): OrderDate < ' 2004-01-01 "  
-   Секции 2 (содержит данные): "2004-01-01" < = OrderDate < ' 2005-01-01 "  
-   Раздел 3 (содержит данные): "2005-01-01" < = OrderDate < ' 2006-01-01 "  
-   Раздел 4 (содержит данные): "2006-01-01" < = OrderDate < ' 2007-01-01 "  
-   Секция 5 (содержит данные): "2007-01-01" < = OrderDate  
  
 `OrdersHistory`Таблица  
  
-   Секция 1 (содержит данные): OrderDate < ' 2004-01-01 "  
-   Секции 2 (пусто): "2004-01-01" < = OrderDate  
  
Чтобы очистить `Orders` таблицы, можно удалить пустой секции, слияние секций 1 и 2 следующим образом:  
  
```  
ALTER TABLE Orders MERGE RANGE ('2004-01-01');  
```  
  
 После слияния `Orders` таблица содержит следующие разделы:  
  
 `Orders`Таблица  
  
-   Секция 1 (содержит данные): OrderDate < ' 2005-01-01 "  
-   Секции 2 (содержит данные): "2005-01-01" < = OrderDate < ' 2006-01-01 "  
-   Раздел 3 (содержит данные): "2006-01-01" < = OrderDate < ' 2007-01-01 "  
-   Раздел 4 (содержит данные): "2007-01-01" < = OrderDate  
  
Предположим, что передает следующего года и вы готовы к архивации 2005 года. Можно выделить для 2005 года в пустую секцию `OrdersHistory` таблицу, разделив пустую секцию следующим образом:  
  
```  
ALTER TABLE OrdersHistory SPLIT RANGE ('2005-01-01');  
```  
  
 После разбиения `OrdersHistory` таблица содержит следующие разделы:  
  
 `OrdersHistory`Таблица  
  
-   Секция 1 (содержит данные): OrderDate < ' 2004-01-01 "  
-   Секции 2 (пусто): "2004-01-01" < "2005-01-01"  
-   Раздел 3 (пусто): "2005-01-01" < = OrderDate  
  
## <a name="see-also"></a>См. также:  
 [sys.tables (Transact-SQL)](../../relational-databases/system-catalog-views/sys-tables-transact-sql.md)   
 [sp_rename (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-rename-transact-sql.md)   
 [CREATE TABLE (Transact-SQL)](../../t-sql/statements/create-table-transact-sql.md)   
 [DROP TABLE &#40; Transact-SQL &#41;](../../t-sql/statements/drop-table-transact-sql.md)   
 [sp_help (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-help-transact-sql.md)   
 [ALTER PARTITION SCHEME &#40; Transact-SQL &#41;](../../t-sql/statements/alter-partition-scheme-transact-sql.md)   
 [ALTER PARTITION FUNCTION &#40; Transact-SQL &#41;](../../t-sql/statements/alter-partition-function-transact-sql.md)   
 [EVENTDATA (Transact-SQL)](../../t-sql/functions/eventdata-transact-sql.md)  
  
  


