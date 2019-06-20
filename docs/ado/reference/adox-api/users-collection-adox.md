---
title: Коллекция Users (ADOX) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Group::Users
- Users
- Catalog::Users
helpviewer_keywords:
- Users collection [ADOX]
ms.assetid: 0a30fa74-6f10-4410-bd70-882e7c43cd46
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: bbf05e0b177cc61ed9de757db46f8950aaa7dccd
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66705626"
---
# <a name="users-collection-adox"></a>Коллекция Users (ADOX)
Содержит все хранящиеся [пользователя](../../../ado/reference/adox-api/user-object-adox.md) объектов [каталога](../../../ado/reference/adox-api/catalog-object-adox.md) или [группы](../../../ado/reference/adox-api/group-object-adox.md).  
  
## <a name="remarks"></a>Примечания  
 **Пользователей** коллекцию [каталога](../../../ado/reference/adox-api/catalog-object-adox.md) представляет пользователей каталога. **Пользователей** коллекции для [группы](../../../ado/reference/adox-api/group-object-adox.md) представляет только пользователи, имеющие членства в определенной группе.  
  
 [Append](../../../ado/reference/adox-api/append-method-adox-users.md) метод **пользователей** является уникальным для ADOX. Можно выполнить следующие действия:  
  
-   Добавить нового пользователя в коллекцию с помощью **Append** метод.  
  
 Остальные свойства и методы являются стандартными для коллекции ADO. Можно выполнить следующие действия:  
  
-   Права пользователя в коллекции с [элемент](../../../ado/reference/ado-api/item-property-ado.md) свойство.  
  
-   Возвращает количество пользователей, содержащихся в коллекции с [число](../../../ado/reference/ado-api/count-property-ado.md) свойство.  
  
-   Удаление пользователя из коллекции с [удалить](../../../ado/reference/adox-api/delete-method-adox-collections.md) метод.  
  
-   Обновление объектов в коллекции в соответствии с текущей базы данных схемы с [обновить](../../../ado/reference/ado-api/refresh-method-ado.md) метод.  
  
> [!NOTE]
>  Перед добавлением **пользователя** объект **пользователей** коллекцию **группы** объекта, **пользователя** с тем же [имя ](../../../ado/reference/adox-api/name-property-adox.md) как один, который будет добавляться уже должен существовать в **пользователей** коллекцию **каталога**.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Свойства, методы и события коллекции Users](../../../ado/reference/adox-api/users-collection-properties-methods-and-events.md)  
  
## <a name="see-also"></a>См. также  
 [GetPermissions и SetPermissions методы (Visual Basic)](../../../ado/reference/adox-api/getpermissions-and-setpermissions-methods-example-vb.md)   
 [Объект Catalog (ADOX)](../../../ado/reference/adox-api/catalog-object-adox.md)   
 [Объект User (ADOX)](../../../ado/reference/adox-api/user-object-adox.md)
