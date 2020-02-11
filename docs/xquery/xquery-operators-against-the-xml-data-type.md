---
title: Операторы XQuery к типу данных XML | Документация Майкрософт
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
ms.openlocfilehash: b113fbd8111072790d1f0904b3e751c6629725b2
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67945959"
---
# <a name="xquery-operators-against-the-xml-data-type"></a>Сравнение операторов XQuery с XML-данными
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  XQuery поддерживает следующие операторы:  
  
-   числовые операторы (+, -, *, div, mod);  
  
-   операторы сравнения значений (eq, ne, lt, gt, le, ge);  
  
-   Операторы для общего сравнения (=,! =, \<, >, \<=, >=)  
  
 Дополнительные сведения об этих операторах см. в разделе [выражения сравнения &#40;XQuery&#41;](../xquery/comparison-expressions-xquery.md)  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-using-general-operators"></a>A. Использование общих операторов  
 Этот запрос иллюстрирует использование общих операторов, применяемых к последовательностям, а также при сравнении последовательностей. Запрос получает последовательность телефонных номеров для каждого клиента из столбца **AdditionalContactInfo** таблицы **Contact** . Далее эта последовательность сравнивается с последовательностью двух телефонных номеров (111-111-1111, 222-2222).  
  
 В запросе используется оператор **=** сравнения. Каждый узел в последовательности справа от **=** оператора сравнивается с каждым узлом последовательности в левой части. Если узлы совпадают, сравнение узлов имеет **значение true**. Затем оно конвертируется в тип данных int и сравнивается с 1, а запрос возвращает идентификатор заказчика.  
  
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
  
 Существует еще один способ узнать, как работает предыдущий запрос: каждое значение телефонного номера, полученное из столбца **AdditionalContactInfo** , сравнивается с набором из двух телефонных номеров. Если значение входит в набор, в результате запроса возвращается этот заказчик.  
  
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
 Следующий запрос получает элементы <`Picture`> для модели продукта, размер изображения которой — Small.  
  
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
  
 Поскольку оба операнда оператора **EQ** являются атомарными значениями, в запросе используется оператор значения. Тот же запрос можно написать с помощью общего оператора сравнения ( **=** ).  
  
## <a name="see-also"></a>См. также:  
 [Функции XQuery для типа данных XML](../xquery/xquery-functions-against-the-xml-data-type.md)   
 [SQL Server &#40;XML-данных&#41;](../relational-databases/xml/xml-data-sql-server.md)   
 [Справочник по языку XQuery &#40;SQL Server&#41;](../xquery/xquery-language-reference-sql-server.md)  
  
  
