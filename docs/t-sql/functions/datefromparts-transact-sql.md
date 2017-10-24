---
title: "DATEFROMPARTS (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 07/29/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DATEFROMPARTS_TSQL
- DATEFROMPARTS
dev_langs:
- TSQL
helpviewer_keywords:
- DATEFROMPARTS function
ms.assetid: 5b885376-87aa-41f1-9e18-04987aead250
caps.latest.revision: 16
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 77c7eb1fcde9b073b3c08f412ac0e46519763c74
ms.openlocfilehash: a94584788187162e4cd7d433d71653a04c5103e2
ms.contentlocale: ru-ru
ms.lasthandoff: 10/17/2017

---
# <a name="datefromparts-transact-sql"></a>DATEFROMPARTS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-all_md](../../includes/tsql-appliesto-ss2012-all-md.md)]

Возвращает **даты** значение для заданного года, месяца и дня.
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Синтаксис  
  
```sql
DATEFROMPARTS ( year, month, day )  
```  
  
## <a name="arguments"></a>Аргументы  
*год*  
Целочисленное выражение, задающее год.
  
*месяц*  
Целочисленное выражение от 1 до 12, задающее месяц.
  
*день*  
Целочисленное выражение, задающее день.
  
## <a name="return-types"></a>Возвращаемые типы
**date**
  
## <a name="remarks"></a>Замечания  
**DATEFROMPARTS** возвращает **даты** значение с присвоено указанный год, месяц и день часть даты и части времени по умолчанию. Если аргументы недопустимы, то возникает ошибка. Если требуемые аргументы имеют значение NULL, возвращается NULL.
  
Для серверов [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] и выше данная функция может быть удаленной. Данная функция не может быть удаленной для серверов с версией ниже [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)].
  
## <a name="examples"></a>Примеры  
В следующем примере демонстрируется **DATEFROMPARTS** функции.
  
```sql
SELECT DATEFROMPARTS ( 2010, 12, 31 ) AS Result;  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
Result  
----------------------------------  
2010-12-31  
  
(1 row(s) affected)  
```  
  
## <a name="see-also"></a>См. также:
[date &#40;Transact-SQL&#41;](../../t-sql/data-types/date-transact-sql.md)
  
  


