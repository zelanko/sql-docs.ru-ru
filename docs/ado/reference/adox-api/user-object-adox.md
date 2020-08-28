---
description: Объект User (ADOX)
title: Объект User (ADOX) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 6e83bd40c226f1d5b5948c6475b259c799907866
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2020
ms.locfileid: "88983054"
---
# <a name="user-object-adox"></a>Объект User (ADOX)
Представляет учетную запись пользователя, имеющую разрешения на доступ в защищенной базе данных.  
  
## <a name="remarks"></a>Remarks  
 Коллекция [пользователей](./users-collection-adox.md) [каталога](./catalog-object-adox.md) представляет всех пользователей каталога. Коллекция **пользователей** для [группы](./group-object-adox.md) представляет только пользователей определенной группы.  
  
 С помощью свойств, коллекций и методов **пользовательского** объекта можно выполнять следующие действия:  
  
-   Выясните пользователя с помощью свойства [Name](./name-property-adox.md) .  
  
-   Измените пароль для пользователя с помощью метода [ChangePassword](./changepassword-method-adox.md) .  
  
-   Определите, имеет ли пользователь разрешения на чтение, запись или удаление [с помощью методов](./getpermissions-method-adox.md) [SetPermissions](./setpermissions-method-adox.md) и.  
  
-   Доступ к группам, к которым принадлежит пользователь, с коллекцией [Groups](./groups-collection-adox.md) .  
  
-   Доступ к свойствам, зависящим от поставщика, с коллекцией [свойств](../ado-api/properties-collection-ado.md) .  
  
-   Определите [ParentCatalog](./parentcatalog-property-adox.md) для пользователя.  
  
 Этот раздел содержит следующий раздел.  
  
-   [Свойства, методы и события объекта User](./user-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>См. также  
 [Примеры методов SetPermissions и Methods (Visual Basic)](./getpermissions-and-setpermissions-methods-example-vb.md)   
 [Коллекция Groups (ADOX)](./groups-collection-adox.md)   
 [Коллекция Users (ADOX)](./users-collection-adox.md)