---
title: Свойство Type (ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Parameter::Type
- Field20::Type
helpviewer_keywords:
- Type property [ADO]
ms.assetid: 8a4c079f-9f4f-4545-801d-85983b8db71e
author: rothja
ms.author: jroth
ms.openlocfilehash: 7bfa47120814058adbc5c2e5f3650a79b2202afb
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/28/2020
ms.locfileid: "87243185"
---
# <a name="type-property-ado"></a>Свойство Type (ADO)
Указывает операционный тип или тип данных для [параметра](../../../ado/reference/ado-api/parameter-object.md), [поля](../../../ado/reference/ado-api/field-object.md)или объекта [Свойства](../../../ado/reference/ado-api/property-object-ado.md) .  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Задает или возвращает значение [дататипинум](../../../ado/reference/ado-api/datatypeenum.md) .  
  
## <a name="remarks"></a>Remarks  
 Для объектов **параметров** свойство **Type** доступно для чтения и записи. Для новых **объектов Field** , добавленных к коллекции [Fields](../../../ado/reference/ado-api/fields-collection-ado.md) [записи](../../../ado/reference/ado-api/record-object-ado.md), **тип** доступен только для чтения и записи только после того, как было указано свойство [value](../../../ado/reference/ado-api/value-property-ado.md) для **поля** и поставщик данных успешно добавил новое **поле** , вызвав метод [Update](../../../ado/reference/ado-api/update-method.md) коллекции **Fields** .  
  
 Для всех остальных объектов свойство **Type** доступно только для чтения.  
  
## <a name="applies-to"></a>Применение  

:::row:::
    :::column:::
        [Объект Field](../../../ado/reference/ado-api/field-object.md)  
    :::column-end:::
    :::column:::
        [Объект Parameter](../../../ado/reference/ado-api/parameter-object.md)  
    :::column-end:::
    :::column:::
        [Объект Property (ADO)](../../../ado/reference/ado-api/property-object-ado.md)  
    :::column-end:::
:::row-end:::

## <a name="see-also"></a>См. также  
 [Пример свойства Type (Field) (VB)](../../../ado/reference/ado-api/type-property-example-field-vb.md)   
 [Пример свойства Type (Property) (VC + +)](../../../ado/reference/ado-api/type-property-example-property-vc.md)   
 [Свойство RecordType (ADO)](../../../ado/reference/ado-api/recordtype-property-ado.md)   
 [Свойство Type (объект Stream ADO)](../../../ado/reference/ado-api/type-property-ado-stream.md)
