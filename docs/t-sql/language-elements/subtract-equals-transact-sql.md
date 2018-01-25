---
title: "-= (Назначение вычитания) (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- -=
- -=_TSQL
dev_langs: TSQL
helpviewer_keywords:
- compound operators, -=
- assignment operators, -=
- augmented operators, -=
- -= (subtract equals)
- -= (subtraction assignment)
ms.assetid: 2a2056b5-1dfa-4ea8-8cfc-6331a2f94da9
caps.latest.revision: "11"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: e42283367d3035ce4d7fcaecb4f7c96bcb7fed68
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
---
# <a name="--subtraction-assignment-transact-sql"></a>-= (Назначение вычитания) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Вычитаются два числа, и задается значение для результата операции. Например, если переменная @x равно 35, @x -= 2 принимает исходное значение @x, вычитает 2 и задает @x новое значение (33).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
expression -= expression  
```  
  
## <a name="arguments"></a>Аргументы  
 *expression*  
 Любое допустимое [выражение](../../t-sql/language-elements/expressions-transact-sql.md) какой-либо один из данных типов в числовой категории, кроме **бит** тип данных.  
  
## <a name="result-types"></a>Типы результата  
 Возвращает результат типа данных аргумента с более высоким приоритетом. Дополнительные сведения см. в разделе [Приоритет типов данных (Transact-SQL)](../../t-sql/data-types/data-type-precedence-transact-sql.md).  
  
## <a name="remarks"></a>Remarks  
 Дополнительные сведения см. в разделе [-&#40; Вычитание &#41; &#40; Transact-SQL &#41; ](../../t-sql/language-elements/subtract-transact-sql.md).  
  
## <a name="see-also"></a>См. также  
 [Составные операторы &#40; Transact-SQL &#41;](../../t-sql/language-elements/compound-operators-transact-sql.md)   
 [Выражения &#40; Transact-SQL &#41;](../../t-sql/language-elements/expressions-transact-sql.md)   
 [Операторы &#40; Transact-SQL &#41;](../../t-sql/language-elements/operators-transact-sql.md)  
  
  
