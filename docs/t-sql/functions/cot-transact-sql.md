---
title: "COT (Transact-SQL) | Документы Microsoft"
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
- COT_TSQL
- COT
dev_langs:
- TSQL
helpviewer_keywords:
- COT function
- cotangent
ms.assetid: c87a9dac-e398-4125-80c3-7df3c2ce6b63
caps.latest.revision: 31
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: d799d83336507aba7b582796f730c53d7ae4840e
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="cot-transact-sql"></a>COT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Математическая функция, которая возвращает тригонометрический котангенс указанного угла в радианах в указанном **float** выражение.
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Синтаксис  
  
```sql
COT ( float_expression )  
```  
  
## <a name="arguments"></a>Аргументы  
*float_expression*  
— [Выражение](../../t-sql/language-elements/expressions-transact-sql.md)типа **float** или типа, который может быть неявно преобразован в **float**.
  
## <a name="return-types"></a>Возвращаемые типы
**float**
  
## <a name="examples"></a>Примеры  
Следующий пример возвращает COT заданного угла.
  
```sql
DECLARE @angle float;  
SET @angle = 124.1332;  
SELECT 'The COT of the angle is: ' + CONVERT(varchar,COT(@angle));  
GO  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
The COT of the angle is: -0.040312                
  
(1 row(s) affected)  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] и[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
Следующий пример возвращает COT заданного угла.
  
```sql
DECLARE @angle float;  
SET @angle = 124.1332;  
SELECT 'The COT of the angle is: ' + CONVERT(varchar,COT(@angle));  
GO  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
The COT of the angle is: -0.040312                
  
(1 row(s) affected)  
```  
  
## <a name="see-also"></a>См. также:
[Математические функции &#40; Transact-SQL &#41;](../../t-sql/functions/mathematical-functions-transact-sql.md)
  
  


