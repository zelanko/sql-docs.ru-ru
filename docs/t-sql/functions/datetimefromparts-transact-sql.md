---
title: "DATETIMEFROMPARTS (Transact-SQL) | Документы Майкрософт"
ms.custom: 
ms.date: 07/29/2017
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
- DATETIMEFROMPARTS_TSQL
- DATETIMEFROMPARTS
dev_langs:
- TSQL
helpviewer_keywords:
- DATETIMEFROMPARTS function
ms.assetid: 6008148b-bf75-4c98-9392-68a89fa0711c
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: ef125163e41d9ab1b2b465a31694428d22407501
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="datetimefromparts-transact-sql"></a>DATETIMEFROMPARTS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-all-md](../../includes/tsql-appliesto-ss2012-all-md.md)]

Возвращает значение **datetime**, соответствующее указанной дате и времени.
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Синтаксис  
  
```sql
DATETIMEFROMPARTS ( year, month, day, hour, minute, seconds, milliseconds )  
```  
  
## <a name="arguments"></a>Аргументы  
*year*  
Целочисленное выражение, задающее год.
  
*month*  
Целочисленное выражение, задающее месяц.
  
*day*  
Целочисленное выражение, задающее день.
  
*hour*  
Целочисленное выражение, задающее часы.
  
*minute*  
Целочисленное выражение, задающее минуты.
  
*секунд*  
Целочисленное выражение, задающее секунды.
  
*milliseconds*  
Целочисленное выражение, задающее миллисекунды.
  
## <a name="return-types"></a>Типы возвращаемых данных
**datetime**
  
## <a name="remarks"></a>Remarks  
**DATETIMEFROMPARTS** возвращает полностью инициализированное значение **datetime**. Если аргументы недопустимы, то возникает ошибка. Если требуемые аргументы имеют значение NULL, возвращается NULL.
  
Для серверов [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] и выше данная функция может быть удаленной. Данная функция не может быть удаленной для серверов с версией ниже [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].
  
## <a name="examples"></a>Примеры  
  
```sql
SELECT DATETIMEFROMPARTS ( 2010, 12, 31, 23, 59, 59, 0 ) AS Result;  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
Result  
---------------------------  
2010-12-31 23:59:59.000  
  
(1 row(s) affected)  
```  
  
## <a name="see-also"></a>См. также раздел
[datetime (Transact-SQL)](../../t-sql/data-types/datetime-transact-sql.md)
  
  

