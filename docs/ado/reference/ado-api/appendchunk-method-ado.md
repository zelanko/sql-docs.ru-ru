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
manager: jroth
ms.openlocfilehash: e4b7b7a97af9059e944d2d2d9e7d19afedf4234d
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66696413"
---
# <a name="appendchunk-method-ado"></a>Метод AppendChunk (ADO)
Добавляет данные в большие текстовые или двоичные данные [поле](../../../ado/reference/ado-api/field-object.md), или к [параметр](../../../ado/reference/ado-api/parameter-object.md) объекта.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
object.AppendChunk Data  
```  
  
#### <a name="parameters"></a>Параметры  
 *object*  
 Объект **поле** или **параметр** объекта.  
  
 *Data*  
 Объект **Variant** , содержащий данные для добавления к объекту.  
  
## <a name="remarks"></a>Примечания  
 Используйте **AppendChunk** метод **поле** или **параметр** объект, который заполняется долго двоичных или символьных данных. В ситуациях, где ограничена системной памяти, можно использовать **AppendChunk** метод для обработки длинных значений в части, а не полностью.  
  
## <a name="field"></a>Поле  
 Если **adFldLong** бит в [атрибуты](../../../ado/reference/ado-api/attributes-property-ado.md) свойство **поле** присваивается **true**, можно использовать  **AppendChunk** метод для этого поля.  
  
 Первый **AppendChunk** вызвать **поле** объект записывает данные в поле, перезаписывая все существующие данные. Последующие **AppendChunk** вызовов добавления к существующим данным. При добавлении данных в одном поле, а затем задать или прочитать значение другого поля в текущей записи, ADO предполагается, что вы закончите, добавление данных в первое поле. При вызове метода **AppendChunk** метод на первое поле, ADO интерпретирует как новый вызов **AppendChunk** операции и перезаписывает существующие данные. Доступ к полям в других [записей](../../../ado/reference/ado-api/recordset-object-ado.md) объекты, не являющиеся клонов первого **набор записей** объекта не приведет к нарушению **AppendChunk** операций.  
  
 Если имеется текущая запись, при вызове **AppendChunk** на **поле** объекта, возникает ошибка.  
  
> [!NOTE]
>  **AppendChunk** метод не работает на **поле** объектов [записи объекта (ADO)](../../../ado/reference/ado-api/record-object-ado.md) объекта. Он не осуществляет никаких операций и приведет к ошибке времени выполнения.  
  
## <a name="parameter"></a>Параметр  
 Если **adParamLong** бит в **атрибуты** свойство **параметр** присваивается **true**, можно использовать  **AppendChunk** метод для этого параметра.  
  
 Первый **AppendChunk** вызвать **параметр** объект записывает данные в параметре, перезаписывая все существующие данные. Последующие **AppendChunk** вызывает **параметр** добавления объекта к существующим данным параметром. **AppendChunk** отклоняет вызов, который передает значение null, все данные параметра.  
  
## <a name="applies-to"></a>Объект применения  
  
|||  
|-|-|  
|[Объект Field](../../../ado/reference/ado-api/field-object.md)|[Объект Parameter](../../../ado/reference/ado-api/parameter-object.md)|  
  
## <a name="see-also"></a>См. также  
 [Примеры AppendChunk и GetChunk методы (Visual Basic)](../../../ado/reference/ado-api/appendchunk-and-getchunk-methods-example-vb.md)   
 [Примеры AppendChunk и GetChunk методы (Visual C++)](../../../ado/reference/ado-api/appendchunk-and-getchunk-methods-example-vc.md)   
 [Свойство Attributes (ADO)](../../../ado/reference/ado-api/attributes-property-ado.md)   
 [Метод GetChunk (ADO)](../../../ado/reference/ado-api/getchunk-method-ado.md)
