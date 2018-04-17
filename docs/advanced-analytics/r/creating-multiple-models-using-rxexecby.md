---
title: Создание нескольких моделей, с помощью rxExecBy (SQL Server машинного обучения) | Документы Microsoft
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 752ab5fc883f8fd99309496abb771931a05afc6a
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="creating-multiple-models-using-rxexecby"></a>Создание нескольких моделей, с помощью rxExecBy
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

2017 г CTP-версия SQL Server 2.0 включает новую функцию **rxExecBy**, который поддерживает параллельную обработку нескольких связанных моделей. Вместо того чтобы обучение один очень большой модели на основе данных из нескольких похожих сущностей, специалист по анализу данных можно очень быстро создать много связанных моделей, каждая с помощью данных, относящихся к одной сущности.

Например предположим, мониторинг сбоев устройства и сбор данных для различных типов оборудования. С помощью rxExecBy, можно предоставить один большой набор данных в качестве входного, укажите столбец, по которому стратификация набора данных, такие как тип устройства и затем создать несколько моделей моделей для отдельных устройств.

Этот процесс были называется с «pleasingly параллельных» обработки, так как она использует задачу, которая была немного обременительной задачей для специалист по анализу данных, или в лучшем трудоемкой и упрощает быстрый и простой операции.

Обычно приложения этот подход включают Прогнозирование для отдельных семьи смарт-м, создание проекций доход для отдельного продукта строк или создание моделей для утверждения кредита, предназначенных для отдельных bank ветвей.

## <a name="how-rxexec-works"></a>Как работает rxExec

Функция rxExecBy в RevoScaleR предназначен для параллельного большого объема обработки большого числа небольших наборов данных.

1. Вызов функции rxExecBy как часть кода R и передайте неупорядоченных данных набора данных.
2. Задайте секцию, по которому следует группировать и сортировать данные.
3. Определение преобразования, или функция, которая должна применяться к каждой секции данных моделирования
4. При выполнении функции, если рабочая среда поддерживает запросы к данным обрабатываются параллельно. Кроме того задачи моделирования или преобразования распространяются среди отдельных ядер и выполняются одновременно. Контекст вычислений, поддерживаемых для этих операций включают RxSpark и RxInSQLServer.
5. Возвращается несколько результатов.

## <a name="rxexecby-syntax-and-examples"></a>rxExecBy синтаксис и примеры

**rxExecBy** принимает четыре входных данных, один из входных данных, которой объект источника данных или набора данных, могут быть секционированы для указанной **ключ** столбца. Эта функция возвращает выходные данные для каждой секции. Формат вывода зависит функция, которая передается в качестве аргумента,, например, если передать функции моделирования, например rxLinMod, может вернуть отдельные обученной модели для каждой секции набора данных.

### <a name="supported-functions"></a>Поддерживаемые функции

Моделирование: `rxLinMod`, `rxLogit`, `rxGlm`, `rxDtree`

Оценки: `rxPredict`,

Преобразование или анализа: `rxCovCor`

## <a name="example"></a>Пример

Ниже приведен пример, как создать несколько моделей с помощью авиакомпании набора данных, что секционирована по столбцу [DayOfWeek]. Определяемая пользователем функция `delayFunc`, применяется к каждой из секций, вызывающий rxExecBy. Эта функция создает отдельные модели для понедельник, Вторник, и т. д.

```SQL
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

Если появляется ошибка, `varsToPartition is invalid`, проверьте, правильно ввели имя ключевого столбца или столбцов. Язык R с учетом регистра.

Обратите внимание, что в этом примере не оптимизирована для SQL Server, и во многих случаях можно было бы добиться повышения производительности с помощью SQL должны быть сгруппированы данные. Тем не менее используя rxExecBy, можно создать параллельных заданий из кода R.

В следующем примере показан процесс в R, используя SQL Server в качестве контекста вычислений:

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


