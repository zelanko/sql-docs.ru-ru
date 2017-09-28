---
title: "SYSDATETIMEOFFSET (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SYSDATETIMEOFFSET_TSQL
- SYSDATETIMEOFFSET
dev_langs:
- TSQL
helpviewer_keywords:
- date and time [SQL Server], SYSDATETIMEOFFSET
- dates [SQL Server], functions
- current date and time [SQL Server]
- functions [SQL Server], time
- system date and time [SQL Server]
- system time [SQL Server]
- SYSDATETIMEOFFSET function [SQL Server]
- functions [SQL Server], date and time
- time [SQL Server], functions
- dates [SQL Server], current date and time
- dates [SQL Server], system date and time
- time zones [SQL Server]
- time [SQL Server], system
ms.assetid: 8423c753-cebe-4edd-871d-0138e092199f
caps.latest.revision: 43
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 2497aa71cae4fa7cf5fecf6fe6bd1383d84680a1
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="sysdatetimeoffset-transact-sql"></a>SYSDATETIMEOFFSET (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Возвращает **datetimeoffset(7)** значение, содержащее дату и время компьютера, на котором экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] запущена. Смещение часового пояса включается.  
  
 Общие сведения о всех [!INCLUDE[tsql](../../includes/tsql-md.md)] типов данных даты и времени и функции, в разделе [даты и времени типов данных и функции &#40; Transact-SQL &#41; ](../../t-sql/functions/date-and-time-data-types-and-functions-transact-sql.md).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
SYSDATETIMEOFFSET ( )  
```  
  
## <a name="return-type"></a>Тип возвращаемых данных  
 **DateTimeOffset(7)**  
  
## <a name="remarks"></a>Замечания  
 [!INCLUDE[tsql](../../includes/tsql-md.md)]инструкции могут ссылаться на функцию SYSDATETIMEOFFSET в любом месте, они могут ссылаться на **datetimeoffset** выражение.  
  
 Функция SYSDATETIMEOFFSET недетерминированная. Невозможно проиндексировать представления и выражения, ссылающиеся на эту функцию в столбце.  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Получает значения даты и времени с помощью GetSystemTimeAsFileTime() Windows API. Точность зависит от физического оборудования и версии Windows, в которой запущен экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Точность возвращаемых значений этого API-интерфейса задана равной 100 нс. Точность может быть определена с помощью GetSystemTimeAdjustment() Windows API.  
  
## <a name="examples"></a>Примеры  
 В следующих примерах с помощью шести системных функций [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], которые возвращают текущую дату и время, происходит возврат даты, времени или и того и другого. Значения возвращаются последовательно и поэтому могут различаться на доли секунды.  
  
### <a name="a-showing-the-formats-that-are-returned-by-the-date-and-time-functions"></a>A. Отображение форматов, которые возвращаются функциями даты и времени  
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
  
 `SYSDATETIME()      2007-04-30 13:10:02.0474381`  
  
 `SYSDATETIMEOFFSET()2007-04-30 13:10:02.0474381 -07:00`  
  
 `SYSUTCDATETIME()   2007-04-30 20:10:02.0474381`  
  
 `CURRENT_TIMESTAMP  2007-04-30 13:10:02.047`  
  
 `GETDATE()          2007-04-30 13:10:02.047`  
  
 `GETUTCDATE()       2007-04-30 20:10:02.047`  
  
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
  
 `2007-04-30`  
  
 `2007-04-30`  
  
 `2007-04-30`  
  
 `2007-04-30`  
  
 `2007-04-30`  
  
 `2007-04-30`  
  
### <a name="c-converting-date-and-time-to-times"></a>В. Преобразование даты и времени во время  
 В следующем примере показано, как преобразовать значения даты и времени в тип `time`.  
  
```  
SELECT CONVERT (time, SYSDATETIME()) AS SYSDATETIME()  
    ,CONVERT (time, SYSDATETIMEOFFSET()) AS SYSDATETIMEOFFSET()  
    ,CONVERT (time, SYSUTCDATETIME()) AS SYSUTCDATETIME()  
    ,CONVERT (time, CURRENT_TIMESTAMP) AS CURRENT_TIMESTAMP  
    ,CONVERT (time, GETDATE()) AS GETDATE()  
    ,CONVERT (time, GETUTCDATE()) AS GETUTCDATE();  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `SYSDATETIME()      13:18:45.3490361`  
  
 `SYSDATETIMEOFFSET()13:18:45.3490361`  
  
 `SYSUTCDATETIME()   20:18:45.3490361`  
  
 `CURRENT_TIMESTAMP  13:18:45.3470000`  
  
 `GETDATE()          13:18:45.3470000`  
  
 `GETUTCDATE()       20:18:45.3470000`  
  
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
  
 `SYSDATETIME()      2007-04-30 13:10:02.0474381`  
  
 `SYSDATETIMEOFFSET()2007-04-30 13:10:02.0474381 -07:00`  
  
 `SYSUTCDATETIME()   2007-04-30 20:10:02.0474381`  
  
 `CURRENT_TIMESTAMP  2007-04-30 13:10:02.047`  
  
 `GETDATE()          2007-04-30 13:10:02.047`  
  
 `GETUTCDATE()       2007-04-30 20:10:02.047`  
  
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
  
 `2007-04-30`  
  
 `2007-04-30`  
  
 `2007-04-30`  
  
 `2007-04-30`  
  
 `2007-04-30`  
  
 `2007-04-30`  
  
### <a name="f-converting-date-and-time-to-times"></a>Е. Преобразование даты и времени во время  
 В следующем примере показано, как преобразовать значения даты и времени в тип `time`.  
  
```  
SELECT CONVERT (time, SYSDATETIME()) AS SYSDATETIME()  
    ,CONVERT (time, SYSDATETIMEOFFSET()) AS SYSDATETIMEOFFSET()  
    ,CONVERT (time, SYSUTCDATETIME()) AS SYSUTCDATETIME()  
    ,CONVERT (time, CURRENT_TIMESTAMP) AS CURRENT_TIMESTAMP  
    ,CONVERT (time, GETDATE()) AS GETDATE()  
    ,CONVERT (time, GETUTCDATE()) AS GETUTCDATE();  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `SYSDATETIME()      13:18:45.3490361`  
  
 `SYSDATETIMEOFFSET()13:18:45.3490361`  
  
 `SYSUTCDATETIME()   20:18:45.3490361`  
  
 `CURRENT_TIMESTAMP  13:18:45.3470000`  
  
 `GETDATE()          13:18:45.3470000`  
  
 `GETUTCDATE()       20:18:45.3470000`  
  
## <a name="see-also"></a>См. также:  
 [CAST и CONVERT &#40; Transact-SQL &#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)   
 [Данных даты и времени типы и функции &#40; Transact-SQL &#41;](../../t-sql/functions/date-and-time-data-types-and-functions-transact-sql.md)  
  
  


