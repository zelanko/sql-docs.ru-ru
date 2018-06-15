---
title: Метод GetObjectOwner (ADOX) | Документы Microsoft
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
- _Catalog::raw_GetObjectOwner
- _Catalog::GetObjectOwner
helpviewer_keywords:
- GetObjectOwner method [ADOX]
ms.assetid: 8965adf0-9075-4125-8142-73eb700029c3
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 06f3cb14603c7799e7084af407df437b12be4769
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/11/2018
ms.locfileid: "35285923"
---
# <a name="getobjectowner-method-adox"></a>Метод GetObjectOwner (ADOX)
Возвращает владельца объекта в [каталога](../../../ado/reference/adox-api/catalog-object-adox.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Owner = Catalog.GetObjectOwner(ObjectName, ObjectType [,ObjectTypeId])  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает **строка** значение, указывающее [имя](../../../ado/reference/adox-api/name-property-adox.md) из [пользователя](../../../ado/reference/adox-api/user-object-adox.md) или [группы](../../../ado/reference/adox-api/group-object-adox.md) , которому принадлежит объект.  
  
#### <a name="parameters"></a>Параметры  
 *ObjectName*  
 Объект **строка** значение, указывающее имя объекта, для которого требуется возвращать имя владельца.  
  
 *ObjectType*  
 Объект **длинные** значение может быть одним из [ObjectTypeEnum](../../../ado/reference/adox-api/objecttypeenum.md) констант, которые указывает тип объекта, для которого требуется получить владельца.  
  
 *ObjectTypeId*  
 Необязательный параметр. Объект **Variant** значение, которое не указывает идентификатор GUID для типа поставщика объектов, определенных в спецификации OLE DB. Этот параметр является обязательным, если *ObjectType* равно **adPermObjProviderSpecific**; в противном случае он не используется.  
  
## <a name="remarks"></a>Примечания  
 Если поставщик не поддерживает возврат владельцы объектов, произойдет ошибка.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Catalog (ADOX)](../../../ado/reference/adox-api/catalog-object-adox.md)  
  
## <a name="see-also"></a>См. также  
 [GetObjectOwner и пример SetObjectOwner методы (Visual Basic)](../../../ado/reference/adox-api/getobjectowner-and-setobjectowner-methods-example-vb.md)   
 [Метод SetObjectOwner](../../../ado/reference/adox-api/setobjectowner-method.md)
