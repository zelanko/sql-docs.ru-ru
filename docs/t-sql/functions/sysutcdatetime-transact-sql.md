---
title: "SYSUTCDATETIME (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 12/01/2015
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SYSUTCDATETIME
- SYSUTCDATETIME_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- dates [SQL Server], functions
- system time [SQL Server]
- functions [SQL Server], date and time
- time [SQL Server], functions
- date and time [SQL Server], SYSUTCDATETIME
- SYSUTCDATETIME function [SQL Server]
- time [SQL Server], system
ms.assetid: f14fc2cd-9ea8-4daf-88f4-418cf523ab55
caps.latest.revision: 39
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: bc1321dd91a0fcb7ab76b207301c6302bb3a5e64
ms.openlocfilehash: 8055c9410631f303c9f8633fd332e5f7d6f6d763
ms.contentlocale: ru-ru
ms.lasthandoff: 10/06/2017

---
# <a name="sysutcdatetime-transact-sql"></a>SYSUTCDATETIME (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Возвращает **datetime2** значение, содержащее дату и время компьютера, на котором экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] запущена. Дата и время возвращаются в формате UTC (время по Гринвичу). Точность дробной части значения секунд может быть задана в диапазоне от 1 до 7 цифр. Точность по умолчанию составляет 7 цифр.  
  
> [!NOTE]  
>  SYSDATETIME и SYSUTCDATE имеют большую точность в долях секунды, чем GETDATE и GETUTCDATE. SYSDATETIMEOFFSET включает смещение часового пояса, заданное в системе. Функции SYSDATETIME, SYSUTCDATE и SYSDATETIMEOFFSET могут быть присвоены переменным любого типа даты и времени.  
  
 Общие сведения о всех [!INCLUDE[tsql](../../includes/tsql-md.md)] типов данных даты и времени и функции, в разделе [и функций даты и времени типов данных](../../t-sql/functions/date-and-time-data-types-and-functions-transact-sql.md).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
SYSUTCDATETIME ( )  
```  
  
## <a name="return-type"></a>Тип возвращаемых данных  
 **datetime2**  
  
## <a name="remarks"></a>Замечания  
 [!INCLUDE[tsql](../../includes/tsql-md.md)]операторы SYSUTCDATETIME может использоваться в любом месте, они могут ссылаться на **datetime2** выражение.  
  
 Тип SYSUTCDATETIME является недетерминированным. Невозможно проиндексировать представления и выражения, ссылающиеся на эту функцию в столбце.  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Получает значения даты и времени с помощью GetSystemTimeAsFileTime() Windows API. Точность зависит от физического оборудования и версии Windows, в которой запущен экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Точность возвращаемых значений этого API-интерфейса задана равной 100 нс. Точность может быть определена с помощью GetSystemTimeAdjustment() Windows API.  
  
## <a name="examples"></a>Примеры  
 В следующих примерах с помощью шести системных функций [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], которые возвращают текущую дату и время, происходит возврат даты, времени или и того и другого. Значения возвращаются последовательно и поэтому могут различаться на доли секунды.  
  
### <a name="a-showing-the-formats-that-are-returned-by-the-date-and-time-functions"></a>A. Отображение форматов, которые возвращаются функциями даты и времени  
 В следующем примере показаны различные идентификаторы, возвращаемые функциями даты и времени.  
  
```  
SELECT SYSDATETIME() AS SYSDATETIME  
    , SYSDATETIMEOFFSET() AS SYSDATETIMEOFFSET  
    , SYSUTCDATETIME() AS SYSUTCDATETIME  
    , CURRENT_TIMESTAMP AS [CURRENT_TIMESTAMP]
    , GETDATE() AS GETDATE  
    , GETUTCDATE() AS GETUTCDATE;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
| SYSDATETIME | SYSDATETIMEOFFSET | SYSUTCDATETIME | CURRENT_TIMESTAMP | GETDATE | GETUTCDATE |
| --- | --- | --- | --- | --- | --- |
| 2007-04-30 13:10:02.0474381 | 2007-04-30 13:10:02.0474381 -07:00 | 2007-04-30 20:10:02.0474381 | 2007-04-30 13:10:02.047 | 2007-04-30 13:10:02.047 | 2007-04-30 20:10:02.047 |

  
### <a name="b-converting-date-and-time-to-date"></a>Б. Преобразование даты и времени в дату  
 В следующем примере показано, как преобразовать значения даты и времени в тип `date`.  
  
