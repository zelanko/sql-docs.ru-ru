---
title: Создание нескольких моделей, с помощью rxExecBy - службы машинного обучения SQL Server
description: Используйте функцию rxExecBy из библиотеки RevoScaleR для построения несколько мини-моделей на компьютере данные, хранящиеся в SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.openlocfilehash: b0316cf40acff1a64aa40a14911f323eb913efc1
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67962687"
---
# <a name="creating-multiple-models-using-rxexecby"></a>Создание нескольких моделей с помощью rxExecBy
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

**RxExecBy** функция в RevoScaleR поддерживает параллельную обработку нескольких связанных моделей. Вместо того чтобы train один большой модели на основе данных из нескольких похожих сущностей, специалист по обработке данных можно быстро создать несколько связанных моделей, каждая с помощью данных, относящихся к одной сущности. 

Например предположим, что вы наблюдаете сбоев устройства записи данных для различных типов оборудования. С помощью rxExecBy, можно предоставить один большой набор данных как входные данные, укажите столбец, который для стратификации указывается набор данных, например тип устройства и затем создать несколько моделей для отдельных устройств.

Этот вариант использования был называется обработкой [«pleasingly параллельных»](https://en.wikipedia.org/wiki/Embarrassingly_parallel) так, как он разбивает большие сложной проблемы на составные части для параллельной обработки.

Типичные приложения этого подхода включают Прогнозирование для отдельных бытовые интеллектуальные счетчики, создание проекции доход для отдельного продукта строк или создание моделей для утверждения кредита, специально созданные для отделения банка отдельных.

## <a name="how-rxexec-works"></a>Как работает rxExec

Функция rxExecBy в RevoScaleR обеспечивает параллельную большого объема обработки для большого числа небольших наборов данных.

1. Вызвать функцию rxExecBy как часть кода R и передать набор данных неупорядоченных данных.
2. Укажите раздел, по которому следует группировать и сортировать данные.
3. Определение преобразования или моделирования функцию, которая должна применяться к каждой секции данных
4. При выполнении функции, запросы данных обрабатываются параллельно, если она поддерживается вашей среде. Кроме того задачи моделирования или преобразования распространяются среди отдельных ядер и выполняться параллельно. Контекст вычисления, поддерживаемых для этих операций включают RxSpark и RxInSQLServer.
5. Возвращается несколько результатов.

## <a name="rxexecby-syntax-and-examples"></a>rxExecBy синтаксис и примеры

**rxExecBy** принимает четыре входных данных, один из входных данных, что объект источника данных или набора данных, могут быть секционированы для указанной **ключ** столбца. Функция возвращает выходные данные для каждой секции. Форма выходных данных зависит от функции, которая передается в качестве аргумента. Например если передать функцию моделирования, такие как rxLinMod, можно возвращать отдельные обученной модели для каждой секции набора данных.

### <a name="supported-functions"></a>Поддерживаемые функции

Моделирование: `rxLinMod`, `rxLogit`, `rxGlm`, `rxDtree`

Оценки: `rxPredict`,

Преобразования или анализа: `rxCovCor`

## <a name="example"></a>Пример

Следующий пример демонстрирует способ создания нескольких моделей с помощью набора данных по Авиабилетам, который секционирована по столбцу [DayOfWeek]. Определяемой пользователем функции, `delayFunc`, применяется к каждой из секций с вызывающей rxExecBy. Функция создает отдельные модели для понедельник, Вторник, и т. д.

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

Если возникает ошибка, `varsToPartition is invalid`, проверьте, правильно ввели имя ключевого столбца или столбцов. В языке R учитывается регистр.

Данном конкретном примере не оптимизирована для SQL Server, и вы сможете во многих случаях достигнуть лучшей производительности с помощью SQL должны быть сгруппированы данные. Тем не менее с помощью rxExecBy, созданием параллельных заданий из кода R.

Следующий пример иллюстрирует процесс в R с помощью SQL Server в качестве контекста вычислений:

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


