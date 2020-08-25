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
ms.openlocfilehash: 84c861c2a344276a80ea8e8fd98f84aeb2bb7cbc
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2020
ms.locfileid: "88776903"
---
# <a name="willchangefield-and-fieldchangecomplete-events-ado"></a>События WillChangeField и FieldChangeComplete (ADO)
Событие **виллчанжефиелд** вызывается до того, как ожидающая операция изменяет значение одного или нескольких объектов [field](./field-object.md) в [наборе записей](./recordset-object-ado.md). Событие **фиелдчанжекомплете** вызывается после изменения значения одного или нескольких объектов **field** .  
  
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
 Объект [ошибки](./error-object.md) . Она описывает ошибку, которая возникла, если значение *адстатус* равно **адстатусеррорсоккурред**; в противном случае он не задан.  
  
 *адстатус*  
 Значение состояния [евентстатусенум](./eventstatusenum.md) .  
  
 При вызове **виллчанжефиелд** этот параметр имеет значение **адстатусок** , если операция, вызвавшая событие, прошла успешно. Он имеет значение **адстатускантдени** , если это событие не может запросить отмену ожидающей операции.  
  
 При вызове **фиелдчанжекомплете** этот параметр имеет значение **адстатусок** , если операция, вызвавшая событие, прошла успешно, или значение **адстатусеррорсоккурред** в случае сбоя операции.  
  
 Перед возвратом **виллчанжефиелд** присвойте этому параметру значение **адстатусканцел** , чтобы запросить отмену ожидающей операции.  
  
 Перед возвратом **фиелдчанжекомплете** задайте для этого параметра значение **адстатусунвантедевент** , чтобы предотвратить появление последующих уведомлений.  
  
 *предшнур*  
 Объект **Recordset** . **Набор записей** , для которого произошло это событие.  
  
## <a name="remarks"></a>Remarks  
 Событие **виллчанжефиелд** или **фиелдчанжекомплете** может возникнуть при установке свойства [value](./value-property-ado.md) и вызове метода [Update](./update-method.md) с параметрами массива полей и значений.  
  
## <a name="see-also"></a>См. также  
 [Пример модели событий ADO (Visual c++)](./ado-events-model-example-vc.md)   
 [Общие сведения об обработчике событий ADO](../../guide/data/ado-event-handler-summary.md)