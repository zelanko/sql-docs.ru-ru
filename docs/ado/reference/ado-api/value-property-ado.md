---
title: Значение свойства (ADO) | Документы Microsoft
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 03/20/2018
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Field20::Value
- _Parameter::Value
helpviewer_keywords:
- Value property [ADO]
ms.assetid: 48919c74-86d4-462e-99b9-8854ceb8d683
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: fd1f9ce0517bd2dcec98917d82818a5390dd60b6
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2018
---
# <a name="value-property-ado"></a>Значение свойства (ADO)

Указывает значение, присваиваемое [поле](../../../ado/reference/ado-api/field-object.md), [параметр](../../../ado/reference/ado-api/parameter-object.md), или [свойство](../../../ado/reference/ado-api/property-object-ado.md) объекта.
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения

Возвращает или задает **Variant** значение, указывающее значение объекта. Значение по умолчанию зависит от [тип](../../../ado/reference/ado-api/type-property-ado.md) свойства.
  
## <a name="remarks"></a>Замечания

Используйте **значение** свойство, чтобы задать или получить данные из **поле** объектов задание или возврат значения параметров с **параметр** объекты, или на задание или возврат значения свойств с **Свойство** объектов. Ли **значение** свойство доступно для чтения/записи или только для чтения, зависит от множество факторов. см. Дополнительные сведения можно найти в разделах соответствующего объекта.

ADO позволяет задавать и возвращает двоичные данные с **значение** свойства.
  
> [!NOTE]
> Для **параметр** объектов, операции чтения ADO **значение** свойство только один раз от поставщика. Если она содержит **параметр** которого **значение** свойство является пустым, и вы создаете [записей](../../../ado/reference/ado-api/recordset-object-ado.md) из команды, убедитесь, что после закрытия  **Набор записей** перед получением **значение** свойства. В противном случае некоторые поставщики предоставляют **значение** свойство может быть пустым и не будет содержать правильное значение.
> 
> Для новых **поле** объектов, добавленных в [поля](../../../ado/reference/ado-api/fields-collection-ado.md) коллекцию [запись](../../../ado/reference/ado-api/record-object-ado.md) объекта, **значение** свойство должно быть задано перед любыми другими **поле** можно задать свойства. Во-первых, конкретное значение для **значение** свойство должна быть назначена и [обновление](../../../ado/reference/ado-api/update-method.md) на **поля** коллекцию с именем. После этого другие свойства, такие как [тип](../../../ado/reference/ado-api/type-property-ado.md) или [атрибуты](../../../ado/reference/ado-api/attributes-property-ado.md) доступны.
  
## <a name="applies-to"></a>Объект применения
  
||||  
|-|-|-|  
|[Объект Field](../../../ado/reference/ado-api/field-object.md)|[Объект Parameter](../../../ado/reference/ado-api/parameter-object.md)|[Объект Property (ADO)](../../../ado/reference/ado-api/property-object-ado.md)|
  
## <a name="see-also"></a>См. также

[Пример свойства (Visual Basic) значение](../../../ado/reference/ado-api/value-property-example-vb.md)
[значение примера свойства (VC ++)](../../../ado/reference/ado-api/value-property-example-vc.md) 
