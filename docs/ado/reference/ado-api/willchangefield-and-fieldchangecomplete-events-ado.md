---
title: WillChangeField и FieldChangeComplete события (ADO) | Документы Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
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
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 108aea1a4f8106c3a84b411591d4866235726efc
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/11/2018
ms.locfileid: "35282857"
---
# <a name="willchangefield-and-fieldchangecomplete-events-ado"></a>WillChangeField и FieldChangeComplete события (ADO)
**WillChangeField** событие вызывается перед ожидающая выполнения операция изменяет значение одного или нескольких [поле](../../../ado/reference/ado-api/field-object.md) объекты в [записей](../../../ado/reference/ado-api/recordset-object-ado.md). **FieldChangeComplete** событие вызывается после изменения значения одного или нескольких **поле** объектов был изменен.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
WillChangeField cFields, Fields, adStatus, pRecordset  
FieldChangeComplete cFields, Fields, pError, adStatus, pRecordset  
```  
  
#### <a name="parameters"></a>Параметры  
 *cFields*  
 Объект **длинные** , указывающее количество **поле** объекты в *поля*.  
  
 *Fields*  
 Для **WillChangeField**, *поля* параметр представляет собой массив **варианты** , содержащий **поле** объекты на основе исходных значений. Для **FieldChangeComplete**, *поля* параметр представляет собой массив **варианты** , содержащий **поле** объекты с измененными значениями .  
  
 *pError*  
 [Ошибка](../../../ado/reference/ado-api/error-object.md) объекта. Здесь описываются ошибки, возникшей при значение *adStatus* — **adStatusErrorsOccurred**; в противном случае оно не задано.  
  
 *adStatus*  
 [EventStatusEnum](../../../ado/reference/ado-api/eventstatusenum.md) значение состояния.  
  
 Когда **WillChangeField** — вызывается, этот параметр имеет значение **adStatusOK** при успешном выполнении операции, которая вызвала событие. Ему присваивается **adStatusCantDeny** Если это событие не удается запросить отмену отложенной операции.  
  
 Когда **FieldChangeComplete** — вызывается, этот параметр имеет значение **adStatusOK** при успешном выполнении операции, которая вызвала событие или для **adStatusErrorsOccurred** Если Сбой операции.  
  
 Прежде чем **WillChangeField** возвращает, присвойте этому параметру значение **adStatusCancel** чтобы запросить отмену отложенной операции.  
  
 Прежде чем **FieldChangeComplete** возвращает, присвойте этому параметру значение **adStatusUnwantedEvent** для предотвращения последующих уведомлений.  
  
 *pRecordset*  
 Объект **записей** объекта. **Записей** для возникновения этого события.  
  
## <a name="remarks"></a>Примечания  
 Объект **WillChangeField** или **FieldChangeComplete** событие может происходить при задании [значение](../../../ado/reference/ado-api/value-property-ado.md) и вызова [обновление](../../../ado/reference/ado-api/update-method.md) метод поля и массив параметров.  
  
## <a name="see-also"></a>См. также  
 [Пример модели событий ADO (VC ++)](../../../ado/reference/ado-api/ado-events-model-example-vc.md)   
 [Общие сведения об обработчике событий ADO](../../../ado/guide/data/ado-event-handler-summary.md)
