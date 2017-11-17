---
title: "СОЗДАТЬ тип (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 04/11/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sql13.swb.sysdatatype.properties.f1
- CREATE TYPE
- TYPE_TSQL
- TYPE
- CREATE_TYPE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- UDTs [SQL Server], creating
- CLR user-defined types [SQL Server]
- user-defined table types [SQL Server]
- user-defined types [SQL Server], creating
- CREATE TYPE statement
- alias data types [SQL Server], creating
- data types [SQL Server], creating
ms.assetid: 2202236b-e09f-40a1-bbc7-b8cff7488905
caps.latest.revision: 92
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 4e7f411871d98fc6854b97478402567017d28222
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="create-type-transact-sql"></a>CREATE TYPE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Создает в текущей базе данных псевдоним типа данных или определяемый пользователем тип в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]. Реализация псевдонима типа данных основывается на собственном системном типе [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Определяемый пользователем тип реализуется с помощью класса сборки в [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] общеязыковая среда выполнения (CLR). Чтобы привязать определяемый пользователем тип к его реализации, сборки среды CLR, который содержит реализацию типа сначала должны быть зарегистрированы в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с помощью [CREATE ASSEMBLY](../../t-sql/statements/create-assembly-transact-sql.md).  
  
 Возможность выполнения CLR-кода в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] отключена по умолчанию. Создавать, изменять и удалять объекты базы данных, которые ссылаются на модули управляемого кода, но эти ссылки не будут выполнены в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Если [параметр clr enabled](../../database-engine/configure-windows/clr-enabled-server-configuration-option.md) включен с помощью [sp_configure](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md).  
 
> [!NOTE]  
>  В этом разделе рассматривается интеграция со средой CLR .NET Framework в SQL Server. Интеграция со средой CLR не применяется к Azure [!INCLUDE[ssSDS](../../includes/sssds-md.md)].
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
-- Disk-Based Type Syntax  
CREATE TYPE [ schema_name. ] type_name  
{   
    FROM base_type   
    [ ( precision [ , scale ] ) ]  
    [ NULL | NOT NULL ]   
  | EXTERNAL NAME assembly_name [ .class_name ]   
  | AS TABLE ( { <column_definition> | <computed_column_definition> }  
        [ <table_constraint> ] [ ,...n ] )    
} [ ; ]  
  
<column_definition> ::=  
column_name <data_type>  
    [ COLLATE collation_name ]   
    [ NULL | NOT NULL ]  
    [   
        DEFAULT constant_expression ]   
      | [ IDENTITY [ ( seed ,increment ) ]   
    ]  
    [ ROWGUIDCOL ] [ <column_constraint> [ ...n ] ]   
  
<data type> ::=   
[ type_schema_name . ] type_name   
    [ ( precision [ , scale ] | max |   
                [ { CONTENT | DOCUMENT } ] xml_schema_collection ) ]   
  
<column_constraint> ::=   
{     { PRIMARY KEY | UNIQUE }   
        [ CLUSTERED | NONCLUSTERED ]   
        [   
            WITH ( <index_option> [ ,...n ] )   
        ]  
  | CHECK ( logical_expression )   
}   
  
<computed_column_definition> ::=  
  
column_name AS computed_column_expression   
[ PERSISTED [ NOT NULL ] ]  
[   
    { PRIMARY KEY | UNIQUE }  
        [ CLUSTERED | NONCLUSTERED ]  
        [   
            WITH ( <index_option> [ ,...n ] )  
        ]  
    | CHECK ( logical_expression )   
]   
  
<table_constraint> ::=  
{   
    { PRIMARY KEY | UNIQUE }   
        [ CLUSTERED | NONCLUSTERED ]   
    ( column [ ASC | DESC ] [ ,...n ] )   
        [   
    WITH ( <index_option> [ ,...n ] )   
        ]  
    | CHECK ( logical_expression )   
}   
  
<index_option> ::=  
{  
    IGNORE_DUP_KEY = { ON | OFF }  
}  
```  
  
```  
-- Memory-Optimized Table Type Syntax  
CREATE TYPE [schema_name. ] type_name  
AS TABLE ( { <column_definition> }  
    |  [ <table_constraint> ] [ ,... n ]    
    | [ <table_index> ] [ ,... n ]    } )
    [ WITH ( <table_option> [ ,... n ] ) ]  
 [ ; ]  
  