```  
SELECT CONVERT (date, SYSDATETIME())  
    ,CONVERT (date, SYSDATETIMEOFFSET())  
    ,CONVERT (date, SYSUTCDATETIME())  
    ,CONVERT (date, CURRENT_TIMESTAMP)  
    ,CONVERT (date, GETDATE())  
    ,CONVERT (date, GETUTCDATE());  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
2007-04-30
2007-04-30
2007-04-30
2007-04-30
2007-04-30
2007-04-30
```  
  
### <a name="c-converting-date-and-time-values-to-time"></a>В. Преобразование значений даты и времени во время  
 В следующем примере показано, как преобразовать значения даты и времени в тип `time`.  
  
 ```
DECLARE @DATETIME DATETIME = GetDate();
DECLARE @TIME TIME
SELECT @TIME = CONVERT(time, @DATETIME)
SELECT @TIME AS 'Time', @DATETIME AS 'Date Time'
```
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
Time             Date Time  
13:49:33.6330000 2009-04-22 13:49:33.633
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] и[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 В следующих примерах с помощью шести системных функций [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], которые возвращают текущую дату и время, происходит возврат даты, времени или и того и другого. Значения возвращаются последовательно и поэтому могут различаться на доли секунды.  
  
### <a name="d-showing-the-formats-that-are-returned-by-the-date-and-time-functions"></a>Г. Отображение форматов, которые возвращаются функциями даты и времени  
 В следующем примере показаны различные идентификаторы, возвращаемые функциями даты и времени.  
  
```  
SELECT SYSDATETIME() AS SYSDATETIME  
    ,SYSDATETIMEOFFSET() AS SYSDATETIMEOFFSET  
    ,SYSUTCDATETIME() AS SYSUTCDATETIME  
    ,CURRENT_TIMESTAMP AS CURRENT_TIMESTAMP  
    ,GETDATE() AS GETDATE  
    ,GETUTCDATE() AS GETUTCDATE;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
SYSDATETIME()      2007-04-30 13:10:02.0474381
SYSDATETIMEOFFSET()2007-04-30 13:10:02.0474381 -07:00
SYSUTCDATETIME()   2007-04-30 20:10:02.0474381
CURRENT_TIMESTAMP  2007-04-30 13:10:02.047
GETDATE()          2007-04-30 13:10:02.047
GETUTCDATE()       2007-04-30 20:10:02.047
```  
  
### <a name="e-converting-date-and-time-to-date"></a>Д. Преобразование даты и времени в дату  
 В следующем примере показано, как преобразовать значения даты и времени в тип `date`.  
  
```  
SELECT CONVERT (date, SYSDATETIME())  
    ,CONVERT (date, SYSDATETIMEOFFSET())  
    ,CONVERT (date, SYSUTCDATETIME())  
    ,CONVERT (date, CURRENT_TIMESTAMP)  
    ,CONVERT (date, GETDATE())  
    ,CONVERT (date, GETUTCDATE());  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
2007-04-30
2007-04-30
2007-04-30
2007-04-30
2007-04-30
2007-04-30
```  
  
### <a name="f-converting-date-and-time-values-to-time"></a>Е. Преобразование значений даты и времени во время  
 В следующем примере показано, как преобразовать значения даты и времени в тип `time`.  
  
 ```
DECLARE @DATETIME DATETIME = GetDate();
DECLARE @TIME TIME
SELECT @TIME = CONVERT(time, @DATETIME)
SELECT @TIME AS 'Time', @DATETIME AS 'Date Time'
```
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
Time             Date Time  
13:49:33.6330000 2009-04-22 13:49:33.633
```  
  
## <a name="see-also"></a>См. также:  
 [CAST и CONVERT &#40; Transact-SQL &#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)   
 [Данных даты и времени типы и функции &#40; Transact-SQL &#41;](../../t-sql/functions/date-and-time-data-types-and-functions-transact-sql.md)   
 [В ЧАСОВОМ ПОЯСЕ &#40; Transact-SQL &#41;](../../t-sql/queries/at-time-zone-transact-sql.md)  
  
  



