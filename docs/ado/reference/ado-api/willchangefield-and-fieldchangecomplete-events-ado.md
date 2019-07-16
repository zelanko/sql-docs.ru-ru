---
title: События WillChangeField и Fieldchangecomplete (ADO) | Документация Майкрософт
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 7484e2a57925cc22c83456c244dc67aded5cefd2
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67945885"
---
# <a name="willchangefield-and-fieldchangecomplete-events-ado"></a>События WillChangeField и FieldChangeComplete (ADO)
**События WillChangeField** событие вызывается перед отложенная операция изменяет значение одного или нескольких [поле](../../../ado/reference/ado-api/field-object.md) объекты в [записей](../../../ado/reference/ado-api/recordset-object-ado.md). **FieldChangeComplete** событие вызывается после значения из одного или нескольких **поле** объектов был изменен.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
WillChangeField cFields, Fields, adStatus, pRecordset  
FieldChangeComplete cFields, Fields, pError, adStatus, pRecordset  
```  
  
#### <a name="parameters"></a>Параметры  
 *cFields*  
 Объект **Long** , указывающее количество **поле** объекты в *поля*.  
  
 *Fields*  
 Для **события WillChangeField**, *поля* параметр представляет собой массив **варианты** , содержащий **поле** объекты с исходными значениями. Для **FieldChangeComplete**, *поля* параметр представляет собой массив **варианты** , содержащий **поле** объекты с измененными значениями .  
  
 *pError*  
 [Ошибка](../../../ado/reference/ado-api/error-object.md) объекта. Он описывает ошибки, возникшей при значение *adStatus* — **adStatusErrorsOccurred**; в противном случае оно не задано.  
  
 *adStatus*  
 [EventStatusEnum](../../../ado/reference/ado-api/eventstatusenum.md) значение состояния.  
  
 Когда **события WillChangeField** является именем, этот параметр имеет значение **adStatusOK** при успешной операции, которая вызвала событие. Ему будет присвоено **adStatusCantDeny** Если это событие не может запросить отмену отложенной операции.  
  
 Когда **FieldChangeComplete** является именем, этот параметр имеет значение **adStatusOK** при успешной операции, которая вызвала событие, или для **adStatusErrorsOccurred** Если Сбой операции.  
  
 Прежде чем **события WillChangeField** возвращает, присвойте этому параметру значение **adStatusCancel** на запрос на отмену отложенной операции.  
  
 Прежде чем **FieldChangeComplete** возвращает, присвойте этому параметру значение **adStatusUnwantedEvent** игнорировать последующие уведомления.  
  
 *pRecordset*  
 Объект **записей** объекта. **Записей** для возникновения этого события.  
  
## <a name="remarks"></a>Примечания  
 Объект **события WillChangeField** или **FieldChangeComplete** событие может происходить при задании [значение](../../../ado/reference/ado-api/value-property-ado.md) и вызова [обновления](../../../ado/reference/ado-api/update-method.md) метод с помощью поля и значения параметров массива.  
  
## <a name="see-also"></a>См. также  
 [Пример модели событий ADO (Visual C++)](../../../ado/reference/ado-api/ado-events-model-example-vc.md)   
 [Общие сведения об обработчике событий ADO](../../../ado/guide/data/ado-event-handler-summary.md)
