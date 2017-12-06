---
title: "Выражения SequenceType (XQuery) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: 
ms.component: xquery
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to: SQL Server
dev_langs: XML
helpviewer_keywords:
- SequenceType expressions
- instance of operator [XQuery]
- expressions [XQuery], SequenceType
- cast as operator
ms.assetid: ad3573da-d820-4d1c-81c4-a83c4640ce22
caps.latest.revision: "25"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: a3c4cb7ecd33427d382704bccc19dbae0d22cc84
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/05/2017
---
# <a name="sequencetype-expressions-xquery"></a>Выражения SequenceType (XQuery)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  В XQuery значение всегда является последовательностью. Тип значения называется типом последовательности. Тип последовательности можно использовать в **экземпляр** выражения XQuery. Для обращения к типам в выражениях XQuery применяется синтаксис SequenceType, описанный в спецификации XQuery.  
  
 Имя атомарного типа также могут использоваться в **приведенное** выражения XQuery. В [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], **экземпляр** и **приведенное** XQuery над типами последовательности поддерживаются частично.  
  
## <a name="instance-of-operator"></a>Оператор instance of  
 **Экземпляр** оператор можно использовать для определения типа динамических или время выполнения значения указанного выражения. Например:  
  
```  
  
Expression instance of SequenceType[Occurrence indicator]  
```  
  
 Обратите внимание, что `instance of` оператор, `Occurrence indicator`, указывает количество элементов, количество элементов в результирующей последовательности. Если он не указан, предполагается, что количество элементов равно 1. В [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], вопросительным знаком (**?)**  поддерживается признака вхождения. **?** Указывает, что признак встречаемости `Expression` может возвращать ноль или один элемент. Если **?** указан признак встречаемости, `instance of` возвращает значение True при `Expression` соответствует указанному типу `SequenceType`независимо от того, следует ли `Expression` возвращает единственный элемент или пустую последовательность.  
  
 Если **?** Признак встречаемости не указан, `sequence of` возвращает значение True, только если `Expression` введите совпадений `Type` указанного и `Expression` возвращает единственное значение.  
  
 **Примечание** знак плюса (**+**) или звездочку (**\***) признаки встречаемости не поддерживаются в [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
 Следующие примеры иллюстрируют использование**экземпляр** оператор языка XQuery.  
  
### <a name="example-a"></a>Пример A  
 В следующем примере создается **xml** переменной типа и определяет запрос к ней. В выражении запроса используется оператор `instance of` для определения того, соответствует ли динамический тип значения, возвращаемого первым операндом, типу второго операнда.  
  
 Следующий запрос возвращает True, потому что значение 125 является экземпляром указанного типа **xs: Integer**:  
  
```  
declare @x xml  
set @x=''  
select @x.query('125 instance of xs:integer')  
go  
```  
  
 Следующий запрос возвращает True, потому что значение, возвращаемое выражением /a[1], то есть первым операндом, является элементом.  
  
```  
declare @x xml  
set @x='<a>1</a>'  
select @x.query('/a[1] instance of element()')  
go  
```  
  
 Подобно этому, в следующем запросе оператор `instance of` также возвращает True, потому что тип значения первого выражения является атрибутом:  
  
```  
declare @x xml  
set @x='<a attr1="x">1</a>'  
select @x.query('/a[1]/@attr1 instance of attribute()')  
go  
```  
  
 В следующем примере выражение `data(/a[1]` возвращает атомарное значение, типизированное как xdt:untypedAtomic. Поэтому оператор `instance of` возвращает значение True.  
  
```  
declare @x xml  
set @x='<a>1</a>'  
select @x.query('data(/a[1]) instance of xdt:untypedAtomic')  
go  
```  
  
 В следующем запросе выражение `data(/a[1]/@attrA` возвращает нетипизированное атомное значение. Поэтому оператор `instance of` возвращает значение True.  
  
```  
declare @x xml  
set @x='<a attrA="X">1</a>'  
select @x.query('data(/a[1]/@attrA) instance of xdt:untypedAtomic')  
go  
```  
  
### <a name="example-b"></a>Пример B-адреса  
 В этом примере запрашиваются данные типизированного XML-столбца образца базы данных AdventureWorks. Сведения о типах предоставляет связанная с этим столбцом коллекция XML-схем.  
  
 В выражении **data()** возвращает типизированное значение атрибута ProductModelID, типом которого является xs: String в соответствии со схемой, связанного со столбцом. Поэтому оператор `instance of` возвращает значение True.  
  
```  
SELECT CatalogDescription.query('  
   declare namespace PD="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
   data(/PD:ProductDescription[1]/@ProductModelID) instance of xs:string  
') as Result  
FROM Production.ProductModel  
WHERE ProductModelID = 19  
```  
  
 Дополнительные сведения см. в статье [Сравнение типизированного и нетипизированного XML](../relational-databases/xml/compare-typed-xml-to-untyped-xml.md).  
  
 Следующие запросы логическое `instance of` выражение, чтобы определить, является ли атрибут LocationID тип xs: Integer:  
  
```  
SELECT Instructions.query('  
   declare namespace AWMI="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
   /AWMI:root[1]/AWMI:Location[1]/@LocationID instance of attribute(LocationID,xs:integer)  
') as Result  
FROM Production.ProductModel  
WHERE ProductModelID=7  
```  
  
 Следующий запрос выполняется для типизированного XML-столбца CatalogDescription. Сведения о типах предоставляет связанная с этим столбцом коллекция XML-схем.  
  
 Для проверки того, возвращает ли выражение `element(ElementName, ElementType?)` узел с конкретным именем и типом, в операторе `instance of` используется выражение `/PD:ProductDescription[1]`.  
  
```  
SELECT CatalogDescription.query('  
     declare namespace PD="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
     /PD:ProductDescription[1] instance of element(PD:ProductDescription, PD:ProductDescription?)  
    ') as Result  
FROM  Production.ProductModel  
where ProductModelID=19  
```  
  
 Запрос возвращает значение True.  
  
### <a name="example-c"></a>Пример В  
 При использовании объединенных типов `instance of` выражения в [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] имеет следующее ограничение: в частности, в том случае, если тип элемента или атрибута является типом объединения `instance of` не всегда может определить точный тип. Таким образом, если атомарные типы, использованные в выражении SequenceType, не являются самым старшим родительским элементом фактического типа выражения в иерархии simpleType, запрос возвращает False. Иначе говоря, атомарные типы, указанные в выражении SequenceType, должны быть непосредственным дочерним элементом anySimpleType. Сведения об иерархии типов см. в разделе [правила приведения типов в языке XQuery](../xquery/type-casting-rules-in-xquery.md).  
  
 В приведенном ниже запросе выполняется следующее:  
  
-   Создается коллекция XML-схем с определенным в ней объединенным типом, таким как целочисленный или строковый тип.  
  
-   Объявляется типизированная **xml** переменной с помощью коллекции XML-схем.  
  
-   Этой переменной назначается экземпляр XML.  
  
-   Выполняется запрос переменной, чтобы продемонстрировать работу оператора `instance of` с объединенным типом.  
  
 Запрос является таковым:  
  
```  
CREATE XML SCHEMA COLLECTION MyTestSchema AS '  
<schema xmlns="http://www.w3.org/2001/XMLSchema" targetNamespace="http://ns" xmlns:ns="http://ns">  
<simpleType name="MyUnionType">  
<union memberTypes="integer string"/>  
</simpleType>  
<element name="TestElement" type="ns:MyUnionType"/>  
</schema>'  
Go  
```  
  
 Следующий запрос возвращает False, потому что тип SequenceType, указанный в выражении `instance of`, не является самым старшим родительским типом фактического типа указанного выражения. Иначе говоря, значение <`TestElement`> имеет целочисленный тип, а его самый старший родительский тип — xs:decimal. Однако он не указан в качестве второго операнда оператора `instance of`.  
  
```  
SET QUOTED_IDENTIFIER ON  
DECLARE @var XML(MyTestSchema)  
  
SET @var = '<TestElement xmlns="http://ns">123</TestElement>'  
  
SELECT @var.query('declare namespace ns="http://ns"   
   data(/ns:TestElement[1]) instance of xs:integer')  
go  
```  
  
 Так как самым старшим родительским типом по отношению к xs:integer является тип xs:decimal, то, если в этом запросе указать в качестве SequenceType тип xs:decimal, запрос возвратит True.  
  
```  
SET QUOTED_IDENTIFIER ON  
DECLARE @var XML(MyTestSchema)  
SET @var = '<TestElement xmlns="http://ns">123</TestElement>'  
SELECT @var.query('declare namespace ns="http://ns"     
   data(/ns:TestElement[1]) instance of xs:decimal')  
go  
```  
  
### <a name="example-d"></a>Пример Г  
 В этом примере вы сначала создать коллекцию XML-схем и использовать его для ввода **xml** переменной. Типизированный **xml** переменной затем выполняется запрос, чтобы проиллюстрировать `instance of` функциональные возможности.  
  
 Следующая коллекция XML-схем определяет простой тип myType и элемент <`root`> типа myType:  
  
```  
drop xml schema collection SC  
go  
CREATE XML SCHEMA COLLECTION SC AS '  
<schema xmlns="http://www.w3.org/2001/XMLSchema" targetNamespace="myNS" xmlns:ns="myNS"  
xmlns:s="http://schemas.microsoft.com/sqlserver/2004/sqltypes">  
      <import namespace="http://schemas.microsoft.com/sqlserver/2004/sqltypes"/>  
      <simpleType name="myType">  
           <restriction base="s:varchar">  
                  <maxLength value="20"/>  
            </restriction>  
      </simpleType>  
      <element name="root" type="ns:myType"/>  
</schema>'  
Go  
```  
  
 Теперь создайте типизированную **xml** переменной и запросов:  
  
```  
DECLARE @var XML(SC)  
SET @var = '<root xmlns="myNS">My data</root>'  
SELECT @var.query('declare namespace sqltypes = "http://schemas.microsoft.com/sqlserver/2004/sqltypes";  
declare namespace ns="myNS";   
   data(/ns:root[1]) instance of ns:myType')  
go  
```  
  
 Так как тип myType наследуется по ограничению от типа varchar, который определен в схеме sqltypes, в этом случае оператор `instance of` также возвратит True.  
  
```  
DECLARE @var XML(SC)  
SET @var = '<root xmlns="myNS">My data</root>'  
SELECT @var.query('declare namespace sqltypes = "http://schemas.microsoft.com/sqlserver/2004/sqltypes";  
declare namespace ns="myNS";   
data(/ns:root[1]) instance of sqltypes:varchar?')  
go  
```  
  
### <a name="example-e"></a>Пример Д  
 В следующем примере выражение получает одно из значений атрибута IDREFS, после чего с помощью оператора `instance of` определяется, имеет ли это значение тип IDREF. В примере выполняются следующие действия.  
  
-   Создает коллекцию схем XML, в котором <`Customer`> элемент имеет **OrderList** атрибут типа IDREFS и <`Order`> элемент имеет **OrderID** идентификатор типа атрибута.  
  
-   Создается типизированная **xml** переменной и присваивает ей экземпляр образец XML-файла.  
  
-   Задается запрос, который должен быть выполнен для переменной. Выражение запроса получает идентификатор первого заказа из атрибута OrderList (типа IDREFS) первого элемента <`Customer`>. Это значение имеет тип IDREF. Таким образом, оператор `instance of` возвращает True.  
  
```  
create xml schema collection SC as  
'<schema xmlns="http://www.w3.org/2001/XMLSchema" xmlns:Customers="Customers" targetNamespace="Customers">  
            <element name="Customers" type="Customers:CustomersType"/>  
            <complexType name="CustomersType">  
                        <sequence>  
                            <element name="Customer" type="Customers:CustomerType" minOccurs="0" maxOccurs="unbounded" />  
                        </sequence>  
            </complexType>  
             <complexType name="OrderType">  
                <sequence minOccurs="0" maxOccurs="unbounded">  
                            <choice>  
                                <element name="OrderValue" type="integer" minOccurs="0" maxOccurs="unbounded"/>  
                            </choice>  
                </sequence>                                             
                <attribute name="OrderID" type="ID" />  
            </complexType>  
  
            <complexType name="CustomerType">  
                <sequence minOccurs="0" maxOccurs="unbounded">  
                            <choice>  
                                <element name="spouse" type="string" minOccurs="0" maxOccurs="unbounded"/>  
                                <element name="Order" type="Customers:OrderType" minOccurs="0" maxOccurs="unbounded"/>  
                            </choice>  
                </sequence>                                             
                <attribute name="CustomerID" type="string" />  
                <attribute name="OrderList" type="IDREFS" />  
            </complexType>  
 </schema>'  
go  
declare @x xml(SC)  
set @x='<CustOrders:Customers xmlns:CustOrders="Customers">  
                <Customer CustomerID="C1" OrderList="OrderA OrderB"  >  
                              <spouse>Jenny</spouse>  
                                <Order OrderID="OrderA"><OrderValue>11</OrderValue></Order>  
                                <Order OrderID="OrderB"><OrderValue>22</OrderValue></Order>  
  
                </Customer>  
                <Customer CustomerID="C2" OrderList="OrderC OrderD" >  
                                <spouse>John</spouse>  
                                <Order OrderID="OrderC"><OrderValue>33</OrderValue></Order>  
                                <Order OrderID="OrderD"><OrderValue>44</OrderValue></Order>  
  
                        </Customer>  
                <Customer CustomerID="C3"  OrderList="OrderE OrderF" >  
                                <spouse>Jane</spouse>  
                                <Order OrderID="OrderE"><OrderValue>55</OrderValue></Order>  
                                <Order OrderID="OrderF"><OrderValue>55</OrderValue></Order>  
                </Customer>  
                <Customer CustomerID="C4"  OrderList="OrderG"  >  
                                <spouse>Tim</spouse>  
                                <Order OrderID="OrderG"><OrderValue>66</OrderValue></Order>  
                        </Customer>  
                <Customer CustomerID="C5"  >  
                </Customer>  
                <Customer CustomerID="C6" >  
                </Customer>  
                <Customer CustomerID="C7"  >  
                </Customer>  
</CustOrders:Customers>'  
  
select @x.query(' declare namespace CustOrders="Customers";   
 data(CustOrders:Customers/Customer[1]/@OrderList)[1] instance of xs:IDREF ? ') as XML_result  
```  
  
### <a name="implementation-limitations"></a>Ограничения реализации  
 Существуют следующие ограничения:  
  
-   **Элемент_схемы()** и **schema-attribute()** типы последовательности не поддерживаются для сравнения с `instance of` оператор.  
  
-   Полные последовательности, например `(1,2) instance of xs:integer*`, не поддерживаются.  
  
-   Если вы используете один из видов **element()** типа, указывающее имя типа, такие как последовательности `element(ElementName, TypeName)`, типа должны быть дополнены знак вопроса (?). Например, инструкция `element(Title, xs:string?)` указывает, что элемент может иметь значение NULL. [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]не поддерживает во время выполнения обнаружения **xsi: nil** свойства с помощью `instance of`.  
  
-   Если значение `Expression` извлекается из элемента или атрибута, типизированного как объединенный тип, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] может идентифицировать только примитивный непроизводный тип, от которого произведен тип значения. Например, если элемент <`e1`> определен как статический тип (xs:integer | xs:string), следующее выражение возвратит False.  
  
    ```  
    data(<e1>123</e1>) instance of xs:integer  
    ```  
  
     Однако выражение `data(<e1>123</e1>) instance of xs:decimal` возвратит True.  
  
