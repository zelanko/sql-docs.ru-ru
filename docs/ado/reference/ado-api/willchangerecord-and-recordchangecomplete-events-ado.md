---
title: События Виллчанжерекорд и Рекордчанжекомплете (ADO) | Документация Майкрософт
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
ms.openlocfilehash: 6e632db34fbbacbee61cd943067052af27a8cfe8
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67938679"
---
# <a name="willchangerecord-and-recordchangecomplete-events-ado"></a>События WillChangeRecord и RecordChangeComplete (ADO)
Событие **виллчанжерекорд** вызывается до того, как в [наборе записей](../../../ado/reference/ado-api/recordset-object-ado.md) изменяется одна или несколько записей (строк). Событие **рекордчанжекомплете** вызывается после изменения одной или нескольких записей.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
WillChangeRecord adReason, cRecords, adStatus, pRecordset  
RecordChangeCompleteadReason, cRecords, pError, adStatus, pRecordset  
```  
  
#### <a name="parameters"></a>Параметры  
 *адреасон*  
 Значение [евентреасоненум](../../../ado/reference/ado-api/eventreasonenum.md) , указывающее причину события. Его значением может быть **адрснадднев**, **адрснделете**, **адрснупдате**, **адрснундаупдате**, **адрснундоадднев**, **адрснундоделете**или **adRsnFirstChange**.  
  
 *крекордс*  
 Значение **типа Long** , указывающее количество измененных записей (затронутых).  
  
 *pError*  
 Объект [ошибки](../../../ado/reference/ado-api/error-object.md) . Она описывает ошибку, которая возникла, если значение *адстатус* равно **адстатусеррорсоккурред**; в противном случае он не задан.  
  
 *адстатус*  
 Значение состояния [евентстатусенум](../../../ado/reference/ado-api/eventstatusenum.md) .  
  
 При вызове **виллчанжерекорд** этот параметр имеет значение **адстатусок** , если операция, вызвавшая событие, прошла успешно. Он имеет значение **адстатускантдени** , если это событие не может запросить отмену ожидающей операции.  
  
 При вызове **рекордчанжекомплете** этот параметр имеет значение **адстатусок** , если операция, вызвавшая событие, прошла успешно, или значение **адстатусеррорсоккурред** в случае сбоя операции.  
  
 Перед возвратом **виллчанжерекорд** задайте для этого параметра значение **адстатусканцел** , чтобы запросить отмену операции, вызвавшей это событие, или задайте для этого параметра значение **адстатусунвантедевент** , чтобы предотвратить появление последующих уведомлений.  
  
 Перед возвратом **рекордчанжекомплете** задайте для этого параметра значение **адстатусунвантедевент** , чтобы предотвратить появление последующих уведомлений.  
  
 *предшнур*  
 Объект **Recordset** . **Набор записей** , для которого произошло это событие.  
  
## <a name="remarks"></a>Remarks  
 Событие **виллчанжерекорд** или **рекордчанжекомплете** может возникать для первого измененного поля в строке из-за следующих операций **с наборами записей** : [Update](../../../ado/reference/ado-api/update-method.md), [Delete](../../../ado/reference/ado-api/delete-method-ado-recordset.md), [CancelUpdate](../../../ado/reference/ado-api/cancelupdate-method-ado.md), [AddNew](../../../ado/reference/ado-api/addnew-method-ado.md), [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md)и [CancelBatch](../../../ado/reference/ado-api/cancelbatch-method-ado.md). Значение [примеры CursorType](../../../ado/reference/ado-api/cursortype-property-ado.md) **набора записей** определяет, какие операции приводят к возникновению событий.  
  
 Во время события **виллчанжерекорд** свойству **** [Filter фильтра](../../../ado/reference/ado-api/filter-property.md) набора записей присваивается значение **адфилтераффектедрекордс**. Это свойство нельзя изменить во время обработки события.  
  
 Необходимо присвоить параметру **адстатус** значение **адстатусунвантедевент** для каждого возможного значения **адреасон** , чтобы полностью отключить уведомление о событии для любого события, включающего параметр **адреасон** .  
  
## <a name="see-also"></a>См. также:  
 [Пример модели событий ADO (Visual c++)](../../../ado/reference/ado-api/ado-events-model-example-vc.md)   
 [Общие сведения об обработчике событий ADO](../../../ado/guide/data/ado-event-handler-summary.md)
