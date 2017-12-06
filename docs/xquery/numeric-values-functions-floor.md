---
title: "FLOOR, функция (XQuery) | Документы Microsoft"
ms.custom: 
ms.date: 03/09/2017
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: 
ms.component: xquery
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to: SQL Server
dev_langs: XML
helpviewer_keywords:
- floor function [XQuery]
- fn:floor function
ms.assetid: 4ace57dd-b66e-4b60-a2b9-a1b0f1a0831d
caps.latest.revision: "27"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 41dee329166c3c791a5caf0d5a31393278a96d5d
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/05/2017
---
# <a name="numeric-values-functions---floor"></a>Числовые значения функции — floor
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Возвращает самое большое число без дробной части, которое не превышает значения аргумента. Если аргумент представляет собой пустую последовательность, то возвращается пустая последовательность.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
fn:floor ($arg as numeric?) as numeric?  
```  
  
## <a name="arguments"></a>Аргументы  
 *$arg*  
 Число, к которому применяется функция.  
  
## <a name="remarks"></a>Замечания  
 Если тип *$arg* является одним из трех базовых числовых типов, **xs: float**, **xs: double**, или **xs: decimal**, тип возвращаемого значения совпадает с *$arg* типа. Если тип *$arg* — тип, который является производным от одного из числовых типов, тип возвращаемого значения будет иметь базовый числовой тип.  
  
 Если входные данные функций fn: FLOOR, fn: CEILING или fn: Round **xdt: untypedAtomic**, нетипизированных данных, оно неявно приводится к **xs: double**. Использование любого другого типа вызовет статическую ошибку.  
  
## <a name="examples"></a>Примеры  
 В этом разделе приведены примеры запросов XQuery к экземплярам XML, которые хранятся в различных **xml** столбцов типа в базе данных AdventureWorks.  
  
 Можно использовать пример в [функция ceiling (XQuery)](../xquery/numeric-values-functions-ceiling.md) для **floor()** функции языка XQuery. Все, нужно сделать, — заменить **ceiling()** функции в запрос с **floor()** функции.  
  
## <a name="implementation-limitations"></a>Ограничения реализации  
 Существуют следующие ограничения:  
  
-   **Floor()** функция сопоставляет все целочисленные значения типу xs: decimal.  
  
## <a name="see-also"></a>См. также:  
 [Функция CEILING &#40; XQuery &#41;](../xquery/numeric-values-functions-ceiling.md)   
 [Round, функция &#40; XQuery &#41;](../xquery/numeric-values-functions-round.md)   
 [Функции XQuery для типа данных XML](../xquery/xquery-functions-against-the-xml-data-type.md)  
  
  
