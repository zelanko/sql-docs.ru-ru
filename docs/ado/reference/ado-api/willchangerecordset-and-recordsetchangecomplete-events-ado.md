---
title: "WillChangeRecordset и RecordsetChangeComplete события (ADO) | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- Recordset::RecordsetChangeComplete
- RecordsetChangeComplete
- Recordset::WillChangeRecordset
- WillChangeRecordset
helpviewer_keywords:
- RecordsetChangeComplete event [ADO]
- WillChangeRecordset event [ADO]
ms.assetid: d5d44659-e0d9-46d9-a297-99c43555082f
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: b720776cd7c230e55e77cb37f7a66de3ad6772b6
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/09/2018
---
# <a name="willchangerecordset-and-recordsetchangecomplete-events-ado"></a>WillChangeRecordset и RecordsetChangeComplete события (ADO)
**WillChangeRecordset** событие вызывается перед ожидающая выполнения операция изменяет [записей](../../../ado/reference/ado-api/recordset-object-ado.md). **RecordsetChangeComplete** событие вызывается после **записей** изменилось.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
WillChangeRecordset adReason, adStatus, pRecordset  
RecordsetChangeComplete adReason, pError, adStatus, pRecordset  
```  
  
#### <a name="parameters"></a>Параметры  
 *adReason*  
 [EventReasonEnum](../../../ado/reference/ado-api/eventreasonenum.md) значение, указывающее причину возникновения данного события. Его значение может быть **adRsnRequery**, **adRsnResynch**, **adRsnClose**, **adRsnOpen**.  
  
 *adStatus*  
 [EventStatusEnum](../../../ado/reference/ado-api/eventstatusenum.md) значение состояния.  
  
 Когда **WillChangeRecordset** — вызывается, этот параметр имеет значение **adStatusOK** при успешном выполнении операции, которая вызвала событие. Ему присваивается **adStatusCantDeny** Если это событие не удается запросить отмену отложенной операции.  
  
 Когда **RecordsetChangeComplete** — вызывается, этот параметр имеет значение **adStatusOK** после успешного операции, которая вызвала событие, **adStatusErrorsOccurred** Если Сбой операции, или **adStatusCancel** Если операции, связанные с ранее принятые **WillChangeRecordset** событие было отменено.  
  
 Прежде чем **WillChangeRecordset** возвращает, присвойте этому параметру значение **adStatusCancel** запрашивать отмену отложенной операции или присвойте этому параметру значение adStatusUnwantedEvent во избежание последующих уведомления.  
  
 Прежде чем **WillChangeRecordset** или **RecordsetChangeComplete** возвращает, присвойте этому параметру значение **adStatusUnwantedEvent** для предотвращения последующих уведомлений.  
  
 *pError*  
 [Ошибка](../../../ado/reference/ado-api/error-object.md) объекта. Здесь описываются ошибки, возникшей при значение *adStatus* — **adStatusErrorsOccurred**; в противном случае оно не задано.  
  
 *pRecordset*  
 Объект **записей** объекта. **Записей** для возникновения этого события.  
  
## <a name="remarks"></a>Remarks  
 Объект **WillChangeRecordset** или **RecordsetChangeComplete** событие может происходить из-за **записей** [Requery](../../../ado/reference/ado-api/requery-method.md) или [Открыть](../../../ado/reference/ado-api/open-method-ado-recordset.md) методы.  
  
 Если поставщик не поддерживает закладки, **RecordsetChange** уведомление о событии возникает каждый раз, новые строки извлекаются из поставщика. Зависит от частоты возникновения этого события **RecordsetCacheSize** свойство.  
  
 Необходимо задать **adStatus** параметр **adStatusUnwantedEvent** для каждого возможного **adReason** значение полной остановки уведомление о событии для любого события, которое включает в себя **adReason** параметра.  
  
## <a name="see-also"></a>См. также  
 [Пример модели событий ADO (VC ++)](../../../ado/reference/ado-api/ado-events-model-example-vc.md)   
 [Общие сведения об обработчике событий ADO](../../../ado/guide/data/ado-event-handler-summary.md)
