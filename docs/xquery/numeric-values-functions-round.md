---
title: Round-функция (XQuery) | Документация Майкрософт
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
manager: craigg
ms.openlocfilehash: 8c0b5847cb5d4b4d6643edceadbd4d95cec5f152
ms.sourcegitcommit: 0f7cf9b7ab23df15624d27c129ab3a539e8b6457
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2018
ms.locfileid: "51292740"
---
# <a name="numeric-values-functions---round"></a>Функции с числовыми значениями — round
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Возвращает ближайшее к аргументу целое значение. Если таких значений несколько, то возвращается набольшее из них. Пример:  
  
 Если аргумент равен 2,5, **round()** возвращает значение 3.  
  
 Если аргумент является 2.4999, **round()** возвращает 2.  
  
 Если аргумент – 2,5, **round()** возвращает значение -2.  
  
 Если аргумент представляет собой пустую последовательность, **round()** возвращает пустую последовательность.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
fn:round ( $arg as numeric?) as numeric?  
```  
  
## <a name="arguments"></a>Аргументы  
 *$arg*  
 Число, к которому применяется функция.  
  
## <a name="remarks"></a>Примечания  
 Если тип *$arg* является одним из трех базовых числовых типов, **xs: float**, **xs: double**, или **xs: decimal**, тип возвращаемого значения совпадает с *$arg* типа. Если тип *$arg* — тип, который является производным от одного из числовых типов, тип возвращаемого значения будет иметь базовый числовой тип.  
  
 Если входные данные для **fn: FLOOR**, **fn: CEILING**, или **fn: Round** "функции" — **xdt: untypedAtomic**, нетипизированных данных, оно неявно приводится к **xs: double**.  
  
 Использование любого другого типа вызовет статическую ошибку.  
  
## <a name="examples"></a>Примеры  
 В этом разделе приведены примеры запросов XQuery к экземплярам XML, хранящимся в различных **xml** -столбец базы данных AdventureWorks.  
  
 Можно использовать пример в [функция ceiling (XQuery)](../xquery/numeric-values-functions-ceiling.md) для **round()** функции языка XQuery. Все, что необходимо сделать это заменить **ceiling()** функция в запросе с **round()** функции.  
  
## <a name="implementation-limitations"></a>Ограничения реализации  
 Существуют следующие ограничения:  
  
-   **Round()** функция сопоставляет целочисленные значения типу xs: decimal.  
  
-   **Round()** функцию xs: double и xs: float значений от - 0, 5e0 до - 0e0 возвращает значение 0e0 вместо - 0e0.  
  
## <a name="see-also"></a>См. также  
 [Функция FLOOR &#40;XQuery&#41;](../xquery/numeric-values-functions-floor.md)   
 [Функция CEILING &#40;XQuery&#41;](../xquery/numeric-values-functions-ceiling.md)  
  
  
