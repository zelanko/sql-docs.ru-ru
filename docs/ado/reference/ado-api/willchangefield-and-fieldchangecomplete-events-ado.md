---
description: События WillChangeField и FieldChangeComplete (ADO)
title: События Виллчанжефиелд и Фиелдчанжекомплете (ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- FieldChangeComplete
- Recordset::WillChangeField
- Recordset::FieldChangeComplete
- WillChangeField
helpviewer_keywords:
- WillChangeField event [ADO]
- fieldchangecomplete event [ADO]
ms.assetid: 3e49fb89-c45b-4d39-823e-3cc887c59b37
author: rothja
ms.author: jroth
ms.openlocfilehash: be000a8ff9154c79c2b98c9bc57f79f3537743c9
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88441536"
---
# <a name="willchangefield-and-fieldchangecomplete-events-ado"></a>События WillChangeField и FieldChangeComplete (ADO)
Событие **виллчанжефиелд** вызывается до того, как ожидающая операция изменяет значение одного или нескольких объектов [field](../../../ado/reference/ado-api/field-object.md) в [наборе записей](../../../ado/reference/ado-api/recordset-object-ado.md). Событие **фиелдчанжекомплете** вызывается после изменения значения одного или нескольких объектов **field** .  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
WillChangeField cFields, Fields, adStatus, pRecordset  
FieldChangeComplete cFields, Fields, pError, adStatus, pRecordset  
```  
  
#### <a name="parameters"></a>Параметры  
 *кфиелдс*  
 Значение **типа Long** , указывающее количество объектов **field** в *полях*.  
  
 *Поля*  
 Для **виллчанжефиелд**параметр *Fields* является массивом **вариантов** , содержащих объекты **полей** с исходными значениями. Для **фиелдчанжекомплете**параметр *Fields* является массивом **вариантов** , содержащих объекты **полей** с измененными значениями.  
  
 *pError*  
 Объект [ошибки](../../../ado/reference/ado-api/error-object.md) . Она описывает ошибку, которая возникла, если значение *адстатус* равно **адстатусеррорсоккурред**; в противном случае он не задан.  
  
 *адстатус*  
 Значение состояния [евентстатусенум](../../../ado/reference/ado-api/eventstatusenum.md) .  
  
 При вызове **виллчанжефиелд** этот параметр имеет значение **адстатусок** , если операция, вызвавшая событие, прошла успешно. Он имеет значение **адстатускантдени** , если это событие не может запросить отмену ожидающей операции.  
  
 При вызове **фиелдчанжекомплете** этот параметр имеет значение **адстатусок** , если операция, вызвавшая событие, прошла успешно, или значение **адстатусеррорсоккурред** в случае сбоя операции.  
  
 Перед возвратом **виллчанжефиелд** присвойте этому параметру значение **адстатусканцел** , чтобы запросить отмену ожидающей операции.  
  
 Перед возвратом **фиелдчанжекомплете** задайте для этого параметра значение **адстатусунвантедевент** , чтобы предотвратить появление последующих уведомлений.  
  
 *предшнур*  
 Объект **Recordset** . **Набор записей** , для которого произошло это событие.  
  
## <a name="remarks"></a>Remarks  
 Событие **виллчанжефиелд** или **фиелдчанжекомплете** может возникнуть при установке свойства [value](../../../ado/reference/ado-api/value-property-ado.md) и вызове метода [Update](../../../ado/reference/ado-api/update-method.md) с параметрами массива полей и значений.  
  
## <a name="see-also"></a>См. также:  
 [Пример модели событий ADO (Visual c++)](../../../ado/reference/ado-api/ado-events-model-example-vc.md)   
 [Общие сведения об обработчике событий ADO](../../../ado/guide/data/ado-event-handler-summary.md)
