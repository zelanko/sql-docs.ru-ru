---
title: 'Создание постоянных элементов при помощи sql: — constant (SQLXML 4.0) | Документация Майкрософт'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- element does not map [SQLXML]
- sql:is-constant
- XSD schemas [SQLXML], constant elements
- element mapping [SQLXML], constant elements
- is-constant annotation
- constant elements [SQLXML]
- annotated XSD schemas, constant elements
ms.assetid: 940eea1b-54f5-445f-b844-c894d9f3941b
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: bc100446eb6dff17125b0df7a60b8c2c82e46277
ms.sourcegitcommit: 45a9d7ffc99502c73f08cb937cbe9e89d9412397
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/22/2019
ms.locfileid: "66013938"
---
# <a name="creating-constant-elements-using-sqlis-constant-sqlxml-40"></a>Создание постоянных элементов при помощи sql:is-constant (SQLXML 4.0)
  Чтобы указать постоянный элемент — то есть элемент в схеме XSD, которые не сопоставлены для любой таблицы базы данных или столбца-можно использовать `sql:is-constant` заметки. Эта заметка имеет логическое значение (0 = false, 1 = true). Допустимые значения: 0, 1, true и false. Заметка `sql:is-constant` может быть указана для элемента, не имеющего атрибутов. Если она задана для элемента, имеющего значение true (или 1), то этот элемент не будет сопоставлен с базой данных, но будет по-прежнему отображаться в XML-документе.  
  
 Заметка `sql:is-constant` может использоваться для следующих задач.  
  
-   Добавление элемента верхнего уровня в XML-документ. XML-документ должен содержать единственный элемент верхнего уровня (корневой элемент).  
  
-   Создание контейнера элементов, таких как  **\<заказы >** элемент, который переносит все заказы.  
  
 `sql:is-constant` Заметки, которые могут добавляться к  **\<complexType >** элемент.  
  
## <a name="examples"></a>Примеры  
 Чтобы создать рабочие образцы на основе следующих примеров, необходимо выполнить определенные требования. Дополнительные сведения см. в разделе [требования для запуска примеров SQLXML](../sqlxml/requirements-for-running-sqlxml-examples.md).  
  
### <a name="a-specifying-sqlis-constant-to-add-a-container-element"></a>A. Указание sql:is-constant для добавления элемента контейнера  
 В этой схемы XSD, с заметками  **\<CustomerOrders >** определяется как постоянный элемент, указав `sql:is-constant` атрибут со значением 1. Таким образом  **\<CustomerOrders >** не сопоставлен с любой таблицы базы данных или столбца. Этот постоянный элемент состоит из  **\<порядок >** дочерних элементов.  
  
 Несмотря на то что  **\<CustomerOrders >** не сопоставляется любой таблицы базы данных или столбца, по-прежнему отображается в результирующем XML как элемента контейнера, содержащего  **\<порядок >** дочерние элементы.  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
<xsd:annotation>  
  <xsd:appinfo>  
    <sql:relationship name="CustOrders"  
        parent="Sales.Customer"  
        parent-key="CustomerID"  
        child="Sales.SalesOrderHeader"  
        child-key="CustomerID" />  
  </xsd:appinfo>  
</xsd:annotation>  
  
  <xsd:element name="Customer" sql:relation="Sales.Customer" >  
   <xsd:complexType>  
     <xsd:sequence>  
        <xsd:element name="CustomerOrders" sql:is-constant="1" >  
          <xsd:complexType>  
            <xsd:sequence>  
              <xsd:element name="Order" sql:relation="Sales.SalesOrderHeader"  
                           sql:relationship="CustOrders"   
                           maxOccurs="unbounded" >  
                <xsd:complexType>  
                   <xsd:attribute name="SalesOrderID" type="xsd:integer" />  
                   <xsd:attribute name="OrderDate" type="xsd:date" />  
                   <xsd:attribute name="CustomerID" type="xsd:string" />  
                </xsd:complexType>  
              </xsd:element>  
            </xsd:sequence>  
           </xsd:complexType>  
          </xsd:element>  
         </xsd:sequence>  
          <xsd:attribute name="CustomerID" type="xsd:string" />  
     </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a>Проверка образца запроса XPath к схеме  
  
1.  Скопируйте приведенный выше код схемы и вставьте его в текстовый файл. Сохраните файл под именем isConstant.xml.  
  
2.  Скопируйте следующий шаблон и вставьте его в текстовый файл. Сохраните файл под именем isConstantT.xml в том же каталоге, где был сохранен файл isConstant.xml.  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
        <sql:xpath-query mapping-schema="isConstant.xml">  
            Customer[@CustomerID=1]  
        </sql:xpath-query>  
    </ROOT>  
    ```  
  
     Путь к каталогу схемы сопоставления (файл isConstant.xml) задается относительно каталога, в котором сохранен шаблон. Можно также задать абсолютный путь, например:  
  
    ```  
    mapping-schema="C:\MyDir\isConstant.xml"  
    ```  
  
3.  Создайте и запустите тестовый скрипт SQLXML 4.0 (Sqlxml4test.vbs), чтобы выполнить шаблон.  
  
     Дополнительные сведения см. в разделе [использование объектов ADO для выполнения запросов SQLXML](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
 Ниже приведен частичный результирующий набор.  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">   
<Customer CustomerID="1">   
  <CustomerOrders>   
    <Order SalesOrderID="43860" OrderDate="2001-08-01" CustomerID="1" />   
    <Order SalesOrderID="44501" OrderDate="2001-11-01" CustomerID="1" />   
    <Order SalesOrderID="45283" OrderDate="2002-02-01" CustomerID="1" />   
    <Order SalesOrderID="46042" OrderDate="2002-05-01" CustomerID="1" />   
    ...  
  </CustomerOrders>   
</Customer>   
</ROOT>  
```  
  
  
