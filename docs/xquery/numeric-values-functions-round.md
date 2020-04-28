---
title: Функция Round (XQuery) | Документация Майкрософт
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- fn:round function
- round function [XQuery]
ms.assetid: 320b572f-bd5b-4055-95a6-dec5718c0041
author: rothja
ms.author: jroth
ms.openlocfilehash: 1927d6e483683699196cfc7e87928f27bf23446a
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "67946544"
---
# <a name="numeric-values-functions---round"></a>Функции с числовыми значениями — round
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Возвращает ближайшее к аргументу целое значение. Если таких значений несколько, то возвращается набольшее из них. Пример:  
  
 Если аргумент равен 2,5, функция **Round ()** возвращает значение 3.  
  
 Если аргумент равен 2,4999, функция **Round ()** возвращает значение 2.  
  
 Если аргумент имеет значение-2,5, функция **Round ()** возвращает значение-2.  
  
 Если аргумент является пустой последовательностью, функция **Round ()** возвращает пустую последовательность.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
fn:round ( $arg as numeric?) as numeric?  
```  
  
## <a name="arguments"></a>Аргументы  
 *$arg*  
 Число, к которому применяется функция.  
  
## <a name="remarks"></a>Remarks  
 Если тип *$arg* является одним из трех числовых базовых типов, **xs: float**, **xs: double**или **xs: decimal**, возвращаемый тип совпадает с типом *$arg* . Если тип *$arg* является типом, производным от одного из числовых типов, то возвращаемым типом является базовый числовой тип.  
  
 Если в качестве входных данных для функций **fn: Floor**, **fn: Ceiling**или **fn: Round** задано значение **xdt: untypedAtomic**, нетипизированные данные, то неявно приводится к типу **xs: Double**.  
  
 Использование любого другого типа вызовет статическую ошибку.  
  
## <a name="examples"></a>Примеры  
 В этом разделе приведены примеры запросов XQuery к экземплярам XML, хранящимся в различных столбцах типа **XML** в базе данных AdventureWorks.  
  
 Вы можете использовать рабочий пример в [функции CEILING (XQuery)](../xquery/numeric-values-functions-ceiling.md) для функции **Round ()** XQuery. Все, что нужно сделать, — заменить функцию **ceiling ()** в запросе функцией **Round ()** .  
  
## <a name="implementation-limitations"></a>Ограничения реализации  
 Существуют следующие ограничения:  
  
-   Функция **Round ()** сопоставляет целочисленные значения с типом xs: Decimal.  
  
-   Функция **Round ()** для значений xs: Double и xs: float в диапазоне от-0,5 E0 до-0e0 сопоставлена с 0e0 вместо-0e0.  
  
## <a name="see-also"></a>См. также:  
 [Функция Floor &#40;XQuery&#41;](../xquery/numeric-values-functions-floor.md)   
 [Функция CEILING &#40;XQuery&#41;](../xquery/numeric-values-functions-ceiling.md)  
  
  
