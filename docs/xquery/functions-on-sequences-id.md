---
title: Функция ID (XQuery) | Документация Майкрософт
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
manager: craigg
ms.openlocfilehash: 80bb427800f57ddaa07e5e53f21b03df9e8317d3
ms.sourcegitcommit: bfa10c54e871700de285d7f819095d51ef70d997
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/14/2019
ms.locfileid: "54255529"
---
# <a name="functions-on-sequences---id"></a>Функции с последовательностями — id
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Возвращает последовательность узлов элемента со значениями xs: ID, которые совпадают со значениями из одного или нескольких значений xs: IDREF, указанных в *$arg*.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
fn:id($arg as xs:IDREF*) as element()*  
```  
  
## <a name="arguments"></a>Аргументы  
 *$arg*  
 Одно или несколько значений xs:IDREF.  
  
## <a name="remarks"></a>Примечания  
 Результатом функции является последовательность элементов в экземпляре XML, в порядке документов, имеющих значение xs:ID, равное одному или нескольким значениям xs:IDREF в списке кандидатов xs:IDREF.  
  
 Если значение xs:IDREF не совпадает ни с одним элементом, функция возвращает пустую последовательность.  
  
## <a name="examples"></a>Примеры  
 В этом разделе приведены примеры запросов XQuery к экземплярам XML, которые хранятся в различных **xml** -столбцов в [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] базы данных.  
  
### <a name="a-retrieving-elements-based-on-the-idref-attribute-value"></a>A. Получение элементов, основанных на значении атрибута IDREF  
 В следующем примере используется функция fn:id для получения элементов <`employee`>, основанных на атрибуте управляющего IDREF. В данном примере атрибут управляющего является атрибутом типа IDREF, а атрибут eid — атрибутом типа ID.  
  
 Для значения атрибута иному менеджеру **id()** функция находит <`employee`> элемент, значение атрибута ID совпадает с входным значением IDREF. Другими словами, для указанного работника **id()** функция возвращает менеджера сотрудника.  
  
 Вот что происходит в примере:  
  
-   создается коллекция XML-схем;  
  
-   Типизированный **xml** переменная создается с помощью коллекции XML-схем.  
  
-   Запрос извлекает элемент, имеющий значение атрибута ID, который ссылается **manager** атрибута IDREF <`employee`> элемента.  
  
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
 В следующем примере атрибут OrderList элемента <`Customer`> является атрибутом типа IDREFS. Он перечисляет идентификаторы заказов определенного заказчика. Для каждого идентификатора заказа существует дочерний элемент <`Order`> в элементе <`Customer`>, предоставляющем значение заказа.  
  
 Выражение запроса `data(CustOrders:Customers/Customer[1]/@OrderList)[1]` получает первое значение из списка IDRES для первого заказчика. Это значение затем передается **id()** функции. Эта функция находит <`Order`> элемент, значение атрибута OrderID которого совпадает с входом **id()** функции.  
  
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
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] не поддерживает версию двумя аргументами **id()**.  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] требуется тип аргумента **id()** быть подтипом xs:IDREF*.  
  
## <a name="see-also"></a>См. также  
 [Функции над последовательностями](https://msdn.microsoft.com/library/672d2795-53ab-49c2-bf24-bc81a47ecd3f)  
  
  
