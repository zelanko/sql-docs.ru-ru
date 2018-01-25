---
title: "sp_execute_external_script (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 01/22/2018
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
ms.openlocfilehash: 283db0150613d9d956cf5b0ec6b6fd295bc4444b
ms.sourcegitcommit: d7dcbcebbf416298f838a39dd5de6a46ca9f77aa
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2018
---
# <a name="spexecuteexternalscript-transact-sql"></a>sp_execute_external_script (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Выполняет сценарий, приведенный в качестве аргумента во внешнем расположении. Сценарий должен быть написан поддерживаемых и зарегистрированных языка. Для выполнения **sp_execute_external_script**, сначала необходимо включить внешние скрипты с помощью инструкции, `sp_configure 'external scripts enabled', 1;`.  
  
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
  
 [ @input_data_1_name = N'*input_data_1_name*' ]  
 Задает имя переменной, которая используется для представления запроса, определенного по @input_data_1. Тип данных переменной в внешнего скрипта зависит от языка. В случае R Входная переменная является кадра данных. В случае Python он должен быть табличной. *input_data_1_name* — **sysname**.  
  
 Значение по умолчанию — `InputDataSet`.  
  
 [ @input_data_1 =  N'*input_data_1*' ]  
 Задает входные данные, используемые внешних скриптов в виде [!INCLUDE[tsql](../../includes/tsql-md.md)] запроса. Тип данных *input_data_1* — **nvarchar(max)**.
  
 [ @output_data_1_name = N'*output_data_1_name*"]  
 Указывает имя переменной в внешний скрипт, который содержит данные, возвращаемые для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] после завершения вызова хранимой процедуры. Тип данных переменной в внешнего скрипта зависит от языка. R выходные данные должны быть кадра данных. Python выходные данные должны быть pandas кадра данных. *output_data_1_name* — **sysname**.  
  
 Значение по умолчанию — «OutputDataSet».  
  
 [ @parallel = 0 | 1], включите параллельное выполнение R-скриптов, задав `@parallel` значение 1. Значение по умолчанию для этого параметра равно 0 (нет параллелизма).  
  
 Для сценариев R, не следует использовать функции RevoScaleR, с помощью `@parallel` параметр может быть полезным для обработки больших наборов данных, при условии, что скрипт элементарно могут выполняться параллельно. Например, при использовании R `predict` функция с моделью, чтобы создать новые прогнозы, задайте `@parallel = 1` как подсказку для ядро запросов. Если запрос может выполняться параллельно, строки распределены в соответствии с **MAXDOP** параметр.  
  
 Если `@parallel = 1` и выходные данные передаются непосредственно на клиентском компьютере, а затем `WITH RESULTS SETS` предложение является обязательным и должен быть указан схему выходных данных.  
  
 Для сценариев R, использовать функции RevoScaleR, параллельная обработка осуществляется автоматически и не следует указывать `@parallel = 1` для **sp_execute_external_script** вызова.  
  
 [ @params = N' *@parameter_name data_type* [OUT | ВЫВОД] [,.. .n] "]  
 Список объявлений входных параметров, используемых в внешних скриптов.  
  
 [ @parameter1 = "*значение1*" [OUT | ВЫВОД] [,.. .n]]  
 Список значений для входных параметров, используемых внешних скриптов.  

## <a name="remarks"></a>Remarks

Используйте **sp_execute_external_script** для выполнения сценариев, написанных на поддерживаемом языке. В настоящее время поддерживаемые языки, R для SQL Server 2016 и Python и R для 2017 г. SQL Server. 

> [!IMPORTANT]
> Дерево запроса управляется [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и пользователи не могут выполнять произвольные операции на основе запроса. 

По умолчанию результирующие наборы, возвращаемые этой хранимой процедурой при выводе безымянные столбцы. Имена столбцов, используемых в сценарии являются локальными для среда скриптов и не отражаются в выходные файлов результирующего набора. Чтобы присвоить имя результирующего набора столбцов, используйте `WITH RESULTS SET` предложения [ `EXECUTE` ](../../t-sql/language-elements/execute-transact-sql.md).
  
 Помимо возврата результирующего набора, можно вернуть скалярные значения для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с помощью параметров OUTPUT. В следующем примере показано использование ВЫХОДНОГО параметра для возврата сериализованный R-модели, используемой в качестве входных данных для сценария:  

В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] включает в себя серверный компонент устанавливается вместе с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], а также набор инструментов рабочей станции и библиотек подключений, которые подключаются к высокопроизводительной среде из специалист по анализу данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Необходимо установить машинного обучения компонентов при [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] программу установки, чтобы разрешить выполнение внешних скриптов. Дополнительные сведения см. в разделе [Настройка служб SQL Server Machine Learning](../../advanced-analytics/r/set-up-sql-server-r-services-in-database.md).  
  
