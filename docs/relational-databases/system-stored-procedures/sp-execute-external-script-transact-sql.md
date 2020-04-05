---
title: sp_execute_external_script (Трансакт-СЗЛ) Документы Майкрософт
ms.custom: ''
ms.date: 11/04/2019
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: machine-learning
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
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions||=azuresqldb-mi-current'
ms.openlocfilehash: 8800df26e505f1fffe25e6f65218481e7a8158f0
ms.sourcegitcommit: 68583d986ff5539fed73eacb7b2586a71c37b1fa
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/04/2020
ms.locfileid: "80663013"
---
# <a name="sp_execute_external_script-transact-sql"></a>sp_execute_external_script (Transact-SQL)

[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

::: moniker range=">=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions"
Процедура **sp_execute_external_script** сохранена выполняет сценарий, представленный в качестве аргумента ввода процедуры, и используется с [службами машинного обучения](../../machine-learning/index.yml) и [языковыми расширениями.](../../language-extensions/language-extensions-overview.md) 

Для служб машинного обучения [Python](../../machine-learning/concepts/extension-python.md) и [R](../../machine-learning/concepts/extension-r.md) поддерживаются на языках. Для языковых расширений Java поддерживается, но должна быть определена с [помощью CREATE EXTERNAL LANGUAGE.](../../t-sql/statements/create-external-language-transact-sql.md)

Для выполнения **sp_execute_external_script**необходимо сначала установить службы машинного обучения или языковые расширения. Для получения дополнительной информации, [Linux](../../linux/sql-server-linux-setup-machine-learning.md) [Install SQL Server Language Extensions on Windows](../../language-extensions/install/install-sql-server-language-extensions-on-windows.md) [Linux](../../linux/sql-server-linux-setup-language-extensions.md) [см.](../../machine-learning/install/sql-machine-learning-services-windows-install.md)
::: moniker-end

::: moniker range="=sql-server-2017||=sqlallproducts-allversions"
Процедура **sp_execute_external_script** сохранению выполняет сценарий, представленный в качестве аргумента ввода процедуры, и используется с [службами машинного обучения](../../machine-learning/index.yml) на сервере S'L Server 2017. 

Для служб машинного обучения [Python](../../machine-learning/concepts/extension-python.md) и [R](../../machine-learning/concepts/extension-r.md) поддерживаются на языках. 

Для выполнения **sp_execute_external_script**необходимо сначала установить службы машинного обучения. Для получения дополнительной информации [см.](../../machine-learning/install/sql-machine-learning-services-windows-install.md)
::: moniker-end

::: moniker range="=sql-server-2016||=sqlallproducts-allversions"
Процедура **sp_execute_external_script** сохранена выполняет сценарий, представленный в качестве аргумента ввода процедуры, и используется с [R-сервисами](../../machine-learning/r/sql-server-r-services.md) на сервере S'L Server 2016.

Для R-сервисов [R](../../machine-learning/concepts/extension-r.md) является поддерживаемым языком.

Для выполнения **sp_execute_external_script**необходимо сначала установить R-сервисы. Для получения дополнительной информации [см.](../../machine-learning/install/sql-r-services-windows-install.md)
::: moniker-end

 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  

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
::: moniker range="=sql-server-2016||=sqlallproducts-allversions"
## <a name="syntax-for-2017-and-earlier"></a>Синтаксис на 2017 год и более ранний

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
 язык n'*язык*' ** \@**  
::: moniker range=">=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions"
 Указывает язык скрипта. *язык* **sysname**. Действительные **значения: R,** **Python**и любой язык, определяемый [CREATE EXTERNAL LANGUAGE](../../t-sql/statements/create-external-language-transact-sql.md) (например, Java).
::: moniker-end
::: moniker range="=sql-server-2017||=sqlallproducts-allversions"
 Указывает язык скрипта. *язык* **sysname**. В сервере S'L Server 2017 действительными значениями являются **R** и **Python.**
::: moniker-end
::: moniker range="=sql-server-2016||=sqlallproducts-allversions"
 Указывает язык скрипта. *язык* **sysname**. В s'L Server 2016 единственным допустимое значение мною составляет **R**.
::: moniker-end

 скрипт n'*скрипт*'Внешний язык, указанный в буквальном или переменном ввода. ** \@** *скрипт* **nvarchar (max)**.  

`[ @input_data_1 =  N'input_data_1' ]`Определяет данные ввода, используемые внешним скриптом, [!INCLUDE[tsql](../../includes/tsql-md.md)] в виде запроса. Тип данных *input_data_1* **nvarchar (max)**.

`[ @input_data_1_name = N'input_data_1_name' ]`Указано имя переменной, используемой для представления запроса, определяемого @input_data_1. Тип данных переменной во внешнем скрипте зависит от языка. В случае R переменной ввода является рамка данных. В случае Python вход должен быть табулярным. *input_data_1_name* **sysname**.  Значение по умолчанию *— ВхотодатSet*.  

::: moniker range=">=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions"
`[ @input_data_1_order_by_columns = N'input_data_1_order_by_columns' ]`Используется для построения моделей для разделов. Определяется имя столбца, используемого для заказа набора результатов, например по названию продукта. Тип данных переменной во внешнем скрипте зависит от языка. В случае R переменной ввода является рамка данных. В случае Python вход должен быть табулярным.

`[ @input_data_1_partition_by_columns = N'input_data_1_partition_by_columns' ]`Используется для построения моделей для разделов. Определяется название столбца, используемого для сегмента данных, например географической области или даты. Тип данных переменной во внешнем скрипте зависит от языка. В случае R переменной ввода является рамка данных. В случае Python вход должен быть табулярным. 
::: moniker-end

`[ @output_data_1_name =  N'output_data_1_name' ]`Условляет сярприз переменной во внешнем скрипте, содержащем данные, которые должны быть возвращены [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] по завершении вызова сохраненной процедуры. Тип данных переменной во внешнем скрипте зависит от языка. Для R выход должен быть рамкой данных. Для Python выход должен быть рамкой данных панд. *output_data_1_name* **sysname**.  Значение по умолчанию — *OutputDataSet*.  

`[ @parallel = 0 | 1 ]`Включить параллельное выполнение R-скриптов, установив `@parallel` параметр до 1. По умолчанию для этого параметра 0 (без параллелизма). Если `@parallel = 1` выход передается непосредственно к клиентской машине, то требуется `WITH RESULT SETS` оговорка и должна быть указана схема вывода.  

 + Для R-скриптов, которые не используют функции RevoScaleR, использование `@parallel` параметра может быть полезным для обработки больших наборов данных, предполагая, что сценарий может быть тривиально параллелизирован. Например, при использовании функции R `predict` с моделью для создания новых прогнозов, установите `@parallel = 1` как подсказку движку запроса. Если запрос можно параллельно, строки распределяются в соответствии с настройками **MAXDOP.**  
  
 + Для R-скриптов, которые используют функции RevoScaleR, параллельная обработка обрабатывается автоматически, и вы не должны указывать `@parallel = 1` **sp_execute_external_script** вызова.  
  
`[ @params = N'@parameter_name data_type [ OUT | OUTPUT ] [ ,...n ]' ]`Список деклараций параметров ввода, которые используются во внешнем скрипте.  
  
`[ @parameter1 = 'value1' [ OUT | OUTPUT ] [ ,...n ] ]`Список значений для параметров ввода, используемых внешним скриптом.  

## <a name="remarks"></a>Примечания

> [!IMPORTANT]
> Дерево запроса контролируется [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и пользователи не могут выполнять произвольные операции в запросе. 

::: moniker range=">=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions"
Используйте **sp_execute_external_script** для выполнения скриптов, написанных на поддерживаемом языке. Поддерживаемые языки используются **Python** и **R** с службами машинного обучения, а любой язык, определяемый [CREATE EXTERNAL LANGUAGE](../../t-sql/statements/create-external-language-transact-sql.md) (например, Java), используется с языковыми расширениями.
::: moniker-end
::: moniker range="=sql-server-2017||=sqlallproducts-allversions"
Используйте **sp_execute_external_script** для выполнения скриптов, написанных на поддерживаемом языке. Поддерживаемые языки — **это Python** и **R** в службах машинного обучения S'L Server 2017.
::: moniker-end
::: moniker range="=sql-server-2016||=sqlallproducts-allversions"
Используйте **sp_execute_external_script** для выполнения скриптов, написанных на поддерживаемом языке. Единственным поддерживаемым языком является **R** в S'L Server 2016 R Services.
::: moniker-end

По умолчанию наборы результатов, возвращающиеся этой сохраненной процедурой, выходят с неназванными столбцов. Имена столбцов, используемые в скрипте, являются локальными для среды скриптов и не отражаются в наборе результатов. Чтобы назвать столбцы набора `WITH RESULT SET` результатов, [`EXECUTE`](../../t-sql/language-elements/execute-transact-sql.md)используйте оговорку .

В дополнение к возвращению набора результатов можно вернуть [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] значения масштабирования, используя параметры OUTPUT. 
  
Вы можете управлять ресурсами, используемыми внешними скриптами, настраивая внешний пул ресурсов. Для получения дополнительной информации см [&#41;&#40;. ](../../t-sql/statements/create-external-resource-pool-transact-sql.md) Информацию о рабочей нагрузке можно получить из представлений каталога губернатора ресурса, DMV и счетчиков. Для получения дополнительной информации [см. Каталог ресурсов губернатора &#40;&#41;, ](../../relational-databases/system-catalog-views/resource-governor-catalog-views-transact-sql.md)ресурс губернатор [Связанные динамические представления управления &#40;&#41;, ](../../relational-databases/system-dynamic-management-views/resource-governor-related-dynamic-management-views-transact-sql.md)и [S'L Server, Внешние сценарии объекта](../../relational-databases/performance-monitor/sql-server-external-scripts-object.md).  

### <a name="monitor-script-execution"></a>Выполнение сценария мониторинга

Мониторинг выполнения скрипта с помощью [sys.dm_external_script_requests](../../relational-databases/system-dynamic-management-views/sys-dm-external-script-requests.md) и [sys.dm_external_script_execution_stats](../../relational-databases/system-dynamic-management-views/sys-dm-external-script-execution-stats.md). 

::: moniker range=">=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions"
### <a name="parameters-for-partition-modeling"></a>Параметры моделирования разделов

Можно установить два дополнительных параметра, которые позволяют моделировать на разделенных данных, где разделы основаны на одном или нескольких столбцах, которые естественным образом сегментируют набор данных на логические разделы, созданные и используемые только при выполнении скрипта. Столбцы, содержащие повторяющиеся значения для возраста, пола, географического региона, даты или времени, являются несколькими примерами, которые поддаются разделенным наборам данных.
 
Эти два параметра **input_data_1_partition_by_columns** и **input_data_1_order_by_columns,** где второй параметр используется для заказа набора результатов. Параметры передаются в виде `sp_execute_external_script` входов с внешним исследующим скриптом один раз для каждого раздела. Для получения дополнительной [информации](https://docs.microsoft.com/sql/machine-learning/tutorials/r-tutorial-create-models-per-partition)и примеров см.

Вы можете выполнять сценарий `@parallel=1`параллельно, указывая . Если запрос ввода можно параллельовать, `@parallel=1` следует установить в `sp_execute_external_script`качестве части аргументов для . По умолчанию оптимизатор запроса работает под `@parallel=1` таблицами, имеющими более 256 строк, но если вы хотите обрабатывать это явно, этот скрипт включает параметр в качестве демонстрации.

> [!Tip]
> Для рабочих нагрузок обучения можно использовать `@parallel` с любым произвольным скриптом обучения, даже при использовании алгоритмов, отличных от Microsoft RX. Как правило, в SQL Server параллелизм в скриптах обучения предусмотрен только в алгоритмах RevoScaleR (с префиксом RX). Но с новыми параметрами в s'L Server vNext можно параллелизировать скрипт, который вызывает функции, специально не разработанные с этой возможностью.
::: moniker-end

### <a name="streaming-execution-for-python-and-r-scripts"></a>Потоковое выполнение для скриптов Python и R  

Потоковая передача позволяет скрипту Python или R работать с большим количеством данных, чем может поместиться в памяти. Чтобы контролировать количество строк, пройдено во время потоковой передачи, `@params` укажите в коллекции целый ряд значения параметра. `@r_rowsPerRead`  Например, если вы обучаете модель, используюую очень широкие данные, можно настроить значение для чтения меньшего количества строк, чтобы гарантировать, что все строки могут быть отправлены в одном фрагменте данных. Этот параметр можно также использовать для управления числом строк, считываемых и обрабатываемых за один раз, чтобы смягчить проблемы с производительностью сервера. 
  
Как `@r_rowsPerRead` параметр для `@parallel` потоковой передачи, так и аргумент следует рассматривать как подсказки. Для нанесения подсказки необходимо создать план запроса S'L, включающий параллельную обработку. Если это невозможно, не удается зафиксировать параллельную обработку.  
  
> [!NOTE]  
> Потоковая и параллельная обработка поддерживаются только в Enterprise Edition. Параметры можно включить в запросы в Standard Edition без ошибки, но параметры не имеют эффекта, и R-скрипты работают в одном процессе.  
  
## <a name="restrictions"></a>Ограничения  

### <a name="data-types"></a>Типы данных

Следующие типы данных не поддерживаются при использовании в вхотворном запросе или параметрах **sp_execute_external_script** процедуры и возвращают ошибку неподдерживаемого типа.  

Как обходной путь, **CAST** столбец или [!INCLUDE[tsql](../../includes/tsql-md.md)] значение для поддерживаемого типа в перед отправкой его на внешний скрипт.  
  
-   **Курсор**  
  
-   **Timestamp**  
  
-   **datetime2**, **datetimeoffset**, **время**  
  
-   **Sql_variant**  
  
-   **текст**, **изображение**  
  
-   **xml**  
  
-   **иерархия,** **геометрия,** **география**  
  
-   Определяемые пользователем типы CLR

Как правило, любой набор результатов, [!INCLUDE[tsql](../../includes/tsql-md.md)] который не может быть отображен к типу данных, выводится как NULL.  

### <a name="restrictions-specific-to-r"></a>Ограничения, характерные для R

Если входные значения включают значения **времени датирования,** которые не соответствуют допустимому диапазону значений в R, значения преобразуются в **NA.** Это необходимо, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поскольку допускает более широкий диапазон значений, чем поддерживается на языке R.

Значения float `+Inf`(например, `-Inf` `NaN`, , ) [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не поддерживаются, даже если оба языка используют IEEE 754. Текущее поведение просто отправляет [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] значения напрямую; в результате клиент S'L [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] бросает ошибку. Таким образом, эти значения преобразуются в **NULL.**

## <a name="permissions"></a>Разрешения

Требуется любое разрешение базы данных **EXTERNAL SCRIPT.**  

## <a name="examples"></a>Примеры

В этом разделе содержатся примеры того, как эта сохраненная процедура может быть использована для выполнения скриптов R или Python с использованием. [!INCLUDE[tsql](../../includes/tsql-md.md)]

### <a name="a-return-an-r-data-set-to-sql-server"></a>A. Возврат набора данных R на сервер S'L  

Следующий пример создает сохраненную процедуру, которая использует **sp_execute_external_script** для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]возврата набора данных Iris, включенных в R, в .  

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

### <a name="b-generate-an-r-model-based-on-data-from-sql-server"></a>Б. Создание модели R на основе данных с сервера S'L  

Следующий пример создает сохраненную процедуру, которая использует **sp_execute_external_script** для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]создания модели радужной оболочки глаза и возврата модели в .  

> [!NOTE]
>  Этот пример требует предварительной установки пакета e1071. Для получения дополнительной [информации, см.](../../machine-learning/package-management/install-additional-r-packages-on-sql-server.md)

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

### <a name="c-create-a-python-model-and-generate-scores-from-it"></a>В. Создание модели Python и формирование оценок на ее основе

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

Заголовки столбцов, используемые в коде Python, не вывешиваются на сервере S'L; Поэтому используйте заявление WITH RESULT, чтобы указать имена столбцов и типы данных для использования s'L.

Для оценки можно также применять собственную функцию [PREDICT](../../t-sql/queries/predict-transact-sql.md), которая обычно выполняется быстрее, так как не вызывает среду выполнения Python или R.

## <a name="see-also"></a>См. также

+ [Службы машинного обучения сервера S'L](../../machine-learning/index.yml)
+ [Продление языка серверов S'L](../../language-extensions/language-extensions-overview.md). 
+ [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
+ [Библиотеки python и типы данных](../../machine-learning/python/python-libraries-and-data-types.md)  
+ [R библиотеки и R типы данных](../../machine-learning/r/r-libraries-and-data-types.md)  
+ [Услуги сервера R](../../machine-learning/r/sql-server-r-services.md)   
+ [Известные проблемы для служб машинного обучения сервера S'L](../../machine-learning/known-issues-for-sql-server-machine-learning-services.md)   
+ [CREATE EXTERNAL LIBRARY &#40;&#41;"Трансакт-СЗЛ"](../../t-sql/statements/create-external-library-transact-sql.md)  
+ [sp_prepare &#40;&#41;](../../relational-databases/system-stored-procedures/sp-prepare-transact-sql.md)   
+ [sp_configure (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)   
+ [Параметр конфигурации сервера external scripts enabled](../../database-engine/configure-windows/external-scripts-enabled-server-configuration-option.md)   
+ [SERVERPROPERTY (Transact-SQL)](../../t-sql/functions/serverproperty-transact-sql.md)   
+ [SQL Server, объект External Scripts](../../relational-databases/performance-monitor/sql-server-external-scripts-object.md)  
+ [sys.dm_external_script_requests](../../relational-databases/system-dynamic-management-views/sys-dm-external-script-requests.md)  
+ [sys.dm_external_script_execution_stats](../../relational-databases/system-dynamic-management-views/sys-dm-external-script-execution-stats.md) 
