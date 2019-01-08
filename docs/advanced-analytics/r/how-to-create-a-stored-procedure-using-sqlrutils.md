---
title: Создание хранимой процедуры с помощью sqlrutils - службы машинного обучения SQL Server
description: Используйте пакету sqlrutils R в SQL Server, чтобы объединять код на языке R в одну функцию, которая может передаваться в качестве аргумента хранимой процедуре.
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: e347deb0a0f05da12a4281e77223a0492f04f13f
ms.sourcegitcommit: 85bfaa5bac737253a6740f1f402be87788d691ef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/15/2018
ms.locfileid: "53432717"
---
# <a name="create-a-stored-pprocedure-using-sqlrutils"></a>Создание хранимых pProcedure, с помощью sqlrutils
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

В этой статье описывается преобразование кода R для запуска в качестве T-SQL, хранимая процедура. Для достижения наилучших результатов может потребоваться немного изменить код, чтобы обеспечить возможность параметризации всех входных данных.

## <a name="bkmk_rewrite"></a>Шаг 1. Перепишите скрипт R

Для получения наилучших результатов следует переписать код R, чтобы инкапсулировать его в виде одной функции.

Все переменные, используемые функцией, должны быть определены внутри функции или должен быть определен в качестве входных параметров. См. в разделе [пример кода](#samples) в этой статье.

Кроме того так как входные параметры для функции R станет входных параметров SQL хранимой процедуры, необходимо убедиться, что входные и выходные данные соответствуют следующим требованиям к типам:

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

## <a name="step-2-generate-required-objects"></a>Шаг 2. Создание необходимых объектов

После того как код R была очищена и могут вызываться в виде одной функции, будет использовать функции из **sqlrutils** пакета для подготовки входных и выходных данных в форме, которую можно передать в конструктор, действительно создающая Хранимая процедура.

**sqlrutils** предоставляет функции, которые определяют схему входных данных и тип и схема вывода данных и тип. Она также включает функции, объекты R можно преобразовать в тип требуемые выходные данные. Вы можете сделать несколько вызовов функции для создания необходимых объектов, в зависимости от типов данных, используемую вашим кодом.

### <a name="inputs"></a>Входные данные

Если функция принимает входные данные, для каждого входного элемента, вызывают следующие функции:

- `setInputData` Если входные данные — это блок данных
- `setInputParameter` для всех остальных типов входных данных

Создается при создании каждого вызова функции, объект R, позже вы передадите как аргумент `StoredProcedure`, чтобы создать полный хранимой процедуры.

### <a name="outputs"></a>Выходные данные

**sqlrutils** предоставляет несколько функций для преобразования R объектов, таких как списки для кадра данных, требуется SQL Server.
Если функция выводит кадр данных напрямую, без первоначального объединения его в список, этот шаг можно пропустить.
Вы также преобразование этот шаг можно пропустить, если пользовательская функция возвращает значение NULL.

Когда преобразование списка или при получении данным элементом из списка, выберите из этих функций:

- `setOutputData` Если переменная для получения из списка — это блок данных
- `setOutputParameter` для всех других элементов списка

Создается при создании каждого вызова функции, объект R, позже вы передадите как аргумент `StoredProcedure`, чтобы создать полный хранимой процедуры.

## <a name="step-3-generate-the-stored-procedure"></a>Шаг 3. Создать хранимую процедуру

Когда готовы все входные и выходные параметры, вызовите `StoredProcedure` конструктор.

**Использование**

`StoredProcedure (func, spName, ..., filePath = NULL ,dbName = NULL, connectionString = NULL, batchSeparator = "GO")`

Чтобы продемонстрировать, предположим, что вы хотите создать хранимую процедуру с именем **sp_rsample** со следующими параметрами:

- Использует существующую функцию **foosql**. Функция была основана на существующий код в функцию R **foo**, но переписала функция соответствует требованиям, как описано в разделе [в этом разделе](#bkmk_rewrite)и с именем обновленной функции как  **foosql**.
- Использует кадров данных **queryinput** как входные данные
- Создает в формате кадра данных с именем переменной R, **sqloutput**
- Вы хотите создать код T-SQL в виде файла `C:\Temp` папки, чтобы обеспечить возможность выполнения более поздней версии с помощью SQL Server Management Studio

```R
StoredProcedure (foosql, sp_rsample, queryinput, sqloutput, filePath = "C:\\Temp")
```

> [!NOTE]
> Поскольку вы создаете файл в файловой системе, можно опустить аргументы, которые определяют подключения к базе данных.

Выходные данные функции является T-SQL хранимой процедурой, которая может быть выполнена для экземпляра SQL Server 2016 (требуются службы R) или SQL Server 2017 (требуется служб машинного обучения с помощью R). 

Дополнительные примеры см. в справке пакета, путем вызова `help(StoredProcedure)` из среды R.

## <a name="step-4-register-and-run-the-stored-procedure"></a>Шаг 4. Регистрация и запуск хранимой процедуры

Существует два способа, можно выполнять хранимую процедуру:

- С помощью T-SQL, из любого клиента, который поддерживает подключения к экземпляру SQL Server 2016 или SQL Server 2017
- Из среды R

Оба метода требуют, что хранимая процедура быть зарегистрирован в базе данных, где планируется использовать хранимую процедуру.

### <a name="register-the-stored-procedure"></a>Зарегистрировать хранимую процедуру

Вы можете зарегистрировать хранимой процедуры, с помощью языка R, или можно выполнить инструкцию CREATE PROCEDURE в T-SQL.

- С помощью T-SQL.  Если вам удобнее работать с помощью T-SQL, откройте SQl Server Management Studio (или любой другой клиент, команды могут выполняться SQL DDL) и выполните инструкцию CREATE PROCEDURE, с помощью кода, подготовленных методом `StoredProcedure` функции.
- С помощью языка R. Хотя по-прежнему среды R, вы можете использовать `registerStoredProcedure` работать в **sqlrutils** для регистрации хранимой процедуры в базе данных.

  Например, может зарегистрировать хранимую процедуру **sp_rsample** в экземпляре и базе данных, определенных в *sqlConnStr*, выполняя этот вызов R:

  ```R
  registerStoredProcedure(sp_rsample, sqlConnStr)
  ```


> [!IMPORTANT]
> Независимо от того, используется ли R или SQL необходимо выполнить инструкцию, используя учетную запись, имеющую разрешения на создание новых объектов базы данных.

### <a name="run-using-sql"></a>Запустить с помощью SQL

После создания хранимой процедуры, откройте подключение к базе данных SQL с помощью любого клиента, который поддерживает T-SQL и передавать значения для любых параметров, необходимых хранимой процедурой.

### <a name="run-using-r"></a>Запустить с помощью языка R

Некоторые дополнительной подготовки необходим, если вы хотите выполнить хранимую процедуру из кода R, а не из SQL Server. Например если хранимая процедура требует входных значений, необходимо задать эти входные параметры, прежде, чем функция может быть выполнена и передает эти объекты в хранимую процедуру в коде R.

Процесс вызова подготовленного хранимой процедуры SQL выглядит следующим образом:

1. Вызовите `getInputParameters` для получения списка объектов входных параметров.
2. Определение `$query` или задайте `$value` для каждого входного параметра.
3. Используйте `executeStoredProcedure` для выполнения хранимой процедуры из среды разработки R, передавая список заданных объектов входных параметров.

## <a name = "samples"></a>Пример

В этом примере показано до и после версии сценарий R, получает данные из базы данных SQL Server, выполняет некоторые преобразования данных и сохраняет его в другую базу данных.

В этом простом примере используется только для демонстрации того, как можно изменить код R, чтобы было проще преобразовать в хранимую процедуру.

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
> При использовании соединения ODBC вместо вызова *RxSqlServerData* функцию, необходимо открыть подключение с помощью *rxOpen* перед тем как выполнять операции в базе данных.


### <a name="after-code-preparation"></a>После подготовки кода

В обновленной версии первая строка определяет имя функции. Весь остальной код из исходного решения R становится частью этой функции.

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


