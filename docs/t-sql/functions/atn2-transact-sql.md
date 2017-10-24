---
title: "ATN2 (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 07/24/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ATN2
- ATN2_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- arctangent
- tangent
- ATN2 function
ms.assetid: 014b291e-7cd7-4c39-b20d-5db3a9f0505d
caps.latest.revision: 36
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 77c7eb1fcde9b073b3c08f412ac0e46519763c74
ms.openlocfilehash: 3c68b65c2bde2d8b4c5cd8f34452563b433c6a29
ms.contentlocale: ru-ru
ms.lasthandoff: 10/17/2017

---
# <a name="atn2-transact-sql"></a>ATN2 (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Возвращает угол в радианах между положительным направлением оси X и лучом, проведенным из начала координат в точку (y, x), где x и y — значения двух указанных выражений с плавающей запятой.
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Синтаксис  
  
```sql
ATN2 ( float_expression , float_expression )  
```  
  
## <a name="arguments"></a>Аргументы  
*float_expression* — [выражение](../../t-sql/language-elements/expressions-transact-sql.md) из **float** тип данных.
  
## <a name="return-types"></a>Возвращаемые типы
**float**
  
## <a name="examples"></a>Примеры  
В следующем примере `ATN2` рассчитывается для указанных компонентов `x` и `y`.
  
```sql
DECLARE @x float = 35.175643, @y float = 129.44;  
SELECT 'The ATN2 of the angle is: ' + CONVERT(varchar,ATN2(@x,@y ));  
GO  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
The ATN2 of the angle is: 0.265345                         
(1 row(s) affected)  
```  
  
## <a name="see-also"></a>См. также:
[Функции CAST и CONVERT (Transact-SQL)](../../t-sql/functions/cast-and-convert-transact-sql.md)  
[&#40; float и real Transact-SQL &#41;](../../t-sql/data-types/float-and-real-transact-sql.md)  
[Математические функции &#40; Transact-SQL &#41;](../../t-sql/functions/mathematical-functions-transact-sql.md)
  
  


