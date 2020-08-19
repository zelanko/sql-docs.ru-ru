---
description: Свойство ActiveCommand (ADO)
title: Свойство ActiveCommand (ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset20::ActiveCommand
helpviewer_keywords:
- ActiveCommand property [ADO]
ms.assetid: fb4088d5-5968-42d6-aeaa-3955046bb4da
author: rothja
ms.author: jroth
ms.openlocfilehash: 38c0a0955e934b4f303937d978f739e00ac6c120
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88451746"
---
# <a name="activecommand-property-ado"></a>Свойство ActiveCommand (ADO)
Указывает объект [Command](../../../ado/reference/ado-api/command-object-ado.md) , который создал связанный объект [набора записей](../../../ado/reference/ado-api/recordset-object-ado.md) .  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает **значение типа Variant** , содержащее объект **Command** . По умолчанию используется пустая ссылка на объект.  
  
## <a name="remarks"></a>Remarks  
 Свойство **ActiveCommand** доступно только для чтения.  
  
 Если объект **команды** не использовался для создания текущего **набора записей**, возвращается ссылка на **пустой** объект.  
  
 Это свойство используется для поиска связанного объекта **Command** , если предоставлен только результирующий объект **набора записей** .  
  
## <a name="applies-to"></a>Применение  
 [Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>См. также:  
 [Пример свойства ActiveCommand (Visual Basic)](../../../ado/reference/ado-api/activecommand-property-example-vb.md)   
 [Пример свойства ActiveCommand (JScript)](../../../ado/reference/ado-api/activecommand-property-example-jscript.md)   
 [Пример свойства ActiveCommand (Visual c++)](../../../ado/reference/ado-api/activecommand-property-example-vc.md)   
 [Объект Command (ADO)](../../../ado/reference/ado-api/command-object-ado.md)
