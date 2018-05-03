---
title: Свойство ActiveCommand (ADO) | Документы Microsoft
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
- Recordset20::ActiveCommand
helpviewer_keywords:
- ActiveCommand property [ADO]
ms.assetid: fb4088d5-5968-42d6-aeaa-3955046bb4da
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b221cc04d9a9e7d4d6c163867d6b77be71292e5e
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
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
 [Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Пример свойства ActiveCommand (Visual Basic)](../../../ado/reference/ado-api/activecommand-property-example-vb.md)   
 [Пример свойства ActiveCommand (JScript)](../../../ado/reference/ado-api/activecommand-property-example-jscript.md)   
 [Пример свойства ActiveCommand (VC ++)](../../../ado/reference/ado-api/activecommand-property-example-vc.md)   
 [Объект Command (ADO)](../../../ado/reference/ado-api/command-object-ado.md)
