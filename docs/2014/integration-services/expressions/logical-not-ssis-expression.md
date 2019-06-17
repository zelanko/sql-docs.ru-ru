---
title: '! (логическое НЕ) (выражение служб SSIS) | Документы Майкрософт'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- logical Not (!)
- '! (logical Not)'
ms.assetid: d5c4d1e1-7be4-4d25-bcd9-5b6ddb53b3b3
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: bfcd8337105766d91e097d35201d749c86ca840e
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62769040"
---
# <a name="-logical-not-ssis-expression"></a>! (логическое НЕ) (выражение служб SSIS)
  Инвертирует логический операнд.  
  
> [!NOTE]  
>  ! Оператор «!» не может использоваться вместе с другими операторами. Например, нельзя объединить оператор «!» и оператор > в один оператор «!>» .  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
!boolean_expression  
  
```  
  
## <a name="arguments"></a>Аргументы  
 *boolean_expression*  
 Является любое допустимое выражение, результатом которого является логическое значение. Дополнительные сведения см. в разделе [Integration Services Data Types](../data-flow/integration-services-data-types.md).  
  
## <a name="result-types"></a>Типы результата  
 DT_BOOL  
  
## <a name="remarks"></a>Примечания  
 Следующая таблица демонстрирует результаты выполнения «!» операции.  
  
|Исходное логическое выражение|После выполнения оператора «!» оператор|  
|---------------------------------|------------------------------------|  
|TRUE|FALSE|  
|NULL|NULL|  
|FALSE|TRUE|  
  
## <a name="expression-examples"></a>Примеры выражений  
 В результате выполнения данного выражения получается значение FALSE, если столбец **Color** имеет значение "red".  
  
```  
!(Color == "red")  
```  
  
 В результате выполнения данного выражения получается значение TRUE, если значение переменной **MonthNumber** совпадает со значением переменной, представляющей номер текущего месяца. Дополнительные сведения см. в разделе [MONTH (выражение служб SSIS)](month-ssis-expression.md) and [GETDATE (выражение служб SSIS)](getdate-ssis-expression.md).  
  
```  
!(@MonthNumber != MONTH(GETDATE())  
```  
  
## <a name="see-also"></a>См. также  
 [Очередность и ассоциативность операторов](operator-precedence-and-associativity.md)   
 [Операторы (выражение служб SSIS)](operators-ssis-expression.md)  
  
  
