---
title: "ЖУРНАЛ (Transact-SQL) | Документы Microsoft"
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
- LOG
- LOG_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- float expressions
- logarithm of expression
- LOG function
ms.assetid: f7c39511-cd84-4362-93ba-0d93655217ee
caps.latest.revision: 42
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 4531f8e411dbe24a67a6fd5d6ac987fcb2d90c18
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="log-transact-sql"></a>LOG (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Возвращает натуральный логарифм указанного **float** выражения в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
-- Syntax for SQL Server  
  
LOG ( float_expression [, base ] )  
```  
  
```  
-- Syntax for Azure SQL Database, Azure SQL Data Warehouse, Parallel Data Warehouse  
  
LOG ( float_expression )  
```  
  
## <a name="arguments"></a>Аргументы  
 *float_expression*  
 — [Выражение](../../t-sql/language-elements/expressions-transact-sql.md) типа **float** или типа, который может быть неявно преобразован в **float**.  
  
 *Base*  
 Необязательный целочисленный аргумент, который определяет основу для логарифма.  
  
**Применяется к**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] через[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
  
## <a name="return-types"></a>Типы возвращаемых значений  
 **float**  
  
## <a name="remarks"></a>Замечания  
 По умолчанию **LOG()** Возвращает натуральный логарифм. Начиная с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], основание логарифма можно изменить на другое значение с помощью необязательного *базового* параметра.  
  
 Натуральный логарифм — это логарифм по основанию **e**, где **e** — это иррациональная константа приблизительно 2,718281828.  
  
 Натуральный логарифм экспоненты числа является номером самой: ЖУРНАЛА (EXP (  *n*  )) =  *n* . Экспонента натурального логарифма числа также является числом сам: EXP (ЖУРНАЛА (  *n*  )) =  *n* .  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-calculating-the-logarithm-for-a-number"></a>A. Вычисление логарифма числа.  
 В следующем примере вычисляется `LOG` для указанного **float** выражение.  
  
```  
DECLARE @var float = 10;  
SELECT 'The LOG of the variable is: ' + CONVERT(varchar, LOG(@var));  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
-------------------------------------  
The LOG of the variable is: 2.30259  
  
(1 row(s) affected)  
```  
  
### <a name="b-calculating-the-logarithm-of-the-exponent-of-a-number"></a>Б. Вычисление логарифма экспоненты числа.  
 В следующем примере вычисляется `LOG` экспоненты числа.  
  
```  
SELECT LOG (EXP (10));  
  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
----------------------------------  
10  
(1 row(s) affected)  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] и[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="c-calculating-the-logarithm-for-a-number"></a>В. Вычисление логарифма числа  
 В следующем примере вычисляется `LOG` для указанного **float** выражение.  
  
```  
SELECT LOG(10);  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `----------------`  
  
 `2.30`  
  
### <a name="d-calculating-the-logarithm-of-the-exponent-of-a-number"></a>Г. Вычисление логарифма от экспоненты числа  
 В следующем примере вычисляется `LOG` экспоненты числа.  
  
```  
SELECT LOG(EXP (10));  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
---------  
10.00
```  
  
## <a name="see-also"></a>См. также:  
 [Математические функции &#40; Transact-SQL &#41;](../../t-sql/functions/mathematical-functions-transact-sql.md)   
 [EXP &#40; Transact-SQL &#41;](../../t-sql/functions/exp-transact-sql.md)   
 [LOG10 &#40; Transact-SQL &#41;](../../t-sql/functions/log10-transact-sql.md)  
  
  


