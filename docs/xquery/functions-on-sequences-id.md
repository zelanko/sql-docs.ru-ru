---
title: id Функция (X-Кери) Документы Майкрософт
description: Узнайте, как использовать функцию идентификатора X's, чтобы вернуть последовательность элементов в экземпляре XML в порядке документа с поставленными значениями xs:IDREF.
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
- fn:id function
- id function
ms.assetid: de99fc60-d0ad-4117-a17d-02bdde6512b4
author: rothja
ms.author: jroth
ms.openlocfilehash: 45b7f9f7ee9fa301b10c29fafb663c3a307509d7
ms.sourcegitcommit: a3f5c3742d85d21f6bde7c6ae133060dcf1ddd44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/15/2020
ms.locfileid: "81388514"
---
# <a name="functions-on-sequences---id"></a>Функции с последовательностями — id
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Возвращает последовательность узлов элементов с значениями xs:ID, которые соответствуют значениям одного или нескольких значений xs:IDREF, поставляемых в *$arg.*  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
fn:id($arg as xs:IDREF*) as element()*  
```  
  
## <a name="arguments"></a>Аргументы  
 *$arg*  
 Одно или несколько значений xs:IDREF.  
  
## <a name="remarks"></a>Remarks  
 Результатом функции является последовательность элементов в экземпляре XML, в порядке документов, имеющих значение xs:ID, равное одному или нескольким значениям xs:IDREF в списке кандидатов xs:IDREF.  
  
 Если значение xs:IDREF не совпадает ни с одним элементом, функция возвращает пустую последовательность.  
  
## <a name="examples"></a>Примеры  
 В этой теме приводятся примеры X-образных экземпляров, которые [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] хранятся в различных столбцах типа **xml** в базе данных.  
  
### <a name="a-retrieving-elements-based-on-the-idref-attribute-value"></a>A. Получение элементов, основанных на значении атрибута IDREF  
 В следующем примере используется fn:id `employee` для извлечения элементов <> на основе атрибута менеджера IDREF. В данном примере атрибут управляющего является атрибутом типа IDREF, а атрибут eid — атрибутом типа ID.  
  
 Для определенного значения атрибута менеджера функция **id()** находит элемент <`employee`>, значение атрибута типа идентификатора соответствует значению вхотого значения IDREF. Другими словами, для конкретного сотрудника функция **id()** возвращает менеджера сотрудника.  
  
 Вот что происходит в примере:  
  
-   создается коллекция XML-схем;  
  
-   Набранная переменная **xml** создается с помощью коллекции схем XML.  
  
-   Запрос извлекает элемент, который имеет значение атрибута **manager** id, на которое `employee` ссылается атрибут менеджера IDREF элемента <> элемент.  
  
```  
-- If exists, drop the XML schema collection (SC).  
-- drop xml schema collection SC  
-- go  
  
create xml schema collection SC as  
'<schema xmlns="http://www.w3.org/2001/XMLSchema" xmlns:e="emp" targetNamespace="emp">  
            <element name="employees" type="e:EmployeesType"/>  
            <complexType name="EmployeesType">  
                 <sequence>  
                      <element name="employee" type="e:EmployeeType" minOccurs="0" maxOccurs="unbounded" />  
                 </sequence>  
            </complexType>    
  
            <complexType name="EmployeeType">  
                        <attribute name="eid" type="ID" />  
                        <attribute name="name" type="string" />  
                        <attribute name="manager" type="IDREF" />  
            </complexType>         
</schema>'  
go  
```  
  
```  
declare @x xml(SC)  
set @x='<e:employees xmlns:e="emp">  
<employee eid="e1" name="Joe" manager="e10" />  
<employee eid="e2" name="Bob" manager="e10" />  
<employee eid="e10" name="Dave" manager="e10" />  
</e:employees>'  
  
select @x.value(' declare namespace e="emp";   
 (fn:id(e:employees/employee[@name="Joe"]/@manager)/@name)[1]', 'varchar(50)')   
Go  
```  
  
 Запрос возвращает значение «Dave». Это значит, что Дэйв является управляющим Джо.  
  
### <a name="b-retrieving-elements-based-on-the-orderlist-idrefs-attribute-value"></a>Б. Извлечение элементов, основанных на значении атрибута OrderList IDREFS  
 В следующем примере атрибутом OrderList `Customer` <> элементом является атрибут типа IDREFS. Он перечисляет идентификаторы заказов определенного заказчика. Для каждого идентификатора заказа есть `Order` `Customer` <> элемента ребенка под <>, обеспечивающим значение заказа.  
  
 Выражение запроса `data(CustOrders:Customers/Customer[1]/@OrderList)[1]` получает первое значение из списка IDRES для первого заказчика. Затем это значение передается функции **id().** Затем функция находит `Order` элемент <>, значение атрибута OrderID соответствует входу с функцией **id().**  
  
```  
drop xml schema collection SC  
go  
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
select @x.query('declare namespace CustOrders="Customers";  
  id(data(CustOrders:Customers/Customer[1]/@OrderList)[1])')  
  
-- result  
<Order OrderID="OrderA">  
  <OrderValue>11</OrderValue>  
</Order>  
```  
  
### <a name="implementation-limitations"></a>Ограничения реализации  
 Существуют следующие ограничения:  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]не поддерживает двухаргументную версию **id()**.  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]требует, чтобы тип **идентификатора** аргумента был подтипом xs:IDREF.  
  
## <a name="see-also"></a>См. также:  
 [Функции над последовательностями](https://msdn.microsoft.com/library/672d2795-53ab-49c2-bf24-bc81a47ecd3f)  
  
  
