---
title: "Свойство ActualSize (ADO) | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- Field20::ActualSize
helpviewer_keywords:
- ActualSize property [ADO]
ms.assetid: 722803d0-cef5-4d4c-b79d-3f2f58052229
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 9d66019d7a71dd480f1a88a28fe94d72a176497c
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="actualsize-property-ado"></a>Свойство ActualSize (ADO)
Указывает фактическую длину поля. s значение в байтах.  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Возвращает **длинные** значение.  
  
## <a name="remarks"></a>Замечания  
 Используйте **ActualSize** свойство для возврата фактическую длину [поле](../../../ado/reference/ado-api/field-object.md) значения объекта. Для всех полей **ActualSize** свойство доступно только для чтения. Если ADO не удается определить длину **поле** значения объекта **ActualSize** возвращает **adUnknown**.  
  
 **ActualSize** и [DefinedSize](../../../ado/reference/ado-api/definedsize-property.md) свойства отличаются, как показано в следующем примере. Объект **поле** объект с объявленным типом **adVarChar** и возвращает максимальную длину 50 символов **DefinedSize** значение 50, но  **ActualSize** он возвращает значение свойства — это количество данных, хранимых в поле для текущей записи. **Поля** с **DefinedSize** больше 255 байт рассматриваются как столбцы переменной длины.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект field](../../../ado/reference/ado-api/field-object.md)  
  
## <a name="see-also"></a>См. также:  
 [ActualSize и DefinedSize-пример свойства (Visual Basic)](../../../ado/reference/ado-api/actualsize-and-definedsize-properties-example-vb.md)   
 [ActualSize и пример свойства DefinedSize (VC ++)](../../../ado/reference/ado-api/actualsize-and-definedsize-properties-example-vc.md)   
 [Свойство DefinedSize](../../../ado/reference/ado-api/definedsize-property.md)

