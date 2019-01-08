---
title: Сопоставление типов последовательности | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- sequence type matching [XQuery]
- XQuery, sequence type matching
ms.assetid: 8c56fb69-ca04-4aba-b55a-64ae216c492d
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 3df2ef3f14cb8ca4fd7e7bcf5799b6966c16dc10
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/28/2018
ms.locfileid: "52511447"
---
# <a name="type-system---sequence-type-matching"></a>Система типов — сопоставление типов последовательности
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Значением выражения языка XQuery всегда является последовательность из нуля или более элементов. Элемент может быть атомарным значением или узлом. Тип элементов последовательности соответствует типу результатов, возвращаемых выражением запроса. Пример:  
  
-   Если значение выражения является атомарным, может понадобиться выяснить, имеет ли оно тип integer, decimal или string.  
  
-   Если значение выражения является XML-узлом, может понадобиться выяснить, является ли оно комментарием, инструкцией по обработке или текстовым узлом.  
  
-   Может возникнуть необходимость выяснить, является ли результат выражения XML-элементом или узлом атрибута с заданным именем и типом.  
  
 Для сопоставления типов элементов последовательности можно использовать логический оператор `instance of`. Дополнительные сведения о `instance of` выражения, см. в разделе [выражения SequenceType &#40;XQuery&#41;](../xquery/sequencetype-expressions-xquery.md).  
  
## <a name="comparing-the-atomic-value-type-returned-by-an-expression"></a>Сравнение типов атомарных значений, возвращенных выражением  
 Определить тип значения в последовательности может понадобиться в том случае, если выражение возвращает последовательность атомарных значений. В следующем примере показано использование синтаксиса типа последовательности для определения типа атомарного значения, возвращаемого выражением.  
  
### <a name="example-determining-whether-a-sequence-is-empty"></a>Пример Определение пустоты последовательности  
 **Empty()** тип последовательности, которая может использоваться в выражении типа последовательности для определения последовательности, возвращаемых в указанном выражении пустую последовательность.  
  
 В следующем примере XML-схема допускает возможность того, что элемент <`root`> пуст:  
  
```  
CREATE XML SCHEMA COLLECTION SC AS N'  
<schema xmlns="https://www.w3.org/2001/XMLSchema">  
      <element name="root" nillable="true" type="byte"/>  
</schema>'  
GO  
```  
  
 Теперь, если типизированный XML-экземпляр указывает значение элемента <`root`>, выражение `instance of empty()` возвращает значение False.  
  
```  
DECLARE @var XML(SC1)  
SET @var = '<root>1</root>'  
-- The following returns False  
SELECT @var.query('data(/root[1]) instance of  empty() ')  
GO  
```  
  
 Если в экземпляре элемент <`root`> пуст, его значением является пустая последовательность, а выражение `instance of empty()` возвращает значение True.  
  
```  
DECLARE @var XML(SC)  
SET @var = '<root xsi:nil="true" xmlns:xsi="https://www.w3.org/2001/XMLSchema-instance" />'  
SELECT @var.query('data(/root[1]) instance of  empty() ')  
GO  
```  
  
### <a name="example-determining-the-type-of-an-attribute-value"></a>Пример Определение типа значения атрибута  
 Иногда требуется выяснить тип последовательности, возвращаемой выражением, до начала обработки. Например, узел может быть определен в XML-схеме с типом union. В следующем примере XML-схема в коллекции определяет атрибут `a` как имеющий объединенный тип данных, значение которого может иметь десятичный или строковый тип данных.  
  
```  
-- Drop schema collection if it exists.  
-- DROP XML SCHEMA COLLECTION SC.  
-- GO  
CREATE XML SCHEMA COLLECTION SC AS N'  
<schema xmlns="https://www.w3.org/2001/XMLSchema">  
  <element name="root">  
    <complexType>  
       <sequence/>  
         <attribute name="a">  
            <simpleType>  
               <union memberTypes="decimal string"/>  
            </simpleType>  
         </attribute>  
     </complexType>  
  </element>  
</schema>'  
GO  
```  
  
 Перед обработкой типизированного XML-экземпляра может понадобиться определить тип данных значения атрибута `a`. В следующем примере значение атрибута `a` имеет десятичный тип данных. Следовательно, выражение `, instance of xs:decimal` возвращает True.  
  
```  
DECLARE @var XML(SC)  
SET @var = '<root a="2.5"/>'  
SELECT @var.query('data((/root/@a)[1]) instance of xs:decimal')  
GO  
```  
  
 Теперь изменим тип значения атрибута `a` на строковый. Выражение `instance of xs:string` возвратит значение True.  
  
```  
DECLARE @var XML(SC)  
SET @var = '<root a="Hello"/>'  
SELECT @var.query('data((/root/@a)[1]) instance of xs:string')  
GO  
```  
  
### <a name="example-cardinality-in-sequence-expressions"></a>Пример Количество элементов выражения последовательности  
 В данном примере показывается влияние количества элементов в выражении последовательности. В представленной ниже XML-схеме определяется элемент <`root`> типа byte, который может быть пустым.  
  
```  
CREATE XML SCHEMA COLLECTION SC AS N'  
<schema xmlns="https://www.w3.org/2001/XMLSchema">  
      <element name="root" nillable="true" type="byte"/>  
</schema>'  
GO  
```  
  
 В следующем примере выражение `instance of` возвращает значение True, так как результатом выполнения выражения является одиночный элемент типа byte.  
  
```  
DECLARE @var XML(SC)  
SET @var = '<root>111</root>'  
SELECT @var.query('data(/root[1]) instance of  xs:byte ')   
GO  
```  
  
 При очистке элемента <`root`> его значением станет пустая последовательность. Поэтому выражение `/root[1]` возвращает пустую последовательность. Следовательно, выражение `instance of xs:byte` возвращает значение False. Обратите внимание, что количество элементов по умолчанию в данном случае равно 1.  
  
```  
DECLARE @var XML(SC)  
SET @var = '<root xsi:nil="true" xmlns:xsi="https://www.w3.org/2001/XMLSchema-instance"></root>'  
SELECT @var.query('data(/root[1]) instance of  xs:byte ')   
GO  
-- result = false  
```  
  
 Если количество элементов указывается с добавлением признака вхождения (`?`), выражение последовательности возвращает значение True.  
  
```  
DECLARE @var XML(SC)  
SET @var = '<root xsi:nil="true" xmlns:xsi="https://www.w3.org/2001/XMLSchema-instance"></root>'  
SELECT @var.query('data(/root[1]) instance of  xs:byte? ')   
GO  
-- result = true  
```  
  
 Обратите внимание, что проверка типа в выражении последовательности проходит в два этапа:  
  
1.  Вначале определяется, совпадает ли тип выражения с указанным типом.  
  
2.  При совпадении типов выражений производится проверка совпадения количества возвращенных выражением элементов с указанным значением признака вхождения.  
  
 Если обе проверки дают положительные результаты, выражение `instance of` возвращает значение True.  
  
### <a name="example-querying-against-an-xml-type-column"></a>Пример Запрос к столбцу типа xml   
 В следующем примере запрос задается для столбца Instructions **xml** введите [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] базы данных. Это типизированный XML-столбец, так как имеется связанная с ним схема. Схема XML определяет целочисленный атрибут `LocationID`. Таким образом, в выражении последовательности `instance of xs:integer?` возвращает значение True.  
  
```  
SELECT Instructions.query('   
declare namespace AWMI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";   
data(/AWMI:root[1]/AWMI:Location[1]/@LocationID) instance of xs:integer?') as Result   
FROM Production.ProductModel   
WHERE ProductModelID = 7  
```  
  
## <a name="comparing-the-node-type-returned-by-an-expression"></a>Сравнение типов узлов, возвращаемых выражением  
 Определить тип узла в последовательности может понадобиться в том случае, если выражение возвращает последовательность узлов. В следующем примере показано использование синтаксиса типа последовательности для определения типа узла, возвращаемого выражением. Можно использовать следующие типы последовательности:  
  
-   **Item()** -соответствует любому элементу в последовательности.  
  
-   **node()** -определяет, является ли последовательность узлом.  
  
-   **processing-instruction()** -определяет, возвращает ли выражение инструкцию по обработке.  
  
-   **comment()** -определяет, возвращает ли выражение комментарий.  
  
-   **document-node()** -определяет, возвращает ли выражение узел документа.  
  
 Следующий пример иллюстрирует эти типы последовательностей.  
  
### <a name="example-using-sequence-types"></a>Пример Использование типов последовательности  
 В этом примере выполняется несколько запросов к нетипизированной xml-переменной. В этих запросах демонстрируется использование указанных типов последовательности.  
  
```  
DECLARE @var XML  
SET @var = '<?xml-stylesheet href="someValue" type="text/xsl" ?>  
<root>text node  
  <!-- comment 1 -->   
  <a>Data a</a>  
  <!-- comment  2 -->  
</root>'  
```  
  
 В первом запросе выражение возвращает типизированное значение элемента <`a`>. Во втором запросе выражение возвращает элемент <`a`>. Оба результата являются элементами. Поэтому оба запроса возвращают значение True.  
  
```  
SELECT @var.query('data(/root[1]/a[1]) instance of item()')  
SELECT @var.query('/root[1]/a[1] instance of item()')  
```  
  
 Все выражения языка XQuery, содержащиеся в трех следующих запросах, возвращают дочерний узел элемента <`root`>. Поэтому выражение типа последовательности `instance of node()` возвращает значение True, а два других выражения (`instance of text()` и `instance of document-node()`) — значение False.  
  
```  
SELECT @var.query('(/root/*)[1] instance of node()')  
SELECT @var.query('(/root/*)[1] instance of text()')  
SELECT @var.query('(/root/*)[1] instance of document-node()')   
```  
  
 В следующем примере выражение `instance of document-node()` возвращает значение True, так как родителем элемента <`root`> является узел документа.  
  
```  
SELECT @var.query('(/root/..)[1] instance of document-node()') -- true  
```  
  
 В следующем запросе выражение получает первый узел XML-экземпляра. Так как он является узлом инструкции по обработке, выражение `instance of processing-instruction()` возвращает значение True.  
  
```  
SELECT @var.query('(/node())[1] instance of processing-instruction()')  
```  
  
### <a name="implementation-limitations"></a>Ограничения реализации  
 Особые ограничения:  
  
-   **document-node()** с типом содержимого синтаксис не поддерживается.  
  
-   **processing-instruction(Name)** синтаксис не поддерживается.  
  
## <a name="element-tests"></a>Проверки элемента  
 Проверка элемента используется для сопоставления узла элемента, возвращаемого выражением, с узлом элемента с указанным именем и типом. Можно использовать следующие проверки элемента:  
  
```  
element ()  
element(ElementName)  
element(ElementName, ElementType?)   
element(*, ElementType?)  
```  
  
## <a name="attribute-tests"></a>Проверки атрибута  
 В ходе проверки атрибута выясняется, является ли атрибут, возвращенный выражением, узлом. Можно использовать следующие проверки атрибутов.  
  
 `attribute()`  
  
 `attribute(AttributeName)`  
  
 `attribute(AttributeName, AttributeType)`  
  
## <a name="test-examples"></a>Примеры проверки  
 В представленных ниже примерах приведены ситуации, в которых можно использовать проверки элемента и атрибута.  
  
### <a name="example-a"></a>Пример A  
 Представленная XML-схема определяет сложный тип данных `CustomerType`, в котором элементы <`firstName`> и <`lastName`> являются необязательными. В указанном XML-экземпляре может понадобиться определить, существует ли запись, содержащая фамилию определенного покупателя.  
  
```  
CREATE XML SCHEMA COLLECTION SC AS N'  
<schema xmlns="https://www.w3.org/2001/XMLSchema"  
targetNamespace="myNS" xmlns:ns="myNS">  
  <complexType name="CustomerType">  
     <sequence>  
        <element name="firstName" type="string" minOccurs="0"   
                  nillable="true" />  
        <element name="lastName" type="string" minOccurs="0"/>  
     </sequence>  
  </complexType>  
  <element name="customer" type="ns:CustomerType"/>  
</schema>  
'  
GO  
DECLARE @var XML(SC)  
SET @var = '<x:customer xmlns:x="myNS">  
<firstName>SomeFirstName</firstName>  
<lastName>SomeLastName</lastName>  
</x:customer>'  
```  
  
 В представленном ниже запросе выражение `instance of element (firstName)` используется для определения, является ли элемент <`firstName`> первым дочерним элементом узла <`customer`>. Если является, выражение возвращает значение True.  
  
```  
SELECT @var.query('declare namespace x="myNS";   
     (/x:customer/*)[1] instance of element (firstName)')  
GO  
```  
  
 Если удалить элемент <`firstName`> из экземпляра, выражение возвращает значение False.  
  
 Также можно использовать следующее:  
  
-   Синтаксис типа последовательности `element(ElementName, ElementType?)`, представленный в следующем запросе. Указанный запрос относится к узлу элемента с именем `firstName` и типом `xs:string`.  
  
    ```  
    SELECT @var.query('declare namespace x="myNS";   
    (/x:customer/*)[1] instance of element (firstName, xs:string?)')  
    ```  
  
-   Синтаксис типа последовательности `element(*, type?)`, представленный в следующем запросе. Указанный запрос извлекает узел элементов, имеющий тип `xs:string`, независимо от его имени.  
  
    ```  
    SELECT @var.query('declare namespace x="myNS"; (/x:customer/*)[1] instance of element (*, xs:string?)')  
    GO  
    ```  
  
### <a name="example-b"></a>Пример Б  
 В следующем примере показано, как определить, является ли узел, возвращенный выражением, элементом узла с указанным именем. Она использует **element()** тестирования.  
  
 В следующем примере два элемента <`Customer`> XML-экземпляра, к которому происходит запрос, имеют два разных типа данных: `SpecialCustomerType` и `CustomerType`. Предположим, что необходимо выяснить тип элемента <`Customer`>, возвращенного выражением. Следующая коллекция XML-схем определяет типы данных `CustomerType` и `SpecialCustomerType`.  
  
```  
CREATE XML SCHEMA COLLECTION SC AS N'  
<schema xmlns="https://www.w3.org/2001/XMLSchema"  
          targetNamespace="myNS"  xmlns:ns="myNS">  
  <complexType name="CustomerType">  
    <sequence>  
      <element name="firstName" type="string"/>  
      <element name="lastName" type="string"/>  
    </sequence>  
  </complexType>  
  <complexType name="SpecialCustomerType">  
     <complexContent>  
       <extension base="ns:CustomerType">  
        <sequence>  
            <element name="Age" type="int"/>  
        </sequence>  
       </extension>  
     </complexContent>  
    </complexType>  
   <element name="customer" type="ns:CustomerType"/>  
</schema>  
'  
GO  
```  
  
 Данная коллекция схем XML используется для создания типизированного **xml** переменной. XML-экземпляр, связанный с данной переменной, содержит два элемента <`customer`> разных типов. Первый элемент имеет тип данных `CustomerType`, а второй элемент — `SpecialCustomerType`.  
  
```  
DECLARE @var XML(SC)  
SET @var = '  
<x:customer xmlns:x="myNS">  
   <firstName>FirstName1</firstName>  
   <lastName>LastName1</lastName>  
</x:customer>  
<x:customer xsi:type="x:SpecialCustomerType" xmlns:x="myNS" xmlns:xsi="https://www.w3.org/2001/XMLSchema-instance">  
   <firstName> FirstName2</firstName>  
   <lastName> LastName2</lastName>  
   <Age>21</Age>  
</x:customer>'  
```  
  
 В следующем запросе выражение `instance of element (*, x:SpecialCustomerType ?)` возвращает значение False, так как оно возвращает первый элемент результата, не имеющий тип данных `SpecialCustomerType`.  
  
```  
SELECT @var.query('declare namespace x="myNS";   
    (/x:customer)[1] instance of element (*, x:SpecialCustomerType ?)')  
```  
  
 Если изменить выражение, используемое в предыдущем запросе, и получить второй элемент <`customer`> (`instance of`), то результатом выполнения выражения `/x:customer)[2]` будет значение True.  
  
### <a name="example-c"></a>Пример В  
 В данном примере используется проверка атрибута. Следующая XML-схема определяет сложный тип CustomerType с атрибутами CustomerID и Age. Атрибут Age является необязательным. Для указанного XML-экземпляра может понадобиться определить, имеется ли у элемента <`customer`> атрибут Age.  
  
```  
CREATE XML SCHEMA COLLECTION SC AS N'  
<schema xmlns="https://www.w3.org/2001/XMLSchema"  
       targetNamespace="myNS" xmlns:ns="myNS">  
<complexType name="CustomerType">  
  <sequence>  
     <element name="firstName" type="string" minOccurs="0"   
               nillable="true" />  
     <element name="lastName" type="string" minOccurs="0"/>  
  </sequence>  
  <attribute name="CustomerID" type="integer" use="required" />  
  <attribute name="Age" type="integer" use="optional" />  
 </complexType>  
 <element name="customer" type="ns:CustomerType"/>  
</schema>  
'  
GO  
```  
  
 Результатом следующего запроса является значение True, так как имеется узел атрибута с именем `Age` в экземпляре XML, к которому производится запрос. В данном выражении используется проверка атрибута `attribute(Age)`. Так как атрибуты не упорядочены, то в запросе вначале извлекаются все атрибуты с помощью выражения FLWOR, а затем производится их проверка с помощью выражения `instance of`. В примере сначала создается коллекцию XML-схем, чтобы создать типизированный **xml** переменной.  
  
```  
DECLARE @var XML(SC)  
SET @var = '<x:customer xmlns:x="myNS" CustomerID="1" Age="22" >  
<firstName>SomeFName</firstName>  
<lastName>SomeLName</lastName>  
</x:customer>'  
SELECT @var.query('declare namespace x="myNS";   
FOR $i in /x:customer/@*  
RETURN  
    IF ($i instance of attribute (Age)) THEN  
        "true"  
        ELSE  
        ()')     
GO  
  
```  
  
 Если из экземпляра удалить необязательный атрибут `Age`, предыдущий запрос возвращает значение False.  
  
 Для проверки атрибута необходимо указать его имя и ввести (`attribute(name,type)`).  
  
```  
SELECT @var.query('declare namespace x="myNS";   
FOR $i in /x:customer/@*  
RETURN  
    IF ($i instance of attribute (Age, xs:integer)) THEN  
        "true"  
        ELSE  
        ()')  
```  
  
 Кроме того, можно указать `attribute(*, type)` синтаксис типа последовательности. Если тип атрибута соответствует указанному типу вне зависимости от его имени, узел атрибута считается удовлетворяющим запросу.  
  
### <a name="implementation-limitations"></a>Ограничения реализации  
 Особые ограничения:  
  
-   В проверке элементов имя типа может стоять признака вхождения (**?**).  
  
-   **элемент (ElementName, TypeName)** не поддерживается.  
  
-   **элемент (\*, TypeName)** не поддерживается.  
  
-   **Schema-element()** не поддерживается.  
  
-   **Schema-Attribute(attributeName)** не поддерживается.  
  
-   Явные запросы для **xsi: Type** или **xsi: nil** не поддерживается.  
  
## <a name="see-also"></a>См. также  
 [Система типов &#40;XQuery&#41;](../xquery/type-system-xquery.md)  
  
  
