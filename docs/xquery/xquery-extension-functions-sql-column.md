---
title: 'SQL: column() (XQuery) | Документация Майкрософт'
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
manager: craigg
ms.openlocfilehash: c5b7babb3f34f906a241669bbde753e3beaace92
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/15/2018
ms.locfileid: "51662273"
---
# <a name="xquery-extension-functions---sqlcolumn"></a>Функции расширения XQuery — sql:column()
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Как описано в разделе [Привязка реляционных данных внутри XML](../t-sql/xml/binding-relational-data-inside-xml-data.md), можно использовать **SQL: column()** можно использовать функцию [методов типа данных XML](../t-sql/xml/xml-data-type-methods.md) для получения реляционного значения внутри XQuery.  
  
 Например [метода query() (тип данных XML)](../t-sql/xml/query-method-xml-data-type.md) используется для указания запроса к экземпляру XML, который хранится в переменной или столбце типа **xml** типа. Кроме того, иногда для совмещения реляционных данных с XML-данными бывает необходимо, чтобы запрос обрабатывал значения еще одного столбца, отличного от XML. Чтобы сделать это, используйте **SQL: column()** функции.  
  
 Значение SQL будет сопоставлено с соответствующим значением XQuery, а в качестве типа этого значения будет присвоен базовый тип XQuery, эквивалентный соответствующему типу SQL.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sql:column("columnName")  
```  
  
## <a name="remarks"></a>Примечания  
 Обратите внимание, что ссылка на столбец, указанный в **SQL: column()** функции внутри XQuery ссылается на столбец в строке, которая обрабатывается.  
  
 В [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], могут ссылаться только на **xml** инструкция insert экземпляр в контексте исходного выражения XML DML; в противном случае — значение не может ссылаться на столбцы, которые относятся к типу **xml** или среды CLR определяемый пользователем тип.  
  
 **SQL: column()** функция не поддерживается в операции СОЕДИНЕНИЯ. Вместо этого можно использовать операцию APPLY.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-using-sqlcolumn-to-retrieve-the-relational-value-inside-xml"></a>A. Получение реляционного значения внутри XML с помощью функции sql:column()  
 В следующем примере конструирования XML показано получение значений реляционного столбца, отличного от XML, для связывания реляционных данных с XML-данными.  
  
 Запрос формирует XML следующей структуры:  
  
```xml
<Product ProductID="771" ProductName="Mountain-100 Silver, 38" ProductPrice="3399.99" ProductModelID="19"   
  ProductModelName="Mountain 100" />  
```  
  
 Обратите внимание на следующие особенности созданного кода XML.  
  
-   **ProductID**, **ProductName**, и **ProductPrice** значения атрибутов извлекаются из **продукта** таблицы.  
  
-   **ProductModelID** значение атрибута извлекается из **ProductModel** таблицы.  
  
-   Чтобы сделать запрос более интересным, **ProductModelName** атрибута значение получается из **CatalogDescription** столбец **тип xml**. Поскольку данные каталога модели продукта XML хранятся не для всех моделей продуктов, с помощью инструкции `if` получаются только существующие значения.  
  
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
  
-   **Пространства имен** ключевое слово в [прологе XQuery](../xquery/modules-and-prologs-xquery-prolog.md) определяет префикс пространства имен XML, «pd», который используется в теле запроса. Обратите внимание, что эти псевдонимы таблиц, «P» и «PM», задаются в предложении FROM самого запроса.  
  
-   **SQL: column()** функция используется для добавления Реляционного значения внутри XML.  
  
 Частичный результат:  
  
```  
ProductID               Result  
-----------------------------------------------------------------  
771         <Product ProductID="771"                   ProductName="Mountain-100 Silver, 38"   
                  ProductPrice="3399.99" ProductModelID="19"   
                  ProductModelName="Mountain 100" />  
...  
```  
  
 Следующий запрос создает XML, содержащий сведения о продукте. К этим сведениям относятся ProductID, ProductName, ProductPrice и (если значение доступно) ProductModelName для всех продуктов, относящихся к конкретной модели, ProductModelID=19. Затем присваивается XML @x переменной **xml** типа.  
  
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
  
## <a name="see-also"></a>См. также  
 [Функции расширения XQuery для SQL Server](https://msdn.microsoft.com/library/4bc5d499-5fec-4c3f-b11e-5ab5ef9d8f97)   
 [Сравнение типизированного и нетипизированного XML](../relational-databases/xml/compare-typed-xml-to-untyped-xml.md)   
 [Данные XML (SQL Server)](../relational-databases/xml/xml-data-sql-server.md)   
 [Создание экземпляров XML-данных](../relational-databases/xml/create-instances-of-xml-data.md)   
 [методов типа данных xml](../t-sql/xml/xml-data-type-methods.md)   
 [Язык модификации XML-данных (XML DML)](../t-sql/xml/xml-data-modification-language-xml-dml.md)  
  
  
