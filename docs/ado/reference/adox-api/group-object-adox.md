---
description: Объект Group (ADOX)
title: Объект Group (ADOX) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Group
helpviewer_keywords:
- group object [ADOX]
ms.assetid: 55ef0ade-68ea-4da5-8aa5-4cd27d1f6d1e
author: rothja
ms.author: jroth
ms.openlocfilehash: 21514bbcbe91e1320a4a2806e545d5f7b40df8d3
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2020
ms.locfileid: "88984435"
---
# <a name="group-object-adox"></a>Объект Group (ADOX)
Представляет учетную запись группы, имеющую разрешения на доступ в защищенной базе данных.  
  
## <a name="remarks"></a>Remarks  
 Коллекция [Groups](./groups-collection-adox.md) [каталога](./catalog-object-adox.md) представляет все учетные записи групп каталога. Коллекция **Groups** для [пользователя](./user-object-adox.md) представляет только группу, к которой принадлежит пользователь.  
  
 С помощью свойств, коллекций и методов объекта **Group** можно:  
  
-   Найдите группу с помощью свойства [Name](./name-property-adox.md) .  
  
-   Определите, имеет ли группа разрешения на чтение, запись или удаление [с помощью методов](./getpermissions-method-adox.md) [SetPermissions](./setpermissions-method-adox.md) и.  
  
-   Доступ к учетным записям пользователей, имеющим членство в группе, с помощью коллекции [пользователей](./users-collection-adox.md) .  
  
-   Доступ к свойствам, зависящим от поставщика, с коллекцией [свойств](../ado-api/properties-collection-ado.md) .  
  
 Этот раздел содержит следующий раздел.  
  
-   [Свойства, методы и события объекта Group](./group-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>См. также  
 [Коллекция Groups (ADOX)](./groups-collection-adox.md)   
 [Коллекция Users (ADOX)](./users-collection-adox.md)