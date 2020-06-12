---
title: Функция floor (XQuery) | Документация Майкрософт
description: Сведения о функции floor () XQuery, возвращающей максимальное число без дробной части, которое не превышает значение аргумента.
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- floor function [XQuery]
- fn:floor function
ms.assetid: 4ace57dd-b66e-4b60-a2b9-a1b0f1a0831d
author: rothja
ms.author: jroth
ms.openlocfilehash: 15bdca46fc62832ecd97932b1b71f999f1f80324
ms.sourcegitcommit: 2f166e139f637d6edfb5731510d632a13205eb25
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/08/2020
ms.locfileid: "84524526"
---
# <a name="numeric-values-functions---floor"></a>Функции с числовыми значениями — floor
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Возвращает самое большое число без дробной части, которое не превышает значения аргумента. Если аргумент представляет собой пустую последовательность, то возвращается пустая последовательность.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
fn:floor ($arg as numeric?) as numeric?  
```  
  
## <a name="arguments"></a>Аргументы  
 *$arg*  
 Число, к которому применяется функция.  
  
## <a name="remarks"></a>Комментарии  
 Если тип *$arg* является одним из трех числовых базовых типов, **xs: float**, **xs: double**или **xs: decimal**, возвращаемый тип совпадает с типом *$arg* . Если тип *$arg* является типом, производным от одного из числовых типов, то возвращаемым типом является базовый числовой тип.  
  
 Если в качестве входных данных для функций Fn: Floor, fn: Ceiling или Fn: Round задано значение **xdt: untypedAtomic**, нетипизированные данные, то неявно приводится к типу **xs: Double**. Использование любого другого типа вызовет статическую ошибку.  
  
## <a name="examples"></a>Примеры  
 В этом разделе приведены примеры запросов XQuery к экземплярам XML, хранящимся в различных столбцах типа **XML** в образце базы данных AdventureWorks.  
  
 Вы можете использовать рабочий пример в [функции CEILING (XQuery)](../xquery/numeric-values-functions-ceiling.md) для функции **floor ()** языка XQuery. Все, что нужно сделать, — заменить функцию **ceiling ()** в запросе функцией **floor ()** .  
  
## <a name="implementation-limitations"></a>Ограничения реализации  
 Существуют следующие ограничения:  
  
-   Функция **floor ()** сопоставляет все целочисленные значения с типом xs: Decimal.  
  
## <a name="see-also"></a>См. также:  
 [Функция CEILING &#40;XQuery&#41;](../xquery/numeric-values-functions-ceiling.md)   
 [Функция Round &#40;XQuery&#41;](../xquery/numeric-values-functions-round.md)   
 [Функции XQuery для типа данных xml](../xquery/xquery-functions-against-the-xml-data-type.md)  
  
  
