---
title: '|| (логическое ИЛИ) (выражение служб SSIS) | Документы Майкрософт'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- OR operator
- logical OR (||)
- '|| (logical OR)'
ms.assetid: a3c07c09-f121-4187-9617-b01adcf843c4
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 84dfcd895224c63b99e7d97bbe0220ad6f1c3e40
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/26/2020
ms.locfileid: "85428351"
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
  
## <a name="remarks"></a>Remarks  
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
  
## <a name="see-also"></a>См. также:  
 [&#124; (битовое включающее ИЛИ) (выражение служб SSIS)](bitwise-inclusive-or-ssis-expression.md)   
 [^ (битовое исключающее ИЛИ) (выражение служб SSIS)](bitwise-exclusive-or-ssis-expression.md)   
 [Очередность и ассоциативность операторов](operator-precedence-and-associativity.md)   
 [Операторы (выражение служб SSIS)](operators-ssis-expression.md)  
  
  
