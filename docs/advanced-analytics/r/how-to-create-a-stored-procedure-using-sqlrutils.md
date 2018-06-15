---
title: Создание хранимой процедуры, с помощью sqlrutils | Документы Microsoft
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 82af827d95def976a04ac69073b58e1420cc9130
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31203706"
---
# <a name="create-a-stored-pprocedure-using-sqlrutils"></a>Создание хранимых pProcedure с помощью sqlrutils
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

В этой статье описывается преобразование кода R для запуска в качестве T-SQL для хранимой процедуры. Для достижения наилучших результатов может потребоваться немного изменить код, чтобы обеспечить возможность параметризации всех входных данных.

## <a name="bkmk_rewrite"></a>Шаг 1. Перепишите скрипт R

Для получения наилучших результатов следует переписать код R, чтобы инкапсулировать его в виде одной функции.

Все переменные, используемые функцией, должен быть определен внутри функции или должен быть определен в качестве входных параметров. В разделе [пример кода](#samples) в этой статье.

Кроме того так как входные параметры для функции R станет SQL входные параметры хранимой процедуры, необходимо убедиться, входные и выходные данные соответствуют следующим требованиям тип:

### <a name="inputs"></a>Входные данные

Среди входных параметров может быть не более одного кадра данных.

Объекты внутри кадра данных, а также все другие входные параметры функции должны относиться к следующим типам данных R:
- POSIXct
- numeric
- character
- integer
- логические
- raw

Если тип входных данных не является одним из перечисленных выше, он должен быть сериализован и передан в функцию в виде *raw*. В этом случае функция также должна включать код для десериализации входных данных.

### <a name="outputs"></a>Выходные данные

Функция может иметь один из следующих вариантов вывода:

- Кадр данных, содержащий поддерживаемые типы данных. Все объекты в кадре данных должны использовать один из поддерживаемых типов данных.
- Именованный список, содержащий не более одного кадра данных. Все элементы в списке должны использовать один из поддерживаемых типов данных.
- Значение NULL, если функция не возвращает никакого результата.

## <a name="step-2-generate-required-objects"></a>Шаг 2. Создание необходимых объектов

После кода R были очищены и может быть вызван в виде одной функции, будет использовать функции в **sqlrutils** пакета для подготовки входы и выходы в форме, который может быть передан в конструктор, который фактически создает Хранимая процедура.

**sqlrutils** предоставляет функции, которые определяют схему входных данных и тип и определение схемы вывода данных и типа. Он также включает функции, которые можно преобразовать в тип выходного объекты R. Может быть несколько вызовов функции для создания требуемых объектов, в зависимости от типов данных, используемую вашим кодом.

### <a name="inputs"></a>Входные данные

Если функция принимает входные данные, для каждого входного вызове следующих функций:

- `setInputData` Если входное значение кадра данных.
- `setInputParameter` для всех остальных типов входных данных

При внесении каждого вызова функции создания объекта R, позже передается как аргумент `StoredProcedure`, чтобы создать полное хранимой процедуры.

### <a name="outputs"></a>Выходные данные

**sqlrutils** предоставляет несколько функций для преобразования R объектов, таких как списки, чтобы data.frame, необходимые для SQL Server.
Если функция выводит кадр данных напрямую, без первоначального объединения его в список, этот шаг можно пропустить.
Вы также преобразование этот шаг можно пропустить, если пользовательская функция возвращает значение NULL.

При преобразовании списка или при получении какой-либо элемент из списка, выберите эти функции:

- `setOutputData` Если переменная для получения из списка кадра данных.
- `setOutputParameter` для всех других элементов списка

При внесении каждого вызова функции создания объекта R, позже передается как аргумент `StoredProcedure`, чтобы создать полное хранимой процедуры.

## <a name="step-3-generate-the-stored-procedure"></a>Шаг 3. Создание хранимой процедуры

Когда готовы входные и выходные параметры, вызвать `StoredProcedure` конструктор.

**Использование**

`StoredProcedure (func, spName, ..., filePath = NULL ,dbName = NULL, connectionString = NULL, batchSeparator = "GO")`

Чтобы проиллюстрировать, предположим, что для создания хранимой процедуры с именем **sp_rsample** со следующими параметрами:

- Использует существующую функцию **foosql**. Функция была основана на существующий код в функцию R **foo**, но переписала функцию должна соответствовать требованиям, описанным в [в этом разделе](#bkmk_rewrite)и обновленные функции, как с именем  **foosql**.
- Использует кадров данных **queryinput** как входные данные
- Создает в качестве выходных данных кадра данных с именем переменной R **sqloutput**
- Вы хотите создать код T-SQL в виде файла `C:\Temp` папки, чтобы запустить его позже с помощью SQL Server Management Studio

```R
StoredProcedure (foosql, sp_rsample, queryinput, sqloutput, filePath = "C:\\Temp")
```

> [!NOTE]
> Поскольку записи файла в файловой системе, можно опустить аргументы, которые определяют подключения к базе данных.

Выходные данные функции являются T-SQL для хранимой процедуры, могут быть выполнены на экземпляре SQL Server 2016 (требуются службы R) или SQL Server 2017 г. (требуется Machine Services обучения с помощью R). 

Дополнительные примеры см. в разделе справки, пакета, путем вызова `help(StoredProcedure)` из среды R.

## <a name="step-4-register-and-run-the-stored-procedure"></a>Шаг 4. Регистрация и запуск хранимой процедуры

Что можно запускать хранимую процедуру двумя способами:

- С помощью T-SQL из любого клиента, который поддерживает подключения к экземпляру SQL Server 2016 или 2017 г. SQL Server
- В среде R

Для обоих методов требуется, хранимая процедура быть зарегистрированы в базе данных, где планируется использовать хранимую процедуру.

### <a name="register-the-stored-procedure"></a>Зарегистрировать хранимую процедуру

Можно зарегистрировать хранимой процедуры, с помощью R, или можно выполнить инструкцию CREATE PROCEDURE в T-SQL.

- С помощью T-SQL.  При наличии удобнее работать с T-SQL, откройте SQl Server Management Studio (или любым другим клиентом, команды могут выполняться SQL DDL) и выполните инструкцию CREATE PROCEDURE, с помощью кода, разработанном в рамках `StoredProcedure` функции.
- С помощью языка R. Хотя по-прежнему в вашей среде R, можно использовать `registerStoredProcedure` функционировать в **sqlrutils** для регистрации хранимой процедуры в базе данных.

  Например, можно зарегистрировать хранимой процедуры **sp_rsample** экземпляра и базы данных, определенных в *sqlConnStr*, выполняя этот вызов R:

  ```R
  registerStoredProcedure(sp_rsample, sqlConnStr)
  ```


> [!IMPORTANT]
> Независимо от того, используется ли R или SQL необходимо выполнить инструкцию, используя учетную запись, имеющую разрешения на создание новых объектов базы данных.

### <a name="run-using-sql"></a>Запустить с помощью SQL

После создания хранимой процедуры открыть подключение к базе данных SQL, используя любой клиент, поддерживающий T-SQL и передавать значения для всех параметров, необходимых для хранимой процедуры.

### <a name="run-using-r"></a>Запустить с помощью R

Если необходимо выполнить хранимую процедуру из кода R, а не из SQL Server требуется некоторые дополнительной подготовки. Например если хранимая процедура требует входных значений, необходимо задать эти входные параметры перед функции могут быть выполнены и передает эти объекты в хранимую процедуру в коде R.

Общий процесс вызова подготовленного SQL хранимой процедуры выглядит следующим образом:

1. Вызовите `getInputParameters` для получения списка объектов входных параметров.
2. Определение `$query` или задайте `$value` для каждого входного параметра.
3. Используйте `executeStoredProcedure` для выполнения хранимой процедуры из среды разработки R, передавая список заданных объектов входных параметров.

## <a name = "samples"></a>Пример

В этом примере показано до и после версии сценарий R, который получает данные из базы данных SQL Server, выполняет некоторые преобразования данных и сохраняет его в другую базу данных.

Этот простой пример используется только для демонстрации того, как можно изменить код R, чтобы было проще преобразовать в хранимую процедуру.

### <a name="before-code-preparation"></a>Прежде чем код подготовки


```R
sqlConnFrom <- "Driver={ODBC Driver 13 for SQL Server};Server=MyServer01;Database=AirlineSrc;Trusted_Connection=Yes;"
  
sqlConnTo <- "Driver={ODBC Driver 13 for SQL Server};Server=MyServer01;Database=AirlineTest;Trusted_Connection=Yes;"
  
sqlQueryAirline <- "SELECT TOP 10000 ArrDelay, CRSDepTime, DayOfWeek FROM [AirlineDemoSmall]"
  
dsSqlFrom <- RxSqlServerData(sqlQuery = sqlQueryAirline, connectionString = sqlConnFrom)
  
dsSqlTo <- RxSqlServerData(table = "cleanData", connectionString = sqlConnTo)
  
xFunc <- function(data) {
    data$CRSDepHour <- as.integer(trunc(data$CRSDepTime))
    return(data)
    }
  
xVars <- c("CRSDepTime")
  
sqlCompute <- RxInSqlServer(numTasks = 4, connectionString = sqlConnTo)
  
rxOpen(dsSqlFrom)
rxOpen(dsSqlTo)
  
if (rxSqlServerTableExists("cleanData", connectionString = sqlConnTo))   {
    rxSqlServerDropTable("cleanData")}
  
rxDataStep(inData = dsSqlFrom, 
     outFile = dsSqlTo,
     transformFunc = xFunc,
     transformVars = xVars,
     overwrite = TRUE)
```

> [!NOTE]
> 
> При использовании соединения ODBC вместо вызова *RxSqlServerData* функции, необходимо открыть соединения с помощью *rxOpen* перед тем как выполнять операции в базе данных.


### <a name="after-code-preparation"></a>После подготовки кода

В обновленной версией первая строка определяет имя функции. Весь код из исходного решения R становится частью этой функции.

```R
myetl1function <- function() { 
   sqlConnFrom <- "Driver={ODBC Driver 13 for SQL Server};Server=MyServer01;Database=Airline01;Trusted_Connection=Yes;"
   sqlConnTo <- "Driver={ODBC Driver 13 for SQL Server};Server=MyServer02;Database=Airline02;Trusted_Connection=Yes;"
    
   sqlQueryAirline <- "SELECT TOP 10000 ArrDelay, CRSDepTime, DayOfWeek FROM [AirlineDemoSmall]"

   dsSqlFrom <- RxSqlServerData(sqlQuery = sqlQueryAirline, connectionString = sqlConnFrom)
  
   dsSqlTo <- RxSqlServerData(table = "cleanData", connectionString = sqlConnTo)
  
   xFunc <- function(data) {
     data$CRSDepHour <- as.integer(trunc(data$CRSDepTime))
     return(data)}
  
   xVars <- c("CRSDepTime")
  
   sqlCompute <- RxInSqlServer(numTasks = 4, connectionString = sqlConnTo)
  
   if (rxSqlServerTableExists("cleanData", connectionString = sqlConnTo)) {rxSqlServerDropTable("cleanData")}
  
   rxDataStep(inData = dsSqlFrom, 
        outFile = dsSqlTo,
        transformFunc = xFunc,
        transformVars = xVars,
        overwrite = TRUE)
   return(NULL)
}
```

> [!NOTE]
> 
> Хотя вам и не требуется явно открывать соединение ODBC внутри кода, оно по-прежнему должно использовать **sqlrutils**.

## <a name="see-also"></a>См. также

[Создание хранимой процедуры с помощью sqlrutils](../../advanced-analytics/r-services/generating-an-r-stored-procedure-for-r-code-using-the-sqlrutils-package.md)


