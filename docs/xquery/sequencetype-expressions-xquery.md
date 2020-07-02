---
title: Выражения SequenceType (XQuery) | Документация Майкрософт
description: Узнайте об экземпляре выражений XQuery SequenceType и приведите его как.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- SequenceType expressions
- instance of operator [XQuery]
- expressions [XQuery], SequenceType
- cast as operator
ms.assetid: ad3573da-d820-4d1c-81c4-a83c4640ce22
author: rothja
ms.author: jroth
ms.openlocfilehash: 909d3cb49879a94c466e58f83997e32c468d9df8
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85643362"
---
# <a name="sequencetype-expressions-xquery"></a>Выражения SequenceType (XQuery)
[!INCLUDE [SQL Server Azure SQL Database ](../includes/applies-to-version/sqlserver.md)]

  В XQuery значение всегда является последовательностью. Тип значения называется типом последовательности. Тип последовательности может использоваться в **экземпляре** выражения XQuery. Для обращения к типам в выражениях XQuery применяется синтаксис SequenceType, описанный в спецификации XQuery.  
  
 Имя атомарного типа также может использоваться в выражении **Cast как** XQuery. В [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] **экземпляр** и **приведенный как** выражения XQuery в секуенцетипес поддерживаются частично.  
  
## <a name="instance-of-operator"></a>Оператор instance of  
 **Экземпляр** оператора может использоваться для определения динамического или типа времени выполнения значения указанного выражения. Пример:  
  
