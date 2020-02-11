---
title: 'Функция SQL: column () (XQuery) | Документация Майкрософт'
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
ms.openlocfilehash: df46abb8efdd5761797a599cf5a8cdebe02e5158
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67946012"
---
# <a name="xquery-extension-functions---sqlcolumn"></a>Функции расширения XQuery — sql:column()
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Как описано в разделе [Привязка реляционных данных в XML](../t-sql/xml/binding-relational-data-inside-xml-data.md), можно использовать функцию **SQL: column (()** при использовании [методов типа данных XML](../t-sql/xml/xml-data-type-methods.md) для предоставления реляционного значения в XQuery.  
  
 Например, [метод query () (тип данных XML)](../t-sql/xml/query-method-xml-data-type.md) используется для указания запроса к экземпляру XML, который хранится в переменной или столбце типа **XML** . Кроме того, иногда для совмещения реляционных данных с XML-данными бывает необходимо, чтобы запрос обрабатывал значения еще одного столбца, отличного от XML. Для этого используется функция **SQL: column ()** .  
  
 Значение SQL будет сопоставлено с соответствующим значением XQuery, а в качестве типа этого значения будет присвоен базовый тип XQuery, эквивалентный соответствующему типу SQL.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sql:column("columnName")  
```  
  
## <a name="remarks"></a>Remarks  
 Обратите внимание, что ссылка на столбец, указанный в функции **SQL: column ()** в запросе XQuery, ссылается на столбец в строке, которая обрабатывается.  
  
 В [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]можно ссылаться только на экземпляр **XML** в контексте ИСХОДНОГО выражения инструкции INSERT XML-DML. в противном случае нельзя ссылаться на столбцы, имеющие тип **XML** или определяемый пользователем тип данных CLR.  
  
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
 [SQL Server функции расширения XQuery](https://msdn.microsoft.com/library/4bc5d499-5fec-4c3f-b11e-5ab5ef9d8f97)   
 [Сравнение типизированного XML с нетипизированным XML](../relational-databases/xml/compare-typed-xml-to-untyped-xml.md)   
 [SQL Server &#40;XML-данных&#41;](../relational-databases/xml/xml-data-sql-server.md)   
 [Создание экземпляров XML-данных](../relational-databases/xml/create-instances-of-xml-data.md)   
 [Методы типа данных XML](../t-sql/xml/xml-data-type-methods.md)   
 [Язык изменения XML-данных &#40;XML DML&#41;](../t-sql/xml/xml-data-modification-language-xml-dml.md)  
  
  
