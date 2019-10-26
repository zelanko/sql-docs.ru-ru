---
title: 'Создание элементов констант с помощью SQL: является константой (SQLXML 4,0) | Документация Майкрософт'
ms.custom: ''
ms.date: 01/11/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
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
ms.reviewer: ''
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 1cb1223c7c72aa091a3dd15da3beacaf65c4b21b
ms.sourcegitcommit: 2a06c87aa195bc6743ebdc14b91eb71ab6b91298
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/25/2019
ms.locfileid: "72906048"
---
# <a name="creating-constant-elements-using-sqlis-constant-sqlxml-40"></a>Создание постоянных элементов при помощи sql:is-constant (SQLXML 4.0)

[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Чтобы задать постоянный элемент, т. е. элемент в схеме XSD, не сопоставленный ни с одной таблицей или столбцом базы данных, можно использовать аннотацию **SQL: —-Constant** . Эта заметка имеет логическое значение (0 = false, 1 = true). Допустимые значения: 0, 1, true и false. Заметка **SQL: имеет значение константы** может быть указана для элемента, у которого нет атрибутов. Если она задана для элемента, имеющего значение true (или 1), то этот элемент не будет сопоставлен с базой данных, но будет по-прежнему отображаться в XML-документе.  
  
 Заметку **SQL: имеет значение константы** можно использовать для:  
  
-   Добавление элемента верхнего уровня в XML-документ. XML-документ должен содержать единственный элемент верхнего уровня (корневой элемент).  
  
-   Создание элементов контейнера, таких как **\<orders >** элемент, который упаковывает все заказы.  
  
 Заметку **SQL: является-Constant** можно добавить к элементу **\<complexType >** .  
  
## <a name="examples"></a>Примеры  
 Чтобы создать рабочие образцы на основе следующих примеров, необходимо выполнить определенные требования. Дополнительные сведения см. в разделе [требования для запуска примеров SQLXML](../../relational-databases/sqlxml/requirements-for-running-sqlxml-examples.md).  
  
### <a name="a-specifying-sqlis-constant-to-add-a-container-element"></a>A. Указание sql:is-constant для добавления элемента контейнера  
 В этой схеме XSD с заметками **\<кустомерордерс >** определен как элемент Constant, указав атрибут **SQL: имеет** значение, равное 1. Таким образом, **\<кустомерордерс >** не сопоставлены ни с одной таблицей или столбцом базы данных. Этот элемент константы состоит из **\<порядка >** дочерних элементов.  
  
 Хотя **\<кустомерордерс >** не сопоставляется ни с одной таблицей или столбцом базы данных, он по-прежнему отображается в результирующем XML-файле как элемент контейнера, содержащий **\<порядок >** дочерних элементов.  
  
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

     Дополнительные сведения см. [в разделе Использование ADO для выполнения запросов SQLXML](../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
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
  
  
