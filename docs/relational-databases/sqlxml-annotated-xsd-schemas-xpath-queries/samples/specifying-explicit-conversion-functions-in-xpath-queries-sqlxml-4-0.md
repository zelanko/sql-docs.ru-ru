---
title: Определение явных функций преобразования в запросах XPath (SQLXML 4.0) | Документация Майкрософт
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: sqlxml
ms.reviewer: ''
ms.suite: sql
ms.technology: xml
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- explicit conversion functions [SQLXML]
- string function
- number function
- XPath queries [SQLXML], explicit conversion functions
ms.assetid: 1111cb5d-2bd9-4bdb-8de2-dc0e47452dd6
caps.latest.revision: 25
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 623f2814322a6a57e6845a8d3d8d734b1b7c68f4
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2018
ms.locfileid: "38032352"
---
# <a name="specifying-explicit-conversion-functions-in-xpath-queries-sqlxml-40"></a>Определение явных функций преобразования в запросах XPath (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Следующие примеры показывают, как явные функции преобразования указываются в запросах XPath. В данных примерах запросы XPath определены в соответствии со схемой сопоставления, которая содержится в файле SampleSchema1.xml. Сведения об этом образце схемы см. в разделе [образец аннотированные схемы XSD для примеров XPath &#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/samples/sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md).  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-use-the-number-explicit-conversion-function"></a>A. Используйте функцию явного преобразования number()  
 **Number()** функция преобразует аргумент в число.  
  
 Предполагая, что значение **ContactID** не является числом, следующий запрос преобразует **ContactID** в число и сравнивает его со значением 4. Запрос возвращает все  **\<сотрудника >** дочерние элементы узла контекста с **ContactID** атрибут, имеющий числовое значение 4:  
  
```  
/child::Contact[number(attribute::ContactID)= 4]  
```  
  
 Ярлык для **атрибут** оси (@) можно указать и поскольку **дочерних** оси используется по умолчанию, его можно исключить из запроса:  
  
```  
/Contact[number(@ContactID) = 4]  
```  
  
 В терминах реляционной базы данных запрос возвращает работника с **ContactID** 4.  
  
##### <a name="to-test-the-xpath-query-against-the-mapping-schema"></a>Проверка запроса XPath к схеме сопоставления  
  
1.  Копировать [образец кода схемы](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/samples/sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md) и вставьте его в текстовый файл. Сохраните файл с именем SampleSchema1.xml.  
  
2.  Создайте следующий шаблон (ExplicitConversionA.xml) и сохраните его в каталоге, в котором сохранен файл SampleSchema1.xml.  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="SampleSchema1.xml">  
        /Contact[number(@ContactID)=4]  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     Путь к каталогу схемы сопоставления (файл SampleSchema1.xml) задается относительно каталога, в котором сохранен шаблон. Можно также задать абсолютный путь, например:  
  
    ```  
    mapping-schema="C:\MyDir\SampleSchema1.xml"  
    ```  
  
3.  Создайте и запустите тестовый скрипт SQLXML 4.0 (Sqlxml4test.vbs), чтобы выполнить шаблон.  
  
     Дополнительные сведения см. в разделе [использование объектов ADO для выполнения запросов SQLXML 4.0](../../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
 Результирующий набор для выполнения этого шаблона:  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Contact ContactID="4" LastName="Acevedo" FirstName="Humberto" Title="Sr." />   
</ROOT>  
```  
  
### <a name="b-use-the-string-explicit-conversion-function"></a>Б. Используйте функцию явного преобразования string()  
 **String()** функция преобразует аргумент в строку.  
  
 Следующий запрос преобразует **ContactID** в строку и сравнивает ее со строковым значением «4». Запрос возвращает все  **\<сотрудника >** дочерние элементы узла контекста с **ContactID** со строковым значением «4»:  
  
```  
/child::Contact[string(attribute::ContactID)="4"]  
```  
  
 Ярлык для **атрибут** оси (@) можно указать и поскольку **дочерних** оси используется по умолчанию, его можно исключить из запроса:  
  
```  
/Contact[string(@ContactID)="4"]  
```  
  
 С функциональной точки зрения этот запрос возвращает те же результаты, что и предыдущий пример запроса, хотя выполняется сопоставление со строковым значением, а не числовым значением (то есть числом 4).  
  
##### <a name="to-test-the-xpath-query-against-the-mapping-schema"></a>Проверка запроса XPath к схеме сопоставления  
  
1.  Копировать [образец кода схемы](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/samples/sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md) и вставьте его в текстовый файл. Сохраните файл с именем SampleSchema1.xml.  
  
2.  Создайте следующий шаблон (ExplicitConversionB.xml) и сохраните его в каталоге, в котором сохранен файл SampleSchema1.xml.  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="SampleSchema1.xml">  
        Contact[string(@ContactID)="4"]  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     Путь к каталогу схемы сопоставления (файл SampleSchema1.xml) задается относительно каталога, в котором сохранен шаблон. Можно также задать абсолютный путь, например:  
  
    ```  
    mapping-schema="C:\MyDir\SampleSchema1.xml"  
    ```  
  
3.  Создайте и запустите тестовый скрипт SQLXML 4.0 (Sqlxml4test.vbs), чтобы выполнить шаблон.  
  
     Дополнительные сведения см. в разделе [использование объектов ADO для выполнения запросов SQLXML 4.0](../../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
 Далее приведен результирующий набор, полученный в результате выполнения этого шаблона.  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Contact ContactID="4" LastName="Acevedo" FirstName="Humberto" Title="Sr." />   
</ROOT>  
```  
  
  
