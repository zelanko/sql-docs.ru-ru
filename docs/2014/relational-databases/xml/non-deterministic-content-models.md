---
title: Недетерминированные модели содержимого | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- non-deterministic content models
- content models [XML in SQL Server]
ms.assetid: 9d4513e7-dd19-4491-b7c7-28bc7c2f8589
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ea86115b88c693e70faa677fdea518f8886bae0f
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63241240"
---
# <a name="non-deterministic-content-models"></a>недетерминированные модели содержимого
  В версиях, предшествующих [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] с пакетом обновления 1 (SP1), схемы XML, содержащие недетерминированные модели содержимого, отклонялись [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 Начиная с версии [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] с пакетом обновления 1 (SP1) недетерминированные модели содержимого принимаются, если ограничение вхождений равно 0, 1 или без ограничений.  
  
## <a name="example-non-deterministic-content-model-rejected"></a>Пример Недетерминированные модели содержимого отклоняются  
 В следующем примере предпринимается попытка создать XML-схему с недетерминированной моделью содержимого. Выполнение этого кода приведет к ошибке, поскольку неясно, должен ли элемент `<root>` содержать последовательность из двух элементов `<a>` или же элемент `<root>` должен содержать две последовательности, состоящие из элемента `<a>` .  
  
```  
CREATE XML SCHEMA COLLECTION MyCollection AS '  
<schema xmlns="http://www.w3.org/2001/XMLSchema">  
    <element name="root">  
        <complexType>  
            <sequence minOccurs="1" maxOccurs="2">  
                <element name="a" type="string" minOccurs="1" maxOccurs="2"/>  
            </sequence>  
        </complexType>  
    </element>  
</schema>  
'  
GO  
```  
  
 Эту схему можно исправить перемещением ограничения вхождения в однозначное расположение. Например, ограничение можно переместить в содержащий последовательность примитив:  
  
```  
<sequence minOccurs="1" maxOccurs="4">  
    <element name="a" type="string" minOccurs="1" maxOccurs="1"/>  
</sequence>  
```  
  
 Ограничение можно также переместить во вложенный элемент:  
  
```  
<sequence minOccurs="1" maxOccurs="1">  
     <element name="a" type="string" minOccurs="1" maxOccurs="4"/>  
</sequence>  
```  
  
## <a name="example-non-deterministic-content-model-accepted"></a>Пример Недетерминированные модели содержимого принимаются  
 Следующая схема отклоняется в версиях [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , предшествующих [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] с пакетом обновления 1 (SP1).  
  
```  
CREATE XML SCHEMA COLLECTION MyCollection AS '  
<schema xmlns="http://www.w3.org/2001/XMLSchema">  
    <element name="root">  
        <complexType>  
            <sequence minOccurs="0" maxOccurs="unbounded">  
                <element name="a" type="string" minOccurs="0" maxOccurs="1"/>  
                <element name="b" type="string" minOccurs="1" maxOccurs="unbounded"/>  
            </sequence>  
        </complexType>  
    </element>  
</schema>  
'  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [Требования и ограничения для коллекций XML-схем на сервере](requirements-and-limitations-for-xml-schema-collections-on-the-server.md)  
  
  
