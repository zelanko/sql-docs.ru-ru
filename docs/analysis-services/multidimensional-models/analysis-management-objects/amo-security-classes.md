---
title: "Классы безопасности AMO | Документы Microsoft"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- Analysis Management Objects, security
- security [AMO]
- AMO, security
ms.assetid: e3d5012a-8121-40de-9244-1fc824228693
caps.latest.revision: 23
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: b61917a7e0191e1645dedef69a311a8f901d12b9
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="amo-security-classes"></a>Классы безопасности объектов AMO
  Этот раздел состоит из следующих подразделов.  
  
-   [Объекты role и RoleMember](#RolesMembers)  
  
-   [Объекты разрешений](#Permissions)  
  
 На следующем рисунке показана связь между классами, описываемыми в этом разделе.  
  
 ![В этом разделе рассматриваются классы безопасности AMO](../../../analysis-services/multidimensional-models/analysis-management-objects/media/amo-securityclasses.gif "в этом разделе рассматриваются классы безопасности AMO")  
  
##  <a name="RolesMembers"></a>Объекты role и RoleMember  
 Объект <xref:Microsoft.AnalysisServices.Role> создается путем добавления его в коллекцию ролей базы данных и обновления объекта <xref:Microsoft.AnalysisServices.Role> до сервера при помощи метода Update. Перед использованием объект <xref:Microsoft.AnalysisServices.Role> необходимо обновить.  
  
 Чтобы удалить объект <xref:Microsoft.AnalysisServices.Role>, к нему необходимо применить метод Drop объекта <xref:Microsoft.AnalysisServices.Role>. Метод Remove из коллекции ролей лишь скрывает роль в приложении, но не удаляет ее с сервера. Объект <xref:Microsoft.AnalysisServices.Role> нельзя удалить, если с ним ассоциированы какие-либо разрешения.  
  
 Объект <xref:Microsoft.AnalysisServices.RoleMember> создается путем добавления пользователя в коллекцию элементов роли и обновления объекта <xref:Microsoft.AnalysisServices.Role> до сервера при помощи метода Update. Роли разрешено создавать только администраторам сервера или базы данных. Объект <xref:Microsoft.AnalysisServices.Role> необходимо обновить на сервере, чтобы любой из его элементов смог использовать какие-либо объекты, разрешения на которые предоставлены пользователю.  
  
 Чтобы удалить объект <xref:Microsoft.AnalysisServices.RoleMember>, его необходимо удалить из коллекции при помощи метода Remove коллекции, а затем обновить роли с помощью метода Update.  
  
 Дополнительные сведения о методах и свойствах, допустимых для этих объектов, см. в разделах <xref:Microsoft.AnalysisServices.Role> и <xref:Microsoft.AnalysisServices.RoleMember> в <xref:Microsoft.AnalysisServices>.  
  
##  <a name="Permissions"></a>Объекты разрешений  
 Объект <xref:Microsoft.AnalysisServices.Permission> создается путем добавления его в коллекцию разрешений объекта и обновления объекта <xref:Microsoft.AnalysisServices.Permission> до сервера при помощи метода Update.  
  
 Чтобы удалить объект <xref:Microsoft.AnalysisServices.Permission>, к нему необходимо применить метод Drop объекта. Метод Remove из коллекции разрешений лишь исключает возможность видеть разрешение в приложении, а не удаляет объект <xref:Microsoft.AnalysisServices.Permission> с сервера. Если с ролью ассоциировано какое-либо разрешение, ее невозможно удалить.  
  
 Дополнительные сведения о доступных методах и свойствах см. в описании класса <xref:Microsoft.AnalysisServices.Permission> из пространства имен <xref:Microsoft.AnalysisServices>.  
  
## <a name="see-also"></a>См. также:  
 <xref:Microsoft.AnalysisServices>   
 [Программирование объектов безопасности AMO](../../../analysis-services/multidimensional-models/analysis-management-objects/programming-amo-security-objects.md)   
 [Разрешения и права доступа &#40; Analysis Services — многомерные данные &#41;](http://msdn.microsoft.com/library/59fa3573-f985-46cb-8042-7da71bd59a7b)   
 [Знакомство с классами объектов AMO](../../../analysis-services/multidimensional-models/analysis-management-objects/amo-classes-introduction.md)   
 [Логическая архитектура &#40; Analysis Services — многомерные данные &#41;](../../../analysis-services/multidimensional-models/olap-logical/understanding-microsoft-olap-logical-architecture.md)   
 [Объекты базы данных &#40; Analysis Services — многомерные данные &#41;](../../../analysis-services/multidimensional-models/olap-logical/database-objects-analysis-services-multidimensional-data.md)  
  
  

