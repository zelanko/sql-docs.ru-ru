---
title: "WillChangeRecord и RecordChangeComplete события (ADO) | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- RecordChangeComplete
- Recordset::WillChangeRecord
- WillChangeRecord
- Recordset::RecordChangeComplete
helpviewer_keywords:
- WillChangeRecord event [ADO]
- recordchangecomplete event [ADO]
ms.assetid: cbc369fd-63af-4a7d-96ae-efa91b78ca69
caps.latest.revision: "12"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 1a421ba630b9cb9eeafaa2087144b765a64f78b9
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="willchangerecord-and-recordchangecomplete-events-ado"></a>WillChangeRecord и RecordChangeComplete события (ADO)
**WillChangeRecord** событие вызывается перед одной или нескольких записей (строк) [записей](../../../ado/reference/ado-api/recordset-object-ado.md) изменения. **RecordChangeComplete** событие вызывается после одного или более записи изменения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
WillChangeRecord adReason, cRecords, adStatus, pRecordset  
RecordChangeCompleteadReason, cRecords, pError, adStatus, pRecordset  
```  
  
#### <a name="parameters"></a>Параметры  
 *adReason*  
 [EventReasonEnum](../../../ado/reference/ado-api/eventreasonenum.md) значение, указывающее причину возникновения данного события. Его значение может быть **adRsnAddNew**, **adRsnDelete**, **adRsnUpdate**, **adRsnUndoUpdate**, **adRsnUndoAddNew**, **adRsnUndoDelete**, или **adRsnFirstChange**.  
  
 *cRecords*  
 Объект **длинные** значение, указывающее количество записей изменение (затронутых).  
  
 *pError*  
 [Ошибка](../../../ado/reference/ado-api/error-object.md) объекта. Здесь описываются ошибки, возникшей при значение *adStatus* — **adStatusErrorsOccurred**; в противном случае оно не задано.  
  
 *adStatus*  
 [EventStatusEnum](../../../ado/reference/ado-api/eventstatusenum.md) значение состояния.  
  
 Когда **WillChangeRecord** — вызывается, этот параметр имеет значение **adStatusOK** при успешном выполнении операции, которая вызвала событие. Ему присваивается **adStatusCantDeny** Если это событие не удается запросить отмену отложенной операции.  
  
 Когда **RecordChangeComplete** — вызывается, этот параметр имеет значение **adStatusOK** при успешном выполнении операции, которая вызвала событие или для **adStatusErrorsOccurred** Если Сбой операции.  
  
 Прежде чем **WillChangeRecord** возвращает, присвойте этому параметру значение **adStatusCancel** чтобы запросить отмену операции, которое вызвало это событие или установите этот параметр,  **adStatusUnwantedEvent** для предотвращения последующих уведомлений.  
  
 Прежде чем **RecordChangeComplete** возвращает, присвойте этому параметру значение **adStatusUnwantedEvent** для предотвращения последующих уведомлений.  
  
 *pRecordset*  
 Объект **записей** объекта. **Записей** для возникновения этого события.  
  
## <a name="remarks"></a>Замечания  
 Объект **WillChangeRecord** или **RecordChangeComplete** событие может происходить первого поля, измененные в строку из-за следующих **записей** операции: [ Обновление](../../../ado/reference/ado-api/update-method.md), [удаление](../../../ado/reference/ado-api/delete-method-ado-recordset.md), [CancelUpdate](../../../ado/reference/ado-api/cancelupdate-method-ado.md), [AddNew](../../../ado/reference/ado-api/addnew-method-ado.md), [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md), и [ CancelBatch](../../../ado/reference/ado-api/cancelbatch-method-ado.md). Значение **записей** [CursorType](../../../ado/reference/ado-api/cursortype-property-ado.md) определяет, какие операции вызывают возникновения событий.  
  
 Во время **WillChangeRecord** событий, **записей** [фильтра](../../../ado/reference/ado-api/filter-property.md) свойству **adFilterAffectedRecords**. Это свойство нельзя изменить во время обработки события.  
  
 Необходимо задать **adStatus** параметр **adStatusUnwantedEvent** для каждого возможного **adReason** значение полной остановки уведомление о событии для любого события, которое включает в себя **adReason** параметра.  
  
## <a name="see-also"></a>См. также:  
 [Пример модели событий ADO (VC ++)](../../../ado/reference/ado-api/ado-events-model-example-vc.md)   
 [Общие сведения об обработчике событий ADO](../../../ado/guide/data/ado-event-handler-summary.md)
