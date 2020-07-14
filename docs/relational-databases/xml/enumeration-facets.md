---
title: Аспекты перечисления | Документация Майкрософт
description: Узнайте, как SQL Server использует аспекты перечисления для проверки XML-схем.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- enumeration facets
ms.assetid: dec23a79-ddd6-4701-9721-55a2c435a34d
author: MightyPen
ms.author: genemi
ms.openlocfilehash: e8939b3c8654452f50b280ad66fe221f94220754
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85633136"
---
# <a name="enumeration-facets"></a>аспекты перечисления
[!INCLUDE [SQL Server Azure SQL Database](../../includes/applies-to-version/sql-asdb.md)]
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
  
## <a name="see-also"></a>См. также:  
 [Требования и ограничения для коллекций схем XML на сервере](../../relational-databases/xml/requirements-and-limitations-for-xml-schema-collections-on-the-server.md)  
  
  
