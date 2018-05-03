---
title: ObjectTypeEnum | Документы Microsoft
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
- ObjectTypeEnum
helpviewer_keywords:
- ObjectTypeEnum enumeration [ADOX]
ms.assetid: 3fdecfca-aa91-4596-ad98-610f1b7f840b
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 075791708909b42144deb8193d5ccbdcf75a2044
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="objecttypeenum"></a>ObjectTypeEnum
Указывает тип объекта базы данных, для которого требуется задать разрешения или его владельца.  
  
|Константа|Значение|Описание|  
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
