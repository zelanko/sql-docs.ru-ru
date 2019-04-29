---
title: Свойство UnderlyingValue | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Field20::GetUnderlyingValue
- Field20::get_UnderlyingValue
- Field20::UnderlyingValue
helpviewer_keywords:
- UnderlyingValue property
ms.assetid: 00a0c8b8-8b63-433f-95b8-020ab05874a0
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b7bcb751fb32634fc544dfa11ee862cd47112514
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63043509"
---
# <a name="underlyingvalue-property"></a>Свойство UnderlyingValue
Указывает текущее значение [поле](../../../ado/reference/ado-api/field-object.md) объекта базы данных.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает **Variant** значение, указывающее значение **поле**.  
  
## <a name="remarks"></a>Примечания  
 Используйте **UnderlyingValue** свойство для возврата текущего значения поля из базы данных. Значение поля в **UnderlyingValue** свойство является значением, которое является видимым для транзакции и может быть результатом недавнего обновления другой транзакцией. Это может отличаться от [OriginalValue](../../../ado/reference/ado-api/originalvalue-property-ado.md) свойство, которое отражает значение, которое изначально было возвращено к [записей](../../../ado/reference/ado-api/recordset-object-ado.md).  
  
 Это похоже на использование [Resync](../../../ado/reference/ado-api/resync-method.md) метод, но **UnderlyingValue** свойство возвращает только значение для указанного поля из текущей записи. Это то же значение, которое [Resync](../../../ado/reference/ado-api/resync-method.md) метод используется для замены [значение](../../../ado/reference/ado-api/value-property-ado.md) свойства.  
  
 При использовании этого свойства с **OriginalValue** можно устранить конфликты, возникающие из пакетных обновлений.  
  
## <a name="record"></a>Записей  
 Для [записи](../../../ado/reference/ado-api/record-object-ado.md) объектов, это свойство будет пустым для поля, добавленные перед [обновления](../../../ado/reference/ado-api/update-method.md) вызывается.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Field](../../../ado/reference/ado-api/field-object.md)  
  
## <a name="see-also"></a>См. также  
 [Примеры OriginalValue и Underlyingvalue свойства (Visual Basic)](../../../ado/reference/ado-api/originalvalue-and-underlyingvalue-properties-example-vb.md)   
 [Примеры OriginalValue и Underlyingvalue свойства (Visual C++)](../../../ado/reference/ado-api/originalvalue-and-underlyingvalue-properties-example-vc.md)   
 [Свойство OriginalValue (ADO)](../../../ado/reference/ado-api/originalvalue-property-ado.md)   
 [Метод Resync](../../../ado/reference/ado-api/resync-method.md)
