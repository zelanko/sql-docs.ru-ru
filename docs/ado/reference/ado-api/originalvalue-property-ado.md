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
manager: craigg
ms.openlocfilehash: 0d25c44883c7f04f1543639ecc870c00ad5beb9d
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47649002"
---
# <a name="originalvalue-property-ado"></a>Свойство OriginalValue (ADO)
Указывает значение [поле](../../../ado/reference/ado-api/field-object.md) , существовали в записи, прежде чем были сделаны изменения.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает **Variant** значение, представляющее значение поля до изменения.  
  
## <a name="remarks"></a>Примечания  
 Используйте **OriginalValue** свойство, чтобы вернуть исходное значение поля для поля из текущей записи.  
  
 В *режим немедленного обновления* (в котором поставщик записывает изменения в источнике данных после вызова метода [обновление](../../../ado/reference/ado-api/update-method.md) метод), **OriginalValue** возвращает значение поля, которые существовали до изменения (то есть с момента последнего **обновления** вызова метода). Это то же значение, которое [CancelUpdate](../../../ado/reference/ado-api/cancelupdate-method-ado.md) метод используется для замены [значение](../../../ado/reference/ado-api/value-property-ado.md) свойства.  
  
 В *пакетный режим обновления* (в котором поставщик кэширует несколько изменений и записывает их в базовом источнике данных только в том случае, когда вы вызываете [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md) метод), **OriginalValue** свойство возвращает значение поля, которые существовали до изменения (то есть с момента последнего **UpdateBatch** вызова метода). Это то же значение, которое [CancelBatch](../../../ado/reference/ado-api/cancelbatch-method-ado.md) метод используется для замены **значение** свойства. При использовании этого свойства с [UnderlyingValue](../../../ado/reference/ado-api/underlyingvalue-property.md) можно устранить конфликты, возникающие из пакетных обновлений.  
  
## <a name="record"></a>Записей  
 Для [записи](../../../ado/reference/ado-api/record-object-ado.md) объектов, **OriginalValue** свойство будет пустым для поля, добавленные перед [обновления](../../../ado/reference/ado-api/update-method.md) вызывается.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Field](../../../ado/reference/ado-api/field-object.md)  
  
## <a name="see-also"></a>См. также  
 [Примеры OriginalValue и Underlyingvalue свойства (Visual Basic)](../../../ado/reference/ado-api/originalvalue-and-underlyingvalue-properties-example-vb.md)   
 [Примеры OriginalValue и Underlyingvalue свойства (Visual C++)](../../../ado/reference/ado-api/originalvalue-and-underlyingvalue-properties-example-vc.md)   
 [Свойство UnderlyingValue](../../../ado/reference/ado-api/underlyingvalue-property.md)
