---
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 234a0eeba57958063a6f2eedb8510486df8a53a0
ms.sourcegitcommit: bfa10c54e871700de285d7f819095d51ef70d997
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/14/2019
ms.locfileid: "54255507"
---
# <a name="willexecute-event-ado"></a>Событие WillExecute (ADO)
**WillExecute** событие вызывается непосредственно перед выполняет ожидания выполнения команды для подключения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
WillExecute Source, CursorType, LockType, Options, adStatus, pCommand, pRecordset, pConnection  
```  
  
#### <a name="parameters"></a>Параметры  
 *Source*  
 Объект **строка** , содержащий команду SQL или имя хранимой процедуры.  
  
 *Примеры CursorType*  
 Объект [CursorTypeEnum](../../../ado/reference/ado-api/cursortypeenum.md) , содержащий тип курсора для **записей** , будет открыт. С помощью этого параметра можно изменить курсор на любой тип во время **записей**[метод Open (объект Recordset ADO)](../../../ado/reference/ado-api/open-method-ado-recordset.md) операции. *Примеры CursorType* будет игнорироваться для любой другой операции.  
  
 *LockType*  
 Объект [LockTypeEnum](../../../ado/reference/ado-api/locktypeenum.md) , содержащий тип блокировки для **записей** , будет открыт. С помощью этого параметра можно изменить блокировку к любому типу во время **RecordsetOpen** операции. *LockType* будет игнорироваться для любой другой операции.  
  
 *Параметры*  
 Объект **Long** значение, указывающее параметры, которые могут использоваться для выполнения команды или открыть **записей**.  
  
 *adStatus*  
 [EventStatusEnum](../../../ado/reference/ado-api/eventstatusenum.md) значение состояния, который может быть **adStatusCantDeny** или **adStatusOK** при вызове этого события. Если это **adStatusCantDeny**, это событие не может запросить отмену отложенной операции.  
  
 *Командной*  
 [Объекта команды (ADO)](../../../ado/reference/ado-api/command-object-ado.md) объекта, для которого применяется это уведомление о событии.  
  
 *pRecordset*  
 [Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md) объекта, для которого применяется это уведомление о событии.  
  
 *pConnection*  
 [Объект соединения (ADO)](../../../ado/reference/ado-api/connection-object-ado.md) объекта, для которого применяется это уведомление о событии.  
  
## <a name="remarks"></a>Примечания  
 Объект **WillExecute** событие может происходить из-за соединения.  [Выполнение метода (объект Connection ADO)](../../../ado/reference/ado-api/execute-method-ado-connection.md), [метод Execute (объект Command ADO)](../../../ado/reference/ado-api/execute-method-ado-command.md), или [метод Open (объект Recordset ADO)](../../../ado/reference/ado-api/open-method-ado-recordset.md) метод *pConnection* следует параметр всегда содержат является допустимой ссылкой **подключения** объекта. Если событие из-за **Connection.Execute**, *pRecordset* и *командной* присвоено **ничего не**. Если событие из-за **Recordset.Open**, *pRecordset* будет ссылаться на параметр **записей** объекта и *командной* параметр имеет значение **ничего не**. Если событие из-за **Command.Execute**, *командной* будет ссылаться на параметр **команда** объекта и *pRecordset* параметр имеет значение **ничего не**.  
  
 **WillExecute** позволяет проверять и изменять параметры ожидающих выполнения. Это событие может вернуть запрос отмены ожидания выполнения команды.  
  
> [!NOTE]
>  Если исходный источник для **команда** является поток, заданный параметром [свойство CommandStream (ADO)](../../../ado/reference/ado-api/commandstream-property-ado.md) свойство, назначив новую строку к **WillExecute** _Источника_ параметр изменяет источник **команда**. **CommandStream** свойство очищается и [свойства CommandText (ADO)](../../../ado/reference/ado-api/commandtext-property-ado.md) свойство будет добавлено в новый источник. Исходный поток, заданный параметром **CommandStream** будут выпущены и будет недоступна.  
  
 Если строки источника, новый диалект отличается от исходного значения [свойство Dialect](../../../ado/reference/ado-api/dialect-property.md) свойство (который предоставивших **CommandStream**), должен быть указан правильный диалект, задав **диалект** свойства объекта команды ссылается *командной*.  
  
## <a name="see-also"></a>См. также  
 [Пример модели событий ADO (Visual C++)](../../../ado/reference/ado-api/ado-events-model-example-vc.md)   
 [Общие сведения об обработчике событий ADO](../../../ado/guide/data/ado-event-handler-summary.md)   
 [Объект Connection (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)
