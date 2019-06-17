---
title: Объект User (ADOX) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- User
helpviewer_keywords:
- User object [ADOX]
ms.assetid: f68e32ce-ef7c-407d-bdb5-d280947ae0e2
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 6fb3ebf1921bf0e61fe9d5a8dcf9fc2cd0dce6c1
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66705643"
---
# <a name="user-object-adox"></a>Объект User (ADOX)
Представляет учетную запись пользователя, имеет разрешения на доступ в рамках защищенной базы данных.  
  
## <a name="remarks"></a>Примечания  
 [Пользователей](../../../ado/reference/adox-api/users-collection-adox.md) коллекцию [каталога](../../../ado/reference/adox-api/catalog-object-adox.md) представляет пользователей каталога. **Пользователей** коллекции для [группы](../../../ado/reference/adox-api/group-object-adox.md) представляет только пользователей из определенной группы.  
  
 С помощью свойств, коллекций и методы **пользователя** объекта, вы можете:  
  
-   Идентификации пользователя с [имя](../../../ado/reference/adox-api/name-property-adox.md) свойство.  
  
-   Изменение пароля для пользователя с [ChangePassword](../../../ado/reference/adox-api/changepassword-method-adox.md) метод.  
  
-   Определить, имеет ли пользователь чтение, запись или удаление разрешений с [GetPermissions](../../../ado/reference/adox-api/getpermissions-method-adox.md) и [SetPermissions](../../../ado/reference/adox-api/setpermissions-method-adox.md) методы.  
  
-   Доступ к группам, к которым принадлежит пользователь, с помощью [группы](../../../ado/reference/adox-api/groups-collection-adox.md) коллекции.  
  
-   Доступ к свойствам поставщика с [свойства](../../../ado/reference/ado-api/properties-collection-ado.md) коллекции.  
  
-   Определить [ParentCatalog](../../../ado/reference/adox-api/parentcatalog-property-adox.md) для пользователя.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Свойства, методы и события объекта User](../../../ado/reference/adox-api/user-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>См. также  
 [GetPermissions и SetPermissions методы (Visual Basic)](../../../ado/reference/adox-api/getpermissions-and-setpermissions-methods-example-vb.md)   
 [Коллекция Groups (ADOX)](../../../ado/reference/adox-api/groups-collection-adox.md)   
 [Коллекция Users (ADOX)](../../../ado/reference/adox-api/users-collection-adox.md)
