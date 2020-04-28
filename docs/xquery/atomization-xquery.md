---
title: Разъединение (XQuery) | Документация Майкрософт
ms.custom: ''
ms.date: 08/01/2016
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- XQuery, atomization
- atomization [XQuery]
ms.assetid: e3d7cf2f-c6fb-43c2-8538-4470a6375af5
author: rothja
ms.author: jroth
ms.openlocfilehash: e034e6464e395c1516eed874ed1c0cff2c32238f
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "67985706"
---
# <a name="atomization-xquery"></a>Атомизация (XQuery)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Атомизация — это процесс извлечения типизированного значения элемента. В определенных обстоятельствах подразумевается, что этот процесс будет осуществлен. Некоторые из операторов XQuery (например, арифметические и операторы сравнения), зависят от этого процесса. Например, при применении арифметических операторов непосредственно к узлам типизированное значение узла сначала извлекается путем неявного вызова [функции данных](../xquery/data-accessor-functions-data-xquery.md). При этом атомарное значение передается в качестве операнда арифметическому оператору.  
  
 Следующий запрос возвращает сумму атрибутов LaborHours. В этом случае **данные ()** неявно применяются к узлам атрибутов.  
  
```  
declare @x xml  
set @x='<ROOT><Location LID="1" SetupTime="1.1" LaborHours="3.3" />  
<Location LID="2" SetupTime="1.0" LaborHours="5" />  
<Location LID="3" SetupTime="2.1" LaborHours="4" />  
</ROOT>'  
-- data() implicitly applied to the attribute node sequence.  
SELECT @x.query('sum(/ROOT/Location/@LaborHours)')  
```  
  
 Хотя это и не является обязательным, можно также явно указать функцию **Data ()** :  
  
```  
SELECT @x.query('sum(data(ROOT/Location/@LaborHours))')  
```  
  
 Другой пример неявной атомизации — использование арифметических операторов. **+** Оператору требуются атомарные значения, и **данные ()** неявно применяются для получения атомарного значения атрибута LaborHours. Запрос задается для столбца Instructions типа **XML** в таблице ProductModel. Следующий запрос трижды возвращает атрибут LaborHours. Обратите внимание на следующие особенности запроса.  
  
-   При конструировании атрибута OrignialLaborHours атомизация неявно применяется к одноэлементной последовательности, которую возвращает (`$WC/@LaborHours`). Типизированное значение атрибута LaborHours присваивается атрибуту OriginalLaborHours.  
  
-   При конструировании атрибута UpdatedLaborHoursV1 арифметический оператор требует атомарных значений. Таким образом, **данные ()** неявно применяются к атрибуту LaborHours, возвращаемому методом (`$WC/@LaborHours`). Затем к нему добавляется атомарное значение 1. Конструкция атрибута UpdatedLaborHoursV2 показывает явное применение **данных ()**, но не является обязательным.  
  
```  
SELECT Instructions.query('  
     declare namespace AWMI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
for $WC in /AWMI:root/AWMI:Location[1]  
        return  
            <WC OriginalLaborHours = "{ $WC/@LaborHours }"  
                UpdatedLaborHoursV1 = "{ $WC/@LaborHours + 1 }"   
                UpdatedLaborHoursV2 = "{ data($WC/@LaborHours) + 1 }" >  
            </WC>') as Result  
FROM Production.ProductModel  
where ProductModelID=7  
```  
  
 Результат:  
  
```  
<WC OriginalLaborHours="2.5"   
    UpdatedLaborHoursV1="3.5"   
    UpdatedLaborHoursV2="3.5" />  
```  
  
 Атомизация приводит к экземпляру простого типа, пустому множеству или к ошибке статического типа.  
  
 Атомарность также возникает в параметрах выражений сравнения, передаваемых функциям, значения, возвращаемые функциями, выражениями **Cast ()** и выражениями сортировки, передаваемыми в предложении ORDER BY.  
  
## <a name="see-also"></a>См. также:  
 [Основы XQuery](../xquery/xquery-basics.md)   
 [Выражения сравнения &#40;XQuery&#41;](../xquery/comparison-expressions-xquery.md)   
 [Функции XQuery для типа данных xml](../xquery/xquery-functions-against-the-xml-data-type.md)  
  
  
