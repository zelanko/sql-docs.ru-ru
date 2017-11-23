---
title: "Объект пользователя (ADOX) | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords: User
helpviewer_keywords: User object [ADOX]
ms.assetid: f68e32ce-ef7c-407d-bdb5-d280947ae0e2
caps.latest.revision: "12"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: a34d35adf84e32738733184430160613ef8eca45
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="user-object-adox"></a>Объект пользователя (ADOX)
Представляет учетную запись пользователя, имеет разрешения на доступ в защищенной базы данных.  
  
## <a name="remarks"></a>Замечания  
 [Пользователей](../../../ado/reference/adox-api/users-collection-adox.md) коллекцию [каталога](../../../ado/reference/adox-api/catalog-object-adox.md) представляет каталог пользователей. **Пользователей** коллекции для [группы](../../../ado/reference/adox-api/group-object-adox.md) представляет только определенной группе пользователей.  
  
 С помощью свойств, коллекций и методов **пользователя** объекта, вы можете:  
  
-   Идентификации пользователя с [имя](../../../ado/reference/adox-api/name-property-adox.md) свойства.  
  
-   Изменение пароля для пользователя с [ChangePassword](../../../ado/reference/adox-api/changepassword-method-adox.md) метод.  
  
-   Определить, является ли учетной записи пользователя, запись или удаление разрешений с [GetPermissions](../../../ado/reference/adox-api/getpermissions-method-adox.md) и [SetPermissions](../../../ado/reference/adox-api/setpermissions-method-adox.md) методы.  
  
-   Доступ к групп, к которым принадлежит пользователь, с [группы](../../../ado/reference/adox-api/groups-collection-adox.md) коллекции.  
  
-   Доступ к свойствам определенного поставщика с [свойства](../../../ado/reference/ado-api/properties-collection-ado.md) коллекции.  
  
-   Определить [ParentCatalog](../../../ado/reference/adox-api/parentcatalog-property-adox.md) для пользователя.  
  
 Этот раздел содержит следующий раздел.  
  
-   [Свойства, методы и события объекта User](../../../ado/reference/adox-api/user-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>См. также:  
 [GetPermissions и пример SetPermissions методы (Visual Basic)](../../../ado/reference/adox-api/getpermissions-and-setpermissions-methods-example-vb.md)   
 [Коллекция групп (ADOX)](../../../ado/reference/adox-api/groups-collection-adox.md)   
 [Коллекция Users (ADOX)](../../../ado/reference/adox-api/users-collection-adox.md)
