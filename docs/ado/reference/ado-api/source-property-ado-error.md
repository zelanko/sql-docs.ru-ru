---
description: Свойство Source (объект Error ADO)
title: Свойство Source (ошибка ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 117e6e1f16800daaf94cba6e4a7643d5aa1c8c1f
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2020
ms.locfileid: "88988985"
---
# <a name="source-property-ado-error"></a>Свойство Source (объект Error ADO)
Указывает имя объекта или приложения, вызвавшего ошибку.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает **строковое** значение, указывающее имя объекта или приложения.  
  
## <a name="remarks"></a>Remarks  
 Используйте свойство **Source** объекта [Error](./error-object.md) , чтобы определить имя объекта или приложения, вызвавшего ошибку. Это может быть имя класса объекта или программный идентификатор. Для ошибок в ADO значение свойства будет **ADODB.** _Objectname_, где *objectname* — имя объекта, вызвавшего ошибку. Для ADOX и объекты данных ActiveX (MD) значение будет равно **ADOX.** _Objectname_ и **ADOMD.** _Objectname_соответственно.  
  
 На основе документации по ошибкам из свойств **Source**, [Number](./number-property-ado.md)и [Description](./description-property.md) объектов **Error** можно написать код, который будет соответствующим образом обрабатывал ошибку.  
  
 Свойство **Source** доступно только для чтения для объектов **ошибок** .  
  
## <a name="applies-to"></a>Применение  
 [Объект Error](./error-object.md)  
  
## <a name="see-also"></a>См. также  
 [Примеры свойств Description, HelpContext, HelpFile, NativeError, Number, Source и SQLState (Visual Basic)](./description-helpcontext-helpfile-nativeerror-number-source-example-vb.md)   
 [Примеры свойств Description, HelpContext, HelpFile, NativeError, Number, Source и SQLState (Visual c++)](./description-helpcontext-helpfile-nativeerror-number-source-example-vc.md)   
 [Свойство Description](./description-property.md)   
 [Свойства HelpContext, HelpFile](./helpcontext-helpfile-properties.md)   
 [Свойство Number (ADO)](./number-property-ado.md)   
 [Свойство Source (запись ADO)](./source-property-ado-record.md)   
 [Свойство Source (объект Recordset ADO)](./source-property-ado-recordset.md)