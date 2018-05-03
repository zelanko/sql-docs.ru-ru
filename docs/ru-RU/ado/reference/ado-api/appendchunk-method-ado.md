---
title: Метод AppendChunk (ADO) | Документы Microsoft
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Parameter::AppendChunk
- Field20::AppendChunk
helpviewer_keywords:
- AppendChunk method [ADO]
ms.assetid: c648b5a8-d4f1-4d16-836e-3957feb03617
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: cd71f62bacdb56385c79eb8dc09f336f3f026aca
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="appendchunk-method-ado"></a>Метод AppendChunk (ADO)
Добавляет данные большие текстовые или двоичные данные [поле](../../../ado/reference/ado-api/field-object.md), или к [параметр](../../../ado/reference/ado-api/parameter-object.md) объекта.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
object.AppendChunk Data  
```  
  
#### <a name="parameters"></a>Параметры  
 *объект*  
 Объект **поле** или **параметр** объекта.  
  
 *Данные*  
 Объект **Variant** , содержащий данные для добавления в объект.  
  
## <a name="remarks"></a>Замечания  
 Используйте **AppendChunk** метод **поле** или **параметр** объекта для наполнения долго двоичных или символьных данных. В ситуациях, где ограничена системной памяти, можно использовать **AppendChunk** метод для обработки длинные значения в части, а не полностью.  
  
## <a name="field"></a>Поле  
 Если **adFldLong** бит в [атрибуты](../../../ado/reference/ado-api/attributes-property-ado.md) свойство **поле** , присваивается значение **true**, можно использовать  **AppendChunk** метода для этого поля.  
  
 Первый **AppendChunk** вызвать **поле** объекта записывает данные в поле, перезаписывая все существующие данные. Последующие **AppendChunk** вызывает добавление к существующим данным. Если данные добавляются к одному полю, а затем задать или прочитать значение другого поля в текущей записи, ADO предполагается, что вы по завершении добавления данных с первым полем. При вызове метода **AppendChunk** метод на первое поле, ADO интерпретирует вызов как новый **AppendChunk** операции и перезаписывает существующие данные. Доступ к полям в других [записей](../../../ado/reference/ado-api/recordset-object-ado.md) объектов, не являющихся клоны первого **записей** объекта не приведет к нарушению **AppendChunk** операций.  
  
 Если отсутствует запись текущей, при вызове **AppendChunk** на **поле** объекта, возникает ошибка.  
  
> [!NOTE]
>  **AppendChunk** метод не выполняет операций **поле** объектов [записи Objects (ADO)](../../../ado/reference/ado-api/record-object-ado.md) объекта. Он не осуществляет никаких операций и приведет к ошибке во время выполнения.  
  
## <a name="parameter"></a>Параметр  
 Если **adParamLong** бит в **атрибуты** свойство **параметр** , присваивается значение **true**, можно использовать  **AppendChunk** метода для этого параметра.  
  
 Первый **AppendChunk** вызвать **параметр** объекта записывает данные в параметр, перезаписывая все существующие данные. Последующие **AppendChunk** вызывает **параметр** добавить объект к существующим данным параметром. **AppendChunk** отменяет вызов, который передает значение null, все данные параметра.  
  
## <a name="applies-to"></a>Объект применения  
  
|||  
|-|-|  
|[Объект Field](../../../ado/reference/ado-api/field-object.md)|[Объект Parameter](../../../ado/reference/ado-api/parameter-object.md)|  
  
## <a name="see-also"></a>См. также  
 [AppendChunk и пример GetChunk методы (Visual Basic)](../../../ado/reference/ado-api/appendchunk-and-getchunk-methods-example-vb.md)   
 [AppendChunk и пример методы GetChunk (VC ++)](../../../ado/reference/ado-api/appendchunk-and-getchunk-methods-example-vc.md)   
 [Свойства атрибутов (ADO)](../../../ado/reference/ado-api/attributes-property-ado.md)   
 [Метод GetChunk (ADO)](../../../ado/reference/ado-api/getchunk-method-ado.md)
