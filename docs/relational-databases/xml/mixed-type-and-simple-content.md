---
title: "Смешанный тип и простое содержимое | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-xml"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "смешанные типы [SQL Server]"
ms.assetid: 6ea1f11d-e64b-4ebb-ab68-4eb6e4027665
caps.latest.revision: 9
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 9
---
# Смешанный тип и простое содержимое
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не поддерживает ограничение смешанного типа простым содержимым.  
  
## Пример  
 В следующей коллекции XML-схем `myComplexTypeA` является сложным типом, который может быть пустым. Это означает, что для обоих его элементов свойство `minOccurs` может быть установлено в значение 0. Попытка ограничить его простым содержимым, как это было сделано в объявлении `myComplexTypeB` , не поддерживается, поэтому создание следующей коллекции схем XML завершится с ошибкой.  
  
```  
CREATE XML SCHEMA COLLECTION SC AS '  
<schema xmlns="http://www.w3.org/2001/XMLSchema" targetNamespace="http://ns" xmlns:ns="http://ns"  
xmlns:ns1="http://ns1">  
  
    <complexType name="myComplexTypeA" mixed="true">  
        <sequence>  
            <element name="a" type="string" minOccurs="0"/>  
            <element name="b" type="string" minOccurs="0" maxOccurs="23"/>  
        </sequence>  
    </complexType>  
  
    <complexType name="myComplexTypeB">  
        <simpleContent>  
            <restriction base="ns:myComplexTypeA">  
                <simpleType>  
                    <restriction base="int">  
                        <minExclusive value="25"/>  
                    </restriction>  
                </simpleType>  
            </restriction>  
        </simpleContent>  
    </complexType>  
</schema>  
'  
GO  
```  
  
## См. также:  
 [Требования и ограничения для коллекций XML-схем на сервере](../../relational-databases/xml/requirements-and-limitations-for-xml-schema-collections-on-the-server.md)  
  
  