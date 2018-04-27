---
title: distinct-values, функция (XQuery) | Документы Microsoft
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql
ms.prod_service: sql
ms.service: ''
ms.component: xquery
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- distinct-values function
- fn:distinct-values function
ms.assetid: f4c2bb53-2bec-4f1a-9c00-cf997fb7ae5b
caps.latest.revision: 26
author: rothja
ms.author: jroth
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c2d83e7cad7352e48576a29144f3cff1603b2e0c
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
---
# <a name="functions-on-sequences---distinct-values"></a>Функции над последовательностями - уникальных значений
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Удаляет повторяющиеся значения из последовательности, указываемой аргументом *$arg*. Если *$arg* представляет собой пустую последовательность, функция возвращает пустую последовательность.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
fn:distinct-values($arg as xdt:anyAtomicType*) as xdt:anyAtomicType*  
```  
  
## <a name="arguments"></a>Аргументы  
 *$arg*  
 Последовательность атомарных значений.  
  
## <a name="remarks"></a>Замечания  
 Все типы атомарных значений, передаваемые **distinct-values()** должны быть подтипами одного базового типа. Базовые типы, которые принимаются — типы, поддерживающие **eq** операции. Эти типы включают в себя три встроенных базовых численных типа, базовые типы даты-времени, а также xs:string, xs:boolean, xdt:untypedAtomic. Значения типа xdt:untypedAtomic приводятся к типу xs:string. Если имеется смесь этих типов или передаются значения других типов, возникает статическая ошибка.  
  
 Результат **distinct-values()** Получает базовый тип переданных типов, например xs: String для xdt: untypedAtomic, с исходным количеством элементов. Если вход статически пуст, подразумевается пустое значение, и формируется статическая ошибка.  
  
 Значения типа xs:string сравниваются в параметрах сортировки кодовых точек Юникода запроса XQuery по умолчанию.  
  
## <a name="examples"></a>Примеры  
 В этом разделе приведены примеры запросов XQuery к экземплярам XML, которые хранятся в различных **xml** столбцов типа в базе данных AdventureWorks.  
  
### <a name="a-using-the-distinct-values-function-to-remove-duplicate-values-from-the-sequence"></a>A. Использование функции distinct-values() для удаления из последовательности повторяющихся значений  
 В этом примере назначается экземпляр XML, содержащий телефонные номера **xml** переменной типа. XQuery, указанным по отношению к этой переменной, использует **distinct-values()** функции, чтобы получить список телефонных номеров, не содержащий дублирующихся значений.  
  
```  
declare @x xml  
set @x = '<PhoneNumbers>  
 <Number>111-111-1111</Number>  
 <Number>111-111-1111</Number>  
 <Number>222-222-2222</Number>  
</PhoneNumbers>'  
-- 1st select  
select @x.query('  
  distinct-values( data(/PhoneNumbers/Number) )  
') as result  
```  
  
 Результат:  
  
```  
111-111-1111 222-222-2222    
```  
  
 В следующем запросе последовательность чисел (1, 1, 2) передается в **distinct-values()** функции. Функция удаляет из последовательности дублирующееся значение и возвращает два оставшихся.  
  
```  
declare @x xml  
set @x = ''  
select @x.query('  
  distinct-values((1, 1, 2))  
') as result  
```  
  
 Запрос возвращает 1 2.  
  
### <a name="implementation-limitations"></a>Ограничения реализации  
 Существуют следующие ограничения:  
  
-   **Distinct-values()** функция сопоставляет целочисленные значения типу xs: decimal.  
  
-   **Distinct-values()** функция поддерживает только указанные выше типы и не поддерживает смесь базовых типов.  
  
-   **Distinct-values()** функции для значений xs: Duration не поддерживается.  
  
-   Синтаксический параметр для указания параметров сортировки не поддерживается.  
  
## <a name="see-also"></a>См. также  
 [Функции XQuery для типа данных XML](../xquery/xquery-functions-against-the-xml-data-type.md)  
  
  
