---
title: "ДЕНЬ (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 07/30/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DAY_TSQL
- DAY
dev_langs:
- TSQL
helpviewer_keywords:
- date and time [SQL Server], DAY
- dates [SQL Server], functions
- DAY function [SQL Server]
- dates [SQL Server], days
- functions [SQL Server], date and time
- dateparts [SQL Server], day
ms.assetid: 2f4410ea-fd3e-4d69-ac4b-3b0091a084bc
caps.latest.revision: 41
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 98e0a1f548fdec917f265595a4a06ec795c5f37e
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="day-transact-sql"></a>DAY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Возвращает целое число, представляющее день (день месяца) указанной *даты*.
  
Общие сведения о всех [!INCLUDE[tsql](../../includes/tsql-md.md)] типов данных даты и времени и функции, в разделе [даты и времени типов данных и функции &#40; Transact-SQL &#41; ](../../t-sql/functions/date-and-time-data-types-and-functions-transact-sql.md).
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Синтаксис  
  
```sql
DAY ( date )  
```  
  
## <a name="arguments"></a>Аргументы  
*date*  
Выражение, которое разрешается к **время**, **даты**, **smalldatetime**, **datetime**, **datetime2**, или **datetimeoffset** значение. *Даты* аргумент может быть выражением, выражением столбца, определяемой пользователем переменной или строковым литералом.
  
## <a name="return-type"></a>Тип возвращаемых данных  
**int**
  
## <a name="return-value"></a>Возвращаемое значение  
Функция DAY возвращает то же значение, что [DATEPART](../../t-sql/functions/datepart-transact-sql.md) (**день**, *даты*).
  
Если *даты* содержит только компонент времени, возвращаемое значение равно 1, базовому дню.
  
## <a name="examples"></a>Примеры  
Следующая инструкция возвращает значение `30`. Порядковый номер дня.
  
```sql
SELECT DAY('2015-04-30 01:01:01.1234567');  
```  
  
Следующая инструкция возвращает значение `1900, 1, 1`. Аргумент для *даты* номер `0`. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] интерпретирует `0` как 1 января 1900 г.
  
```sql
SELECT YEAR(0), MONTH(0), DAY(0);  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] и[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
В следующем примере возвращается `30`. Порядковый номер дня.
  
```sql
-- Uses AdventureWorks  
  
SELECT TOP 1 DAY('2010-07-30T01:01:01.1234')   
FROM dbo.DimCustomer;  
```  
  
В следующем примере возвращается `1900, 1, 1`. Аргумент для *даты* номер `0`. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] интерпретирует `0` как 1 января 1900 г.
  
```sql
-- Uses AdventureWorks  
  
SELECT TOP 1 YEAR(0), MONTH(0), DAY(0) FROM dbo.DimCustomer;  
```  
  
## <a name="see-also"></a>См. также:
[Функции CAST и CONVERT (Transact-SQL)](../../t-sql/functions/cast-and-convert-transact-sql.md)
  
  



