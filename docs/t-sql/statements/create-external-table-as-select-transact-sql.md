---
title: "Создание ВНЕШНЕГО TABLE AS SELECT (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 08/10/2017
ms.prod: 
ms.prod_service: sql-data-warehouse, pdw
ms.reviewer: 
ms.service: sql-data-warehouse
ms.component: t-sql|statements
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: f2ca379cf30fe2e7d359a294a18804f0b5e6faeb
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
---
# <a name="create-external-table-as-select-transact-sql"></a>Создание ВНЕШНЕГО TABLE AS SELECT (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Создает внешнюю таблицу и затем, в параллельном режиме, результаты экспортируются [!INCLUDE[tsql](../../includes/tsql-md.md)] инструкции SELECT в BLOB-объекта хранилища Azure или Hadoop.  
  
 Используйте инструкцию, чтобы создать ВНЕШНИЕ таблицы AS ВЫБЕРИТЕ (CETAS):  
  
-   Экспорт таблицы базы данных в хранилище больших двоичных объектов Azure или Hadoop.  
  
-   Импорт данных из хранилища больших двоичных объектов Azure или Hadoop и их сохранения в базе данных.  
  
-   Запрос данных из Hadoop или BLOB-объекта хранилища Azure, соединять их с таблиц реляционной базы данных и записывать результаты обратно в хранилище больших двоичных объектов Azure или Hadoop.  
  
