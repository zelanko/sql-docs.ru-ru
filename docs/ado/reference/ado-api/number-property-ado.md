---
title: Свойство Number (ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Error::Number
- Error::GetNumber
- Error::get_Number
helpviewer_keywords:
- number property [ADO]
ms.assetid: f92323c5-dd11-4a63-a505-d9014a0f067f
author: MightyPen
ms.author: genemi
ms.openlocfilehash: ce027747c843e02998f4845db7075e70cf8733b6
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "67917988"
---
# <a name="number-property-ado"></a>Свойство Number (ADO)
Указывает число, которое однозначно определяет объект [ошибки](../../../ado/reference/ado-api/error-object.md) .  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение **типа Long** , которое может соответствовать одной из констант [еррорвалуинум](../../../ado/reference/ado-api/errorvalueenum.md) .  
  
## <a name="remarks"></a>Remarks  
 Чтобы определить, какая ошибка возникла, используйте свойство **Number** . Значение свойства является уникальным числом, которое соответствует условию ошибки.  
  
 Коллекция [Errors](../../../ado/reference/ado-api/errors-collection-ado.md) ВОЗВРАЩАЕТ значение HRESULT в шестнадцатеричном формате (например, 0x80004005) или длинном значении (например, 2147467259). Эти значения HRESULT могут быть вызваны базовыми компонентами, такими как OLE DB или даже самим OLE. Дополнительные сведения об этих номерах см. в разделе [ошибки (OLE DB)](https://msdn.microsoft.com/ed74e62d-4948-4eeb-a7c9-fd7ad46af7fd) в [справочнике по программисту OLE DB](https://msdn.microsoft.com/3c5e2dd5-35e5-4a93-ac3a-3818bb43bbf8)*.*  
  
## <a name="applies-to"></a>Применяется к  
 [Объект Error](../../../ado/reference/ado-api/error-object.md)  
  
## <a name="see-also"></a>См. также  
 [Примеры свойств Description, HelpContext, HelpFile, NativeError, Number, Source и SQLState (Visual Basic)](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vb.md)   
 [Примеры свойств Description, HelpContext, HelpFile, NativeError, Number, Source и SQLState (Visual c++)](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vc.md)   
 [Свойство Description](../../../ado/reference/ado-api/description-property.md)   
 [Свойства HelpContext, HelpFile](../../../ado/reference/ado-api/helpcontext-helpfile-properties.md)   
 [Свойство Source (объект Error ADO)](../../../ado/reference/ado-api/source-property-ado-error.md)
