---
title: "Математические функции (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 07/06/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- calculations [SQL Server]
- mathematical functions [SQL Server]
- functions [SQL Server], mathematical
ms.assetid: 46495a2e-81d0-4677-9d72-9db083cd1023
caps.latest.revision: 24
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 5ec4a6767acab606d6459b439683a88a0cae1caf
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="mathematical-functions-transact-sql"></a>Математические функции (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Следующие скалярные функции выполняют вычисление, обычно на основании входных значений, заданных в качестве аргументов, и возвращают числовые значения:  
  
||||  
|-|-|-|  
|[ABS](../../t-sql/functions/abs-transact-sql.md)|[ГРАДУСОВ](../../t-sql/functions/degrees-transact-sql.md)|[ФУНКЦИЯ RAND](../../t-sql/functions/rand-transact-sql.md)|  
|[ACOS](../../t-sql/functions/acos-transact-sql.md)|[EXP](../../t-sql/functions/exp-transact-sql.md)|[ОКРУГЛЕНИЕ](../../t-sql/functions/round-transact-sql.md)|  
|[ASIN](../../t-sql/functions/asin-transact-sql.md)|[ФУНКЦИЯ FLOOR](../../t-sql/functions/floor-transact-sql.md)|[ВХОД](../../t-sql/functions/sign-transact-sql.md)|  
|[ATAN](../../t-sql/functions/atan-transact-sql.md)|[ЖУРНАЛ](../../t-sql/functions/log-transact-sql.md)|[SIN](../../t-sql/functions/sin-transact-sql.md)|  
|[ATN2](../../t-sql/functions/atn2-transact-sql.md)|[LOG10](../../t-sql/functions/log10-transact-sql.md)|[ФУНКЦИЯ SQRT](../../t-sql/functions/sqrt-transact-sql.md)|  
|[ФУНКЦИЯ CEILING](../../t-sql/functions/ceiling-transact-sql.md)|[PI](../../t-sql/functions/pi-transact-sql.md)|[КВАДРАТ](../../t-sql/functions/square-transact-sql.md)|  
|[COS](../../t-sql/functions/cos-transact-sql.md)|[ПИТАНИЯ](../../t-sql/functions/power-transact-sql.md)|[TAN](../../t-sql/functions/tan-transact-sql.md)|  
|[COT](../../t-sql/functions/cot-transact-sql.md)|[RADIANS](../../t-sql/functions/radians-transact-sql.md)||  
  
> [!NOTE]  
>  Арифметические функции, такие как ABS, CEILING, DEGREES, FLOOR, POWER, RADIANS и SIGN, возвращают значение того же типа, что и входное значение. Тригонометрические и другие функции, включая EXP, LOG, LOG10, КВАДРАТНЫЕ и SQRT, привести свои входные значения **float** и возвращают **float** значение.  
  
 Все математические функции, кроме RAND, являются детерминированными. Это значит, что они возвращают одни и те же результаты каждый раз, когда вызываются с одними и теми же входными значениями. Функция RAND является детерминированной только в том случае, если задан параметр начального значения. Дополнительные сведения о детерминизме функций см. в разделе [функций](../../relational-databases/user-defined-functions/deterministic-and-nondeterministic-functions.md).  
  
## <a name="see-also"></a>См. также:  
  [Арифметические операторы &#40; Transact-SQL &#41;](../../t-sql/language-elements/arithmetic-operators-transact-sql.md)  
  [Встроенные функции (Transact-SQL)](~/t-sql/functions/functions.md)  
  
  

