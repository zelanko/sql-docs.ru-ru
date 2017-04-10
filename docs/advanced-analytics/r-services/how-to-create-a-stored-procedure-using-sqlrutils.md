---
title: "Создание хранимой процедуры с помощью sqlrutils | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "R"
ms.assetid: 5ba99b49-481e-4b30-967a-a429b855b1bd
caps.latest.revision: 10
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 10
---
# Создание хранимой процедуры с помощью sqlrutils
В этом разделе описывается преобразование кода R для запуска в качестве хранимой процедуры T-SQL. Для достижения наилучших результатов может потребоваться немного изменить код, чтобы обеспечить возможность параметризации всех входных данных.

## <a name="step-1-format-your-r-script"></a>Шаг 1. Форматирование скрипта R

1. Поместите весь код в одну функцию.

   Это означает, что все переменные, используемые функцией, должны быть определены внутри функции или в качестве входных параметров. См. [пример кода](#samples) в этой статье.

## <a name="step-2-standardize-the-inputs-and-outputs"></a>Шаг 2. Стандартизация входных и выходных данных

Входные параметры функции станут входными параметрами хранимой процедуры SQL и поэтому должны отвечать следующим требованиям к типам.
- Среди входных параметров может быть не более одного кадра данных.
- Объекты внутри кадра данных, а также все другие входные параметры функции должны относиться к следующим типам данных R:
    - POSIXct
    - numeric
    - character
    - integer
    - логические
    - raw

- Если тип входных данных не является одним из перечисленных выше, он должен быть сериализован и передан в функцию в виде *raw*. В этом случае функция также должна включать код для десериализации входных данных.

Функция может иметь один из следующих вариантов вывода:

- Кадр данных, содержащий поддерживаемые типы данных. Все объекты в кадре данных должны использовать один из поддерживаемых типов данных.
- Именованный список, содержащий не более одного кадра данных. Все элементы в списке должны использовать один из поддерживаемых типов данных. 
- Значение NULL, если функция не возвращает никакого результата.

## <a name="step-3-make-calls-to-the-sqlrutils-package-to-generate-the-stored-procedure"></a>Шаг 3. Выполнение вызовов к пакету sqlrutils для создания хранимой процедуры

После того как код очищен и может быть вызван в виде одной функции, можно приступить к использованию функций в **sqlrutils** для преобразования кода в хранимую процедуру.

В зависимости от типов данных параметров вы будете использовать различные функции для сбора данных и создания объекта параметра.

1. Если функция принимает входные параметры, создайте для каждого из них один из следующих объектов: 
    - Если входной параметр является кадром данных, используйте `setInputData`.
    - Для всех других входных параметров используйте `setInputParameter`.

2. Если функция выводит список, создайте объект для обработки необходимых данных из списка: 
    - Если переменная в списке является кадром данных, используйте `setOutputData`.
    - Для всех других элементов списка используйте `setOutputParameter`.
    - Если функция выводит кадр данных напрямую, без первоначального объединения его в список, этот шаг можно пропустить. 
    - Этот шаг можно пропустить, если функция возвращает значение NULL.

3. Когда готовы все входные и выходные параметры, выполните вызов к конструктору `StoredProcedure` для создания хранимой процедуры, содержащей функцию R.
4. Чтобы немедленно зарегистрировать хранимую процедуру в базе данных, используйте `registerStoredProcedure`.

## <a name="step-4-execute-the-stored-procedure"></a>Шаг 4. Выполнение хранимой процедуры

1. Если вы хотите выполнить хранимую процедуру из кода R, а не из SQL Server, и этой хранимой процедуре требуются входные данные, следует задать эти входные параметры до того момента, когда функция может быть выполнена. 
    - Вызовите `getInputParameters` для получения списка объектов входных параметров.
    - Определение `$query` или задайте `$value` для каждого входного параметра. 

2. Используйте `executeStoredProcedure` для выполнения хранимой процедуры из среды разработки R, передавая список заданных объектов входных параметров.

## <a name="a-name-samplesaexamples-prepare-your-code"></a><a name = "samples"></a>Примеры: подготовка кода 

В этом примере код R считывает информацию из базы данных, выполняет некоторые преобразования этих данных и сохраняет их в другую базу данных. Этот простой пример служит лишь для демонстрации того, как можно изменить код R, чтобы упростить интерфейс для преобразования хранимой процедуры.

**Перед форматированием**


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
Обратите внимание, что при использовании соединения ODBC вместо вызова функции *RxSqlServerData* следует открыть соединения с помощью *rxOpen*, прежде чем можно будет выполнять операции в базе данных.



**После форматирования**

В преобразованной версии первая строка определяет имя функции.

Весь остальной код из исходного решения R становится частью этой функции. 

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
Хотя вам и не требуется явно открывать соединение ODBC внутри кода, оно по-прежнему должно использовать **sqlrutils**. 


## <a name="see-also"></a>См. также:

[Создание хранимой процедуры с помощью sqlrutils](../../advanced-analytics/r-services/generating-an-r-stored-procedure-for-r-code-using-the-sqlrutils-package.md)

