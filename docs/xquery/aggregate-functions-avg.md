---
title: "Функция AVG (XQuery) | Документы Microsoft"
ms.custom: 
ms.date: 08/09/2016
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: 
ms.component: xquery
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- fn:avg function
- avg function [XQuery]
ms.assetid: 0cc60267-3c56-4a88-8ad7-bb07f0255d56
caps.latest.revision: 
author: rothja
ms.author: jroth
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ee1d24bc4b28b7a041baa42ac829424e5daa6f8b
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/09/2018
---
# <a name="aggregate-functions---avg"></a>Агрегатные функции — среднее
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает среднее значение для последовательности чисел.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
fn:avg($arg as xdt:anyAtomicType*) as xdt:anyAtomicType?  
```  
  
## <a name="arguments"></a>Аргументы  
 *$arg*  
 Последовательность атомарных значений, для которых вычисляется среднее значение.  
  
## <a name="remarks"></a>Remarks  
 Все типы атомарных значений, передаваемые **avg()** должны быть подтипами только одного из трех встроенных базовых числовых типов или типа xdt: untypedAtomic. Они не могут быть смешанными. Значения типа xdt:untypedAtomic приводятся к типу xs:double. Результат **avg()** Получает базовый тип переданных типов, например xs: double в случае использования xdt: untypedAtomic.  
  
 Если входное значение статически пусто, подразумевается пустое значение и возвращается статическая ошибка.  
  
 **Avg()** функция возвращает среднее значение чисел вычисляется. Например:  
  
 **SUM (** *$arg* **) число div (** *$arg* **)**  
  
 Если *$arg* представляет собой пустую последовательность, возвращается пустая последовательность.  
  
 Если значение xdt: untypedAtomic не может быть приведен к типу xs: double, это значение игнорируется во входной последовательности *$arg*.  
  
 Во всех прочих случаях функция возвращает статическую ошибку.  
  
## <a name="examples"></a>Примеры  
 В этом разделе приведены примеры запросов XQuery к экземплярам XML, которые хранятся в различных **xml** столбцов типа в базе данных AdventureWorks.  
  
### <a name="a-using-the-avg-xquery-function-to-find-work-center-locations-in-the-manufacturing-process-in-which-labor-hours-are-greater-than-the-average-for-all-work-center-locations"></a>A. Использование функции XQuery avg() для поиска на производстве расположения цехов, время работы в которых превышает среднее значение для всех цехов.  
 Можно переписать запрос, приведенный в [функция min (XQuery)](../xquery/aggregate-functions-min.md) использовать **avg()** функции.  
  
## <a name="implementation-limitations"></a>Ограничения реализации  
 Существуют следующие ограничения:  
  
-   **Avg()** функция сопоставляет все целочисленные значения типу xs: decimal.  
  
-   **Avg()** функция значения типа xs: Duration не поддерживается.  
  
-   не поддерживаются последовательности, в которых смешиваются типы на основе разных базовых типов;  
  
## <a name="see-also"></a>См. также  
 [Функции XQuery для типа данных XML](../xquery/xquery-functions-against-the-xml-data-type.md)  
  
  
