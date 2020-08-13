---
title: sp_execute_external_script (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 08/06/2020
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: machine-learning-services
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
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=azuresqldb-mi-current||=sqlallproducts-allversions'
ms.openlocfilehash: 074836973123ae4f0f49acf72cf7bf6f56b17cf5
ms.sourcegitcommit: 9b41725d6db9957dd7928a3620fe4db41eb51c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/13/2020
ms.locfileid: "88180261"
---
# <a name="sp_execute_external_script-transact-sql"></a>sp_execute_external_script (Transact-SQL)
[!INCLUDE [SQL Server 2016 SQL MI](../../includes/applies-to-version/sqlserver2016-asdbmi.md)]

::: moniker range=">=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions"
Хранимая процедура **sp_execute_external_script** выполняет скрипт, предоставленный в качестве входного аргумента для процедуры, и используется с [службы машинного обучения](../../machine-learning/sql-server-machine-learning-services.md) и [расширениями языка](../../language-extensions/language-extensions-overview.md). 

Для Службы машинного обучения, [Python](../../machine-learning/concepts/extension-python.md) и [R](../../machine-learning/concepts/extension-r.md) поддерживают языки. Для расширений языка Java поддерживается, но должна быть определена с помощью [создания внешнего языка](../../t-sql/statements/create-external-language-transact-sql.md).

Для выполнения **sp_execute_external_script**необходимо сначала установить службы машинного обучения или расширения языка. Дополнительные сведения см. в статьях [установка SQL Server службы машинного обучения (Python и R) в Windows](../../machine-learning/install/sql-machine-learning-services-windows-install.md) и [Linux](../../linux/sql-server-linux-setup-machine-learning.md)или [Установка расширений языка SQL Server в Windows](../../language-extensions/install/install-sql-server-language-extensions-on-windows.md) и [Linux](../../linux/sql-server-linux-setup-language-extensions.md).
::: moniker-end

::: moniker range="=sql-server-2017||=sqlallproducts-allversions"
Хранимая процедура **sp_execute_external_script** выполняет скрипт, предоставленный в качестве входного аргумента для процедуры, и используется с [Службы машинного обучения](../../machine-learning/sql-server-machine-learning-services.md) в SQL Server 2017.

Для Службы машинного обучения, [Python](../../machine-learning/concepts/extension-python.md) и [R](../../machine-learning/concepts/extension-r.md) поддерживают языки.

Для выполнения **sp_execute_external_script**необходимо сначала установить службы машинного обучения. Дополнительные сведения см. [в разделе Install SQL Server службы машинного обучения (Python и R) в Windows](../../machine-learning/install/sql-machine-learning-services-windows-install.md).
::: moniker-end

::: moniker range="=sql-server-2016||=sqlallproducts-allversions"
Хранимая процедура **sp_execute_external_script** выполняет скрипт, предоставленный в качестве входного аргумента для процедуры, и используется со [службами R](../../machine-learning/r/sql-server-r-services.md) в SQL Server 2016.

Для служб R поддерживается язык [r](../../machine-learning/concepts/extension-r.md) .

Для выполнения **sp_execute_external_script**необходимо сначала установить службы R Services. Дополнительные сведения см. [в разделе Install SQL Server службы машинного обучения (Python и R) в Windows](../../machine-learning/install/sql-r-services-windows-install.md).
::: moniker-end

::: moniker range="=azuresqldb-mi-current||=sqlallproducts-allversions"
Хранимая процедура **sp_execute_external_script** выполняет скрипт, предоставленный в качестве входного аргумента для процедуры, и используется с [службы машинного обучения в управляемый экземпляр Azure SQL](/azure/azure-sql/managed-instance/machine-learning-services-overview).

Для Службы машинного обучения, [Python](../../machine-learning/concepts/extension-python.md) и [R](../../machine-learning/concepts/extension-r.md) поддерживают языки.

Для выполнения **sp_execute_external_script**необходимо сначала включить службы машинного обучения. Дополнительные сведения см. в [документации по службы машинного обучения в Azure SQL управляемый экземпляр](/azure/azure-sql/managed-instance/machine-learning-services-overview).
::: moniker-end

![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  

::: moniker range=">=sql-server-ver15||>=sql-server-linux-ver15||=azuresqldb-mi-current||=sqlallproducts-allversions"
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
::: moniker range="=sql-server-2016||=sqlallproducts-allversions"
## <a name="syntax-for-sql-server-2017-and-earlier"></a>Синтаксис для SQL Server 2017 и более ранних версий

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
 ** \@ Language** = N '*язык*'  
::: moniker range=">=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions"
 Указывает язык скрипта. *язык* имеет тип **sysname**. Допустимые значения: **R**, **Python**и любой язык, определенный с помощью [создания внешнего языка](../../t-sql/statements/create-external-language-transact-sql.md) (например, Java).
::: moniker-end
::: moniker range="=sql-server-2017||=sqlallproducts-allversions"
 Указывает язык скрипта. *язык* имеет тип **sysname**. В SQL Server 2017 допустимыми значениями являются **R** и **Python**.
::: moniker-end
::: moniker range="=sql-server-2016||=sqlallproducts-allversions"
 Указывает язык скрипта. *язык* имеет тип **sysname**. В SQL Server 2016 единственным допустимым значением является **R**.
::: moniker-end
::: moniker range="=azuresqldb-mi-current||=sqlallproducts-allversions"
 Указывает язык скрипта. *язык* имеет тип **sysname**. В Управляемый экземпляр SQL Azure допустимыми значениями являются **R** и **Python**.
::: moniker-end

 ** \@ script** = N "*Скрипт*" внешний язык скрипта, указанный в качестве входных литералов или переменных. *script* имеет тип **nvarchar (max)**.  

`[ @input_data_1 =  N'input_data_1' ]`Задает входные данные, используемые внешним скриптом в форме [!INCLUDE[tsql](../../includes/tsql-md.md)] запроса. Тип данных *input_data_1* — **nvarchar (max)**.

`[ @input_data_1_name = N'input_data_1_name' ]`Задает имя переменной, используемой для представления запроса, определенного параметром @input_data_1 . Тип данных переменной во внешнем скрипте зависит от языка. В случае с R входная переменная является кадром данных. В случае Python входные данные должны быть табличными. *input_data_1_name* имеет тип **sysname**.  Значение по умолчанию — *InputDataSet*.  

::: moniker range=">=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions"
`[ @input_data_1_order_by_columns = N'input_data_1_order_by_columns' ]`Используется для построения моделей отдельных секций. Указывает имя столбца, используемого для упорядочивания результирующего набора, например по названию продукта. Тип данных переменной во внешнем скрипте зависит от языка. В случае с R входная переменная является кадром данных. В случае Python входные данные должны быть табличными.

`[ @input_data_1_partition_by_columns = N'input_data_1_partition_by_columns' ]`Используется для построения моделей отдельных секций. Указывает имя столбца, используемого для сегментирования данных, таких как географическая область или дата. Тип данных переменной во внешнем скрипте зависит от языка. В случае с R входная переменная является кадром данных. В случае Python входные данные должны быть табличными. 
::: moniker-end

`[ @output_data_1_name =  N'output_data_1_name' ]`Задает имя переменной во внешнем скрипте, которая содержит данные, возвращаемые [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] при завершении вызова хранимой процедуры. Тип данных переменной во внешнем скрипте зависит от языка. Для R выходные данные должны быть кадром данных. Для Python выходные данные должны быть кадром данных Pandas. *output_data_1_name* имеет тип **sysname**.  Значение по умолчанию — *OutputDataSet*.  

`[ @parallel = 0 | 1 ]`Включите параллельное выполнение скриптов R, задав `@parallel` для параметра значение 1. Значение по умолчанию для этого параметра равно 0 (без параллелизма). Если `@parallel = 1` и выходные данные передаются непосредственно на клиентский компьютер, `WITH RESULT SETS` предложение является обязательным, и необходимо указать выходную схему.  

 + Для скриптов R, которые не используют функции RevoScaleR, использование `@parallel` параметра может оказаться полезным для обработки больших наборов данных, предполагая, что скрипт может быть тривиальным. Например, при использовании `predict` функции R с моделью для создания новых прогнозов установите в `@parallel = 1` качестве подсказки для обработчика запросов. Если запрос можно выполнить параллельно, строки распределяются в соответствии с параметром **MAXDOP** .  
  
 + Для скриптов R, использующих функции RevoScaleR, параллельная обработка обрабатывается автоматически, и не следует указывать `@parallel = 1` для вызова **sp_execute_external_script** .  
  
`[ @params = N'@parameter_name data_type [ OUT | OUTPUT ] [ ,...n ]' ]`Список объявлений входных параметров, используемых во внешнем скрипте.  
  
`[ @parameter1 = 'value1' [ OUT | OUTPUT ] [ ,...n ] ]`Список значений входных параметров, используемых внешним скриптом.  

## <a name="remarks"></a>Remarks

> [!IMPORTANT]
> Дерево запросов управляется машинным обучением SQL, и пользователи не могут выполнять произвольные операции с запросом.

::: moniker range=">=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions"
Используйте **sp_execute_external_script** для выполнения скриптов, написанных на поддерживаемом языке. Поддерживаемые языки — это **Python** и **R** , используемые с службы машинного обучения, а также любой язык, определенный с помощью [создания внешнего языка](../../t-sql/statements/create-external-language-transact-sql.md) (например, Java), используемого с расширениями языка.
::: moniker-end
::: moniker range="=sql-server-2017||=sqlallproducts-allversions"
Используйте **sp_execute_external_script** для выполнения скриптов, написанных на поддерживаемом языке. Поддерживаемые языки — **Python** и **R** в SQL Server 2017 службы машинного обучения.
::: moniker-end
::: moniker range="=sql-server-2016||=sqlallproducts-allversions"
Используйте **sp_execute_external_script** для выполнения скриптов, написанных на поддерживаемом языке. Единственным поддерживаемым языком является **R** в SQL Server 2016 R Services.
::: moniker-end
::: moniker range="=azuresqldb-mi-current||=sqlallproducts-allversions"
Используйте **sp_execute_external_script** для выполнения скриптов, написанных на поддерживаемом языке. Поддерживаемые языки — **Python** и **R** в Azure SQL управляемый экземпляр службы машинного обучения.
::: moniker-end

По умолчанию результирующие наборы, возвращаемые этой хранимой процедурой, выводятся с неименованными столбцами. Имена столбцов, используемые в скрипте, являются локальными для среды сценариев и не отражаются в выходном результирующем наборе. Чтобы присвоить имя столбцам результирующего набора, используйте `WITH RESULT SET` предложение [`EXECUTE`](../../t-sql/language-elements/execute-transact-sql.md) .

В дополнение к возврату результирующего набора можно возвращать скалярные значения, используя выходные параметры.

::: moniker range=">=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions"
Вы можете управлять ресурсами, используемыми внешними скриптами, настроив внешний пул ресурсов. Дополнительные сведения см. в статье [Создание внешнего пула ресурсов &#40;&#41;Transact-SQL ](../../t-sql/statements/create-external-resource-pool-transact-sql.md). Сведения о рабочей нагрузке можно получить из представлений каталога регулятора ресурсов, представления динамического административного представления и счетчиков. Дополнительные сведения см. в статьях [Resource Governor представления каталога &#40;&#41;Transact-SQL ](../../relational-databases/system-catalog-views/resource-governor-catalog-views-transact-sql.md), [Resource Governor связанные динамические административные представления &#40;transact-sql&#41;](../../relational-databases/system-dynamic-management-views/resource-governor-related-dynamic-management-views-transact-sql.md)и [SQL Server, External Scripts Object](../../relational-databases/performance-monitor/sql-server-external-scripts-object.md).  
::: moniker-end

### <a name="monitor-script-execution"></a>Мониторинг выполнения скрипта

Мониторинг выполнения скрипта с помощью [sys. dm_external_script_requests](../../relational-databases/system-dynamic-management-views/sys-dm-external-script-requests.md) и [sys. dm_external_script_execution_stats](../../relational-databases/system-dynamic-management-views/sys-dm-external-script-execution-stats.md).

::: moniker range=">=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions"
### <a name="parameters-for-partition-modeling"></a>Параметры моделирования секций

Можно задать два дополнительных параметра, которые позволяют моделировать секционированные данные, где секции основаны на одном или нескольких столбцах, которые позволяют естественно сегментировать набор данных в логические секции, созданные и используемые только во время выполнения скрипта. Столбцы, содержащие повторяющиеся значения для Age, Gender, географического региона, даты или времени, представляют собой несколько примеров, которые применяются к секционированным наборам данных.

Эти два параметра являются **input_data_1_partition_by_columns** и **input_data_1_order_by_columns**, где второй параметр используется для упорядочивания результирующего набора. Параметры передаются в качестве входных данных во `sp_execute_external_script` внешний скрипт, который выполняется один раз для каждой секции. Дополнительные сведения и примеры см. в разделе [учебник. Создание моделей на основе секций](https://docs.microsoft.com/sql/machine-learning/tutorials/r-tutorial-create-models-per-partition).

Скрипт можно выполнить параллельно, указав `@parallel=1` . Если входной запрос можно выполнить параллельно, следует задать в `@parallel=1` качестве части аргументов значение `sp_execute_external_script` . По умолчанию оптимизатор запросов работает в `@parallel=1` таблицах, имеющих более 256 строк, но если вы хотите, чтобы эта возможность была бы обработана явно, этот скрипт включает параметр в качестве демонстрации.

> [!Tip]
> Для рабочих нагрузок обучения можно использовать `@parallel` с любым произвольным скриптом обучения, даже при использовании алгоритмов, отличных от Microsoft RX. Как правило, в SQL Server параллелизм в скриптах обучения предусмотрен только в алгоритмах RevoScaleR (с префиксом RX). Но с новыми параметрами в SQL Server 2019 и более поздних версиях можно параллелизации скрипта, который вызывает функции, не разработанные специально для этой возможности.
::: moniker-end

### <a name="streaming-execution-for-python-and-r-scripts"></a>Потоковое выполнение для скриптов Python и R  

Потоковая передача позволяет скрипту Python или R работать с большим объемом данных, чем может уместиться в памяти. Для управления числом строк, передаваемых во время потоковой передачи, укажите целочисленное значение параметра `@r_rowsPerRead` в `@params` коллекции.  Например, при обучении модели, использующей очень широкие данные, можно изменить значение для чтения меньшего количества строк, чтобы все строки можно было отправить в один блок данных. Этот параметр также можно использовать для управления числом строк, считываемых и обрабатываемых одновременно, чтобы снизить производительность сервера. 
  
Как `@r_rowsPerRead` параметр для потоковой передачи, так и `@parallel` аргумент должны рассматриваться как подсказки. Чтобы подсказка была применена, необходимо создать план SQL-запроса, включающий параллельную обработку. Если это невозможно, параллельная обработка не может быть включена.  
  
> [!NOTE]  
> Потоковая передача и параллельная обработка поддерживаются только в выпуске Enterprise Edition. Вы можете включить параметры в запросы в выпуске Standard без возникновения ошибки, но параметры не будут действовать, а скрипты R выполняются в одном процессе.  
  
## <a name="restrictions"></a>Ограничения  

### <a name="data-types"></a>Типы данных

Следующие типы данных не поддерживаются при использовании входного запроса или параметров **sp_execute_external_script** процедуры и возвращают ошибку неподдерживаемого типа.  

В качестве обходного **CAST** решения [!INCLUDE[tsql](../../includes/tsql-md.md)] перед отправкой в внешний скрипт необходимо привести столбец или значение к поддерживаемому типу.  
  
+ **курсор**  
  
+ **timestamp**  
  
+ **datetime2**, **DateTimeOffset**, **время**  
  
+ **sql_variant**  
  
+ **текст**, **изображение**  
  
+ **xml**  
  
+ **hierarchyid**, **геометрия**, **География**  
  
+ Определяемые пользователем типы CLR

В общем случае любой результирующий набор, который не может быть сопоставлен с [!INCLUDE[tsql](../../includes/tsql-md.md)] типом данных, выводится как null.  

### <a name="restrictions-specific-to-r"></a>Ограничения, относящиеся к R

Если входные данные содержат значения **типа DateTime** , которые не соответствуют допустимому диапазону значений в R, то значения преобразуются в **НД**. Это необходимо, поскольку машинное обучение SQL допускает больший диапазон значений, чем поддерживается в языке R.

Значения float (например,, `+Inf` , `-Inf` `NaN` ) не поддерживаются в машинном обучении SQL, хотя оба языка используют стандарт IEEE 754. Текущее поведение просто отправляет значения непосредственно в SQL; в результате клиент SQL выдает ошибку. Поэтому эти значения преобразуются в **значение NULL**.

## <a name="permissions"></a>Разрешения

Необходимо разрешение на **выполнение любых внешних скриптов** для базы данных.  

## <a name="examples"></a>Примеры

В этом разделе содержатся примеры того, как эта хранимая процедура может использоваться для выполнения скриптов R или Python с помощью [!INCLUDE[tsql](../../includes/tsql-md.md)] .

### <a name="a-return-an-r-data-set-to-sql-server"></a>A. Возврат набора данных R в SQL Server  

В следующем примере создается хранимая процедура, которая использует **sp_execute_external_script** для возврата набора данных IRI, входящего в состав R.  

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

### <a name="b-create-a-python-model-and-generate-scores-from-it"></a>Б. Создание модели Python и формирование оценок на ее основе

В этом примере показано, как использовать `sp_execute_external_script` для создания оценок в простой модели Python.

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

Заголовки столбцов, используемые в коде Python, не выводятся в SQL Server; Поэтому для указания имен столбцов и типов данных, используемых SQL, используйте инструкцию WITH RESULT.

::: moniker range=">=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions"
### <a name="c-generate-an-r-model-based-on-data-from-sql-server"></a>В. Создание модели R на основе данных из SQL Server  

В следующем примере создается хранимая процедура, которая использует **sp_execute_external_script** для создания модели IRI и возврата модели.  

> [!NOTE]
> В этом примере требуется дополнительная установка пакета e1071. Дополнительные сведения см. [в статье Установка дополнительных пакетов R на SQL Server](../../machine-learning/package-management/install-additional-r-packages-on-sql-server.md).

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
::: moniker-end

Для оценки можно также применять собственную функцию [PREDICT](../../t-sql/queries/predict-transact-sql.md), которая обычно выполняется быстрее, так как не вызывает среду выполнения Python или R.

## <a name="see-also"></a>См. также раздел

+ [Машинное обучение SQL](../../machine-learning/index.yml)
+ [Расширения языка SQL Server](../../language-extensions/language-extensions-overview.md). 
+ [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
+ [Создание внешней библиотеки &#40;&#41;Transact-SQL](../../t-sql/statements/create-external-library-transact-sql.md)  
+ [sp_prepare &#40;Transact SQL&#41;](../../relational-databases/system-stored-procedures/sp-prepare-transact-sql.md)   
+ [sp_configure (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)   
+ [Параметр конфигурации сервера «external scripts enabled»](../../database-engine/configure-windows/external-scripts-enabled-server-configuration-option.md)   
+ [SERVERPROPERTY (Transact-SQL)](../../t-sql/functions/serverproperty-transact-sql.md)   
+ [SQL Server, объект External Scripts](../../relational-databases/performance-monitor/sql-server-external-scripts-object.md)  
+ [sys.dm_external_script_requests](../../relational-databases/system-dynamic-management-views/sys-dm-external-script-requests.md)  
+ [sys.dm_external_script_execution_stats](../../relational-databases/system-dynamic-management-views/sys-dm-external-script-execution-stats.md) 
