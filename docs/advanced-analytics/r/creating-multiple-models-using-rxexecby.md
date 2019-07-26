---
title: Создание нескольких моделей с помощью rxExecBy
description: Используйте функцию Рксексекби из библиотеки RevoScaleR для создания нескольких мини-моделей на основе данных компьютера, хранящихся в SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.openlocfilehash: 5d3e03e718aea725267a2251768ef040905b020e
ms.sourcegitcommit: 9062c5e97c4e4af0bbe5be6637cc3872cd1b2320
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/24/2019
ms.locfileid: "68470189"
---
# <a name="creating-multiple-models-using-rxexecby"></a>Создание нескольких моделей с помощью rxExecBy
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Функция **рксексекби** в RevoScaleR поддерживает параллельную обработку нескольких связанных моделей. Вместо того, чтобы обучать одну крупную модель на основе данных из нескольких схожих сущностей, анализу данных может быстро создать множество связанных моделей, каждый из которых использует данные, относящиеся к одной сущности. 

Например, предположим, что вы отслеживаете сбои устройств, записывая данные для различных типов оборудования. С помощью Рксексекби можно предоставить в качестве входных данных один большой набор данных, указать столбец, по которому будет стратифи набор данных, например тип устройства, а затем создать несколько моделей для отдельных устройств.

Этот вариант использования был помечен как ["привлекательный параллельный"](https://en.wikipedia.org/wiki/Embarrassingly_parallel) , так как он разбивает сложную задачу на части компонентов для параллельной обработки.

К типичным приложениям такого подхода относятся прогнозирование для отдельных интеллектуальных приборов семьи, создание прогнозов доходов для отдельных линеек продуктов или создание моделей для утверждений по ссуде, адаптированных к отдельным банковским отделениям.

## <a name="how-rxexec-works"></a>Как работает rxExec

Функция Рксексекби в RevoScaleR разработана для больших объемов параллельной обработки большого количества небольших наборов данных.

1. Функция Рксексекби вызывается как часть кода R и передает набор данных неупорядоченных данных.
2. Укажите секцию, по которой должны быть сгруппированы и отсортированы данные.
3. Определите функцию преобразования или моделирования, которую следует применить к каждой секции данных.
4. При выполнении функции запросы данных обрабатываются параллельно, если среда поддерживает ее. Более того, задачи моделирования и преобразования распределяются между отдельными ядрами и выполняются параллельно. Поддерживаемый контекст вычислений для операций три включает RxSpark и RxInSQLServer.
5. Возвращается несколько результатов.

## <a name="rxexecby-syntax-and-examples"></a>Синтаксис и примеры Рксексекби

**рксексекби** принимает четыре входных значения, один из входов — набор данных или объект источника данных, который можно секционировать по  указанному ключевому столбцу. Функция возвращает выходные данные для каждой секции. Форма выходных данных зависит от функции, передаваемой в качестве аргумента. Например, при передаче функции моделирования, такой как rxLinMod, можно вернуть отдельную обученную модель для каждой секции набора данных.

### <a name="supported-functions"></a>Поддерживаемые функции

Моделирование: `rxLinMod`, `rxLogit`, `rxGlm`,`rxDtree`

Оценка: `rxPredict`,

Преобразование или анализ:`rxCovCor`

## <a name="example"></a>Пример

В следующем примере показано, как создать несколько моделей с помощью набора данных авиакомпании, который секционируется в столбце [DayOfWeek]. Определяемая пользователем функция `delayFunc`применяется к каждой секции путем вызова рксексекби. Функция создает отдельные модели для понедельника, вторники и т. д.

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

Если возникает ошибка, `varsToPartition is invalid`проверьте, правильно ли введено имя ключевого столбца или столбцов. В языке R учитывается регистр.

Этот пример не оптимизирован для SQL Server, и во многих случаях повышение производительности достигается благодаря использованию SQL для группирования данных. Однако с помощью Рксексекби можно создавать параллельные задания из R.

В следующем примере показан процесс в R с использованием SQL Server в качестве контекста вычислений:

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


