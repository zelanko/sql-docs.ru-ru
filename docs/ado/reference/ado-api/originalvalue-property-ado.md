---
title: "Свойство OriginalValue (ADO) | Документы Microsoft"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- Field20::OriginalValue
helpviewer_keywords:
- OriginalValue property [ADO]
ms.assetid: 6e33c6ec-14d9-4b1d-ba9b-cb99862e7bac
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 018f07a06e96f9284d0a8e63742a5abebca925e1
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="originalvalue-property-ado"></a>Свойство OriginalValue (ADO)
Указывает значение [поле](../../../ado/reference/ado-api/field-object.md) , состоянии, предшествующем в записи были сделаны изменения.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает **Variant** значение, представляющее значение поля до изменения.  
  
## <a name="remarks"></a>Замечания  
 Используйте **OriginalValue** свойство, чтобы вернуть исходное значение поля для поля с текущей записью.  
  
 В *режим немедленного обновления* (в котором поставщик записывает изменения в источнике данных после вызова метода [обновление](../../../ado/reference/ado-api/update-method.md) метод), **OriginalValue** возвращает свойство значение поля, которые существовали до изменения (то есть с момента последнего **обновление** вызова метода). Это то же самое значение, которое [CancelUpdate](../../../ado/reference/ado-api/cancelupdate-method-ado.md) метод используется для замены [значение](../../../ado/reference/ado-api/value-property-ado.md) свойства.  
  
 В *пакетный режим обновления* (в котором поставщик кэширует внесение нескольких изменений и записывает их в базовом источнике данных только при вызове [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md) метод), **OriginalValue** свойство возвращает значение поля, которые существовали до изменения (то есть с момента последнего **UpdateBatch** вызова метода). Это то же самое значение, которое [CancelBatch](../../../ado/reference/ado-api/cancelbatch-method-ado.md) метод используется для замены **значение** свойства. При использовании этого свойства и [UnderlyingValue](../../../ado/reference/ado-api/underlyingvalue-property.md) можно устранить конфликты, возникающие из пакета обновления.  
  
## <a name="record"></a>Записей  
 Для [запись](../../../ado/reference/ado-api/record-object-ado.md) объектов, **OriginalValue** свойства не определено для поля, добавленные перед [обновление](../../../ado/reference/ado-api/update-method.md) вызывается.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект field](../../../ado/reference/ado-api/field-object.md)  
  
## <a name="see-also"></a>См. также:  
 [OriginalValue и UnderlyingValue-пример свойства (Visual Basic)](../../../ado/reference/ado-api/originalvalue-and-underlyingvalue-properties-example-vb.md)   
 [OriginalValue и пример свойства UnderlyingValue (VC ++)](../../../ado/reference/ado-api/originalvalue-and-underlyingvalue-properties-example-vc.md)   
 [Свойство UnderlyingValue](../../../ado/reference/ado-api/underlyingvalue-property.md)

