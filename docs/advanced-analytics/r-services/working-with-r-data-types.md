---
title: "Работа с типами данных R | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "01/31/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5df99e1c-a89a-42c1-9d68-ffe8d9577c94
caps.latest.revision: 16
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 12
---
# Работа с типами данных R
  В то время как [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживает несколько типов данных десятков R имеет ограниченное число скалярных типов данных (числовые, целое число, сложные логические, знаков, даты и времени и raw). Таким образом, при использовании в сценариях R данных из  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] возможны следующие ситуации.  
  
-   Данные неявно преобразуются в совместимый тип данных.  
  
-   Данные не удается неявно преобразовать, возвращается сообщение об ошибке.  
  
 Как правило, если у вас есть сомнения по поводу использования определенного типа или структуры данных в R, воспользуйтесь функцией  `str()` , чтобы получить внутреннюю структуру и тип объекта R. Результат выполнения функции выводится на консоль R. Также он доступен в результатах запроса, на вкладке **Сообщения** в [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].  
  
 Если определенное [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] тип данных не поддерживается R, но необходимо использовать в скрипте R столбцы данных, мы рекомендуем использовать [CAST и CONVERT & #40; Transact-SQL & #41;](../../t-sql/functions/cast-and-convert-transact-sql.md) функции, чтобы убедиться, что преобразование типов данных выполняется должным образом перед использованием их в скрипте R.  
  
 Дополнительные сведения о [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] см. типы данных, [типы данных & #40; Transact-SQL и #41;](../../t-sql/data-types/data-types-transact-sql.md)  
  
## Преобразование типов данных между R и SQL Server  
 В следующей таблице показано, как меняются типы данных и значения, когда данные из [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] используются в сценариях R и затем возвращаются в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
|||||  
|-|-|-|-|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] type|Класс R|Тип в **RESULT SET**|Комментарии|  
|**smalldatetime**|`POSIXct`|**DateTime**|Указывается в формате GMT|  
|**smallmoney**|`numeric`|**Число с плавающей запятой**||  
|**DateTime**|`POSIXct`|**DateTime**|Указывается в формате GMT|  
|**money**|`numeric`|**Число с плавающей запятой**||  
|**uniqueidentifier**|`character`|**varchar(max)**||  
|**numeric(p,s)**|`numeric`|**Число с плавающей запятой**||  
|**Decimal(p,s)**|`numeric`|**Число с плавающей запятой**||  
|**date**|`POSIXct`|**DateTime**|Указывается в формате GMT|  
|**tinyint**|`integer`|**int**||  
|**bit**|`logical`|**bit**||  
|**smallint**|`integer`|**int**||  
|**int**|`integer`|**int**||  
|**Число с плавающей запятой**|`numeric`|**Число с плавающей запятой**||  
|**real**|`numeric`|**Число с плавающей запятой**||  
|**bigint**|`numeric`|**Число с плавающей запятой**||  
|**binary(n)**<br /><br /> n <= 8000|`raw`|**varbinary(max)**|Может использоваться только для входных параметров и выходных данных|  
|**char(n)**<br /><br /> n <= 8000|`character`|**varchar(max)**||  
|**varbinary(n)**<br /><br /> n <= 8000|`raw`|**varbinary(max)**|Может использоваться только для входных параметров и выходных данных|  
|**varchar(n)**<br /><br /> n <= 8000|`character`|**varchar(max)**||  
|**varbinary(max)**|`raw`|**varbinary(max)**|Может использоваться только для входных параметров и выходных данных|  
  
## Примеры преобразования типов данных  
 Следующий запрос возвращает последовательность значений из [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] таблицы и хранимой процедуры  [sp_execute_external_script & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) для вывода значений, используя R среды выполнения.  
  
```  
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
  
```  
'data.frame':2 obs. of  4 variables:   
 $ c1: int  1 -11   
 $ c2: Factor w/ 2 levels "Hello","world": 1 2   
 $ c3: Factor w/ 2 levels "6732EA46-2D5D-430B-8A01-86E7F3351C3E",..: 2 1   
 $ cR: num  4 2  
```  
  
 На приведенном примере можно увидеть, что при выполнении этого запроса были выполнены следующие типы неявных преобразований.  
  
-   **Столбец C1**. Столбец представляется как **int** в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], `integer` в R, и **int** в выходных данных результирующем наборе.  
  
     Преобразование типа не выполнялось.  
  
-   **Столбец C2**. Столбец представляется как **varchar(10)** в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], `factor` в R, и **varchar(max)** в выходных данных.  
  
     Обратите внимание, как изменяется выходные данные; Любая строка из R (коэффициент или обычной строкой) будет представлен как **varchar(max)**, независимо от длины строк.  
  
-   **Столбец C3**.  Столбец представляется как **uniqueidentifier** в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], `character` в R, и **varchar(max)** в выходных данных.  
  
     Обратите внимание на преобразование типа данных. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживает **uniqueidentifier** но не поддерживает R; таким образом, идентификаторы представлены в виде строки.  
  
-   **Столбец C4**. Этого столбца нет в исходных данных. Он содержит значения, созданные сценарием R.  
 
 ## См. также:
 [Возможности и задачи служб R SQL Server](../../advanced-analytics/r-services/sql-server-r-services-features-and-tasks.md)
  
  