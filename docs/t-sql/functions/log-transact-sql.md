---
title: "LOG (Transact-SQL) | Документы Майкрософт"
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
- LOG
- LOG_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- float expressions
- logarithm of expression
- LOG function
ms.assetid: f7c39511-cd84-4362-93ba-0d93655217ee
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: ab2d021e583c3f4bec009e7959ea4fccfea8c5a3
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="log-transact-sql"></a>LOG (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Возвращает натуральный логарифм указанного выражения типа **float** в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
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
 [Выражение](../../t-sql/language-elements/expressions-transact-sql.md) типа **float** или типа, который может быть неявно преобразован в тип **float**.  
  
 *base*  
 Необязательный целочисленный аргумент, который определяет основу для логарифма.  
  
**Применимо к**: с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
  
## <a name="return-types"></a>Типы возвращаемых значений  
 **float**  
  
## <a name="remarks"></a>Remarks  
 По умолчанию **LOG()** возвращает натуральный логарифм. Начиная с версии [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], с помощью необязательного параметра *base* основание логарифма можно изменить на другое значение.  
  
 Натуральный логарифм — это логарифм по основанию **e**, где **e** — это иррациональная константа, которая приблизительно равна 2,718281828.  
  
 Натуральный логарифм от экспоненты числа равен самому этому числу: LOG( EXP( *n* ) ) = *n*. Экспонента натурального логарифма числа равна самому этому числу: EXP( LOG( *n* ) ) = *n*.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-calculating-the-logarithm-for-a-number"></a>A. Вычисление логарифма числа.  
 В приведенном ниже примере вычисляется `LOG` для указанного выражения типа **float**.  
  
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
 В приведенном ниже примере вычисляется `LOG` для экспоненты числа.  
  
```  
SELECT LOG (EXP (10));  
  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
----------------------------------  
10  
(1 row(s) affected)  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] и [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="c-calculating-the-logarithm-for-a-number"></a>В. Вычисление логарифма числа  
 В приведенном ниже примере вычисляется `LOG` для указанного выражения типа **float**.  
  
```  
SELECT LOG(10);  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
 ----------------`  
  
 2.30
 ```  
  
## <a name="see-also"></a>См. также:  
 [Математические функции (Transact-SQL)](../../t-sql/functions/mathematical-functions-transact-sql.md)   
 [EXP (Transact-SQL)](../../t-sql/functions/exp-transact-sql.md)   
 [LOG10 (Transact-SQL)](../../t-sql/functions/log10-transact-sql.md)  
  
  

