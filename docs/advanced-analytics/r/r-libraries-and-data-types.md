---
title: "Работа с типами данных R | Документация Майкрософт"
ms.custom: SQL2016_New_Updated
ms.date: 01/31/2017
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5df99e1c-a89a-42c1-9d68-ffe8d9577c94
caps.latest.revision: "16"
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: e72c4a984359230ace9f800e8ac4efbfcfe5f2a1
ms.sourcegitcommit: 23433249be7ee3502c5b4d442179ea47305ceeea
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/20/2017
---
# <a name="r-libraries-and-r-data-types"></a>Библиотеки R и типами данных R

В этом разделе описываются библиотеки R, которые будут включены и типы данных, которые поддерживаются в следующих продуктах.

+ Службы R SQL Server 2016 (в базе данных)
+ Изучение служб (в базе данных) машины SQL Server

В этом разделе также перечислены неподдерживаемые типы данных и списки тип данных преобразования, которые может выполнять неявно при передаче данных между R и SQL Server.

## <a name="r-libraries"></a>Библиотеки R

Оба продукта служб R и Machine Services обучения с помощью R, выравнивается с отдельными выпусками Microsoft R Open. Например, последний выпуск служб SQL Server 2017 г машины обучения, основана на Microsoft R Open 3.3.3.

Чтобы узнать версию R, связанные с конкретным экземпляром SQL Server, откройте RGui.

