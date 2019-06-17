---
title: Свойство (объект Error ADO) источника | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Error::get_Source
- Error::Source
- Error::GetSource
helpviewer_keywords:
- Source property [ADO Error]
ms.assetid: 4044ba15-f013-4c4c-9fe1-b4410fe9a778
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 89a4597cc846db1bb3bb2fac0a79ec8c2090d9d3
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66711147"
---
# <a name="source-property-ado-error"></a>Свойство Source (объект Error ADO)
Указывает имя объекта или приложения, вызвавшего ошибку.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает **строка** значение, указывающее имя объекта или приложения.  
  
## <a name="remarks"></a>Примечания  
 Используйте **источника** свойство [ошибка](../../../ado/reference/ado-api/error-object.md) объектом, чтобы определить имя объекта или приложения, вызвавшего ошибку. Это может быть имя класса объекта или программный код. Для ошибок в ADO, будет значение свойства **ADODB.** _ObjectName_, где *ObjectName* является имя объекта, который вызвал ошибку. Для ADOX и ADO MD, значение будет **ADOX.** _ObjectName_ и **ADOMD.** _ObjectName_, соответственно.  
  
 Исходя из документации по ошибок из **источника**, [номер](../../../ado/reference/ado-api/number-property-ado.md), и [описание](../../../ado/reference/ado-api/description-property.md) свойства **ошибка** объектов, можно написать код который будет соответствующим образом обработать ошибку.  
  
 **Источника** свойство доступно только для чтения для **ошибка** объектов.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Error](../../../ado/reference/ado-api/error-object.md)  
  
## <a name="see-also"></a>См. также  
 [Description, HelpContext, HelpFile, NativeError, номер, источника и SQLState свойства пример (Visual Basic)](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vb.md)   
 [Описание, HelpContext, HelpFile, NativeError, номер, источника и пример свойства SQLState (Visual C++)](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vc.md)   
 [Свойство Description](../../../ado/reference/ado-api/description-property.md)   
 [Свойства HelpContext и HelpFile](../../../ado/reference/ado-api/helpcontext-helpfile-properties.md)   
 [Свойство Number (ADO)](../../../ado/reference/ado-api/number-property-ado.md)   
 [Свойство Source (объект Record ADO)](../../../ado/reference/ado-api/source-property-ado-record.md)   
 [Свойство Source (объект Recordset ADO)](../../../ado/reference/ado-api/source-property-ado-recordset.md)
