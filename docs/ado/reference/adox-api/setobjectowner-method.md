---
title: Метод SetObjectOwner | Документы Microsoft
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
- _Catalog::SetObjectOwner
- _Catalog::raw_SetObjectOwner
helpviewer_keywords:
- SetObjectOwner method [ADOX]
ms.assetid: e5170a37-9d6e-43db-bfb6-9b6631fa3048
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a3d3642d0641a55bdb476998b722a04dc81edf10
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2018
---
# <a name="setobjectowner-method"></a>Метод SetObjectOwner
Указывает владельца объекта в [каталога](../../../ado/reference/adox-api/catalog-object-adox.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Catalog.SetObjectOwner ObjectName, ObjectType, OwnerName [,ObjectTypeId]  
```  
  
#### <a name="parameters"></a>Параметры  
 *ObjectName*  
 Объект **строка** значение, указывающее имя объекта, для которого требуется задать владельца.  
  
 *ObjectType*  
 Объект **длинные** значение может быть одним из [ObjectTypeEnum](../../../ado/reference/adox-api/objecttypeenum.md) константы, которое указывает тип владельца.  
  
 *OwnerName*  
 Объект **строка** значение, указывающее [имя](../../../ado/reference/adox-api/name-property-adox.md) из [пользователя](../../../ado/reference/adox-api/user-object-adox.md) или [группы](../../../ado/reference/adox-api/group-object-adox.md) быть владельцем объекта.  
  
 *ObjectTypeId*  
 Необязательно. Объект **Variant** значение, которое указывает идентификатор GUID для типа объекта поставщика, не определенных в спецификации OLE DB. Этот параметр является обязательным, если *ObjectType* равно **adPermObjProviderSpecific**; в противном случае он не используется.  
  
## <a name="remarks"></a>Замечания  
 Если поставщик не поддерживает указание владельцы объектов, произойдет ошибка.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Catalog (ADOX)](../../../ado/reference/adox-api/catalog-object-adox.md)  
  
## <a name="see-also"></a>См. также  
 [GetObjectOwner и пример SetObjectOwner методы (Visual Basic)](../../../ado/reference/adox-api/getobjectowner-and-setobjectowner-methods-example-vb.md)   
 [Метод GetObjectOwner (ADOX)](../../../ado/reference/adox-api/getobjectowner-method-adox.md)