-   Запрашивать данные из Hadoop или BLOB-объекта хранилища Azure, преобразовать его с помощью возможности быстрой обработки базы данных и записывать ее назад в хранилище больших двоичных объектов Azure или Hadoop.  
  
 Дополнительные сведения см. в разделе [Приступая к работе с PolyBase](../../relational-databases/polybase/get-started-with-polybase.md).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "значок ссылки на раздел") [синтаксические обозначения Transact-SQL &#40; Transact-SQL &#41;](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
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
 Одно для трех - частей имя таблицы для создания базы данных. Для внешней таблицы только метаданные таблицы хранятся в реляционной базе данных.  
  
 РАСПОЛОЖЕНИЕ = "*hdfs_folder*"  
 Указывает место записи результатов инструкции SELECT для внешнего источника данных. Область является именем папки и при необходимости можно включить путь относительно папки корневого кластера Hadoop или BLOB-объекта хранилища Azure.  PolyBase будет создан путь к папке, если он еще не существует.  
  
 Внешние файлы записываются в *hdfs_folder* и именованные *Идзапроса_дата_время_ид.формат*, где *идентификатор* — это нарастающий идентификатор и *формат* — это формат экспортированных данных. Пример: QID776_20160130_182739_0.orc.  
  
 DATA_SOURCE = *external_data_source_name*  
 Задает имя объекта источника внешних данных, содержащий местоположение, где хранятся внешние данные, или будет сохранен. Расположение — кластер Hadoop или BLOB-объект хранилища Azure. Для создания внешнего источника данных, используйте [CREATE EXTERNAL DATA SOURCE &#40; Transact-SQL &#41; ](../../t-sql/statements/create-external-data-source-transact-sql.md).  
  
 FILE_FORMAT = *external_file_format_name*  
 Указывает имя объекта формата внешнего файла, содержащий формат файла внешних данных. Чтобы создать формата внешних файлов, используйте [CREATE EXTERNAL FILE FORMAT &#40; Transact-SQL &#41; ](../../t-sql/statements/create-external-file-format-transact-sql.md).  
  
 Отклонить параметры  
 Отклонить параметры не применяются во время выполнения этой инструкции CREATE EXTERNAL TABLE AS SELECT. Вместо этого они указаны здесь, чтобы базы данных их можно использовать позже при импорте данных из внешней таблицы. Позже когда инструкция CREATE TABLE AS SELECT выбирает данные из внешней таблицы, базы данных будет использовать параметры отклонения для определения число или процент строк, может произойти сбой импорта до остановки импорта.  
  
 REJECT_VALUE = *reject_value*  
 Указывает значение или процент строк, в которых может произойти сбой импорта до базы данных останавливает выполнение импорта.  
  
 REJECT_TYPE = **значение** | процент  
 Уточняет, является ли параметр REJECT_VALUE указан как литеральное значение или процент.  
  
 value  
 REJECT_VALUE является буквенные значения, а не в процентах.  Базы данных будет остановлено импорта строк из файла внешних данных, когда число строк превышает *reject_value*.  
  
 Например если REJECT_VALUE = 5 и REJECT_TYPE = value, базы данных будет остановить импорт строк, после 5 строк произошел сбой импорта.  
  
 Процент  
 REJECT_VALUE представлены в процентах, а не литеральное значение. Будет остановки импорта строк из внешней базы данных файла данных, когда *процент* строки с ошибками превышает *reject_value*. Процент сбойных строк вычисляется с интервалами.  
  
 REJECT_SAMPLE_VALUE = *reject_sample_value*  
 Требуется, если REJECT_TYPE = процентное значение, это указывает число строк, следует попытаться импортировать до базы данных пересчитает процент сбойных строк.  
  
 Например если REJECT_SAMPLE_VALUE = 1000, базы данных будет вычислять процент сбойных строк после попытки импорта 1000 строк из файла внешних данных. Если процент сбойных строк меньше, чем *reject_value*, базы данных будет предпринята попытка загрузить другой 1000 строк. База данных продолжает повторно вычислить процент сбойных строк после предпринимается попытка импорта каждого дополнительных 1000 строк.  
  
> [!NOTE]  
>  Так как базы данных вычисляет процент сбойных строк с интервалами, может превышать фактический процент сбойных строк *reject_value*.  
  
 Пример  
  
 В этом примере показано, как три варианта ОТКЛОНИТЬ взаимодействуют друг с другом. Например если REJECT_TYPE = процент REJECT_VALUE = 30 лет, а значение REJECT_SAMPLE_VALUE = 100, возможна следующая ситуация:  
  
-   Базы данных будет пытаться загрузить первые 100 строк; 25 успешно завершится неудачей и 75.  
  
-   Процент сбойных строк вычисляется как 25%, это меньше отклоняемое значение 30%. Таким образом, нет необходимости остановить загрузку.  
  
-   Базы данных пытается загрузить следующие 100 строк; Это время 25 успешно и 75 ошибкой.  
  
-   Процент сбойных строк повторно по мере 50%. Процент сбойных строк превысил значение 30% отклонения.  
  
-   Загрузка завершится ошибкой с 50% не удается строк после попытки загрузить 200 строк который больше указанного значения 30%.  
  
 С *обобщенное_табличное_выражение*  
 Задается временно именованный результирующий набор, называемый обобщенным табличным выражением (ОТВ). Дополнительные сведения см. в разделе [с общее_табличное_выражение &#40; Transact-SQL &#41; ](../../t-sql/queries/with-common-table-expression-transact-sql.md).  
  
 ВЫБЕРИТЕ \<select_criteria > заполняет новую таблицу с результатами из инструкции SELECT. *select_criteria* текст инструкции SELECT, которое определяет, какие данные необходимо скопировать в новую таблицу. Сведения об инструкциях SELECT см. в разделе [ВЫБЕРИТЕ &#40; Transact-SQL &#41; ](../../t-sql/queries/select-transact-sql.md).  
  
## <a name="permissions"></a>Разрешения  
 Для выполнения этой команды **пользователя базы данных** должен все эти разрешения или членства:  
  
-   **ALTER SCHEMA** разрешение на локальный схему, которой будет содержаться новая таблица или членство в роли **db_ddladmin** предопределенной роли базы данных.  
  
-   **CREATE TABLE** разрешения или членства в **db_ddladmin** предопределенной роли базы данных.  
  
-   **ВЫБЕРИТЕ** разрешений на любые объекты, на которые ссылается *select_criteria*.  
  
 Имя входа должно все эти разрешения:  
  
-   **ADMINISTER BULK OPERATIONS** разрешение  
  
-   **ALTER ANY EXTERNAL DATA SOURCE** разрешение  
  
-   **ALTER ANY EXTERNAL FILE FORMAT** разрешение  
  
-   Имя входа должно иметь разрешения на запись для чтения и записи на внешнюю папку в кластере Hadoop или BLOB-объекта хранилища Azure.  
 
 > [!IMPORTANT]  
 >  Разрешение ALTER ANY EXTERNAL DATA SOURCE предоставляет любому участнику возможность создания и изменения любого объекта источника внешних данных, и таким образом, он также предоставляет возможность доступа к все учетные данные уровня базы данных в базе данных. Это разрешение следует рассматривать как широкими правами и поэтому должен предоставлять только доверенным участникам в системе.
  
## <a name="error-handling"></a>Обработка ошибок  
 Когда CREATE EXTERNAL TABLE AS SELECT экспортирует данные в файл с разделителями текста, отсутствует файл отклонения для строк, которые не удалось экспортировать.  
  
 При создании внешней таблицы, базы данных пытается подключиться к внешней кластера Hadoop или BLOB-объекта хранилища Azure. При сбое соединения, команда не будет выполнена и внешней таблицы не создаются. Может занять около минуты или более для происходит сбой выполнения команды с момента базы данных повторные попытки соединения по крайней мере 3 раза.  
  
 Если CREATE EXTERNAL TABLE AS SELECT отменена или завершилась неудачно, базы данных сделает одноразовый попытка удалить новые файлы и папки уже созданы на внешнем источнике данных.  
  
 База данных сообщит Java ошибки, происходящие на внешнем источнике данных во время экспорта данных.  
  
##  <a name="GeneralRemarks"></a>Общие замечания  
 После завершения выполнения инструкции CETAS, можно запустить [!INCLUDE[tsql](../../includes/tsql-md.md)] запросы на внешнюю таблицу. Эти операции выполнит импорт данных в базу данных на время выполнения запроса, если не импортировать с помощью инструкции CREATE TABLE AS SELECT.  
  
 Имя внешней таблицы и определения, хранятся в метаданных базы данных. Данные хранятся в источнике внешних данных.  
  
 Внешние файлы получают имена вида *ИДзапроса_дата_время_ИД.формат*, где *ИД* — это нарастающий идентификатор, а *формат* — это формат экспортированных данных. Пример: QID776_20160130_182739_0.orc.  
  
 Оператор CETAS всегда создается несекционированная таблица, даже если исходная таблица является секционированной.  
  
 Для планов запросов создается со объяснение databaseuses эти операции плана запроса для внешних таблиц:  
  
-   Внешние случайный порядок перемещения  
  
-   Переместить внешние вещания  
  
-   Перемещение внешних секции  
  
 **ПРИМЕНЯЕТСЯ к:**[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]как необходимый компонент для создания внешней таблицы, администратор приложения необходимо настроить подключения к hadoop. Дополнительные сведения см. в разделе Настройка подключения к внешним данным (Analytics Platform System) в APS документации, который можно загрузить из [здесь](http://www.microsoft.com/download/details.aspx?id=48241).  
  
## <a name="limitations-and-restrictions"></a>Ограничения  
 Поскольку данных внешней таблицы находится за пределами базы данных, резервного копирования и операциями восстановления будет работать только с данными, хранящимися в базе данных. Это означает, что только метаданные будут резервного копирования и восстановления.  
  
 При восстановлении резервной копии базы данных, содержащий внешнюю таблицу базы данных не проверяет подключение к внешнему источнику данных. Если исходный источник недоступен, восстановление метаданных внешней таблицы, по-прежнему выполняется успешно, однако операциями SELECT для внешней таблицы не удастся.  
  
 Базы данных не гарантирует согласованность данных между databaseand внешних данных. Вы, клиент, отвечают исключительно для поддержания согласованности между внешних данных и базы данных.  
  
 Операций языка обработки данных не поддерживаются во внешних таблицах. Например, нельзя использовать [!INCLUDE[tsql](../../includes/tsql-md.md)] update, insert или delete [!INCLUDE[tsql](../../includes/tsql-md.md)]инструкции для изменения внешних данных.  
  
 CREATE TABLE, DROP TABLE, CREATE STATISTICS, DROP STATISTICS, CREATE VIEW и DROP VIEW являются операции языка DDL определения только тех данных, разрешенные для внешних таблиц.  
  
 PolyBase может использовать более 33 k-файлов в папке, при выполнении 32 параллельных запросов PolyBase. Это максимальное число включает файлы и вложенные папки в каждой папке HDFS. Если степень параллелизма меньше 32, пользователь может использовать запросы PolyBase папки, в которой содержат более 33 k файлы HDFS. [!INCLUDE[msCoName](../../includes/msconame-md.md)]Корпорация Майкрософт рекомендует пользователям Hadoop и PolyBase сохранить короткие пути к файлам и использовать не более 30 k-файлы в папке HDFS. При обращении к слишком много файлов происходит исключение нехватки памяти в виртуальной машины Java.  
  
 [SET ROWCOUNT &#40; Transact-SQL &#41; ](../../t-sql/statements/set-rowcount-transact-sql.md) не влияет на этот CREATE EXTERNAL TABLE AS SELECT. Чтобы достичь такое же поведение, используйте [в начало &#40; Transact-SQL &#41; ](../../t-sql/queries/top-transact-sql.md).  
  
 Если CREATE EXTERNAL TABLE AS SELECT выбирает RCFile, значения столбца в RCFile не должно содержать канала "|" символов.  
  
## <a name="locking"></a>Блокировка  
 Принимает объект SCHEMARESOLUTION разделяемую блокировку.  
  
##  <a name="Examples"></a> Примеры  
  
### <a name="a-create-a-hadoop-table-using-create-external-table-as-select-cetas"></a>A. Создать таблицу Hadoop с помощью СОЗДАНИЯ ВНЕШНЕЙ таблицы AS ВЫБЕРИТЕ (CETAS)  
 В следующем примере создается новый внешний таблицу с именем `hdfsCustomer`, с помощью определения столбцов и данных из исходной таблицы `dimCustomer`.  
  
 Определение таблицы хранятся в базе данных, а результаты инструкции SELECT экспортируются "/ pdwdata/customer.tbl" файл Hadoop внешнего источника данных *customer_ds*. Этот файл имеет формат согласно формата внешнего файла *customer_ff*.  
  
 Имя файла, созданное базой данных и содержит идентификатор запроса для простоты выравнивание файла с запросом, который его создал.  
  
 Путь `hdfs://xxx.xxx.xxx.xxx:5000/files/` предшествующий каталоге клиентов должен уже существовать. Однако если каталог клиента не существует, базы данных создаст каталог.  
  
> [!NOTE]  
>  В этом примере задает для 5000. Если порт не указан, база данных использует 8020 в качестве порта по умолчанию.  
  
 Результирующее Hadoop, расположение и имя файла будет `hdfs:// xxx.xxx.xxx.xxx:5000/files/Customer/ QueryID_YearMonthDay_HourMinutesSeconds_FileIndex.txt.`.  
  
```  
  
      -- Example is based on AdventureWorks   
CREATE EXTERNAL TABLE hdfsCustomer  
WITH (  
        LOCATION='/pdwdata/customer.tbl',  
        DATA_SOURCE = customer_ds,  
        FILE_FORMAT = customer_ff  
) AS SELECT * FROM dimCustomer;  
```  
  
### <a name="b-use-a-query-hint-with-create-external-table-as-select-cetas"></a>Б. Использование подсказки в запросе с создать ВНЕШНИЕ таблицы AS ВЫБЕРИТЕ (CETAS)  
 Этот запрос показывает использование указаний запросов соединения с помощью инструкции CETAS основной синтаксис. После отправки запроса базы данных использует стратегию соединения хэш для создания плана запроса. Дополнительные сведения о указания соединения и как использовать предложение OPTION. в разделе [предложение OPTION &#40; Transact-SQL &#41; ](../../t-sql/queries/option-clause-transact-sql.md).  
  
> [!NOTE]  
>  В этом примере задает для 5000. Если порт не указан, база данных использует 8020 в качестве порта по умолчанию.  
  
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
  
## <a name="see-also"></a>См. также  
 [CREATE EXTERNAL DATA SOURCE (Transact-SQL)](../../t-sql/statements/create-external-data-source-transact-sql.md)   
 [CREATE EXTERNAL FILE FORMAT (Transact-SQL)](../../t-sql/statements/create-external-file-format-transact-sql.md)   
 [CREATE EXTERNAL TABLE (Transact-SQL)](../../t-sql/statements/create-external-table-transact-sql.md)   
 [СОЗДАТЬ ТАБЛИЦУ &#40; Хранилище данных Azure SQL, параллельное хранилище данных &#41;](~/t-sql/statements/create-table-azure-sql-data-warehouse.md)   
 [CREATE TABLE AS SELECT #40; Хранилище данных Azure SQL &#41;](../../t-sql/statements/create-table-as-select-azure-sql-data-warehouse.md)   
 [DROP TABLE &#40; Transact-SQL &#41;](../../t-sql/statements/drop-table-transact-sql.md)   
 [ALTER TABLE (Transact-SQL)](../../t-sql/statements/alter-table-transact-sql.md)  
  
  


