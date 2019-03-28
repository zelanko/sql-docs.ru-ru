---
title: sp_execute_external_script (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 08/14/2018
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_execute_external_script_TSQL
- sys.sp_execute_external_script
- sys.sp_execute_external_script_TSQL
- sp_execute_external_script
dev_langs:
- TSQL
helpviewer_keywords:
- sp_execute_external_script
ms.assetid: de4e1fcd-0e1a-4af3-97ee-d1becc7f04df
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions||=azuresqldb-mi-current'
ms.openlocfilehash: f11b09d93510fe1da89abc1a723e7698f1fdd915
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/27/2019
ms.locfileid: "58531046"
---
# <a name="spexecuteexternalscript-transact-sql"></a>sp_execute_external_script (Transact-SQL)

[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

Выполняет скрипт, указанные в качестве входного аргумента в процедуру. Сценарий выполняется в [extensibility framework](../../advanced-analytics/concepts/extensibility-framework.md). Скрипт должен быть написан на языке поддерживаемых и зарегистрированных в ядре СУБД наличие по крайней мере одно расширение: [**R**](../../advanced-analytics/concepts/extension-r.md), [ **Python**](../../advanced-analytics/concepts/extension-python.md), или [ **Java** (в SQL Server 2019 только предварительная версия)](../../advanced-analytics/java/extension-java.md). 

Для выполнения **sp_execute_external_script**, необходимо сначала включить внешние скрипты с помощью инструкции, `sp_configure 'external scripts enabled', 1;`.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  

> [!Note]
> Машинного обучения (R и Python) и программирования расширений устанавливаются как дополнительный компонент для экземпляра компонента database engine. Поддержка определенных расширений различаются в зависимости от версии SQL Server.

::: moniker range=">=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions"
## <a name="syntax"></a>Синтаксис

```
sp_execute_external_script   
    @language = N'language',   
    @script = N'script'  
    [ , @input_data_1 = N'input_data_1' ]   
    [ , @input_data_1_name = N'input_data_1_name' ]  
    [ , @input_data_1_order_by_columns = N'input_data_1_order_by_columns' ]    
    [ , @input_data_1_partition_by_columns = N'input_data_1_partition_by_columns' ]  
    [ , @output_data_1_name = N'output_data_1_name' ]  
    [ , @parallel = 0 | 1 ]  
    [ , @params = N'@parameter_name data_type [ OUT | OUTPUT ] [ ,...n ]' ] 
    [ , @parameter1 = 'value1' [ OUT | OUTPUT ] [ ,...n ] ]
```
::: moniker-end
::: moniker range=">=sql-server-2016 <=sql-server-2017||=sqlallproducts-allversions"
## <a name="syntax-for-2017-and-earlier"></a>Синтаксис для 2017 и более ранних версий

```
sp_execute_external_script   
    @language = N'language',   
    @script = N'script'  
    [ , @input_data_1 = N'input_data_1' ]   
    [ , @input_data_1_name = N'input_data_1_name' ]  
    [ , @output_data_1_name = N'output_data_1_name' ]  
    [ , @parallel = 0 | 1 ]  
    [ , @params = N'@parameter_name data_type [ OUT | OUTPUT ] [ ,...n ]' ] 
    [ , @parameter1 = 'value1' [ OUT | OUTPUT ] [ ,...n ] ]
```
::: moniker-end

## <a name="arguments"></a>Аргументы
 **@language** = N "*языка*"  
 Указывает язык скрипта. *Язык* — **sysname**.  В зависимости от версии SQL Server допустимые значения: Java (Предварительная версия SQL Server 2019), R (SQL Server 2016 и более поздние версии) и Python (SQL Server 2017 и более поздние версии). 
  
 **@script** = N "*скрипт*" внешний язык скрипта, указанных в качестве входных литералом или переменной. *сценарий* — **nvarchar(max)**.  

`[ @input_data_1 =  N'input_data_1' ]` Указывает входные данные, используемые внешних скриптов в виде [!INCLUDE[tsql](../../includes/tsql-md.md)] запроса. Тип данных *input_data_1* — **nvarchar(max)**.

`[ @input_data_1_name = N'input_data_1_name' ]` Задает имя переменной, которая используется для представления запроса определяется @input_data_1. Тип данных переменной в внешних скриптов зависит от языка. В случае R Входная переменная — это блок данных. В случае Python входные данные должны быть табличных. *input_data_1_name* — **sysname**.  Значение по умолчанию — *InputDataSet*.  

::: moniker range=">=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions"
`[ @input_data_1_order_by_columns = N'input_data_1_order_by_columns' ]` Применяется только к SQL Server 2019 и используется для построения моделей каждого раздела. Задает имя столбца, используемого для сортировки результирующего набора, например по названию продукта. Тип данных переменной в внешних скриптов зависит от языка. В случае R Входная переменная — это блок данных. В случае Python входные данные должны быть табличных.

`[ @input_data_1_partition_by_columns = N'input_data_1_partition_by_columns' ]` Применяется только к SQL Server 2019 и используется для построения моделей каждого раздела. Задает имя столбца, используемого для сегментирования данных, например географический регион или дата. Тип данных переменной в внешних скриптов зависит от языка. В случае R Входная переменная — это блок данных. В случае Python входные данные должны быть табличных. 
::: moniker-end

`[ @output_data_1_name =  N'output_data_1_name' ]` Указывает имя переменной в внешнего скрипта, содержащий данные, возвращаемые для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] после завершения вызова хранимой процедуры. Тип данных переменной в внешних скриптов зависит от языка. R выходные данные должны быть кадр данных. Python выходные данные должны быть во фрейм данных pandas. *output_data_1_name* — **sysname**.  Значение по умолчанию — *OutputDataSet*.  

`[ @parallel = 0 | 1 ]` Включение параллельного выполнения R-скриптов, задав `@parallel` параметр 1. Значение по умолчанию для этого параметра равно 0 (без параллелизма). Если `@parallel = 1` и выходные данные передаются непосредственно на клиентском компьютере, а затем `WITH RESULT SETS` предложение является обязательным и должно быть указано схему выходных данных.  

 + Для скриптов R, не использующих функции RevoScaleR, с помощью `@parallel` параметр может быть полезным для обработки больших наборов данных, при условии, что скрипт можно просто распараллелить. Например, при использовании R `predict` функции с помощью модели, чтобы создать новые прогнозы, задайте `@parallel = 1` как подсказку для ядро запросов. Если запрос может выполняться параллельно, строки распределены в соответствии с **MAXDOP** параметр.  
  
 + Для скриптов R, использующих функции RevoScaleR, параллельная обработка осуществляется автоматически и не следует указывать `@parallel = 1` для **sp_execute_external_script** вызова.  
  
`[ @params = N'@parameter_name data_type [ OUT | OUTPUT ] [ ,...n ]' ]` Список объявлений входного параметра, которые используются в внешнего скрипта.  
  
`[ @parameter1 = 'value1' [ OUT | OUTPUT ] [ ,...n ] ]` Список значений для входных параметров, используемых внешних скриптов.  

## <a name="remarks"></a>Примечания

> [!IMPORTANT]
> Дерево запроса управляется [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и пользователи не могут выполнять произвольные операции с запросом. 

Используйте **sp_execute_external_script** для выполнения сценариев, написанных на поддерживаемом языке. В настоящее время поддерживаемых языков: R для SQL Server 2016 R Services и Python и R для службы машинного обучения SQL Server 2017. 

По умолчанию результирующие наборы, возвращаемые этой хранимой процедурой, выходных данных с помощью безымянные столбцы. Имена столбцов, используемые в сценариях являются локальными для среда скриптов и не отражаются в выводимые результирующего набора. Чтобы присвоить имя результирующего набора столбцов, используйте `WITH RESULT SET` предложении [ `EXECUTE` ](../../t-sql/language-elements/execute-transact-sql.md).
  
 Помимо возврата результирующего набора, может возвращать скалярные значения для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с помощью параметров OUTPUT. В следующем примере показано использование ВЫХОДНОГО параметра для возврата сериализованную модель R, используемый в качестве входных данных для сценария:  
  
Ресурсы, используемые внешних скриптов, настроив внешний пул ресурсов можно управлять. Дополнительные сведения см. в разделе [CREATE EXTERNAL RESOURCE POOL (Transact-SQL)](../../t-sql/statements/create-external-resource-pool-transact-sql.md). Сведения о рабочей нагрузке можно получить из представления каталога регулятора ресурсов, динамические Административные представления и счетчики. Дополнительные сведения см. в разделе [представления каталога регулятора ресурсов &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/resource-governor-catalog-views-transact-sql.md), [Resource Governor динамические административные представления &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/resource-governor-related-dynamic-management-views-transact-sql.md)и [ SQL Server, объект External Scripts](../../relational-databases/performance-monitor/sql-server-external-scripts-object.md).  

### <a name="monitor-script-execution"></a>Выполнение скрипта монитора

Мониторинг выполнения сценария с помощью [sys.dm_external_script_requests](../../relational-databases/system-dynamic-management-views/sys-dm-external-script-requests.md) и [sys.dm_external_script_execution_stats](../../relational-databases/system-dynamic-management-views/sys-dm-external-script-execution-stats.md). 

::: moniker range=">=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions"
### <a name="parameters-for-partition-modeling"></a>Параметры для моделирования секции

 В SQL Server 2019 года сейчас в общедоступной предварительной версии, можно задать два дополнительных параметра, позволяющие моделирование с использованием секционированных данных, где секции основаны на один или больше столбцов, которые вы предоставляете, которые естественным образом разделить набор данных на логические разделы создается и используется только во время выполнения скрипта. Столбцы, содержащие повторяющиеся значения для age, gender, географический регион, дата или время, приведено несколько примеров, которые предоставляются для секционированных наборов данных.
 
 Два параметра **input_data_1_partition_by_columns** и **input_data_1_order_by_columns**, где второй параметр используется для упорядочения результирующего набора. Параметры передаются в качестве входных данных для `sp_execute_external_script` с внешнего скрипта выполняется один раз для каждой секции. Дополнительные сведения и примеры см. в разделе [руководства: Создание моделей на основе секций](https://docs.microsoft.com/sql/advanced-analytics/tutorials/r-tutorial-create-models-per-partition.md).

 Можно выполнить сценарий в параллельном режиме, указав `@parallel=1`. Если входной запрос может выполняться параллельно, следует задать `@parallel=1` как часть аргументов `sp_execute_external_script`. По умолчанию оптимизатор запросов работает в `@parallel=1` в таблицах, имеющих более 256 строки, но если вы хотите обрабатывать это явным образом, этот сценарий включает в себя параметр в качестве демонстрации.

 > [!Tip]
> Для обучения workoads, можно использовать `@parallel` для любого сценария произвольные обучения, даже те, с помощью алгоритмов Майкрософт rx. Как правило только алгоритмы RevoScaleR (с префикса rx) предлагают параллелизм в сценариях обучения в SQL Server. Но с помощью новых параметров в SQL Server vNext, можно распараллеливать скрипт, который вызывает функции, разработанная специально не с данной возможностью.
::: moniker-end

### <a name="streaming-execution-for-r-and-python-scripts"></a>Потоковое выполнение сценариев R и Python  

Потоковая передача позволяет скрипт R или Python для работы с данными большего, чем может поместиться в памяти. Чтобы контролировать число строк, передаваемых во время потоковой передачи, укажите целочисленное значение для параметра, `@r_rowsPerRead` в `@params` коллекции.  Например если обучаем модель, которая использует очень широкие данных, вы можете изменить значение для чтения меньше строк, чтобы убедиться, что все строки могут отправляться в один блок данных. Этот параметр может использоваться для управления количеством строк считываются и обрабатываются одновременно, для устранения проблем производительности сервера. 
  
Оба `@r_rowsPerRead` параметр для потоковой передачи и `@parallel` аргумент следует учитывать указания. Для указания, должен быть применен должна существовать возможность создать план запроса SQL, который поддерживает параллельную обработку. Если это невозможно, невозможно включить параллельную обработку.  
  
> [!NOTE]  
>  Потоковая передача и параллельной обработки, поддерживаются только в выпуске Enterprise Edition. Можно включить параметры в запросах в выпуске Standard Edition без возникновения ошибки, но параметры имеют не эффект и скриптов R, запущенных в одном процессе.  
  
## <a name="restrictions"></a>Ограничения  


### <a name="data-types"></a>Типы данных

При использовании в входного запроса, или параметры не поддерживаются следующие типы данных **sp_execute_external_script** процедуры и возвращают ошибку неподдерживаемого типа.  

Обойти это ограничение **ПРИВЕДЕНИЯ** столбца или значение в поддерживаемый тип в [!INCLUDE[tsql](../../includes/tsql-md.md)] перед отправкой внешнего скрипта.  
  
-   **курсор**  
  
-   **timestamp**  
  
-   **datetime2**, **datetimeoffset**, **времени**  
  
-   **sql_variant**  
  
-   **текст**, **изображения**  
  
-   **xml**  
  
-   **HierarchyID**, **geometry**, **geography**  
  
-   Определяемые пользователем типы CLR

Как правило, любой результат набор, который не может быть сопоставлен [!INCLUDE[tsql](../../includes/tsql-md.md)] тип данных выводится как NULL.  

### <a name="restrictions-specific-to-r"></a>Ограничения, касающиеся R

Если входные данные включает **datetime** значений, которые не помещаются в R допустимого диапазона значений, значения преобразуются в **NA**. Это необходимо, так как [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] допускает более широкий диапазон значений, чем поддерживается в языке R.

Значения с плавающей запятой (например, `+Inf`, `-Inf`, `NaN`) не поддерживаются в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] несмотря на то, что оба языка используют IEEE 754. Текущее поведение просто отправляет значения [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] напрямую; в результате клиента SQL в [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] выдает ошибку. Таким образом, эти значения преобразуются в **NULL**.

## <a name="permissions"></a>Разрешения

Требуется **EXECUTE ANY EXTERNAL SCRIPT** разрешение базы данных.  

## <a name="examples"></a>Примеры

Этот раздел содержит примеры использования этой хранимой процедуры для выполнения сценариев R или Python с помощью [!INCLUDE[tsql](../../includes/tsql-md.md)].

### <a name="a-return-an-r-data-set-to-sql-server"></a>A. Возвращает набор данных R для SQL Server  

В следующем примере создается хранимая процедура, которая использует **sp_execute_external_script** для возвращения набора данных Iris, включенные в R, чтобы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  

```sql
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
GO
```

### <a name="b-generate-an-r-model-based-on-data-from-sql-server"></a>Б. Создание модели R на основе данных из SQL Server  

В следующем примере создается хранимая процедура, которая использует **sp_execute_external_script** для создания модели и возвращения модели для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  

> [!NOTE]
>  В этом примере требуется предварительное установки пакета e1071. Дополнительные сведения см. в разделе [установить дополнительные пакеты R на SQL Server](../../advanced-analytics/r/install-additional-r-packages-on-sql-server.md).

```sql
DROP PROC IF EXISTS generate_iris_model;
GO
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
GO
```

Чтобы создать аналогичную модель с помощью Python, необходимо изменить идентификатор языка с `@language=N'R'` на `@language = N'Python'` и внести необходимые изменения в аргумент `@script`. В противном случае все параметры будут работать так же, как в R.

### <a name="c-create-a-python-model-and-generate-scores-from-it"></a>В. Создание модели Python и формирование оценок из него

В этом примере показано, как использовать процедуру sp\_execute\_external\_script для создания оценок на основе простой модели Python. 

```sql
CREATE PROCEDURE [dbo].[py_generate_customer_scores]
AS
BEGIN

-- Input query to generate the customer data
DECLARE @input_query NVARCHAR(MAX) = N'SELECT customer, orders, items, cost FROM dbo.Sales.Orders'

EXEC sp_execute_external_script @language = N'Python', @script = N'
import pandas as pd
from sklearn.cluster import KMeans

# Get data from input query
customer_data = my_input_data

# Define the model
n_clusters = 4
est = KMeans(n_clusters=n_clusters, random_state=111).fit(customer_data[["orders","items","cost"]])
clusters = est.labels_
customer_data["cluster"] = clusters

OutputDataSet = customer_data
'
, @input_data_1 = @input_query
, @input_data_1_name = N'my_input_data'
WITH RESULT SETS (("CustomerID" int, "Orders" float,"Items" float,"Cost" float,"ClusterResult" float));
END;
GO
```

Заголовки столбцов, используемые в коде Python, не выводятся в SQL Server; Таким образом используйте инструкцию с РЕЗУЛЬТАТОМ, чтобы указать имена столбцов и типы данных для SQL.

Для оценки можно также применять собственную функцию [PREDICT](../../t-sql/queries/predict-transact-sql.md), которая обычно выполняется быстрее, так как не вызывает среду выполнения Python или R.

## <a name="see-also"></a>См. также

 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Типы данных и библиотек Python](../../advanced-analytics/python/python-libraries-and-data-types.md)  
 [Библиотеки R и типами данных R](../../advanced-analytics/r/r-libraries-and-data-types.md)  
 [Службы R SQL Server](../../advanced-analytics/r/sql-server-r-services.md)   
 [Известные проблемы для машинного обучения служб SQL Server](../../advanced-analytics/known-issues-for-sql-server-machine-learning-services.md)   
 [CREATE EXTERNAL LIBRARY &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-library-transact-sql.md)  
 [sp_prepare &#40;Transact SQL&#41;](../../relational-databases/system-stored-procedures/sp-prepare-transact-sql.md)   
 [sp_configure (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)   
 [Параметр конфигурации сервера external scripts enabled](../../database-engine/configure-windows/external-scripts-enabled-server-configuration-option.md)   
 [SERVERPROPERTY (Transact-SQL)](../../t-sql/functions/serverproperty-transact-sql.md)   
 [SQL Server, объект External Scripts](../../relational-databases/performance-monitor/sql-server-external-scripts-object.md)  
[sys.dm_external_script_requests](../../relational-databases/system-dynamic-management-views/sys-dm-external-script-requests.md)  
[sys.dm_external_script_execution_stats](../../relational-databases/system-dynamic-management-views/sys-dm-external-script-execution-stats.md) 