-   Для **processing-instruction()** и **document-node()** типов последовательностей разрешены только формы без аргументов. Например, форма `processing-instruction()` поддерживается, но форма `processing-instruction('abc')` недопустима.  
  
## <a name="cast-as-operator"></a>Оператор cast as  
 **Приведенное** выражение может использоваться для преобразования значения в определенный тип данных. Например:  
  
```  
  
Expression cast as  AtomicType?  
```  
  
 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] требует, чтобы после операнда `AtomicType` был указан вопросительный знак (?). Например, как показано в следующем запросе `"2" cast as xs:integer?` Преобразует строковое значение в целое число:  
  
```  
declare @x xml  
set @x=''  
select @x.query('"2" cast as xs:integer?')  
```  
  
 В следующем запросе **data()** возвращает типизированное значение атрибута ProductModelID, строкового типа. `cast as`Оператор преобразует значение в xs: Integer.  
  
```  
WITH XMLNAMESPACES ('http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription' AS PD)  
SELECT CatalogDescription.query('  
   data(/PD:ProductDescription[1]/@ProductModelID) cast as xs:integer?  
') as Result  
FROM Production.ProductModel  
WHERE ProductModelID = 19  
```  
  
 Явное использование **data()** в этот запрос не требуется. Оператор `cast as` неявно выполняет атомизацию входного выражения.  
  
