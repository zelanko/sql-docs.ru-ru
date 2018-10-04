---
title: + (объединение) (выражение служб SSIS) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
helpviewer_keywords:
- concatenation [Integration Services]
- + (concatenate operator)
- concatenate operator (+)
ms.assetid: 0fed6334-7a4f-42dc-a611-191fcaa0e443
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 809586f89288a930a672e2f6daa45fafe7901ec6
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48146244"
---
# <a name="-concatenate-ssis-expression"></a>+ (объединение) (выражение служб SSIS)
  Сцепляют два выражения в одно.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
character_expression1 + character_expression2  
  
```  
  
## <a name="arguments"></a>Аргументы  
 *expression1, expression2*  
 Допустимые типы данных выражения: DT_STR, DT_WSTR, DT_TEXT, DT_NTEXT, или DT_IMAGE.  
  
## <a name="result-types"></a>Типы результата  
 DT_WSTR  
  
## <a name="remarks"></a>Примечания  
 Выражение может использовать любой из типов данных — DT_STR, DT_WSTR или оба сразу.  
  
 Объединение типов данных DT_STR и DT_WSTR возвращает результат в формате DT_WSTR. Длина строки — это сумма длин первоначальных строк в символах.  
  
 Могут быть сцеплены только данные со строковым типом данных (DT_STR и DT_WSTR) или данные большого двоичного объекта (BLOB) и типы данных DT_TEXT, DT_NTEXT и DT_IMAGE. Другие типы данных перед объединением должны быть преобразованы в один из этих типов данных. Дополнительные сведения о допустимых приведениях типов данных см. в разделе [Приведение (выражение служб SSIS)](cast-ssis-expression.md).  
  
 Оба выражения должны состоять из одного типа данных, или должна быть возможность преобразовать тип данных одного выражения в тип данных другого выражения. Например, если строка «Дата заказа: » и столбец **OrderDate** объединены, значения в **OrderDate** будут преобразованы в строковый тип данных. Для объединения двух числовых значений оба числовых значения должны быть приведены к строковому типу данных.  
  
 Объединение может использовать только один тип данных BLOB: DT_TEXT, DT_NTEXT или DT_IMAGE.  
  
 Если любой из элементов равен NULL, результат будет NULL.  
  
 Строковые литералы должны заключаться в кавычки.  
  
## <a name="expression-examples"></a>Примеры выражений  
 Пример объединяет значения в столбцах **FirstName** и **LastName** и вставляет символ пробела между ними.  
  
```  
FirstName + ' ' + LastName  
```  
  
 Этот пример сцепляет переменные **ZIPCode** и **ZIPCode+4**. Обе переменные имеют строковый тип данных. **ZIPCode+4** должна быть заключена в квадратные скобки, поскольку имя переменной включает символ "+".  
  
```  
@ZIPCcode + "-" + @[ZipCode+4]  
```  
  
## <a name="see-also"></a>См. также  
 [Приоритет и ассоциативность операторов](operator-precedence-and-associativity.md)   
 [Операторы &#40;выражение служб SSIS&#41;](operators-ssis-expression.md)  
  
  
