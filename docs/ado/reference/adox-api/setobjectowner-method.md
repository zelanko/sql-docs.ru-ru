---
title: Метод SetObjectOwner | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Catalog::SetObjectOwner
- _Catalog::raw_SetObjectOwner
helpviewer_keywords:
- SetObjectOwner method [ADOX]
ms.assetid: e5170a37-9d6e-43db-bfb6-9b6631fa3048
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 50a02898c1694fa43b8bf522a1a1bca65300efda
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67965231"
---
# <a name="setobjectowner-method"></a>Метод SetObjectOwner
Указывает владельца объекта в [каталога](../../../ado/reference/adox-api/catalog-object-adox.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Catalog.SetObjectOwner ObjectName, ObjectType, OwnerName [,ObjectTypeId]  
```  
  
#### <a name="parameters"></a>Параметры  
 *ObjectName*  
 Объект **строка** значение, указывающее имя объекта, для которого необходимо указать владельца.  
  
 *ObjectType*  
 Объект **Long** значение, которое может быть одним из [ObjectTypeEnum](../../../ado/reference/adox-api/objecttypeenum.md) констант, указывающих тип владельца.  
  
 *OwnerName*  
 Объект **строка** значение, указывающее [имя](../../../ado/reference/adox-api/name-property-adox.md) из [пользователя](../../../ado/reference/adox-api/user-object-adox.md) или [группы](../../../ado/reference/adox-api/group-object-adox.md) его владельцем объекта.  
  
 *ObjectTypeId*  
 Необязательный. Объект **Variant** значение, которое указывает идентификатор GUID для типа объекта поставщика, который не определен в спецификации OLE DB. Этот параметр является обязательным, если *ObjectType* присваивается **adPermObjProviderSpecific**; в противном случае он не используется.  
  
## <a name="remarks"></a>Примечания  
 Если поставщик не поддерживает указание владельцы объектов, произойдет ошибка.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Catalog (ADOX)](../../../ado/reference/adox-api/catalog-object-adox.md)  
  
## <a name="see-also"></a>См. также  
 [GetObjectOwner и Setobjectowner методы (Visual Basic)](../../../ado/reference/adox-api/getobjectowner-and-setobjectowner-methods-example-vb.md)   
 [Метод GetObjectOwner (ADOX)](../../../ado/reference/adox-api/getobjectowner-method-adox.md)
