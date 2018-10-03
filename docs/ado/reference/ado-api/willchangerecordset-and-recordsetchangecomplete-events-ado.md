---
title: События WillChangeRecordset и Recordsetchangecomplete (ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9ed1c7a9f1ed86359eef75fdaf13c9e40d838f3f
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47718872"
---
# <a name="willchangerecordset-and-recordsetchangecomplete-events-ado"></a>События WillChangeRecordset и RecordsetChangeComplete (ADO)
**События WillChangeRecordset** событие вызывается перед отложенная операция изменяет [записей](../../../ado/reference/ado-api/recordset-object-ado.md). **RecordsetChangeComplete** событие вызывается после **записей** был изменен.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
WillChangeRecordset adReason, adStatus, pRecordset  
RecordsetChangeComplete adReason, pError, adStatus, pRecordset  
```  
  
#### <a name="parameters"></a>Параметры  
 *adReason*  
 [EventReasonEnum](../../../ado/reference/ado-api/eventreasonenum.md) значение, указывающее причину для данного события. Его значение может быть **adRsnRequery**, **adRsnResynch**, **adRsnClose**, **adRsnOpen**.  
  
 *adStatus*  
 [EventStatusEnum](../../../ado/reference/ado-api/eventstatusenum.md) значение состояния.  
  
 Когда **события WillChangeRecordset** является именем, этот параметр имеет значение **adStatusOK** при успешной операции, которая вызвала событие. Ему будет присвоено **adStatusCantDeny** Если это событие не может запросить отмену отложенной операции.  
  
 При **RecordsetChangeComplete** является именем, этот параметр имеет значение **adStatusOK** Если успешного выполнения операции, которая вызвала событие **adStatusErrorsOccurred** Если Сбой операции, или **adStatusCancel** Если операции, связанные с ранее принятые **события WillChangeRecordset** событие было отменено.  
  
 Прежде чем **события WillChangeRecordset** возвращает, присвойте этому параметру значение **adStatusCancel** запросить отмену отложенной операции или присвойте этому параметру значение adStatusUnwantedEvent во избежание последующих уведомления.  
  
 Прежде чем **события WillChangeRecordset** или **RecordsetChangeComplete** возвращает, присвойте этому параметру значение **adStatusUnwantedEvent** игнорировать последующие уведомления.  
  
 *pError*  
 [Ошибка](../../../ado/reference/ado-api/error-object.md) объекта. Он описывает ошибки, возникшей при значение *adStatus* — **adStatusErrorsOccurred**; в противном случае оно не задано.  
  
 *pRecordset*  
 Объект **записей** объекта. **Записей** для возникновения этого события.  
  
## <a name="remarks"></a>Примечания  
 Объект **события WillChangeRecordset** или **RecordsetChangeComplete** событие может происходить из-за **записей** [Requery](../../../ado/reference/ado-api/requery-method.md) или [Откройте](../../../ado/reference/ado-api/open-method-ado-recordset.md) методы.  
  
 Если поставщик не поддерживает закладки, **RecordsetChange** уведомления о событии возникает при каждом новых строк, возвращаемых от поставщика. Зависит от частоты возникновения этого события **RecordsetCacheSize** свойство.  
  
 Необходимо задать **adStatus** параметр **adStatusUnwantedEvent** для каждого возможного **adReason** значение полностью остановить уведомление о событии для любого события, которое включает в себя **adReason** параметра.  
  
## <a name="see-also"></a>См. также  
 [Пример модели событий ADO (Visual C++)](../../../ado/reference/ado-api/ado-events-model-example-vc.md)   
 [Общие сведения об обработчике событий ADO](../../../ado/guide/data/ado-event-handler-summary.md)
