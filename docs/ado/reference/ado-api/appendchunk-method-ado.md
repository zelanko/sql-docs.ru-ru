---
title: Метод AppendChunk (ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Parameter::AppendChunk
- Field20::AppendChunk
helpviewer_keywords:
- AppendChunk method [ADO]
ms.assetid: c648b5a8-d4f1-4d16-836e-3957feb03617
author: MightyPen
ms.author: genemi
ms.openlocfilehash: f9d575460daf0f801f6d6dd2e80b0c67f4886dc7
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "67920566"
---
# <a name="appendchunk-method-ado"></a>Метод AppendChunk (ADO)
Добавляет данные к большому текстовому или двоичному [полю](../../../ado/reference/ado-api/field-object.md)данных или к объекту [параметра](../../../ado/reference/ado-api/parameter-object.md) .  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
object.AppendChunk Data  
```  
  
#### <a name="parameters"></a>Параметры  
 *object*  
 Объект **поля** или **параметра** .  
  
 *Data*  
 **Значение типа Variant** , содержащее данные, добавляемые к объекту.  
  
## <a name="remarks"></a>Remarks  
 Используйте метод **AppendChunk** для **поля** или объекта **параметра** , чтобы заполнить его длинными двоичными или символьными данными. В ситуациях, когда память системы ограничена, можно использовать метод **AppendChunk** для обработки длинных значений в частях, а не в полном объеме.  
  
## <a name="field"></a>Поле  
 Если бит **адфлдлонг** в свойстве [Attributes](../../../ado/reference/ado-api/attributes-property-ado.md) объекта **field** имеет значение **true**, для этого поля можно использовать метод **AppendChunk** .  
  
 Первый вызов **AppendChunk** для объекта **field** записывает данные в поле, перезаписывая существующие данные. Последующие вызовы **AppendChunk** вызывают добавление к существующим данным. Если вы добавляете данные в одно поле, а затем задаете или считываете значение другого поля в текущей записи, то ADO предполагает, что добавление данных к первому полю завершено. При повторном вызове метода **AppendChunk** в первом поле ADO интерпретирует вызов как новую операцию **AppendChunk** и перезаписывает существующие данные. Доступ к полям других объектов [набора записей](../../../ado/reference/ado-api/recordset-object-ado.md) , которые не являются клонами первого объекта **набора записей** , не приведет к нарушению операций **AppendChunk** .  
  
 Если при вызове **AppendChunk** для объекта **поля** текущая запись отсутствует, возникает ошибка.  
  
> [!NOTE]
>  Метод **AppendChunk** не работает с объектами **полей** объекта [записи (ADO)](../../../ado/reference/ado-api/record-object-ado.md) . Она не выполняет никаких операций и выдает ошибку во время выполнения.  
  
## <a name="parameter"></a>Параметр  
 Если бит **адпарамлонг** в свойстве **Attributes** объекта **Parameter** имеет значение **true**, можно использовать метод **AppendChunk** для этого параметра.  
  
 Первый вызов **AppendChunk** для объекта **Parameter** записывает данные в параметр, перезаписывая существующие данные. Последующие вызовы **AppendChunk** для объекта **Parameter** добавляют существующие данные параметров. Вызов **AppendChunk** , который передает значение null, отбрасывает все данные параметров.  
  
## <a name="applies-to"></a>Применяется к  
  
|||  
|-|-|  
|[Объект Field](../../../ado/reference/ado-api/field-object.md)|[Объект Parameter](../../../ado/reference/ado-api/parameter-object.md)|  
  
## <a name="see-also"></a>См. также:  
 [Примеры методов AppendChunk и-блока (Visual Basic)](../../../ado/reference/ado-api/appendchunk-and-getchunk-methods-example-vb.md)   
 [Примеры методов AppendChunk и-блока (Visual c++)](../../../ado/reference/ado-api/appendchunk-and-getchunk-methods-example-vc.md)   
 [Свойство Attributes (ADO)](../../../ado/reference/ado-api/attributes-property-ado.md)   
 [Метод GetChunk (ADO)](../../../ado/reference/ado-api/getchunk-method-ado.md)
