---
title: Макс. функция (XQuery) | Документация Майкрософт
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
- max function [XQuery]
- fn:max function
ms.assetid: 5ee625c0-044a-4cda-b210-02b64e619d65
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 814d8b0d33c55bd6aac77965d19a403ee7aec0c0
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47625152"
---
# <a name="aggregate-functions---max"></a>Агрегатные функции — max
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Возвращает из последовательности атомарных значений *$arg*, один элемент, значение которого больше, чем для всех остальных.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
fn:max($arg as xdt:anyAtomicType*) as xdt:anyAtomicType?  
```  
  
## <a name="arguments"></a>Аргументы  
 *$arg*  
 Последовательность атомарных значений, из которой требуется вернуть максимальное значение.  
  
## <a name="remarks"></a>Примечания  
 Все типы атомарных значений, которые передаются **max()** должны быть подтипами одного базового типа. Базовые типы, которые принимаются — типы, поддерживающие **gt** операции. Эти типы включают в себя три встроенных базовых численных типа, базовые типы даты-времени, а также xs:string, xs:boolean, xdt:untypedAtomic. Значения типа xdt:untypedAtomic приводятся к типу xs:double. Если имеется смесь этих типов или передаются другие значения других типов, возникает статическая ошибка.  
  
 Результат **max()** Получает базовый тип переданных типов, например xs: double в случае xdt: untypedAtomic. Если вход статически пуст, подразумевается пустое значение, и формируется статическая ошибка.  
  
 **Max()** функция возвращает одно значение в последовательности, которой больше, чем любой другой во входной последовательности. Для значений xs:string используются параметры сортировки кодовых точек Юникода по умолчанию. Если значение xdt: untypedAtomic не может быть приведен к типу xs: double, значение игнорируется во входной последовательности, *$arg*. Если вход — это динамически вычисляемая пустая последовательность, возвращается пустая последовательность.  
  
## <a name="examples"></a>Примеры  
 В этом разделе приведены примеры запросов XQuery к экземплярам XML, которые хранятся в различных **xml** -столбцов в [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] базы данных.  
  
### <a name="a-using-the-max-xquery-function-to-find-work-center-locations-in-the-manufacturing-process-that-have-the-most-labor-hours"></a>A. Использование XQuery-функции max() для поиска в производственном процессе цехов с наибольшим количеством рабочих часов  
 Запрос, приведенный в [функция min (XQuery)](../xquery/aggregate-functions-min.md) можно переписать с использованием **max()** функции.  
  
## <a name="implementation-limitations"></a>Ограничения реализации  
 Существуют следующие ограничения:  
  
-   **Max (**) функция сопоставляет все целочисленные значения типу xs: decimal.  
  
-   **Max()** функция значения типа xs: Duration не поддерживается.  
  
-   не поддерживаются последовательности, в которых смешиваются типы на основе разных базовых типов;  
  
-   Синтаксический параметр для указания параметров сортировки не поддерживается.  
  
## <a name="see-also"></a>См. также  
 [Функции XQuery для типа данных XML](../xquery/xquery-functions-against-the-xml-data-type.md)  
  
  
