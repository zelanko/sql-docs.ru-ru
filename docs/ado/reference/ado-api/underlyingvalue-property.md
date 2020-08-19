---
description: Свойство UnderlyingValue
title: UnderlyingValue, свойство | Документация Майкрософт
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 12788438d7db4cf51df564ea7d262bb4e7ef693d
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88441706"
---
# <a name="underlyingvalue-property"></a>Свойство UnderlyingValue
Указывает текущее значение объекта [поля](../../../ado/reference/ado-api/field-object.md) в базе данных.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение **типа Variant** , указывающее значение **поля**.  
  
## <a name="remarks"></a>Remarks  
 Используйте свойство **UnderlyingValue** , чтобы вернуть текущее значение поля из базы данных. Значение поля в свойстве **UnderlyingValue** является значением, видимым для транзакции и может быть результатом последнего обновления другой транзакции. Это может отличаться от свойства [originalValue](../../../ado/reference/ado-api/originalvalue-property-ado.md) , которое отражает значение, первоначально возвращенное [набору записей](../../../ado/reference/ado-api/recordset-object-ado.md).  
  
 Это похоже на использование метода повторной [синхронизации](../../../ado/reference/ado-api/resync-method.md) , но свойство **UnderlyingValue** возвращает только значение для определенного поля из текущей записи. Это то же значение, которое метод [Resync](../../../ado/reference/ado-api/resync-method.md) использует для замены свойства [value](../../../ado/reference/ado-api/value-property-ado.md) .  
  
 При использовании этого свойства со свойством **originalValue** можно разрешить конфликты, возникающие в пакетных обновлениях.  
  
## <a name="record"></a>Записей  
 Для объектов [записи](../../../ado/reference/ado-api/record-object-ado.md) это свойство будет пустым для полей, добавленных до вызова метода [Update](../../../ado/reference/ado-api/update-method.md) .  
  
## <a name="applies-to"></a>Применение  
 [Объект Field](../../../ado/reference/ado-api/field-object.md)  
  
## <a name="see-also"></a>См. также:  
 [Примеры свойств OriginalValue и UnderlyingValue (Visual Basic)](../../../ado/reference/ado-api/originalvalue-and-underlyingvalue-properties-example-vb.md)   
 [Пример свойств OriginalValue и UnderlyingValue (Visual c++)](../../../ado/reference/ado-api/originalvalue-and-underlyingvalue-properties-example-vc.md)   
 [Свойство OriginalValue (ADO)](../../../ado/reference/ado-api/originalvalue-property-ado.md)   
 [Метод Resync](../../../ado/reference/ado-api/resync-method.md)