1. Для экземпляра по умолчанию путь будет следующим:`C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\R_SERVICES\bin\x64\`
2. Отображается сообщение, список рассылки R и Microsoft R Open номер версии.

Версии R, включенных в определенной версии Microsoft R Server, в разделе [R Server — новые](https://msdn.microsoft.com/microsoft-r/rserver-whats-new#new-and-updated-packages).

Обратите внимание, что означает, что несколько версий пакет R можно установить на том же компьютере с несколькими пользователями, совместное использование того же пакета, или с использованием разных версий одного пакета, система управления пакетами в SQL Server. Дополнительные сведения см. в разделе [управления пакета R в SQL Server](../r/r-package-management-for-sql-server-r-services.md).

## <a name="r-and-sql-data-types"></a>Типы данных SQL и R

В то время как [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживает несколько десятков типов данных, R имеет ограниченное число скалярных типов данных (числовые, целое число, символ сложные данные, логические, даты и времени и raw). В результате при использовании данных из [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в сценариях R, данные могут быть неявно преобразованы в совместимый тип данных. Тем не менее часто точное преобразование не может выполняться автоматически, и возвращается сообщение об ошибке, например «Тип данных необработанное SQL».

В этом разделе перечислены неявные преобразования, которые предоставляются и перечислены типы данных не поддерживается. Некоторые рекомендации обеспечивает сопоставление типов данных между R и SQL Server.

## <a name="implicit-data-type-conversions-between-r-and-sql-server"></a>Неявные преобразования типов данных между R и SQL Server

В следующей таблице показано, как меняются типы данных и значения, когда данные из [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] используются в сценариях R и затем возвращаются в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].

|Тип SQL|Класс R|Тип результирующего набора|Комментарии|
|-|-|-|-|
|**bigint**|`numeric`|**float**||
|**binary(n)**<br /><br /> n <= 8000|`raw`|**varbinary(max)**|Может использоваться только для входных параметров и выходных данных|
|**bit**|`logical`|**bit**||
|**char(n)**<br /><br /> n <= 8000|`character`|**varchar(max)**||
|**datetime**|`POSIXct`|**datetime**|Указывается в формате GMT|
|**date**|`POSIXct`|**datetime**|Указывается в формате GMT|
|**decimal(p,s)**|`numeric`|**float**||
|**float**|`numeric`|**float**||
|**int**|`integer`|**int**||
|**money**|`numeric`|**float**||
|**numeric(p,s)**|`numeric`|**float**||
|**real**|`numeric`|**float**||
|**smalldatetime**|`POSIXct`|**datetime**|Указывается в формате GMT|
|**smallint**|`integer`|**int**||
|**smallmoney**|`numeric`|**float**||
|**tinyint**|`integer`|**int**||
|**uniqueidentifier**|`character`|**varchar(max)**||
|**varbinary(n)**<br /><br /> n <= 8000|`raw`|**varbinary(max)**|Может использоваться только для входных параметров и выходных данных|
|**varbinary(max)**|`raw`|**varbinary(max)**|Может использоваться только для входных параметров и выходных данных|
|**varchar(n)**<br /><br /> n <= 8000|`character`|**varchar(max)**||


## <a name="data-types-not-supported-by-r"></a>Типы данных, не поддерживаемые языком R

Следующие типы данных, поддерживаемые [системой типов SQL Server](../../t-sql/data-types/data-types-transact-sql.md), могут создавать проблемы при передаче в код R:

+ Типы данных, перечисленные в **других** раздела систему типов SQL: **курсор**, **timestamp**, **hierarchyid**,  **uniqueidentifier**, **sql_variant**, **xml**, **таблицы**
+ все пространственные типы;
+ **image**

## <a name="data-types-that-might-convert-poorly"></a>Типы данных, которые могут быть преобразованы с ошибками

+ Большинство типов datetime поддерживаются, за исключением типа **datetimeoffset**. 
+ Большинство числовых типов данных поддерживаются, но преобразования могут завершаться ошибкой для типов **money** и **smallmoney**.
+ Поддерживается тип **varchar**, но так как SQL Server, как правило, использует формат Юникод, во всех возможных случаях рекомендуется применять **nvarchar** и другие типы текстовых данных в Юникоде.
+ Функции библиотеки RevoScaleR, которые начинаются с префикса rx, могут обрабатывать двоичные типы данных SQL (например, **binary** и **varbinary**), но в большинстве случаев для этих типов требуется особая обработка. Большая часть кода R не поддерживает работу с двоичными столбцами.

  
 Дополнительные сведения о типах данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] см. в статье [Data Types (Transact-SQL)](../../t-sql/data-types/data-types-transact-sql.md) (Типы данных (Transact-SQL)).

## <a name="changes-in-data-types-between-sql-server-2016-and-earlier-versions"></a>Изменения типов данных между SQL Server 2016 и более ранними версиями

Microsoft SQL Server 2016 и база данных SQL Microsoft Azure содержат улучшения преобразований типов данных и других операций. Большинство этих улучшений обеспечивают повышенную точность при работе с типами с плавающей запятой, а также незначительные изменения операций в классических типах **datetime**.

Эти улучшения доступны по умолчанию при использовании уровня совместимости базы данных 130 и выше. Однако при использовании другого уровня совместимости или подключении к базе данных с помощью более старой версии, точность чисел или других результатов может отличаться. 

Дополнительные сведения см. в статье [SQL Server 2016 improvements in handling some data types and uncommon operations](https://support.microsoft.com/help/4010261/sql-server-2016-improvements-in-handling-some-data-types-and-uncommon-) (Улучшения SQL Server 2016 для обработки некоторых типов данных и нестандартных операций).
 

## <a name="verify-r-and-sql-data-schemas-in-advance"></a>Предварительная проверка схем данных R и SQL 

Как правило, если у вас есть сомнения по поводу использования определенного типа или структуры данных в R, воспользуйтесь функцией  `str()` , чтобы получить внутреннюю структуру и тип объекта R. Результат выполнения функции выводится на консоль R. Также он доступен в результатах запроса, на вкладке **Сообщения** в [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]. 

При получении данных из базы данных для использования в коде R всегда следует удалять столбцы, которые нельзя использовать в R, а также столбцы, бесполезные при анализе, например идентификаторы GUID (uniqueidentifier), метки времени и другие столбцы, используемые для аудита или данных журнала преобразований, созданных в рамках процессов извлечения, преобразования и загрузки. 

Обратите внимание, что включение ненужных столбцов может значительно снизить производительность кода R, особенно если столбцы большого количества элементов используются как коэффициенты. Поэтому мы советуем использовать системные хранимые процедуры SQL Server и представления сведений для получения типов данных для данной таблицы заранее и устранения или преобразования несовместимых столбцов. Дополнительные сведения см. в статье о [представлении информационной схемы в Transact-SQL](../../relational-databases/system-information-schema-views/system-information-schema-views-transact-sql.md).

Если определенный тип данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не поддерживается языком R, но вам необходим доступ к столбцам этого типа в скрипте R, мы советуем использовать функции [CAST и CONVERT (Transact-SQL)](../../t-sql/functions/cast-and-convert-transact-sql.md). С их помощью вы сможете правильно преобразовать тип данных в скрипте R.  

> [!WARNING]
При использовании **rxDataStep** для удаления несовместимых столбцов во время перемещения данных учтите, что аргументы _varsToKeep_ и _varsToDrop_ не поддерживаются для типа источника данных **RxSqlServerData**.


## <a name="examples"></a>Примеры

### <a name="example-1-implicit-conversion"></a>Пример 1. Неявное преобразование

В следующем примере показано преобразование данных при выполнении цикла приема-передачи между SQL Server и R.

Запрос возвращает последовательность значений из [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] таблицы и хранимой процедуры [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) для вывода значений при помощи среды выполнения R.

```SQL
CREATE TABLE MyTable (    
 c1 int,    
 c2 varchar(10),    
 c3 uniqueidentifier    
);    
go    
INSERT MyTable VALUES(1, 'Hello', newid());    
INSERT MyTable VALUES(-11, 'world', newid());    
SELECT * FROM MyTable;    
  
