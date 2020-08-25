---
description: События WillChangeRecord и RecordChangeComplete (ADO)
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 8f69b16392204722e4efd3dc91602a920316919d
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2020
ms.locfileid: "88776883"
---
# <a name="willchangerecord-and-recordchangecomplete-events-ado"></a>События WillChangeRecord и RecordChangeComplete (ADO)
Событие **виллчанжерекорд** вызывается до того, как в [наборе записей](./recordset-object-ado.md) изменяется одна или несколько записей (строк). Событие **рекордчанжекомплете** вызывается после изменения одной или нескольких записей.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
WillChangeRecord adReason, cRecords, adStatus, pRecordset  
RecordChangeCompleteadReason, cRecords, pError, adStatus, pRecordset  
```  
  
#### <a name="parameters"></a>Параметры  
 *adReason*  
 Значение [евентреасоненум](./eventreasonenum.md) , указывающее причину события. Его значением может быть **адрснадднев**, **адрснделете**, **адрснупдате**, **адрснундаупдате**, **адрснундоадднев**, **адрснундоделете**или **adRsnFirstChange**.  
  
 *крекордс*  
 Значение **типа Long** , указывающее количество измененных записей (затронутых).  
  
 *pError*  
 Объект [ошибки](./error-object.md) . Она описывает ошибку, которая возникла, если значение *адстатус* равно **адстатусеррорсоккурред**; в противном случае он не задан.  
  
 *адстатус*  
 Значение состояния [евентстатусенум](./eventstatusenum.md) .  
  
 При вызове **виллчанжерекорд** этот параметр имеет значение **адстатусок** , если операция, вызвавшая событие, прошла успешно. Он имеет значение **адстатускантдени** , если это событие не может запросить отмену ожидающей операции.  
  
 При вызове **рекордчанжекомплете** этот параметр имеет значение **адстатусок** , если операция, вызвавшая событие, прошла успешно, или значение **адстатусеррорсоккурред** в случае сбоя операции.  
  
 Перед возвратом **виллчанжерекорд** задайте для этого параметра значение **адстатусканцел** , чтобы запросить отмену операции, вызвавшей это событие, или задайте для этого параметра значение **адстатусунвантедевент** , чтобы предотвратить появление последующих уведомлений.  
  
 Перед возвратом **рекордчанжекомплете** задайте для этого параметра значение **адстатусунвантедевент** , чтобы предотвратить появление последующих уведомлений.  
  
 *предшнур*  
 Объект **Recordset** . **Набор записей** , для которого произошло это событие.  
  
## <a name="remarks"></a>Remarks  
 Событие **виллчанжерекорд** или **рекордчанжекомплете** может возникать для первого измененного поля в строке из-за следующих операций **с наборами записей** : [Update](./update-method.md), [Delete](./delete-method-ado-recordset.md), [CancelUpdate](./cancelupdate-method-ado.md), [AddNew](./addnew-method-ado.md), [UpdateBatch](./updatebatch-method.md)и [CancelBatch](./cancelbatch-method-ado.md). Значение [примеры CursorType](./cursortype-property-ado.md) **набора записей** определяет, какие операции приводят к возникновению событий.  
  
 Во время события **виллчанжерекорд** свойству **Recordset** [Filter фильтра](./filter-property.md) набора записей присваивается значение **адфилтераффектедрекордс**. Это свойство нельзя изменить во время обработки события.  
  
 Необходимо присвоить параметру **адстатус** значение **адстатусунвантедевент** для каждого возможного значения **адреасон** , чтобы полностью отключить уведомление о событии для любого события, включающего параметр **адреасон** .  
  
## <a name="see-also"></a>См. также  
 [Пример модели событий ADO (Visual c++)](./ado-events-model-example-vc.md)   
 [Общие сведения об обработчике событий ADO](../../guide/data/ado-event-handler-summary.md)