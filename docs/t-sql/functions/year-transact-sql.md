---
title: "ГОД (Transact-SQL) | Документы Microsoft"
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
- YEAR
- YEAR_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- dates [SQL Server], functions
- dates [SQL Server], years
- date and time [SQL Server], YEAR
- functions [SQL Server], date and time
- YEAR function [SQL Server]
- dateparts [SQL Server], year
ms.assetid: 74aa7ccc-8575-4018-80cf-14aeca379687
caps.latest.revision: 44
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: ee3f419d092f6e8b327dd5e4ac498afa4036ebbb
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="year-transact-sql"></a>YEAR (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Возвращает целое число, представляющее год указанной *даты*.  
  
 Общие сведения о всех [!INCLUDE[tsql](../../includes/tsql-md.md)] типов данных даты и времени и функции, в разделе [даты и времени типов данных и функции &#40; Transact-SQL &#41; ](../../t-sql/functions/date-and-time-data-types-and-functions-transact-sql.md).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
-- Syntax for SQL Server, Azure SQL Database, Azure SQL Data Warehouse, Parallel Data Warehouse  
  
YEAR ( date )  
```  
  
## <a name="arguments"></a>Аргументы  
 *date*  
 Выражение, которое разрешается к **время**, **даты**, **smalldatetime**, **datetime**, **datetime2**, или **datetimeoffset** значение. *Даты* аргумент может быть выражением, выражением столбца, определяемой пользователем переменной или строковым литералом.  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 **int**  
  
## <a name="return-value"></a>Возвращаемое значение  
 Функция YEAR возвращает то же значение, что [DATEPART](../../t-sql/functions/datepart-transact-sql.md) (**года**, *даты*).  
  
 Если *даты* содержит только компонент времени, возвращаемое значение равно 1900, базовому году.  
  
## <a name="examples"></a>Примеры  
 Следующая инструкция возвращает значение `2007`. Порядковый номер года.  
  
```  
SELECT YEAR('2007-04-30T01:01:01.1234567-07:00');  
```  
  
 Следующая инструкция возвращает значение `1900, 1, 1`. Аргумент для *даты* номер `0`. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] интерпретирует `0` как 1 января 1900 г.  
  
```  
SELECT YEAR(0), MONTH(0), DAY(0);  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] и[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 Следующая инструкция возвращает значение `2010`. Порядковый номер года.  
  
```  
SELECT YEAR('2010-07-20T01:01:01.1234');  
```  
  
 Следующая инструкция возвращает значение `1900, 1, 1`. Аргумент для *даты* номер `0`. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] интерпретирует `0` как 1 января 1900 г.  
  
```  
SELECT TOP 1 YEAR(0), MONTH(0), DAY(0);  
```  
  
## <a name="see-also"></a>См. также:  
 [Функции CAST и CONVERT (Transact-SQL)](../../t-sql/functions/cast-and-convert-transact-sql.md)  
  
  


