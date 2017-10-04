---
title: "Создание ИНДЕКСА COLUMNSTORE (Transact-SQL) | Документы Microsoft"
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
- CREATE_COLUMNSTORE_INDEX_TSQL
- COLUMNSTORE INDEX
- COLUMNSTORE_INDEX_TSQL
- CREATE CLUSTERED COLUMNSTORE INDEX
- COLUMNSTORE_TSQL
- CREATE NONCLUSTERED COLUMNSTORE INDEX
- CREATE_NONCLUSTERED_COLUMNSTORE_INDEX_TSQL
- CREATE COLUMNSTORE INDEX
- CREATE_CLUSTERED_COLUMNSTORE_INDEX_TSQL
- COLUMNSTORE
dev_langs:
- TSQL
helpviewer_keywords:
- index creation [SQL Server], columnstore indexes
- columnstore index, creating
- CREATE COLUMNSTORE INDEX statement
- CREATE INDEX statement
ms.assetid: 7e1793b3-5383-4e3d-8cef-027c0c8cb5b1
caps.latest.revision: 76
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 96ec352784f060f444b8adcae6005dd454b3b460
ms.openlocfilehash: 0fb8883678dad7a62cac9c2109b093ee79e27b27
ms.contentlocale: ru-ru
ms.lasthandoff: 09/27/2017

---

# <a name="create-columnstore-index-transact-sql"></a>CREATE COLUMNSTORE INDEX (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-all_md](../../includes/tsql-appliesto-ss2012-all-md.md)]

Преобразование таблицы rowstore в кластеризованный индекс или создайте некластеризованный индекс columnstore. Используйте индекс columnstore для эффективного выполнения оперативной аналитики в реальном времени рабочей нагрузки OLTP или повысить производительность запроса и сжатие данных для рабочих нагрузок хранилищ данных.  
  
> [!NOTE]  
>  Начиная с [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)], можно создать как кластеризованный индекс таблицы.   Больше не нужно создавать таблицу rowstore и преобразовать ее в кластеризованном индексе.  
  