Можно выбрать ресурсы, используемые внешних скриптов путем настройки внешнего пула ресурсов. Дополнительные сведения см. в разделе [CREATE EXTERNAL RESOURCE POOL (Transact-SQL)](../../t-sql/statements/create-external-resource-pool-transact-sql.md). Сведения о рабочей нагрузки можно получить из представления каталога регулятора ресурсов, динамические административные Представления и счетчики. Дополнительные сведения см. в разделе [представления каталога регулятора ресурсов &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/resource-governor-catalog-views-transact-sql.md), [Регулятора ресурсов, связанные с динамическим административным представлениям &#40; Transact-SQL &#41; ](../../relational-databases/system-dynamic-management-views/resource-governor-related-dynamic-management-views-transact-sql.md), и [SQL Server, внешние сценарии объекта](../../relational-databases/performance-monitor/sql-server-external-scripts-object.md).  

Монитор выполнения скрипта с помощью [sys.dm_external_script_requests](../../relational-databases/system-dynamic-management-views/sys-dm-external-script-requests.md) и [sys.dm_external_script_execution_stats](../../relational-databases/system-dynamic-management-views/sys-dm-external-script-execution-stats.md). 

## <a name="streaming-execution-for-r-and-python-scripts"></a>Потоковое выполнение скриптов R и Python  

Потоковая передача позволяет выполнение скрипта R или Python для работы с большим объемом данных, чем может поместиться в памяти. Чтобы управлять количеством строк, переданных во время потоковой передачи, укажите целочисленное значение для параметра, `@r_rowsPerRead` в `@params` коллекции.  Например если для обучения модели, использующей данные очень широкие может изменить значение для чтения меньшее число строк, чтобы гарантировать отправку всех строк в одном блоке данных. Этот параметр также можно использовать для управления число строк считываемых и обрабатываемых за один раз для устранения проблем с производительностью сервера. 
  
Оба `@r_rowsPerRead` параметр для потоковой передачи и `@parallel` аргумент следует учитывать указания. Для указания, должна быть применена должна существовать возможность создать план запроса SQL, который поддерживает параллельную обработку. Если это невозможно, невозможно включить параллельной обработки.  
  
> [!NOTE]  
>  Потоковая передача и параллельную обработку поддерживаются только в выпуске Enterprise Edition. Параметры можно включить в запросах в выпуске Standard Edition без возникновения ошибки, но параметры имеют не эффект и сценариев R выполняются в одном процессе.  
  
## <a name="restrictions"></a>Ограничения  


### <a name="data-types"></a>Типы данных

При использовании входного запроса, или параметры не поддерживаются следующие типы данных `sp_execute_external_script` процедуры и возвращают ошибку неподдерживаемого типа.  

Чтобы избежать этого **ПРИВЕДЕНИЯ** столбца или значение в поддерживаемый тип в [!INCLUDE[tsql](../../includes/tsql-md.md)] перед отправкой внешних скриптов.  
  
-   **курсор**  
  
-   **timestamp**  
  
-   **datetime2**, **datetimeoffset**, **time**  
  
-   **sql_variant**  
  
-   **text**, **image**  
  
-   **xml**  
  
-   **HierarchyID**, **geometry**, **geography**  
  
-   Определяемые пользователем типы CLR

В общем случае любой результирующего набора, который не может быть сопоставлен с [!INCLUDE[tsql](../../includes/tsql-md.md)] тип данных выводится как NULL.  

### <a name="restrictions-specific-to-r"></a>Ограничения, относящиеся к R

Если входные данные включает **datetime** значения, которые не помещаются в R допустимого диапазона значений, значения преобразуются в **NA**. Это необходимо, поскольку [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] позволяет использовать больший диапазон значений, чем поддерживается в языке R.

Значения с плавающей запятой (например, `+Inf`, `-Inf`, `NaN`) не поддерживаются в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] даже если оба языка используют IEEE 754. Текущее поведение отправляются только значения [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] напрямую; таким образом, клиент SQL в [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] вызывает ошибку. Таким образом, эти значения преобразуются в **NULL**.

