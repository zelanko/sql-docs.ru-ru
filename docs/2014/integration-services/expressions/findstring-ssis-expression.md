---
title: FINDSTRING (выражение служб SSIS) | Документы Майкрософт
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
- FINDSTRING function
ms.assetid: c83cb1b1-3c52-4496-b518-4c9253b9336d
caps.latest.revision: 41
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 82b5df9c4ee132a313b822da4aadc0bc5f90fd75
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37272833"
---
# <a name="findstring-ssis-expression"></a>FINDSTRING (выражение служб SSIS)
  Возвращает местоположение заданного вхождения строки в символьном выражении. Возвращаемый результат является относительным положением вхождения в выражении, нумерация символов которого начинается с единицы. Значением параметра строки должно быть символьное выражение, а значением параметра вхождения должно быть целое число. Если строка не найдена, возвращается значение 0. Если строка встречается меньшее количество раз, чем определено аргументом, то возвращается значение 0.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
FINDSTRING(character_expression, searchstring, occurrence)  
```  
  
## <a name="arguments"></a>Аргументы  
 *character_expression*  
 Символьная строка, в которой производится поиск.  
  
 *searchstring*  
 Искомая символьная строка.  
  
 *occurrence*  
 Целое число со знаком или без него, указывающее, какое по порядку вхождение *searchstring* следует искать.  
  
## <a name="result-types"></a>Типы результата  
 DT_I4  
  
## <a name="remarks"></a>Примечания  
 Функция FINDSTRING работает только с типом данных DT_WSTR.  Аргументы*character_expression* и *searchstring* , которые являются строковыми литералами или столбцами данных, содержащими данные типа DT_STR, неявно приводятся к типу данных DT_WSTR до того, как функция FINDSTRING выполнит свою операцию. Прочие типы данных должны быть явно приведены к типу данных DT_WSTR. Дополнительные сведения см. в разделах [Типы данных служб Integration Services](../data-flow/integration-services-data-types.md) и [Приведение (выражение служб SSIS)](cast-ssis-expression.md).  
  
 Функция FINDSTRING возвращает NULL, если или *character_expression*, или *searchstring* равен NULL.  
  
 Для получения относительного положения первого вхождения в аргументе *occurrence* следует использовать 1, для второго вхождения — 2 и т. д.  
  
 Аргумент *occurrence* должен быть целым числом, значение которого больше 0.  
  
## <a name="expression-examples"></a>Примеры выражений  
 В данном примере используется строковый литерал. Он возвращает значение 11.  
  
```  
FINDSTRING("New York, NY, NY", "NY", 1)   
```  
  
 В данном примере используется строковый литерал. Так как строка «NY» встретилась меньше двух раз, то возвращается значение 0.  
  
```  
FINDSTRING("New York, NY, NY", "NY", 3)   
```  
  
 В этом примере используется столбец **Name** . Он возвращает местоположение значения n в столбце **Name** . Возвращаемый результат зависит от значения в столбце **Name**. Если **Name** содержит Anderson, функция возвращает значение 8.  
  
```  
FINDSTRING(Name,"n", 2)   
```  
  
 В этом примере используются столбцы **Name** и **Size** . Он возвращает местоположение самого левого символа значения **Size** в столбце **Name** . Возвращаемый результат зависит от значений столбца. Если **Name** содержит Mountain,500Red,42 и **Size** содержит 42, возвращаемый результат равен 17.  
  
```  
FINDSTRING(Name,Size,1)   
```  
  
## <a name="see-also"></a>См. также  
 [ЗАМЕНИТЕ &#40;выражение служб SSIS&#41;](replace-ssis-expression.md)   
 [Функции &#40;выражение служб SSIS&#41;](functions-ssis-expression.md)  
  
  