Перейдите к примеры:  
-   [Примеры для преобразования таблицы rowstore в columnstore](../../t-sql/statements/create-columnstore-index-transact-sql.md#convert)  
-   [Примеры для некластеризованных индексов columnstore](../../t-sql/statements/create-columnstore-index-transact-sql.md#nonclustered)  
  
Перейдите к сценариям:  
-   [Индексы ColumnStore для операционной аналитики в реальном времени](../../relational-databases/indexes/get-started-with-columnstore-for-real-time-operational-analytics.md)  
-   [Индексы Сolumnstore для хранилищ данных](../../relational-databases/indexes/columnstore-indexes-data-warehouse.md)  
  
Подробнее:  
-   [Руководство по индексам ColumnStore](../../relational-databases/indexes/columnstore-indexes-overview.md)  
-   [Обзор возможностей индексов ColumnStore](../../relational-databases/indexes/columnstore-indexes-what-s-new.md)  
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
-- Syntax for SQL Server and Azure SQL Database  
  
-- Create a clustered columnstore index on disk-based table.  
CREATE CLUSTERED COLUMNSTORE INDEX index_name  
    ON [database_name. [schema_name ] . | schema_name . ] table_name  
    [ WITH ( < with_option> [ ,...n ] ) ]  
    [ ON <on_option> ]  
[ ; ]  
  
--Create a non-clustered columnstore index on a disk-based table.  
CREATE [NONCLUSTERED]  COLUMNSTORE INDEX index_name   
    ON [database_name. [schema_name ] . | schema_name . ] table_name   
        ( column  [ ,...n ] )  
    [ WHERE <filter_expression> [ AND <filter_expression> ] ]
    [ WITH ( < with_option> [ ,...n ] ) ]  
    [ ON <on_option> ]   
[ ; ]  
  
<with_option> ::=  
      DROP_EXISTING = { ON | OFF } -- default is OFF  
    | MAXDOP = max_degree_of_parallelism 
    | ONLINE = { ON | OFF } 
    | COMPRESSION_DELAY  = { 0 | delay [ Minutes ] }  
    | DATA_COMPRESSION = { COLUMNSTORE | COLUMNSTORE_ARCHIVE }  
      [ ON PARTITIONS ( { partition_number_expression | range } [ ,...n ] ) ]  
  
<on_option>::=  
      partition_scheme_name ( column_name )   
    | filegroup_name   
    | "default"   
  
<filter_expression> ::=  
      column_name IN ( constant [ ,...n ]  
    | column_name { IS | IS NOT | = | <> | != | > | >= | !> | < | <= | !< } constant  
  
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
CREATE CLUSTERED COLUMNSTORE INDEX index_name   
    ON [ database_name . [ schema_name ] . | schema_name . ] table_name  
    [ WITH ( DROP_EXISTING = { ON | OFF } ) ] --default is OFF  
[;]  
```  
  
## <a name="arguments"></a>Аргументы  
СОЗДАНИЕ КЛАСТЕРИЗОВАННОГО ИНДЕКСА COLUMNSTORE  
Создайте кластеризованный индекс, в котором все данные сжаты, хранящихся в столбце. Индекс включает все столбцы в таблице и сохраняет всю таблицу. Если существующая таблица является кучи или кластеризованного индекса, таблица была преобразована в кластеризованном индексе. Если таблица уже хранится в виде кластеризованного индекса columnstore, существующий индекс удаляется и перестраивается.  
  
*index_name*  
Указывает имя для нового индекса.  
  
Если в таблице уже есть кластеризованный индекс, можно указать то же имя, что и существующий индекс или удалить СУЩЕСТВУЮЩИЙ параметр можно использовать для указания нового имени.  
  
ON [*имя_базы_данных*. [*schema_name* ]. | *schema_name* . ] *имя_таблицы*  
   Задает одно-, двух- или трехкомпонентное имя таблицы, которая должна быть сохранена как кластеризованный индекс columnstore. Если таблица является кучей или кластеризованный индекс таблицы преобразуется из rowstore в ColumnStore. Если таблица уже columnstore, эта инструкция перестраивает кластеризованный индекс.  
  
на  
DROP_EXISTING = [OFF] | ON  
   DROP_EXISTING = ON позволяет удалить существующий кластеризованный индекс и создать новый индекс columnstore.  

   Значение по умолчанию DROP_EXISTING = OFF ожидает имя индекса совпадает с существующим именем. Возникает ошибка имеет индекс с указанным именем уже существует.  
  
MAXDOP = *max_degree_of_parallelism*  
   Переопределяет существующую конфигурацию максимальной степени параллелизма сервера на время выполнения этой операции с индексом. MAXDOP можно использовать для ограничения числа процессоров, используемых при параллельном выполнении планов. Максимальное число процессоров — 64.  
  
   *max_degree_of_parallelism* значения могут быть:  
   - 1 — подавляет создание параллельных планов.  
   - \>1 — ограничьте максимальное количество процессоров, используемых в параллельных операциях с индексами заданным или меньшим числом в зависимости от текущей рабочей нагрузки системы. Например, если MAXDOP = 4, число используемых процессоров, 4 или меньше.  
   - 0 (по умолчанию) — в зависимости от текущей рабочей нагрузки системы использует реальное или меньшее число процессоров.  
  
   Дополнительные сведения см. в разделе [Настройка параметра max degree of parallelism Server Configuration Option](../../database-engine/configure-windows/configure-the-max-degree-of-parallelism-server-configuration-option.md), и [Настройка параллельных операций с индексами](../../relational-databases/indexes/configure-parallel-index-operations.md).  
 
COMPRESSION_DELAY = **0** | *задержки* [минут]  
   Применяется к: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].

   Для таблицы на диске *задержки* указывает минимальное количество минут, должны оставаться в разностную группу строк, в состояние CLOSED в разностную группу строк, до SQL Server можно сжать в сжатую группу строк. Так как не отслеживания вставки и обновления таблиц на диске время в отдельных строках, SQL Server применяет задержка разностных групп строк в состояние CLOSED.  
   Значение по умолчанию — 0 минут.  
   Рекомендации по использованию COMPRESSION_DELAY, см. в разделе [начало работы с Columnstore для операционной аналитики в реальном времени](../../relational-databases/indexes/get-started-with-columnstore-for-real-time-operational-analytics.md).  
  
DATA_COMPRESSION = COLUMNSTORE | COLUMNSTORE_ARCHIVE  
   Применяется к: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].
Задает режим сжатия данных для указанной таблицы, номера секции или диапазона секций. Существуют следующие параметры выбора.   
COLUMNSTORE  
   COLUMNSTORE по умолчанию и задает для сжатия с применением сжатия columnstore большинство высокопроизводительных. Это типичный вариант.  
  
COLUMNSTORE_ARCHIVE  
   COLUMNSTORE_ARCHIVE дальнейшей сжатие таблицы или секции для меньшего размера. Используйте этот параметр для ситуаций, таких как архивация, требуется уменьшение размера хранилища и допускается увеличение затрат времени на сохранение и выборку.  
  
   Дополнительные сведения о сжатии см. в разделе [сжатие данных](../../relational-databases/data-compression/data-compression.md).  

ON  
   Параметры ON позволяют задавать параметры для хранения данных, такие как схема секционирования, конкретная файловая группа или файловая группа по умолчанию. Если параметр ON не указан, индекс использует параметры секционирования или файловой группы параметры существующей таблицы.  
  
   *partition_scheme_name* **(** *column_name* **)**  
   Задает схему секционирования для таблицы. Эта схема секционирования должна уже существовать в базе данных. Чтобы создать схему секционирования, в разделе [CREATE PARTITION SCHEME](../../t-sql/statements/create-partition-scheme-transact-sql.md).  
 
   *column_name* указывает столбец, по которому секционируется секционированного индекса. Этот столбец должен соответствовать типу данных, длине и точности аргумента секции функции, *partition_scheme_name* использует.  

   *filegroup_name*  
   Указывает файловую группу для хранения кластеризованного индекса columnstore. Если местоположение не указано и таблица не секционирована, индекс использует ту же файловую группу, что и базовая таблица или представление. Файловая группа должна существовать.  

   **«**по умолчанию**»**  
   Чтобы создать индекс в файловой группе по умолчанию, используйте «default» или [default].  
  
   Если указано значение «default» (по умолчанию), параметр QUOTED_IDENTIFIER должен иметь значение ON для текущего сеанса. QUOTED_IDENTIFIER по умолчанию равен ON. Дополнительные сведения см. в разделе [SET QUOTED_IDENTIFIER (Transact-SQL)](../../t-sql/statements/set-quoted-identifier-transact-sql.md).  
  
СОЗДАНИЕ ИНДЕКСА COLUMNSTORE [НЕКЛАСТЕРИЗОВАННЫЙ]  
Создать в памяти некластеризованный индекс columnstore в таблице rowstore хранятся в виде кучи или кластеризованного индекса. Индекс может иметь отфильтрованное условие и не должны включать все столбцы базовой таблицы. Индекс columnstore требуется достаточно места для хранения копии данных. Он может обновляться и обновляется по мере изменения базовой таблицы. Некластеризованный индекс columnstore в кластеризованном индексе позволяет аналитика в реальном времени.  
  
*index_name*  
   Указывает имя индекса. *index_name* должно быть уникальным в пределах таблицы, но не обязательно должны быть уникальными в пределах базы данных. Имена индексов должны соответствовать правилам [идентификаторы](../../relational-databases/databases/database-identifiers.md).  
  
 **(** *столбца* [ **,**... *n* ] **)**  
    Задает столбцы для хранения. Некластеризованный индекс columnstore является более 1024 столбцов.  
   Каждый столбец должен иметь поддерживаемый тип данных для индексов columnstore. В разделе [ограничения](../../t-sql/statements/create-columnstore-index-transact-sql.md#LimitRest) список поддерживаемых типов данных.  

ON [*имя_базы_данных*. [*schema_name* ]. | *schema_name* . ] *имя_таблицы*  
   Указывает одно-, двух- или трехкомпонентное имя таблицы, содержащей индекс.  

С ПОМОЩЬЮ ИНСТРУКЦИИ DROP_EXISTING = [OFF] | ON  
   DROP_EXISTING = ON существующий индекс удаляется и перестраивается. Указанное имя индекса должно совпадать с уже существующим индексом, но определение индекса может быть изменено. Например, можно указать другие столбцы или параметры индекса.
  
   DROP_EXISTING = OFF, выводится сообщение об ошибке, если индекс с указанным именем уже существует. Тип индекса не может быть изменен с помощью аргумента DROP_EXISTING. Для обратной совместимости синтаксиса аргумент WITH DROP_EXISTING эквивалентен аргументу WITH DROP_EXISTING = ON.  

MAXDOP = *max_degree_of_parallelism*  
   Переопределяет [Настройка параметра max degree of parallelism Server Configuration Option](../../database-engine/configure-windows/configure-the-max-degree-of-parallelism-server-configuration-option.md) параметр конфигурации в течение операции с индексами. MAXDOP можно использовать для ограничения числа процессоров, используемых при параллельном выполнении планов. Максимальное число процессоров — 64.  
  
   *max_degree_of_parallelism* значения могут быть:  
   - 1 — подавляет создание параллельных планов.  
   - \>1 — ограничьте максимальное количество процессоров, используемых в параллельных операциях с индексами заданным или меньшим числом в зависимости от текущей рабочей нагрузки системы. Например, если MAXDOP = 4, число используемых процессоров, 4 или меньше.  
   - 0 (по умолчанию) — в зависимости от текущей рабочей нагрузки системы использует реальное или меньшее число процессоров.  
  
   Дополнительные сведения см. в статье [Настройка параллельных операций с индексами](../../relational-databases/indexes/configure-parallel-index-operations.md).  
  
> [!NOTE]  
>  Параллельные операции с индексами доступны не во всех выпусках [!INCLUDE[msC](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Сведения о функциях, поддерживаемых различными выпусками [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], см. в статье [Возможности, поддерживаемые различными выпусками SQL Server 2016](../../sql-server/editions-and-supported-features-for-sql-server-2016.md).  
  
ONLINE = [ON | OFF]   
   Применяется к: [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)], в некластеризованные индексы columnstore только.
ON указывает, что некластеризованный индекс columnstore в оперативном и доступно новой копии индекса, для которого производится построение.

   ОТКЛЮЧЕНИЕ указывает, что индекс не доступны для использования во время создания новой копии. Поскольку это некластеризованный индекс, остается базовой таблицы, доступные только некластеризованный индекс columnstore не используется для обработки запросов до завершения новый индекс. 

COMPRESSION_DELAY = **0** | \<задержки > [минут]  
   Применяется к: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. 
  
   Задает нижнюю границу на продолжительность строки должны оставаться в разностную группу строк, прежде чем он подходит для миграции в сжатую группу строк. Например клиент можно сказать, что, если строка не содержит изменений в течение 120 минут, делает его подходящим для сжатием в формат хранения по столбцам. Для индекса columnstore для таблиц на диске, не отслеживать время при вставке или обновлении строки мы используйте дельта времени закрытия группы строк как прокси для строки. Значение по умолчанию-0 минут. Строка переносится в хранилище столбцов после 1 миллион строк накопленных в разностную группу строк, и она была отмечена как закрытые.  
  
DATA_COMPRESSION  
   Задает режим сжатия данных для указанной таблицы, номера секции или диапазона секций. Существуют следующие параметры выбора.  
COLUMNSTORE  
   Применяется к: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Применяется только к индексам columnstore, включая некластеризованные и кластеризованные индексы columnstore. COLUMNSTORE по умолчанию и задает для сжатия с применением сжатия columnstore большинство высокопроизводительных. Это типичный вариант.  
  
COLUMNSTORE_ARCHIVE  
   Применяется к: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].
Применяется только к индексам columnstore, включая некластеризованные и кластеризованные индексы columnstore. COLUMNSTORE_ARCHIVE дальнейшей сжатие таблицы или секции для меньшего размера. Это может использоваться для архивации или в других ситуациях, где требуется уменьшение объема пространства и допускается увеличение затрат времени на сохранение и выборку  
  
 Дополнительные сведения о сжатии см. в разделе [сжатие данных](../../relational-databases/data-compression/data-compression.md).  
  
ГДЕ \<filter_expression > [AND \<filter_expression >] применяется к: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].
  
   Вызывается предикат фильтра, этот параметр указывает столбцы, которые будут включены в индекс. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]создает отфильтрованную статистику для строк данных отфильтрованного индекса.  
  
   Предикат фильтра использует простую логику сравнения. Сравнения с помощью литералов NULL с операторами сравнения недопустимы. Вместо этого используются операторы IS NULL и IS NOT NULL.  
  
   Далее приведено несколько примеров использования предикатов фильтра для таблицы `Production.BillOfMaterials`:  
   `WHERE StartDate > '20000101' AND EndDate <= '20000630'`    
   `WHERE ComponentID IN (533, 324, 753)`  
   `WHERE StartDate IN ('20000404', '20000905') AND EndDate IS NOT NULL`  
   
   Рекомендации для отфильтрованных индексов см. в разделе [Create Filtered Indexes](../../relational-databases/indexes/create-filtered-indexes.md).  
  
ON  
   Эти параметры указывают файловые группы, для которой создается индекс.  
  
*partition_scheme_name* **(** *column_name* **)**  
   Указывает схему секционирования, которая определяет файловые группы, на которой сопоставлен секции секционированного индекса. Схема секционирования должна существовать в базе данных, выполнив [CREATE PARTITION SCHEME](../../t-sql/statements/create-partition-scheme-transact-sql.md). 
   *column_name* указывает столбец, по которому секционируется секционированного индекса. Этот столбец должен соответствовать типу данных, длине и точности аргумента секции функции, *partition_scheme_name* использует. *column_name* предназначен не только для столбцов в определении индекса. При секционировании индекса columnstore компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] добавляет столбец секционирования как столбец индекса, если этого столбца еще нет в списке.  
   Если *partition_scheme_name* или *файловой группы* не указано и таблица секционирована, индекс помещается в ту же схему секционирования, с помощью тем же столбцом секционирования, что и базовая таблица.  
   Индекс columnstore для секционированной таблицы должен быть выровнен по секциям.  
   Дополнительные сведения о секционировании индексов см. в разделе [секционированных таблиц и индексов](../../relational-databases/partitions/partitioned-tables-and-indexes.md).  

*filegroup_name*  
   Указывает имя файловой группы, в которой создается индекс. Если *filegroup_name* не указано и таблица не секционирована, индекс использует ту же файловую группу, что и базовая таблица. Файловая группа должна существовать.  
 
**«**по умолчанию**»**  
Создает заданный индекс в файловой группе, используемой по умолчанию.  
  
Слово «default» в этом контексте не является ключевым. Он представляет собой идентификатор файловой группы по умолчанию и должен иметь разделители, как в выражениях ON **»**по умолчанию**»** или ON **[**по умолчанию**]**. Если указано значение «default» (по умолчанию), параметр QUOTED_IDENTIFIER должен иметь значение ON для текущего сеанса. Это параметр по умолчанию. Дополнительные сведения см. в разделе [SET QUOTED_IDENTIFIER (Transact-SQL)](../../t-sql/statements/set-quoted-identifier-transact-sql.md).  
  
##  <a name="Permissions"></a> Разрешения  
 Требуется разрешение ALTER на таблицу.  
  
##  <a name="GenRemarks"></a>Общие замечания  
 Индекс columnstore могут создаваться для временной таблицы. После удаления таблицы или окончания сеанса индекс также уничтожается.  
 
## <a name="filtered-indexes"></a>Отфильтрованные индексы  
Отфильтрованный индекс является оптимизированным некластеризованным индексом, предназначенным для запросов, выбирающих небольшой процент строк таблицы. Чтобы проиндексировать часть данных таблицы, в нем используется предикат фильтра. Правильно составленный отфильтрованный индекс может увеличить скорость выполнения запроса, уменьшить стоимость хранения и обслуживания.  
  
### <a name="required-set-options-for-filtered-indexes"></a>Обязательные параметры SET для отфильтрованных индексов  
Параметры SET в столбце Required Value необходимы при возникновении любого из следующих условий.  
- Создание отфильтрованного индекса.  
- Операция INSERT, UPDATE, DELETE или MERGE изменяет данные в отфильтрованном индексе.  
- Отфильтрованный индекс используется оптимизатором запросов для создания плана запроса.  
  
    |Задание параметров|Обязательное значение|Значение сервера по умолчанию|По умолчанию<br /><br /> Значение OLE DB и ODBC|По умолчанию<br /><br /> Значение DB-Library|  
    |-----------------|--------------------|--------------------------|---------------------------------------|-----------------------------------|  
    |ANSI_NULLS|ON|ON|ON|OFF|  
    |ANSI_PADDING|ON|ON|ON|OFF|  
    |ANSI_WARNINGS*|ON|ON|ON|OFF|  
    |ARITHABORT|ON|ON|OFF|OFF|  
    |CONCAT_NULL_YIELDS_NULL|ON|ON|ON|OFF|  
    |NUMERIC_ROUNDABORT|OFF|OFF|OFF|OFF|  
    |QUOTED_IDENTIFIER|ON|ON|ON|OFF|   
  
     *Если уровень совместимости базы данных равен 90 или более, при установке параметра ANSI_WARNINGS в состояние ON параметр ARITHABORT также устанавливается в состояние ON. Если уровень совместимости базы данных установлен в состояние 80 или более раннее, то параметр ARITHABORT необходимо явным образом установить в состояние ON.  
  
 Если параметры SET неверны, может произойти следующее.  
  
-   Отфильтрованный индекс не будет создан.  
  
-   Компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] сформирует ошибку и выполнит откат любой инструкции INSERT, UPDATE, DELETE или MERGE, которая изменила значения данных в индексе.  
  
-   Оптимизатор запросов не учтет индекс в плане выполнения любой инструкции Transact-SQL.  
  
 Дополнительные сведения об отфильтрованных индексах см. в разделе [Create Filtered Indexes](../../relational-databases/indexes/create-filtered-indexes.md). 
  
##  <a name="LimitRest"></a> Ограничения  

**Каждый столбец в индекс columnstore должен иметь одно из следующих распространенных типов данных бизнеса:** 
-   DateTimeOffset [(  *n*  )]  
-   datetime2 [(  *n*  )]  
-   datetime  
-   smalldatetime  
-   date  
-   время [(  *n*  )]  
-   число с плавающей запятой [(  *n*  )]  
-   реальные [(  *n*  )]  
-   Decimal [( *точности* [ *, масштаб* ] **)** ]
-   числовые [( *точности* [ *, масштаб* ] **)** ]    
-   money  
-   smallmoney  
-   bigint  
-   int  
-   smallint  
-   tinyint  
-   bit  
-   nvarchar [(  *n*  )] 
-   nvarchar(max) (применяется к [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] и базы данных SQL Azure на premium ценовую категорию, кластеризованные индексы columnstore только)   
-   nchar [(  *n*  )]  
-   varchar [(  *n*  )]  
-   varchar(max) (применяется к [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] и базы данных SQL Azure на premium ценовую категорию, кластеризованные индексы columnstore только)
-   char [(  *n*  )]  
-   varbinary [(  *n*  )] 
-   varbinary (max) (применяется к [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] и базы данных SQL Azure на premium ценовую категорию, кластеризованные индексы columnstore только)
-   двоичные [(  *n*  )]  
-   uniqueidentifier (применяется к [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] и более поздние версии)
  
Если базовая таблица содержит столбец типа данных, который не поддерживается для индексов columnstore, необходимо исключить этот столбец из некластеризованный индекс columnstore.  
  
**Столбцы, использующие любой из следующих типов данных не может быть включен в индекс columnstore:**
-   ntext, text, и image  
-   nvarchar(max), varchar(max) и varbinary(max) (применяется к [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] и более ранние версии, так и некластеризованные индексы columnstore) 
-   rowversion (и timestamp)  
-   sql_variant  
-   Типы CLR (hierarchyid и пространственные типы)  
-   xml  
-   uniqueidentifier (применяется к [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)])  

**Некластеризованные индексы columnstore.**
-   Не более 1024 столбцов.  
-   Таблица с некластеризованным индексом columnstore может иметь ограничения уникальности, ограничения первичного ключа или ограничения внешнего ключа, но эти ограничения не могут быть включены в некластеризованный индекс columnstore.  
-   Не может быть создан для представления или индексированного представления.  
-   Не может содержать разреженный столбец.  
-   Не может быть изменен с помощью **ALTER INDEX** инструкции. Чтобы изменить некластеризованный индекс, следует удалить и повторно создать индекс columnstore. Можно использовать **ALTER INDEX** отключить и перестроить индекс columnstore.  
-   Невозможно создать с помощью **INCLUDE** ключевое слово.  
-   Не удается включить **ASC** или **DESC** ключевые слова для сортировки индексов. Индексы columnstore упорядочены в соответствии с алгоритмами сжатия. В результате сортировки можно потерять многие преимущества в производительности.  
-   Нельзя включать столбцы больших объектов (LOB) типа nvarchar(max), varchar(max) и varbinary(max) в некластеризованные индексы хранилищ столбцов. Только кластеризованные индексы columnstore поддерживают типы больших ОБЪЕКТОВ, начиная с версии [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] версии и базы данных SQL Azure, настроенной на ценовой категории "премиум". Обратите внимание, что предыдущие версии не поддерживают типы LOB в кластеризованные и некластеризованные индексы columnstore.


 **Индексы ColumnStore не может объединяться с помощью следующих средств:**  
-   вычисляемые столбцы; Начиная с SQL Server 2017 г., в кластеризованном индексе может содержать несохраняемым вычисляемым столбцом. Однако в 2017 г. SQL Server, кластеризованные индексы columnstore не может содержать материализованные вычисляемые столбцы и нельзя созданный некластеризованные индексы на вычисляемых столбцах. 
-   Сжатие страниц и строк, и **vardecimal** формат хранения (индекс columnstore уже сжат в другом формате.)  
-   Репликация  
-   Файловый поток

Нельзя использовать курсоры или триггеры в таблице с кластеризованным индексом columnstore. Это ограничение не применяется к некластеризованным индексам columnstore; можно использовать курсоры и триггеры для таблицы с некластеризованным индексом columnstore.

**Особые ограничения SQL Server 2014**  
Эти ограничения применяются только к SQL Server 2014. В этом выпуске мы представили обновленные кластеризованные индексы columnstore. Некластеризованные индексы columnstore были по-прежнему доступны только для чтения.  

-   Отслеживание изменений. Нельзя использовать отслеживание изменений с некластеризованных индексов columnstore (NCCI), так как они доступны только для чтения. Он может быть использовано для кластеризованных индексов columnstore (CCI).  
-   Система отслеживания измененных данных. Нельзя использовать изменит системы отслеживания измененных данных для некластеризованного индекса columnstore (NCCI), так как они доступны только для чтения. Он может быть использовано для кластеризованных индексов columnstore (CCI).  
-   Вторичная реплика для чтения. Кластеризованный кластеризованный индекс columnstore (CCI) недоступен из вторичной группы доступности всегда OnReadable.  Некластеризованный индекс columnstore (NCCI) можно открыть из доступных для чтения получателя.  
-   Несколько активных результирующих наборов (MARS). SQL Server 2014 использует режим MARS для соединения только для чтения для таблицы с индексом columnstore.    SQL Server 2014 не поддерживает режим MARS, для операций языка DML обработки данных для таблицы с индексом columnstore. В этом случае SQL Server завершает соединения и прерывает выполнение транзакции.  
  
 Сведения о преимуществах в производительности и ограничениях индексов columnstore см. в разделе [Общие сведения об индексах Columnstore](../../relational-databases/indexes/columnstore-indexes-overview.md).
  
##  <a name="Metadata"></a> Метаданные  
 Все столбцы в индексе columnstore хранятся в метаданных как включенные столбцы. Индекс columnstore не имеет ключевых столбцов. Эти системные представления предоставляют сведения об индексах columnstore.  
  
-   [sys.indexes (Transact-SQL)](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)  
-   [sys.index_columns (Transact-SQL)](../../relational-databases/system-catalog-views/sys-index-columns-transact-sql.md)  
-   [sys.partitions (Transact-SQL)](../../relational-databases/system-catalog-views/sys-partitions-transact-sql.md)  
-   [sys.column_store_segments (Transact-SQL)](../../relational-databases/system-catalog-views/sys-column-store-segments-transact-sql.md)  
-   [sys.column_store_dictionaries &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-column-store-dictionaries-transact-sql.md)  
-   [sys.column_store_row_groups &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-column-store-row-groups-transact-sql.md)  

##  <a name="convert"></a>Примеры для преобразования таблицы rowstore в columnstore  
  
### <a name="a-convert-a-heap-to-a-clustered-columnstore-index"></a>A. Преобразование кучи в кластеризованный индекс columnstore  
 В этом примере создается таблица как куча, затем преобразуется в кластеризованный индекс с именем columnstore cci_Simple. В результате таблица rowstore становится таблицей columnstore.  
  
```  
CREATE TABLE SimpleTable(  
    ProductKey [int] NOT NULL,   
    OrderDateKey [int] NOT NULL,   
    DueDateKey [int] NOT NULL,   
    ShipDateKey [int] NOT NULL);  
GO  
CREATE CLUSTERED COLUMNSTORE INDEX cci_Simple ON SimpleTable;  
GO  
```  
  
### <a name="b-convert-a-clustered-index-to-a-clustered-columnstore-index-with-the-same-name"></a>Б. Преобразование кластеризованного индекса в кластеризованный индекс columnstore с тем же именем.  
 В этом примере создается таблица с кластеризованным индексом, затем демонстрируется синтаксис преобразования кластеризованного индекса в кластеризованный индекс columnstore. В результате таблица rowstore становится таблицей columnstore.  
  
```  
CREATE TABLE SimpleTable (  
    ProductKey [int] NOT NULL,   
    OrderDateKey [int] NOT NULL,   
    DueDateKey [int] NOT NULL,   
    ShipDateKey [int] NOT NULL);  
GO  
CREATE CLUSTERED INDEX cl_simple ON SimpleTable (ProductKey);  
GO  
CREATE CLUSTERED COLUMNSTORE INDEX cl_simple ON SimpleTable  
WITH (DROP_EXISTING = ON);  
GO  
```  
  
### <a name="c-handle-nonclustered-indexes-when-converting-a-rowstore-table-to-a-columnstore-index"></a>В. Обрабатывайте некластеризованные индексы, при преобразовании таблицы rowstore в индекс columnstore.  
 В этом примере показано, как обрабатывать некластеризованные индексы, при преобразовании таблицы rowstore в индекс columnstore. На самом деле, начиная с версии [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] никаких специальных действий не требуется; [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] автоматически определяет и перестраивает некластеризованные индексы в новый кластеризованный индекс.  
  
 Если вы хотите удалить некластеризованных индексов, используйте инструкцию DROP INDEX до создания индекса columnstore. Параметр DROP EXISTING только удаляет кластеризованный индекс, который преобразуется. Он не удаляет некластеризованные индексы.  
  
 В [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] и [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)], не удалось создать некластеризованный индекс в индексе columnstore. В этом примере показано, как в предыдущих выпусках необходимо удалить некластеризованные индексы до создания индекса columnstore.  
  
```  
  
--Create the table for use with this example.  
CREATE TABLE SimpleTable (  
    ProductKey [int] NOT NULL,   
    OrderDateKey [int] NOT NULL,   
    DueDateKey [int] NOT NULL,   
    ShipDateKey [int] NOT NULL);  
GO  
  
--Create two nonclustered indexes for use with this example  
CREATE INDEX nc1_simple ON SimpleTable (OrderDateKey);  
CREATE INDEX nc2_simple ON SimpleTable (DueDateKey);   
GO  
  
--SQL Server 2012 and SQL Server 2014: you need to drop the nonclustered indexes  
--in order to create the columnstore index.   
  
DROP INDEX SimpleTable.nc1_simple;  
DROP INDEX SimpleTable.nc2_simple;  
  
--Convert the rowstore table to a columnstore index.  
CREATE CLUSTERED COLUMNSTORE INDEX cci_simple ON SimpleTable;   
GO  
  
```  
  
### <a name="d-convert-a-large-fact-table-from-rowstore-to-columnstore"></a>Г. Преобразование большой таблицы фактов из rowstore в columnstore  
 В этом примере показано, как преобразовать большую таблицу фактов из таблицы rowstore в таблицу columnstore.  
  
 Преобразование таблицы rowstore в таблицу columnstore.  
  
1.  Сначала создается небольшая таблица для использования в этом примере.  
  
    ```  
    --Create a rowstore table with a clustered index and a non-clustered index.  
    CREATE TABLE MyFactTable (  
        ProductKey [int] NOT NULL,  
        OrderDateKey [int] NOT NULL,  
         DueDateKey [int] NOT NULL,  
         ShipDateKey [int] NOT NULL )  
    )  
    WITH (  
        CLUSTERED INDEX ( ProductKey )  
    );  
  
    --Add a non-clustered index.  
    CREATE INDEX my_index ON MyFactTable ( ProductKey, OrderDateKey );  
    ```  
  
2.  Удалите все некластеризованные индексы из таблицы rowstore.  
  
    ```  
    --Drop all non-clustered indexes  
    DROP INDEX my_index ON MyFactTable;  
    ```  
  
3.  Удалить кластеризованный индекс.  
  
    -   Это следует делать только в том случае, если необходимо указать новое имя индекса при его преобразовании в кластеризованный индекс columnstore. Если не удалить кластеризованный индекс, то новый кластеризованный индекс columnstore имеет то же имя.  
  
        > [!NOTE]  
        >  Имя индекса может оказаться легче запомнить, если вы используете собственное имя. Все кластеризованные индексы rowstore используют имя по умолчанию, который является "ClusteredIndex_\<GUID >".  
  
    ```  
    --Process for dropping a clustered index.  
    --First, look up the name of the clustered rowstore index.  
    --Clustered rowstore indexes always use the DEFAULT name ‘ClusteredIndex_<GUID>’.  
    SELECT i.name   
    FROM sys.indexes i   
    JOIN sys.tables t  
    ON ( i.type_desc = 'CLUSTERED' ) WHERE t.name = 'MyFactTable';  
  
    --Drop the clustered rowstore index.  
    DROP INDEX ClusteredIndex_d473567f7ea04d7aafcac5364c241e09 ON MyDimTable;  
    ```  
  
4.  Преобразуйте таблицу rowstore в таблицу columnstore с кластеризованным индексом columnstore.  
  
    ```  
    --Option 1: Convert to columnstore and name the new clustered columnstore index MyCCI.  
    CREATE CLUSTERED COLUMNSTORE INDEX MyCCI ON MyFactTable;  
  
    --Option 2: Convert to columnstore and use the rowstore clustered   
    --index name for the columnstore clustered index name.  
    --First, look up the name of the clustered rowstore index.  
    SELECT i.name   
    FROM sys.indexes i  
    JOIN sys.tables t   
    ON ( i.type_desc = 'CLUSTERED' )  
    WHERE t.name = 'MyFactTable';  
  
    --Second, create the clustered columnstore index and   
    --Replace ClusteredIndex_d473567f7ea04d7aafcac5364c241e09  
    --with the name of your clustered index.  
    CREATE CLUSTERED COLUMNSTORE INDEX   
    ClusteredIndex_d473567f7ea04d7aafcac5364c241e09  
     ON MyFactTable  
    WITH DROP_EXISTING = ON;  
    ```  
  
### <a name="e-convert-a-columnstore-table-to-a-rowstore-table-with-a-clustered-index"></a>Д. Преобразование таблицы columnstore в таблицу rowstore с кластеризованным индексом  
 Чтобы преобразовать таблицу columnstore в таблицу rowstore с кластеризованным индексом, используйте инструкцию CREATE INDEX с параметром DROP_EXISTING.  
  
```  
CREATE CLUSTERED INDEX ci_MyTable   
ON MyFactTable  
WITH ( DROP EXISTING = ON );  
```  
  
### <a name="f-convert-a-columnstore-table-to-a-rowstore-heap"></a>Е. Преобразование таблицы columnstore в кучу rowstore  
 Чтобы преобразовать таблицу columnstore в кучу rowstore, просто удалите кластеризованный индекс columnstore.  
  
```  
DROP INDEX MyCCI   
ON MyFactTable;  
```  
  

### <a name="g-defragment-by-rebuilding-the-entire-clustered-columnstore-index"></a>Ж. Дефрагментация, перестроив весь кластеризованный индекс columnstore  
   Применяется к: SQL Server 2014  
  
 Есть два способа полностью перестроить кластеризованный индекс columnstore. Можно использовать создать КЛАСТЕРИЗОВАННЫЙ индекс COLUMNSTORE, или [ALTER INDEX &#40; Transact-SQL &#41; ](../../t-sql/statements/alter-index-transact-sql.md) с параметром REBUILD. Оба метода дают одинаковые результаты.  
  
> [!NOTE]  
>  Начиная с SQL Server 2016, используйте инструкцию ALTER INDEX REORGANIZE не перестраивая с помощью методов, описанных в этом примере.  
  
```  
--Determine the Clustered Columnstore Index name of MyDimTable.  
SELECT i.object_id, i.name, t.object_id, t.name   
FROM sys.indexes i   
JOIN sys.tables t  
ON (i.type_desc = 'CLUSTERED COLUMNSTORE')  
WHERE t.name = 'RowstoreDimTable';  
  
--Rebuild the entire index by using CREATE CLUSTERED INDEX.  
CREATE CLUSTERED COLUMNSTORE INDEX my_CCI   
ON MyFactTable  
WITH ( DROP_EXISTING = ON );  
  
--Rebuild the entire index by using ALTER INDEX and the REBUILD option.  
ALTER INDEX my_CCI  
ON MyFactTable  
REBUILD PARTITION = ALL  
WITH ( DROP_EXISTING = ON );  
  
```  
  
##  <a name="nonclustered"></a>Примеры для некластеризованных индексов columnstore  
  
### <a name="a-create-a-columnstore-index-as-a-secondary-index-on-a-rowstore-table"></a>A. Создание индекса columnstore в качестве вторичного индекса в таблице rowstore  
 В этом примере создается некластеризованный индекс columnstore в таблице rowstore. В этом случае можно создать только один индекс columnstore. Индекс columnstore требует дополнительного места, поскольку он содержит копию данных в таблице rowstore. В этом примере создается простая таблица и кластеризованный индекс и затем демонстрируется синтаксис создания некластеризованного индекса columnstore.  
  
```  
CREATE TABLE SimpleTable  
(ProductKey [int] NOT NULL,   
OrderDateKey [int] NOT NULL,   
DueDateKey [int] NOT NULL,   
ShipDateKey [int] NOT NULL);  
GO  
CREATE CLUSTERED INDEX cl_simple ON SimpleTable (ProductKey);  
GO  
CREATE NONCLUSTERED COLUMNSTORE INDEX csindx_simple  
ON SimpleTable  
(OrderDateKey, DueDateKey, ShipDateKey);  
GO  
```  
  
### <a name="b-create-a-simple-nonclustered-columnstore-index-using-all-options"></a>Б. Создание простого некластеризованного индекса columnstore с использованием всех параметров  
 В следующем примере демонстрируется синтаксис создания некластеризованного индекса columnstore с использованием всех параметров.  
  
```  
CREATE NONCLUSTERED COLUMNSTORE INDEX csindx_simple  
ON SimpleTable  
(OrderDateKey, DueDateKey, ShipDateKey)  
WITH (DROP_EXISTING =  ON,   
    MAXDOP = 2)  
ON "default"  
GO  
```  
  
 Более сложный пример с использованием секционированных таблиц, в разделе [Общие сведения об индексах Columnstore](../../relational-databases/indexes/columnstore-indexes-overview.md).  
  
### <a name="c-create-a-nonclustered-columnstore-index-with-a-filtered-predicate"></a>В. Создать некластеризованный индекс columnstore с отфильтрованном предикате  
 В следующем примере создается отфильтрованный некластеризованный индекс columnstore для таблицы Production.BillOfMaterials в [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] базы данных. Предикат фильтра может включать столбцы, не являющиеся ключевыми в отфильтрованном индексе. Предикат в примере выбирает только те строки, где EndDate не равно NULL.  
  
```  
IF EXISTS (SELECT name FROM sys.indexes  
    WHERE name = N'FIBillOfMaterialsWithEndDate'   
    AND object_id = OBJECT_ID(N'Production.BillOfMaterials'))  
DROP INDEX FIBillOfMaterialsWithEndDate  
    ON Production.BillOfMaterials;  
GO  
CREATE NONCLUSTERED COLUMNSTORE INDEX "FIBillOfMaterialsWithEndDate"  
    ON Production.BillOfMaterials (ComponentID, StartDate)  
    WHERE EndDate IS NOT NULL;  
  
```  
  
###  <a name="ncDML"></a> Г. Изменение данных в некластеризованном индексе columnstore  
   Применяется к: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] через [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)].
  
 После создания некластеризованного индекса columnstore в таблице нельзя непосредственно изменять данные в этой таблице. Запрос с помощью инструкции INSERT, UPDATE, DELETE или MERGE завершается неудачей и возвращает сообщение об ошибке. Для добавления или изменения данных в таблице можно воспользоваться одним из следующих способов.  
  
-   Отключить или удалить индекс columnstore. Затем можно обновлять данные в таблице. Если отключить индекс columnstore, то можно перестроить его после окончания обновления данных. Например:  
  
    ```  
    ALTER INDEX mycolumnstoreindex ON mytable DISABLE;  
    -- update mytable --  
    ALTER INDEX mycolumnstoreindex on mytable REBUILD  
    ```  
  
-   Загрузка данных в промежуточную таблицу, не имеющую индекса columnstore. Создание индекса columnstore в промежуточной таблице. Переключение промежуточной таблицы в пустую секцию главной таблицы.  
  
-   Переключение секции из таблицы с индексом columnstore в пустую промежуточную таблицу. Если в промежуточной таблице имеется индекс columnstore, отключите индекс columnstore. Выполните все обновления. Постройте (или перестройте) индекс columnstore. Переключитесь с промежуточной таблицы обратно на (теперь пустую) секцию главной таблицы.  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] и[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="a-change-a-clustered-index-to-a-clustered-columnstore-index"></a>A. Изменить кластеризованный индекс в кластеризованный индекс columnstore  
 С помощью инструкции CREATE CLUSTERED COLUMNSTORE INDEX с помощью инструкции DROP_EXISTING = ON, вы можете:  
  
-   Преобразовать кластеризованный индекс в кластеризованный индекс.  
  
-   Перестройте кластеризованный индекс.  
  
 В этом примере создается таблица xDimProduct как таблица rowstore с кластеризованным индексом, а затем использует создать КЛАСТЕРИЗОВАННЫЙ индекс COLUMNSTORE для изменения таблицы из таблицы rowstore в таблицу columnstore.  
  
```  
-- Uses AdventureWorks  
  
IF EXISTS (SELECT name FROM sys.tables  
    WHERE name = N'xDimProduct'  
    AND object_id = OBJECT_ID (N'xDimProduct'))  
DROP TABLE xDimProduct;  
  
--Create a distributed table with a clustered index.  
CREATE TABLE xDimProduct (ProductKey, ProductAlternateKey, ProductSubcategoryKey)  
WITH ( DISTRIBUTION = HASH(ProductKey),  
    CLUSTERED INDEX (ProductKey) )  
AS SELECT ProductKey, ProductAlternateKey, ProductSubcategoryKey FROM DimProduct;  
  
--Change the existing clustered index   
--to a clustered columnstore index with the same name.  
--Look up the name of the index before running this statement.  
CREATE CLUSTERED COLUMNSTORE INDEX <index_name>   
ON xdimProduct   
WITH ( DROP_EXISTING = ON );  
```  
  
### <a name="b-rebuild-a-clustered-columnstore-index"></a>Б. Перестроение кластеризованного индекса columnstore  
 Основываясь на предыдущем примере, в этом примере использует CREATE CLUSTERED COLUMNSTORE INDEX для перестроения существующего кластеризованного индекса columnstore вызывается cci_xDimProduct.  
  
```  
--Rebuild the existing clustered columnstore index.  
CREATE CLUSTERED COLUMNSTORE INDEX cci_xDimProduct   
ON xdimProduct   
WITH ( DROP_EXISTING = ON );  
```  
  
### <a name="c-change-the-name-of-a-clustered-columnstore-index"></a>В. Изменение имени в кластеризованном индексе  
 Чтобы изменить имя в кластеризованном индексе, удалите существующий кластеризованный индекс и затем заново создайте индекс с новым именем.  
  
 Рекомендуется только при выполнении этой операции с небольшая таблица или пустая таблица. Занимает много времени на удаление больших кластеризованный индекс и перестроить с другим именем.  
  
 С помощью cci_xDimProduct кластеризованный индекс columnstore из предыдущего примера, в этом примере удаляется кластеризованный индекс cci_xDimProduct и затем повторно создает кластеризованный индекс с именем mycci_xDimProduct.  
  
```  
--For illustration purposes, drop the clustered columnstore index.   
--The table continues to be distributed, but changes to a heap.  
DROP INDEX cci_xdimProduct ON xDimProduct;  
  
--Create a clustered index with a new name, mycci_xDimProduct.  
CREATE CLUSTERED COLUMNSTORE INDEX mycci_xDimProduct  
ON xdimProduct  
WITH ( DROP_EXISTING = OFF );  
```  
  
### <a name="d-convert-a-columnstore-table-to-a-rowstore-table-with-a-clustered-index"></a>Г. Преобразование таблицы columnstore в таблицу rowstore с кластеризованным индексом  
 Может возникнуть ситуация, для которого вы хотите удалить кластеризованный индекс и создать кластеризованный индекс. Это сохраняет таблицу в формате rowstore. Этот пример преобразует таблицу columnstore в таблицу rowstore с кластеризованным индексом с тем же именем. Данные будут утеряны. Все данные переносятся в таблицу rowstore и столбцы, перечисленные становится ключевых столбцов в кластеризованном индексе.  
  
```  
--Drop the clustered columnstore index and create a clustered rowstore index.   
--All of the columns are stored in the rowstore clustered index.   
--The columns listed are the included columns in the index.  
CREATE CLUSTERED INDEX cci_xDimProduct    
ON xdimProduct (ProductKey, ProductAlternateKey, ProductSubcategoryKey, WeightUnitMeasureCode)  
WITH ( DROP_EXISTING = ON);  
  
```  
  
### <a name="e-convert-a-columnstore-table-back-to-a-rowstore-heap"></a>Д. Преобразование таблицы columnstore обратно в кучу rowstore  
 Используйте [DROP INDEX (SQL Server PDW)](http://msdn.microsoft.com/en-us/f59cab43-9f40-41b4-bfdb-d90e80e9bf32) Чтобы удалить кластеризованный индекс и преобразовать таблицу в кучу rowstore. Этот пример преобразует cci_xDimProduct таблицу в кучу rowstore. Таблица по-прежнему распространяется, но хранится в виде кучи.  
  
```  
--Drop the clustered columnstore index. The table continues to be distributed, but changes to a heap.  
DROP INDEX cci_xdimProduct ON xdimProduct;  
```  


