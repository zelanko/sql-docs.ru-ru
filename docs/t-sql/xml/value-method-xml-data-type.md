---
title: "Метод value() (тип данных xml) | Документы Microsoft"
ms.custom: 
ms.date: 07/26/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|xml
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- value method
- value() method
ms.assetid: 298a7361-dc9a-4902-9b1e-49a093cd831d
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Active
ms.openlocfilehash: 7a3822e0469836b59369eb676ece956533d4df58
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
---
# <a name="value-method-xml-data-type"></a>Метод value() (тип данных xml)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Выполняет запрос XQuery к структуре XML и возвращает значение типа SQL. Данный метод возвращает скалярное значение.  
  
 Этот метод обычно используется для извлечения значения из экземпляра XML хранится в **xml** столбец типа, параметра или переменной. При этом его можно использовать в запросах SELECT для объединения или сравнения данных XML с данными в столбцах других типов.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
value (XQuery, SQLType)  
```  
  
## <a name="arguments"></a>Аргументы  
 *XQuery*  
 — *XQuery* выражение, строковый литерал, извлекающий данные из экземпляра XML. Выражение XQuery должно возвращать не более одного значения. Иначе возвращается ошибка.  
  
 *SQLType*  
 Предпочтительный тип SQL — строковый литерал, который необходимо вернуть. Тип возвращаемого значения этот метод соответствует *SQLType* параметра. *SQLType* не может быть **xml** тип данных, среда CLR определяемого пользователем тип CLR, **изображения**, **текст**, **ntext**, или **sql_variant** тип данных. *SQLType* может быть SQL, определяемого пользователем типа.  
  
 **Value()** использует метод [!INCLUDE[tsql](../../includes/tsql-md.md)] неявно преобразовать оператор и пытается преобразовать результат выражения XQuery, сериализованное строковое представление, из типа данных XSD в соответствующий тип SQL, определяемое [!INCLUDE[tsql](../../includes/tsql-md.md)] преобразования. Дополнительные сведения о правилах приведения типов для оператора CONVERT см. в разделе [CAST и CONVERT &#40; Transact-SQL &#41; ](../../t-sql/functions/cast-and-convert-transact-sql.md).  
  
> [!NOTE]  
>  Для обеспечения высокой производительности вместо использования **value()** метод в предикат для сравнения с реляционным значением используйте **exist()** с **SQL: column()**. Это показано в следующем примере Г.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-using-the-value-method-against-an-xml-type-variable"></a>A. Использование метода value() над переменной типа xml  
 В следующем примере экземпляр XML хранится в переменной типа `xml`. Метод `value()` извлекает из переменной XML значение атрибута `ProductID`. Затем полученное значение присваивается переменной типа `int`.  
  
```  
DECLARE @myDoc xml  
DECLARE @ProdID int  
SET @myDoc = '<Root>  
<ProductDescription ProductID="1" ProductName="Road Bike">  
<Features>  
  <Warranty>1 year parts and labor</Warranty>  
  <Maintenance>3 year parts and labor extended maintenance is available</Maintenance>  
</Features>  
</ProductDescription>  
</Root>'  
  
