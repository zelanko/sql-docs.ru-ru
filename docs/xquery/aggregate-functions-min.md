---
title: Функция MIN (XQuery) | Документы Microsoft
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
applies_to:
- SQL Server
dev_langs:
- XML
helpviewer_keywords:
- fn:min function
- min function [XQuery]
ms.assetid: db0b7d94-3fa6-488f-96d6-6a9a7d6eda23
caps.latest.revision: 28
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 7491ef774ae0664432223af05e89ffdf57788540
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="aggregate-functions---min"></a>Агрегатные функции - min
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Возвращает из последовательности атомарных значений *$arg*, один элемент, значение которого меньше всех остальных.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
fn:min($arg as xdt:anyAtomicType*) as xdt:anyAtomicType?  
```  
  
## <a name="arguments"></a>Аргументы  
 *$arg*  
 Последовательность элементов, из которой необходимо вернуть минимальное значение.  
  
## <a name="remarks"></a>Замечания  
 Все типы атомарных значений, передаваемые **min()** должны быть подтипами одного базового типа. Базовые типы, которые принимаются — типы, поддерживающие **gt** операции. Эти типы включают в себя три встроенных базовых численных типа, базовые типы даты-времени, а также xs:string, xs:boolean, xdt:untypedAtomic. Значения типа xdt:untypedAtomic приводятся к типу xs:double. Если имеется смесь этих типов или передаются значения других других типов, возникает статическая ошибка.  
  
 Результат **min()** Получает базовый тип переданных типов, например xs: double в случае использования xdt: untypedAtomic. Если вход статически пуст, подразумевается пустое значение и возвращается статическая ошибка.  
  
 **Min()** функция возвращает одно значение в последовательности, которая меньше, чем любой другой из входной последовательности. Для значений xs:string используются параметры сортировки кодовых точек Юникода по умолчанию. Если значение xdt: untypedAtomic не может быть приведен к типу xs: double, значение обрабатывается во входной последовательности *$arg*. Если вход — это динамически вычисляемая пустая последовательность, возвращается пустая последовательность.  
  
## <a name="examples"></a>Примеры  
 В этом разделе приведены примеры запросов XQuery к экземплярам XML, которые хранятся в различных **xml** столбцов типа в базе данных AdventureWorks.  
  
### <a name="a-using-the-min-xquery-function-to-find-the-work-center-location-that-has-the-fewest-labor-hours"></a>A. Использование функции min() языка XQuery для поиска расположения цеха с наименьшим количеством рабочих часов  
 Следующий запрос в процессе производства модели продукта (ProductModelID=7) получает все расположения цехов с наименьшим количеством рабочих часов. Обычно возвращается одно расположение, как показано далее. Если несколько расположений имеют одинаковое количество рабочих часов, возвращаются все.  
  
```  
select ProductModelID, Name, Instructions.query('  
  declare namespace AWMI=  
    "http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
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
  
-   **Имен** ключевое слово в прологе XQuery определяет префикс пространства имен. Данный префикс затем используется в теле XQuery.  
  
 Текст XQuery составляет XML, который содержит \<расположение > с WCID и **LaborHrs** атрибуты.  
  
-   Запрос также получает номер ProductModelID и значения имени.  
  
 Результат:  
  
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
  
  
