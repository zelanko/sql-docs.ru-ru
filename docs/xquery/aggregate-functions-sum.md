---
title: Функция Sum (XQuery) | Документация Майкрософт
description: Сведения о функции XQuery Sum (), возвращающей сумму последовательности чисел.
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
- sum function [XQuery]
- fn:sum function
ms.assetid: 12288f37-b54c-4237-b75e-eedc5fe8f96d
author: rothja
ms.author: jroth
ms.openlocfilehash: 3b6efd2cc3d5793d4524c4ab3d058a6375d23892
ms.sourcegitcommit: 5c7634b007f6808c87094174b80376cb20545d5f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/17/2020
ms.locfileid: "84886931"
---
# <a name="aggregate-functions---sum"></a>Агрегатные функции — sum
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Возвращает сумму последовательности чисел.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
fn:sum($arg as xdt:anyAtomicType*) as xdt:anyAtomicType  
```  
  
## <a name="arguments"></a>Аргументы  
 *$arg*  
 Последовательность атомарных значений, сумма которых должна быть вычислена.  
  
## <a name="remarks"></a>Комментарии  
 Все типы атомарных значений, передаваемых **функции Sum ()** , должны быть подтипами одного и того же базового типа. Базовые типы, которые принимаются, — это три встроенных числовых базовых типа или тип xdt:untypedAtomic. Значения типа xdt:untypedAtomic приводятся к типу xs:double. Если существует смесь этих типов или передаются другие значения других типов, возникает статическая ошибка.  
  
 Результат **Sum ()** получает базовый тип переданных типов, таких как xs: Double в случае xdt: untypedAtomic, даже если входные данные при необходимости являются пустой последовательностью. Если вход статически пуст, результатом будет значение 0 со статическим и динамическим типом xs:integer.  
  
 Функция **Sum ()** возвращает сумму числовых значений. Если значение xdt: untypedAtomic не может быть приведено к типу xs: Double, оно игнорируется во входной последовательности *$arg*. Если вход — это динамически вычисленная пустая последовательность, будет возвращено значение 0 используемого базового типа.  
  
 Функция возвращает ошибку времени выполнения, если происходит переполнение или исключение выхода за пределы диапазона.  
  
## <a name="examples"></a>Примеры  
 В этом разделе приведены примеры запросов XQuery к экземплярам XML, хранящимся в различных столбцах типа **XML** в [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] базе данных.  
  
### <a name="a-using-the-sum-xquery-function-to-find-the-total-combined-number-of-labor-hours-for-all-work-center-locations-in-the-manufacturing-process"></a>A. Использование функции языка XQuery sum() для определения полного количества рабочих часов для всех расположений цехов в производственном процессе  
 Следующий запрос находит общее количество трудовых часов для всех расположений цехов в производственном процессе всех моделей продукта, для которых сохранены производственные команды.  
  
```  
SELECT Instructions.query('         
   declare namespace AWMI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";         
  <ProductModel PMID= "{ sql:column("Production.ProductModel.ProductModelID") }"         
  ProductModelName = "{ sql:column("Production.ProductModel.Name") }" >         
   <TotalLaborHrs>         
     { sum(//AWMI:Location/@LaborHours) }         
   </TotalLaborHrs>         
 </ProductModel>         
    ') as Result         
FROM Production.ProductModel         
WHERE Instructions is not NULL         
```  
  
 Частичный результат.  
  
```  
<ProductModel PMID="7" ProductModelName="HL Touring Frame">  
   <TotalLaborHrs>12.75</TotalLaborHrs>  
</ProductModel>  
<ProductModel PMID="10" ProductModelName="LL Touring Frame">  
  <TotalLaborHrs>13</TotalLaborHrs>  
</ProductModel>  
...  
```  
  
 Вместо возврата результата в формате XML можно написать запрос для формирования относительных результатов, как показано в следующем запросе:  
  
```  
SELECT ProductModelID,         
        Name,         
        Instructions.value('declare namespace   
      AWMI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";         
    sum(//AWMI:Location/@LaborHours)', 'float') as TotalLaborHours         
FROM Production.ProductModel         
WHERE Instructions is not NULL          
```  
  
 Частичный результат:  
  
```  
ProductModelID Name                 TotalLaborHours         
-------------- -------------------------------------------------  
7              HL Touring Frame           12.75                   
10             LL Touring Frame           13                      
43             Touring Rear Wheel         3                       
...  
```  
  
### <a name="implementation-limitations"></a>Ограничения реализации  
 Существуют следующие ограничения:  
  
-   Поддерживается только одна версия аргумента **Sum ()** .  
  
-   Если вход — это динамически вычисленная пустая последовательность, будет возвращено значение 0 используемого базового типа вместо типа xs:integer.  
  
-   Функция **Sum ()** сопоставляет все целые числа с xs: Decimal.  
  
-   Функция **Sum ()** для значений типа xs: Duration не поддерживается.  
  
-   не поддерживаются последовательности, в которых смешиваются типы на основе разных базовых типов;  
  
-   Сумма ((xs: Double ("INF"), xs: Double ("-INF"))) вызывает ошибку домена.  
  
## <a name="see-also"></a>См. также:  
 [Функции XQuery для типа данных xml](../xquery/xquery-functions-against-the-xml-data-type.md)  
  
  
