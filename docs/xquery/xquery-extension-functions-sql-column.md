---
title: 'Функция SQL: column () (XQuery) | Документация Майкрософт'
description: 'Узнайте, как с помощью функции XQuery SQL: column () можно привязывать реляционные данные, отличные от XML, в XML и одновременно объединять реляционные и XML-данные.'
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
- sql:column function
- sql:column() function
ms.assetid: e8f67bdf-b489-49a9-9d0f-2069c1750467
author: rothja
ms.author: jroth
ms.openlocfilehash: 55a38974ec5e85eeec58195c18edd1f6fb8b5cb4
ms.sourcegitcommit: 22dacedeb6e8721e7cdb6279a946d4002cfb5da3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/14/2020
ms.locfileid: "92038072"
---
# <a name="xquery-extension-functions---sqlcolumn"></a>Функции расширения XQuery — sql:column()
[!INCLUDE [SQL Server Azure SQL Database ](../includes/applies-to-version/sqlserver.md)]

  Как описано в разделе [Привязка реляционных данных в XML](../t-sql/xml/binding-relational-data-inside-xml-data.md), можно использовать функцию **SQL: column (()** при использовании [методов типа данных XML](../t-sql/xml/xml-data-type-methods.md) для предоставления реляционного значения в XQuery.  
  
 Например, [метод query () (тип данных XML)](../t-sql/xml/query-method-xml-data-type.md) используется для указания запроса к экземпляру XML, который хранится в переменной или столбце типа **XML** . Кроме того, иногда для совмещения реляционных данных с XML-данными бывает необходимо, чтобы запрос обрабатывал значения еще одного столбца, отличного от XML. Для этого используется функция **SQL: column ()** .  
  
 Значение SQL будет сопоставлено с соответствующим значением XQuery, а в качестве типа этого значения будет присвоен базовый тип XQuery, эквивалентный соответствующему типу SQL.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sql:column("columnName")  
```  
  
## <a name="remarks"></a>Remarks  
 Обратите внимание, что ссылка на столбец, указанный в функции **SQL: column ()** в запросе XQuery, ссылается на столбец в строке, которая обрабатывается.  
  
 В [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] можно ссылаться только на экземпляр **XML** в контексте исходного выражения инструкции INSERT XML. в противном случае нельзя ссылаться на столбцы, имеющие тип **XML** или определяемый пользователем тип данных CLR.  
  
 Функция **SQL: column ()** не поддерживается в операциях JOIN. Вместо этого можно использовать операцию APPLY.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-using-sqlcolumn-to-retrieve-the-relational-value-inside-xml"></a>A. Получение реляционного значения внутри XML с помощью функции sql:column()  
 В следующем примере конструирования XML показано получение значений реляционного столбца, отличного от XML, для связывания реляционных данных с XML-данными.  
  
 Запрос формирует XML следующей структуры:  
  
```xml
<Product ProductID="771" ProductName="Mountain-100 Silver, 38" ProductPrice="3399.99" ProductModelID="19"   
  ProductModelName="Mountain 100" />  
```  
  
 Обратите внимание на следующие особенности созданного кода XML.  
  
-   Значения атрибутов **ProductID**, **ProductName**и **ProductPrice** получены из таблицы **Product** .  
  
-   Значение атрибута **ProductModelID** извлекается из таблицы **ProductModel** .  
  
-   Чтобы сделать запрос более интересным, значение атрибута **ProductModelName** получается из столбца **CatalogDescription** **типа XML**. Поскольку данные каталога модели продукта XML хранятся не для всех моделей продуктов, с помощью инструкции `if` получаются только существующие значения.  
  
    ```sql
    SELECT P.ProductID, CatalogDescription.query('  
    declare namespace pd="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
           <Product   
               ProductID=       "{ sql:column("P.ProductID") }"  
               ProductName=     "{ sql:column("P.Name") }"  
               ProductPrice=    "{ sql:column("P.ListPrice") }"  
               ProductModelID= "{ sql:column("PM.ProductModelID") }" >  
               { if (not(empty(/pd:ProductDescription))) then  
                 attribute ProductModelName { /pd:ProductDescription[1]/@ProductModelName }  
                else   
                   ()  
    }  
            </Product>  
    ') as Result  
    FROM Production.ProductModel PM, Production.Product P  
    WHERE PM.ProductModelID = P.ProductModelID  
    AND   CatalogDescription is not NULL  
    ORDER By PM.ProductModelID  
    ```  
  
 Обратите внимание на следующие данные из предыдущего запроса:  
  
-   Поскольку значения получаются из двух разных таблиц, предложение FROM задает пару таблиц. Условие в предложении WHERE фильтрует результаты и получает только те продукты, у которых в каталоге есть описание моделей.  
  
-   Ключевое слово **Namespace** в [прологе XQuery](../xquery/modules-and-prologs-xquery-prolog.md) определяет префикс пространства имен XML "PD", который используется в теле запроса. Обратите внимание, что эти псевдонимы таблиц, «P» и «PM», задаются в предложении FROM самого запроса.  
  
-   Функция **SQL: column ()** используется для переноса в XML значений, отличных от XML.  
  
 Частичный результат:  
  
```  
ProductID               Result  
-----------------------------------------------------------------  
771         <Product ProductID="771"                   ProductName="Mountain-100 Silver, 38"   
                  ProductPrice="3399.99" ProductModelID="19"   
                  ProductModelName="Mountain 100" />  
...  
```  
  
 Следующий запрос создает XML, содержащий сведения о продукте. К этим сведениям относятся ProductID, ProductName, ProductPrice и (если значение доступно) ProductModelName для всех продуктов, относящихся к конкретной модели, ProductModelID=19. Затем XML присваивается @x переменной типа **XML** .  
  
```sql
declare @x xml  
SELECT @x = CatalogDescription.query('  
declare namespace pd="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
       <Product   
           ProductID=       "{ sql:column("P.ProductID") }"  
           ProductName=     "{ sql:column("P.Name") }"  
           ProductPrice=    "{ sql:column("P.ListPrice") }"  
           ProductModelID= "{ sql:column("PM.ProductModelID") }" >  
           { if (not(empty(/pd:ProductDescription))) then  
             attribute ProductModelName { /pd:ProductDescription[1]/@ProductModelName }  
            else   
               ()  
}  
        </Product>  
')   
FROM Production.ProductModel PM, Production.Product P  
WHERE PM.ProductModelID = P.ProductModelID  
And P.ProductModelID = 19  
select @x  
```  
  
## <a name="see-also"></a>См. также:  
 [SQL Server функции расширения XQuery]()   
 [Сравнение типизированного и нетипизированного XML](../relational-databases/xml/compare-typed-xml-to-untyped-xml.md)   
 [Данные XML (SQL Server)](../relational-databases/xml/xml-data-sql-server.md)   
 [Создание экземпляров XML-данных](../relational-databases/xml/create-instances-of-xml-data.md)   
 [методов типа данных xml](../t-sql/xml/xml-data-type-methods.md)   
 [Язык модификации XML-данных (XML DML)](../t-sql/xml/xml-data-modification-language-xml-dml.md)  
  
