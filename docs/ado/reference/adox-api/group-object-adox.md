---
title: Сгруппировать объект (ADOX) | Документация Майкрософт
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: b4b3de5f445ddd09bf7d069b0b93d82c6f8de978
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67966210"
---
# <a name="group-object-adox"></a>Объект Group (ADOX)
Представляет учетную запись группы, имеющую разрешения на доступ в рамках защищенной базы данных.  
  
## <a name="remarks"></a>Примечания  
 [Группы](../../../ado/reference/adox-api/groups-collection-adox.md) коллекцию [каталога](../../../ado/reference/adox-api/catalog-object-adox.md) представляет учетные записи групп каталога. **Группы** коллекции для [пользователя](../../../ado/reference/adox-api/user-object-adox.md) представляет только группы, к которой принадлежит пользователь.  
  
 С помощью свойств, коллекций и методы **группы** объекта, вы можете:  
  
-   Идентифицировать группу с [имя](../../../ado/reference/adox-api/name-property-adox.md) свойство.  
  
-   Определить, имеет ли чтение группы, записи или удаления разрешений с помощью [GetPermissions](../../../ado/reference/adox-api/getpermissions-method-adox.md) и [SetPermissions](../../../ado/reference/adox-api/setpermissions-method-adox.md) методы.  
  
-   Доступ к учетным записям пользователя, имеющих членства в группе с [пользователей](../../../ado/reference/adox-api/users-collection-adox.md) коллекции.  
  
-   Доступ к свойствам поставщика с [свойства](../../../ado/reference/ado-api/properties-collection-ado.md) коллекции.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Свойства, методы и события объекта Group](../../../ado/reference/adox-api/group-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>См. также  
 [Коллекция Groups (ADOX)](../../../ado/reference/adox-api/groups-collection-adox.md)   
 [Коллекция Users (ADOX)](../../../ado/reference/adox-api/users-collection-adox.md)
