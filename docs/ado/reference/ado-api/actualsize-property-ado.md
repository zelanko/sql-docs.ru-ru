---
description: Свойство ActualSize (ADO)
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 53384838d53003f0c4f81ec3b629e987ce2649a8
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88451636"
---
# <a name="actualsize-property-ado"></a>Свойство ActualSize (ADO)
Указывает фактическую длину значения поля в байтах.  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Возвращает значение **типа Long** .  
  
## <a name="remarks"></a>Remarks  
 Используйте свойство **ActualSize** , чтобы вернуть фактическую длину значения объекта [поля](../../../ado/reference/ado-api/field-object.md) . Для всех полей свойство **ActualSize** доступно только для чтения. Если ADO не удается определить длину значения объекта **поля** , свойство **ActualSize** возвращает **адункновн**.  
  
 Свойства **ActualSize** и [DefinedSize](../../../ado/reference/ado-api/definedsize-property.md) различаются, как показано в следующем примере. Объект **поля** с объявленным типом **адварчар** и максимальной длиной 50 символов возвращает значение свойства **DefinedSize** , равное 50, но возвращаемое значение свойства **ActualSize** — это длина данных, хранящихся в поле для текущей записи. **Поля** с **DefinedSize** размером более 255 байт рассматриваются как столбцы переменной длины.  
  
## <a name="applies-to"></a>Применение  
 [Объект Field](../../../ado/reference/ado-api/field-object.md)  
  
## <a name="see-also"></a>См. также:  
 [Примеры свойств ActualSize и DefinedSize (Visual Basic)](../../../ado/reference/ado-api/actualsize-and-definedsize-properties-example-vb.md)   
 [Пример свойств ActualSize и DefinedSize (Visual c++)](../../../ado/reference/ado-api/actualsize-and-definedsize-properties-example-vc.md)   
 [Свойство DefinedSize](../../../ado/reference/ado-api/definedsize-property.md)
