---
title: "Деление (выражение служб SSIS) | Документы Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- / (divide)
- divide operator (/)
ms.assetid: 5bde9223-872d-443e-8a27-57735e1d8f3d
caps.latest.revision: 36
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: bf7ca9400837b33ed016c03408028b0102c7418f
ms.contentlocale: ru-ru
ms.lasthandoff: 08/03/2017

---
# <a name="divide-ssis-expression"></a>Деление (выражение служб SSIS)
  Делит первое числовое выражение на второе.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
dividend / divisor  
  
```  
  
## <a name="arguments"></a>Аргументы  
 *dividend*  
 Делимое числовое выражение. *dividend* может быть любым допустимым числовым выражением. Дополнительные сведения см. в статье [Integration Services Data Types](../../integration-services/data-flow/integration-services-data-types.md).  
  
 *divisor*  
 Числовое выражение, на которое делится делимое. *divisor* может быть любым допустимым числовым выражением, отличным от нуля.  
  
## <a name="result-types"></a>Типы результата  
 Определяются типами данных обоих аргументов. Дополнительные сведения см. в разделе [Integration Services Data Types in Expressions](../../integration-services/expressions/integration-services-data-types-in-expressions.md).  
  
## <a name="remarks"></a>Замечания  
 Если один из операндов равен NULL, то результатом является значение NULL.  
  
 Деление на ноль недопустимо. В зависимости от того, как вычисляется подвыражение *divisor* , возникает одна из следующих ошибок:  
  
-   Если подвыражение *divisor* , результатом которого является ноль, является константой, то ошибка появляется во время разработки, и в результате файл не проходит проверку правильности.  
  
-   Если подвыражение *divisor* , результатом которого является ноль, содержит переменные, но не содержит входных столбцов, то компонент, которому принадлежит выражение, прерывает предварительную проверку правильности, которая производится перед выполнением пакета.  
  
-   Если вложенное выражение *divisor* , результатом которого является ноль, содержит входные столбцы, то во время выполнения возникает ошибка, которая обрабатывается в соответствии с правилами потока ошибок компонента потока данных.  
  
## <a name="expression-examples"></a>Примеры выражений  
 Этот пример делит два числовых литерала.  
  
```  
25 / 5  
```  
  
 Этот пример делит значения в столбце **ListPrice** на значения в столбце **StandardCost** .  
  
```  
ListPrice / StandardCost  
```  
  
## <a name="see-also"></a>См. также  
 [Приоритет и ассоциативность операторов](../../integration-services/expressions/operator-precedence-and-associativity.md)   
 [Операторы &#40; Выражение служб SSIS &#41;](../../integration-services/expressions/operators-ssis-expression.md)  
  
  
