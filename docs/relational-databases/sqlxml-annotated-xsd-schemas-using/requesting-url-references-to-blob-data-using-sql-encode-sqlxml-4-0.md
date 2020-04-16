---
title: Получить ссылки на данные BLOB с помощью кв/кодов (S'LXML)
description: Узнайте, как запросить ссылку на данные BLOB, указав аннотацию sql:encode в S'LXML 4.0.
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
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
author: MightyPen
ms.author: genemi
ms.reviewer: ''
ms.custom: seo-lt-2019
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 487ed2bbee997db22739bdeecd7e024b817ace80
ms.sourcegitcommit: a3f5c3742d85d21f6bde7c6ae133060dcf1ddd44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/15/2020
ms.locfileid: "81388110"
---
# <a name="requesting-url-references-to-blob-data-using-sqlencode-sqlxml-40"></a>Получение URL-ссылок на данные BLOB с использованием sql:encode (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  В схеме XSD с заметками, когда атрибут (или элемент) сопоставляется со столбцом BLOB в Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], данные внутри XML возвращаются в формате Base 64.  
  
 Если вы хотите вернуть ссылку на данные (URI), которые могут быть использованы позже для получения данных BLOB в двоичном формате, укажите аннотацию **sql:codecode.** Можно указать **sql:кодирование** на атрибуте или элементе простого типа.  
  
 Укажите **аннотацию sql: кодирования,** чтобы указать, что URL-адрес в поле должен быть возвращен вместо значения поля. **sql:код зависит** от основного ключа для генерации синглтона, выбранного в URL. Основной ключ можно указать с помощью аннотации **sql:key-fields.**  
  
 Аннотации **sql:код** может быть присвоено значение "url" или "по умолчанию". Значение «default» возвращает данные в формате Base 64.  
  
 Аннотация **sql:код не** может использоваться с **sql:use-cdata** или на id, IDREF, IDREFS, NMTOKEN или NMTOKENS. Он также не может быть использован с **фиксированным** атрибутом XSD.  
  
> [!NOTE]  
>  Столбцы типа BLOB невозможно использовать, как часть ключа или внешнего ключа.  
  
## <a name="examples"></a>Примеры  
 Чтобы создать рабочие образцы на основе следующих примеров, необходимо выполнить определенные требования. Для получения дополнительной информации [см.](../../relational-databases/sqlxml/requirements-for-running-sqlxml-examples.md)  
  
### <a name="a-specifying-sqlencode-to-obtain-a-url-reference-to-blob-data"></a>A. Указание заметки sql:encode для получения URL-ссылки на данные BLOB  
 В этом примере схема отображения определяет **sql:encode** на **атрибуте LargePhoto** для получения ссылки URI на конкретную фотографию продукта (вместо извлечения двоичных данных в базовом 64-кодированном формате).  
  
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
  
     Для получения дополнительной [информации см.](../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)  
  
 Результат:  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
   <ProductPhoto ProductPhotoID="100"  
                 LargePhoto="dbobject/Production.ProductPhoto[@ProductPhotoID="100"]/@LargePhoto" />   
</ROOT>  
```  
  
  
