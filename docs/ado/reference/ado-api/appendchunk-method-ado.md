---
description: Метод AppendChunk (ADO)
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 0df71772820d5871c32e40827400b8cdd40db99d
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2020
ms.locfileid: "88776483"
---
# <a name="appendchunk-method-ado"></a>Метод AppendChunk (ADO)
Добавляет данные к большому текстовому или двоичному [полю](./field-object.md)данных или к объекту [параметра](./parameter-object.md) .  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
object.AppendChunk Data  
```  
  
#### <a name="parameters"></a>Параметры  
 *object*  
 Объект **поля** или **параметра** .  
  
 *Данные*  
 **Значение типа Variant** , содержащее данные, добавляемые к объекту.  
  
## <a name="remarks"></a>Remarks  
 Используйте метод **AppendChunk** для **поля** или объекта **параметра** , чтобы заполнить его длинными двоичными или символьными данными. В ситуациях, когда память системы ограничена, можно использовать метод **AppendChunk** для обработки длинных значений в частях, а не в полном объеме.  
  
## <a name="field"></a>Поле  
 Если бит **адфлдлонг** в свойстве [Attributes](./attributes-property-ado.md) объекта **field** имеет значение **true**, для этого поля можно использовать метод **AppendChunk** .  
  
 Первый вызов **AppendChunk** для объекта **field** записывает данные в поле, перезаписывая существующие данные. Последующие вызовы **AppendChunk** вызывают добавление к существующим данным. Если вы добавляете данные в одно поле, а затем задаете или считываете значение другого поля в текущей записи, то ADO предполагает, что добавление данных к первому полю завершено. При повторном вызове метода **AppendChunk** в первом поле ADO интерпретирует вызов как новую операцию **AppendChunk** и перезаписывает существующие данные. Доступ к полям других объектов [набора записей](./recordset-object-ado.md) , которые не являются клонами первого объекта **набора записей** , не приведет к нарушению операций **AppendChunk** .  
  
 Если при вызове **AppendChunk** для объекта **поля** текущая запись отсутствует, возникает ошибка.  
  
> [!NOTE]
>  Метод **AppendChunk** не работает с объектами **полей** объекта [записи (ADO)](./record-object-ado.md) . Она не выполняет никаких операций и выдает ошибку во время выполнения.  
  
## <a name="parameter"></a>Параметр  
 Если бит **адпарамлонг** в свойстве **Attributes** объекта **Parameter** имеет значение **true**, можно использовать метод **AppendChunk** для этого параметра.  
  
 Первый вызов **AppendChunk** для объекта **Parameter** записывает данные в параметр, перезаписывая существующие данные. Последующие вызовы **AppendChunk** для объекта **Parameter** добавляют существующие данные параметров. Вызов **AppendChunk** , который передает значение null, отбрасывает все данные параметров.  
  
## <a name="applies-to"></a>Применение  

:::row:::
    :::column:::
        [Объект Field](./field-object.md)  
    :::column-end:::
    :::column:::
        [Объект Parameter](./parameter-object.md)  
    :::column-end:::
:::row-end:::

## <a name="see-also"></a>См. также  
 [Примеры методов AppendChunk и-блока (Visual Basic)](./appendchunk-and-getchunk-methods-example-vb.md)   
 [Примеры методов AppendChunk и-блока (Visual c++)](./appendchunk-and-getchunk-methods-example-vc.md)   
 [Свойство Attributes (ADO)](./attributes-property-ado.md)   
 [Метод GetChunk (ADO)](./getchunk-method-ado.md)