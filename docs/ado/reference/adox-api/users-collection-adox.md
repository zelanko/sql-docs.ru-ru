---
title: Коллекция пользователей (ADOX) | Документация Майкрософт
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 4befb68c861edee0f5c1423e86ee1fb21067c2a5
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2020
ms.locfileid: "82753172"
---
# <a name="users-collection-adox"></a>Коллекция Users (ADOX)
Содержит все сохраненные [пользовательские](../../../ado/reference/adox-api/user-object-adox.md) объекты [каталога](../../../ado/reference/adox-api/catalog-object-adox.md) или [группы](../../../ado/reference/adox-api/group-object-adox.md).  
  
## <a name="remarks"></a>Remarks  
 Коллекция **пользователей** [каталога](../../../ado/reference/adox-api/catalog-object-adox.md) представляет всех пользователей каталога. Коллекция **пользователей** для [группы](../../../ado/reference/adox-api/group-object-adox.md) представляет только тех пользователей, которые имеют членство в определенной группе.  
  
 Метод [append](../../../ado/reference/adox-api/append-method-adox-users.md) для коллекции **пользователей** уникален для ADOX. Можно сделать следующее:  
  
-   Добавьте нового пользователя в коллекцию с помощью метода **append** .  
  
 Остальные свойства и методы являются стандартными для коллекций ADO. Можно сделать следующее:  
  
-   Доступ к пользователю в коллекции со свойством [Item](../../../ado/reference/ado-api/item-property-ado.md) .  
  
-   Возвращает число пользователей, содержащихся в коллекции, с помощью свойства [Count](../../../ado/reference/ado-api/count-property-ado.md) .  
  
-   Удалите пользователя из коллекции с помощью метода [Delete](../../../ado/reference/adox-api/delete-method-adox-collections.md) .  
  
-   Обновите объекты в коллекции, чтобы отразить схему текущей базы данных методом [Refresh](../../../ado/reference/ado-api/refresh-method-ado.md) .  
  
> [!NOTE]
>  Перед добавлением объекта **пользователя** в коллекцию **Users** объекта **Group** объект **пользователя** с тем же [именем](../../../ado/reference/adox-api/name-property-adox.md) , что и у добавляемого, должен уже существовать в коллекции **пользователей** **каталога**.  
  
 Этот раздел содержит следующий раздел.  
  
-   [Свойства, методы и события коллекции Users](../../../ado/reference/adox-api/users-collection-properties-methods-and-events.md)  
  
## <a name="see-also"></a>См. также  
 [Примеры методов SetPermissions и Methods (Visual Basic)](../../../ado/reference/adox-api/getpermissions-and-setpermissions-methods-example-vb.md)   
 [Объект каталога (ADOX)](../../../ado/reference/adox-api/catalog-object-adox.md)   
 [Объект User (ADOX)](../../../ado/reference/adox-api/user-object-adox.md)
