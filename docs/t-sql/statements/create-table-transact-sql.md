---
title: "Создание таблицы (Transact-SQL) | Документы Microsoft"
ms.custom:
- SQL2016_New_Updated
ms.date: 08/10/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- FILESTREAM_TSQL
- TABLE
- CREATE_TABLE_TSQL
- CREATE TABLE
- FILESTREAM
- TABLE_TSQL
- FILESTREAM_ON
- FILESTREAM_ON_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- CHECK constraints
- global temporary tables [SQL Server]
- local temporary tables [SQL Server]
- size [SQL Server], tables
- UNIQUE constraints [SQL Server], creating
- constraints [SQL Server], columns
- maximum number of indexes per table
- number of tables per database
- number of indexes per table
- table creation [SQL Server], CREATE TABLE
- temporary tables [SQL Server], creating
- table size [SQL Server]
- nullability [SQL Server]
- partitioned tables [SQL Server], creating
- DEFAULT definition
- null values [SQL Server], columns
- number of rows per table
- maximum number of columns per table
- FOREIGN KEY constraints, creating
- PRIMARY KEY constraints
- number of bytes per row
- CREATE TABLE statement
- number of columns per table
- maximum number of bytes per row
ms.assetid: 1e068443-b9ea-486a-804f-ce7b6e048e8b
caps.latest.revision: 256
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 0978041b1c2683f6af3f6c531ddc10edc6b9bcbf
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="create-table-transact-sql"></a>Инструкция CREATE TABLE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Создает новую таблицу в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].  
  
> [!NOTE]   
>  Для [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] синтаксиса, в разделе [CREATE TABLE (хранилище данных SQL Azure)](../../t-sql/statements/create-table-azure-sql-data-warehouse.md).
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
--Simple CREATE TABLE Syntax (common if not using options)  
CREATE TABLE   
    [ database_name . [ schema_name ] . | schema_name . ] table_name   
    ( { <column_definition> } [ ,...n ] )   
[ ; ]  
```  
  
## <a name="syntax"></a>Синтаксис  
  
```  
--Disk-Based CREATE TABLE Syntax  
CREATE TABLE   
    [ database_name . [ schema_name ] . | schema_name . ] table_name   
    [ AS FileTable ]  
    ( {   <column_definition>   
        | <computed_column_definition>    
        | <column_set_definition>   
        | [ <table_constraint> ]   
        | [ <table_index> ] }  
          [ ,...n ]    
          [ PERIOD FOR SYSTEM_TIME ( system_start_time_column_name   
             , system_end_time_column_name ) ]  
      )  
    [ ON { partition_scheme_name ( partition_column_name )   
           | filegroup   
           | "default" } ]   
    [ TEXTIMAGE_ON { filegroup | "default" } ]   
    [ FILESTREAM_ON { partition_scheme_name   
           | filegroup   
           | "default" } ]  
    [ WITH ( <table_option> [ ,...n ] ) ]  
[ ; ]  
  
