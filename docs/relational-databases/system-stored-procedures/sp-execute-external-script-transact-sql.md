---
title: "sp_execute_external_script (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 10/20/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_execute_external_script_TSQL
- sys.sp_execute_external_script
- sys.sp_execute_external_script_TSQL
- sp_execute_external_script
dev_langs: TSQL
helpviewer_keywords: sp_execute_external_script
ms.assetid: de4e1fcd-0e1a-4af3-97ee-d1becc7f04df
caps.latest.revision: "34"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: d437e6e8d86aa648d9c6ef11a8ca04297cafbaf3
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="spexecuteexternalscript-transact-sql"></a>sp_execute_external_script (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Выполняет сценарий, приведенный в качестве аргумента во внешнем расположении. Сценарий должен быть написан поддерживаемых и зарегистрированных языка. Дерево запроса управляется [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и пользователи не могут выполнять произвольные операции на основе запроса. Для выполнения **sp_execute_external_script**, необходимо сначала включить внешние скрипты с помощью `sp_configure 'external scripts enabled', 1;` инструкции.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
sp_execute_external_script   
    @language = N'language,   
    @script = N'script'  
    [ , @input_data_1 = N'input_data_1' ]   
    [ , @input_data_1_name = N'input_data_1_name' ]   
    [ , @output_data_1_name = N'output_data_1_name' ]  
    [ , @parallel = 0 | 1 ]  
    [ , @params = N'@parameter_name data_type [ OUT | OUTPUT ] [ ,...n ]' ] 
    [ , @parameter1 = 'value1' [ OUT | OUTPUT ] [ ,...n ] ]
```  
  
## <a name="arguments"></a>Аргументы  
 @language= N'*языка*"  
 Указывает язык скрипта. *Язык* — **sysname**.  

 Допустимые значения: `Python` или `R`. 
  
 @script= N'*сценарий*"  
 Внешний язык сценария, указанного как литерал или ВВОД. *сценарий* — **nvarchar(max)**.  
  
 [ @input_data_1_name = N'*input_data_1_name*"]  
 Задает имя переменной, которая используется для представления запроса, определенного по @input_data_1. Тип данных переменной в внешнего скрипта зависит от языка. В случае R Входная переменная является кадра данных. В случае Python он должен быть табличной. *input_data_1_name* — **sysname**.  
  
 Значение по умолчанию — «InputDataSet».  
  
 [ @input_data_1 = N'*input_data_1*"]  
 Задает входные данные, используемые внешних скриптов в виде [!INCLUDE[tsql](../../includes/tsql-md.md)] запроса. *input_data_1* — **nvarchar(max)**.  
  
 [ @output_data_1_name = N'*output_data_1_name*"]  
 Указывает имя переменной в внешний скрипт, который содержит данные, возвращаемые для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] после завершения вызова хранимой процедуры. Тип данных переменной в внешнего скрипта зависит от языка. Если R выходные данные должны присутствовать кадра данных. В случае Python выходных данных должно быть pandas кадра данных. *output_data_1_name* — **sysname**.  
  
 Значение по умолчанию — «OutputDataSet».  
  
 [ @parallel = 0 | 1 ]  
 Включите параллельное выполнение R-скриптов, задав `@parallel` значение 1. Значение по умолчанию для этого параметра равно 0 (нет параллелизма).  
  
 Для сценариев R, не следует использовать функции RevoScaleR, с помощью `@parallel` параметр может быть полезным для обработки больших наборов данных, при условии, что скрипт элементарно могут выполняться параллельно. Например, при использовании R `predict` функция с моделью, чтобы создать новые прогнозы, задайте `@parallel = 1` как подсказку для ядро запросов. Если запрос может выполняться параллельно, строки распределены в соответствии с **MAXDOP** параметр.  
  
 Если `@parallel = 1` и выходные данные передаются непосредственно на клиентском компьютере, а затем `WITH RESULTS SETS` предложение является обязательным и должен быть указан схему выходных данных.  
  
 Для сценариев R, использовать функции RevoScaleR, параллельная обработка осуществляется автоматически и не следует указывать `@parallel = 1` для **sp_execute_external_script** вызова.  
  
 [ @params = N' *@parameter_name data_type* [OUT | ВЫВОД] [,.. .n] "]  
 Список объявлений входных параметров, используемых в внешних скриптов.  
  
 [ @parameter1 = "*значение1*" [OUT | ВЫВОД] [,.. .n]]  
 Список значений для входных параметров, используемых внешних скриптов.  


## <a name="remarks"></a>Замечания  
 Процедура **sp_execute_external_script** служит для выполнения сценариев, написанных на поддерживаемом языке, например R. В версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]службы [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] включают в себя серверный компонент, устанавливаемый с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], а также набор инструментов рабочей станции и библиотек подключений, которые позволяют специалистам по анализу и обработке данных подключаться к высокопроизводительной среде [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Установка служб R (в базе данных) во время [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] программу установки, чтобы разрешить выполнение сценариев R. Дополнительные сведения см. в разделе [Настройка SQL Server R Services &#40; В базе данных &#41;](../../advanced-analytics/r-services/set-up-sql-server-r-services-in-database.md).  
  
 Можно выбрать ресурсы, используемые внешних скриптов путем настройки внешнего пула ресурсов. Дополнительные сведения см. в разделе [CREATE EXTERNAL RESOURCE POOL (Transact-SQL)](../../t-sql/statements/create-external-resource-pool-transact-sql.md). Сведения о рабочей нагрузки можно получить из представления каталога регулятора ресурсов, динамические административные Представления и счетчики. Дополнительные сведения см. в разделе [представления каталога регулятора ресурсов &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/resource-governor-catalog-views-transact-sql.md), [Регулятора ресурсов, связанные с динамическим административным представлениям &#40; Transact-SQL &#41; ](../../relational-databases/system-dynamic-management-views/resource-governor-related-dynamic-management-views-transact-sql.md), и [SQL Server, внешние сценарии объекта](../../relational-databases/performance-monitor/sql-server-external-scripts-object.md).  

Монитор выполнения скрипта с помощью [sys.dm_external_script_requests](../../relational-databases/system-dynamic-management-views/sys-dm-external-script-requests.md) и [sys.dm_external_script_execution_stats](../../relational-databases/system-dynamic-management-views/sys-dm-external-script-execution-stats.md). 

 По умолчанию результирующие наборы, возвращаемые этой хранимой процедурой при выводе безымянные столбцы. Имена столбцов, используемых в сценарии являются локальными для среда скриптов и не отражаются в выходные файлов результирующего набора. Чтобы присвоить имя результирующего набора столбцов, используйте `WITH RESULTS SET` предложения [ `EXECUTE` ](../../t-sql/language-elements/execute-transact-sql.md).
  
 Помимо возврата результирующего набора, можно вернуть скалярные значения из сценария R для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с помощью ВЫХОДНЫХ параметров. В следующем примере показано использование ВЫХОДНОГО параметра:  
  
```  
DECLARE @model varbinary(max);  
EXEC sp_execute_external_script  
        @language = N'R'  
        , @script = N'  
    # build classification model to predict tipped or not  
    logitObj <- glm(tipped ~ passenger_count + trip_distance + trip_time_in_secs + direct_distance, data = featureDataSource, family = binomial(link=logit));  
  
    # First, serialize a model and put it into a database table  
    modelbin <- serialize(logitObj, NULL);  
    '  
        , @input_data_1 = N'  
SELECT tipped, passenger_count, trip_time_in_secs, trip_distance, d.direct_distance  
  FROM dbo.nyctaxi_sample TABLESAMPLE (1 PERCENT) REPEATABLE (98074)  
  CROSS APPLY [CalculateDistance](pickup_latitude, pickup_longitude,  dropoff_latitude, dropoff_longitude) as d  
'  
        , @input_data_1_name = N'featureDataSource'  
        , @params = N'@modelbin varbinary(max) OUTPUT'  
        , @modelbin = @model OUTPUT;  
```  


## <a name="streaming-execution-for-r-script"></a>Потоковое выполнение скрипта R  
 Поддерживается потоковая передача выполнение скрипта R, указав `@r_rowsPerRead int parameter` в `@params` коллекции.  Потоковая передача позволяет скрипты R для работы с данными, которые не помещаются в памяти. Например, если миллиардов строк для оценки с помощью predict, функция новый `@r_rowsPerRead` используется для разбиения во время выполнения в один поток. Этот параметр контролирует количество строк, отправляемых процессам R, он также может использоваться для регулировать количество строк, считываемых за один раз. Это может быть полезно для устранения проблем с производительностью сервера, если, например, еще прошла обучение большой моделью. Обратите внимание, что этот параметр может использоваться только в случаях, где выходные данные скрипта R не зависит от чтения или при рассмотрении весь набор строк.  
  
 Оба `@r_rowsPerRead` параметр для потоковой передачи и `@parallel` аргумент следует учитывать указания. Для указания, должна быть применена должна существовать возможность создать план запроса SQL, который поддерживает параллельную обработку. Если это невозможно, невозможно включить параллельной обработки.  
  
> [!NOTE]  
>  Потоковая передача и параллельную обработку поддерживаются только в выпуске Enterprise Edition. Параметры можно включить в запросах в выпуске Standard Edition без возникновения ошибки, но параметры имеют не эффект и сценариев R выполняются в одном процессе.  
  
## <a name="restrictions"></a>Ограничения  
 **Типы данных:** следующие типы данных не поддерживаются при использовании входного запроса, или параметры `sp_execute_external_script` процедуры и возвращают ошибку неподдерживаемого типа.  
  
 Чтобы избежать этого **ПРИВЕДЕНИЯ** столбца или значение в поддерживаемый тип в [!INCLUDE[tsql](../../includes/tsql-md.md)] и отправлять их в R.  
  
-   **курсор**  
  
-   **timestamp**  
  
-   **datetime2**, **datetimeoffset**, **времени**  
  
-   **sql_variant**  
  
-   **текст**, **изображения**  
  
-   **xml**  
  
-   **HierarchyID**, **geometry**, **geography**  
  
-   Определяемые пользователем типы CLR  
  
 **DateTime** значений во входных данных преобразуются в NA на стороне R для значений, которые не помещаются в р. Это необходимо, так как допустимого диапазона значений [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] позволяет использовать больший диапазон значений, чем поддерживается в языке R.  
  
 Число с плавающей запятой значения (например, + Inf, -Inf, NaN), не поддерживаются в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] даже если оба языка используют IEEE 754. Текущее поведение отправляются только значения [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] напрямую и как sqlclient результат в [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] вызывает ошибку. Эти значения преобразуются **NULL**.  
  
 Любой R результирующий набор, который не может быть сопоставлен с [!INCLUDE[tsql](../../includes/tsql-md.md)] тип данных выводится как NULL.  
  
## <a name="permissions"></a>Permissions  
 Требуется **EXECUTE ANY EXTERNAL SCRIPT** разрешение базы данных.  
  
## <a name="examples"></a>Примеры  
 Этот раздел содержит примеры использования этой хранимой процедуры для выполнения сценариев R с помощью [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
### <a name="a-return-a-data-set-from-r-to-sql-server"></a>A. Возвращает набор данных из R в SQL Server  
 В следующем примере создается хранимая процедура, которая использует **sp_execute_external_script** для возврата из R в набор данных iris [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
```  
DROP PROC IF EXISTS get_iris_dataset;  
go  
CREATE PROC get_iris_dataset  
AS  
BEGIN  
 EXEC   sp_execute_external_script  
       @language = N'R'  
     , @script = N'iris_data <- iris;'  
     , @input_data_1 = N''  
     , @output_data_1_name = N'iris_data'  
     WITH RESULT SETS (("Sepal.Length" float not null,   
           "Sepal.Width" float not null,  
        "Petal.Length" float not null,   
        "Petal.Width" float not null, "Species" varchar(100)));  
END;  
go  
```  
  
### <a name="b-generate-a-model-based-on-data-from-sql-server"></a>Б. Формирование модели на основе данных из SQL Server  
 В следующем примере создается хранимая процедура, которая использует **sp_execute_external_script** для формирования iris модели и модели, чтобы вернуть [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!NOTE]  
>  В этом примере требуется установка пакета e1071. Дополнительные сведения см. в разделе [Установка дополнительных пакетов R на сервере SQL Server](../../advanced-analytics/r-services/install-additional-r-packages-on-sql-server.md).  
  
```  
DROP PROC IF EXISTS generate_iris_model;  
go  
  
CREATE PROC generate_iris_model  
AS  
BEGIN  
 EXEC sp_execute_external_script  
      @language = N'R'  
     , @script = N'  
          library(e1071);  
          irismodel <-naiveBayes(iris_data[,1:4], iris_data[,5]);  
          trained_model <- data.frame(payload = as.raw(serialize(irismodel, connection=NULL)));  
'  
     , @input_data_1 = N'select "Sepal.Length", "Sepal.Width", "Petal.Length", "Petal.Width", "Species" from iris_data'  
     , @input_data_1_name = N'iris_data'  
     , @output_data_1_name = N'trained_model'  
    WITH RESULT SETS ((model varbinary(max)));  
END;  
go  
```  
  
## <a name="see-also"></a>См. также:  
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Библиотеки Python и типы данных](../../advanced-analytics/python/python-libraries-and-data-types.md)  
 [Библиотеки R и типами данных R](../../advanced-analytics/r/r-libraries-and-data-types.md)  
 [Службы R SQL Server](../../advanced-analytics/r-services/sql-server-r-services.md)   
 [Известные проблемы для SQL Server R Services](../../advanced-analytics/r-services/known-issues-for-sql-server-r-services.md)   
 [СОЗДАТЬ ВНЕШНЮЮ БИБЛИОТЕКУ &#40; Transact-SQL &#41;](../../t-sql/statements/create-external-library-transact-sql.md)  
 [sp_prepare &#40; Transact SQL &#41;](../../relational-databases/system-stored-procedures/sp-prepare-transact-sql.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)   
 [Параметр конфигурации сервера External scripts enabled](../../database-engine/configure-windows/external-scripts-enabled-server-configuration-option.md)   
 [SERVERPROPERTY (Transact-SQL)](../../t-sql/functions/serverproperty-transact-sql.md)   
 [SQL Server, объект External Scripts](../../relational-databases/performance-monitor/sql-server-external-scripts-object.md)  
[sys.dm_external_script_requests](../../relational-databases/system-dynamic-management-views/sys-dm-external-script-requests.md)  
[sys.dm_external_script_execution_stats](../../relational-databases/system-dynamic-management-views/sys-dm-external-script-execution-stats.md) 
  