SET @ProdID =  @myDoc.value('(/Root/ProductDescription/@ProductID)[1]', 'int' )  
SELECT @ProdID  
```  
  
 В результате возвращается значение 1.  
  
 Хотя экземпляр XML содержит только один атрибут `ProductID`, правила статической типизации требуют явно указать, что выражение пути возвращает единственное значение. Поэтому в конце выражения пути указан дополнительный знак `[1]`. Дополнительные сведения о статической типизации см. в разделе [XQuery и Статическая типизация](../../xquery/xquery-and-static-typing.md).  
  
### <a name="b-using-the-value-method-to-retrieve-a-value-from-an-xml-type-column"></a>Б. Использование метода value() для извлечения значения из столбца типа xml  
 Следующий запрос адресован **xml** столбец типа (`CatalogDescription`) в `AdventureWorks` базы данных. Запрос извлекает значения атрибутов `ProductModelID` из каждого экземпляра XML, который хранится в столбце.  
  
```  
SELECT CatalogDescription.value('             
    declare namespace PD="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";             
       (/PD:ProductDescription/@ProductModelID)[1]', 'int') AS Result             
FROM Production.ProductModel             
WHERE CatalogDescription IS NOT NULL             
ORDER BY Result desc             
```  
  
 Обратите внимание на следующие данные из предыдущего запроса:  
  
-   Для определения префикса пространства имен используется ключевое слово `namespace`.  
  
-   Требования к статической типизации в выражении пути обязывают в методе `[1]` добавлять `value()` в конце выражения пути, чтобы явно указать, что оно возвращает единственное значение.  
  
 Частичный результат:  
  
```  
-----------  
35           
34           
...  
```  
  
### <a name="c-using-the-value-and-exist-methods-to-retrieve-values-from-an-xml-type-column"></a>В. Использование методов value() и exist() для извлечения значений из столбца типа xml  
 В следующем примере показано использование обеих `value()` метод и [метода exist()](../../t-sql/xml/exist-method-xml-data-type.md) из **xml** тип данных. Метод `value()` извлекает значения атрибутов `ProductModelID` из экземпляров XML. Метод `exist()` в предложении `WHERE` фильтрует строки, извлеченные из таблицы.  
  
 Запрос извлекает идентификаторы моделей продуктов из экземпляров XML, которые среди прочих данных содержат сведения о гарантии (элемент <`Warranty`>). Условие в предложении `WHERE` приводит к тому, что метод `exist()` извлекает только те строки, которые соответствуют условию.  
  
```  
SELECT CatalogDescription.value('  
     declare namespace PD="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
           (/PD:ProductDescription/@ProductModelID)[1] ', 'int') as Result  
FROM  Production.ProductModel  
WHERE CatalogDescription.exist('  
     declare namespace PD="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
     declare namespace wm="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain";  
  
     /PD:ProductDescription/PD:Features/wm:Warranty ') = 1  
```  
  
 Обратите внимание на следующие данные из предыдущего запроса:  
  
-   Столбец `CatalogDescription` является типизированным XML-столбцом. Это означает, что с ним связан набор схем. В [прологе XQuery](../../xquery/modules-and-prologs-xquery-prolog.md), объявление пространства имен используется для определения префикса, который используется далее в тексте запроса.  
  
-   Если метод `exist()` возвращает значение `1` (TRUE), это значит, что экземпляр XML содержит дочерний элемент <`Warranty`>.  
  
-   Метод `value()` в предложении `SELECT` затем извлекает значения атрибутов `ProductModelID` в виде целых чисел.  
  
 Частичный результат:  
  
```  
Result       
-----------  
19           
23           
...  
```  
  
### <a name="d-using-the-exist-method-instead-of-the-value-method"></a>Г. Использование метода exist() вместо метода value()  
 Для увеличения производительности операции сравнения с реляционным значением вместо метода `value()` в предикате используйте метод `exist()` совместно с `sql:column()`. Например:  
  
```  
CREATE TABLE T (c1 int, c2 varchar(10), c3 xml)  
GO  
  
SELECT c1, c2, c3   
FROM T  
WHERE c3.value( '/root[1]/@a', 'integer') = c1  
GO  
```  
  
 Запрос будет выглядеть следующим образом:  
  
```  
SELECT c1, c2, c3   
FROM T  
WHERE c3.exist( '/root[@a=sql:column("c1")]') = 1  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [Добавление пространств имен в запросы с WITH XMLNAMESPACES](../../relational-databases/xml/add-namespaces-to-queries-with-with-xmlnamespaces.md)   
 [Сравнение типизированного и нетипизированного XML](../../relational-databases/xml/compare-typed-xml-to-untyped-xml.md)   
 [Создание экземпляров XML-данных](../../relational-databases/xml/create-instances-of-xml-data.md)   
 [методов типа данных xml](../../t-sql/xml/xml-data-type-methods.md)   
 [Язык модификации XML-данных &#40; Язык XML DML &#41;](../../t-sql/xml/xml-data-modification-language-xml-dml.md)  
  
  
