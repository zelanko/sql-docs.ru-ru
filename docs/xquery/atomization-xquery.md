---
title: "Атомизация (XQuery) | Документы Microsoft"
ms.custom: 
ms.date: 08/01/2016
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: 
ms.component: xquery
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: XML
helpviewer_keywords:
- XQuery, atomization
- atomization [XQuery]
ms.assetid: e3d7cf2f-c6fb-43c2-8538-4470a6375af5
caps.latest.revision: "16"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 1b35d5e55a2d0e913586e7c60d161e4e2e85c6cb
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/05/2017
---
# <a name="atomization-xquery"></a>Атомизация (XQuery)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Атомизация — это процесс извлечения типизированного значения элемента. В определенных обстоятельствах подразумевается, что этот процесс будет осуществлен. Некоторые из операторов XQuery (например, арифметические и операторы сравнения), зависят от этого процесса. Например, когда арифметические операторы применяют непосредственно к узлам, типизированное значение узла сначала извлекается с помощью неявного вызова [данных функция](../xquery/data-accessor-functions-data-xquery.md). При этом атомарное значение передается в качестве операнда арифметическому оператору.  
  
 Следующий запрос возвращает сумму атрибутов LaborHours. В этом случае **data()** неявно применяется к узлам атрибутов.  
  
```  
declare @x xml  
set @x='<ROOT><Location LID="1" SetupTime="1.1" LaborHours="3.3" />  
<Location LID="2" SetupTime="1.0" LaborHours="5" />  
<Location LID="3" SetupTime="2.1" LaborHours="4" />  
</ROOT>'  
-- data() implicitly applied to the attribute node sequence.  
SELECT @x.query('sum(/ROOT/Location/@LaborHours)')  
```  
  
 Несмотря на то, что не требуется, можно также явно указать **data()** функции:  
  
```  
SELECT @x.query('sum(data(ROOT/Location/@LaborHours))')  
```  
  
 Другой пример неявной атомизации — использование арифметических операторов.  **+**  Оператор требует атомарных значений и **data()** неявно применяется для получения элементарного значения атрибута LaborHours. Запрос адресован столбцу Instructions типа **xml** типа Instructions таблицы ProductModel. Следующий запрос трижды возвращает атрибут LaborHours. Обратите внимание на следующие особенности запроса.  
  
-   При конструировании атрибута OrignialLaborHours атомизация неявно применяется к одноэлементной последовательности, которую возвращает (`$WC/@LaborHours`). Типизированное значение атрибута LaborHours присваивается атрибуту OriginalLaborHours.  
  
-   При конструировании атрибута UpdatedLaborHoursV1 арифметический оператор требует атомарных значений. Таким образом **data()** неявно применяется к атрибуту LaborHours, который возвращается (`$WC/@LaborHours`). Затем к нему добавляется атомарное значение 1. Конструирование атрибута UpdatedLaborHoursV2 показывает явное применение **data()**, но не является обязательным.  
  
```  
SELECT Instructions.query('  
     declare namespace AWMI="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
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
  
 Атомизация происходит также с параметрами выражений сравнения, передаваемыми функциям, значениями, возвращаемыми функциями, **cast()** выражения и выражениями сортировки, передаваемыми по порядку предложением.  
  
## <a name="see-also"></a>См. также:  
 [Основы языка XQuery](../xquery/xquery-basics.md)   
 [Выражения сравнения &#40; XQuery &#41;](../xquery/comparison-expressions-xquery.md)   
 [Функции XQuery для типа данных XML](../xquery/xquery-functions-against-the-xml-data-type.md)  
  
  
