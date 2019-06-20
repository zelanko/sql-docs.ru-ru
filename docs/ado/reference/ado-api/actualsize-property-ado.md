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
manager: jroth
ms.openlocfilehash: b864f480542c7ff649bf9b830ba445517dafb91b
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66698900"
---
# <a name="actualsize-property-ado"></a>Свойство ActualSize (ADO)
Указывает фактическую длину значения поля в байтах.  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Возвращает **Long** значение.  
  
## <a name="remarks"></a>Примечания  
 Используйте **ActualSize** фактическую длину возвращаемого свойства [поле](../../../ado/reference/ado-api/field-object.md) значения объекта. Для всех полей **ActualSize** свойство доступно только для чтения. Если ADO не может определить длину **поле** значения объекта, **ActualSize** возвращает **adUnknown**.  
  
 **ActualSize** и [DefinedSize](../../../ado/reference/ado-api/definedsize-property.md) свойства отличаются, как показано в следующем примере. Объект **поле** объект с объявленным типом **adVarChar** и возвращает максимальную длину 50 символов **DefinedSize** значение 50, но  **Примеры ActualSize** он возвращает значение свойства представляет собой длину данных, хранящихся в поле для текущей записи. **Поля** с **DefinedSize** длиной более 255 байт, обрабатываются как столбцы переменной длины.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Field](../../../ado/reference/ado-api/field-object.md)  
  
## <a name="see-also"></a>См. также  
 [Примеры ActualSize и Definedsize свойства (Visual Basic)](../../../ado/reference/ado-api/actualsize-and-definedsize-properties-example-vb.md)   
 [Примеры ActualSize и Definedsize свойства (Visual C++)](../../../ado/reference/ado-api/actualsize-and-definedsize-properties-example-vc.md)   
 [Свойство DefinedSize](../../../ado/reference/ado-api/definedsize-property.md)
