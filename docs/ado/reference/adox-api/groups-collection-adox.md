---
description: Коллекция Groups (ADOX)
title: Коллекция Groups (ADOX) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Groups
- User::Groups
- Catalog::Groups
helpviewer_keywords:
- Groups collection [ADOX]
ms.assetid: 09aa7b0a-69d5-4564-80a7-20ad8189670f
author: rothja
ms.author: jroth
ms.openlocfilehash: 70c32ba5e4726aca7d6ad8b37c7df082d25b94b0
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88439996"
---
# <a name="groups-collection-adox"></a>Коллекция Groups (ADOX)
Содержит все сохраненные объекты [групп](../../../ado/reference/adox-api/group-object-adox.md) каталога или пользователя.  
  
## <a name="remarks"></a>Remarks  
 Коллекция **Groups** [каталога](../../../ado/reference/adox-api/catalog-object-adox.md) представляет все учетные записи групп каталога. Коллекция **Groups** для [пользователя](../../../ado/reference/adox-api/user-object-adox.md) представляет только группу, к которой принадлежит пользователь.  
  
 Метод [append](../../../ado/reference/adox-api/append-method-adox-groups.md) для коллекции **GROUPS** уникален для ADOX. Вы можете:  
  
-   Добавьте новую группу безопасности в коллекцию с помощью метода **append** .  
  
 Остальные свойства и методы являются стандартными для коллекций ADO. Вы можете:  
  
-   Доступ к группе в коллекции со свойством [Item](../../../ado/reference/ado-api/item-property-ado.md) .  
  
-   Возвращает количество групп, содержащихся в коллекции, с помощью свойства [Count](../../../ado/reference/ado-api/count-property-ado.md) .  
  
-   Удалите группу из коллекции с помощью метода [Delete](../../../ado/reference/adox-api/delete-method-adox-collections.md) .  
  
-   Обновите объекты в коллекции, чтобы отразить текущую схему базы данных методом [Refresh](../../../ado/reference/ado-api/refresh-method-ado.md) .  
  
> [!NOTE]
>  Перед добавлением объекта **группы** в коллекцию **Groups** объекта **пользователя** объект **группы** с тем же [именем](../../../ado/reference/adox-api/name-property-adox.md) , что и один из добавляемых, должен уже существовать в коллекции **Groups** **каталога**.  
  
 Этот раздел содержит следующий раздел.  
  
-   [Свойства, методы и события коллекции Groups](../../../ado/reference/adox-api/groups-collection-properties-methods-and-events.md)  
  
## <a name="see-also"></a>См. также:  
 [Объект каталога (ADOX)](../../../ado/reference/adox-api/catalog-object-adox.md)   
 [Объект Group (ADOX)](../../../ado/reference/adox-api/group-object-adox.md)
