---
title: Смешанный тип и простое содержимое | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- mixed types [SQL Server]
ms.assetid: 6ea1f11d-e64b-4ebb-ab68-4eb6e4027665
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: cf0e4f54334d84aea5a33392655110374e893cc4
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "63241271"
---
# <a name="mixed-type-and-simple-content"></a>Смешанный тип и простое содержимое
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не поддерживает ограничение смешанного типа простым содержимым.  
  
## <a name="example"></a>Пример  
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
  
## <a name="see-also"></a>См. также:  
 [Требования и ограничения для коллекций схем XML на сервере](requirements-and-limitations-for-xml-schema-collections-on-the-server.md)  
  
  
