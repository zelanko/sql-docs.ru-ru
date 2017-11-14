---
title: "Свойство ActiveCommand (ADO) | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- Recordset20::ActiveCommand
helpviewer_keywords:
- ActiveCommand property [ADO]
ms.assetid: fb4088d5-5968-42d6-aeaa-3955046bb4da
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 4b1580dbedaa9c7667cd7b320817fdaea6ad48d7
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="activecommand-property-ado"></a>Свойство ActiveCommand (ADO)
Указывает [команда](../../../ado/reference/ado-api/command-object-ado.md) объекта, который создан связанный [записей](../../../ado/reference/ado-api/recordset-object-ado.md) объекта.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает **Variant** , содержащий **команда** объекта. Значение по умолчанию — пустая ссылка на объект.  
  
## <a name="remarks"></a>Замечания  
 **ActiveCommand** свойство доступно только для чтения.  
  
 Если **команда** объект не использовался для создания текущего **записей**, то **Null** возвращается ссылка на объект.  
  
 Это свойство используется для поиска соответствующего **команда** объекта имеются только итоговый **записей** объекта.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект набора записей (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>См. также:  
 [Пример свойства ActiveCommand (Visual Basic)](../../../ado/reference/ado-api/activecommand-property-example-vb.md)   
 [Пример свойства ActiveCommand (JScript)](../../../ado/reference/ado-api/activecommand-property-example-jscript.md)   
 [Пример свойства ActiveCommand (VC ++)](../../../ado/reference/ado-api/activecommand-property-example-vc.md)   
 [Объект команды (ADO)](../../../ado/reference/ado-api/command-object-ado.md)

