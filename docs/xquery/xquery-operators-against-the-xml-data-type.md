---
title: Сравнение операторов XQuery с xml-данных | Документы Microsoft
ms.custom: ''
ms.date: 03/16/2017
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
- XQuery, operators
- operators [XQuery]
- xml data type [SQL Server], XQuery
ms.assetid: 39ca3d2e-e928-4333-872b-75c4ccde8e79
caps.latest.revision: 23
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a4af87b91b32142d4b4266af5b10fa54e80eae7c
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
---
# <a name="xquery-operators-against-the-xml-data-type"></a>Сравнение операторов XQuery с XML-данными
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  XQuery поддерживает следующие операторы:  
  
-   числовые операторы (+, -, *, div, mod);  
  
-   операторы сравнения значений (eq, ne, lt, gt, le, ge);  
  
-   Операторы общего сравнения (=,! =, \<, >, \<=, > =)  
  
 Дополнительные сведения об этих операторах см. в разделе [выражения сравнения &#40;XQuery&#41;](../xquery/comparison-expressions-xquery.md)  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-using-general-operators"></a>A. Использование общих операторов  
 Этот запрос иллюстрирует использование общих операторов, применяемых к последовательностям, а также при сравнении последовательностей. Этот запрос извлекает последовательность телефонных номеров для каждого заказчика из **AdditionalContactInfo** столбец **контакт** таблицы. Далее эта последовательность сравнивается с последовательностью двух телефонных номеров (111-111-1111, 222-2222).  
  
 В запросе используется **=** оператор сравнения. Каждый узел последовательности справа от **=** оператор сравнивается с каждым узлом последовательности слева. При совпадении узлов сравнение узлов получает **TRUE**. Затем оно конвертируется в тип данных int и сравнивается с 1, а запрос возвращает идентификатор заказчика.  
  
```  
WITH XMLNAMESPACES (  
'http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactInfo' AS ACI,  
'http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes' AS ACT)  
SELECT ContactID   
FROM   Person.Contact  
WHERE  AdditionalContactInfo.value('  
      //ACI:AdditionalContactInfo//ACT:telephoneNumber/ACT:number =   
          ("111-111-1111", "222-2222")',  
      'bit')= cast(1 as bit)  
```  
  
 Имеется еще один способ определения того, как работает описанный запрос: каждый значение телефонного номера получаться **AdditionalContactInfo** столбца сравнивается с набором из двух телефонных номеров. Если значение входит в набор, в результате запроса возвращается этот заказчик.  
  
### <a name="b-using-a-numeric-operator"></a>Б. Использование числового оператора  
 Оператор + в данном запросе является оператором значения, так как он применяется к одному объекту. К примеру, значение 1 добавляется к размеру лота, возвращаемому этим запросом.  
  
```  
SELECT ProductModelID, Instructions.query('  
     declare namespace   
 AWMI="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
     for $i in (/AWMI:root/AWMI:Location)[1]  
     return   
       <Location LocationID="{ ($i/@LocationID) }"  
                   LotSize  = "{  number($i/@LotSize) }"  
                   LotSize2 = "{ number($i/@LotSize) + 1 }"  
                   LotSize3 = "{ number($i/@LotSize) + 2 }" >  
  
       </Location>  
') as Result  
FROM Production.ProductModel  
where ProductModelID=7  
```  
  
### <a name="c-using-a-value-operator"></a>В. Использование оператора значения  
 Следующий запрос считывает элементы <`Picture`> для модели продукта, размер картинки которой равен «small».  
  
```  
SELECT CatalogDescription.query('  
     declare namespace PD="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
     for $P in /PD:ProductDescription/PD:Picture[PD:Size eq "small"]  
     return  
           $P  
    ') as Result  
FROM Production.ProductModel  
where ProductModelID=19  
```  
  
 Так как оба операнда **eq** оператор представляют собой атомарные значения, в запросе используется оператор значений. Тот же запрос можно написать с помощью общего оператора сравнения ( **=** ).  
  
## <a name="see-also"></a>См. также  
 [Функции XQuery для типа данных xml](../xquery/xquery-functions-against-the-xml-data-type.md)   
 [Данные XML (SQL Server)](../relational-databases/xml/xml-data-sql-server.md)   
 [Справочник по языку XQuery (SQL Server)](../xquery/xquery-language-reference-sql-server.md)  
  
  
