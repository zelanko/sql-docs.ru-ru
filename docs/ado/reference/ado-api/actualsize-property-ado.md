---
description: Свойство ActualSize (ADO)
title: Свойство ActualSize (ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
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
ms.openlocfilehash: 6684c03c94d26b8c8f6366ac41ccd1b331016426
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2020
ms.locfileid: "88976905"
---
# <a name="actualsize-property-ado"></a>Свойство ActualSize (ADO)
Указывает фактическую длину значения поля в байтах.  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Возвращает значение **типа Long** .  
  
## <a name="remarks"></a>Remarks  
 Используйте свойство **ActualSize** , чтобы вернуть фактическую длину значения объекта [поля](./field-object.md) . Для всех полей свойство **ActualSize** доступно только для чтения. Если ADO не удается определить длину значения объекта **поля** , свойство **ActualSize** возвращает **адункновн**.  
  
 Свойства **ActualSize** и [DefinedSize](./definedsize-property.md) различаются, как показано в следующем примере. Объект **поля** с объявленным типом **адварчар** и максимальной длиной 50 символов возвращает значение свойства **DefinedSize** , равное 50, но возвращаемое значение свойства **ActualSize** — это длина данных, хранящихся в поле для текущей записи. **Поля** с **DefinedSize** размером более 255 байт рассматриваются как столбцы переменной длины.  
  
## <a name="applies-to"></a>Применение  
 [Объект Field](./field-object.md)  
  
## <a name="see-also"></a>См. также  
 [Примеры свойств ActualSize и DefinedSize (Visual Basic)](./actualsize-and-definedsize-properties-example-vb.md)   
 [Пример свойств ActualSize и DefinedSize (Visual c++)](./actualsize-and-definedsize-properties-example-vc.md)   
 [Свойство DefinedSize](./definedsize-property.md)