### <a name="constructor-functions"></a>Функции-конструкторы  
 Можно использовать функции-конструкторы атомарных типов. Например, вместо использования `cast as` оператор, `"2" cast as xs:integer?`, можно использовать **xs:integer()** функции конструктора, как показано в следующем примере:  
  
```  
declare @x xml  
set @x=''  
select @x.query('xs:integer("2")')  
```  
  
 Следующий код возвращает значение xs:date, равное 2000-01-01Z:  
  
```  
declare @x xml  
set @x=''  
select @x.query('xs:date("2000-01-01Z")')  
```  
  
 Конструкторы можно применять и при работе с пользовательскими атомарными типами. Например, если коллекции XML-схем, связанные с типом данных XML определяет простой тип, **myType()** конструктор может использоваться для возврата значения этого типа.  
  
#### <a name="implementation-limitations"></a>Ограничения реализации  
  
-   Выражения языка XQuery **typeswitch**, **приводимым**, и **обрабатывать** не поддерживаются.  
  
-   **приведенное** требуется знак вопроса (?) После атомарного типа.  
  
-   **xs: QName** не поддерживается как для приведения. Используйте **expanded-QName** вместо него.  
  
-   **xs: Date**, **xs: time**, и **xs: DateTime** требуют часовой пояс, который обозначается Z.  
  
     Например, следующий запрос завершается неудачей, потому что часовой пояс не указан:  
  
    ```  
    DECLARE @var XML  
    SET @var = ''  
    SELECT @var.query(' <a>{xs:date("2002-05-25")}</a>')  
    go  
    ```  
  
     Если дополнить значение признаком часового пояса Z, запрос выполняется успешно:  
  
    ```  
    DECLARE @var XML  
    SET @var = ''  
    SELECT @var.query(' <a>{xs:date("2002-05-25Z")}</a>')  
    go  
    ```  
  
     Результат:  
  
    ```  
    <a>2002-05-25Z</a>  
    ```  
  
## <a name="see-also"></a>См. также:  
 [Выражения языка XQuery](../xquery/xquery-expressions.md)   
 [Система типов &#40; XQuery &#41;](../xquery/type-system-xquery.md)  
  
  
