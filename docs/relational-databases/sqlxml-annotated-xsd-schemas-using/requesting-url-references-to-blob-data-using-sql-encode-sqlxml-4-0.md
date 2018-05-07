---
title: 'Запрос URL-ссылки на данные BLOB с помощью sql: encode (SQLXML 4.0) | Документы Microsoft'
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: sqlxml
ms.reviewer: ''
ms.suite: sql
ms.technology: xml
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- sql:encode
- encode annotation
- URL references to BLOB data [SQLXML]
- references to BLOB data [SQLXML]
- annotated XSD schemas, URL references to BLOB data
- requesting URL references to BLOB data
- BLOBs, URL references
- Base 64-encoded format
ms.assetid: 2f8cd93b-c636-462b-8291-167197233ee0
caps.latest.revision: 28
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 537e2656730c7659edd22ac68722bf43e892ad3d
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="requesting-url-references-to-blob-data-using-sqlencode-sqlxml-40"></a>Получение URL-ссылок на данные BLOB с использованием sql:encode (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  В схеме XSD с заметками, когда атрибут (или элемент) сопоставляется со столбцом BLOB в Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], данные внутри XML возвращаются в формате Base 64.  
  
 Если требуется ссылка на данные (URI) должен быть возвращен, можно использовать позже для получения данных BLOB в двоичном формате, укажите **sql: encode** заметки. Можно указать **sql: encode** на атрибут или элемент простого типа.  
  
 Укажите **sql: encode** заметки, чтобы указать, что URL-адрес в поле должны быть возвращены вместо значения поля. **SQL: encode** зависит от первичного ключа для создания одноэлементного выбора в URL-адрес. Первичный ключ можно задать с помощью **SQL: Key-поля** заметки.  
  
 **Sql: encode** заметки можно назначить «url» или значение «default». Значение «default» возвращает данные в формате Base 64.  
  
 **Sql: encode** заметки не может использоваться с **SQL: USE-cdata** или для ID, IDREF, IDREFS, NMTOKEN или NMTOKENS атрибутов типов. Он также не может использоваться с XSD **фиксированной** атрибута.  
  
> [!NOTE]  
>  Столбцы типа BLOB невозможно использовать, как часть ключа или внешнего ключа.  
  
## <a name="examples"></a>Примеры  
 Чтобы создать рабочие образцы на основе следующих примеров, необходимо выполнить определенные требования. Дополнительные сведения см. в разделе [требования для выполнения примеров SQLXML](../../relational-databases/sqlxml/requirements-for-running-sqlxml-examples.md).  
  
### <a name="a-specifying-sqlencode-to-obtain-a-url-reference-to-blob-data"></a>A. Указание заметки sql:encode для получения URL-ссылки на данные BLOB  
 В этом примере схема сопоставления указывает **sql: encode** на **LargePhoto** атрибут для получения URI-ссылку на фотографию определенного продукта (вместо извлечения двоичных данных в Base 64 - закодированном формате).  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  
  <xsd:element name="ProductPhoto" sql:relation="Production.ProductPhoto"   
               sql:key-fields="ProductPhotoID" >  
   <xsd:complexType>  
      <xsd:attribute name="ProductPhotoID"  type="xsd:int"  />  
     <xsd:attribute name="LargePhoto" type="xsd:string" sql:encode="url" />  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a>Проверка образца запроса XPath к схеме  
  
1.  Скопируйте приведенный выше код схемы и вставьте его в текстовый файл. Сохраните файл с именем sqlEncode.xml.  
  
2.  Скопируйте следующий шаблон и вставьте его в текстовый файл. Сохраните файл под именем sqlEncodeT.xml в том же каталоге, где был сохранен файл sqlEncode.xml.  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
        <sql:xpath-query mapping-schema="sqlEncode.xml">  
            /ProductPhoto[@ProductPhotoID=100]  
        </sql:xpath-query>  
    </ROOT>  
    ```  
  
     Путь к каталогу схемы сопоставления (файл sqlEncode.xml) задается относительно каталога, в котором сохранен шаблон. Можно также задать абсолютный путь, например:  
  
    ```  
    mapping-schema="C:\SqlXmlTest\sqlEncode.xml"  
    ```  
  
3.  Создайте и запустите тестовый скрипт SQLXML 4.0 (Sqlxml4test.vbs), чтобы выполнить шаблон.  
  
     Дополнительные сведения см. в разделе [с помощью ADO для выполнения запросов SQLXML 4.0](../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
 Результат:  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
   <ProductPhoto ProductPhotoID="100"  
                 LargePhoto="dbobject/Production.ProductPhoto[@ProductPhotoID="100"]/@LargePhoto" />   
</ROOT>  
```  
  
  
