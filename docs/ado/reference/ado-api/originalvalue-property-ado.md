---
title: Свойство OriginalValue (ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Field20::OriginalValue
helpviewer_keywords:
- OriginalValue property [ADO]
ms.assetid: 6e33c6ec-14d9-4b1d-ba9b-cb99862e7bac
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 512569ce2baa8acabdf8bcbf8f637ebf20e4f613
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "67917842"
---
# <a name="originalvalue-property-ado"></a>Свойство OriginalValue (ADO)
Указывает значение [поля](../../../ado/reference/ado-api/field-object.md) , которое существовало в записи до внесения каких-либо изменений.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение **типа Variant** , представляющее значение поля до любого изменения.  
  
## <a name="remarks"></a>Remarks  
 Используйте свойство **originalValue** , чтобы вернуть исходное значение поля для поля из текущей записи.  
  
 В *режиме немедленного обновления* (в котором поставщик записывает изменения в базовый источник данных после вызова метода [Update](../../../ado/reference/ado-api/update-method.md) ) свойство **originalValue** возвращает значение поля, существовавшее до любых изменений (то есть с момента последнего вызова метода **обновления** ). Это то же значение, которое метод [CancelUpdate](../../../ado/reference/ado-api/cancelupdate-method-ado.md) использует для замены свойства [value](../../../ado/reference/ado-api/value-property-ado.md) .  
  
 В *режиме пакетного обновления* (в котором поставщик кэширует несколько изменений и записывает их в базовый источник данных только при вызове метода [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md) ), свойство **originalValue** возвращает значение поля, существовавшее до любых изменений (то есть с момента последнего вызова метода **UpdateBatch** ). Это то же значение, которое метод [CancelBatch](../../../ado/reference/ado-api/cancelbatch-method-ado.md) использует для замены свойства **value** . При использовании этого свойства со свойством [UnderlyingValue](../../../ado/reference/ado-api/underlyingvalue-property.md) можно разрешить конфликты, возникающие в пакетных обновлениях.  
  
## <a name="record"></a>Записей  
 Для объектов [записи](../../../ado/reference/ado-api/record-object-ado.md) свойство **originalValue** будет пустым для полей, добавленных до вызова метода [Update](../../../ado/reference/ado-api/update-method.md) .  
  
## <a name="applies-to"></a>Применяется к  
 [Объект Field](../../../ado/reference/ado-api/field-object.md)  
  
## <a name="see-also"></a>См. также  
 [Примеры свойств OriginalValue и UnderlyingValue (Visual Basic)](../../../ado/reference/ado-api/originalvalue-and-underlyingvalue-properties-example-vb.md)   
 [Пример свойств OriginalValue и UnderlyingValue (Visual c++)](../../../ado/reference/ado-api/originalvalue-and-underlyingvalue-properties-example-vc.md)   
 [Свойство UnderlyingValue](../../../ado/reference/ado-api/underlyingvalue-property.md)
