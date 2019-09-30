---
title: + (объединение) (выражение служб SSIS) | Документы Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- concatenation [Integration Services]
- + (concatenate operator)
- concatenate operator (+)
ms.assetid: 0fed6334-7a4f-42dc-a611-191fcaa0e443
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 366e307220d08192df04b95201758751cce90112
ms.sourcegitcommit: e8af8cfc0bb51f62a4f0fa794c784f1aed006c71
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/26/2019
ms.locfileid: "71297668"
---
# <a name="-concatenate-ssis-expression"></a>+ (объединение) (выражение служб SSIS)

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


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
  
## <a name="remarks"></a>Remarks  
 Выражение может использовать любой из типов данных — DT_STR, DT_WSTR или оба сразу.  
  
 Объединение типов данных DT_STR и DT_WSTR возвращает результат в формате DT_WSTR. Длина строки — это сумма длин первоначальных строк в символах.  
  
 Могут быть сцеплены только данные со строковым типом данных (DT_STR и DT_WSTR) или данные большого двоичного объекта (BLOB) и типы данных DT_TEXT, DT_NTEXT и DT_IMAGE. Другие типы данных перед объединением должны быть преобразованы в один из этих типов данных. Дополнительные сведения о допустимых приведениях типов данных см. в разделе [Приведение (выражение служб SSIS)](../../integration-services/expressions/cast-ssis-expression.md).  
  
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
  
## <a name="see-also"></a>См. также:  
 [Очередность и ассоциативность операторов](../../integration-services/expressions/operator-precedence-and-associativity.md)   
 [Операторы (выражение служб SSIS)](../../integration-services/expressions/operators-ssis-expression.md)  
  
  
