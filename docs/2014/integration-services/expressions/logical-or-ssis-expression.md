---
title: '|| (логическое ИЛИ) (выражение служб SSIS) | Документы Майкрософт'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- OR operator
- logical OR (||)
- '|| (logical OR)'
ms.assetid: a3c07c09-f121-4187-9617-b01adcf843c4
caps.latest.revision: 33
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: f69d71354db0c658a644c0cd4068e894b3fb94fe
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37316974"
---
# <a name="-logical-or-ssis-expression"></a>|| (логическое ИЛИ) (выражение служб SSIS)
  Выполняет логическую операцию ИЛИ. Выражение принимает значение TRUE, если одно или оба условия имеют значение TRUE.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
boolean_expression1 || boolean_expression2  
```  
  
## <a name="arguments"></a>Аргументы  
 *boolean_expression1, boolean_expression2*  
 Любое допустимое выражение, результатом которого являются TRUE, FALSE или NULL  
  
## <a name="result-types"></a>Типы результата  
 DT_BOOL  
  
## <a name="remarks"></a>Примечания  
 Следующая таблица демонстрирует результаты выполнения оператора ||:  
  
|Результат|Выражение|Выражение|  
|------------|----------------|----------------|  
|TRUE|TRUE|TRUE|  
|TRUE|TRUE|FALSE|  
|FALSE|FALSE|FALSE|  
|NULL|NULL|NULL|  
|TRUE|NULL|TRUE|  
|NULL|NULL|FALSE|  
  
## <a name="ssis-expression-examples"></a>Примеры выражений служб SSIS  
 В этом примере используются столбцы **StandardCost** и **ListPrice** . Пример возвращает значение TRUE, если значение столбца **StandardCost** меньше 300 или значение столбца **ListPrice** больше 500.  
  
```  
StandardCost < 300 || ListPrice > 500  
```  
  
 Этот пример использует переменные **SPrice** и **LPrice** вместо числовых литералов.  
  
```  
StandardCost < @SPrice || ListPrice > @LPrice  
```  
  
## <a name="see-also"></a>См. также  
 [&#124;&#40;Побитовое включающее или&#41; &#40;выражение служб SSIS&#41;](bitwise-inclusive-or-ssis-expression.md)   
 [^ (битовое исключающее ИЛИ) (выражение служб SSIS)](bitwise-exclusive-or-ssis-expression.md)   
 [Приоритет и ассоциативность операторов](operator-precedence-and-associativity.md)   
 [Операторы &#40;выражение служб SSIS&#41;](operators-ssis-expression.md)  
  
  