```  
  
Expression instance of SequenceType[Occurrence indicator]  
```  
  
 Обратите внимание, что `instance of` оператор, `Occurrence indicator` указывает количество элементов в результирующей последовательности. Если он не указан, предполагается, что количество элементов равно 1. В [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] поддерживается только индикатор вхождения вопросительного знака (**?)** . Элемент **?** Индикатор вхождения указывает, что `Expression` может возвращать ноль или один элемент. Если **?** указан индикатор вхождения, `instance of` возвращает значение true, если `Expression` тип соответствует указанному `SequenceType` , независимо от того, `Expression` возвращает ли элемент Singleton или пустую последовательность.  
  
 Если **?** не указан индикатор вхождения, `sequence of` возвращает значение true, только если `Expression` тип соответствует `Type` указанному и `Expression` возвращает Singleton.  
  
 **Примечание** . Символ плюса ( **+** ) и индикаторы вхождения звездочки (**&#42;**) не поддерживаются в [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .  
  
 В следующих примерах показано использование**экземпляра** оператора XQuery.  
  
### <a name="example-a"></a>Пример A  
 В следующем примере создается переменная типа **XML** и задается запрос к ней. В выражении запроса используется оператор `instance of` для определения того, соответствует ли динамический тип значения, возвращаемого первым операндом, типу второго операнда.  
  
 Следующий запрос возвращает значение true, так как значение 125 является экземпляром указанного типа, **xs: integer**:  
  
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
  
### <a name="example-b"></a>Пример Б  
 В этом примере запрашиваются данные типизированного XML-столбца образца базы данных AdventureWorks. Сведения о типах предоставляет связанная с этим столбцом коллекция XML-схем.  
  
 В выражении **Data ()** возвращает типизированное значение атрибута ProductModelID, тип которого — xs: String в соответствии со схемой, связанной со столбцом. Поэтому оператор `instance of` возвращает значение True.  
  
```  
SELECT CatalogDescription.query('  
   declare namespace PD="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
   data(/PD:ProductDescription[1]/@ProductModelID) instance of xs:string  
') as Result  
FROM Production.ProductModel  
WHERE ProductModelID = 19  
```  
  
 Дополнительные сведения см. [в разделе Сравнение типизированного XML с нетипизированным XML](../relational-databases/xml/compare-typed-xml-to-untyped-xml.md).  
  
 Следующие запросы Усесебулеан `instance of` выражение, чтобы определить, имеет ли атрибут LocationID тип xs: integer:  
  
```  
SELECT Instructions.query('  
   declare namespace AWMI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
   /AWMI:root[1]/AWMI:Location[1]/@LocationID instance of attribute(LocationID,xs:integer)  
') as Result  
FROM Production.ProductModel  
WHERE ProductModelID=7  
```  
  
 Следующий запрос выполняется для типизированного XML-столбца CatalogDescription. Сведения о типах предоставляет связанная с этим столбцом коллекция XML-схем.  
  
 Для проверки того, возвращает ли выражение `element(ElementName, ElementType?)` узел с конкретным именем и типом, в операторе `instance of` используется выражение `/PD:ProductDescription[1]`.  
  
```  
SELECT CatalogDescription.query('  
     declare namespace PD="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
     /PD:ProductDescription[1] instance of element(PD:ProductDescription, PD:ProductDescription?)  
    ') as Result  
FROM  Production.ProductModel  
where ProductModelID=19  
```  
  
 Запрос возвращает значение True.  
  
### <a name="example-c"></a>Пример В  
 При использовании типов Union `instance of` выражение в [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] имеет ограничение: в частности, если тип элемента или атрибута является типом объединения, `instance of` может не определить точный тип. Таким образом, если атомарные типы, использованные в выражении SequenceType, не являются самым старшим родительским элементом фактического типа выражения в иерархии simpleType, запрос возвращает False. Иначе говоря, атомарные типы, указанные в выражении SequenceType, должны быть непосредственным дочерним элементом anySimpleType. Дополнительные сведения об иерархии типов см. [в разделе правила приведения типов в XQuery](../xquery/type-casting-rules-in-xquery.md).  
  
 В приведенном ниже запросе выполняется следующее:  
  
-   Создается коллекция XML-схем с определенным в ней объединенным типом, таким как целочисленный или строковый тип.  
  
-   Объявите типизированную **XML-** переменную с помощью коллекции XML-схем.  
  
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
  
 Следующий запрос возвращает False, потому что тип SequenceType, указанный в выражении `instance of`, не является самым старшим родительским типом фактического типа указанного выражения. То есть значение <`TestElement`> является целочисленным типом. а его самый старший родительский тип — xs:decimal. Однако он не указан в качестве второго операнда оператора `instance of`.  
  
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
 В этом примере сначала создается коллекция XML-схем, которая используется для ввода переменной **XML** . Затем запрашивается типизированная **XML-** переменная для иллюстрации `instance of` функциональных возможностей.  
  
 Следующая коллекция схем XML определяет простой тип, myType и элемент, <`root`> типа myType:  
  
```  
drop xml schema collection SC  
go  
CREATE XML SCHEMA COLLECTION SC AS '  
<schema xmlns="http://www.w3.org/2001/XMLSchema" targetNamespace="myNS" xmlns:ns="myNS"  
xmlns:s="https://schemas.microsoft.com/sqlserver/2004/sqltypes">  
      <import namespace="https://schemas.microsoft.com/sqlserver/2004/sqltypes"/>  
      <simpleType name="myType">  
           <restriction base="s:varchar">  
                  <maxLength value="20"/>  
            </restriction>  
      </simpleType>  
      <element name="root" type="ns:myType"/>  
</schema>'  
Go  
```  
  
 Теперь создайте типизированную **XML-** переменную и запросите ее:  
  
```  
DECLARE @var XML(SC)  
SET @var = '<root xmlns="myNS">My data</root>'  
SELECT @var.query('declare namespace sqltypes = "https://schemas.microsoft.com/sqlserver/2004/sqltypes";  
declare namespace ns="myNS";   
   data(/ns:root[1]) instance of ns:myType')  
go  
```  
  
 Так как тип myType наследуется по ограничению от типа varchar, который определен в схеме sqltypes, в этом случае оператор `instance of` также возвратит True.  
  
```  
DECLARE @var XML(SC)  
SET @var = '<root xmlns="myNS">My data</root>'  
SELECT @var.query('declare namespace sqltypes = "https://schemas.microsoft.com/sqlserver/2004/sqltypes";  
declare namespace ns="myNS";   
data(/ns:root[1]) instance of sqltypes:varchar?')  
go  
```  
  
### <a name="example-e"></a>Пример Д  
 В следующем примере выражение получает одно из значений атрибута IDREFS, после чего с помощью оператора `instance of` определяется, имеет ли это значение тип IDREF. В примере выполняются следующие действия.  
  
-   Создает коллекцию XML-схем, в которой `Customer` элемент> <имеет атрибут типа **OrderList** IDREFS, а `Order` элемент <> имеет атрибут типа идентификатора **OrderID** .  
  
-   Создает типизированную переменную **XML** и присваивает ей образец XML-экземпляра.  
  
-   Задается запрос, который должен быть выполнен для переменной. Выражение запроса получает значение идентификатора первого заказа из атрибута OrderList атрибута Type первого <`Customer`>. Это значение имеет тип IDREF. Таким образом, оператор `instance of` возвращает True.  
  
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
  
-   Типы последовательностей **Schema-Element ()** и **Schema-Attribute ()** не поддерживаются для сравнения с `instance of` оператором.  
  
-   Полные последовательности, например `(1,2) instance of xs:integer*`, не поддерживаются.  
  
-   При использовании вида последовательности **element ()** , указывающего имя типа, например `element(ElementName, TypeName)` , тип должен быть дополнен вопросительным знаком (?). Например, инструкция `element(Title, xs:string?)` указывает, что элемент может иметь значение NULL. [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]не поддерживает обнаружение во время выполнения свойства **xsi: nil** с помощью `instance of` .  
  
-   Если значение `Expression` извлекается из элемента или атрибута, типизированного как объединенный тип, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] может идентифицировать только примитивный непроизводный тип, от которого произведен тип значения. Например, если для <`e1`> определен статический тип (xs: integer | xs: String), следующий пример вернет значение false.  
  
    ```  
    data(<e1>123</e1>) instance of xs:integer  
    ```  
  
     Однако выражение `data(<e1>123</e1>) instance of xs:decimal` возвратит True.  
  
