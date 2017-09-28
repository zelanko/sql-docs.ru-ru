---
title: "SQRT (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SQRT
- SQRT_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- SQRT function
- square root values
ms.assetid: 26e244e8-e82d-4664-a445-1226230ee1c5
caps.latest.revision: 37
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 5287fca25554a29211a48ab9584bc893b097686a
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="sqrt-transact-sql"></a>SQRT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Возвращает квадратный корень данного числа с плавающей точкой.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
SQRT ( float_expression )  
```  
  
## <a name="arguments"></a>Аргументы  
 *float_expression*  
 — [Выражение](../../t-sql/language-elements/expressions-transact-sql.md) типа **float** или типа, который может быть неявно преобразован в тип float.  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 **float**  
  
## <a name="examples"></a>Примеры  
 Следующий пример возвращает квадратный корень чисел от `1.00` до `10.00`.  
  
```  
DECLARE @myvalue float;  
SET @myvalue = 1.00;  
WHILE @myvalue < 10.00  
   BEGIN  
      SELECT SQRT(@myvalue);  
      SET @myvalue = @myvalue + 1  
   END;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
------------------------   
1.0                        
------------------------   
1.4142135623731            
------------------------   
1.73205080756888           
------------------------   
2.0                        
------------------------   
2.23606797749979           
------------------------   
2.44948974278318           
------------------------   
2.64575131106459           
------------------------   
2.82842712474619           
------------------------   
3.0  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] и[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 Следующий пример возвращает квадратный корень чисел `1.00` и `10.00`.  
  
```  
SELECT SQRT(1.00), SQRT(10.00);  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `----------  ------------`  
  
 `1.00        3.16`  
  
## <a name="see-also"></a>См. также:  
 [Математические функции &#40; Transact-SQL &#41;](../../t-sql/functions/mathematical-functions-transact-sql.md)  
  
  


