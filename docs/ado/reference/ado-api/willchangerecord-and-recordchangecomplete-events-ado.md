---
title: События WillChangeRecord и Recordchangecomplete (ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
f1_keywords:
- RecordChangeComplete
- Recordset::WillChangeRecord
- WillChangeRecord
- Recordset::RecordChangeComplete
helpviewer_keywords:
- WillChangeRecord event [ADO]
- recordchangecomplete event [ADO]
ms.assetid: cbc369fd-63af-4a7d-96ae-efa91b78ca69
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: ef2e02ec156aeed69089a585d743e16e592eb95f
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66710158"
---
# <a name="willchangerecord-and-recordchangecomplete-events-ado"></a>События WillChangeRecord и RecordChangeComplete (ADO)
**События WillChangeRecord** событие вызывается перед одну или несколько записей (строк) [записей](../../../ado/reference/ado-api/recordset-object-ado.md) изменить. **RecordChangeComplete** событие вызывается после одного или изменить несколько записей.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
WillChangeRecord adReason, cRecords, adStatus, pRecordset  
RecordChangeCompleteadReason, cRecords, pError, adStatus, pRecordset  
```  
  
#### <a name="parameters"></a>Параметры  
 *adReason*  
 [EventReasonEnum](../../../ado/reference/ado-api/eventreasonenum.md) значение, указывающее причину для данного события. Его значение может быть **adRsnAddNew**, **adRsnDelete**, **adRsnUpdate**, **adRsnUndoUpdate**, **adRsnUndoAddNew**, **adRsnUndoDelete**, или **adRsnFirstChange**.  
  
 *cRecords*  
 Объект **Long** значение, указывающее количество записей, изменив (затронутые).  
  
 *pError*  
 [Ошибка](../../../ado/reference/ado-api/error-object.md) объекта. Он описывает ошибки, возникшей при значение *adStatus* — **adStatusErrorsOccurred**; в противном случае оно не задано.  
  
 *adStatus*  
 [EventStatusEnum](../../../ado/reference/ado-api/eventstatusenum.md) значение состояния.  
  
 Когда **события WillChangeRecord** является именем, этот параметр имеет значение **adStatusOK** при успешной операции, которая вызвала событие. Ему будет присвоено **adStatusCantDeny** Если это событие не может запросить отмену отложенной операции.  
  
 Когда **RecordChangeComplete** является именем, этот параметр имеет значение **adStatusOK** при успешной операции, которая вызвала событие, или для **adStatusErrorsOccurred** Если Сбой операции.  
  
 Прежде чем **события WillChangeRecord** возвращает, присвойте этому параметру значение **adStatusCancel** на запрос на отмену операции, вызвавшее данное событие или присвойте этому параметру значение  **adStatusUnwantedEvent** игнорировать последующие уведомления.  
  
 Прежде чем **RecordChangeComplete** возвращает, присвойте этому параметру значение **adStatusUnwantedEvent** игнорировать последующие уведомления.  
  
 *pRecordset*  
 Объект **записей** объекта. **Записей** для возникновения этого события.  
  
## <a name="remarks"></a>Примечания  
 Объект **события WillChangeRecord** или **RecordChangeComplete** событие может происходить первого поля, измененные в строке, из-за следующих **записей** операций: [Обновление](../../../ado/reference/ado-api/update-method.md), [удалить](../../../ado/reference/ado-api/delete-method-ado-recordset.md), [CancelUpdate](../../../ado/reference/ado-api/cancelupdate-method-ado.md), [AddNew](../../../ado/reference/ado-api/addnew-method-ado.md), [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md), и [CancelBatch](../../../ado/reference/ado-api/cancelbatch-method-ado.md). Значение **записей** [CursorType](../../../ado/reference/ado-api/cursortype-property-ado.md) определяет, какие операции вызывают события, которые происходят.  
  
 Во время **события WillChangeRecord** событий, **записей** [фильтра](../../../ado/reference/ado-api/filter-property.md) свойству **adFilterAffectedRecords**. Это свойство нельзя изменять во время обработки события.  
  
 Необходимо задать **adStatus** параметр **adStatusUnwantedEvent** для каждого возможного **adReason** значение полностью остановить уведомление о событии для любого события, которое включает в себя **adReason** параметра.  
  
## <a name="see-also"></a>См. также  
 [Пример модели событий ADO (Visual C++)](../../../ado/reference/ado-api/ado-events-model-example-vc.md)   
 [Общие сведения об обработчике событий ADO](../../../ado/guide/data/ado-event-handler-summary.md)
