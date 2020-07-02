---
title: Функция Round (XQuery) | Документация Майкрософт
description: Сведения о функции XQuery Round (), возвращающей число, не имеющее дробной части, ближайшей к заданному аргументу.
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
ms.openlocfilehash: 7433ab9f3bd6bcadda324db1a5907f4d83040575
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85720010"
---
# <a name="numeric-values-functions---round"></a>Функции с числовыми значениями — round
[!INCLUDE [SQL Server Azure SQL Database ](../includes/applies-to-version/sqlserver.md)]

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
  
## <a name="remarks"></a>Примечания  
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
  
## <a name="see-also"></a>См. также  
 [Функция Floor &#40;XQuery&#41;](../xquery/numeric-values-functions-floor.md)   
 [Функция CEILING &#40;XQuery&#41;](../xquery/numeric-values-functions-ceiling.md)  
  
  