<column_definition> ::=  
column_name <data_type>  
    [ COLLATE collation_name ]   [ NULL | NOT NULL ]    [  
      [ IDENTITY [ (1 , 1) ]  
    ]  
    [ <column_constraint> [ ... n ] ]    [ <column_index> ]  
  
<data type> ::=  
 [type_schema_name . ] type_name [ (precision [ , scale ]) ]  
  
<column_constraint> ::=  
{ PRIMARY KEY {   NONCLUSTERED HASH WITH (BUCKET_COUNT = bucket_count) 
                | NONCLUSTERED } }  
  
< table_constraint > ::=  
{ PRIMARY KEY { NONCLUSTERED HASH (column [ ,... n ] ) 
                   WITH (BUCKET_COUNT = bucket_count) 
               | NONCLUSTERED  (column [ ASC | DESC ] [ ,... n ] )  } }  
  
<column_index> ::=  
  INDEX index_name  
{ { [ NONCLUSTERED ] HASH WITH (BUCKET_COUNT = bucket_count) 
     | NONCLUSTERED } }  
  
< table_index > ::=  
  INDEX constraint_name  
{ { [ NONCLUSTERED ] HASH (column [ ,... n ] ) WITH (BUCKET_COUNT = bucket_count) 
 |  [NONCLUSTERED]  (column [ ASC | DESC ] [ ,... n ] )} }  
  
<table_option> ::=  
{  
    [MEMORY_OPTIMIZED = {ON | OFF}]  
}  
```  
  
## <a name="arguments"></a>Аргументы  
 *schema_name*  
 Имя схемы, к которой относится псевдоним типа данных или определяемый пользователем тип данных.  
  
 *Функция TYPE_NAME*  
 Имя псевдонима типа данных или определяемого пользователем типа данных. Имена типов должны соответствовать правилам для [идентификаторы](../../relational-databases/databases/database-identifiers.md).  
  
 *base_type*  
 — [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Указан тип данных, на котором основан тип данных псевдонима. *base_type* — **sysname**, без значения по умолчанию и может принимать одно из следующих значений:  
  
|||||  
|-|-|-|-|  
|**bigint**|**двоичный (**  *n*  **)**|**bit**|**char (**  *n*  **)**|  
|**date**|**datetime**|**datetime2**|**datetimeoffset**|  
|**decimal**|**float**|**image**|**int**|  
|**money**|**nchar (**  *n*  **)**|**ntext**|**numeric**|  
|**nvarchar (**  *n*  &#124; **max)**|**real**|**smalldatetime**|**smallint**|  
|**smallmoney**|**sql_variant**|**text**|**time**|  
|**tinyint**|**uniqueidentifier**|**varbinary (**  *n*  &#124; **max)**|**varchar (**  *n*  &#124; **max)**|  
  
 *base_type* может быть также синонимом любого типа данных, сопоставляемого одному из этих системных типов данных.  
  
 *precision*  
 Для **десятичное** или **числовое**, неотрицательное целое число, которое указывает на максимальное общее число десятичных разрядов, которые могут быть сохранены, слева и справа от десятичной запятой. Дополнительные сведения см. в разделе [decimal и numeric &#40; Transact-SQL &#41; ](../../t-sql/data-types/decimal-and-numeric-transact-sql.md).  
  
 *масштаб*  
 Для **десятичное** или **числовое**, неотрицательное целое число, которое указывает максимальное количество десятичных разрядов, которые могут храниться справа от десятичной запятой, и он должен быть меньше или равно точности . Дополнительные сведения см. в разделе [decimal и numeric &#40; Transact-SQL &#41; ](../../t-sql/data-types/decimal-and-numeric-transact-sql.md).  
  
 **ЗНАЧЕНИЕ NULL** | НЕ NULL  
 Указывает, может ли данный тип иметь значение NULL. Если не указано иное, по умолчанию принимается значение NULL.  
  
 *assembly_name*  
 **Область применения**: начиная с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Указывает [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] сборки, которая ссылается на реализацию определяемого пользователем типа в среде CLR. *assembly_name* должно соответствовать существующей сборке в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в текущей базе данных.  
  
> [!NOTE]  
>  Параметр EXTERNAL_NAME недоступен в автономной базе данных.  
  
 **[.** *class_name***]**   
 **Область применения**: начиная с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Задает класс сборки, реализующей определяемый пользователем тип. *class_name* должен быть допустимым идентификатором и существовать как класс в сборке с видимостью сборки. *class_name* с учетом регистра, независимо от параметров сортировки базы данных и должен точно соответствовать имени класса в соответствующей сборке. Имя класса может быть именем пространства имен, заключенных в квадратные скобки (**[]**) Если язык программирования, который используется для написания класса используется концепция пространств имен, например C#. Если *class_name* не указан, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] оно интерпретируется таким же, как *type_name*.  
  
 \<column_definition >  
 Определяет столбцы для определяемого пользователем табличного типа.  
  
 \<Тип данных >  
 Определяет тип данных в столбце для определяемого пользователем табличного типа. Дополнительные сведения о типах данных см. в разделе [типы данных &#40; Transact-SQL &#41; ](../../t-sql/data-types/data-types-transact-sql.md). Дополнительные сведения о таблицах см. в разделе [CREATE TABLE &#40; Transact-SQL &#41; ](../../t-sql/statements/create-table-transact-sql.md).  
  
 \<column_constraint >  
 Определяет ограничения столбца для определяемого пользователем табличного типа. Из ограничений поддерживаются PRIMARY KEY, UNIQUE и CHECK. Дополнительные сведения о таблицах см. в разделе [CREATE TABLE &#40; Transact-SQL &#41; ](../../t-sql/statements/create-table-transact-sql.md).  
  
 \<computed_column_definition >  
 Определяет выражение вычисляемого столбца в качестве столбца в определяемом пользователем табличном типе. Дополнительные сведения о таблицах см. в разделе [CREATE TABLE &#40; Transact-SQL &#41; ](../../t-sql/statements/create-table-transact-sql.md).  
  
 \<table_constraint >  
 Определяет ограничение таблицы на основе определяемого пользователем табличного типа. Из ограничений поддерживаются PRIMARY KEY, UNIQUE и CHECK.  
  
 \<index_option >  
 Определяет реакцию на ошибку, возникшую из-за дублирования значений ключа при вставке нескольких строк в уникальный кластеризованный или уникальный некластеризованный индекс. Дополнительные сведения о параметрах индекса см. в разделе [CREATE INDEX &#40; Transact-SQL &#41; ](../../t-sql/statements/create-index-transact-sql.md).  
  
 INDEX  
 Индексы столбцов и таблиц необходимо указывать в составе инструкции CREATE TABLE. DROP INDEX и CREATE INDEX не поддерживаются для таблиц, оптимизированных для памяти.  
  
 MEMORY_OPTIMIZED  
 **Применяется к**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] и [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].  
  
 Указывает, является ли тип таблицы оптимизированным для памяти. Этот параметр по умолчанию выключен. Таблица (тип) не является таблицей (типом), оптимизированной для памяти. Оптимизированные для памяти типы таблицы — это оптимизированные для памяти пользовательские таблицы, схемы которых, как и схемы других пользовательских таблиц, сохраняются на диске.  
  
 BUCKET_COUNT  
 **Применяется к**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] и [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].  
  
 Отображает число контейнеров, которые необходимо создать в хэш-индексе. Максимальное значение для параметра BUCKET_COUNT в хэш-индексах составляет 1 073 741 824. Дополнительные сведения о подсчете числа контейнеров см. в разделе [индексы для оптимизированных для памяти таблиц](../../relational-databases/in-memory-oltp/indexes-for-memory-optimized-tables.md). *bucket_count* аргумент является обязательным.  
  
 HASH  
 **Применяется к**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] и [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].  
  
 Указывает, что был создан индекс HASH. Хэш-индексы поддерживаются только в таблицах, оптимизированных для памяти.  
  
## <a name="remarks"></a>Замечания  
 Класс сборки, которая ссылается на *assembly_name*, и его методы должны удовлетворять всем требованиям к реализации определяемых пользователем типов в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Дополнительные сведения об этих требованиях см. в разделе [определяемые пользователем типы](../../relational-databases/clr-integration-database-objects-user-defined-types/clr-user-defined-types.md).  
  
 К числу дополнительных соображений относятся следующие:  
  
-   данный класс может иметь перегруженные методы, но эти методы могут вызываться только из управляемого кода, а не с помощью языка [!INCLUDE[tsql](../../includes/tsql-md.md)];  
  
-   Любые статические члены должны объявляться как **const** или **readonly** Если *assembly_name* имеет значение SAFE или EXTERNAL_ACCESS.  
  
 Внутри базы данных может существовать только один определяемый пользователем тип, зарегистрированный на основе любого указанного типа, который был загружен в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] из CLR. Если определяемый пользователем тип создается на основе типа CLR, для которого в этой базе данных уже существует пользовательский тип, инструкция CREATE TYPE вызывает сбой. Это ограничение необходимо для того, чтобы избежать неоднозначности при разрешении типа SQL Type, если тип CLR может соответствовать более чем одному определяемому пользователем типу.  
  
 Если любой метод мутатора в типе не возвращает *void*, инструкция CREATE TYPE не выполняется.  
  
 Чтобы внести изменения в определяемый пользователем тип, нужно удалить этот тип с помощью инструкции DROP TYPE и затем снова создать его.  
  
 В отличие от определяемых пользователем типов, которые создаются с помощью **sp_addtype**, **открытый** роли базы данных не предоставляется автоматически разрешение REFERENCES на типы, которые создаются с помощью инструкции CREATE TYPE. Это разрешение должно предоставляться отдельно.  
  
 В определяемых пользователем табличных типов, структурированный определяемых пользователем типов, используемых в *column_name* \<тип данных > являются частью области схемы базы данных, в которой определен тип таблицы. Чтобы получить доступ к определяемым пользователем структурированным типам в другой области базы данных, используйте двухкомпонентные имена.  
  
 В определяемых пользователем табличных типах первичный ключ на вычисляемых столбцах должен иметь атрибуты PERSISTED и NOT NULL.  
  
## <a name="memory-optimized-table-types"></a>Оптимизированные для памяти типы таблиц  
 Начиная с версии [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)], обработка данных в типе таблицы может выполняться в основной памяти, но не на диске. Дополнительные сведения см. в разделе [In-Memory OLTP (оптимизация в памяти)](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md). Примеры кода, демонстрирующий создание оптимизированных для памяти табличные типы см. в разделе [создание таблиц, оптимизированных для памяти и в собственном коде хранимых процедур, скомпилированных в](../../relational-databases/in-memory-oltp/creating-a-memory-optimized-table-and-a-natively-compiled-stored-procedure.md).  
  
## <a name="permissions"></a>Permissions  
 Требует разрешения CREATE TYPE в текущей базе данных и разрешения ALTER для схемы *schema_name*. Если аргумент *schema_name* не указан, в действие вступают принимаемые по умолчанию правила разрешения имен с целью определения схемы для текущего пользователя. Если *assembly_name* указан, пользователь должен владеть сборкой, или иметь разрешение REFERENCES на него.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-creating-an-alias-type-based-on-the-varchar-data-type"></a>A. Создание псевдонима на базе типа данных varchar  
 В следующем примере создается псевдоним на базе определенного в системе типа данных `varchar`.  
  
```  
CREATE TYPE SSN  
FROM varchar(11) NOT NULL ;  
```  
  
### <a name="b-creating-a-user-defined-type"></a>Б. Создание определяемого пользователем типа  
 В следующем примере создается тип `Utf8String` , ссылается на класс `utf8string` в сборке `utf8string`. Перед тем как приступить к созданию этого типа, сборка `utf8string` регистрируется в локальной базе данных. Замените двоичную часть инструкции CREATE ASSEMBLY на допустимое описание.  
  
**Область применения**: начиная с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
```  
CREATE ASSEMBLY utf8string  
AUTHORIZATION [dbi]   
FROM 0x4D... ;  
GO  
CREATE TYPE Utf8String   
EXTERNAL NAME utf8string.[Microsoft.Samples.SqlServer.utf8string] ;  
GO  
```  
  
### <a name="c-creating-a-user-defined-table-type"></a>В. Создание определяемого пользователем табличного типа  
 В следующем примере создается определяемый пользователем табличный тип, который имеет два столбца. Дополнительные сведения о том, как создание и использование возвращающих табличные значения параметров см. в разделе [использование возвращающих табличные значения параметры &#40; компонент Database Engine &#41;](../../relational-databases/tables/use-table-valued-parameters-database-engine.md).  
  
```  
CREATE TYPE LocationTableType AS TABLE   
    ( LocationName VARCHAR(50)  
    , CostRate INT );  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [СОЗДАТЬ СБОРКУ &#40; Transact-SQL &#41;](../../t-sql/statements/create-assembly-transact-sql.md)   
 [Тип удаления &#40; Transact-SQL &#41;](../../t-sql/statements/drop-type-transact-sql.md)   
 [EVENTDATA (Transact-SQL)](../../t-sql/functions/eventdata-transact-sql.md)  
  
  

