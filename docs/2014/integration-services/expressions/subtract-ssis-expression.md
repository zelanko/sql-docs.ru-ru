---
title: '- (вычитание) (выражение служб SSIS) | Документы Майкрософт'
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
- '- (subtract)'
- subtract operator (-)
ms.assetid: b48da086-37dd-460a-8a4b-912f52c9b158
caps.latest.revision: 32
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: cbceb06967d0bbfb305bd46673c8bbbcb9e1bfcf
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37324624"
---
# <a name="--subtract-ssis-expression"></a>- (вычитание) (выражение служб SSIS)
  Вычитает второе числовое выражение из первого.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
numeric_expression1 – numeric_expression2  
  
```  
  
## <a name="arguments"></a>Аргументы  
 *numeric_expression1, numeric_expression2*  
 Любое допустимое выражение числовых типов данных. Дополнительные сведения см. в статье [Integration Services Data Types](../data-flow/integration-services-data-types.md).  
  
## <a name="result-types"></a>Типы результата  
 Определяется типом данных двух аргументов. Дополнительные сведения см. в разделе [Integration Services Data Types in Expressions](integration-services-data-types-in-expressions.md).  
  
## <a name="remarks"></a>Примечания  
 Заключите унарное отрицательное выражение в скобки для того, чтобы выражение было вычислено в правильном порядке.  
  
## <a name="remarks"></a>Примечания  
 Если один из операндов равен NULL, то результатом является значение NULL.  
  
## <a name="expression-examples"></a>Примеры выражений  
 Этот пример вычитает числовые литералы.  
  
```  
5 - 6.09  
```  
  
 Этот пример вычитает значение столбца **StandardCost** из значения столбца **ListPrice** .  
  
```  
ListPrice - StandardCost  
```  
  
 Этот пример вычитает вычисленное значение из значения столбца **ListPrice** . Переменная **Discount%** должна быть заключена в квадратные скобки, поскольку имя включает символ %. Дополнительные сведения см. в разделе [Идентификаторы (службы SSIS)](identifiers-ssis.md).  
  
```  
ListPrice - (ListPrice * @[Discount%])  
```  
  
## <a name="see-also"></a>См. также  
 [Приоритет и ассоциативность операторов](operator-precedence-and-associativity.md)   
 [Операторы &#40;выражение служб SSIS&#41;](operators-ssis-expression.md)  
  
  