## <a name="permissions"></a>Разрешения

Требуется **EXECUTE ANY EXTERNAL SCRIPT** разрешение базы данных.  

## <a name="examples"></a>Примеры

Этот раздел содержит примеры использования этой хранимой процедуры для выполнения сценариев R или Python, с помощью [!INCLUDE[tsql](../../includes/tsql-md.md)].

### <a name="a-return-an-r-data-set-to-sql-server"></a>A. Возвращает набор данных R для SQL Server  

В следующем примере создается хранимая процедура, которая использует **sp_execute_external_script** для возврата набора данных Iris, входящий в состав R для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  

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

### <a name="b-generate-an-r-model-based-on-data-from-sql-server"></a>Б. Создание R-модели на основе данных из SQL Server  

В следующем примере создается хранимая процедура, которая использует **sp_execute_external_script** для формирования iris модели и модели, чтобы вернуть [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  

> [!NOTE]
>  В этом примере требуется предварительное установки пакета e1071. Дополнительные сведения см. в разделе [Установка дополнительных пакетов R в SQL Server](../../advanced-analytics/r/install-additional-r-packages-on-sql-server.md).

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

Чтобы создать аналогичной модели с помощью Python, нужно изменить идентификатор языка из `@language=N'R'` для `@language = N'Python'`и внесите необходимые изменения `@script` аргумент. В противном случае все параметры работают одинаково как для R.

### <a name="c-create-a-python-model-and-generate-scores-from-it"></a>В. Создайте модель Python и формирования оценок от него

В этом примере показано, как использовать sp\_выполнение\_внешних\_скрипт для формирования оценок на простую модель Python. 

```sql
CREATE PROCEDURE [dbo].[py_generate_customer_scores]
AS
BEGIN

## Input query to generate the customer data
DECLARE @input_query NVARCHAR(MAX) = N'SELECT customer, orders, items, cost FROM dbo.Sales.Orders`

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

Используется в коде Python заголовки столбцов не являются выходные данные в SQL Server. Таким образом инструкция с РЕЗУЛЬТАТЫ для указания имен столбцов и типов данных SQL для использования.

Для оценки, можно также использовать собственный [PREDICT](../../t-sql/queries/predict-transact-sql.md) функции, которая обычно выполняется быстрее, так как позволяет избежать вызова среды выполнения Python или R.

## <a name="see-also"></a>См. также:

 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Библиотеки Python и типы данных](../../advanced-analytics/python/python-libraries-and-data-types.md)  
 [Библиотеки R и типами данных R](../../advanced-analytics/r/r-libraries-and-data-types.md)  
 [Службы R SQL Server](../../advanced-analytics/r/sql-server-r-services.md)   
 [Известные проблемы для обучения службы машины SQL Server](../../advanced-analytics/known-issues-for-sql-server-machine-learning-services.md)   
 [СОЗДАТЬ ВНЕШНЮЮ БИБЛИОТЕКУ &#40; Transact-SQL &#41;](../../t-sql/statements/create-external-library-transact-sql.md)  
 [sp_prepare &#40; Transact SQL &#41;](../../relational-databases/system-stored-procedures/sp-prepare-transact-sql.md)   
 [sp_configure (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)   
 [Параметр конфигурации сервера External scripts enabled](../../database-engine/configure-windows/external-scripts-enabled-server-configuration-option.md)   
 [SERVERPROPERTY (Transact-SQL)](../../t-sql/functions/serverproperty-transact-sql.md)   
 [SQL Server, объект External Scripts](../../relational-databases/performance-monitor/sql-server-external-scripts-object.md)  
[sys.dm_external_script_requests](../../relational-databases/system-dynamic-management-views/sys-dm-external-script-requests.md)  
[sys.dm_external_script_execution_stats](../../relational-databases/system-dynamic-management-views/sys-dm-external-script-execution-stats.md) 
