---
title: Свойство Source (ошибка ADO) | Документация Майкрософт
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
ms.openlocfilehash: 6b55ebbe5a167b7d70cf606fc4e37e7ede36b486
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "67916903"
---
# <a name="source-property-ado-error"></a>Свойство Source (объект Error ADO)
Указывает имя объекта или приложения, вызвавшего ошибку.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает **строковое** значение, указывающее имя объекта или приложения.  
  
## <a name="remarks"></a>Remarks  
 Используйте свойство **Source** объекта [Error](../../../ado/reference/ado-api/error-object.md) , чтобы определить имя объекта или приложения, вызвавшего ошибку. Это может быть имя класса объекта или программный идентификатор. Для ошибок в ADO значение свойства будет **ADODB.** _Objectname_, где *objectname* — имя объекта, вызвавшего ошибку. Для ADOX и объекты данных ActiveX (MD) значение будет равно **ADOX.** _Objectname_ и **ADOMD.** _Objectname_соответственно.  
  
 На основе документации по ошибкам из свойств **Source**, [Number](../../../ado/reference/ado-api/number-property-ado.md)и [Description](../../../ado/reference/ado-api/description-property.md) объектов **Error** можно написать код, который будет соответствующим образом обрабатывал ошибку.  
  
 Свойство **Source** доступно только для чтения для объектов **ошибок** .  
  
## <a name="applies-to"></a>Применяется к  
 [Объект Error](../../../ado/reference/ado-api/error-object.md)  
  
## <a name="see-also"></a>См. также  
 [Примеры свойств Description, HelpContext, HelpFile, NativeError, Number, Source и SQLState (Visual Basic)](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vb.md)   
 [Примеры свойств Description, HelpContext, HelpFile, NativeError, Number, Source и SQLState (Visual c++)](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vc.md)   
 [Свойство Description](../../../ado/reference/ado-api/description-property.md)   
 [Свойства HelpContext, HelpFile](../../../ado/reference/ado-api/helpcontext-helpfile-properties.md)   
 [Свойство Number (ADO)](../../../ado/reference/ado-api/number-property-ado.md)   
 [Свойство Source (запись ADO)](../../../ado/reference/ado-api/source-property-ado-record.md)   
 [Свойство Source (объект Recordset ADO)](../../../ado/reference/ado-api/source-property-ado-recordset.md)
