---
description: Событие WillExecute (ADO)
title: Событие WillExecute (ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- WillExecute
- Connection::WillExecute
helpviewer_keywords:
- WillExecute event [ADO]
ms.assetid: dd755e46-f589-48a3-93a9-51ff998d44b5
author: rothja
ms.author: jroth
ms.openlocfilehash: affe058e06d20ffec9c27a5f4a60812f6fee1b03
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2020
ms.locfileid: "88776873"
---
# <a name="willexecute-event-ado"></a>Событие WillExecute (ADO)
Событие **WillExecute** вызывается непосредственно перед выполнением ожидающей команды в соединении.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
WillExecute Source, CursorType, LockType, Options, adStatus, pCommand, pRecordset, pConnection  
```  
  
#### <a name="parameters"></a>Параметры  
 *Source*  
 **Строка** , содержащая команду SQL или имя хранимой процедуры.  
  
 *Примеры CursorType*  
 Объект [курсортипинум](./cursortypeenum.md) , содержащий тип курсора для **набора записей** , который будет открыт. С помощью этого параметра можно изменить курсор на любой тип во время операции набора **записей**[(ADO Recordset)](./open-method-ado-recordset.md) . *Примеры CursorType* будет игнорироваться для любой другой операции.  
  
 *LockType*  
 Объект [локктипинум](./locktypeenum.md) , содержащий тип блокировки для **набора записей** , который будет открыт. С помощью этого параметра можно изменить блокировку на любой тип во время операции **рекордсетопен** . *LockType* будет игнорироваться для любой другой операции.  
  
 *Параметры*  
 Значение **типа Long** , указывающее параметры, которые можно использовать для выполнения команды или открытия **набора записей**.  
  
 *адстатус*  
 Значение состояния [евентстатусенум](./eventstatusenum.md) , которое может быть **адстатускантдени** или **адстатусок** при вызове этого события. Если это **адстатускантдени**, это событие может не запрашивать отмену ожидающей операции.  
  
 *пкомманд*  
 Объект [команды (ADO)](./command-object-ado.md) , к которому относится данное уведомление о событии.  
  
 *предшнур*  
 Объект [Recordset Object (ADO)](./recordset-object-ado.md) , к которому относится данное уведомление о событии.  
  
 *пконнектион*  
 Объект [соединения (ADO)](./connection-object-ado.md) , к которому относится данное уведомление о событии.  
  
## <a name="remarks"></a>Remarks  
 Событие **WillExecute** может возникать из-за соединения.  Метод [Execute (соединение ADO)](./execute-method-ado-connection.md), [метод Execute (команда ADO)](./execute-method-ado-command.md)или [открытый метод (набор записей ADO)](./open-method-ado-recordset.md) . параметр *пконнектион* всегда должен содержать допустимую ссылку на объект **соединения** . Если событие вызвано **Connection.Exeмилые** *, то параметры* предустановки и *Пкомманд* задаются как **Nothing**. Если это событие связано с **набором Recordset. Open**, параметр *предшнура* будет ссылаться на объект **Recordset** , а параметр *пкомманд* имеет значение **Nothing**. Если событие происходит из-за **Command.Exeмилые**, параметр *пкомманд* будет ссылаться на объект **Command** , *а параметру* предустановки — значение **Nothing**.  
  
 **WillExecute** позволяет проверять и изменять параметры ожидания выполнения. Это событие может возвращать запрос на отмену ожидающей команды.  
  
> [!NOTE]
>  Если исходный источник для **команды** является потоком, заданным свойством [CommandStream (ADO)](./commandstream-property-ado.md) , присвоение новой строки параметру_источника_ **WillExecute**изменяет источник **команды**. Свойство **CommandStream** будет сброшено, а свойство [свойства CommandText (ADO)](./commandtext-property-ado.md) будет обновлено новым источником. Исходный поток, заданный **CommandStream** , будет освобожден, и к нему невозможно получить доступ.  
  
 Если диалект новой исходной строки отличается от исходного значения свойства [диалекта](./dialect-property.md) (соответствующего **CommandStream**), необходимо указать правильный диалект, задав свойство **диалекта** объекта Command, на который ссылается *пкомманд*.  
  
## <a name="see-also"></a>См. также  
 [Пример модели событий ADO (Visual c++)](./ado-events-model-example-vc.md)   
 [Сводка по обработчику событий ADO](../../guide/data/ado-event-handler-summary.md)   
 [Объект Connection (ADO)](./connection-object-ado.md)