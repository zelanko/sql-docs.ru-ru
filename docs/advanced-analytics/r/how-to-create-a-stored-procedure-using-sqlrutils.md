---
title: Создание хранимой процедуры с помощью sqlrutils
description: Используйте пакет sqlrutils R в SQL Server для объединения кода языка R в одну функцию, которая может быть передана в качестве аргумента хранимой процедуре.
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.openlocfilehash: 0713a126a237f20b2de4e3b16225bb9e5ae26307
ms.sourcegitcommit: c1382268152585aa77688162d2286798fd8a06bb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/19/2019
ms.locfileid: "68345577"
---
# <a name="create-a-stored-pprocedure-using-sqlrutils"></a>Создание хранимой Ппроцедуре с помощью sqlrutils
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

В этой статье описываются действия по преобразованию кода R для выполнения в качестве хранимой процедуры T-SQL. Для достижения наилучших результатов может потребоваться немного изменить код, чтобы обеспечить возможность параметризации всех входных данных.

## <a name="bkmk_rewrite"></a>Шаг 1. Переписать скрипт R

Для получения наилучших результатов следует переписать код R, чтобы инкапсулировать его как единую функцию.

Все переменные, используемые функцией, должны быть определены внутри функции или должны быть определены как входные параметры. См. [пример кода](#samples) в этой статье.

Кроме того, поскольку входные параметры функции R станут входными параметрами хранимой процедуры SQL, необходимо убедиться, что входные и выходные данные соответствуют следующим требованиям к типу:

### <a name="inputs"></a>Входные данные

Среди входных параметров может быть не более одного кадра данных.

Объекты внутри кадра данных, а также все другие входные параметры функции должны относиться к следующим типам данных R:
- POSIXct
- NUMERIC
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

## <a name="step-2-generate-required-objects"></a>Шаг 2. Создать необходимые объекты

После того как код R был очищен и может быть вызван как отдельная функция, вы будете использовать функции в пакете **sqlrutils** для подготовки входных и выходных данных в форме, которая может быть передана в конструктор, который фактически создает хранимую процедуру.

**sqlrutils** предоставляет функции, которые определяют схему входных данных и тип, а также определяют схему и тип выходных данных. Он также включает функции, которые могут преобразовывать объекты R в требуемый выходной тип. Можно выполнить несколько вызовов функций, чтобы создать необходимые объекты в зависимости от типов данных, используемых вашим кодом.

### <a name="inputs"></a>Входные данные

Если функция принимает входные данные, для каждого входного значения вызывайте следующие функции:

- `setInputData`Если входные данные являются кадром данных
- `setInputParameter`для всех других типов входных данных

При выполнении каждого вызова функции создается объект R, который позже будет передан в качестве аргумента `StoredProcedure`для создания полной хранимой процедуры.

### <a name="outputs"></a>Выходные данные

**sqlrutils** предоставляет несколько функций для преобразования объектов R, таких как списки, в данные. кадр, необходимый для SQL Server.
Если функция выводит кадр данных напрямую, без первоначального объединения его в список, этот шаг можно пропустить.
Вы также можете пропустить преобразование этого шага, если функция возвращает значение NULL.

При преобразовании списка или получении определенного элемента из списка выберите следующие функции:

- `setOutputData`Если переменная, которую необходимо получить из списка, является кадром данных
- `setOutputParameter`для всех других членов списка

При выполнении каждого вызова функции создается объект R, который позже будет передан в качестве аргумента `StoredProcedure`для создания полной хранимой процедуры.

## <a name="step-3-generate-the-stored-procedure"></a>Шаг 3. Создание хранимой процедуры

Когда все входные и выходные параметры готовы, выполните вызов `StoredProcedure` конструктора.

**Использование**

`StoredProcedure (func, spName, ..., filePath = NULL ,dbName = NULL, connectionString = NULL, batchSeparator = "GO")`

Предположим, что необходимо создать хранимую процедуру с именем **sp_rsample** и следующими параметрами:

- Использует существующую функцию **фускл**. Функция была основана на существующем коде в функции R **foo**, но вы переписали функцию для соответствия требованиям, описанным в [этом разделе](#bkmk_rewrite), и назвали обновленную функцию как **фускл**.
- Использует кадр данных **куеринпут** в качестве входного.
- Формирует выходной кадр данных с именем переменной R **склаутпут**
- Необходимо создать код T-SQL в виде файла в `C:\Temp` папке, чтобы его можно было запустить с помощью SQL Server Management Studio позже

```R
StoredProcedure (foosql, sp_rsample, queryinput, sqloutput, filePath = "C:\\Temp")
```

> [!NOTE]
> Поскольку файл записывается в файловую систему, можно опустить аргументы, определяющие подключение к базе данных.

Выходные данные функции — это хранимая процедура T-SQL, которая может быть выполнена на экземпляре SQL Server 2016 (требуются службы R) или SQL Server 2017 (требуется Службы машинного обучения с R). 

Дополнительные примеры см. в справке по пакетам путем вызова `help(StoredProcedure)` из среды R.

## <a name="step-4-register-and-run-the-stored-procedure"></a>Шаг 4. Регистрация и выполнение хранимой процедуры

Существует два способа выполнения хранимой процедуры:

- Использование T-SQL из любого клиента, поддерживающего подключения к экземпляру SQL Server 2016 или SQL Server 2017
- Из среды R

Для обоих методов требуется, чтобы хранимая процедура была зарегистрирована в базе данных, где предполагается использовать хранимую процедуру.

### <a name="register-the-stored-procedure"></a>Регистрация хранимой процедуры

Хранимую процедуру можно зарегистрировать с помощью языка R или выполнить инструкцию CREATE PROCEDURE в T-SQL.

- С помощью T-SQL.  Если вы знакомы с T-SQL, откройте SQL Server Management Studio (или любой другой клиент, который может выполнять команды SQL DDL) и выполните инструкцию CREATE PROCEDURE, используя код, подготовленный `StoredProcedure` функцией.
- Использование языка R. Пока вы все еще используете среду R, вы можете использовать `registerStoredProcedure` функцию в **sqlrutils** для регистрации хранимой процедуры в базе данных.

  Например, можно зарегистрировать хранимую процедуру **sp_rsample** в экземпляре и базе данных, определенной в *склконнстр*, выполнив этот вызов R:

  ```R
  registerStoredProcedure(sp_rsample, sqlConnStr)
  ```


> [!IMPORTANT]
> Независимо от того, используется ли R или SQL, необходимо выполнить инструкцию, используя учетную запись с разрешениями на создание новых объектов базы данных.

### <a name="run-using-sql"></a>Выполнение с помощью SQL

После создания хранимой процедуры откройте подключение к базе данных SQL с помощью любого клиента, поддерживающего T-SQL, и передайте значения для всех параметров, необходимых для хранимой процедуры.

### <a name="run-using-r"></a>Запустить с помощью R

Если вы хотите выполнить хранимую процедуру из кода R, а не SQL Server, требуется дополнительная подготовка. Например, если хранимой процедуре требуются входные значения, необходимо задать эти входные параметры перед выполнением функции, а затем передать эти объекты в хранимую процедуру в коде R.

Общий процесс вызова подготовленной хранимой процедуры SQL выглядит следующим образом:

1. Вызовите `getInputParameters` для получения списка объектов входных параметров.
2. Определение `$query` или задайте `$value` для каждого входного параметра.
3. Используйте `executeStoredProcedure` для выполнения хранимой процедуры из среды разработки R, передавая список заданных объектов входных параметров.

## <a name = "samples"></a>Например

В этом примере показаны до и после версий скрипта R, который получает данные из SQL Server базы данных, выполняет некоторые преобразования данных и сохраняет их в другой базе данных.

Этот простой пример используется только для демонстрации того, как можно изменить код R, чтобы упростить преобразование в хранимую процедуру.

### <a name="before-code-preparation"></a>Перед началом подготовки кода


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
> При использовании соединения ODBC вместо вызова функции *RxSqlServerData* необходимо открыть подключение с помощью *rxOpen* , прежде чем можно будет выполнять операции с базой данных.


### <a name="after-code-preparation"></a>После подготовки кода

В обновленной версии первая строка определяет имя функции. Весь остальной код из исходного решения R станет частью этой функции.

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

[sqlrutils (SQL)](ref-r-sqlrutils.md)


