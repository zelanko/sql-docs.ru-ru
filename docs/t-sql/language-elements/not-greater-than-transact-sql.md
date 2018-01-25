---
title: "!&gt; (Не больше чем) (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/13/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- Azure SQL Database
- SQL Server (starting with 2008)
f1_keywords:
- Not Greater
- Greater
- '!>_TSQL'
- '!>'
- Not Greater Than
dev_langs: TSQL
helpviewer_keywords:
- '!> (not greater than)'
- not greater than operator (!>)
ms.assetid: 71a413ed-64f1-4ab9-9c52-c5959a77d00f
caps.latest.revision: "27"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 4879f8ed9fe2a0ac66f04ec5de6692de96f0d388
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
---
# <a name="gt-not-greater-than-transact-sql"></a>!&gt; (Не больше) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Сравнивает два выражения (оператор сравнения). При сравнении ненулевых выражений результат будет TRUE, если значение левого операнда не больше значения правого операнда; в противном случае, результат будет FALSE. В отличие от оператора сравнения = (равенство), результат сравнения двух значений NULL с помощью оператора !> не зависит от свойства ANSI_NULLS.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
expression !> expression  
```  
  
## <a name="arguments"></a>Аргументы  
 *expression*  
 Любое допустимое [выражение](../../t-sql/language-elements/expressions-transact-sql.md). Оба выражения должны иметь типы данных, допускающие неявное преобразование. Преобразование зависит от правил [приоритетов типов данных](../../t-sql/data-types/data-type-precedence-transact-sql.md).  
  
## <a name="result-types"></a>Типы результата  
 **Логическое значение**  
  
## <a name="see-also"></a>См. также  
 [Типы данных (Transact-SQL)](../../t-sql/data-types/data-types-transact-sql.md)   
 [Операторы &#40; Transact-SQL &#41;](../../t-sql/language-elements/operators-transact-sql.md)  
  
  
