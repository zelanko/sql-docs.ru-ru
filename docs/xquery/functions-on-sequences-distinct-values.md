---
title: Функция distinct-values (XQuery) | Документация Майкрософт
description: Узнайте, как использовать функцию distinct-values в языке XQuery для удаления повторяющихся значений из последовательности.
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
- distinct-values function
- fn:distinct-values function
ms.assetid: f4c2bb53-2bec-4f1a-9c00-cf997fb7ae5b
author: rothja
ms.author: jroth
ms.openlocfilehash: 1a82bfef35b0d8aec39f7f539f65e6ff1fe8f3ee
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85753576"
---
# <a name="functions-on-sequences---distinct-values"></a>Функции с последовательностями — distinct-values
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../includes/applies-to-version/sqlserver.md)]

  Удаляет дублирующиеся значения из последовательности, указанной параметром *$arg*. Если *$arg* является пустой последовательностью, функция возвращает пустую последовательность.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
fn:distinct-values($arg as xdt:anyAtomicType*) as xdt:anyAtomicType*  
```  
  
## <a name="arguments"></a>Аргументы  
 *$arg*  
 Последовательность атомарных значений.  
  
## <a name="remarks"></a>Примечания  
 Все типы атомарных значений, которые передаются в **различные значения ()** , должны быть подтипами одного и того же базового типа. Допустимые базовые типы — это типы, поддерживающие операцию **EQ** . Эти типы включают в себя три встроенных базовых численных типа, базовые типы даты-времени, а также xs:string, xs:boolean, xdt:untypedAtomic. Значения типа xdt:untypedAtomic приводятся к типу xs:string. Если имеется смесь этих типов или передаются значения других типов, возникает статическая ошибка.  
  
 Результат **distinct-values ()** получает базовый тип переданных типов, например xs: String в случае xdt: untypedAtomic с исходной кратностью. Если вход статически пуст, подразумевается пустое значение, и формируется статическая ошибка.  
  
 Значения типа xs:string сравниваются в параметрах сортировки кодовых точек Юникода запроса XQuery по умолчанию.  
  
## <a name="examples"></a>Примеры  
 В этом разделе приведены примеры запросов XQuery к экземплярам XML, хранящимся в различных столбцах типа **XML** в базе данных AdventureWorks.  
  
### <a name="a-using-the-distinct-values-function-to-remove-duplicate-values-from-the-sequence"></a>A. Использование функции distinct-values() для удаления из последовательности повторяющихся значений  
 В этом примере экземпляр XML, содержащий телефонные номера, назначается переменной типа **XML** . В языке XQuery, указанном для этой переменной, используется функция **distinct-values ()** для компиляции списка телефонных номеров, которые не содержат дубликатов.  
  
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
  
 В следующем запросе в функцию **distinct-values ()** передается последовательность чисел (1, 1, 2). Функция удаляет из последовательности дублирующееся значение и возвращает два оставшихся.  
  
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
  
-   Функция **distinct-values ()** сопоставляет целочисленные значения с типом xs: Decimal.  
  
-   Функция **distinct-values ()** поддерживает только упомянутые выше типы и не поддерживает смесь базовых типов.  
  
-   Функция **distinct-values ()** для значений xs: Duration не поддерживается.  
  
-   Синтаксический параметр для указания параметров сортировки не поддерживается.  
  
## <a name="see-also"></a>См. также  
 [Функции XQuery для типа данных xml](../xquery/xquery-functions-against-the-xml-data-type.md)  
  
  
