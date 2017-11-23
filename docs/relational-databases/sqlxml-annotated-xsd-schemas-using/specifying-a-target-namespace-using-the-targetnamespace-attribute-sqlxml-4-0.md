---
title: "Указание целевого пространства имен с помощью атрибута (SQLXML 4.0) targetNamespace | Документы Microsoft"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: sqlxml
ms.reviewer: 
ms.suite: sql
ms.technology: dbe-xml
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- namespaces [SQLXML], annotated XSD schemas
- targetNamespace attribute
- XSD schemas [SQLXML], target namespaces
- annotated XSD schemas, target namespaces
- xsd:targetNamespace
- attributeFormDefault attribute
- elementFormDefault attribute
- target namespaces [SQLXML]
ms.assetid: f3df9877-6672-4444-8245-2670063c9310
caps.latest.revision: "27"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 1a7333141672e9c6979202a95f24d42cae0ed82e
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="specifying-a-target-namespace-using-the-targetnamespace-attribute-sqlxml-40"></a>Задание целевого пространства имен с помощью атрибута targetNamespace (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]При написании схем XSD, можно использовать XSD **targetNamespace** атрибут для указания целевого пространства имен. В этом разделе описывается как XSD **targetNamespace**, **elementFormDefault**, и **attributeFormDefault** атрибуты работают, как они влияют на экземпляр XML, который создан, и как запросы XPath указываются с пространствами имен.  
  
 Можно использовать **xsd: targetNamespace** атрибут, чтобы поместить элементы и атрибуты из пространства имен по умолчанию в другом пространстве имен. Можно указать, будут ли локально объявленные элементы и атрибуты схемы уточняться пространством имен, использоваться явно путем применения префикса либо использоваться неявно. Можно использовать **elementFormDefault** и **attributeFormDefault** атрибуты  **\<xsd: schema >** элемента, чтобы указать глобально уточнения локальных элементов и атрибутов либо можно использовать **формы** атрибут для указания отдельных элементов и атрибутов отдельно.  
  
## <a name="examples"></a>Примеры  
 Чтобы создать рабочие образцы на основе следующих примеров, необходимо выполнить определенные требования. Дополнительные сведения см. в разделе [требования для выполнения примеров SQLXML](../../relational-databases/sqlxml/requirements-for-running-sqlxml-examples.md).  
  
### <a name="a-specifying-a-target-namespace"></a>A. Указание целевого пространства имен  
 Следующая схема XSD указывает целевое пространство имен с помощью **xsd: targetNamespace** атрибута. Эта схема также выставляет **elementFormDefault** и **attributeFormDefault** значений для атрибута **«unqualified»** (значение по умолчанию для этих атрибутов). Это глобальная декларация и влияет на все локальные элементы (**\<порядок >** в схеме) и атрибутов (**CustomerID**, **ContactName**и  **OrderID** в схеме).  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema"  
            xmlns:CO="urn:MyNamespace"   
            targetNamespace="urn:MyNamespace" >  
<xsd:annotation>  
  <xsd:appinfo>  
    <sql:relationship name="CustOrders"  
          parent="Sales.Customer"  
          parent-key="CustomerID"  
          child="Sales.SalesOrderHeader"  
          child-key="CustomerID" />  
  </xsd:appinfo>  
</xsd:annotation>  
  
  <xsd:element name="Customer"   
               sql:relation="Sales.Customer"   
               type="CO:CustomerType" />  
  
  <xsd:complexType name="CustomerType" >  
     <xsd:sequence>  
        <xsd:element name="Order"   
                     sql:relation="Sales.SalesOrderHeader"  
                     sql:relationship="CustOrders"  
                     type="CO:OrderType" />  
     </xsd:sequence>  
        <xsd:attribute name="CustomerID"   type="xsd:string" />   
        <xsd:attribute name="SalesPersonID"  type="xsd:string" />  
  </xsd:complexType>  
  <xsd:complexType name="OrderType" >  
     <xsd:attribute name="SalesOrderID" type="xsd:integer" />  
     <xsd:attribute name="CustomerID" type="xsd:string" />  
  </xsd:complexType>  
