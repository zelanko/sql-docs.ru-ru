---
title: Аспекты перечисления | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-xml
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- enumeration facets
ms.assetid: dec23a79-ddd6-4701-9721-55a2c435a34d
caps.latest.revision: 8
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: bf9f843f840c5f174bafe0dbdd5dff46bf55c4f2
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37227054"
---
# <a name="enumeration-facets"></a>аспекты перечисления
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] отклоняет XML-схемы с типами, которые имеют шаблоны аспектов или перечислений, нарушающих эти аспекты.  
  
## <a name="example"></a>Пример  
 Следующая схема была бы отклонена, потому что показанное значение перечисления включает значение, содержащее символы в разных регистрах. Она также была бы отклонена, потому что это значение нарушает значение шаблона, которое ограничивает значения только символами нижнего регистра.  
  
```  
CREATE XML SCHEMA COLLECTION MySampleCollection AS '  
<schema xmlns="http://www.w3.org/2001/XMLSchema" targetNamespace="http://ns" xmlns:ns="http://ns">  
    <simpleType name="MyST">  
       <restriction base="string">  
          <pattern value="[a-z]*"/>  
       </restriction>  
    </simpleType>  
  
    <simpleType name="MyST2">  
       <restriction base="ns:MyST">  
           <enumeration value="mYstring"/>  
       </restriction>  
    </simpleType>  
</schema>'  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [Требования и ограничения для коллекций схем XML на сервере](requirements-and-limitations-for-xml-schema-collections-on-the-server.md)  
  
  
