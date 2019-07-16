---
title: Событие ExecuteComplete (ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Connection::ExecuteComplete
- ExecuteComplete
helpviewer_keywords:
- ExecuteComplete event [ADO]
ms.assetid: 62470d42-e511-494c-bec4-ad4591734b7b
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 62b78b608526ae0d6943a7416a21687fd1e51412
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67918784"
---
# <a name="executecomplete-event-ado"></a>Событие ExecuteComplete (ADO)
**ExecuteComplete** событие вызывается после завершения выполнения команды.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
ExecuteComplete RecordsAffected, pError, adStatus, pCommand, pRecordset, pConnection  
```  
  
#### <a name="parameters"></a>Параметры  
 *RecordsAffected*  
 Объект **Long** значение, указывающее количество записей, затронутых этой командой.  
  
 *pError*  
 [Ошибка](../../../ado/reference/ado-api/error-object.md) объекта. Он описывает ошибки, возникшей при значение **adStatus** — **adStatusErrorsOccurred**; в противном случае оно не задано.  
  
 *adStatus*  
 [EventStatusEnum](../../../ado/reference/ado-api/eventstatusenum.md) значение состояния. Когда это событие вызывается, этот параметр имеет значение **adStatusOK** при успешной операции, которая вызвала событие, или чтобы **adStatusErrorsOccurred** Если произошел сбой операции.  
  
 Прежде чем это событие возвращает, присвойте этому параметру значение **adStatusUnwantedEvent** игнорировать последующие уведомления.  
  
 *Командной*  
 [Команда](../../../ado/reference/ado-api/command-object-ado.md) объект, который был выполнен. Содержит **команда** даже в том случае, если вызов **Connection.Execute** или **Recordset.Open** без явного создания **команда** , в какие варианты **команда** создается внутренне путем ADO.  
  
 *pRecordset*  
 Объект [записей](../../../ado/reference/ado-api/recordset-object-ado.md) объект, являющийся результатом выполнения команды. Это **записей** может быть пустым. Вы никогда не должны уничтожить этого объекта набора записей в этот обработчик событий. Это приведет к нарушению прав доступа при ADO пытается получить доступ к объекту, который больше не существует.  
  
 *pConnection*  
 Объект [подключения](../../../ado/reference/ado-api/connection-object-ado.md) объекта. Соединение, по которому выполнялась операция.  
  
## <a name="remarks"></a>Примечания  
 **ExecuteComplete** событие может происходить из-за **подключения.** [Выполнение](../../../ado/reference/ado-api/execute-method-ado-connection.md), **команды.** [Выполнение](../../../ado/reference/ado-api/execute-method-ado-command.md), **набор записей.** [Откройте](../../../ado/reference/ado-api/open-method-ado-recordset.md), **набор записей.** [Requery](../../../ado/reference/ado-api/requery-method.md), или **набор записей.** [NextRecordset](../../../ado/reference/ado-api/nextrecordset-method-ado.md) методы.  
  
## <a name="see-also"></a>См. также  
 [Пример модели событий ADO (Visual C++)](../../../ado/reference/ado-api/ado-events-model-example-vc.md)   
 [Общие сведения об обработчике событий ADO](../../../ado/guide/data/ado-event-handler-summary.md)
