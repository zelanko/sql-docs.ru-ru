---
title: 'Получение URL-адрес ссылок на данные BLOB с использованием sql: encode (SQLXML 4.0) | Документация Майкрософт'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 4b33588c55b22e044260aedc1b0809d24c4f1eb8
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2018
ms.locfileid: "52793386"
---
# <a name="requesting-url-references-to-blob-data-using-sqlencode-sqlxml-40"></a>Получение URL-ссылок на данные BLOB с использованием sql:encode (SQLXML 4.0)
  В схеме XSD с заметками, когда атрибут (или элемент) сопоставляется со столбцом BLOB в Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], данные внутри XML возвращаются в формате Base 64.  
  
 Если требуется возвратить ссылку на эти данные (идентификатор URI), которую впоследствии можно будет использовать для получения данных BLOB в двоичном формате, укажите заметку `sql:encode`. Заметку `sql:encode` можно указывать для атрибута или элемента простого типа.  
  
 Задайте заметку `sql:encode`, чтобы указать, что необходимо вернуть URL-адрес поля вместо значения поля. При формировании одноэлементного выбора в URL-адресе заметка `sql:encode` зависит от первичного ключа. Первичный ключ можно указать при помощи заметки `sql:key-fields`.  
  
 Заметке `sql:encode` можно назначить значение «url» или «default». Значение «default» возвращает данные в формате Base 64.  
  
 Заметку `sql:encode` нельзя использовать с `sql:use-cdata` или для типов атрибутов ID, IDREF, IDREFS, NMTOKEN и NMTOKENS. Он также не может использоваться с XSD **фиксированной** атрибута.  
  
> [!NOTE]  
>  Столбцы типа BLOB невозможно использовать, как часть ключа или внешнего ключа.  
  
## <a name="examples"></a>Примеры  
 Чтобы создать рабочие образцы на основе следующих примеров, необходимо выполнить определенные требования. Дополнительные сведения см. в разделе [требования для запуска примеров SQLXML](../sqlxml/requirements-for-running-sqlxml-examples.md).  
  
### <a name="a-specifying-sqlencode-to-obtain-a-url-reference-to-blob-data"></a>A. Указание заметки sql:encode для получения URL-ссылки на данные BLOB  
 В этом примере схема сопоставления задает `sql:encode` на **LargePhoto** атрибут, чтобы получить URI-ссылку на фотографию определенного продукта (вместо извлечения двоичных данных в формате Base 64).  
  
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
  
     Дополнительные сведения см. в разделе [использование объектов ADO для выполнения запросов SQLXML 4.0](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
 Это результат:  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
   <ProductPhoto ProductPhotoID="100"  
                 LargePhoto="dbobject/Production.ProductPhoto[@ProductPhotoID="100"]/@LargePhoto" />   
</ROOT>  
```  
  
  
