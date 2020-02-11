---
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: d2a2f23360cf3ce032d14af7ca475d5c2c3ea638
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67921678"
---
# <a name="activecommand-property-ado"></a>Свойство ActiveCommand (ADO)
Указывает объект [Command](../../../ado/reference/ado-api/command-object-ado.md) , который создал связанный объект [набора записей](../../../ado/reference/ado-api/recordset-object-ado.md) .  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает **значение типа Variant** , содержащее объект **Command** . По умолчанию используется пустая ссылка на объект.  
  
## <a name="remarks"></a>Remarks  
 Свойство **ActiveCommand** доступно только для чтения.  
  
 Если объект **команды** не использовался для создания текущего **набора записей**, возвращается ссылка на **пустой** объект.  
  
 Это свойство используется для поиска связанного объекта **Command** , если предоставлен только результирующий объект **набора записей** .  
  
## <a name="applies-to"></a>Применяется к  
 [Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>См. также:  
 [Пример свойства ActiveCommand (Visual Basic)](../../../ado/reference/ado-api/activecommand-property-example-vb.md)   
 [Пример свойства ActiveCommand (JScript)](../../../ado/reference/ado-api/activecommand-property-example-jscript.md)   
 [Пример свойства ActiveCommand (Visual c++)](../../../ado/reference/ado-api/activecommand-property-example-vc.md)   
 [Объект Command (ADO)](../../../ado/reference/ado-api/command-object-ado.md)
