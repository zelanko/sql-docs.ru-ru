---
title: CREATE EXTERNAL TABLE AS SELECT (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 08/10/2017
ms.prod_service: sql-data-warehouse, pdw
ms.reviewer: ''
ms.service: sql-data-warehouse
ms.suite: sql
ms.component: t-sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- CREATE EXTERNAL TABLE AS SELECT
- CREATE_EXTERNAL_TABLE_AS_SELECT
- CREATE EXTERNAL TABLE AS SELECT_TSQL
helpviewer_keywords:
- External, table
- PolyBase, external table
- External, table create as select
- PolyBase, create table as select
ms.assetid: 32dfe254-6df7-4437-bfd6-ca7d37557b0a
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 74dc570a61b33aa6b6a2718bde3c927e6eabb1a7
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2018
ms.locfileid: "38017514"
---
# <a name="create-external-table-as-select-transact-sql"></a>CREATE EXTERNAL TABLE AS SELECT (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Создает внешнюю таблицу, а затем параллельно экспортирует результаты инструкции SELECT [!INCLUDE[tsql](../../includes/tsql-md.md)] в Hadoop или хранилище BLOB-объектов Azure.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL (Transact-SQL)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
CREATE EXTERNAL TABLE [ [database_name  . [ schema_name ] . ] | schema_name . ] table_name   
    WITH (   
        LOCATION = 'hdfs_folder',  
        DATA_SOURCE = external_data_source_name,  
        FILE_FORMAT = external_file_format_name  
        [ , <reject_options> [ ,...n ] ]  
    )  
    AS <select_statement>  
[;]  
  
<reject_options> ::=  
{  
    | REJECT_TYPE = value | percentage  
    | REJECT_VALUE = reject_value  
    | REJECT_SAMPLE_VALUE = reject_sample_value  
}  
  
<select_statement> ::=  
    [ WITH <common_table_expression> [ ,...n ] ]  
    SELECT <select_criteria>  
```  
  
## <a name="arguments"></a>Аргументы  
 [ [ *database_name* . [ *schema_name* ] . ] | *schema_name* . ] *table_name*  
 Имя создаваемой в базе данных таблицы, состоящее из одной, двух или трех частей. Для внешней таблицы в реляционной базе данных сохраняются только метаданные таблицы.  
  
 LOCATION =  '*hdfs_folder*'  
 Указывает место записи результатов инструкции SELECT во внешнем источнике данных. Расположение является именем папки и может включать путь относительно корневой папки кластера Hadoop или хранилища BLOB-объектов Azure.  PolyBase создаст путь и папку, если эти объекты еще не существуют.  
  
 Внешние файлы записываются в папку *hdfs_folder* и получают имена вида *QueryID_date_time_ID.format*, где *ID* — это нарастающий идентификатор, а *format* — это формат экспортированных данных. Пример: QID776_20160130_182739_0.orc.  
  
 DATA_SOURCE = *external_data_source_name*  
 Задает имя объекта внешнего источника данных, которое содержит расположение, где хранятся или будут храниться внешние данные. Это расположение — кластер Hadoop или хранилище BLOB-объектов Azure. Для создания внешнего источника данных используйте инструкцию [CREATE EXTERNAL DATA SOURCE (Transact-SQL)](../../t-sql/statements/create-external-data-source-transact-sql.md).  
  
 FILE_FORMAT = *external_file_format_name*  
 Задает имя объекта формата внешнего файла, который хранит формат внешнего файла данных. Чтобы создать формат внешнего файла, используйте [CREATE EXTERNAL FILE FORMAT (Transact-SQL)](../../t-sql/statements/create-external-file-format-transact-sql.md).  
  
 Параметры отклонения  
 Параметры отклонения не применяются в момент выполнения инструкции CREATE EXTERNAL TABLE AS SELECT. Вместо этого они указаны здесь, чтобы база данных могла использовать их позже, при импорте данных из внешней таблицы. Позже, когда инструкция CREATE TABLE AS SELECT выбирает данные из внешней таблицы, базы данных будет использовать параметры отклонения, чтобы определить число и процент строк, которые, возможно, не удастся импортировать до завершения импорта.  
  
 REJECT_VALUE = *reject_value*  
 Задает значение или процент строк, которые, возможно, не удастся импортировать до завершения в базе данных операции импорта.  
  
 REJECT_TYPE = **value** | percentage  
 Уточняет, указан параметр REJECT_VALUE как литеральное значение или процент.  
  
 value  
 REJECT_VALUE указан в виде литерала, а не в процентах.  База данных прекратит импортировать строки из внешнего файла данных, когда число строк с ошибкой превысит *reject_value*.  
  
 Например, если REJECT_VALUE = 5 и REJECT_TYPE = value, база данных перестанет импортировать строки после сбоя импорта пяти строк.  
  
 процент  
 REJECT_VALUE указывается в процентах, а не в виде литерала. База данных прекратит импортировать строки из внешнего файла данных, когда *процент* строк с ошибкой превысит *reject_value*. Процент отклоненных строк вычисляется с интервалами.  
  
 REJECT_SAMPLE_VALUE = *reject_sample_value*  
 Является обязательным, если REJECT_TYPE = percentage. Оно указывает число строк, которое следует попытаться импортировать до того, как база данных пересчитает процент строк со сбоями.  
  
 Например, если задано REJECT_SAMPLE_VALUE = 1000, база данных рассчитает процент отклоненных строк после попытки импортировать 1000 строк из внешнего файла данных. Если процент отклоненных строк меньше значения *reject_value*, база данных попытается загрузить следующие 1000 строк. База данных продолжает повторно вычислять процент отклоненных строк после каждой попытки извлечения 1000 строк.  
  
> [!NOTE]  
>  Поскольку база данных вычисляет процент отклоненных строк с интервалами, фактический процент отклоненных строк может превысить *reject_value*.  
  
 Пример  
  
 В этом примере показано, как три параметра REJECT взаимодействуют друг с другом. Например, если задано REJECT_TYPE = percentage, REJECT_VALUE = 30 и REJECT_SAMPLE_VALUE = 100, произойдет следующее:  
  
-   База данных попытается загрузить первые 100 строк; из них 25 отклонено, а 75 — загружено успешно.  
  
-   Процент строк с ошибками равен 25 %, что меньше значения отклонения — 30 %. Таким образом, нет необходимости останавливать загрузку.  
  
-   База данных пытается загрузить следующие 100 строк. На этот раз 25 загружено успешно и 75 — отклонено.  
  
-   Процент отклоненных строк пересчитывается и составляет 50 %. Процент отклоненных строк превысил значение отклонения 30 %.  
  
-   Загрузка завершится ошибкой с 50 % отклоненных строк после попытки загрузить 200 строк, что превышает заданный лимит 30 %.  
  
 WITH *common_table_expression*  
 Задается временно именованный результирующий набор, называемый обобщенным табличным выражением (ОТВ). Дополнительные сведения см. в разделе [WITH common_table_expression (Transact-SQL)](../../t-sql/queries/with-common-table-expression-transact-sql.md).  
  
 SELECT \<select_criteria> заполняет новую таблицу результатами выполнения инструкции SELECT. *select_criteria* являются основной частью инструкции SELECT и определяют, какие данные нужно скопировать в новую таблицу. Сведения об инструкциях SELECT см. в разделе [SELECT (Transact-SQL)](../../t-sql/queries/select-transact-sql.md).  
  
## <a name="permissions"></a>Разрешения  
 Для выполнения этой команды **пользователю базы данных** потребуются все указанные ниже разрешения и роли:  
  
-   Разрешение **ALTER SCHEMA** для локальной схемы, которая будет содержать новую таблицу, или наличие предопределенной роли базы данных **db_ddladmin**.  
  
-   Разрешение **CREATE TABLE** или наличие предопределенной роли базы данных **db_ddladmin**.  
  
-   Разрешение **SELECT** для любых объектов, на которые ссылается *select_criteria*.  
  
 Учетные данные для входа в систему должны обладать всеми нижеперечисленными разрешениями:  
  
-   Разрешение **ADMINISTER BULK OPERATIONS**  
  
-   Разрешение **ALTER ANY EXTERNAL DATA SOURCE**  
  
-   Разрешение **ALTER ANY EXTERNAL FILE FORMAT**  
  
-   Учетные данные для входа в систему должны иметь разрешения записи для чтения из внешней папки в кластере Hadoop или хранилище BLOB-объектов Azure и записи в нее.  
 
 > [!IMPORTANT]  
 >  Разрешение ALTER ANY EXTERNAL DATA SOURCE предоставляет любому субъекту возможность создания и изменения объекта внешнего источника данных и, таким образом, также предоставляет возможность доступа ко всем учетным данным уровня базы данных в базе данных. Это разрешение следует рассматривать как высоко привилегированное, поэтому его следует предоставлять только доверенным субъектам в системе.
  
## <a name="error-handling"></a>Обработка ошибок  
 Если разрешение CREATE EXTERNAL TABLE AS SELECT экспортирует данные в файл с разделителями текста, файл отклонения для строк, которые не удается экспортировать, отсутствует.  
  
 При создании внешней таблицы база данных пытается подключиться к внешнему кластеру Hadoop или хранилищу BLOB-объектов Azure. Если соединение завершается ошибкой, произойдет сбой выполнения команды, внешняя таблица создана не будет. Это может занять около минуты, поскольку база данных повторяет попытки соединения по меньшей мере 3 раза.  
  
 Если инструкция CREATE EXTERNAL TABLE AS SELECT отменена или завершилась неудачно, база данных попытается однократно удалить любые новые файлы и папки, которые уже созданы во внешнем источнике данных.  
  
 База данных сообщит о любых ошибках Java, которые произошли во внешнем источнике данных во время экспорта данных.  
  
##  <a name="GeneralRemarks"></a> Общие замечания  
 После завершения выполнения инструкции CETAS можно выполнять запросы [!INCLUDE[tsql](../../includes/tsql-md.md)] во внешней таблице. Эти операции импортируют данные в базу данных на время выполнения запроса, если только вы не выполните импорт с помощью команды CREATE TABLE AS SELECT.  
  
 Имя и определение внешней таблицы хранятся в метаданных базы данных. Данные хранятся во внешнем источнике данных.  
  
 Внешние файлы получают имена вида *ИДзапроса_дата_время_ИД.формат*, где *ИД* — это нарастающий идентификатор, а *формат* — это формат экспортированных данных. Пример: QID776_20160130_182739_0.orc.  
  
 Инструкция CETAS всегда создает несекционированную таблицу, даже если исходная таблица является секционированной.  
  
 Для планов запросов, созданных с помощью инструкции EXPLAIN, база данных использует эти операции плана запросов для внешних таблиц:  
  
-   перемещение "внешнее перемешивание"  
  
-   перемещение "внешняя трансляция"  
  
-   перемещение "внешнее секционирование"  
  
 **ПРИМЕНИМО К:**  [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]В качестве обязательного условия создания внешней таблицы администратор устройства должен настроить подключение Hadoop. Дополнительные сведения см. в разделе "Настройка подключения к внешним данным" (Analytics Platform System) в документации APS, доступной для скачивания [здесь](http://www.microsoft.com/download/details.aspx?id=48241).  
  
## <a name="limitations-and-restrictions"></a>Ограничения  
 Поскольку данные внешней таблицы находится за пределами базы данных, операции резервного копирования и восстановления будут выполняться только с данными, сохраненными в базе данных. Это означает, что копируются и восстанавливаются только метаданные.  
  
 База данных не проверяет подключение к внешнему источнику данных при восстановлении резервной копии базы данных, которая содержит внешнюю таблицу. Если исходный источник недоступен, восстановление метаданных во внешней таблицы выполняется успешно, однако операции SELECT во внешней таблице завершатся сбоем.  
  
 База данных не гарантирует согласованности данных между базой данных и внешними данными. Вы, клиент, несете полную ответственность за поддержание согласованности между внешними данными и базой данных  
  
 Операций языка обработки данных (DML) не поддерживаются во внешних таблицах. Так, для изменения внешних данных невозможно использовать инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)]обновления, вставки или удаления[!INCLUDE[tsql](../../includes/tsql-md.md)] для изменения внешних данных.  
  
 CREATE TABLE, DROP TABLE, CREATE STATISTICS, DROP STATISTICS, CREATE VIEW и DROP VIEW — это все операции языка описания данных (DDL), которые можно выполнять во внешних таблицах.  
  
 PolyBase может обработать не более 33 тысяч файлов на папку при выполнении параллельных запросов PolyBase со степенью 32. Это максимальное число включает файлы и вложенные папки в каждой папке HDFS. Если степень параллелизма меньше 32, пользователь может выполнять запросы PolyBase к папкам в HDFS, если в них содержится более 33 тысяч файлов. [!INCLUDE[msCoName](../../includes/msconame-md.md)] рекомендует пользователям Hadoop и PolyBase указывать короткие пути к файлам и использовать не более 30 тысяч файлов на папку HDFS. При ссылке на слишком большое число файлов может возникнуть исключение, связанное с нехваткой памяти на виртуальной машине Java.  
  
 [SET ROWCOUNT (Transact-SQL)](../../t-sql/statements/set-rowcount-transact-sql.md) никак не влияет на эту инструкцию CREATE EXTERNAL TABLE AS SELECT. Чтобы обеспечить аналогичное поведение, воспользуйтесь инструкцией [TOP (Transact-SQL)](../../t-sql/queries/top-transact-sql.md).  
  
 Если инструкция CREATE EXTERNAL TABLE AS SELECT выбирает из файла RCFile, значения столбца в файле RCFile не должны содержать вертикальную черту (|).  
  
## <a name="locking"></a>Блокировка  
 Принимает общую блокировку на объект SCHEMARESOLUTION.  
  
##  <a name="Examples"></a> Примеры  
  
### <a name="a-create-a-hadoop-table-using-create-external-table-as-select-cetas"></a>A. Создание таблицы Hadoop с использованием CREATE EXTERNAL TABLE AS SELECT (CETAS)  
 В следующем примере создается новая внешняя таблица с именем `hdfsCustomer`; для этого используются определения столбцов и данные из исходной таблицы `dimCustomer`.  
  
 Определение таблицы хранится в базе данных, а результаты инструкции SELECT экспортируются в файл /pdwdata/customer.tbl во внешнем источнике данных Hadoop *customer_ds*. Этот файл форматируется в соответствии с форматом внешнего файла *customer_ff*.  
  
 Имя файла создается базой данных и содержит ИД запроса, что позволяет легко сопоставлять файл с создавшим его запросом.  
  
 Путь `hdfs://xxx.xxx.xxx.xxx:5000/files/`, предшествующий каталогу "Клиент", должен уже существовать. Однако если каталог "Клиент" не существует, база данных создаст этот каталог.  
  
> [!NOTE]  
>  В этом примере указано значение 5000. Если порт не задан, база данных использует в качестве порта по умолчанию 8020.  
  
 Конечное расположение Hadoop и имя файла будут иметь вид `hdfs:// xxx.xxx.xxx.xxx:5000/files/Customer/ QueryID_YearMonthDay_HourMinutesSeconds_FileIndex.txt.`.  
  
```  
  
      -- Example is based on AdventureWorks   
CREATE EXTERNAL TABLE hdfsCustomer  
WITH (  
        LOCATION='/pdwdata/customer.tbl',  
        DATA_SOURCE = customer_ds,  
        FILE_FORMAT = customer_ff  
) AS SELECT * FROM dimCustomer;  
```  
  
### <a name="b-use-a-query-hint-with-create-external-table-as-select-cetas"></a>Б. Использование указания запроса с инструкцией CREATE EXTERNAL TABLE AS SELECT (CETAS)  
 В этом запросе показан базовый синтаксис для указания запроса на соединение с инструкцией CETAS. После отправки запроса база данных использует стратегию хэш-соединения для создания плана запроса. Дополнительные сведения об указаниях соединения и использовании предложения OPTION см. в разделе [Предложение OPTION (Transact-SQL)](../../t-sql/queries/option-clause-transact-sql.md).  
  
> [!NOTE]  
>  В этом примере указано значение 5000. Если порт не задан, база данных использует в качестве порта по умолчанию 8020.  
  
```  
  
      -- Example is based on AdventureWorks  
CREATE EXTERNAL TABLE dbo.FactInternetSalesNew  
WITH   
    (   
        LOCATION = '/files/Customer',  
        DATA_SOURCE = customer_ds,  
        FILE_FORMAT = customer_ff  
    )  
AS SELECT T1.* FROM dbo.FactInternetSales T1 JOIN dbo.DimCustomer T2  
ON ( T1.CustomerKey = T2.CustomerKey )  
OPTION ( HASH JOIN );  
```  
  
## <a name="see-also"></a>См. также:  
 [CREATE EXTERNAL DATA SOURCE (Transact-SQL)](../../t-sql/statements/create-external-data-source-transact-sql.md)   
 [CREATE EXTERNAL FILE FORMAT (Transact-SQL)](../../t-sql/statements/create-external-file-format-transact-sql.md)   
 [CREATE EXTERNAL TABLE (Transact-SQL)](../../t-sql/statements/create-external-table-transact-sql.md)   
 [CREATE TABLE (хранилище данных SQL Azure или Parallel Data Warehouse)](~/t-sql/statements/create-table-azure-sql-data-warehouse.md)   
 [CREATE TABLE AS SELECT (хранилище данных SQL Azure)](../../t-sql/statements/create-table-as-select-azure-sql-data-warehouse.md)   
 [DROP TABLE (Transact-SQL)](../../t-sql/statements/drop-table-transact-sql.md)   
 [ALTER TABLE (Transact-SQL)](../../t-sql/statements/alter-table-transact-sql.md)  
  
  


