---
title: Метод GetObjectOwner (ADOX) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Catalog::raw_GetObjectOwner
- _Catalog::GetObjectOwner
helpviewer_keywords:
- GetObjectOwner method [ADOX]
ms.assetid: 8965adf0-9075-4125-8142-73eb700029c3
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9b2c967ac293ed59fde6494e12c2afc2c5b6de90
ms.sourcegitcommit: bd5f23f2f6b9074c317c88fc51567412f08142bb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/24/2019
ms.locfileid: "63464714"
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
 Объект **строка** значение, указывающее имя объекта, для которого для получения имени владельца.  
  
 *ObjectType*  
 Объект **Long** значение, которое может быть одним из [ObjectTypeEnum](../../../ado/reference/adox-api/objecttypeenum.md) константы, которое указывает тип объекта, для которого требуется получить владельца.  
  
 *ObjectTypeId*  
 Необязательный. Объект **Variant** значение, которое указывает идентификатор GUID для типа объекта поставщика, не определенных в спецификации OLE DB. Этот параметр является обязательным, если *ObjectType* присваивается **adPermObjProviderSpecific**; в противном случае он не используется.  
  
## <a name="remarks"></a>Примечания  
 Если поставщик не поддерживает возврат владельцы объектов, произойдет ошибка.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Catalog (ADOX)](../../../ado/reference/adox-api/catalog-object-adox.md)  
  
## <a name="see-also"></a>См. также  
 [GetObjectOwner и Setobjectowner методы (Visual Basic)](../../../ado/reference/adox-api/getobjectowner-and-setobjectowner-methods-example-vb.md)   
 [Метод SetObjectOwner](../../../ado/reference/adox-api/setobjectowner-method.md)
