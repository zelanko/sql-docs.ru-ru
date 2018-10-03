---
title: Пример свойства DefinedSize | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Field20::DefinedSize
helpviewer_keywords:
- DefinedSize property [ADO]
ms.assetid: 3ee27314-a305-4fbc-8433-9ee9a909afd6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4267776593637a01aef38a218f7272261fd1d448
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47789192"
---
# <a name="definedsize-property"></a>Свойство DefinedSize
Показывает объем данных [поле](../../../ado/reference/ado-api/field-object.md) объекта.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает **Long** значение, которое отражает размер, определенный для поля, которое зависит от типа данных поля объекта; см. в разделе [тип](../../../ado/reference/ado-api/type-property-ado.md) Дополнительные сведения. Для поля, которое использует тип данных фиксированной длины возвращается размер типа данных в байтах. Для поля, которое использует тип данных переменной длины это одно из следующих:  
  
1.  Максимальная длина поля в символах (для **adVarChar** и **adVarWChar**) или в байтах (для **adVarBinary**, и **adVarNumeric**) Если поле имеет определенной длины. Например **adVarChar(5)** поле имеет длину не более 5.  
  
2.  Максимальная длина типа данных в символах (для **adChar** и **adWChar**) или в байтах (для **adBinary** и **adNumeric**) Если поле не имеет определенной длины.  
  
3.  ~ 0 (побитовое, значение 0; все биты установлены в значение 1) Если определена максимальная длина поля, ни тип данных.  
  
4.  Для типов данных, которые не имеют длину, это имеет значение ~ 0 (побитовое, значение 0; все биты установлены в значение 1).  
  
## <a name="remarks"></a>Примечания  
 Используйте **DefinedSize** свойства, чтобы определить объем данных **поле** объекта.  
  
 **DefinedSize** и [ActualSize](../../../ado/reference/ado-api/actualsize-property-ado.md) свойства отличаются. Например, рассмотрим **поле** объект с объявленным типом **adVarChar** и **DefinedSize** значение 50, содержащей один символ. **ActualSize** он возвращает значение свойства имеет длину в байтах один символ.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Field](../../../ado/reference/ado-api/field-object.md)  
  
## <a name="see-also"></a>См. также  
 [Примеры ActualSize и Definedsize свойства (Visual Basic)](../../../ado/reference/ado-api/actualsize-and-definedsize-properties-example-vb.md)   
 [Примеры ActualSize и Definedsize свойства (Visual C++)](../../../ado/reference/ado-api/actualsize-and-definedsize-properties-example-vc.md)   
 [Свойство ActualSize (ADO)](../../../ado/reference/ado-api/actualsize-property-ado.md)
