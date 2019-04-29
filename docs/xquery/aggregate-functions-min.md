---
title: Функция MIN (XQuery) | Документация Майкрософт
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
manager: craigg
ms.openlocfilehash: 69381eb0ffdd3638079d824d8d4c150563375a6c
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63046968"
---
# <a name="aggregate-functions---min"></a>Агрегатные функции — min
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Возвращает из последовательности атомарных значений *$arg*, один элемент, значение которого меньше всех остальных.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
fn:min($arg as xdt:anyAtomicType*) as xdt:anyAtomicType?  
```  
  
## <a name="arguments"></a>Аргументы  
 *$arg*  
 Последовательность элементов, из которой необходимо вернуть минимальное значение.  
  
## <a name="remarks"></a>Примечания  
 Все типы атомарных значений, которые передаются **min()** должны быть подтипами одного базового типа. Базовые типы, которые принимаются — типы, поддерживающие **gt** операции. Эти типы включают в себя три встроенных базовых численных типа, базовые типы даты-времени, а также xs:string, xs:boolean, xdt:untypedAtomic. Значения типа xdt:untypedAtomic приводятся к типу xs:double. Если имеется смесь этих типов или передаются другие значения других типов, возникает статическая ошибка.  
  
 Результат **min()** Получает базовый тип переданных типов, например xs: double в случае xdt: untypedAtomic. Если вход статически пуст, подразумевается пустое значение и возвращается статическая ошибка.  
  
 **Min()** функция возвращает одно значение в последовательности, которая меньше, чем любой другой во входной последовательности. Для значений xs:string используются параметры сортировки кодовых точек Юникода по умолчанию. Если значение xdt: untypedAtomic не может быть приведен к типу xs: double, значение игнорируется во входной последовательности, *$arg*. Если вход — это динамически вычисляемая пустая последовательность, возвращается пустая последовательность.  
  
## <a name="examples"></a>Примеры  
 В этом разделе приведены примеры запросов XQuery к экземплярам XML, которые хранятся в различных **xml** -столбец базы данных AdventureWorks.  
  
### <a name="a-using-the-min-xquery-function-to-find-the-work-center-location-that-has-the-fewest-labor-hours"></a>A. Использование функции min() языка XQuery для поиска расположения цеха с наименьшим количеством рабочих часов  
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
  
-   **Пространства имен** ключевое слово в прологе XQuery определяет префикс пространства имен. Данный префикс затем используется в теле XQuery.  
  
 Текст XQuery составляет XML, который имеет \<расположение > элемент с WCID и **LaborHrs** атрибуты.  
  
-   Запрос также получает номер ProductModelID и значения имени.  
  
 Это результат:  
  
```  
ProductModelID   Name              Result  
---------------  ----------------  ---------------------------------  
7                HL Touring Frame  <Location WCID="45" LaborHrs="0.5"/>   
```  
  
## <a name="implementation-limitations"></a>Ограничения реализации  
 Существуют следующие ограничения:  
  
-   **Min()** функция сопоставляет все целочисленные значения типу xs: decimal.  
  
-   **Min()** функция значения типа xs: Duration не поддерживается.  
  
-   не поддерживаются последовательности, в которых смешиваются типы на основе разных базовых типов;  
  
-   Синтаксический параметр для указания параметров сортировки не поддерживается.  
  
## <a name="see-also"></a>См. также  
 [Функции XQuery для типа данных XML](../xquery/xquery-functions-against-the-xml-data-type.md)  
  
  
