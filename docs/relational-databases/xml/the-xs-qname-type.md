---
title: "Тип xs:QName | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-xml
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- xs:QName type
ms.assetid: 72c5bfde-b0b2-4372-bf36-97ba930dea06
caps.latest.revision: 9
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: a8a81cbeff6ba6760c6bd9a686828064c7f0bf7a
ms.contentlocale: ru-ru
ms.lasthandoff: 04/11/2017

---
# <a name="the-xsqname-type"></a>Тип xs:QName
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не поддерживает типы, унаследованные из **xs:QName** и использующие элемент ограничения XML-схемы. Кроме того, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в настоящее время не поддерживает типы объединений с **QName** в качестве типа элемента.  
  
## <a name="example"></a>Пример  
 Следующая инструкция `CREATE XML SCHEMA COLLECTION` не сможет загрузить XML-схему, так как указан тип `xs:QName` в качестве типа объединения:  
  
```  
CREATE XML SCHEMA COLLECTION QNameLimitation1 AS N'  
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema">  
    <xs:simpleType name="myUnion">  
        <xs:union memberTypes="xs:int xs:QName"/>  
    </xs:simpleType>  
</xs:schema>'  
GO  
  
CREATE XML SCHEMA COLLECTION QNameLimitation2 AS N'  
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema">  
    <xs:simpleType name="myUnion">  
        <xs:union memberTypes="xs:integer">  
   <xs:simpleType>  
    <xs:list itemType="xs:QName"/>  
   </xs:simpleType>  
  </xs:union>  
    </xs:simpleType>  
</xs:schema>'  
GO  
```  
  
 Обе инструкции потерпят неудачу с сообщением об ошибке.  
  
## <a name="see-also"></a>См. также:  
 [Требования и ограничения для коллекций XML-схем на сервере](../../relational-databases/xml/requirements-and-limitations-for-xml-schema-collections-on-the-server.md)  
  
  
