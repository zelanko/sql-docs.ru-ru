---
description: Метод GetObjectOwner (ADOX)
title: Метод примеры методов getobjectowner (ADOX) | Документация Майкрософт
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 1c68adc866ce3ee73ca184a1e5e2851b3545329d
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2020
ms.locfileid: "88770513"
---
# <a name="getobjectowner-method-adox"></a>Метод GetObjectOwner (ADOX)
Возвращает владельца объекта в [каталоге](./catalog-object-adox.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Owner = Catalog.GetObjectOwner(ObjectName, ObjectType [,ObjectTypeId])  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает **строковое** значение, указывающее [имя](./name-property-adox.md) [пользователя](./user-object-adox.md) или [группы](./group-object-adox.md) , которым принадлежит объект.  
  
#### <a name="parameters"></a>Параметры  
 *ObjectName*  
 **Строковое** значение, указывающее имя объекта, для которого возвращается владелец.  
  
 *ObjectType*  
 Значение типа **Long** , которое может быть одной из констант [обжекттипинум](./objecttypeenum.md) , указывающее тип объекта, для которого необходимо получить владельца.  
  
 *обжекттипеид*  
 Необязательный элемент. Значение **типа Variant** , указывающее идентификатор GUID для типа объекта поставщика, не определенного спецификацией OLE DB. Этот параметр является обязательным, если для *ObjectType* задано значение **адпермобжпровидерспеЦифик**. в противном случае он не используется.  
  
## <a name="remarks"></a>Remarks  
 Если поставщик не поддерживает возврат владельцев объектов, возникнет ошибка.  
  
## <a name="applies-to"></a>Применение  
 [Объект Catalog (ADOX)](./catalog-object-adox.md)  
  
## <a name="see-also"></a>См. также  
 [Примеры методов примеры методов getobjectowner и SetObjectOwner (Visual Basic)](./getobjectowner-and-setobjectowner-methods-example-vb.md)   
 [Метод SetObjectOwner](./setobjectowner-method.md)