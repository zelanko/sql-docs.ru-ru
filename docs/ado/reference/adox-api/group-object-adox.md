---
description: Объект Group (ADOX)
title: Объект Group (ADOX) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
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
ms.openlocfilehash: aeeaf4d849efbfe2549a1c4f20b3689048b43a24
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88440016"
---
# <a name="group-object-adox"></a>Объект Group (ADOX)
Представляет учетную запись группы, имеющую разрешения на доступ в защищенной базе данных.  
  
## <a name="remarks"></a>Remarks  
 Коллекция [Groups](../../../ado/reference/adox-api/groups-collection-adox.md) [каталога](../../../ado/reference/adox-api/catalog-object-adox.md) представляет все учетные записи групп каталога. Коллекция **Groups** для [пользователя](../../../ado/reference/adox-api/user-object-adox.md) представляет только группу, к которой принадлежит пользователь.  
  
 С помощью свойств, коллекций и методов объекта **Group** можно:  
  
-   Найдите группу с помощью свойства [Name](../../../ado/reference/adox-api/name-property-adox.md) .  
  
-   Определите, имеет ли группа разрешения на чтение, запись или удаление [с помощью методов](../../../ado/reference/adox-api/getpermissions-method-adox.md) [SetPermissions](../../../ado/reference/adox-api/setpermissions-method-adox.md) и.  
  
-   Доступ к учетным записям пользователей, имеющим членство в группе, с помощью коллекции [пользователей](../../../ado/reference/adox-api/users-collection-adox.md) .  
  
-   Доступ к свойствам, зависящим от поставщика, с коллекцией [свойств](../../../ado/reference/ado-api/properties-collection-ado.md) .  
  
 Этот раздел содержит следующий раздел.  
  
-   [Свойства, методы и события объекта Group](../../../ado/reference/adox-api/group-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>См. также:  
 [Коллекция Groups (ADOX)](../../../ado/reference/adox-api/groups-collection-adox.md)   
 [Коллекция Users (ADOX)](../../../ado/reference/adox-api/users-collection-adox.md)
