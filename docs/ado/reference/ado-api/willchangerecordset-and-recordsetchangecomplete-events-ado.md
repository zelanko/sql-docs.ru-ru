---
description: События WillChangeRecordset и RecordsetChangeComplete (ADO)
title: События Виллчанжерекордсет и Рекордсетчанжекомплете (ADO) | Документация Майкрософт
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
author: rothja
ms.author: jroth
ms.openlocfilehash: fa7ec524d950a45dd11e1bc62a983810ab2550ca
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88441516"
---
# <a name="willchangerecordset-and-recordsetchangecomplete-events-ado"></a>События WillChangeRecordset и RecordsetChangeComplete (ADO)
Событие **виллчанжерекордсет** вызывается до того, как ожидающая операция изменяет [набор записей](../../../ado/reference/ado-api/recordset-object-ado.md). Событие **рекордсетчанжекомплете** вызывается после изменения **набора записей** .  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
WillChangeRecordset adReason, adStatus, pRecordset  
RecordsetChangeComplete adReason, pError, adStatus, pRecordset  
```  
  
#### <a name="parameters"></a>Параметры  
 *adReason*  
 Значение [евентреасоненум](../../../ado/reference/ado-api/eventreasonenum.md) , указывающее причину события. Его значением может быть **адрснрекуери**, **адрснресинч**, **адрснклосе**, **адрснопен**.  
  
 *адстатус*  
 Значение состояния [евентстатусенум](../../../ado/reference/ado-api/eventstatusenum.md) .  
  
 При вызове **виллчанжерекордсет** этот параметр имеет значение **адстатусок** , если операция, вызвавшая событие, прошла успешно. Он имеет значение **адстатускантдени** , если это событие не может запросить отмену ожидающей операции.  
  
 При вызове **рекордсетчанжекомплете** этот параметр имеет значение **адстатусок** , если операция, вызвавшая событие, была выполнена успешно, **адстатусеррорсоккурред** , если операция завершилась сбоем, или **адстатусканцел** , если операция, связанная с ранее принятым событием **виллчанжерекордсет** , была отменена.  
  
 Перед возвратом **виллчанжерекордсет** задайте для этого параметра значение **адстатусканцел** , чтобы запросить отмену ожидающей операции, или задайте для этого параметра значение адстатусунвантедевент, чтобы избежать появления последующих уведомлений.  
  
 Перед возвратом **виллчанжерекордсет** или **рекордсетчанжекомплете** присвойте этому параметру значение **адстатусунвантедевент** , чтобы предотвратить появление последующих уведомлений.  
  
 *pError*  
 Объект [ошибки](../../../ado/reference/ado-api/error-object.md) . Она описывает ошибку, которая возникла, если значение *адстатус* равно **адстатусеррорсоккурред**; в противном случае он не задан.  
  
 *предшнур*  
 Объект **Recordset** . **Набор записей** , для которого произошло это событие.  
  
## <a name="remarks"></a>Remarks  
 Событие **виллчанжерекордсет** или **рекордсетчанжекомплете** может возникать из-за методов [Requery](../../../ado/reference/ado-api/requery-method.md) или [Open](../../../ado/reference/ado-api/open-method-ado-recordset.md) **набора записей** .  
  
 Если поставщик не поддерживает закладки, уведомление о событии **рекордсетчанже** возникает каждый раз при получении новых строк от поставщика. Частота этого события зависит от свойства **рекордсеткачесизе** .  
  
 Необходимо присвоить параметру **адстатус** значение **адстатусунвантедевент** для каждого возможного значения **адреасон** , чтобы полностью отключить уведомление о событии для любого события, включающего параметр **адреасон** .  
  
## <a name="see-also"></a>См. также:  
 [Пример модели событий ADO (Visual c++)](../../../ado/reference/ado-api/ado-events-model-example-vc.md)   
 [Общие сведения об обработчике событий ADO](../../../ado/guide/data/ado-event-handler-summary.md)
