---
title: Создание множества моделей с помощью rxExecBy
description: Используйте функцию rxExecBy из библиотеки RevoScaleR для создания нескольких мини-моделей на основе машинных данных, хранящихся в SQL Server.
ms.prod: sql
ms.technology: machine-learning-services
ms.date: 04/15/2018
ms.topic: how-to
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15'
ms.openlocfilehash: 94f54e84a7f78dd92bacee399415149ca3b08a07
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/14/2020
ms.locfileid: "97470905"
---
# <a name="creating-multiple-models-using-rxexecby"></a>Создание нескольких моделей с помощью rxExecBy
[!INCLUDE [SQL Server 2016 and later](../../includes/applies-to-version/sqlserver2016.md)]

Функция **rxExecBy** библиотеки RevoScaleR поддерживает параллельную обработку нескольких связанных моделей. Вместо того, чтобы обучать одну большую модель на основе данных из нескольких схожих сущностей, специалист по обработке и анализу данных может быстро создать множество связанных моделей, каждая из которых использует данные одной сущности. 

Предположим, например, что вы отслеживаете отказы устройств, записывая данные множества различных типов оборудования. С помощью rxExecBy можно предоставить в качестве входных данных один большой набор данных, указать столбец, по которому будет стратифицироваться набор данных, например, тип устройства, а затем создать несколько моделей для отдельных устройств.

Такой подход называют ["привлекательной параллельностью"](https://en.wikipedia.org/wiki/Embarrassingly_parallel), так как он разбивает сложную задачу на части, которые можно обрабатывать параллельно.

Типичные области применения этого подхода включают прогнозирование для отдельных интеллектуальных домашних приборов учета, создание прогноза доходов для отдельных линеек продуктов или создание моделей для одобрения кредита, адаптированных к отдельным отделениям банка.

## <a name="how-rxexec-works"></a>Как работает rxExec

Функция rxExecBy библиотеки RevoScaleR разработана для больших объемов параллельной обработки большого количества небольших наборов данных.

1. Вы вызываете функцию rxExecBy как часть кода R и передаете неупорядоченные данные в виде набора данных.
2. Укрываете секцию, по которой необходимо сгруппировать и отсортировать данные.
3. Определяете функцию преобразования или моделирования, которую следует применить к каждой секции данных.
4. При выполнении функции запросы данных обрабатываются параллельно, если среда поддерживает параллельность. Более того, задачи моделирования и преобразования распределяются между отдельными ядрами и выполняются параллельно. Поддерживаемые контексты вычислений для этих операций включают RxSpark и RxInSQLServer.
5. Возвращается множественные результаты.

## <a name="rxexecby-syntax-and-examples"></a>Синтаксис и примеры использования rxExecBy

**rxExecBy** принимает четыре входных значения, одно из которых — набор данных или объект источника данных, который можно секционировать по указанному столбцу **key**. Функция возвращает выходные данные для каждой секции. Форма выходных данных зависит от функции, передаваемой в качестве аргумента. Например, при передаче функции моделирования, такой как rxLinMod, можно получить отдельную обученную модель для каждой секции набора данных.

### <a name="supported-functions"></a>Поддерживаемые функции

Моделирование: `rxLinMod`, `rxLogit`, `rxGlm`, `rxDtree`

Оценка: `rxPredict`

Преобразование и анализ: `rxCovCor`

## <a name="example"></a>Пример

В следующем примере показано, как создать несколько моделей с помощью набора данных авиакомпании, который секционируется по столбцу [DayOfWeek]. Определяемая пользователем функция `delayFunc` применяется к каждой секции путем вызова rxExecBy. Функция создает отдельные модели для понедельника, вторника и т. д.

```sql
EXEC sp_execute_external_script
@language = N'R'
, @script = N'
delayFunc <- function(key, data, params) { 
    df <- rxImport(inData = airlineData) 
    rxLinMod(ArrDelay ~ CRSDepTime, data = df) 
} 
OutputDataSet <- rxExecBy(airlineData, c("DayOfWeek"), delayFunc)
'
, @input_data_1 = N'select ArrDelay, DayOfWeek, CRSDepTime from AirlineDemoSmall]'
, @input_data_1_name = N'airlineData'

```

Если возникает ошибка `varsToPartition is invalid`, проверьте, правильно ли введено имя ключевого столбца или столбцов. В языке R учитывается регистр.

Этот пример не оптимизирован для SQL Server, и во многих случаях можно достичь повышения производительности, используя SQL для группировки данных. Однако с помощью rxExecBy можно создавать параллельные задания из R.

В следующем примере показана реализация в R с использованием SQL Server в качестве контекста вычислений:

```R
sqlServerConnString <- "SERVER=hostname;DATABASE=TestDB;UID=DBUser;PWD=Password;"
inTable <- paste("airlinedemosmall")
sqlServerDataDS <- RxSqlServerData(table = inTable, connectionString = sqlServerConnString)

# user function
".Count" <- function(keys, data, params)
{
  myDF <- rxImport(inData = data)
  return (nrow(myDF))
}

# Set SQL Server compute context with level of parallelism = 2
sqlServerCC <- RxInSqlServer(connectionString = sqlServerConnString, numTasks = 4)
rxSetComputeContext(sqlServerCC)

# Execute rxExecBy in SQL Server compute context
sqlServerCCResults <- rxExecBy(inData = sqlServerDataDS, keys = c("DayOfWeek"), func = .Count)
```


