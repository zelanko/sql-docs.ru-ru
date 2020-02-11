---
title: DefinedSize, свойство | Документация Майкрософт
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
ms.openlocfilehash: 4bfb0db701801f1853009594b9d6d24aeb41c629
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67933215"
---
# <a name="definedsize-property"></a>Свойство DefinedSize
Указывает емкость данных для объекта [поля](../../../ado/reference/ado-api/field-object.md) .  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение типа **Long** , отражающее заданный размер поля, который зависит от типов данных объекта Field. Дополнительные сведения см. в разделе [тип](../../../ado/reference/ado-api/type-property-ado.md) . Для поля, использующего тип данных фиксированной длины, возвращаемое значение — это размер типа данных в байтах. Для поля, использующего тип данных переменной длины, это одно из следующих:  
  
1.  Максимальная длина поля в символах (для **адварчар** и **адварвчар**) или в байтах (для **адварбинари**и **адварнумерик**), если поле имеет определенную длину. Например, поле **адварчар (5)** имеет максимальную длину 5.  
  
2.  Максимальная длина типа данных в символах (для **адчар** и **адвчар**) или в байтах (для **адбинари** и **аднумерик**), если поле не имеет определенной длины.  
  
3.  ~ 0 (побитовое значение не равно 0; все биты установлены в 1), если ни поле, ни тип данных не имеют определенной максимальной длины.  
  
4.  Для типов данных, длина которых не превышает длину, для этого параметра задано значение ~ 0 (битовая, а не 0, все биты установлены в 1).  
  
## <a name="remarks"></a>Remarks  
 Используйте свойство **DefinedSize** , чтобы определить емкость данных для объекта **поля** .  
  
 Свойства **DefinedSize** и [ActualSize](../../../ado/reference/ado-api/actualsize-property-ado.md) различаются. Например, рассмотрим объект **field** с объявленным типом **адварчар** и значением свойства **DefinedSize** 50, содержащим один символ. Возвращаемое значение свойства **ActualSize** — это длина в байтах одного символа.  
  
## <a name="applies-to"></a>Применяется к  
 [Объект Field](../../../ado/reference/ado-api/field-object.md)  
  
## <a name="see-also"></a>См. также:  
 [Примеры свойств ActualSize и DefinedSize (Visual Basic)](../../../ado/reference/ado-api/actualsize-and-definedsize-properties-example-vb.md)   
 [Пример свойств ActualSize и DefinedSize (Visual c++)](../../../ado/reference/ado-api/actualsize-and-definedsize-properties-example-vc.md)   
 [Свойство ActualSize (ADO)](../../../ado/reference/ado-api/actualsize-property-ado.md)
