---
description: Коллекция Users (ADOX)
title: Коллекция пользователей (ADOX) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
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
ms.openlocfilehash: a1f511e637696e5b14905bcccba50cb13737d6e7
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2020
ms.locfileid: "88983035"
---
# <a name="users-collection-adox"></a>Коллекция Users (ADOX)
Содержит все сохраненные [пользовательские](./user-object-adox.md) объекты [каталога](./catalog-object-adox.md) или [группы](./group-object-adox.md).  
  
## <a name="remarks"></a>Remarks  
 Коллекция **пользователей** [каталога](./catalog-object-adox.md) представляет всех пользователей каталога. Коллекция **пользователей** для [группы](./group-object-adox.md) представляет только тех пользователей, которые имеют членство в определенной группе.  
  
 Метод [append](./append-method-adox-users.md) для коллекции **пользователей** уникален для ADOX. Вы можете:  
  
-   Добавьте нового пользователя в коллекцию с помощью метода **append** .  
  
 Остальные свойства и методы являются стандартными для коллекций ADO. Вы можете:  
  
-   Доступ к пользователю в коллекции со свойством [Item](../ado-api/item-property-ado.md) .  
  
-   Возвращает число пользователей, содержащихся в коллекции, с помощью свойства [Count](../ado-api/count-property-ado.md) .  
  
-   Удалите пользователя из коллекции с помощью метода [Delete](./delete-method-adox-collections.md) .  
  
-   Обновите объекты в коллекции, чтобы отразить схему текущей базы данных методом [Refresh](../ado-api/refresh-method-ado.md) .  
  
> [!NOTE]
>  Перед добавлением объекта **пользователя** в коллекцию **Users** объекта **Group** объект **пользователя** с тем же [именем](./name-property-adox.md) , что и у добавляемого, должен уже существовать в коллекции **пользователей** **каталога**.  
  
 Этот раздел содержит следующий раздел.  
  
-   [Свойства, методы и события коллекции Users](./users-collection-properties-methods-and-events.md)  
  
## <a name="see-also"></a>См. также  
 [Примеры методов SetPermissions и Methods (Visual Basic)](./getpermissions-and-setpermissions-methods-example-vb.md)   
 [Объект каталога (ADOX)](./catalog-object-adox.md)   
 [Объект User (ADOX)](./user-object-adox.md)