EXECUTE sp_execute_external_script    
 @language = N'R'    
 , @script = N'    
inputDataSet["cR"] <- c(4, 2)    
str(inputDataSet)    
outputDataSet <- inputDataSet'    
 , @input_data_1 = N'SELECT c1, c2, c3 FROM MyTable'    
 , @input_data_1_name = N'inputDataSet'    
 , @output_data_1_name = N'outputDataSet'    
 WITH RESULT SETS((C1 int, C2 varchar(max), C3 varchar(max), C4 float));  
```

**Результаты**

||||||
|-|-|-|-|-|
||C1|C2|C3|C4|
|1|1|Привет|6e225611-4b58-4995-a0a5-554d19012ef1|4|
|1|-11|мир|6732ea46-2d5d-430b-8ao1-86e7f3351c3e|2|

Обратите внимание на использование функции `str` в R для получения схемы выходных данных. Эта функция возвращает следующую информацию:

<code>'data.frame':2 obs. of  4 variables:</code>
<code> $ c1: int  1 -11</code>
<code> $ c2: Factor w/ 2 levels "Hello","world": 1 2</code>
<code> $ c3: Factor w/ 2 levels "6732EA46-2D5D-430B-8A01-86E7F3351C3E",..: 2 1</code>
<code> $ cR: num  4 2</code>

На приведенном примере можно увидеть, что при выполнении этого запроса были выполнены следующие типы неявных преобразований.

-   **Столбец C1**. В **ssNoversion** этот столбец имеет тип [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], в R — `integer` , а в выходном наборе данных — **ssNoversion** .  
  
     Преобразование типа не выполнялось.  
  
-   **Столбец C2**. В **ssNoversion** этот столбец имеет тип [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], в R — `factor` , а в выходном наборе данных — **varchar(max)** .  
  
     Обратите внимание, что тип выходных данных изменился. Любая строка из R (фактор или обычная строка) будет представлена как **varchar(max)**вне зависимости от длины строки.  
  
-   **Столбец C3**.  В **ssNoversion** этот столбец имеет тип [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], в R — `character` , а в выходном наборе данных — **varchar(max)** .
  
     Обратите внимание на преобразование типа данных. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживает тип **ssNoversion** , но R — нет. Поэтому идентификаторы представляются в виде строк.
  
-   **Столбец C4**. Этого столбца нет в исходных данных. Он содержит значения, созданные сценарием R.


## <a name="example-2-dynamic-column-selection-using-r"></a>Пример 2. Динамический выбор столбцов с помощью R

В следующем примере показано, как использовать код R для проверки на наличие недопустимых типов столбцов. Приведенный ниже код получает схему указанной таблицы с помощью системных представлений SQL Server и удаляет все столбцы с заданным недопустимым типом.

```R
connStr <- "Server=.;Database=TestDB;Trusted_Connection=Yes"
data <- RxSqlServerData(connectionString = connStr, sqlQuery = "SELECT COLUMN_NAME FROM TestDB.INFORMATION_SCHEMA.COLUMNS WHERE TABLE_NAME = N'testdata' AND DATA_TYPE <> 'image';")
columns <- rxImport(data)
columnList <- do.call(paste, c(as.list(columns$COLUMN_NAME), sep = ","))
sqlQuery <- paste("SELECT", columnList, "FROM testdata")
```

## <a name="see-also"></a>См. также:

[Библиотеки Python и типы данных](../python/python-libraries-and-data-types.md)
