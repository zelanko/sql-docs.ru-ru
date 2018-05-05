---
title: Свойство ActualSize (ADO) | Документы Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.component: ado
ms.technology: connectivity
ms.custom: ''
ms.date: 03/20/2018
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Field20::ActualSize
helpviewer_keywords:
- ActualSize property [ADO]
ms.assetid: 722803d0-cef5-4d4c-b79d-3f2f58052229
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 697202ef2c88d5fa33657c74713d884f2cbe916c
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="actualsize-property-ado"></a>Свойство ActualSize (ADO)
Указывает фактическую длину значения поля в байтах.  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Возвращает **длинные** значение.  
  
## <a name="remarks"></a>Замечания  
 Используйте **ActualSize** свойство для возврата фактическую длину [поле](../../../ado/reference/ado-api/field-object.md) значения объекта. Для всех полей **ActualSize** свойство доступно только для чтения. Если ADO не удается определить длину **поле** значения объекта **ActualSize** возвращает **adUnknown**.  
  
 **ActualSize** и [DefinedSize](../../../ado/reference/ado-api/definedsize-property.md) свойства отличаются, как показано в следующем примере. Объект **поле** объект с объявленным типом **adVarChar** и возвращает максимальную длину 50 символов **DefinedSize** значение 50, но  **ActualSize** он возвращает значение свойства — это количество данных, хранимых в поле для текущей записи. **Поля** с **DefinedSize** больше 255 байт рассматриваются как столбцы переменной длины.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Field](../../../ado/reference/ado-api/field-object.md)  
  
## <a name="see-also"></a>См. также  
 [ActualSize и DefinedSize-пример свойства (Visual Basic)](../../../ado/reference/ado-api/actualsize-and-definedsize-properties-example-vb.md)   
 [ActualSize и пример свойства DefinedSize (VC ++)](../../../ado/reference/ado-api/actualsize-and-definedsize-properties-example-vc.md)   
 [Свойство DefinedSize](../../../ado/reference/ado-api/definedsize-property.md)