</xsd:schema>  
```  
  
 В схеме:  
  
-   **CustomerType** и **OrderType** объявления типов являются глобальными и поэтому включаются в целевое пространство имен схемы. В результате, когда эти ссылки на типы в объявлении  **\<клиента >** элемента и его  **\<порядок >** дочерний элемент указан префикс, связанный с целевым пространством имен.  
  
-   **\<Клиента >** элемент также включается в целевое пространство имен схемы, так как это глобальный элемент в схеме.  
  
 Выполните следующий XPath-запрос к схеме:  
  
```  
(/CO:Customer[@CustomerID=1)   
```  
  
 Этот XPath-запрос создает следующий экземпляр документа (показаны только несколько заказов):  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <y0:Customer xmlns:y0="urn:MyNamespace"   
      CustomerID="ALFKI" ContactName="Maria Anders">  
        <Order CustomerID="ALFKI" OrderID="10643" />   
        <Order CustomerID="ALFKI" OrderID="10692" />   
        ...  
  </y0:Customer>  
  </ROOT>  
```  
  
 Этот экземпляр документа определяет пространство имен urn: MyNamespace и связывает префикс (y0) к нему. Префикс применяется только к  **\<клиента >** глобального элемента. (Элемент является глобальным, так как он объявлен в качестве дочернего элемента  **\<xsd: schema >** элемента в схеме.)  
  
 Префикс не применяется к локальные элементы и атрибуты, так как значение **elementFormDefault** и **attributeFormDefault** атрибуты значения **«unqualified»**в схеме. Обратите внимание, что  **\<порядок >** элемент является локальным, потому что он объявлен как дочерний  **\<complexType >** элемент, определяющий  **\< Тип клиента >** элемента. Аналогичным образом, атрибуты (**CustomerID**, **OrderID**, и **ContactName**) являются локальными, а не как глобальные.  
  
##### <a name="to-create-a-working-sample-of-this-schema"></a>Создание рабочего образца этой схемы  
  
1.  Скопируйте приведенный выше код схемы и вставьте его в текстовый файл. Сохраните файл с именем targetNameSpace.xml.  
  
2.  Скопируйте следующий шаблон и вставьте его в текстовый файл. Сохраните файл с именем targetNameSpace.xml в тот же каталог, куда уже был сохранен файл targetNamespace.xml.  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="targetNamespace.xml"  
                       xmlns:CO="urn:MyNamespace" >  
        /CO:Customer[@CustomerID=1]  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     Запрос XPath в шаблоне возвращает  **\<клиента >** элемент для заказчика со значением CustomerID, равным 1. Обратите внимание, что в запросе XPath префикс пространства имен указан для элемента запроса, а не для атрибута. (Как указано в схеме, локальные атрибуты не определены).  
  
     Указанный для схемы сопоставления путь к каталогу (targetNamespace.xml) задается относительно каталога, в котором сохранен шаблон. Можно также задать абсолютный путь, например:  
  
    ```  
    mapping-schema="C:\MyDir\targetNamepsace.xml"  
    ```  
  
3.  Создайте и запустите тестовый скрипт SQLXML 4.0 (Sqlxml4test.vbs), чтобы выполнить шаблон.  
  
     Дополнительные сведения см. в разделе [с помощью ADO для выполнения запросов SQLXML](../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
 Если схема данных указывает **elementFormDefault** и **attributeFormDefault** атрибуты со значением **«полное»**, документ будет иметь все локальной элементы и атрибуты полное имя. Можно изменить предыдущую схему, чтобы включить эти атрибуты в  **\<xsd: schema >** элемента и выполняла шаблон еще раз. Так как атрибуты в экземпляре теперь также имеют квалификатор, XPath-запрос изменится так, чтобы включать префикс пространства имен.  
  
 Измененный XPath-запрос:  
  
```  
/CO:Customer[@CO:CustomerID=1]  
```  
  
 Возвращаемый XML-документ:  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
   <y0:Customer xmlns:y0="urn:MyNamespace" CustomerID="1" SalesPersonID="280">  
      <Order SalesOrderID="43860" CustomerID="1" />   
      <Order SalesOrderID="44501" CustomerID="1" />   
      <Order SalesOrderID="45283" CustomerID="1" />   
      <Order SalesOrderID="46042" CustomerID="1" />   
   </y0:Customer>  
</ROOT>  
```  
  
  
