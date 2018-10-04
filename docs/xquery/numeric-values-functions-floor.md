---
title: FLOOR, функция (XQuery) | Документация Майкрософт
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- floor function [XQuery]
- fn:floor function
ms.assetid: 4ace57dd-b66e-4b60-a2b9-a1b0f1a0831d
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 5f06ae6337436ac599d6d804e9481dfe59c57f0a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47766692"
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
  
## <a name="remarks"></a>Примечания  
 Если тип *$arg* является одним из трех базовых числовых типов, **xs: float**, **xs: double**, или **xs: decimal**, тип возвращаемого значения совпадает с *$arg* типа. Если тип *$arg* — тип, который является производным от одного из числовых типов, тип возвращаемого значения будет иметь базовый числовой тип.  
  
 Если входные данные функций fn: FLOOR, fn: CEILING или fn: Round **xdt: untypedAtomic**, нетипизированных данных, оно неявно приводится к **xs: double**. Использование любого другого типа вызовет статическую ошибку.  
  
## <a name="examples"></a>Примеры  
 В этом разделе приведены примеры запросов XQuery к экземплярам XML, которые хранятся в различных **xml** столбцов типа в базе данных AdventureWorks.  
  
 Можно использовать пример в [функция ceiling (XQuery)](../xquery/numeric-values-functions-ceiling.md) для **floor()** функции языка XQuery. Все, что необходимо сделать это заменить **ceiling()** функция в запросе с **floor()** функции.  
  
## <a name="implementation-limitations"></a>Ограничения реализации  
 Существуют следующие ограничения:  
  
-   **Floor()** функция сопоставляет все целочисленные значения типу xs: decimal.  
  
## <a name="see-also"></a>См. также  
 [Функция CEILING &#40;XQuery&#41;](../xquery/numeric-values-functions-ceiling.md)   
 [Функция Round &#40;XQuery&#41;](../xquery/numeric-values-functions-round.md)   
 [Функции XQuery для типа данных XML](../xquery/xquery-functions-against-the-xml-data-type.md)  
  
  
