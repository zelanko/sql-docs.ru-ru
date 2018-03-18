---
title: "DAY (Transact-SQL) | Документы Майкрософт"
ms.custom: 
ms.date: 07/30/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
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
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: 444df60a2cfe3adae045020b3db8d673946dccb1
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="day-transact-sql"></a>DAY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Возвращает целое число, представляющее день (день месяца) указанной даты *date*.
  
Обзор всех типов данных и функций даты и времени в языке [!INCLUDE[tsql](../../includes/tsql-md.md)] см. в статье [Типы данных и функции даты и времени (Transact-SQL)](../../t-sql/functions/date-and-time-data-types-and-functions-transact-sql.md).
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Синтаксис  
  
```sql
DAY ( date )  
```  
  
## <a name="arguments"></a>Аргументы  
*date*  
Выражение, которое можно привести к значению типа **time**, **date**, **smalldatetime**, **datetime**, **datetime2** или **datetimeoffset**. Аргумент *date* может быть выражением, выражением столбца, определяемой пользователем переменной или строковым литералом.
  
## <a name="return-type"></a>Тип возвращаемых данных  
**int**
  
## <a name="return-value"></a>Возвращаемое значение  
Функция DAY возвращает то же значение, что и [DATEPART](../../t-sql/functions/datepart-transact-sql.md) (**day**, *date*).
  
Если дата *date* содержит только компонент времени, возвращаемое значение равно 1, базовому дню.
  
## <a name="examples"></a>Примеры  
Следующая инструкция возвращает значение `30`. Порядковый номер дня.
  
```sql
SELECT DAY('2015-04-30 01:01:01.1234567');  
```  
  
Следующая инструкция возвращает значение `1900, 1, 1`. В качестве значения аргумента *date* задается число `0`. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] интерпретирует `0` как 1 января 1900 г.
  
```sql
SELECT YEAR(0), MONTH(0), DAY(0);  
```  
  
## <a name="see-also"></a>См. также раздел
[Функции CAST и CONVERT (Transact-SQL)](../../t-sql/functions/cast-and-convert-transact-sql.md)
  
  


