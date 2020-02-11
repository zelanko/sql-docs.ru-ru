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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67965231"
---
# <a name="setobjectowner-method"></a>Метод SetObjectOwner
Указывает владельца объекта в [каталоге](../../../ado/reference/adox-api/catalog-object-adox.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Catalog.SetObjectOwner ObjectName, ObjectType, OwnerName [,ObjectTypeId]  
```  
  
#### <a name="parameters"></a>Параметры  
 *ИмяОбъекта*  
 **Строковое** значение, указывающее имя объекта, для которого необходимо указать владельца.  
  
 *ObjectType*  
 Значение типа **Long** , которое может быть одной из констант [обжекттипинум](../../../ado/reference/adox-api/objecttypeenum.md) , которое указывает тип владельца.  
  
 *OwnerName*  
 **Строковое** значение, указывающее [имя](../../../ado/reference/adox-api/name-property-adox.md) [пользователя](../../../ado/reference/adox-api/user-object-adox.md) или [группы](../../../ado/reference/adox-api/group-object-adox.md) для владельца объекта.  
  
 *обжекттипеид*  
 Необязательный параметр. Значение **типа Variant** , указывающее идентификатор GUID для типа объекта поставщика, который не определен спецификацией OLE DB. Этот параметр является обязательным, если для *ObjectType* задано значение **адпермобжпровидерспеЦифик**. в противном случае он не используется.  
  
## <a name="remarks"></a>Remarks  
 Если поставщик не поддерживает указание владельцев объектов, возникнет ошибка.  
  
## <a name="applies-to"></a>Применяется к  
 [Объект Catalog (ADOX)](../../../ado/reference/adox-api/catalog-object-adox.md)  
  
## <a name="see-also"></a>См. также:  
 [Примеры методов примеры методов getobjectowner и SetObjectOwner (Visual Basic)](../../../ado/reference/adox-api/getobjectowner-and-setobjectowner-methods-example-vb.md)   
 [Метод GetObjectOwner (ADOX)](../../../ado/reference/adox-api/getobjectowner-method-adox.md)
