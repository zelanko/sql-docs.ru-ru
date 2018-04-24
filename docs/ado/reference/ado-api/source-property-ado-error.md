---
title: Исходное свойство (ошибка ADO) | Документы Microsoft
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Error::get_Source
- Error::Source
- Error::GetSource
helpviewer_keywords:
- Source property [ADO Error]
ms.assetid: 4044ba15-f013-4c4c-9fe1-b4410fe9a778
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 7259b18975c3eb0203d97bd3b0796a69677002ca
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2018
---
# <a name="source-property-ado-error"></a>Свойство Source (ошибка)
Указывает имя объекта или приложения, вызвавшего ошибку.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает **строка** значение, указывающее имя объекта или приложения.  
  
## <a name="remarks"></a>Замечания  
 Используйте **источника** свойство [ошибка](../../../ado/reference/ado-api/error-object.md) объектом, чтобы определить имя объекта или приложения, вызвавшего ошибку. Это может быть имя класса объекта или программный код. Для ошибок в ADO, значение свойства будет **ADODB. *** ObjectName*, где *ObjectName* имя объекта, запустившего ошибку. ADOX и ADO MD, будет иметь значение **ADOX. *** ObjectName* и **ADOMD. *** ObjectName,* соответственно.  
  
 Зависимости документации ошибок из **источника**, [номер](../../../ado/reference/ado-api/number-property-ado.md), и [описание](../../../ado/reference/ado-api/description-property.md) свойства **ошибка** объектов, можно написать код который будет соответствующим образом обработать ошибку.  
  
 **Источника** свойство доступно только для чтения для **ошибка** объектов.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Error](../../../ado/reference/ado-api/error-object.md)  
  
## <a name="see-also"></a>См. также  
 [Описание, HelpContext, файл справки, NativeError, номер, источника и пример свойства SQLState (Visual Basic)](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vb.md)   
 [Описание, HelpContext, файл справки, NativeError, номер, источник и пример свойства SQLState (VC ++)](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vc.md)   
 [Свойство Description](../../../ado/reference/ado-api/description-property.md)   
 [HelpContext HelpFile свойства](../../../ado/reference/ado-api/helpcontext-helpfile-properties.md)   
 [Свойство номера (ADO)](../../../ado/reference/ado-api/number-property-ado.md)   
 [Свойство Source (ADO запись)](../../../ado/reference/ado-api/source-property-ado-record.md)   
 [Свойство Source (объект Recordset ADO)](../../../ado/reference/ado-api/source-property-ado-recordset.md)