-   Для типов последовательности операций **обработки ()** и **document-node ()** разрешены только формы без аргументов. Например, форма `processing-instruction()` поддерживается, но форма `processing-instruction('abc')` недопустима.  
  
## <a name="cast-as-operator"></a>Оператор cast as  
 Выражение **cast as** можно использовать для преобразования значения в конкретный тип данных. Пример:  
  
```  
  
Expression cast as  AtomicType?  
```  
  
 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] требует, чтобы после операнда `AtomicType` был указан вопросительный знак (?). Например, как показано в следующем запросе, `"2" cast as xs:integer?` Преобразует строковое значение в целое число:  
  
```  
declare @x xml  
set @x=''  
select @x.query('"2" cast as xs:integer?')  
```  
  
 В следующем запросе **Data ()** возвращает типизированное значение атрибута ProductModelID, строковый тип. `cast as`Оператор преобразует значение в тип xs: integer.  
  
```  
WITH XMLNAMESPACES ('https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription' AS PD)  
SELECT CatalogDescription.query('  
   data(/PD:ProductDescription[1]/@ProductModelID) cast as xs:integer?  
') as Result  
FROM Production.ProductModel  
WHERE ProductModelID = 19  
```  
  
 Явное использование **Data ()** в этом запросе не требуется. Оператор `cast as` неявно выполняет атомизацию входного выражения.  
  
### <a name="constructor-functions"></a>Функции-конструкторы  
 Можно использовать функции-конструкторы атомарных типов. Например, вместо использования `cast as` оператора `"2" cast as xs:integer?` можно использовать функцию конструктора **xs: integer ()** , как показано в следующем примере:  
  
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
  
 Конструкторы можно применять и при работе с пользовательскими атомарными типами. Например, если коллекция XML-схем, связанная с типом данных XML, определяет простой тип, то для возврата значения этого типа можно использовать конструктор **MyType ()** .  
  
#### <a name="implementation-limitations"></a>Ограничения реализации  
  
-   Выражения XQuery **типесвитч**, **casted**и **Treat** не поддерживаются.  
  
-   **для приведения AS** требуется вопросительный знак (?) После атомарного типа.  
  
-   **xs: QName** не поддерживается в качестве типа для приведения. Вместо этого используйте **Расширенный-QName** .  
  
-   для **xs: Date**, **xs: Time**и **xs: DateTime** требуется часовой пояс, обозначенный буквой Z.  
  
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
  
## <a name="see-also"></a>См. также  
 [Выражения XQuery](../xquery/xquery-expressions.md)   
 [Введите System &#40;XQuery&#41;](../xquery/type-system-xquery.md)  
  
  
