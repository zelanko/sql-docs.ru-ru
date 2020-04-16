---
title: Операторы X-образного типа против xml (ru) Документы Майкрософт
description: Узнайте об операторах X's, которые могут быть использованы против типа данных xml.
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- XQuery, operators
- operators [XQuery]
- xml data type [SQL Server], XQuery
ms.assetid: 39ca3d2e-e928-4333-872b-75c4ccde8e79
author: rothja
ms.author: jroth
ms.openlocfilehash: d5692aa5b46d79c68165fa6f1320034fdb7e03b3
ms.sourcegitcommit: a3f5c3742d85d21f6bde7c6ae133060dcf1ddd44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/15/2020
ms.locfileid: "81388300"
---
# <a name="xquery-operators-against-the-xml-data-type"></a>Сравнение операторов XQuery с XML-данными
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  XQuery поддерживает следующие операторы:  
  
-   числовые операторы (+, -, *, div, mod);  
  
-   операторы сравнения значений (eq, ne, lt, gt, le, ge);  
  
-   Операторы для общего сравнения ( \<q, \<! , , >, >)  
  
 Для получения дополнительной информации об этих оператора [&#41;&#40;х см.](../xquery/comparison-expressions-xquery.md)  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-using-general-operators"></a>A. Использование общих операторов  
 Этот запрос иллюстрирует использование общих операторов, применяемых к последовательностям, а также при сравнении последовательностей. Запрос извлекает последовательность телефонных номеров для каждого клиента из столбца **AdditionalContactInfo** таблицы **Контакт.** Далее эта последовательность сравнивается с последовательностью двух телефонных номеров (111-111-1111, 222-2222).  
  
 В запросе **=** используется оператор сравнения. Каждый узлы в последовательности на **=** правой стороне оператора сравнивают с каждым узлом в последовательности на левой стороне. Если узлы совпадают, сравнение узлов **является правдой**. Затем оно конвертируется в тип данных int и сравнивается с 1, а запрос возвращает идентификатор заказчика.  
  
```sql
WITH XMLNAMESPACES (  
'https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactInfo' AS ACI,  
'https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes' AS ACT)  
SELECT ContactID   
FROM   Person.Contact  
WHERE  AdditionalContactInfo.value('  
      //ACI:AdditionalContactInfo//ACT:telephoneNumber/ACT:number =   
          ("111-111-1111", "222-2222")',  
      'bit')= cast(1 as bit)  
```  
  
 Существует еще один способ наблюдать за тем, как работает предыдущий запрос: значение каждого номера телефона, извлеченное из столбца **AdditionalContactInfo,** сравнивается с набором двух телефонных номеров. Если значение входит в набор, в результате запроса возвращается этот заказчик.  
  
### <a name="b-using-a-numeric-operator"></a>Б. Использование числового оператора  
 Оператор + в данном запросе является оператором значения, так как он применяется к одному объекту. К примеру, значение 1 добавляется к размеру лота, возвращаемому этим запросом.  
  
```sql
SELECT ProductModelID, Instructions.query('  
     declare namespace   
 AWMI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
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
 Следующий запрос получает <`Picture`> элементов для модели продукта, где размер изображения является "небольшим":  
  
```sql
SELECT CatalogDescription.query('  
     declare namespace PD="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
     for $P in /PD:ProductDescription/PD:Picture[PD:Size eq "small"]  
     return  
           $P  
    ') as Result  
FROM Production.ProductModel  
where ProductModelID=19  
```  
  
 Поскольку оба operands для оператора **eq** являются атомными значениями, оператор значений используется в запросе. Вы можете написать тот же запрос с **=** помощью оператора общего сравнения ().  
  
## <a name="see-also"></a>См. также:  
 [Функции X'ери против типа данных xml](../xquery/xquery-functions-against-the-xml-data-type.md)   
 [XML данные &#40;&#41;сервера S'L](../relational-databases/xml/xml-data-sql-server.md)   
 [Справочник по языку XQuery (SQL Server)](../xquery/xquery-language-reference-sql-server.md)  
  
  
