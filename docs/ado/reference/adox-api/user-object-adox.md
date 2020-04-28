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
ms.openlocfilehash: cf454e28e7a823eb643b5bbd92b0396fac15a028
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "67964978"
---
# <a name="user-object-adox"></a>Объект User (ADOX)
Представляет учетную запись пользователя, имеющую разрешения на доступ в защищенной базе данных.  
  
## <a name="remarks"></a>Remarks  
 Коллекция [пользователей](../../../ado/reference/adox-api/users-collection-adox.md) [каталога](../../../ado/reference/adox-api/catalog-object-adox.md) представляет всех пользователей каталога. Коллекция **пользователей** для [группы](../../../ado/reference/adox-api/group-object-adox.md) представляет только пользователей определенной группы.  
  
 С помощью свойств, коллекций и методов **пользовательского** объекта можно выполнять следующие действия:  
  
-   Выясните пользователя с помощью свойства [Name](../../../ado/reference/adox-api/name-property-adox.md) .  
  
-   Измените пароль для пользователя с помощью метода [ChangePassword](../../../ado/reference/adox-api/changepassword-method-adox.md) .  
  
-   Определите, имеет ли пользователь разрешения на чтение, запись или удаление [с помощью методов](../../../ado/reference/adox-api/getpermissions-method-adox.md) [SetPermissions](../../../ado/reference/adox-api/setpermissions-method-adox.md) и.  
  
-   Доступ к группам, к которым принадлежит пользователь, с коллекцией [Groups](../../../ado/reference/adox-api/groups-collection-adox.md) .  
  
-   Доступ к свойствам, зависящим от поставщика, с коллекцией [свойств](../../../ado/reference/ado-api/properties-collection-ado.md) .  
  
-   Определите [ParentCatalog](../../../ado/reference/adox-api/parentcatalog-property-adox.md) для пользователя.  
  
 Этот раздел содержит следующий раздел.  
  
-   [Свойства, методы и события объекта User](../../../ado/reference/adox-api/user-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>См. также:  
 [Примеры методов SetPermissions и Methods (Visual Basic)](../../../ado/reference/adox-api/getpermissions-and-setpermissions-methods-example-vb.md)   
 [Коллекция Groups (ADOX)](../../../ado/reference/adox-api/groups-collection-adox.md)   
 [Коллекция Users (ADOX)](../../../ado/reference/adox-api/users-collection-adox.md)
