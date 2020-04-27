---
title: 'Создание разделов CDATA с помощью SQL: use-CDATA (SQLXML 4,0) | Документация Майкрософт'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- markup characters [SQLXML]
- special characters [SQLXML]
- use-cdata annotation
- plain text [SQLXML]
- CDATA sections
- escaping blocks of text [SQLXML]
- annotated XSD schemas, CDATA sections
- sql:use-cdata
ms.assetid: 26d2b9dc-f857-44ff-bcd4-aaf64ff809d0
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: cddde2ed1e40b2ea21cf4ebff75bea3beed8f2ce
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "66014013"
---
# <a name="creating-cdata-sections-using-sqluse-cdata-sqlxml-40"></a>Создание разделов CDATA с использованием sql:use-cdata (SQLXML 4.0)
  В XML разделы CDATA используются для экранирования блоков текста, содержащих символы, которые в противном случае распознаются как символы разметки.  
  
 База данных в Майкрософт [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] иногда может содержать символы, которые обрабатываются синтаксическим анализатором XML как символы разметки. Например, угловые скобки\< (и >), символ "меньше или равно" (<=), а амперсанд (&) обрабатываются как символы разметки. Но специальные символы такого типа можно заключить в раздел CDATA во избежание их обработки в качестве символов разметки. Текст в разделе CDATA обрабатывается средством синтаксического анализа XML как простой текст.  
  
 Заметка `sql:use-cdata` используется для указания на то, что данные, возвращаемые [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], необходимо ввести в раздел CDATA (т. е. заметка указывает, должно ли значение из столбца, обозначенного заметкой `sql:field`, быть заключено в раздел CDATA). Заметку `sql:use-cdata` можно задавать только для элементов, которые сопоставляются со столбцом базы данных.  
  
 Заметка `sql:use-cdata` имеет логическое значение (0 = false, 1 = true). Допустимые значения: 0, 1, true и false.  
  
 Эту заметку нельзя использовать с `sql:url-encode` или для типов атрибутов ID, IDREF, IDREFS, NMTOKEN и NMTOKENS.  
  
## <a name="examples"></a>Примеры  
 Чтобы создать рабочие образцы на основе следующих примеров, необходимо выполнить определенные требования. Дополнительные сведения см. в разделе [требования для запуска примеров SQLXML](../sqlxml/requirements-for-running-sqlxml-examples.md).  
  
### <a name="a-specifying-sqluse-cdata-on-an-element"></a>А) Указание заметки sql:use-cdata для элемента  
 В следующей схеме `sql:use-cdata` для ** \<>AddressLine1** в элементе ** \<>адреса** задано значение 1 (true). В результате этого данные возвращаются в разделе CDATA.  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:element name="Address"   
               sql:relation="Person.Address"   
               sql:key-fields="AddressID" >  
   <xsd:complexType>  
        <xsd:sequence>  
          <xsd:element name="AddressID"  type="xsd:string" />  
          <xsd:element name="AddressLine1" type="xsd:string"   
                       sql:use-cdata="1" />  
        </xsd:sequence>  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a>Проверка образца запроса XPath к схеме  
  
1.  Скопируйте приведенный выше код схемы и вставьте его в текстовый файл. Сохраните этот файл с именем UseCData.xml.  
  
2.  Скопируйте следующий шаблон и вставьте его в текстовый файл. Сохраните этот файл под именем UseCDataT.xml в том же каталоге, в котором был сохранен файл UseCData.xml.  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
        <sql:xpath-query mapping-schema="UseCData.xml">  
            /Address[AddressID < 11]  
        </sql:xpath-query>  
    </ROOT>  
    ```  
  
     Путь к каталогу схемы сопоставления (файл UseCData.xml) задается относительно каталога, в котором сохранен шаблон. Можно также задать абсолютный путь, например:  
  
    ```  
    mapping-schema="C:\SqlXmlTest\UseCData.xml"  
    ```  
  
3.  Создайте и запустите тестовый скрипт SQLXML 4.0 (Sqlxml4test.vbs), чтобы выполнить шаблон.  
  
     Дополнительные сведения см. [в разделе Использование ADO для выполнения запросов SQLXML 4,0](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
 Ниже приведен частичный результирующий набор.  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">   
  <Address>   
    <AddressID>1</CustomerID>   
    <AddressLine1>   
      <![CDATA[ 1970 Napa Ct.  ]]>   
    </AddressLine1>   
  </Address>  
  <Address>  
    <AddressLine1>   
      <![CDATA[ 9833 Mt. Dias Blv. ]]>   
    </AddressLine1>   
  </Address>  
  ...  
</ROOT>  
```  
  
  
