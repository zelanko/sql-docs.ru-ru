---
title: POWER (выражение служб SSIS) | Документы Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- POWER function
ms.assetid: db48ae65-bfa6-4db1-8d3c-d0d4f8a399bc
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 4748de700d229d03058154b5b46e15aa66ba27f7
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47595362"
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
  
## <a name="remarks"></a>Remarks  
 Перед выполнением операции возведения в степень аргументы *numeric_expression* и *power* приводятся к типу DT_R8. Дополнительные сведения см. в статье [Integration Services Data Types](../../integration-services/data-flow/integration-services-data-types.md).  
  
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
  
## <a name="see-also"></a>См. также:  
 [Функции (выражение служб SSIS)](../../integration-services/expressions/functions-ssis-expression.md)  
  
  
