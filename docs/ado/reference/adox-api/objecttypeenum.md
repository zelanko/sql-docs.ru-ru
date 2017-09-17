---
title: "ObjectTypeEnum | Документы Microsoft"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- ObjectTypeEnum
helpviewer_keywords:
- ObjectTypeEnum enumeration [ADOX]
ms.assetid: 3fdecfca-aa91-4596-ad98-610f1b7f840b
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 8eb88d7f3df60d8c54782d20af73e3fd5e917db3
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="objecttypeenum"></a>ObjectTypeEnum
Указывает тип объекта базы данных, для которого требуется задать разрешения или его владельца.  
  
|Константа|Значение|Description|  
|--------------|-----------|-----------------|  
|**adPermObjColumn**|2|Объект является столбцом.|  
|**adPermObjDatabase**|3|Объект является базой данных.|  
|**adPermObjProcedure**|4|Объект не является процедурой.|  
|**adPermObjProviderSpecific**|-1|Объект является типом, определяемым поставщиком. Если произойдет ошибка *ObjectType* параметр **adPermObjProviderSpecific** и *ObjectTypeId* не задано.|  
|**adPermObjTable**|1|Объект является таблицей.|  
|**adPermObjView**|5|Объект является представлением.|  
  
## <a name="applies-to"></a>Объект применения  
  
|||  
|-|-|  
|[Метод GetObjectOwner (ADOX)](../../../ado/reference/adox-api/getobjectowner-method-adox.md)|[Метод GetPermissions (ADOX)](../../../ado/reference/adox-api/getpermissions-method-adox.md)|  
|[Метод SetObjectOwner](../../../ado/reference/adox-api/setobjectowner-method.md)|[Метод SetPermissions (ADOX)](../../../ado/reference/adox-api/setpermissions-method-adox.md)|
