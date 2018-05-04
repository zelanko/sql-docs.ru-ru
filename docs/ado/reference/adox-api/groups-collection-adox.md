---
title: Группирует коллекцию (ADOX) | Документы Microsoft
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Groups
- User::Groups
- Catalog::Groups
helpviewer_keywords:
- Groups collection [ADOX]
ms.assetid: 09aa7b0a-69d5-4564-80a7-20ad8189670f
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1ee212995aa48b00de5a31893547dc7380bd80a7
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="groups-collection-adox"></a>Коллекция групп (ADOX)
Содержит все хранящиеся [группы](../../../ado/reference/adox-api/group-object-adox.md) объекты каталога или пользователя.  
  
## <a name="remarks"></a>Замечания  
 **Группы** коллекцию [каталога](../../../ado/reference/adox-api/catalog-object-adox.md) представляет все учетные записи групп в каталоге. **Группы** коллекции для [пользователя](../../../ado/reference/adox-api/user-object-adox.md) представляет группу, к которой принадлежит пользователь.  
  
 [Append](../../../ado/reference/adox-api/append-method-adox-groups.md) метод **группы** является уникальным для ADOX. Возможные действия:  
  
-   Добавить новую группу безопасности в коллекцию с **Append** метод.  
  
 Остальные свойства и методы являются стандартными коллекциям ADO. Возможные действия:  
  
-   Доступ к группе в коллекции с [элемент](../../../ado/reference/ado-api/item-property-ado.md) свойство.  
  
-   Возвращает количество групп, содержащихся в коллекции с [число](../../../ado/reference/ado-api/count-property-ado.md) свойство.  
  
-   Удаление группы из коллекции с [удалить](../../../ado/reference/adox-api/delete-method-adox-collections.md) метод.  
  
-   Обновление объектов в коллекции в соответствии с текущей схемы базы данных с [обновление](../../../ado/reference/ado-api/refresh-method-ado.md) метод.  
  
> [!NOTE]
>  Перед добавлением **группы** объект **группы** коллекцию **пользователя** объекта, **группы** с тем же [ Имя](../../../ado/reference/adox-api/name-property-adox.md) как один, который будет добавляться уже должен существовать в **группы** коллекцию **каталога**.  
  
 Этот раздел содержит следующий раздел.  
  
-   [Свойства, методы и события коллекции Groups](../../../ado/reference/adox-api/groups-collection-properties-methods-and-events.md)  
  
## <a name="see-also"></a>См. также  
 [Объект каталога (ADOX)](../../../ado/reference/adox-api/catalog-object-adox.md)   
 [Объект Group (ADOX)](../../../ado/reference/adox-api/group-object-adox.md)
