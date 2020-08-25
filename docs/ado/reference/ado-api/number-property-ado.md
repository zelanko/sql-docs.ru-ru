---
description: Свойство Number (ADO)
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
author: rothja
ms.author: jroth
ms.openlocfilehash: fe4984a9bdbeff69f7c2beba4d91833cdca85f50
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2020
ms.locfileid: "88774103"
---
# <a name="number-property-ado"></a>Свойство Number (ADO)
Указывает число, которое однозначно определяет объект [ошибки](./error-object.md) .  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение **типа Long** , которое может соответствовать одной из констант [еррорвалуинум](./errorvalueenum.md) .  
  
## <a name="remarks"></a>Remarks  
 Чтобы определить, какая ошибка возникла, используйте свойство **Number** . Значение свойства является уникальным числом, которое соответствует условию ошибки.  
  
 Коллекция [Errors](./errors-collection-ado.md) ВОЗВРАЩАЕТ значение HRESULT в шестнадцатеричном формате (например, 0x80004005) или длинном значении (например, 2147467259). Эти значения HRESULT могут быть вызваны базовыми компонентами, такими как OLE DB или даже самим OLE. Дополнительные сведения об этих номерах см. в разделе [ошибки (OLE DB)](/previous-versions/windows/desktop/ms724533(v=vs.85)) в [справочнике по программисту OLE DB](/previous-versions/windows/desktop/ms713643(v=vs.85))*.*  
  
## <a name="applies-to"></a>Применение  
 [Объект Error](./error-object.md)  
  
## <a name="see-also"></a>См. также  
 [Примеры свойств Description, HelpContext, HelpFile, NativeError, Number, Source и SQLState (Visual Basic)](./description-helpcontext-helpfile-nativeerror-number-source-example-vb.md)   
 [Примеры свойств Description, HelpContext, HelpFile, NativeError, Number, Source и SQLState (Visual c++)](./description-helpcontext-helpfile-nativeerror-number-source-example-vc.md)   
 [Свойство Description](./description-property.md)   
 [Свойства HelpContext, HelpFile](./helpcontext-helpfile-properties.md)   
 [Свойство Source (объект Error ADO)](./source-property-ado-error.md)