<column_definition> ::=  
column_name <data_type>  
    [ FILESTREAM ]  
    [ COLLATE collation_name ]   
    [ SPARSE ]  
    [ MASKED WITH ( FUNCTION = ' mask_function ') ]  
    [ CONSTRAINT constraint_name [ DEFAULT constant_expression ] ]   
    [ IDENTITY [ ( seed,increment ) ]  
    [ NOT FOR REPLICATION ]   
    [ GENERATED ALWAYS AS ROW { START | END } [ HIDDEN ] ]   
    [ NULL | NOT NULL ]  
    [ ROWGUIDCOL ]  
    [ ENCRYPTED WITH   
        ( COLUMN_ENCRYPTION_KEY = key_name ,  
          ENCRYPTION_TYPE = { DETERMINISTIC | RANDOMIZED } ,   
          ALGORITHM = 'AEAD_AES_256_CBC_HMAC_SHA_256'  
        ) ]  
    [ <column_constraint> [ ...n ] ]   
    [ <column_index> ]  
  
<data type> ::=   
[ type_schema_name . ] type_name   
    [ ( precision [ , scale ] | max |   
        [ { CONTENT | DOCUMENT } ] xml_schema_collection ) ]   
  
<column_constraint> ::=   
[ CONSTRAINT constraint_name ]   
{     { PRIMARY KEY | UNIQUE }   
        [ CLUSTERED | NONCLUSTERED ]   
        [   
            WITH FILLFACTOR = fillfactor    
          | WITH ( < index_option > [ , ...n ] )   
        ]   
        [ ON { partition_scheme_name ( partition_column_name )   
            | filegroup | "default" } ]  
  
  | [ FOREIGN KEY ]   
        REFERENCES [ schema_name . ] referenced_table_name [ ( ref_column ) ]   
        [ ON DELETE { NO ACTION | CASCADE | SET NULL | SET DEFAULT } ]   
        [ ON UPDATE { NO ACTION | CASCADE | SET NULL | SET DEFAULT } ]   
        [ NOT FOR REPLICATION ]   
  
  | CHECK [ NOT FOR REPLICATION ] ( logical_expression )   
}   
  
<column_index> ::=   
 INDEX index_name [ CLUSTERED | NONCLUSTERED ]  
    [ WITH ( <index_option> [ ,... n ] ) ]  
    [ ON { partition_scheme_name (column_name )   
         | filegroup_name  
         | default   
         }  
    ]   
    [ FILESTREAM_ON { filestream_filegroup_name | partition_scheme_name | "NULL" } ]  
  
<computed_column_definition> ::=  
column_name AS computed_column_expression   
[ PERSISTED [ NOT NULL ] ]  
[   
    [ CONSTRAINT constraint_name ]  
    { PRIMARY KEY | UNIQUE }  
        [ CLUSTERED | NONCLUSTERED ]  
        [   
            WITH FILLFACTOR = fillfactor   
          | WITH ( <index_option> [ , ...n ] )  
        ]  
        [ ON { partition_scheme_name ( partition_column_name )   
        | filegroup | "default" } ]  
  
    | [ FOREIGN KEY ]   
        REFERENCES referenced_table_name [ ( ref_column ) ]   
        [ ON DELETE { NO ACTION | CASCADE } ]   
        [ ON UPDATE { NO ACTION } ]   
        [ NOT FOR REPLICATION ]   
  
    | CHECK [ NOT FOR REPLICATION ] ( logical_expression )   
]   
  
<column_set_definition> ::=  
column_set_name XML COLUMN_SET FOR ALL_SPARSE_COLUMNS  
  
< table_constraint > ::=  
[ CONSTRAINT constraint_name ]   
{   
    { PRIMARY KEY | UNIQUE }   
        [ CLUSTERED | NONCLUSTERED ]   
        (column [ ASC | DESC ] [ ,...n ] )   
        [   
            WITH FILLFACTOR = fillfactor   
           |WITH ( <index_option> [ , ...n ] )   
        ]  
        [ ON { partition_scheme_name (partition_column_name)  
            | filegroup | "default" } ]   
    | FOREIGN KEY   
        ( column [ ,...n ] )   
        REFERENCES referenced_table_name [ ( ref_column [ ,...n ] ) ]   
        [ ON DELETE { NO ACTION | CASCADE | SET NULL | SET DEFAULT } ]   
        [ ON UPDATE { NO ACTION | CASCADE | SET NULL | SET DEFAULT } ]   
        [ NOT FOR REPLICATION ]   
    | CHECK [ NOT FOR REPLICATION ] ( logical_expression )  
 

  
< table_index > ::=   
{  
    {  
      INDEX index_name [ CLUSTERED | NONCLUSTERED ]   
         (column_name [ ASC | DESC ] [ ,... n ] )   
    | INDEX index_name CLUSTERED COLUMNSTORE  
    | INDEX index_name [ NONCLUSTERED ] COLUMNSTORE (column_name [ ,... n ] )  
    }  
    [ WITH ( <index_option> [ ,... n ] ) ]   
    [ ON { partition_scheme_name (column_name )   
         | filegroup_name  
         | default   
         }  
    ]   
    [ FILESTREAM_ON { filestream_filegroup_name | partition_scheme_name | "NULL" } ]  
  
}   


<table_option> ::=  
{  
    [DATA_COMPRESSION = { NONE | ROW | PAGE }  
      [ ON PARTITIONS ( { <partition_number_expression> | <range> }   
      [ , ...n ] ) ]]  
    [ FILETABLE_DIRECTORY = <directory_name> ]   
    [ FILETABLE_COLLATE_FILENAME = { <collation_name> | database_default } ]  
    [ FILETABLE_PRIMARY_KEY_CONSTRAINT_NAME = <constraint_name> ]  
    [ FILETABLE_STREAMID_UNIQUE_CONSTRAINT_NAME = <constraint_name> ]  
    [ FILETABLE_FULLPATH_UNIQUE_CONSTRAINT_NAME = <constraint_name> ]  
    [ SYSTEM_VERSIONING = ON [ ( HISTORY_TABLE = schema_name . history_table_name  
        [, DATA_CONSISTENCY_CHECK = { ON | OFF } ] ) ] ]  
    [ REMOTE_DATA_ARCHIVE =   
      {   
          ON [ ( <table_stretch_options> [,...n] ) ]  
        | OFF ( MIGRATION_STATE = PAUSED )   
      }   
    ]  
}  
  
<table_stretch_options> ::=  
{  
     [ FILTER_PREDICATE = { null | table_predicate_function } , ]  
       MIGRATION_STATE = { OUTBOUND | INBOUND | PAUSED }  
 }  
  
<index_option> ::=  
{   
    PAD_INDEX = { ON | OFF }   
  | FILLFACTOR = fillfactor   
  | IGNORE_DUP_KEY = { ON | OFF }   
  | STATISTICS_NORECOMPUTE = { ON | OFF }   
  | ALLOW_ROW_LOCKS = { ON | OFF}   
  | ALLOW_PAGE_LOCKS ={ ON | OFF}   
  | COMPRESSION_DELAY= {0 | delay [Minutes]}  
  | DATA_COMPRESSION = { NONE | ROW | PAGE | COLUMNSTORE | COLUMNSTORE_ARCHIVE }  
       [ ON PARTITIONS ( { <partition_number_expression> | <range> }   
       [ , ...n ] ) ]  
}  
<range> ::=   
<partition_number_expression> TO <partition_number_expression>  
```  
  
```  
  
      --Memory optimized CREATE TABLE Syntax  
CREATE TABLE  
    [database_name . [schema_name ] . | schema_name . ] table_name  
    ( { <column_definition>  
    | [ <table_constraint> ] [ ,... n ]  
    | [ <table_index> ]  
      [ ,... n ] }   
      [ PERIOD FOR SYSTEM_TIME ( system_start_time_column_name   
        , system_end_time_column_name ) ]  
)  
    [ WITH ( <table_option> [ ,... n ] ) ]  
 [ ; ]  
  
<column_definition> ::=  
column_name <data_type>  
    [ COLLATE collation_name ]  
    [ GENERATED ALWAYS AS ROW { START | END } [ HIDDEN ] ]   
    [ NULL | NOT NULL ]  
[  
    [ CONSTRAINT constraint_name ] DEFAULT memory_optimized_constant_expression ]  
    | [ IDENTITY [ ( 1, 1 ) ]  
]  
    [ <column_constraint> ]  
    [ <column_index> ]  
  
<data type> ::=  
 [type_schema_name . ] type_name [ (precision [ , scale ]) ]  
  
<column_constraint> ::=  
 [ CONSTRAINT constraint_name ]  
{   
  { PRIMARY KEY | UNIQUE }    
      {   NONCLUSTERED   
        | NONCLUSTERED HASH WITH (BUCKET_COUNT = bucket_count)   
      }   
  | [ FOREIGN KEY ]   
        REFERENCES [ schema_name . ] referenced_table_name [ ( ref_column ) ]   
  | CHECK ( logical_expression )   
}  
  
< table_constraint > ::=  
 [ CONSTRAINT constraint_name ]  
{    
   { PRIMARY KEY | UNIQUE }  
     {   
       NONCLUSTERED (column [ ASC | DESC ] [ ,... n ])  
       | NONCLUSTERED HASH (column [ ,... n ] ) WITH ( BUCKET_COUNT = bucket_count )   
                    }   
    | FOREIGN KEY   
        ( column [ ,...n ] )   
        REFERENCES referenced_table_name [ ( ref_column [ ,...n ] ) ]   
    | CHECK ( logical_expression )   
}  
  
<column_index> ::=  
  INDEX index_name  
{ [ NONCLUSTERED ] | [ NONCLUSTERED ] HASH WITH (BUCKET_COUNT = bucket_count)  }  
  
<table_index> ::=  
  INDEX index_name  
{   [ NONCLUSTERED ] HASH (column [ ,... n ] ) WITH (BUCKET_COUNT = bucket_count)   
  | [ NONCLUSTERED ] (column [ ASC | DESC ] [ ,... n ] )   
      [ ON filegroup_name | default ]  
  | CLUSTERED COLUMNSTORE [WITH ( COMPRESSION_DELAY = {0 | delay [Minutes]})]  
      [ ON filegroup_name | default ]  
  
}  
  
<table_option> ::=  
{  
    MEMORY_OPTIMIZED = ON   
  | DURABILITY = {SCHEMA_ONLY | SCHEMA_AND_DATA}  
  | SYSTEM_VERSIONING = ON [ ( HISTORY_TABLE = schema_name . history_table_name  
        [, DATA_CONSISTENCY_CHECK = { ON | OFF } ] ) ]   
  
}  
```  
  
## <a name="arguments"></a>Аргументы  
 *database_name*  
 Имя базы данных, в которой создается таблица. *database_name* необходимо указать имя существующей базы данных. Если не указан, *имя_базы_данных* значения по умолчанию для текущей базы данных. Имя входа для текущего соединения должны быть связаны с Идентификатором пользователя, существующего в базы данных, указанной *имя_базы_данных*, и этот пользователь должен обладать разрешениями CREATE TABLE.  
  
 *schema_name*  
 Имя схемы, которой принадлежит новая таблица.  
  
 *имя_таблицы*  
 Имя новой таблицы. Имена таблиц должны соответствовать правилам для [идентификаторы](../../relational-databases/databases/database-identifiers.md). *имя_таблицы* не может превышать 128 символов, за исключением имен локальных временных таблиц (имена с префиксом знак номера (#)), не должна превышать 116 символов.  
  
 AS FileTable 
 
**Область применения**: начиная с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. 
 
 Создает новую таблицу FileTable. Нет необходимости указывать столбцы, так как таблица FileTable имеет фиксированное схему. Дополнительные сведения о таблицах Filetable см. в разделе [FileTables &#40; SQL Server &#41; ](../../relational-databases/blob/filetables-sql-server.md).  
  
 *column_name*  
 *computed_column_expression*  
 Выражение, определяющее значение вычисляемого столбца. Вычисляемый столбец представляет собой виртуальный столбец, физически не хранящийся в таблице, если для него не установлен признак PERSISTED. Значение столбца вычисляется на основе выражения, использующего другие столбцы той же таблицы. Например, вычисляемый столбец может иметь определение: **стоимость** AS **цены** \* **qty**. Выражение может быть именем невычисляемого столбца, константой, функцией, переменной или любой их комбинацией, соединенной одним или несколькими операторами. Выражение не может быть вложенным запросом или содержать псевдонимы типов данных.  
  
 Вычисляемые столбцы могут использоваться в списках выбора, предложениях WHERE, ORDER BY и в любых других местах, в которых могут использоваться обычные выражения, за исключением следующих случаев.  
  
-   Для использования в ограничениях FOREIGN KEY или CHECK вычисляемые столбцы должны быть помечены как PERSISTED.  
  
-   Вычисляемый столбец может использоваться в качестве ключевого столбца в индексе или в качестве компонента какого-либо ограничения PRIMARY KEY или UNIQUE, если значение этого вычисляемого столбца определено детерминистическим выражением, а тип данных результата разрешен в столбцах индекса.  
  
     Например, если таблица содержит целочисленные столбцы **** и **b**, вычисляемый столбец **a + b** может быть индексирован, но вычисляемый столбец **a + DATEPART (dd, GETDATE())**  не может быть индексирован, так как его значение может изменяться при последующих вызовах.  
  
-   Вычисляемый столбец не может быть целевым столбцом инструкций INSERT или UPDATE.  
  
> [!NOTE]  
>  Каждая строка таблицы может содержать различные значения столбцов, задействованных в вычисляемом столбце; таким образом, значение вычисляемого столбца не будет одним и тем же в каждой строке.  
  
 Компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] автоматически определяет для вычисляемых столбцов допустимость значений NULL на основе использованных выражений. Считается, что результат большинства выражений допускает значение NULL, даже если используются только столбцы, для которых значение NULL запрещено, так как при возможном переполнении или потере точности может получаться значение NULL. Используйте функцию COLUMNPROPERTY со **AllowsNull** свойство вычисляемого столбца таблицы принимать значение NULL. Выражение, которое допускает значение NULL может быть преобразован в не допускающее классификацию, указав ISNULL с *check_expression* константа, где константа представляет собой ненулевое значение, заменяющее любое значение NULL. Для вычисляемых столбцов, основанных на выражениях, содержащих определяемые пользователем типы среды CLR, требуется разрешение REFERENCES на тип.  
  
 PERSISTED  
 Указывает, что компонент [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] будет физически хранить вычисляемые значения в таблице и обновлять их при изменении любого столбца, от которого зависит вычисляемый столбец. Указание PERSISTED для вычисляемого столбца позволяет создать индекс по вычисляемому столбцу, который будет детерминистическим, но неточным. Дополнительные сведения см. в разделе [Indexes on Computed Columns](../../relational-databases/indexes/indexes-on-computed-columns.md). Все вычисляемые столбцы, используемые в столбцах секционирования секционированной таблицы, должны быть явно помечены как PERSISTED. *computed_column_expression* должно быть детерминированным, если указан параметр PERSISTED.  
  
 ON { *partition_scheme* | *файловой группы* | **»**по умолчанию**»** }  

 Указывает схему секционирования или файловую группу, в которой хранится таблица. Если *partition_scheme* указан, таблица будет разбита на секции хранятся на один набор секционированной таблицы или несколько файловых групп, определенных в *partition_scheme*. Если *файловой группы* указан, таблица хранится в именованной файловой группе. Это должна быть существующая файловая группа в базе данных. Если **»**по умолчанию**»** указан, или если ON не определен вообще, таблица сохраняется в файловой группе по умолчанию. Механизм хранения таблицы, указанный в инструкции CREATE TABLE, изменить в дальнейшем невозможно.  
  
 ON {*partition_scheme* | *файловой группы* | **»**по умолчанию**»**} также могут быть указаны в первичный ключ или ограничения уникальности. С помощью этих ограничений создаются индексы. Если *файловой группы* указан, индекс сохраняется в именованной файловой группе. Если **»**по умолчанию**»** указан, или если ON не определен вообще, индекс сохраняется в той же файловой группе, что и таблица. Если ограничение PRIMARY KEY или UNIQUE создает кластеризованный индекс, страницы данных таблицы сохраняются в той же файловой группе, что и индекс. Если указан параметр CLUSTERED или ограничение создает кластеризованный индекс, а также *partition_scheme* указан, отличается от *partition_scheme* или *файловойгруппы* определение таблицы, или наоборот, будет принята только определение ограничения, а остальные будут проигнорированы.  
  
> [!NOTE]  
>  В этом контексте default не является ключевым словом. Он представляет собой идентификатор файловой группы по умолчанию и должен иметь разделители, как в выражениях ON **»**по умолчанию**»** или ON **[**по умолчанию**]**. Если **»**по умолчанию**»** указан, параметр QUOTED_IDENTIFIER должен иметь значение ON для текущего сеанса. Это параметр по умолчанию. Дополнительные сведения см. в разделе [SET QUOTED_IDENTIFIER (Transact-SQL)](../../t-sql/statements/set-quoted-identifier-transact-sql.md).  
  
> [!NOTE]  
>  После создания секционированной таблицы рассмотрите возможность присвоить параметру LOCK_ESCALATION для таблицы значения AUTO. При этом можно усовершенствовать параллелизм, разрешив укрупнение блокировок до уровня секции (HoBT) вместо таблицы. Дополнительные сведения см. в разделе [ALTER TABLE (Transact-SQL)](../../t-sql/statements/alter-table-transact-sql.md).  
  
 Параметр TEXTIMAGE_ON { *файловой группы*| **»**по умолчанию**»** }  
 Указывает, что **текст**, **ntext**, **изображения**, **xml**, **varchar(max)**,  **nvarchar(max)**, **varbinary(max)**, и столбцов определяемого пользователем типа данных CLR (включая geometry и geography) хранятся в указанной файловой группе.  
  
 Параметр TEXTIMAGE_ON недопустим, если в таблице нет столбцов с большими значениями. Нельзя указывать параметр TEXTIMAGE_ON, если *partition_scheme* указано. Если **»**по умолчанию**»** указано, или параметр TEXTIMAGE_ON не определен вообще, столбцы больших значений хранятся в файловой группе по умолчанию. Способ хранения любых данных столбцов с большими значениями, определенный инструкцией CREATE TABLE, изменить в дальнейшем невозможно.  

> [!NOTE]  
> Varchar(max), nvarchar(max), varbinary(max), xml и большие значения UDT хранятся непосредственно в строке данных, до предельного размера в 8000 байт и пока значение умещается записи. Если значение не умещается в записи, сортируется ли указатель в строке, а остальные хранится вне строки в пространстве для хранения LOB. имеет значение по умолчанию 0.
Параметр TEXTIMAGE_ON изменяется только расположение «LOB дискового пространства», но не влияет на, когда данные хранятся в строке. Используйте большой value types out of row, параметр sp_tableoption для хранения всего значения больших ОБЪЕКТОВ вне строки. 


> [!NOTE]  
>  В этом контексте default не является ключевым словом. Он представляет собой идентификатор файловой группы по умолчанию и должен иметь разделители, как в выражениях TEXTIMAGE_ON **»**по умолчанию**»** или TEXTIMAGE_ON **[**по умолчанию**]**. Если **»**по умолчанию**»** указан, параметр QUOTED_IDENTIFIER должен иметь значение ON для текущего сеанса. Это параметр по умолчанию. Дополнительные сведения см. в разделе [SET QUOTED_IDENTIFIER (Transact-SQL)](../../t-sql/statements/set-quoted-identifier-transact-sql.md).  
  
 FILESTREAM_ON { *partition_scheme_name* | файловая группа | **»**по умолчанию**»** } **применяется к**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. 
 
 Задает файловую группу для данных FILESTREAM.  
  
 Если таблица содержит данные FILESTREAM и является секционированной, необходимо включить предложение FILESTREAM_ON и указать схему секционирования файловых групп файлового потока. В этой схеме секционирования должны использоваться те же функции и столбцы секционирования, что и в схеме секционирования для таблицы; в противном случае возникает ошибка.  
  
 Если таблица не секционирована, столбец FILESTREAM не может быть секционирован. Данные FILESTREAM для таблицы должны храниться в отдельной файловой группе. Эта файловая группа указывается в предложении FILESTREAM_ON.  
  
 Если таблица не является секционированной и предложение FILESTREAM_ON не указано, используется файловая группа FILESTREAM, для которой задано свойство DEFAULT. При отсутствии файловой группы FILESTREAM возникает ошибка.  
  
-   Как и в случае с предложениями ON и TEXTIMAGE_ON, значение, указанное с помощью инструкции CREATE TABLE для предложения FILESTREAM_ON, не может быть изменено, за исключением следующих ситуаций.  
  
-   Объект [CREATE INDEX](../../t-sql/statements/create-index-transact-sql.md) преобразует кучу в кластеризованный индекс. В этом случае можно указать другую файловую группу FILESTREAM, схему секционирования или значение NULL.  
  
-   Объект [DROP INDEX](../../t-sql/statements/drop-index-transact-sql.md) инструкция преобразует кластеризованный индекс в кучу. В данном случае другую файловую группу FILESTREAM, схему секционирования или **»**по умолчанию**»** можно указать.  
  
 Файловая группа в `FILESTREAM_ON <filegroup>` предложения или каждой файловой группы FILESTREAM, который указан в схеме секционирования, должен иметь один файл, заданный для файловой группы. Этот файл должен быть определен с помощью [CREATE DATABASE](../../t-sql/statements/create-database-sql-server-transact-sql.md) или [инструкции ALTER DATABASE](../../t-sql/statements/alter-database-transact-sql.md) оператор; в противном случае возникает ошибка.  
  
 Связанные разделы о FILESTREAM см. в разделе [большой двоичный объект &#40; Большой двоичный объект &#41; Данные &#40; SQL Server &#41; ](../../relational-databases/blob/binary-large-object-blob-data-sql-server.md).  
  
 [ *type_schema_name***.** ] *type_name*  
 Указывает тип данных столбца и схему, к которой он принадлежит. Дисковые таблицы могут иметь один из следующих типов данных:  
  
-   Системный тип данных.  
  
-   Псевдонимы типа на основе системного типа данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Прежде чем псевдонимы типов данных можно будет использовать в определении таблицы, их нужно создать с помощью инструкции CREATE TYPE. Состояние признака NULL или NOT NULL для псевдонима типа данных может быть переопределено с помощью инструкции CREATE TABLE. Однако его длину изменить нельзя; длина типа данных-псевдонима не определяется инструкцией CREATE TABLE.  
  
-   Определяемый пользователем тип данных CLR. Прежде чем определяемые пользователем типы данных CLR можно будет использовать в определении таблицы, их нужно создать с помощью инструкции CREATE TYPE. Для создания столбца с определяемым пользователем типом данных CLR требуется разрешение REFERENCES на этот тип.  
  
 Если *type_schema_name* не указан, [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] ссылки *type_name* в следующем порядке:  
  
-   системный тип данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)];  
  
-   в установленной по умолчанию для текущего пользователя схеме в текущей базе данных;  
  
-   Схема **dbo** в текущей базе данных.  
  
 Для таблиц, оптимизированных для памяти, в разделе [поддерживаемые типы данных для In-Memory OLTP](../../relational-databases/in-memory-oltp/supported-data-types-for-in-memory-oltp.md) список поддерживаемых систем типов.  
  
 *precision*  
 Точность указанного типа данных. Дополнительные сведения о допустимых значениях точности см. в разделе [точность, масштаб и длина](../../t-sql/data-types/precision-scale-and-length-transact-sql.md).  
  
 *масштаб*  
 Масштаб указанного типа данных. Дополнительные сведения о допустимых значениях масштаба см. в разделе [точность, масштаб и длина](../../t-sql/data-types/precision-scale-and-length-transact-sql.md).  
  
 **max**  
 Применяется только к **varchar**, **nvarchar**, и **varbinary** типы данных для хранения 2 ^ 31 байт символьных и двоичных данных или 2 ^ 30 байт данных в Юникоде.  
  
 CONTENT  
 Указывает, что каждый экземпляр **xml** в тип данных *column_name* может содержать несколько элементов верхнего уровня. CONTENT применим только к **xml** данных типа и может быть указан только в том случае, если *xml_schema_collection* также указан. Если этот параметр не указан, CONTENT принимается в качестве поведения по умолчанию.  
  
 DOCUMENT  
 Указывает, что каждый экземпляр **xml** в тип данных *column_name* может содержать только один элемент верхнего уровня. DOCUMENT применим только к **xml** данных типа и может быть указан только в том случае, если *xml_schema_collection* также указан.  
  
 *xml_schema_collection*  
 Применяется только к **xml** тип данных для сопоставления с типом коллекции XML-схем. Перед вводом **xml** столбца в схеме схемы сначала должна быть создана в базе данных с помощью [CREATE XML SCHEMA COLLECTION](../../t-sql/statements/create-xml-schema-collection-transact-sql.md).  
  
 DEFAULT  
 Указывает значение, присваиваемое столбцу в случае отсутствия явно заданного значения при вставке. Определения DEFAULT могут применяться к любым столбцам, за исключением определенных как **timestamp**, или обладающих свойством IDENTITY. Если для столбца определяемого пользователем типа указано значение по умолчанию, тип должен поддерживать неявное преобразование из *constant_expression* для определяемого пользователем типа. Определения DEFAULT удаляются, когда таблица удаляется из памяти. В качестве значения по умолчанию могут использоваться только константы (например, символьные строки), скалярные функции (системные, определяемые пользователем или функции CLR) или значение NULL. Для сохранения совместимости с более ранними версиями сервера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] значению DEFAULT может быть присвоено имя ограничения.  
  
 *constant_expression*  
 Константа, значение NULL или системная функция, используемая в качестве значения столбца по умолчанию.  
  
 *memory_optimized_constant_expression*  
 Константа, значение NULL или системная функция, используемая в качестве значения столбца по умолчанию. Должно поддерживаться для хранимых процедур, скомпилированных в собственном коде. Дополнительные сведения о встроенных функциях в скомпилированных хранимых процедурах см. в разделе [поддерживаемые функции для собственном коде T-SQL модулей, скомпилированных в](../../relational-databases/in-memory-oltp/supported-features-for-natively-compiled-t-sql-modules.md).  
  
 IDENTITY  
 Указывает, что новый столбец является столбцом идентификаторов. При добавлении в таблицу новой строки компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] формирует для этого столбца уникальное последовательное значение. Столбцы идентификаторов обычно используются с ограничением PRIMARY KEY для поддержания уникальности идентификаторов строк в таблице. Свойство IDENTITY может назначаться **tinyint**, **smallint**, **int**, **bigint**, **decimal(p,0)**, или **numeric(p,0)** столбцы. Для каждой таблицы можно создать только один столбец идентификаторов. Ограниченные значения по умолчанию и ограничения DEFAULT не могут использоваться в столбце идентификаторов. Необходимо указать как начальное значение, так и приращение, или же не указывать ничего. Если ничего не указано, применяется значение по умолчанию (1,1).  
  
 В таблице, оптимизированной для памяти, единственное допустимое значение для обоих *начальное значение* и *приращения* -1; (1,1) по умолчанию для *начальное значение* и *приращения*.  
  
 *Начальное значение*  
 Значение, используемое для самой первой строки, загружаемой в таблицу.  
  
 *приращение*  
 Значение приращения, добавляемое к значению идентификатора предыдущей загруженной строки.  
  
 NOT FOR REPLICATION  
 В инструкции CREATE TABLE предложение NOT FOR REPLICATION может указываться для свойства IDENTITY, а также ограничений FOREIGN KEY и CHECK. Если это предложение указано для свойства IDENTITY, значения в столбцах идентификаторов не приращиваются, если вставку выполняют агенты репликации. Если ограничение сопровождается этим предложением, оно не выполняется, когда агенты репликации выполняют операции вставки, обновления или удаления.  
  
 ВСЕГДА СОЗДАВАЕМЫЙ СТРОКИ AS {ПУСК | ЗАВЕРШИТЬ} [СКРЫТЫЕ] [NOT NULL]  
 **Применяется к**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] и [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].  
  
 Указывает datetime2 указанный столбец будет использоваться системой для записи, либо время начала, в течение которого запись остается действительным, либо время окончания, для которого действителен записи. Столбец должен быть определен как NOT NULL. При попытке указать их в качестве значения NULL, система выдает ошибку. Если NOT NULL для столбца периода не указан явно, система будет столбец определен как NOT NULL по умолчанию. Этот аргумент используется в сочетании с PERIOD FOR SYSTEM_TIME и с SYSTEM_VERSIONING = ON аргументы, чтобы включить систему управления версиями в таблице. Дополнительные сведения см. в разделе [Temporal Tables](../../relational-databases/tables/temporal-tables.md).  
  
 Вы можете пометить один или оба столбца периода **HIDDEN** флаг неявно скрыть эти столбцы таким образом, что **ВЫБЕРИТЕ \* FROM**  *`<table>`*  — нет Возвращает значение для этих столбцов. По умолчанию столбцы period не скрыты. Для использования, скрытые столбцы должны быть явно включены во всех запросах, которые ссылаются непосредственно на временная таблица. Чтобы изменить **HIDDEN** атрибут для существующего столбца периода **ПЕРИОД** необходимо удалить и создать заново с другой скрытый флаг.  
  
 `INDEX *index_name* [ CLUSTERED | NONCLUSTERED ] (*column_name* [ ASC | DESC ] [ ,... *n* ] )`  
     
**Применяется к**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] и [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].

Задает создание индекса для таблицы. Это может быть кластеризованный или некластеризованный индекс. Индекс будет содержать столбцы, перечисленные и приводит к сортировке данных в порядке возрастания или убывания.  
  
 Индекс *index_name* CLUSTERED COLUMNSTORE  
   
  
**Применяется к**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] и [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].
  
 Указывает сохранить таблицу целиком в виде столбцов с кластеризованным индексом columnstore. Это всегда включает все столбцы в таблице. Данные не отсортированы в алфавитном или цифровом порядке, так как строки сортируются так, чтобы получить преимущества сжатия columnstore.  
  
 Индекс *index_name* COLUMNSTORE [NONCLUSTERED] (*column_name* [,...*n* ] )  
   
  
**Применяется к**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] и [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].
  
 Позволяет создать некластеризованный индекс columnstore для таблицы. Базовая таблица может быть rowstore кучи или кластеризованного индекса или его можно в кластеризованном индексе. Во всех случаях для создания некластеризованного индекса columnstore в таблице хранятся вторую копию данных для столбцов в индексе.  
  
 Некластеризованный индекс columnstore хранится и управляется как кластеризованный индекс. Некластеризованный индекс columnstore для называется, поскольку столбцов может быть ограничен, и она указана как вторичный индекс для таблицы.  
  
 ON *partition_scheme_name***(***column_name***)**  
 Задает схему секционирования, которая определяет файловые группы соответствующие секциям секционированного индекса. Схема секционирования должна существовать в базе данных путем выполнения инструкции [CREATE PARTITION SCHEME](../../t-sql/statements/create-partition-scheme-transact-sql.md) или [ALTER PARTITION SCHEME](../../t-sql/statements/alter-partition-scheme-transact-sql.md). *column_name* указывает столбец, по которому будет секционирован секционированного индекса. Этот столбец должен соответствовать типу данных, длине и точности аргумента секции функции, *partition_scheme_name* использует. *column_name* предназначен не только для столбцов в определении индекса. Любой столбец в базовой таблице, можно указать, за исключением при секционировании УНИКАЛЬНОГО индекса, *column_name* должен быть выбран из используемых в уникальном ключе. Это ограничение дает возможность компоненту [!INCLUDE[ssDE](../../includes/ssde-md.md)] проверять уникальность значений ключа только в одной секции.  
  
> [!NOTE]  
>  При секционировании неуникального кластеризованного индекса компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] по умолчанию добавляет столбец секционирования в список ключей кластеризованного индекса, если этого столбца еще нет в списке. При секционировании неуникального некластеризованного индекса компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] добавляет столбец секционирования как неключевой (включенный) столбец индекса, если этого столбца еще нет в списке.  
  
 Если *partition_scheme_name* или *файловой группы* не указано и таблица секционирована, индекс помещается в ту же схему секционирования, с помощью тем же столбцом секционирования, что и базовая таблица.  
  
> [!NOTE]  
>  Для XML-индекса задать схему секционирования невозможно. Если базовая таблица секционирована, XML-индекс использует ту же схему секционирования, что и таблица.  
  
 Дополнительные сведения о секционировании индексов [секционированных таблиц и индексов](../../relational-databases/partitions/partitioned-tables-and-indexes.md).  
  
 ON *filegroup_name*  
 Создает заданный индекс в указанной файловой группе. Если местоположение не указано и таблица или представление не секционированы, индекс использует ту же файловую группу, что и базовая таблица или базовое представление. Файловая группа должна существовать.  
  
 ON **»**по умолчанию**»**  
 Создает заданный индекс в файловой группе, используемой по умолчанию.  
  
 Слово «default» в этом контексте не является ключевым. Он представляет собой идентификатор файловой группы по умолчанию и должен иметь разделители, как в выражениях ON **»**по умолчанию**»** или ON **[**по умолчанию**]**. Если указано значение «default» (по умолчанию), параметр QUOTED_IDENTIFIER должен иметь значение ON для текущего сеанса. Это параметр по умолчанию. Дополнительные сведения см. в разделе [SET QUOTED_IDENTIFIER (Transact-SQL)](../../t-sql/statements/set-quoted-identifier-transact-sql.md).  
  
 [FILESTREAM_ON { *filestream_filegroup_name* | *partition_scheme_name* | «NULL»}]  
   
**Область применения**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion.md)].

 Указывает размещение данных FILESTREAM для таблицы при создании кластеризованного индекса. Предложение FILESTREAM_ON позволяет перемещать данные FILESTREAM в другую файловую группу FILESTREAM или схему секционирования.  
  
 *filestream_filegroup_name* имя файловой группы FILESTREAM. В файловой группе должен быть определен один файл для файловой группы с помощью [CREATE DATABASE](../../t-sql/statements/create-database-sql-server-transact-sql.md) или [инструкции ALTER DATABASE](../../t-sql/statements/alter-database-transact-sql.md) оператор; в противном случае возникает ошибка.  
  
 Если таблица секционирована, должно быть включено предложение FILESTREAM_ON и указана схема секционирования файловых групп FILESTREAM, использующая те же функции и столбцы секционирования, что и схема секционирования для таблицы. В противном случае произойдет ошибка.  
  
 Если таблица не секционирована, столбец FILESTREAM не может быть секционирован. Данные FILESTREAM для этой таблицы необходимо хранить в отдельной файловой группе, указанной в предложении FILESTREAM_ON.  
  
 Предложение FILESTREAM_ON NULL может быть указано в инструкции CREATE INDEX, если создается кластеризованный индекс и таблица не содержит столбец FILESTREAM.  
  
 Дополнительные сведения см. в разделе [FILESTREAM (SQL Server)](../../relational-databases/blob/filestream-sql-server.md).  
  
 ROWGUIDCOL  
 Указывает, что новый столбец является столбцом идентификаторов GUID строки. Только один **uniqueidentifier** столбца в каждой таблице можно определить как столбец ROWGUIDCOL. Применение свойства ROWGUIDCOL позволяет ссылаться на столбец с помощью ключевого слова $ROWGUID. Свойство ROWGUIDCOL может присваиваться только **uniqueidentifier** столбца. Ключевым словом ROWGUIDCOL нельзя обозначать столбцы определяемых пользователем типов данных.  
  
 Свойство ROWGUIDCOL не обеспечивает уникальности значений, хранимых в столбце. Кроме того, при указании данного свойства автоматического формирования значений для новых строк, вставляемых в таблицу, не выполняется. Для формирования уникальных значений для каждого столбца, либо использовать [NEWID](../../t-sql/functions/newid-transact-sql.md) или [NEWSEQUENTIALID](../../t-sql/functions/newsequentialid-transact-sql.md) работу на [вставить](../../t-sql/statements/insert-transact-sql.md) инструкций или использовать эти функции по умолчанию для столбец.  
  
 ЗАШИФРОВАН  
 Указывает столбцы, шифрования с помощью [постоянного шифрования](../../relational-databases/security/encryption/always-encrypted-database-engine.md) компонентов.  
  
 COLUMN_ENCRYPTION_KEY = *key_name*  
 Указывает ключ шифрования столбца. Дополнительные сведения см. в разделе [CREATE COLUMN ENCRYPTION KEY &#40; Transact-SQL &#41; ](../../t-sql/statements/create-column-encryption-key-transact-sql.md).  
  
 ENCRYPTION_TYPE = {ДЕТЕРМИНИРОВАННЫМ | СЛУЧАЙНОЕ ШИФРОВАНИЕ;}  
 **Детерминированное шифрование** использует метод, который всегда создает одно и то же зашифрованное значение для любого текстового значения. С помощью детерминированного шифрования позволяет выполнять поиск с помощью сравнения равенства, группирование и соединение таблиц с помощью соединения равенства, на основе зашифрованных значений, при этом также несанкционированные пользователи могут определять некоторую информацию о зашифрованных значениях путем анализа закономерностей в зашифрованный столбец. Соединение двух таблиц для столбцов, зашифрованных детерминированного возможна, только если оба столбца шифруются с помощью того же ключа шифрования столбца. При использовании детерминированного шифрования необходимо указать порядок сортировки binary2 в параметрах сортировки для символьных столбцов.  
  
 **Случайное шифрование** использует метод, который шифрует данные менее предсказуемым образом. Случайное шифрование более безопасна, но не позволяет выполнять поиск равенства, группирование и объединение по зашифрованным столбцам. Столбцы с помощью случайного шифрования, невозможно проиндексировать.  
  
 Детерминированное шифрование используется для столбцов, которые будут являться параметров поиска или группирования параметров, например ИНН. Используйте случайное шифрование, для данных, например номер кредитной карты, который не сгруппированы с другими записями, и используется для соединения таблиц и которого не осуществляется поиск, так как другие столбцы (такие как номер транзакции) используется для поиска строки, которая содержит зашифрованный столбец, представляющие интерес.  
  
 Столбцы должны иметь подходящий тип данных.  
  
 АЛГОРИТМ  
 Должно быть **«AEAD_AES_256_CBC_HMAC_SHA_256»**.  
  
 Дополнительные сведения, включая возможность ограничения см. в разделе [постоянного шифрования &#40; компонент Database Engine &#41;](../../relational-databases/security/encryption/always-encrypted-database-engine.md).  
  
 **Область применения**: начиная с [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 SPARSE  
 Указывает, что столбец является разреженным столбцом. Хранилище разреженных столбцов оптимизируется для значений NULL. Для разреженных столбцов нельзя указать параметр NOT NULL. Дополнительные ограничения и Дополнительные сведения о разреженных столбцах см. в разделе [Использование разреженных столбцов](../../relational-databases/tables/use-sparse-columns.md).  
  
 С МАСКОЙ (ФУНКЦИЯ = " *mask_function* ")  
 **Область применения**: начиная с [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Задает маску динамических данных. *mask_function* имя функция маскирования с соответствующими параметрами. Доступны три функции:  
  
-   Default()  
  
-   Email()  
  
-   partial()  
  
-   Random()  
  
 Параметры функции. в разделе [динамической маскировки данных](../../relational-databases/security/dynamic-data-masking.md).  
  
 FILESTREAM  
   
**Область применения**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion.md)].

 Допустимо только для **varbinary(max)** столбцов. Указывает хранилище FILESTREAM для **varbinary(max)** данные большого двоичного ОБЪЕКТА.  
  
 Таблица также должна содержать столбец **uniqueidentifier** типом данных с атрибутом ROWGUIDCOL. Этот столбец не должен допускать значений NULL и должен иметь относящееся к одному столбцу ограничение UNIQUE или PRIMARY KEY. Значение идентификатора GUID для столбца должно быть предоставлено приложением во время вставки данных или ограничением DEFAULT, в котором используется функция NEWID ().  
  
 Столбец ROWGUIDCOL нельзя удалить, а связанные ограничения нельзя изменить, если в таблице определен столбец FILESTREAM. Столбец ROWGUIDCOL можно удалить только после удаления последнего столбца FILESTREAM.  
  
 Если для столбца задан атрибут хранилища FILESTREAM, то все значения для этого столбца хранятся в контейнере данных FILESTREAM в файловой системе.  
  
 COLLATE *collation_name*  
 Задает параметры сортировки для столбца. Могут использоваться параметры сортировки Windows или параметры сортировки SQL. *collation_name* применимо только к столбцам **char**, **varchar**, **текст**, **nchar**, **nvarchar**, и **ntext** типов данных. Если этот аргумент не указан, столбцу назначаются либо параметры сортировки определяемого пользователем типа, если столбец принадлежит к определяемому пользователем типу данных, либо установленные по умолчанию параметры сортировки для базы данных.  
  
 Дополнительные сведения об именах параметров сортировки Windows и SQL см. в разделе [имя параметров сортировки Windows](../../t-sql/statements/windows-collation-name-transact-sql.md) и [имя параметров сортировки SQL](../../t-sql/statements/sql-server-collation-name-transact-sql.md).  
  
 Дополнительные сведения о предложении COLLATE см. в разделе [COLLATE &#40; Transact-SQL &#41; ](~/t-sql/statements/collations.md).  
  
 CONSTRAINT  
 Необязательное ключевое слово, указывающее на начало определения ограничения PRIMARY KEY, NOT NULL, UNIQUE, FOREIGN KEY или CHECK.  
  
 *constraint_name*  
 Имя ограничения. Имена ограничений должны быть уникальными в пределах схемы, к которой принадлежит таблица.  
  
 NULL | NOT NULL  
 Определяет, допустимы ли для столбца значения NULL. Параметр NULL не является ограничением в строгом смысле слова, но может быть указан так же, как и NOT NULL. Ограничение NOT NULL может быть указано для вычисляемых столбцов только в случае, если одновременно указан параметр PERSISTED.  
  
 PRIMARY KEY  
 Ограничение, которое обеспечивает целостность сущностей для указанного столбца или столбцов с помощью уникального индекса. Можно создать только одно ограничение PRIMARY KEY для таблицы.  
  
 UNIQUE  
 Ограничение, которое обеспечивает целостность сущностей для указанного столбца или столбцов с помощью уникального индекса. В таблице может быть несколько ограничений UNIQUE.  
  
 CLUSTERED | NONCLUSTERED  
 Указывает, что для ограничения PRIMARY KEY или UNIQUE создается кластеризованный или некластеризованный индекс. Для ограничений PRIMARY KEY по умолчанию создается кластеризованный индекс (CLUSTERED), а для ограничений UNIQUE — некластеризованный (NONCLUSTERED).  
  
 В инструкции CREATE TABLE параметр CLUSTERED можно задать только для одного ограничения. Если для ограничения UNIQUE указан параметр CLUSTERED, и, кроме того, указано ограничение PRIMARY KEY, то для PRIMARY KEY применяется по умолчанию значение NONCLUSTERED.  
  
 В следующем примере показано использование параметра NONCLUSTERED в дисковой таблице.  
  
```  
CREATE TABLE t1 ( c1 int, INDEX ix_1 NONCLUSTERED (c1))   
CREATE TABLE t2( c1 int INDEX ix_1 NONCLUSTERED (c1))   
CREATE TABLE t3( c1 int, c2 int INDEX ix_1 NONCLUSTERED)   
CREATE TABLE t4( c1 int, c2 int, INDEX ix_1 NONCLUSTERED (c1,c2))  
```  
  
 FOREIGN KEY REFERENCES  
 Ограничение, которое обеспечивает ссылочную целостность данных в этом столбце или столбцах. Ограничения FOREIGN KEY требуют, чтобы каждое значение в столбце существовало в соответствующем связанном столбце или столбцах в связанной таблице. Ограничения FOREIGN KEY могут ссылаться только на столбцы, являющиеся ограничениями PRIMARY KEY или UNIQUE в связанной таблице или на столбцы, на которые имеются ссылки в индексе UNIQUE INDEX связанной таблицы. Внешние ключи в вычисляемых столбцах должны быть также помечены как PERSISTED.  
  
 [ *имя_схемы***.**] *referenced_table_name*]  
 Имя таблицы, на которую ссылается ограничение FOREIGN KEY, и схема, к которой она принадлежит.  
  
 **(** *ref_column* [ **,**... *n* ] **)**  
 Столбец или список столбцов из таблицы, на которую ссылается ограничение FOREIGN KEY.  
  
 ON DELETE { **ВМЕШАТЕЛЬСТВО** | CASCADE | SET NULL | SET DEFAULT}  
 Определяет операцию, которая производится над строками создаваемой таблицы, если эти строки имеют ссылочную связь, а строка, на которую имеются ссылки, удаляется из родительской таблицы. Параметр по умолчанию — NO ACTION.  
  
 NO ACTION  
 Компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] формирует ошибку, и выполняется откат операции удаления строки из родительской таблицы.  
  
 CASCADE  
 Если из родительской таблицы удаляется строка, соответствующие ей строки удаляются и из ссылающейся таблицы.  
  
 SET NULL  
 Все значения, составляющие внешний ключ, при удалении соответствующей строки родительской таблицы устанавливаются в NULL. Для выполнения этого ограничения внешние ключевые столбцы должны допускать значения NULL.  
  
 SET DEFAULT  
 Все значения, составляющие внешний ключ, при удалении соответствующей строки родительской таблицы устанавливаются в значение по умолчанию. Для выполнения этого ограничения все внешние ключевые столбцы должны иметь определения по умолчанию. Если столбец допускает значения NULL и значение по умолчанию явно не определено, значением столбца по умолчанию становится NULL.  
  
 Не следует использовать параметр CASCADE, если таблица будет включена в публикацию слиянием, в которой используются логические записи. Дополнительные сведения о логических записях см. в статье [Группирование изменений в связанных строках с помощью логических записей](../../relational-databases/replication/merge/group-changes-to-related-rows-with-logical-records.md).  
  
 Параметр ON DELETE CASCADE нельзя указывать, если в таблице уже существует триггер ON DELETE.  
  
 Например, в [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] базы данных, **ProductVendor** таблица имеет ссылочную связь с **поставщика** таблицы. **ProductVendor.BusinessEntityID** ссылок на внешние ключи **Vendor.BusinessEntityID** первичного ключа.  
  
 Если при выполнении инструкции DELETE для строки в **поставщика** указано действие ON DELETE CASCADE и таблицы для **ProductVendor.BusinessEntityID**, [!INCLUDE[ssDE](../../includes/ssde-md.md)] проверяет наличие одного или нескольких зависимых строки в **ProductVendor** таблицы. Если они существуют, зависимые строки в **ProductVendor** таблицы будут удалены, а также ссылки на строки в **поставщика** таблицы.  
  
 И наоборот, если указано NO ACTION [!INCLUDE[ssDE](../../includes/ssde-md.md)] вызывает ошибку и откатывает действие delete по **поставщика** строк, если хотя бы одна строка в **ProductVendor** таблице, ссылающейся на него.  
  
 ПРИ ОБНОВЛЕНИИ { **ВМЕШАТЕЛЬСТВО** | CASCADE | SET NULL | SET DEFAULT}  
 Указывает, какое действие совершается над строками в изменяемой таблице, когда эти строки имеют ссылочную связь и строка родительской таблицы, на которую указывает ссылка, обновляется. Параметр по умолчанию — NO ACTION.  
  
 NO ACTION  
 Компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] возвращает ошибку, а обновление строки родительской таблицы откатывается.  
  
 CASCADE  
 Соответствующие строки обновляются в ссылающейся таблице, если эта строка обновляется в родительской таблице.  
  
 SET NULL  
 Всем значениям, составляющим внешний ключ, присваивается значение NULL, когда обновляется соответствующая строка в родительской таблице. Для выполнения этого ограничения внешние ключевые столбцы должны допускать значения NULL.  
  
 SET DEFAULT  
 Всем значениям, составляющим внешний ключ, присваивается их значение по умолчанию, когда обновляется соответствующая строка в родительской таблице. Для выполнения этого ограничения все внешние ключевые столбцы должны иметь определения по умолчанию. Если столбец допускает значения NULL и значение по умолчанию явно не определено, значением столбца по умолчанию становится NULL.  
  
 Не следует использовать параметр CASCADE, если таблица будет включена в публикацию слиянием, в которой используются логические записи. Дополнительные сведения о логических записях см. в статье [Группирование изменений в связанных строках с помощью логических записей](../../relational-databases/replication/merge/group-changes-to-related-rows-with-logical-records.md).  
  
 Действия ON UPDATE CASCADE, SET NULL и SET DEFAULT не могут быть определены, если в изменяемой таблице уже существует триггер INSTEAD OF для условия ON UPDATE.  
  
 Например, в [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] базы данных, **ProductVendor** таблица имеет ссылочную связь с **поставщика** таблицы: **ProductVendor.BusinessEntity** ссылки на внешние ключи **Vendor.BusinessEntityID** первичного ключа.  
  
 Если при выполнении инструкции UPDATE для строки в **поставщика** таблицы, а действие ON UPDATE CASCADE задается для **ProductVendor.BusinessEntityID**, [!INCLUDE[ssDE](../../includes/ssde-md.md)] проверяет наличие одного или нескольких зависимых строки в **ProductVendor** таблицы. Если они существуют, зависимые строки в **ProductVendor** обновляются таблицы, а также ссылки на строки в **поставщика** таблицы.  
  
 И наоборот, если указано NO ACTION [!INCLUDE[ssDE](../../includes/ssde-md.md)] вызывает ошибку и откатывает операцию обновления **поставщика** строк, если хотя бы одна строка в **ProductVendor** таблице, ссылающейся на него.  
  
 CHECK  
 Ограничение, обеспечивающее целостность домена путем ограничения возможных значений, которые могут быть введены в столбец или столбцы. Ограничения CHECK в вычисляемых столбцах должны быть также помечены как PERSISTED.  
  
 *Logical_Expression*  
 Логическое выражение, возвращающее значения TRUE или FALSE. Псевдонимы типа данных частью выражения быть не могут.  
  
 *столбец*  
 Столбец или список столбцов (в скобках), используемый в ограничениях таблицы для указания столбцов, используемых в определении ограничения.  
  
 [ **ASC** | DESC]  
 Указывает порядок сортировки столбца или столбцов, участвующих в ограничениях таблицы. Значение по умолчанию — ASC.  
  
 *partition_scheme_name*  
 Имя схемы секционирования, определяющей файловые группы, которым сопоставляются секции секционированной таблицы. Эта схема секционирования должна существовать в базе данных.  
  
 [ *partition_column_name***.** ]  
 Указывает столбец, по которому будет секционирована таблица. Столбец должен совпадать с указанным в разделе функции, которая *partition_scheme_name* по типу данных, длине и точности. Вычисляемый столбец, участвующий в функции секционирования, должен быть явно обозначен ключевым словом PERSISTED.  
  
> [!IMPORTANT]  
>  Рекомендуется указывать параметр NOT NULL для столбца секционирования секционированных таблиц, а также для несекционированных таблиц, являющихся источниками или целями для операций ALTER TABLE...SWITCH. В результате любые ограничения CHECK, заданные для столбцов секционирования, не будут проверять значения NULL.  
  
 С коэффициентом ЗАПОЛНЕНИЯ  **=**  *fillfactor*  
 Указывает, насколько плотно компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] должен заполнять каждую страницу индекса, используемую для хранения данных индекса. Определяемый пользователем *fillfactor* может принимать значения от 1 до 100. Если значение не задано, по умолчанию принимается значение 0. Значения коэффициентов заполнения 0 и 100 идентичны.  
  
> [!IMPORTANT]  
>  Документации с FILLFACTOR = *fillfactor* освобождает как единственного параметра индекса, который применяется к ограничениям PRIMARY KEY или UNIQUE, сохраняется для обеспечения обратной совместимости, но не документируется таким образом в будущем.  
  
 *имя_набора_столбцов* XML COLUMN_SET FOR ALL_SPARSE_COLUMNS  
 Имя набора столбцов. Набор столбцов представляет собой нетипизированное XML-представление, в котором все разреженные столбцы таблицы объединены в структурированные выходные данные. Дополнительные сведения о наборах столбцов см. в разделе [Использование наборов столбцов](../../relational-databases/tables/use-column-sets.md).  
  
 PERIOD FOR SYSTEM_TIME (*system_start_time_column_name* , *system_end_time_column_name* )  
   
**Применяется к**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] и [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].
  
 Задает имена столбцов, система будет использовать для записи период, в течение которого запись остается действительным. Этот аргумент используется в сочетании с создается всегда AS строки {Пуск | КОНЕЦ} и с SYSTEM_VERSIONING = ON аргументы, чтобы включить систему управления версиями в таблице. Дополнительные сведения см. в разделе [Temporal Tables](../../relational-databases/tables/temporal-tables.md).  
  
 COMPRESSION_DELAY  
   
**Применяется к**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] и [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].
  
 Для оптимизированной для памяти задержка задает минимальное количество минут, должны оставаться строки в таблице, без изменений, прежде чем он станет отсрочить сжатие в индекс columnstore. SQL Server выбирает определенных строк для сжатия в соответствии с их время последнего обновления. Например, если строки изменяется часто в течение двухчасового периода времени, можно задать COMPRESSION_DELAY = 120 минут для обеспечения завершения обновления до SQL Server сжимает строки.  
  
 Для таблицы на диске задержка задает минимальное количество минут, которые должны оставаться в состоянии CLOSED разностную группу строк в разностную группу строк, до SQL Server можно сжать в сжатую группу строк. Так как не отслеживания вставки и обновления таблиц на диске время в отдельных строках, SQL Server применяет задержка разностных групп строк в состояние CLOSED.  
  
 Значение по умолчанию — 0 минут.  
  
 Для рекомендации по использованию COMPRESSION_DELAY, см. в разделе [начало работы с Columnstore для операционной аналитики в реальном времени](../../relational-databases/indexes/get-started-with-columnstore-for-real-time-operational-analytics.md)  
  
 \<table_option >:: = Указывает один или несколько параметров таблицы.  
  
 DATA_COMPRESSION  
 Задает режим сжатия данных для указанной таблицы, номера секции или диапазона секций. Существуют следующие параметры выбора.  
  
 NONE  
 Таблица или указанные секции не сжимаются.  
  
 ROW  
 Таблицы или указанные секции сжимаются, используя сжатие строк.  
  
 PAGE  
 Таблицы или указанные секции сжимаются, используя сжатие страниц.  
  
 COLUMNSTORE  
   
  
**Применяется к**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] и [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].
  
 Применяется только к индексам columnstore, включая некластеризованные и кластеризованные индексы columnstore. COLUMNSTORE указывает, сжимать сжатием columnstore большинство производительным. Это типичный вариант.  
  
 COLUMNSTORE_ARCHIVE  
   
  
**Применяется к**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] и [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].  
  
 Применяется только к индексам columnstore, включая некластеризованные и кластеризованные индексы columnstore. COLUMNSTORE_ARCHIVE обеспечивает дальнейшее сжатие таблицы или секции для меньшего размера. Это может использоваться для архивации или в других ситуациях, где требуется уменьшение объема пространства и допускается увеличение затрат времени на сохранение и выборку  
  
 Дополнительные сведения о сжатии см. в разделе [сжатие данных](../../relational-databases/data-compression/data-compression.md).  
  
 В СЕКЦИЯХ **(** { `<partition_number_expression>` | [ **,**... *n* ] **)**  
 Указывает секции, к которым применяется параметр DATA_COMPRESSION. Если таблица не секционирована, аргумент ON PARTITIONS приведет к формированию ошибки. Если не указано предложение ON PARTITIONS, параметр DATA_COMPRESSION применяется ко всем секциям секционированной таблицы.  
  
 *выражение_номера_секции* можно задать следующими способами:  
  
-   Указать номер секции, например: ON PARTITIONS (2).  
  
-   Указать номера нескольких секций через запятые, например ON PARTITIONS (1, 5).  
  
-   Указать диапазоны и отдельные секции, например: ON PARTITIONS (2, 4, 6 TO 8).  
  
 `<range>`можно указать как номера секций, разделенные словом TO, например: ON PARTITIONS (6 – 8).  
  
 Чтобы для разных секций задать разные типы сжатия данных, укажите параметр DATA_COMPRESSION несколько раз, например следующим образом.  
  
```  
WITH   
(  
DATA_COMPRESSION = NONE ON PARTITIONS (1),   
DATA_COMPRESSION = ROW ON PARTITIONS (2, 4, 6 TO 8),   
DATA_COMPRESSION = PAGE ON PARTITIONS (3, 5)  
)  
```  
  
 \<index_option >:: =  
 Указывает один или более параметров индекса. Полное описание этих параметров см. в разделе [CREATE INDEX &#40; Transact-SQL &#41; ](../../t-sql/statements/create-index-transact-sql.md).  
  
 PAD_INDEX = {ON | **OFF** }  
 Если указано значение ON, процент свободного места, определяемый параметром FILLFACTOR, применяется к страницам индекса промежуточного уровня. Если указано значение OFF или значение FILLFACTOR не указано, страницы промежуточного уровня заполняются до приблизительного объема, оставляющего достаточно места для, как минимум, одной строки максимального размера, которого может достигать индекс, при этом учитывается набор ключей на промежуточных страницах. Значение по умолчанию — OFF.  
  
 Значение коэффициента ЗАПОЛНЕНИЯ  **=**  *fillfactor*  
 Определяет величину в процентах, показывающую насколько должен компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] заполнять конечный уровень каждой страницы индекса во время его создания и изменения. *значение коэффициента заполнения* должно быть целым числом от 1 до 100. Значение по умолчанию равно 0. Значения коэффициентов заполнения 0 и 100 идентичны.  
  
 IGNORE_DUP_KEY = {ON | **OFF** }  
 Определяет ответ на ошибку, случающуюся, когда операция вставки пытается вставить в уникальный индекс повторяющиеся значения ключа. Параметр IGNORE_DUP_KEY применяется только к операциям вставки, производимым после создания или перестроения индекса. Параметр не имеет значения при выполнении [CREATE INDEX](../../t-sql/statements/create-index-transact-sql.md), [ALTER INDEX](../../t-sql/statements/alter-index-transact-sql.md), или [обновление](../../t-sql/queries/update-transact-sql.md). Значение по умолчанию — OFF.  
  
 ON  
 Если в уникальный индекс вставляются повторяющиеся значения ключа, выводится предупреждающее сообщение. С ошибкой завершаются только строки, нарушающие ограничение уникальности.  
  
 OFF  
 Если в уникальный индекс вставляются повторяющиеся значения ключа, выводится сообщение об ошибке. Будет выполнен откат всей операции INSERT.  
  
 IGNORE_DUP_KEY нельзя установить в значение ON для индексов, создаваемых для представлений, неуникальных индексов, XML-индексов, пространственных индексов и фильтруемых индексов.  
  
 Для просмотра значения IGNORE_DUP_KEY используйте [sys.indexes](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md).  
  
 Для обратной совместимости синтаксиса аргумент WITH IGNORE_DUP_KEY эквивалентен аргументу WITH IGNORE_DUP_KEY = ON.  
  
 STATISTICS_NORECOMPUTE  **=**  {ON | **OFF** }  
 Если указано значение ON, автоматический пересчет устаревших статистик индекса не производится. Если указано значение OFF, включается автоматическое обновление статистик. Значение по умолчанию — OFF.  
  
 ALLOW_ROW_LOCKS  **=**  { **ON** | {OFF}  
 Если указано значение ON, при доступе к индексу допустимы блокировки строк. Компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] определяет, когда используются блокировки строки. При значении OFF блокировки строк не используются. Значение по умолчанию — ON.  
  
 ALLOW_PAGE_LOCKS  **=**  { **ON** | {OFF}  
 Если указано значение ON, при доступе к индексу допустимы блокировки страниц. Компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] определяет, когда используются блокировки страниц. При значении OFF блокировки страниц не используются. Значение по умолчанию — ON.  
  
 FILETABLE_DIRECTORY = *directory_name*  
   
  
**Область применения**: начиная с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. 
  
 Указывает имя каталога таблицы FileTable, совместимое с Windows. Это имя должно быть уникальным среди всех имен каталогов FileTable в базе данных. Проверка уникальности выполняется без учета регистра, независимо от параметров сортировки. Если это значение не задано, то используется имя таблицы FileTable.  
  
 FILETABLE_COLLATE_FILENAME = { *имя_параметров_сортировки* | database_default}  
   
  
**Область применения**: начиная с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. 
  
 Указывает имя параметров сортировки, применяемых к столбцу **Name** в таблице FileTable. Для соответствия семантике именования файлов Windows параметры сортировки не должны учитывать регистр. Если это значение не задано, то используются параметры сортировки по умолчанию базы данных. Если в параметрах сортировки по умолчанию базы данных учитывается регистр, то выдается ошибка и операция CREATE TABLE оканчивается неуспешно.  
  
 *collation_name*  
 Имя параметров сортировки, не учитывающих регистр.  
  
 database_default  
 Указывает, что для базы данных следует использовать параметры сортировки по умолчанию. Эти параметры сортировки не должны учитывать регистр символов.  
  
 FILETABLE_PRIMARY_KEY_CONSTRAINT_NAME = *constraint_name*  
   
**Область применения**: начиная с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. 
  
 Указывает имя, которое должно использоваться для ограничения первичного ключа, автоматически создаваемого в FileTable. Если это значение не задано, то имя для ограничения формируется системой.  
  
 FILETABLE_STREAMID_UNIQUE_CONSTRAINT_NAME = *constraint_name*  
   
  
**Область применения**: начиная с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. 
  
 Указывает имя, которое используется для ограничения уникальности, автоматически создается на **stream_id** столбца в таблице FileTable. Если это значение не задано, то имя для ограничения формируется системой.  
  
 FILETABLE_FULLPATH_UNIQUE_CONSTRAINT_NAME = *constraint_name*  
   
  
**Область применения**: начиная с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. 
  
 Указывает имя, которое используется для ограничения уникальности, автоматически создается на **parent_path_locator** и **имя** столбцы в таблице FileTable. Если это значение не задано, то имя для ограничения формируется системой.  
  
 SYSTEM_VERSIONING  **=**  ON [(HISTORY_TABLE  **=**  *schema_name* .  *history_table_name* [, DATA_CONSISTENCY_CHECK  **=**  { **ON** | {OFF}])]  
   
  
**Применяется к**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] и [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].   
  
 Включает системы управления версиями, таблицы, если соблюдены требования ограничение первичного ключа, ограничение на допустимость значений NULL и тип данных. Если **HISTORY_TABLE** аргумент не используется, система создает новую таблицу журнала сопоставления схему текущей таблицы в той же файловой группе, что и текущая таблица, создание связи между двумя таблицами и позволяет системе запись журнала для каждой записи в текущей таблице в таблице журнала. Имя этой таблицы журнала будет `MSSQL_TemporalHistoryFor<primary_table_object_id>`. По умолчанию таблица журнала сжимается с использованием метода **PAGE** . Если аргумент HISTORY_TABLE используется для создания ссылки и использовать существующую таблицу журнала, связь создается между текущей таблицей и указанной таблицы. Если текущая таблица секционирована, таблица журнала создается в файловой группе по умолчанию, так как конфигурация секционирования не реплицируется автоматически из текущей таблицы в таблицу журнала. Если при создании таблицы журнала указывается ее имя, следует также указать имя схемы и таблицы. При создании ссылки на существующую таблицу журнала вы можете указать необходимость проверки согласованности данных. Проверка согласованности данных гарантирует, что существующие записи не перекрываются. Проверка согласованности данных является проверкой по умолчанию. Этот аргумент используется в сочетании с PERIOD FOR SYSTEM_TIME и СОЗДАННЫЙ всегда AS строки {Пуск | Аргументы окончания} Включение системы управления версиями в таблице. Дополнительные сведения см. в разделе [Temporal Tables](../../relational-databases/tables/temporal-tables.md).  
  
 REMOTE_DATA_ARCHIVE = {ON [( *table_stretch_options* [,... n])] | OFF (ПАРАМЕТРА MIGRATION_STATE = ПРИОСТАНОВЛЕН)}  
   
  
**Область применения**: начиная с [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Создает новую таблицу базы данных Stretch, включен или отключен. Дополнительные сведения см. в разделе [Stretch Database](../../sql-server/stretch-database/stretch-database.md).  
  
 **Включение базы данных Stretch для таблицы**  
  
 Если включить растяжение для таблицы, указав `ON`, можно дополнительно указать `MIGRATION_STATE = OUTBOUND` начинается немедленно, перенос данных или `MIGRATION_STATE = PAUSED` чтобы отложить перенос данных. Значение по умолчанию — `MIGRATION_STATE = OUTBOUND`. Дополнительные сведения о включении растяжения для таблицы см. в разделе [включения базы данных Stretch для таблицы](../../sql-server/stretch-database/enable-stretch-database-for-a-table.md).  
  
 **Предварительные требования**. Прежде чем включать Stretch для таблицы, необходимо включить растяжение на сервере и в базе данных. Дополнительные сведения см. в разделе [Enable Stretch Database for a database](../../sql-server/stretch-database/enable-stretch-database-for-a-database.md).  
  
 **Разрешения**. Включение Stretch для базы данных или таблицы требуются права db_owner. Включение Stretch для таблицы также требуется разрешение ALTER на таблицу.  
  
 [FILTER_PREDICATE = {null | *предикат* }]  
   
  
**Область применения**: начиная с [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 При необходимости указывает предикат фильтра для выбора строк для миграции из таблицы, которая содержит исторические и текущие данные. Этот предикат должен вызывать детерминированной встроенной табличной функции. Дополнительные сведения см. в разделе [включения базы данных Stretch для таблицы](../../sql-server/stretch-database/enable-stretch-database-for-a-table.md) и [Выбор строк для миграции с помощью функции фильтрации](../../sql-server/stretch-database/select-rows-to-migrate-by-using-a-filter-function-stretch-database.md). 
   
> [!IMPORTANT]  
>  Если указать плохо оптимизированный предикат фильтра, перенос данных будет выполняться медленно. Stretch Database применяет предикат фильтра к таблице при помощи оператора CROSS APPLY.  
  
 Если предикат фильтра не указан, переносится вся таблица.  
  
 При указании предикат фильтра, необходимо указать *параметра MIGRATION_STATE*.  
  
 ПАРАМЕТРА MIGRATION_STATE = {ИСХОДЯЩИХ |  ВХОДЯЩИЙ | ПРИОСТАНОВЛЕНО}  
   
  
**Применяется к**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]и Azure SQL. 
  
-   Укажите `OUTBOUND` для переноса данных из SQL Server в Azure.  
  
-   Укажите `INBOUND` для копирования удаленной данные таблицы из Azure обратно в SQL Server и отключить растяжение для таблицы. Дополнительные сведения см. в разделе [Отключение Stretch Database и возврат удаленных данных](../../sql-server/stretch-database/disable-stretch-database-and-bring-back-remote-data.md).  
  
     Эта операция предусматривает расходы на передачу данных и не может быть отменена.  
  
-   Укажите `PAUSED` чтобы приостанавливать и откладывать переноса данных. Дополнительные сведения см. в разделе [Приостановка и возобновление переноса данных &#40; База данных Stretch &#41; ](../../sql-server/stretch-database/pause-and-resume-data-migration-stretch-database.md).  
  
 MEMORY_OPTIMIZED  
   
  
**Применяется к**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] и [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].  
  
 Значение ON указывает, что таблица является оптимизированным для памяти. Оптимизированные для памяти таблицы являются частью функции OLTP в памяти, которая используется для оптимизации производительности обработки транзакций. Чтобы приступить к работе с In-Memory OLTP см. [краткое руководство 1: технологии выполнения OLTP в памяти для быстрее производительности Transact-SQL](../../relational-databases/in-memory-oltp/survey-of-initial-areas-in-in-memory-oltp.md). Более подробные сведения о таблицах, оптимизированных для памяти. в разделе [оптимизированные для памяти таблицы](../../relational-databases/in-memory-oltp/memory-optimized-tables.md).  
  
 Значение по умолчанию OFF указывает, что таблицы на диске.  
  
 DURABILITY  
   
  
**Применяется к**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] и [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].   
  
 Значение SCHEMA_AND_DATA указывает, что таблица является устойчивой, это означает, что изменения сохраняются на диске и остались после перезапуска или отработки отказа.  SCHEMA_AND_DATA — это значение по умолчанию.  
  
 Значение SCHEMA_ONLY указывает, что таблица не является надежной. Схема таблицы сохраняется, но обновления данных не сохраняются после перезапуска или отработки отказа базы данных. DURABILITY = SCHEMA_ONLY допускается только с аргументом MEMORY_OPTIMIZED = ON.  
  
> [!WARNING]  
>  При создании таблицы с **DURABILITY = SCHEMA_ONLY**, и **READ_COMMITTED_SNAPSHOT** впоследствии изменяется с помощью **инструкции ALTER DATABASE**, данные в таблице будут утеряны.  
  
 BUCKET_COUNT  
   
  
**Применяется к**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] и [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]. 
  
 Отображает число контейнеров, которые необходимо создать в хэш-индексе. Максимальное значение для параметра BUCKET_COUNT в хэш-индексах составляет 1 073 741 824. Дополнительные сведения о подсчете числа контейнеров см. в разделе [индексы для оптимизированных для памяти таблиц](../../relational-databases/in-memory-oltp/indexes-for-memory-optimized-tables.md).  
  
 Bucket_count — это обязательный аргумент.  
  
 INDEX  
   
  
**Применяется к**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] и [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]. 
  
Индексы столбцов и таблиц, можно указать как часть инструкции CREATE TABLE. Дополнительные сведения о добавлении и удалении индексов в таблицах, оптимизированных для памяти см.: [изменение таблиц](../../relational-databases/in-memory-oltp/altering-memory-optimized-tables.md)
  
 HASH  
   
  
**Применяется к**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] и [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]. 
  
 Указывает, что был создан индекс HASH.  
  
 Хэш-индексы поддерживаются только в таблицах, оптимизированных для памяти.  
  
## <a name="remarks"></a>Замечания  
 Сведения о количестве допустимых таблиц, столбцов, ограничений и индексов см. в разделе [Maximum Capacity Specifications for SQL Server](../../sql-server/maximum-capacity-specifications-for-sql-server.md).  
  
 Пространство таблицам и индексам обычно выделяется по одному экстенту за раз. Если ЗАДАТЬ инструкции mixed_page_allocation ALTER DATABASE присвоено значение TRUE, или всегда до [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]при создании таблицы или индекса им выделяются страницы из смешанных экстентов, пока число страниц для однородного экстента. Каждый раз, когда число страниц достигает размера однородного экстента, и текущие выделенные экстенты становятся заполненными, выделяется новый экстент. Отчет об объеме пространства выделение и использование таблицы, выполнение **sp_spaceused**.  
  
 Компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] не требует указания параметров DEFAULT, IDENTITY, ROWGUIDCOL или ограничения столбцов в определенном порядке при определении столбца.  
  
 После создания таблицы параметр QUOTED IDENTIFIER всегда сохраняется в метаданных таблицы в состоянии ON, даже если он был установлен в состояние OFF при создании таблицы.  
  
## <a name="temporary-tables"></a>Временные таблицы  
 Можно создавать локальные и глобальные временные таблицы. Локальные временные таблицы видимы только во время текущего сеанса, а глобальные — во всех сеансах. Временные таблицы не подлежат секционированию.  
  
 Префикс имен локальных временных таблиц знак номера (#*table_name*), а имени глобальной временной таблицы — двойной знак номера префикса (##*table_name*).  
  
 Инструкции SQL ссылаются временной таблицы, используя значение, указанное для *table_name* в инструкции CREATE TABLE для примера ###:  
  
```  
CREATE TABLE #MyTempTable (cola INT PRIMARY KEY);  
  
INSERT INTO #MyTempTable VALUES (1);  
```  
  
 Если в пределах одной хранимой процедуры или пакета создается более одной временной таблицы, им должны быть присвоены разные имена.  
  
 Если локальная временная таблица создается хранимой процедурой или приложением, которые одновременно могут выполняться несколькими пользователями, компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] должен иметь возможность различать таблицы, созданные разными пользователями. Компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] делает это путем внутреннего присоединения числового суффикса к имени каждой локальной временной таблицы. Полное имя временной таблицы, хранящееся в **sysobjects** в таблицу **tempdb** состоит из имени таблицы, указанной в инструкции CREATE TABLE и числового суффикса, созданный системой. Чтобы разрешить для этого суффикса *table_name* указано как имя локальной временной не может превышать 116 символов.  
  
 Временные таблицы автоматически удаляются при выходе за пределы области определения, если не удалять их явно с помощью инструкции DROP TABLE.  
  
-   Локальная временная таблица, созданная хранимой процедурой, удаляется автоматически при завершении хранимой процедуры. К этой таблице могут обращаться любые вложенные хранимые процедуры, выполняемые хранимой процедурой, создавшей таблицу. Процесс, вызвавший хранимую процедуру, создавшую таблицу, к этой таблице обращаться не может.  
  
-   Все прочие локальные временные таблицы удаляются автоматически в конце текущего сеанса.  
  
-   Глобальные временные таблицы автоматически удаляются при завершении сеанса, создавшего таблицу, и прекращении обращения к ним всех прочих задач. Взаимосвязь между задачей и таблицей поддерживается только на время выполнения отдельной инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)]. Это означает, что глобальная временная таблица удаляется после выполнения последней инструкции языка [!INCLUDE[tsql](../../includes/tsql-md.md)], активно обращавшейся к ней во время завершения создавшего таблицу сеанса.  
  
 Локальная временная таблица, созданная хранимой процедурой или триггером, может иметь то же имя, что и временная таблица, созданная до вызова хранимой процедуры или триггера. Однако если запрос обращается к временной таблице и одновременно существует две таблицы с одинаковым именем, не определено, к какой из таблиц будет направлен запрос. Вложенные хранимые процедуры могут также создавать временные таблицы с тем же именем, что и временная таблица, созданная вызывающей хранимой процедурой. Однако для применения изменений к таблице, созданной во вложенной процедуре, эта таблица должна иметь ту же структуру с теми же именами столбцов, что и таблица, созданная в вызывающей процедуре. Это показано в следующем примере.  
  
```  
CREATE PROCEDURE dbo.Test2  
AS  
    CREATE TABLE #t(x INT PRIMARY KEY);  
    INSERT INTO #t VALUES (2);  
    SELECT Test2Col = x FROM #t;  
GO  
  
CREATE PROCEDURE dbo.Test1  
AS  
    CREATE TABLE #t(x INT PRIMARY KEY);  
    INSERT INTO #t VALUES (1);  
    SELECT Test1Col = x FROM #t;  
EXEC Test2;  
GO  
  
CREATE TABLE #t(x INT PRIMARY KEY);  
INSERT INTO #t VALUES (99);  
GO  
  
EXEC Test1;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
 (1 row(s) affected) 
 Test1Col 
 ----------- 
 1 

 (1 row(s) affected) 
 Test2Col 
 ----------- 
 2 
 ```
  
 При создании локальных или глобальных временных таблиц синтаксис инструкции CREATE TABLE поддерживает определение всех ограничений, кроме FOREIGN KEY. Если во временной таблице указано ограничение FOREIGN KEY, инструкция возвращает предупредительное сообщение, указывающее на то, что ограничение было пропущено. При этом таблица создается без ограничений FOREIGN KEY. В ограничениях FOREIGN KEY обращение к временным таблицам недопустимо.  
  
 При создании таблицы с именованным ограничением внутри области, определяемой пользователем транзакции, возможность выполнения инструкций, формирующих временные таблицы, ограничивается одним пользователем единовременно. Например, если хранимая процедура формирует временную таблицу с именованным ограничением первичного ключа, то она не может быть выполнена несколькими пользователями одновременно.  


## <a name="database-scoped-global-temporary-tables-azure-sql-database"></a>Глобальные временные таблицы (база данных SQL Azure) в области базы данных

Глобальные временные таблицы для SQL Server (для инициализации ## имя таблицы) хранятся в базе данных tempdb и совместно используются сеансы всех пользователей во всем экземпляре SQL Server. Сведения о табличных типов SQL см. выше раздел на создание таблиц.  

База данных SQL Azure поддерживает глобальные временные таблицы, которые также хранятся в базе данных tempdb и областью действия на уровне базы данных.  Это означает, что глобальные временные таблицы являются общими для всех пользователей сеансов в пределах одной и той же базе данных Azure SQL. Сеансы пользователей из других баз данных Azure SQL не удается получить доступ к глобальные временные таблицы.

Глобальные временные таблицы для базы данных SQL Azure следуйте того же синтаксиса и семантики, SQL Server использует для временных таблиц.  Аналогичным образом глобальные временные хранимые процедуры распространяются также на уровне базы данных в базе данных SQL Azure. Локальные временные таблицы (# имя таблицы для инициализации) также поддерживается для базы данных SQL Azure и следуйте же синтаксис и семантику, используемый SQL Server.  См. в разделе выше [временные таблицы](#temporary-tables).  

> [!IMPORTANT]
> Эта функция находится в общедоступной предварительной версии и доступно для баз данных SQL Azure.
>

### <a name="troubleshooting-global-temporary-tables-for-azure-sql-db"></a>Глобальные временные таблицы для устранения неполадок в базе данных SQL Azure 

Для устранения неполадок tempdb [Устранение неполадок недостаточно места на диске в базе данных tempdb](https://technet.microsoft.com/library/ms176029%28v=sql.105%29.aspx?f=255&MSPPError=-2147217396). Для доступа к устранению неполадок динамических административных представлений в базе данных SQL Azure, необходимо быть администратором сервера.
  
### <a name="permissions"></a>Permissions  

 Любой пользователь может создавать глобальные временные объекты. Если не предоставлены какие-либо дополнительные разрешения, то пользователи могут производить доступ только к тем объектам, которыми они владеют. .  
  
### <a name="examples"></a>Примеры 

- Объект сеанса создает глобальных временных таблиц ##test в testdb1 базы данных SQL Azure и добавляет одну строку

```tsql
CREATE TABLE ##test ( a int, b int);
INSERT INTO ##test values (1,1);

--Obtain object ID for temp table ##test 
SELECT OBJECT_ID('tempdb.dbo.##test') AS 'Object ID'; 

---Result
1253579504

---Obtain global temp table name for a given object ID 1253579504 in tempdb (2)
SELECT name FROM tempdb.sys.objects WHERE object_id = 1253579504

---Result
##test
```
- Сеанс B подключается к базе данных SQL Azure testdb1 и может получить доступ к таблице ##test созданные в сеансе A

```tsql
SELECT * FROM ##test
---Results
1,1
```

- Сеанс C подключается к другой базе данных в базе данных SQL Azure testdb2 и хочет получить доступ к ##test в testdb1. Выберите неудачей из-за области базы данных, для глобальных временных таблиц 

```tsql
SELECT * FROM ##test
---Results
Msg 208, Level 16, State 0, Line 1
Invalid object name '##test'
```

- Обращение с текущего пользователя базы данных testdb1 системный объект в базе данных tempdb базы данных SQL Azure

```tsql
SELECT * FROM tempdb.sys.objects
SELECT * FROM tempdb.sys.columns
SELECT * FROM tempdb.sys.database_files
```



## <a name="partitioned-tables"></a>Секционированные таблицы  
 Перед созданием секционированной таблицы с помощью инструкции CREATE TABLE следует вначале создать функцию секционирования, чтобы указать, как должна быть секционирована таблица. Функция секционирования создается с помощью [CREATE PARTITION FUNCTION](../../t-sql/statements/create-partition-function-transact-sql.md). Затем необходимо создать схему секционирования, чтобы указать файловые группы, которые будут содержать указанные функцией секционирования секции. Схема секционирования создается с помощью [CREATE PARTITION SCHEME](../../t-sql/statements/create-partition-scheme-transact-sql.md). Для секционированных таблиц нельзя указать ограничения PRIMARY KEY или UNIQUE для разделения файловых групп. Дополнительные сведения см. в разделе [Partitioned Tables and Indexes](../../relational-databases/partitions/partitioned-tables-and-indexes.md).  
  
## <a name="primary-key-constraints"></a>Ограничения PRIMARY KEY  
  
-   В таблице возможно наличие только одного ограничения по первичному ключу.  
  
-   Индекс, формируемый ограничением PRIMARY KEY, не может привести к выходу количества индексов в таблице за пределы в 999 некластеризованных индексов и 1 кластеризованный.  
  
-   Если для ограничения PRIMARY KEY не указан параметр CLUSTERED или NONCLUSTERED, применяется параметр CLUSTERED, если для ограничения UNIQUE не определено кластеризованных индексов.  
  
-   Все столбцы с ограничением PRIMARY KEY должны иметь признак NOT NULL. Если допустимость значения NULL не указана, то для всех столбцов c ограничением PRIMARY KEY устанавливается признак NOT NULL.  
  
    > [!NOTE]  
    >  Для таблиц, оптимизированных для памяти может быть NULLable ключевой столбец.  
  
-   Если первичный ключ определен на столбце определяемого пользователем типа данных CLR, реализация этого типа должна поддерживать двоичную сортировку. Дополнительные сведения об определяемых пользователем типах данных CLR см. в разделе [Определяемые пользователем типы данных CLR](../../relational-databases/clr-integration-database-objects-user-defined-types/clr-user-defined-types.md).  
  
## <a name="unique-constraints"></a>Ограничения UNIQUE  
  
-   Если для ограничения UNIQUE не указан параметр CLUSTERED или NONCLUSTERED, по умолчанию применяется параметр NONCLUSTERED.  
  
-   Каждое ограничение уникальности создает индекс. Количество ограничений UNIQUE не может привести к выходу количества индексов в таблице за пределы в 999 некластеризованных индексов и 1 кластеризованный.  
  
-   Если ограничение уникальности определено на столбце определяемого пользователем типа данных CLR, реализация этого типа должна поддерживать двоичную сортировку или сортировку на основе оператора. Дополнительные сведения об определяемых пользователем типах данных CLR см. в разделе [Определяемые пользователем типы данных CLR](../../relational-databases/clr-integration-database-objects-user-defined-types/clr-user-defined-types.md).  
  
## <a name="foreign-key-constraints"></a>Ограничения FOREIGN KEY  
  
-   Если столбцу, имеющему ограничение внешнего ключа, задается значение, отличное от NULL, такое же значение должно существовать и в указываемом столбце; в противном случае будет возвращено сообщение о нарушении внешнего ключа.  
  
-   Если не указаны исходные столбцы, ограничения FOREIGN KEY применяются к предшествующему столбцу.  
  
-   Ограничения FOREIGN KEY могут ссылаться только на таблицы в пределах той же базы данных на том же сервере. Межбазовую ссылочную целостность необходимо реализовать посредством триггеров. Дополнительные сведения см. в разделе [CREATE TRIGGER (Transact-SQL)](../../t-sql/statements/create-trigger-transact-sql.md).  
  
-   Ограничения FOREIGN KEY могут ссылаться на другие столбцы той же таблицы. Это называется самовызовом.  
  
-   Предложение REFERENCES ограничения внешнего ключа на уровне столбца может содержать только один ссылочный столбец. Этот столбец должен принадлежать к тому же типу данных, что и столбец, для которого определяется ограничение.  
  
-   Предложение REFERENCES ограничения внешнего ключа на уровне таблицы должно содержать такое же число ссылочных столбцов, какое содержится в списке столбцов в ограничении. Тип данных каждого ссылочного столбца должен также совпадать с типом соответствующего столбца в списке столбцов.  
  
-   CASCADE, SET NULL и SET DEFAULT не может указываться Если столбец типа **timestamp** является частью внешнего ключа или ссылочного ключа.  
  
-   Ключевые слова CASCADE, SET NULL, SET DEFAULT и NO ACTION можно сочетать в таблицах, имеющих взаимные ссылочные связи. Если компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] обнаруживает ключевое слово NO ACTION, оно остановит и произведет откат связанных операций CASCADE, SET NULL и SET DEFAULT. Если инструкция DELETE содержит сочетание ключевых слов CASCADE, SET NULL, SET DEFAULT и NO ACTION, то все операции CASCADE, SET NULL и SET DEFAULT выполняются перед поиском компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)] операции NO ACTION.  
  
-   Компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] не имеет стандартного предела на количество ограничений FOREIGN KEY, содержащихся в таблице, ссылающейся на другие таблицы, или на количество ограничений FOREIGN KEY в других таблицах, ссылающихся на указанную таблицу.  
  
     Тем не менее фактическое количество ограничений FOREIGN KEY, доступных для использования, ограничивается конфигурацией оборудования, базы данных и приложения. Рекомендуется, чтобы таблица содержала не более 253 ограничений FOREIGN KEY, а также чтобы на нее ссылалось не более 253 ограничений FOREIGN KEY. Предел эффективности в конкретном случае может более или менее зависеть от приложения и оборудования. При разработке базы данных и приложений следует учитывать стоимость принудительных ограничений FOREIGN KEY.  
  
-   Ограничения FOREIGN KEY не применяются к временным таблицам.  
  
-   Ограничения FOREIGN KEY могут ссылаться только на столбцы с ограничениями PRIMARY KEY или UNIQUE в таблице, на которую указывает ссылка, или на столбцы уникального индекса (UNIQUE INDEX) такой таблицы.  
  
-   Если внешний ключ определен на столбце определяемого пользователем типа данных CLR, реализация этого типа должна поддерживать двоичную сортировку. Дополнительные сведения об определяемых пользователем типах данных CLR см. в разделе [Определяемые пользователем типы данных CLR](../../relational-databases/clr-integration-database-objects-user-defined-types/clr-user-defined-types.md).  
  
-   Столбцы, участвующие в связи по внешнему ключу, должны иметь одинаковую длину и масштаб.  
  
## <a name="default-definitions"></a>Определения DEFAULT  
  
-   Столбец может иметь только определение DEFAULT.  
  
-   Ограничение DEFAULT может содержать значения констант, функции, стандартные функции без параметров SQL или значение NULL. В следующей таблице приведены функции без параметров и возвращаемые ими по умолчанию значения в процессе выполнения инструкции INSERT.  
  
    |Функция без параметров SQL-92|Возвращенное значение|  
    |------------------------------|--------------------|  
    |CURRENT_TIMESTAMP|Текущие дата и время.|  
    |CURRENT_USER|Имя пользователя, выполняющего вставку.|  
    |SESSION_USER|Имя пользователя, выполняющего вставку.|  
    |SYSTEM_USER|Имя пользователя, выполняющего вставку.|  
    |Пользователь|Имя пользователя, выполняющего вставку.|  
  
-   *constant_expression* по умолчанию определение не может ссылаться на другой столбец в таблице или на другие таблицы, представления или хранимые процедуры.  
  
-   Определения DEFAULT нельзя создавать для столбцов с **timestamp** тип данных или столбцов со свойством IDENTITY.  
  
-   Определения DEFAULT нельзя создавать для столбцов с псевдонимами типов данных, если такой тип привязан к определенному по умолчанию объекту.  
  
## <a name="check-constraints"></a>Ограничения CHECK  
  
-   Столбец может содержать любое количество ограничений CHECK, а условие может включать несколько логических выражений, соединенных операторами AND и OR. При указании нескольких ограничений CHECK для столбца их проверка производится в порядке создания.  
  
-   Условие поиска должно возвращать логическое выражение и не может ссылаться на другую таблицу.  
  
-   Ограничение CHECK уровня столбца может ссылаться только на ограничиваемый столбец, а ограничение CHECK уровня таблицы — только на столбцы этой таблицы.  
  
     Правила и ограничения CHECK выполняют одну и ту же функцию проверки данных при выполнении инструкций INSERT и UPDATE.  
  
-   Если для столбца или столбцов задано правило либо одно или несколько ограничений CHECK, применяются все ограничения.  
  
-   Ограничения CHECK нельзя определять для **текст**, **ntext**, или **изображения** столбцов.  
  
## <a name="additional-constraint-information"></a>Дополнительные сведения об ограничениях  
  
-   Индекс, созданный для ограничения, не может быть удален с помощью инструкции DROP INDEX; необходимо удалить ограничение с помощью инструкции ALTER TABLE. Индекс, созданный для ограничения и используемый им, можно перестроить с помощью инструкции ALTER INDEX...REBUILD. Дополнительные сведения см. в статье [Реорганизация и перестроение индексов](../../relational-databases/indexes/reorganize-and-rebuild-indexes.md).  
  
-   Имена ограничений должны подчиняться правилам для [идентификаторы](../../relational-databases/databases/database-identifiers.md), за исключением того, что имя не может начинаться со знака номера (#). Если *constraint_name* — не указано имя, формируемое системой назначается ограничение. Имя ограничения отображается в любых сообщениях об ошибках, связанных с нарушением ограничения.  
  
-   При нарушении ограничения в инструкции INSERT, UPDATE или DELETE выполнение инструкции прекращается. Однако если параметр SET XACT_ABORT установлен в OFF, а инструкция является частью явной транзакции, выполнение этой транзакции продолжается. Если параметр SET XACT_ABORT установлен в ON, производится откат всей транзакции. Можно также использовать инструкцию ROLLBACK TRANSACTION с определением транзакции, проверив @@ERROR системная функция.  
  
-   Если присвоены значения ALLOW_ROW_LOCKS = ON и ALLOW_PAGE_LOCK = ON, при доступе к индексу допустимы блокировки на уровне строк, страниц и таблиц. Компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] выбирает соответствующую блокировку и может повышать уровень с блокировки строки или страницы до блокировки таблицы. Если присвоены значения ALLOW_ROW_LOCKS = OFF и ALLOW_PAGE_LOCK = OFF, при доступе к индексу допустима только блокировка на уровне таблиц.  
  
-   Если в таблице содержатся ограничения FOREIGN KEY или CHECK и триггеры, условия ограничений вычисляются перед выполнением триггера.  
  
 Для отчета, таблицы и ее столбцы, **sp_help** или **sp_helpconstraint**. Чтобы переименовать таблицу, используйте **sp_rename**. Для отчета о представлениях и хранимых процедур, которые зависят от таблицы, используется [sys.dm_sql_referenced_entities](../../relational-databases/system-dynamic-management-views/sys-dm-sql-referenced-entities-transact-sql.md) и [sys.dm_sql_referencing_entities](../../relational-databases/system-dynamic-management-views/sys-dm-sql-referencing-entities-transact-sql.md).  
  
## <a name="nullability-rules-within-a-table-definition"></a>Правила допустимости значения NULL в рамках определения таблицы  
 Допустимость значения NULL для столбца зависит от того, разрешено ли значение NULL в качестве допустимого значения данных этого столбца. Значение NULL не является нулем или пустым значением: NULL указывает, что запись не была произведена или было явно указано значение NULL; обычно оно означает, что значение неизвестно или неприменимо.  
  
 При создании или изменении таблицы с помощью инструкции CREATE TABLE или ALTER TABLE настройки базы данных и сеанса влияют на возможность типа данных, указанного в определении столбца, принимать значение NULL и могут переопределять ее. Рекомендуется всегда явно определять столбец как NULL или NOT NULL для невычисляемых столбцов или, если используется пользовательский тип данных, разрешать, чтобы для столбца применялась возможность, установленная для этого типа по умолчанию. Для разреженных столбцов всегда должно быть разрешено значение NULL.  
  
 Если возможность столбца принимать значение NULL не задана явно, она определяется согласно правилам, указанным в следующей таблице.  
  
|Тип данных столбца|Правило|  
|----------------------|----------|  
|Псевдоним типа данных|Компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] использует допустимость значений NULL, указанную при создании типа данных. Чтобы определить допустимость значений NULL по умолчанию для типа данных, используйте **sp_help**.|  
|CLR, определяемый пользователем тип данных|Допустимость значения NULL определяется в соответствии с определением столбца.|  
|Системный тип данных|Если для системного типа данных предусмотрен только один вариант, он и применяется. **Отметка времени** данных типа должны быть NOT NULL. Если любые параметры сеанса с помощью инструкции SET установлены в ON:<br />**ANSI_NULL_DFLT_ON** = ON, присваивается значение NULL.  <br />**ANSI_NULL_DFLT_OFF** = ON, не присваивается значение NULL.<br /><br /> Если настроены какие-либо параметры базы данных с помощью инструкции ALTER DATABASE:<br />**ANSI_NULL_DEFAULT_ON** = ON, присваивается значение NULL.  <br />**ANSI_NULL_DEFAULT_OFF** = ON, не присваивается значение NULL.<br /><br /> Чтобы просмотреть параметр базы данных ANSI_NULL_DEFAULT, используйте **sys.databases** представление каталога|  
  
 Если для сеанса не установлен ни один из параметров ANSI_NULL_DFLT, а база данных настроена по умолчанию (ANSI_NULL_DEFAULT = OFF), применяется установленное по умолчанию значение NOT NULL.  
  
 Если столбец является вычисляемым, допустимость значения NULL для него всегда определяется компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)] автоматически. Чтобы выяснить допустимость значений NULL для столбца этого типа, используйте функцию COLUMNPROPERTY со **AllowsNull** свойство.  
  
> [!NOTE]  
>  Как драйвер ODBC для SQL Server, так и поставщик OLE DB для SQL Server (Майкрософт) предусматривают по умолчанию значение параметра ANSI_NULL_DFLT_ON = ON. Пользователи ODBC и OLE DB могут настраивать этот параметр в источниках данных ODBC или с помощью установки атрибутов или свойств соединения в приложении.  
  
## <a name="data-compression"></a>Data Compression  
 В системных таблицах не может быть включено сжатие. При создании таблицы параметру сжатия данных присваивается значение NONE, если не указано иное. При указании списка секций или секции, выходящей за пределы диапазона, будет сформирована ошибка. Дополнительную информацию о сжатии данных см. в разделе [Сжатие данных](../../relational-databases/data-compression/data-compression.md).  
  
 Оценить состояние сжатия таблицы, индекса или секции можно с помощью хранимой процедуры [sp_estimate_data_compression_savings](../../relational-databases/system-stored-procedures/sp-estimate-data-compression-savings-transact-sql.md) .  
  
## <a name="permissions"></a>Permissions  
 Требует разрешения CREATE TABLE в базе данных и разрешения ALTER на схему, в которой создается таблица.  
  
 Если какие-либо столбцы в инструкции CREATE TABLE определены как принадлежащие к определяемому пользователем типу данных CLR, необходимо быть владельцем данного типа либо иметь разрешение REFERENCES на него.  
  
 Если какие-либо столбцы в инструкции CREATE TABLE имеют связанную коллекцию схем XML, необходимо быть владельцем этого набора схем или иметь разрешение REFERENCES на него.  
  
 Любой пользователь может создавать временные таблицы в базе данных tempdb.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-create-a-primary-key-constraint-on-a-column"></a>A. Создание ограничения PRIMARY KEY для столбца  
 В следующем примере показано определение ограничения PRIMARY KEY с кластеризованным индексом для столбца `EmployeeID` таблицы `Employee`. Поскольку имя ограничения не указано, оно будет подставлено системой.  
  
```  
CREATE TABLE dbo.Employee (EmployeeID int  
PRIMARY KEY CLUSTERED);  
```  
  
### <a name="b-using-foreign-key-constraints"></a>Б. Использование ограничений FOREIGN KEY  
 Ограничение FOREIGN KEY используется для ссылки на другую таблицу. Внешние ключи могут включать один или несколько столбцов. В следующем примере показано ограничение FOREIGN KEY с одним столбцом в таблице `SalesOrderHeader`, ссылающееся на таблицу `SalesPerson`. Для ограничения FOREIGN KEY с одним столбцом требуется только предложение REFERENCES.  
  
```  
SalesPersonID int NULL  
REFERENCES SalesPerson(SalesPersonID)  
```  
  
 Кроме того, предложение FOREIGN KEY можно применить явно и заново определить атрибут столбца. Обратите внимание, что имена столбцов в обеих таблицах могут различаться.  
  
```  
FOREIGN KEY (SalesPersonID) REFERENCES SalesPerson(SalesPersonID)  
```  
  
 Ограничения по ключам с несколькими столбцами создаются в виде табличных ограничений. В базе данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] таблица `SpecialOfferProduct` включает ограничение PRIMARY KEY с несколькими столбцами. В следующем примере показано, как обращаться к этому ключу из другой таблицы; задавать имя ограничения явно необязательно.  
  
```  
CONSTRAINT FK_SpecialOfferProduct_SalesOrderDetail FOREIGN KEY  
 (ProductID, SpecialOfferID)  
REFERENCES SpecialOfferProduct (ProductID, SpecialOfferID)  
```  
  
### <a name="c-using-unique-constraints"></a>В. Использование ограничений UNIQUE  
 Ограничения UNIQUE используются для указания уникальности непервичных ключевых столбцов. В следующем примере применяется ограничение уникальности столбца `Name` таблицы `Product`.  
  
```  
Name nvarchar(100) NOT NULL  
UNIQUE NONCLUSTERED  
```  
  
### <a name="d-using-default-definitions"></a>Г. Использование определений DEFAULT  
 Определения DEFAULT (вместе с инструкциями INSERT и UPDATE) позволяют указать значение по умолчанию, используемое, если значение не задано. Например, база данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] может включать таблицу уточняющих запросов, содержащую различные должности, которые могут занимать сотрудники компании. В столбце, описывающем каждую должность, значение символьной строки по умолчанию может содержать описание, отображаемое, если фактическое описание должности не было введено явно.  
  
```  
DEFAULT 'New Position - title not formalized yet'  
```  
  
 Кроме констант, определения DEFAULT могут включать функции. Следующий пример позволяет получить текущую дату для той или иной записи.  
  
```  
DEFAULT (getdate())  
```  
  
 Обработка функциями без параметров также может повысить целостность данных. Чтобы определить пользователя, вставившего строку, используйте функцию без параметров для USER. Не заключайте функции без параметров в скобки.  
  
```  
DEFAULT USER  
```  
  
### <a name="e-using-check-constraints"></a>Д. Использование ограничений CHECK  
 В следующем примере показано ограничение, применяемое к значениям, вводимым в столбец `CreditRating` таблицы `Vendor`. Ограничение не имеет имени.  
  
```  
CHECK (CreditRating >= 1 and CreditRating <= 5)  
```  
  
 В этом примере показано именованное ограничение вводимых в столбец таблицы символьных данных по шаблону.  
  
```  
CONSTRAINT CK_emp_id CHECK (emp_id LIKE   
'[A-Z][A-Z][A-Z][1-9][0-9][0-9][0-9][0-9][FM]'   
OR emp_id LIKE '[A-Z]-[A-Z][1-9][0-9][0-9][0-9][0-9][FM]')  
```  
  
 В этом примере указывается, что значения должны входить в заданный список или соответствовать заданному шаблону.  
  
```  
CHECK (emp_id IN ('1389', '0736', '0877', '1622', '1756')  
OR emp_id LIKE '99[0-9][0-9]')  
```  
  
### <a name="f-showing-the-complete-table-definition"></a>Е. Вывод на экран полного определения таблицы  
 В следующем примере выводятся полные определения таблицы со всеми определениями ограничений для таблицы `PurchaseOrderDetail`, созданной в базе данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]. Обратите внимание, что для выполнения этого образца схема таблицы заменяется на схему `dbo`.  
  
```  
CREATE TABLE dbo.PurchaseOrderDetail  
(  
    PurchaseOrderID int NOT NULL  
        REFERENCES Purchasing.PurchaseOrderHeader(PurchaseOrderID),  
    LineNumber smallint NOT NULL,  
    ProductID int NULL   
        REFERENCES Production.Product(ProductID),  
    UnitPrice money NULL,  
    OrderQty smallint NULL,  
    ReceivedQty float NULL,  
    RejectedQty float NULL,  
    DueDate datetime NULL,  
    rowguid uniqueidentifier ROWGUIDCOL  NOT NULL  
        CONSTRAINT DF_PurchaseOrderDetail_rowguid DEFAULT (newid()),  
    ModifiedDate datetime NOT NULL   
        CONSTRAINT DF_PurchaseOrderDetail_ModifiedDate DEFAULT (getdate()),  
    LineTotal  AS ((UnitPrice*OrderQty)),  
    StockedQty  AS ((ReceivedQty-RejectedQty)),  
    CONSTRAINT PK_PurchaseOrderDetail_PurchaseOrderID_LineNumber  
               PRIMARY KEY CLUSTERED (PurchaseOrderID, LineNumber)  
               WITH (IGNORE_DUP_KEY = OFF)  
)   
ON PRIMARY;  
```  
  
### <a name="g-creating-a-table-with-an-xml-column-typed-to-an-xml-schema-collection"></a>Ж. Создание таблицы со столбцом, приведенным к типу коллекции схем XML  
 В следующем примере создается таблица со столбцом `xml`, приведенным к типу коллекции схем XML `HRResumeSchemaCollection`. `DOCUMENT` Ключевое слово указывает, что каждый экземпляр `xml` в тип данных *column_name* может содержать только один элемент верхнего уровня.  
  
```  
CREATE TABLE HumanResources.EmployeeResumes   
   (LName nvarchar(25), FName nvarchar(25),   
    Resume xml( DOCUMENT HumanResources.HRResumeSchemaCollection) );  
```  
  
### <a name="h-creating-a-partitioned-table"></a>З. Создание секционированной таблицы  
 В следующем примере создается функция секционирования для разделения таблицы или индекса на четыре секции. Затем создается схема секционирования, определяющая файловые группы, в которых содержится каждая из четырех секций. Наконец, создается таблица, использующая схему секционирования. В примере предполагается, что в базе данных уже существуют файловые группы.  
  
```  
CREATE PARTITION FUNCTION myRangePF1 (int)  
    AS RANGE LEFT FOR VALUES (1, 100, 1000) ;  
GO  
  
CREATE PARTITION SCHEME myRangePS1  
    AS PARTITION myRangePF1  
    TO (test1fg, test2fg, test3fg, test4fg) ;  
GO  
  
CREATE TABLE PartitionTable (col1 int, col2 char(10))  
    ON myRangePS1 (col1) ;  
GO  
```  
  
 Секции назначаются на основе столбца `col1` таблицы `PartitionTable` следующими способами.  
  
|Файловая группа|test1fg|test2fg|test3fg|test4fg|  
|---------------|-------------|-------------|-------------|-------------|  
|**Секции**|1|2|3|4|  
|**Значения**|столбец 1 \<= 1|Col1 > 1 AND col1 \<= 100|Col1 > 100 AND col1 \<= 1000|col1 > 1000|  
  
### <a name="i-using-the-uniqueidentifier-data-type-in-a-column"></a>И. Использование типа данных uniqueidentifier в столбце  
 В следующем примере создается таблица со столбцом типа `uniqueidentifier`. В этом примере используется ограничение PRIMARY KEY для защиты таблицы от вставки пользователями повторяющихся значений, а также функция `NEWSEQUENTIALID()` в ограничении `DEFAULT` для указания значений для новых строк. К столбцу `uniqueidentifier` применяется свойство ROWGUIDCOL, чтобы на столбец можно было ссылаться с помощью ключевого слова $ROWGUID.  
  
```  
CREATE TABLE dbo.Globally_Unique_Data  
    (guid uniqueidentifier   
        CONSTRAINT Guid_Default DEFAULT   
        NEWSEQUENTIALID() ROWGUIDCOL,  
    Employee_Name varchar(60)  
    CONSTRAINT Guid_PK PRIMARY KEY (guid) );  
```  
  
### <a name="j-using-an-expression-for-a-computed-column"></a>К. Использование выражения для вычисляемого столбца  
 В следующем примере показано использование выражения (`(low + high)/2`) для вычисления столбца `myavg`.  
  
```  
CREATE TABLE dbo.mytable   
    ( low int, high int, myavg AS (low + high)/2 ) ;  
```  
  
### <a name="k-creating-a-computed-column-based-on-a-user-defined-type-column"></a>Л. Создание вычисляемого столбца на основе столбца определяемого пользователем типа  
 В следующем примере создается таблица с одним столбцом, имеющим определяемый пользовательским тип `utf8string`, и предполагается, что как сборка, содержащая данный тип, так и сам тип, уже созданы в текущей базе данных. Второй столбец определяется на основе `utf8string`и использует метод `ToString()` из **type(class)** `utf8string` для вычисления значения для столбца.  
  
```  
CREATE TABLE UDTypeTable   
    ( u utf8string, ustr AS u.ToString() PERSISTED ) ;  
```  
  
### <a name="l-using-the-username-function-for-a-computed-column"></a>М. Использование функции USER_NAME для вычисляемого столбца  
 В следующем примере используется функция `USER_NAME()` в столбце `myuser_name`.  
  
```  
CREATE TABLE dbo.mylogintable  
    ( date_in datetime, user_id int, myuser_name AS USER_NAME() ) ;  
```  
  
### <a name="m-creating-a-table-that-has-a-filestream-column"></a>Н. Создание таблицы со столбцом FILESTREAM  
 В следующем примере создается таблица со столбцом `FILESTREAM` `Photo`. Если таблица содержит один или более столбцов `FILESTREAM`, она должна содержать столбец `ROWGUIDCOL`.  
  
```  
CREATE TABLE dbo.EmployeePhoto  
    (  
    EmployeeId int NOT NULL PRIMARY KEY,  
    ,Photo varbinary(max) FILESTREAM NULL  
    ,MyRowGuidColumn uniqueidentifier NOT NULL ROWGUIDCOL  
        UNIQUE DEFAULT NEWID()  
    );  
```  
  
### <a name="n-creating-a-table-that-uses-row-compression"></a>О. О. Создание таблицы, использующей сжатие строк  
 В следующем примере создается таблица, использующая сжатие строк.  
  
```  
CREATE TABLE dbo.T1   
(c1 int, c2 nvarchar(200) )  
WITH (DATA_COMPRESSION = ROW);  
```  
  
 Дополнительные примеры сжатия данных, в разделе [сжатие данных](../../relational-databases/data-compression/data-compression.md).  
  
### <a name="o-creating-a-table-that-has-sparse-columns-and-a-column-set"></a>П. Создание таблицы с разреженными столбцами и набором столбцов  
 В следующих примерах показано создание таблицы с разреженным столбцом и таблицы с двумя разреженными столбцами и набором столбцов. В примерах используется основной синтаксис. Более сложные примеры см. в разделе [Использование разреженных столбцов](../../relational-databases/tables/use-sparse-columns.md) и [использование наборов столбцов](../../relational-databases/tables/use-column-sets.md).  
  
 В следующем примере создается таблица с разреженным столбцом.  
  
```  
CREATE TABLE dbo.T1  
    (c1 int PRIMARY KEY,  
    c2 varchar(50) SPARSE NULL ) ;  
```  
  
 В этом примере создается таблица с двумя разреженными столбцами и набором столбцов с именем `CSet`.  
  
```  
CREATE TABLE T1  
    (c1 int PRIMARY KEY,  
    c2 varchar(50) SPARSE NULL,  
    c3 int SPARSE NULL,  
    CSet XML COLUMN_SET FOR ALL_SPARSE_COLUMNS ) ;  
```  
  
### <a name="p-creating-a-system-versioned-disk-based-temporal-table"></a>Т. Создание с системным управлением версиями дисковой темпоральной таблицы  
   
  
**Применяется к**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] и [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].
  
 Создание темпоральной таблицы, связанной с новой таблицей журнала и способ создания темпоральной таблицы, связанной с существующей таблицей журнала в следующих примерах. Обратите внимание, что временная таблица должна иметь первичный ключ включен для таблицы включено для системы управления версиями. Примеры показан способ добавления или удаления системы управления версиями в существующей таблице в разделе системы управления версиями в [примеры](../../t-sql/statements/alter-table-transact-sql.md#Example_Top). Варианты использования, в разделе [временных таблицах](../../relational-databases/tables/temporal-tables.md).  
  
 В этом примере создается новая таблица с новой таблицей журнала.  
  
```  
CREATE TABLE Department   
(  
    DepartmentNumber char(10) NOT NULL PRIMARY KEY CLUSTERED,   
    DepartmentName varchar(50) NOT NULL,   
    ManagerID int  NULL,   
    ParentDepartmentNumber char(10) NULL,   
    SysStartTime datetime2 GENERATED ALWAYS AS ROW START HIDDEN NOT NULL,   
    SysEndTime datetime2 GENERATED ALWAYS AS ROW END HIDDEN NOT NULL,     
    PERIOD FOR SYSTEM_TIME (SysStartTime,SysEndTime)     
)  
WITH (SYSTEM_VERSIONING = ON);  
```  
  
 В этом примере создается новая таблица с существующей таблицей журнала.  
  
```  
  
--Existing table   
CREATE TABLE Department_History   
(  
    DepartmentNumber char(10) NOT NULL,   
    DepartmentName varchar(50) NOT NULL,   
    ManagerID int  NULL,   
    ParentDepartmentNumber char(10) NULL,   
    SysStartTime datetime2 NOT NULL,   
    SysEndTime datetime2 NOT NULL   
);  
--Temporal table  
CREATE TABLE Department   
(  
    DepartmentNumber char(10) NOT NULL PRIMARY KEY CLUSTERED,   
    DepartmentName varchar(50) NOT NULL,   
    ManagerID INT  NULL,   
    ParentDepartmentNumber char(10) NULL,   
    SysStartTime datetime2 GENERATED ALWAYS AS ROW START HIDDEN NOT NULL,   
    SysEndTime datetime2 GENERATED ALWAYS AS ROW END HIDDEN NOT NULL,     
    PERIOD FOR SYSTEM_TIME (SysStartTime,SysEndTime)    
)  
WITH   
    (SYSTEM_VERSIONING = ON   
        (HISTORY_TABLE = dbo.Department_History, DATA_CONSISTENCY_CHECK = ON )  
    );  
```  
  
### <a name="q-creating-a-system-versioned-memory-optimized-temporal-table"></a>У. Создание с системным управлением версиями оптимизированных для памяти темпоральной таблицы  
   
  
**Применяется к**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] и [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].
  
 В следующем примере демонстрируется создание с системным управлением версиями оптимизированных для памяти темпоральной таблицы связывается с новой таблицей журнала на диске.  
  
 В этом примере создается новая таблица с новой таблицей журнала.  
  
```  
CREATE SCHEMA History  
GO  
CREATE TABLE dbo.Department   
(  
    DepartmentNumber char(10) NOT NULL PRIMARY KEY CLUSTERED,   
    DepartmentName varchar(50) NOT NULL,   
    ManagerID int  NULL,   
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
  
 В этом примере создается новая таблица с существующей таблицей журнала.  
  
```  
  
--Existing table   
CREATE TABLE Department_History   
(  
    DepartmentNumber char(10) NOT NULL,   
    DepartmentName varchar(50) NOT NULL,   
    ManagerID int  NULL,   
    ParentDepartmentNumber char(10) NULL,   
    SysStartTime datetime2 NOT NULL,   
    SysEndTime datetime2 NOT NULL   
);  
--Temporal table  
CREATE TABLE Department   
(  
    DepartmentNumber char(10) NOT NULL PRIMARY KEY CLUSTERED,   
    DepartmentName varchar(50) NOT NULL,   
    ManagerID INT  NULL,   
    ParentDepartmentNumber char(10) NULL,   
    SysStartTime datetime2 GENERATED ALWAYS AS ROW START HIDDEN NOT NULL,   
    SysEndTime datetime2 GENERATED ALWAYS AS ROW END HIDDEN NOT NULL,     
    PERIOD FOR SYSTEM_TIME (SysStartTime,SysEndTime)    
)  
WITH   
    (SYSTEM_VERSIONING = ON   
        (HISTORY_TABLE = dbo.Department_History, DATA_CONSISTENCY_CHECK = ON )  
    );  
```  
  
### <a name="r-creating-a-table-with-encrypted-columns"></a>Ф. Создание таблицы с зашифрованными столбцами  
 В следующем примере создается таблица с двумя зашифрованных столбцов. Дополнительные сведения см. в разделе [Постоянное шифрование (компонент Database Engine)](../../relational-databases/security/encryption/always-encrypted-database-engine.md).  
  
```  
CREATE TABLE Customers (  
    CustName nvarchar(60)   
        ENCRYPTED WITH   
            (  
             COLUMN_ENCRYPTION_KEY = MyCEK,  
             ENCRYPTION_TYPE = RANDOMIZED,  
             ALGORITHM = 'AEAD_AES_256_CBC_HMAC_SHA_256'  
            ),   
    SSN varchar(11) COLLATE  Latin1_General_BIN2  
        ENCRYPTED WITH   
            (  
             COLUMN_ENCRYPTION_KEY = MyCEK,  
             ENCRYPTION_TYPE = DETERMINISTIC ,  
             ALGORITHM = 'AEAD_AES_256_CBC_HMAC_SHA_256'  
            ),   
    Age int NULL  
);  
```

### <a name="s-create-an-inline-filtered-index"></a>Х. Создать отфильтрованный индекс встроенной 
Создает таблицы с помощью встроенного отфильтрованного индекса.
  
  ```
  CREATE TABLE t1 
 (
      c1 int,
      index IX1  (c1) WHERE c1 > 0   
 )
GO
 ```
 
  
## <a name="see-also"></a>См. также:  
 [ALTER TABLE (Transact-SQL)](../../t-sql/statements/alter-table-transact-sql.md)   
 [COLUMNPROPERTY &#40; Transact-SQL &#41;](../../t-sql/functions/columnproperty-transact-sql.md)   
 [CREATE INDEX (Transact-SQL)](../../t-sql/statements/create-index-transact-sql.md)   
 [CREATE VIEW (Transact-SQL)](../../t-sql/statements/create-view-transact-sql.md)   
 [Типы данных (Transact-SQL)](../../t-sql/data-types/data-types-transact-sql.md)   
 [DROP INDEX &#40; Transact-SQL &#41;](../../t-sql/statements/drop-index-transact-sql.md)   
 [sys.dm_sql_referenced_entities (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-sql-referenced-entities-transact-sql.md)   
 [sys.dm_sql_referencing_entities (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-sql-referencing-entities-transact-sql.md)   
 [DROP TABLE &#40; Transact-SQL &#41;](../../t-sql/statements/drop-table-transact-sql.md)   
 [CREATE PARTITION FUNCTION (Transact-SQL)](../../t-sql/statements/create-partition-function-transact-sql.md)   
 [CREATE PARTITION SCHEME (Transact-SQL)](../../t-sql/statements/create-partition-scheme-transact-sql.md)   
 [CREATE TYPE (Transact-SQL)](../../t-sql/statements/create-type-transact-sql.md)   
 [EVENTDATA (Transact-SQL)](../../t-sql/functions/eventdata-transact-sql.md)   
 [sp_help (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-help-transact-sql.md)   
 [sp_helpconstraint &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-helpconstraint-transact-sql.md)   
 [sp_rename (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-rename-transact-sql.md)   
 [sp_spaceused &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-spaceused-transact-sql.md)  
  
  



