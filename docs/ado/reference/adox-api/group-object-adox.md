---
title: Группы объектов (ADOX) | Документы Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Group
helpviewer_keywords:
- group object [ADOX]
ms.assetid: 55ef0ade-68ea-4da5-8aa5-4cd27d1f6d1e
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 36c26ab9fd3fc92f0636adaff725ef37b181a081
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/11/2018
ms.locfileid: "35286033"
---
# <a name="group-object-adox"></a>Объект группы (ADOX)
Представляет учетную запись группы, имеющую разрешения на доступ в защищенной базы данных.  
  
## <a name="remarks"></a>Примечания  
 [Группы](../../../ado/reference/adox-api/groups-collection-adox.md) коллекцию [каталога](../../../ado/reference/adox-api/catalog-object-adox.md) представляет учетные записи групп каталога. **Группы** коллекции для [пользователя](../../../ado/reference/adox-api/user-object-adox.md) представляет группу, к которой принадлежит пользователь.  
  
 С помощью свойств, коллекций и методов **группы** объекта, вы можете:  
  
-   Идентифицировать группу с [имя](../../../ado/reference/adox-api/name-property-adox.md) свойства.  
  
-   Проверить группу чтения, записи или удаления разрешений с [GetPermissions](../../../ado/reference/adox-api/getpermissions-method-adox.md) и [SetPermissions](../../../ado/reference/adox-api/setpermissions-method-adox.md) методы.  
  
-   Доступ к учетные записи пользователей, имеющих членства в группе с [пользователей](../../../ado/reference/adox-api/users-collection-adox.md) коллекции.  
  
-   Доступ к свойствам определенного поставщика с [свойства](../../../ado/reference/ado-api/properties-collection-ado.md) коллекции.  
  
 Этот раздел содержит следующий раздел.  
  
-   [Свойства, методы и события объекта Group](../../../ado/reference/adox-api/group-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>См. также  
 [Коллекция групп (ADOX)](../../../ado/reference/adox-api/groups-collection-adox.md)   
 [Коллекция Users (ADOX)](../../../ado/reference/adox-api/users-collection-adox.md)
