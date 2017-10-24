---
title: "+= (Равно со сложением) (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- +=
- +=_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- += (add equals)
- compound operators, +=
ms.assetid: 9ea52519-80d1-473f-b988-0572f0e2c92f
caps.latest.revision: 17
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 0d07ab123822db8f381af6fcc4f1707529bed359
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="-add-equals-transact-sql"></a>+= (РАВНО со сложением) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Складывает два числа и присваивает значению результат этой операции. Например, если переменная @x равно 35, @x += 2 принимает исходное значение @x, добавить 2 и задает @x новое значение (37).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
expression += expression  
```  
  
## <a name="arguments"></a>Аргументы  
 *expression*  
 Любое допустимое [выражение](../../t-sql/language-elements/expressions-transact-sql.md) любого типа данных числовой категории, кроме **бит** тип данных.  
  
## <a name="result-types"></a>Типы результата  
 Возвращает результат типа данных аргумента с более высоким приоритетом. Дополнительные сведения см. в разделе [Приоритет типов данных (Transact-SQL)](../../t-sql/data-types/data-type-precedence-transact-sql.md).  
  
## <a name="remarks"></a>Замечания  
 Дополнительные сведения см. в разделе [+ &#40; Добавить &#41; &#40; Transact-SQL &#41; ](../../t-sql/language-elements/add-transact-sql.md).  
  
## <a name="see-also"></a>См. также:  
 [Составные операторы &#40; Transact-SQL &#41;](../../t-sql/language-elements/compound-operators-transact-sql.md)   
 [Выражения &#40; Transact-SQL &#41;](../../t-sql/language-elements/expressions-transact-sql.md)   
 [Операторы &#40; Transact-SQL &#41;](../../t-sql/language-elements/operators-transact-sql.md)   
 [+= &#40; Объединение строк &#41; &#40; Transact-SQL &#41;](../../t-sql/language-elements/string-concatenation-equal-transact-sql.md)  
  
  

