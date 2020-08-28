---
description: Свойство ActiveCommand (ADO)
title: Свойство ActiveCommand (ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
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
ms.openlocfilehash: df737543e8cc09735c7da413b89406b6f2385079
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2020
ms.locfileid: "88977162"
---
# <a name="activecommand-property-ado"></a>Свойство ActiveCommand (ADO)
Указывает объект [Command](./command-object-ado.md) , который создал связанный объект [набора записей](./recordset-object-ado.md) .  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает **значение типа Variant** , содержащее объект **Command** . По умолчанию используется пустая ссылка на объект.  
  
## <a name="remarks"></a>Remarks  
 Свойство **ActiveCommand** доступно только для чтения.  
  
 Если объект **команды** не использовался для создания текущего **набора записей**, возвращается ссылка на **пустой** объект.  
  
 Это свойство используется для поиска связанного объекта **Command** , если предоставлен только результирующий объект **набора записей** .  
  
## <a name="applies-to"></a>Применение  
 [Объект Recordset (ADO)](./recordset-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Пример свойства ActiveCommand (Visual Basic)](./activecommand-property-example-vb.md)   
 [Пример свойства ActiveCommand (JScript)](./activecommand-property-example-jscript.md)   
 [Пример свойства ActiveCommand (Visual c++)](./activecommand-property-example-vc.md)   
 [Объект Command (ADO)](./command-object-ado.md)