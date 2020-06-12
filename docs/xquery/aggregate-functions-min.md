---
title: Функция min (XQuery) | Документация Майкрософт
description: Сведения о функции min () XQuery, возвращающей один элемент в последовательности, значение которой меньше, чем все остальные.
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
- fn:min function
- min function [XQuery]
ms.assetid: db0b7d94-3fa6-488f-96d6-6a9a7d6eda23
author: rothja
ms.author: jroth
ms.openlocfilehash: b209f6d46c47de5a604eee3c14c681a333bcdec8
ms.sourcegitcommit: 2f166e139f637d6edfb5731510d632a13205eb25
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/08/2020
ms.locfileid: "84529978"
---
# <a name="aggregate-functions---min"></a>Агрегатные функции — min
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Возвращает из последовательности атомарных значений, *$arg*один элемент, значение которого меньше значения всех остальных.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
fn:min($arg as xdt:anyAtomicType*) as xdt:anyAtomicType?  
```  
  
## <a name="arguments"></a>Аргументы  
 *$arg*  
 Последовательность элементов, из которой необходимо вернуть минимальное значение.  
  
## <a name="remarks"></a>Комментарии  
 Все типы атомарных значений, которые передаются в **min ()** , должны быть подтипами одного и того же базового типа. Допустимые базовые типы — это типы, поддерживающие операцию **gt** . Эти типы включают в себя три встроенных базовых численных типа, базовые типы даты-времени, а также xs:string, xs:boolean, xdt:untypedAtomic. Значения типа xdt:untypedAtomic приводятся к типу xs:double. Если существует смесь этих типов или передаются другие значения других типов, возникает статическая ошибка.  
  
 Результат **min ()** получает базовый тип переданных типов, например xs: Double в случае xdt: untypedAtomic. Если вход статически пуст, подразумевается пустое значение и возвращается статическая ошибка.  
  
 Функция **min ()** возвращает одно значение в последовательности, которое меньше, чем любое другое во входной последовательности. Для значений xs:string используются параметры сортировки кодовых точек Юникода по умолчанию. Если значение xdt: untypedAtomic не может быть приведено к типу xs: Double, оно игнорируется во входной последовательности *$arg*. Если вход — это динамически вычисляемая пустая последовательность, возвращается пустая последовательность.  
  
## <a name="examples"></a>Примеры  
 В этом разделе приведены примеры запросов XQuery к экземплярам XML, хранящимся в различных столбцах типа **XML** в базе данных AdventureWorks.  
  
### <a name="a-using-the-min-xquery-function-to-find-the-work-center-location-that-has-the-fewest-labor-hours"></a>А) Использование функции min() языка XQuery для поиска расположения цеха с наименьшим количеством рабочих часов  
 Следующий запрос в процессе производства модели продукта (ProductModelID=7) получает все расположения цехов с наименьшим количеством рабочих часов. Обычно возвращается одно расположение, как показано далее. Если несколько расположений имеют одинаковое количество рабочих часов, возвращаются все.  
  
```  
select ProductModelID, Name, Instructions.query('  
  declare namespace AWMI=  
    "https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
  for   $Location in /AWMI:root/AWMI:Location  
  where $Location/@LaborHours =  
          min( /AWMI:root/AWMI:Location/@LaborHours )  
return  
  <Location WCID=     "{ $Location/@LocationID }"   
              LaborHrs= "{ $Location/@LaborHours }" />  
  ') as Result   
FROM  Production.ProductModel  
WHERE ProductModelID=7  
```  
  
 Обратите внимание на следующие данные из предыдущего запроса:  
  
-   Ключевое слово **Namespace** в прологе XQuery определяет префикс пространства имен. Данный префикс затем используется в теле XQuery.  
  
 В теле запроса XQuery создается XML-код, содержащий \<Location> элемент с атрибутами вЦид и **лаборхрс** .  
  
-   Запрос также получает номер ProductModelID и значения имени.  
  
 Результат:  
  
```  
ProductModelID   Name              Result  
---------------  ----------------  ---------------------------------  
7                HL Touring Frame  <Location WCID="45" LaborHrs="0.5"/>   
```  
  
## <a name="implementation-limitations"></a>Ограничения реализации  
 Существуют следующие ограничения:  
  
-   Функция **min ()** сопоставляет все целые числа с xs: Decimal.  
  
-   Функция **min ()** для значений типа xs: Duration не поддерживается.  
  
-   не поддерживаются последовательности, в которых смешиваются типы на основе разных базовых типов;  
  
-   Синтаксический параметр для указания параметров сортировки не поддерживается.  
  
## <a name="see-also"></a>См. также:  
 [Функции XQuery для типа данных xml](../xquery/xquery-functions-against-the-xml-data-type.md)  
  
  
