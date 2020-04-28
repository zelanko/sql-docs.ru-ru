---
title: Свойство ActualSize (ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 03/20/2018
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Field20::ActualSize
helpviewer_keywords:
- ActualSize property [ADO]
ms.assetid: 722803d0-cef5-4d4c-b79d-3f2f58052229
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 6d405113044d10244d8c4fc3483c6220bf630dc5
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "67921423"
---
# <a name="actualsize-property-ado"></a>Свойство ActualSize (ADO)
Указывает фактическую длину значения поля в байтах.  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Возвращает значение **типа Long** .  
  
## <a name="remarks"></a>Remarks  
 Используйте свойство **ActualSize** , чтобы вернуть фактическую длину значения объекта [поля](../../../ado/reference/ado-api/field-object.md) . Для всех полей свойство **ActualSize** доступно только для чтения. Если ADO не удается определить длину значения объекта **поля** , свойство **ActualSize** возвращает **адункновн**.  
  
 Свойства **ActualSize** и [DefinedSize](../../../ado/reference/ado-api/definedsize-property.md) различаются, как показано в следующем примере. Объект **поля** с объявленным типом **адварчар** и максимальной длиной 50 символов возвращает значение свойства **DefinedSize** , равное 50, но возвращаемое значение свойства **ActualSize** — это длина данных, хранящихся в поле для текущей записи. **Поля** с **DefinedSize** размером более 255 байт рассматриваются как столбцы переменной длины.  
  
## <a name="applies-to"></a>Применяется к  
 [Объект Field](../../../ado/reference/ado-api/field-object.md)  
  
## <a name="see-also"></a>См. также:  
 [Примеры свойств ActualSize и DefinedSize (Visual Basic)](../../../ado/reference/ado-api/actualsize-and-definedsize-properties-example-vb.md)   
 [Пример свойств ActualSize и DefinedSize (Visual c++)](../../../ado/reference/ado-api/actualsize-and-definedsize-properties-example-vc.md)   
 [Свойство DefinedSize](../../../ado/reference/ado-api/definedsize-property.md)
