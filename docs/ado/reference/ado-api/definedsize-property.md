---
title: Свойство DefinedSize | Документы Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Field20::DefinedSize
helpviewer_keywords:
- DefinedSize property [ADO]
ms.assetid: 3ee27314-a305-4fbc-8433-9ee9a909afd6
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0b060258acc6e267ff9e518aa4591bdfd0eef69e
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/11/2018
ms.locfileid: "35277563"
---
# <a name="definedsize-property"></a>Свойство DefinedSize
Показывает объем данных [поле](../../../ado/reference/ado-api/field-object.md) объекта.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает **длинные** значение, отражающее определенный размер поля, которое зависит от типа данных поля объекта см. в разделе [типа](../../../ado/reference/ado-api/type-property-ado.md) для получения дополнительной информации. Для поля, которое использует тип данных фиксированной длины возвращаемое значение имеет размер типа данных в байтах. Для поля, которое использует тип данных переменной длины это одна из следующих:  
  
1.  Максимальная длина в символах поля (для **adVarChar** и **adVarWChar**) или в байтах (для **adVarBinary**, и **adVarNumeric**), если поле имеет определенной длины. Например **adVarChar(5)** поле не должно превышать 5.  
  
2.  Максимальная длина типа данных в символах (для **adChar** и **adWChar**) или в байтах (для **adBinary** и **adNumeric**) Если поле не имеет определенной длины.  
  
3.  ~ 0 (Побитовый оператор, значение не 0; все биты устанавливаются в 1) Если определена максимальная длина поля, ни тип данных.  
  
4.  Для типов данных, которые имеют длину, он равен ~ 0 (Побитовый оператор, значение не 0; все биты устанавливаются в 1).  
  
## <a name="remarks"></a>Примечания  
 Используйте **DefinedSize** свойства, чтобы определить объем данных **поле** объекта.  
  
 **DefinedSize** и [ActualSize](../../../ado/reference/ado-api/actualsize-property-ado.md) свойства отличаются. Например, рассмотрим **поле** объект с объявленным типом **adVarChar** и **DefinedSize** значение свойства 50, содержащей один символ. **ActualSize** он возвращает значение свойства — это длина в байтах один символ.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Field](../../../ado/reference/ado-api/field-object.md)  
  
## <a name="see-also"></a>См. также  
 [ActualSize и DefinedSize-пример свойства (Visual Basic)](../../../ado/reference/ado-api/actualsize-and-definedsize-properties-example-vb.md)   
 [ActualSize и пример свойства DefinedSize (VC ++)](../../../ado/reference/ado-api/actualsize-and-definedsize-properties-example-vc.md)   
 [Свойство ActualSize (ADO)](../../../ado/reference/ado-api/actualsize-property-ado.md)
