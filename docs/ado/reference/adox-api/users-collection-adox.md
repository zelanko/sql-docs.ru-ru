---
title: "Коллекции пользователей (ADOX) | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- Group::Users
- Users
- Catalog::Users
helpviewer_keywords: Users collection [ADOX]
ms.assetid: 0a30fa74-6f10-4410-bd70-882e7c43cd46
caps.latest.revision: "10"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 84e4484d2902913be2cf2afa615a474aeb2b4bf7
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="users-collection-adox"></a>Коллекции пользователей (ADOX)
Содержит все хранящиеся [пользователя](../../../ado/reference/adox-api/user-object-adox.md) объектов [каталога](../../../ado/reference/adox-api/catalog-object-adox.md) или [группы](../../../ado/reference/adox-api/group-object-adox.md).  
  
## <a name="remarks"></a>Remarks  
 **Пользователей** коллекцию [каталога](../../../ado/reference/adox-api/catalog-object-adox.md) представляет каталог пользователей. **Пользователей** коллекции для [группы](../../../ado/reference/adox-api/group-object-adox.md) представляет только пользователи, имеющие членства в определенной группе.  
  
 [Append](../../../ado/reference/adox-api/append-method-adox-users.md) метод **пользователей** является уникальным для ADOX. Возможные действия:  
  
-   Добавление нового пользователя в коллекцию с помощью **Append** метод.  
  
 Остальные свойства и методы являются стандартными коллекциям ADO. Возможные действия:  
  
-   Права пользователя в коллекции с [элемент](../../../ado/reference/ado-api/item-property-ado.md) свойство.  
  
-   Возвращает количество пользователей, содержащихся в коллекции с [число](../../../ado/reference/ado-api/count-property-ado.md) свойство.  
  
-   Удаление пользователя из коллекции с помощью [удалить](../../../ado/reference/adox-api/delete-method-adox-collections.md) метод.  
  
-   Обновление объектов в коллекции в соответствии с текущей базы данных в схеме с [обновление](../../../ado/reference/ado-api/refresh-method-ado.md) метод.  
  
> [!NOTE]
>  Перед добавлением **пользователя** объект **пользователей** коллекцию **группы** объекта, **пользователя** с тем же [имя ](../../../ado/reference/adox-api/name-property-adox.md) как один, который будет добавляться уже должен существовать в **пользователей** коллекцию **каталога**.  
  
 Этот раздел содержит следующий раздел.  
  
-   [Свойства, методы и события коллекции Users](../../../ado/reference/adox-api/users-collection-properties-methods-and-events.md)  
  
## <a name="see-also"></a>См. также:  
 [GetPermissions и пример SetPermissions методы (Visual Basic)](../../../ado/reference/adox-api/getpermissions-and-setpermissions-methods-example-vb.md)   
 [Объект каталога (ADOX)](../../../ado/reference/adox-api/catalog-object-adox.md)   
 [Объект User (ADOX)](../../../ado/reference/adox-api/user-object-adox.md)
