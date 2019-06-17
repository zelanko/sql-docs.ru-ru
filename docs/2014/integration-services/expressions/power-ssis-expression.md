---
title: POWER (выражение служб SSIS) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- POWER function
ms.assetid: db48ae65-bfa6-4db1-8d3c-d0d4f8a399bc
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 3d25801b7cc7f6282ebc8cf7b1ce7839159312dc
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62897419"
---
# <a name="power-ssis-expression"></a>POWER (выражение служб SSIS)
  Возвращает результат возведения числового выражения в степень. Показатель степени должен быть целым числом.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
POWER(numeric_expression,power)  
```  
  
## <a name="arguments"></a>Аргументы  
 *numeric_expression*  
 Допустимое числовое выражение.  
  
 *power*  
 Допустимое числовое выражение.  
  
## <a name="result-types"></a>Типы результата  
 DT_R8  
  
## <a name="remarks"></a>Примечания  
 Перед выполнением операции возведения в степень аргументы *numeric_expression* и *power* приводятся к типу DT_R8. Дополнительные сведения см. в разделе [Integration Services Data Types](../data-flow/integration-services-data-types.md).  
  
 В случае если результатом *numeric_expression* является ноль, а *power* меньше ноля, средство оценки выражений возвращает ошибку, а выходному параметру присваивается значение NULL.  
  
 В случае если результатом *numeric_expression* или *power* является неопределенное значение, выходному параметру присваивается значение NULL.  
  
 Аргумент *power* может быть дробным. Например, показатель степени может иметь значение 0,5.  
  
## <a name="expression-examples"></a>Примеры выражений  
 В этом примере используется числовой литерал. Функция возводит число 4 в степень 3 и возвращает 64.  
  
```  
POWER(4,3)  
```  
  
 Данный пример использует столбец со значением параметра **Length** и переменную **DimensionCount** . Если параметр **Length** имеет значение 8, а параметр **DimensionCount** значение 2, функция возвращает 64.  
  
```  
POWER(Length, @DimensionCount)   
```  
  
## <a name="see-also"></a>См. также  
 [Функции (выражение служб SSIS)](functions-ssis-expression.md)  
  
  
