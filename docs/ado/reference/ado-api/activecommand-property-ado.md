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
author: rothja
ms.author: jroth
ms.openlocfilehash: b89876366c80d20bde110da9e9d86414873e86bc
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2020
ms.locfileid: "82747476"
---
# <a name="activecommand-property-ado"></a>Свойство ActiveCommand (ADO)
Указывает объект [Command](../../../ado/reference/ado-api/command-object-ado.md) , который создал связанный объект [набора записей](../../../ado/reference/ado-api/recordset-object-ado.md) .  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает **значение типа Variant** , содержащее объект **Command** . По умолчанию используется пустая ссылка на объект.  
  
## <a name="remarks"></a>Примечания  
 Свойство **ActiveCommand** доступно только для чтения.  
  
 Если объект **команды** не использовался для создания текущего **набора записей**, возвращается ссылка на **пустой** объект.  
  
 Это свойство используется для поиска связанного объекта **Command** , если предоставлен только результирующий объект **набора записей** .  
  
## <a name="applies-to"></a>Применяется к  
 [Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Пример свойства ActiveCommand (Visual Basic)](../../../ado/reference/ado-api/activecommand-property-example-vb.md)   
 [Пример свойства ActiveCommand (JScript)](../../../ado/reference/ado-api/activecommand-property-example-jscript.md)   
 [Пример свойства ActiveCommand (Visual c++)](../../../ado/reference/ado-api/activecommand-property-example-vc.md)   
 [Объект Command (ADO)](../../../ado/reference/ado-api/command-object-ado.md)
