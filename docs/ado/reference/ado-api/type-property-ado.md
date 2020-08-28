---
description: Свойство Type (ADO)
title: Свойство Type (ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
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
ms.openlocfilehash: 9f4dcfd3c22363ab4950e03844647f990a34f4d5
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2020
ms.locfileid: "88988315"
---
# <a name="type-property-ado"></a>Свойство Type (ADO)
Указывает операционный тип или тип данных для [параметра](./parameter-object.md), [поля](./field-object.md)или объекта [Свойства](./property-object-ado.md) .  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Задает или возвращает значение [дататипинум](./datatypeenum.md) .  
  
## <a name="remarks"></a>Remarks  
 Для объектов **параметров** свойство **Type** доступно для чтения и записи. Для новых **объектов Field** , добавленных к коллекции [Fields](./fields-collection-ado.md) [записи](./record-object-ado.md), **тип** доступен только для чтения и записи только после того, как было указано свойство [value](./value-property-ado.md) для **поля** и поставщик данных успешно добавил новое **поле** , вызвав метод [Update](./update-method.md) коллекции **Fields** .  
  
 Для всех остальных объектов свойство **Type** доступно только для чтения.  
  
## <a name="applies-to"></a>Применение  

:::row:::
    :::column:::
        [Объект Field](./field-object.md)  
    :::column-end:::
    :::column:::
        [Объект Parameter](./parameter-object.md)  
    :::column-end:::
    :::column:::
        [Объект Property (ADO)](./property-object-ado.md)  
    :::column-end:::
:::row-end:::

## <a name="see-also"></a>См. также  
 [Пример свойства Type (Field) (VB)](./type-property-example-field-vb.md)   
 [Пример свойства Type (Property) (VC + +)](./type-property-example-property-vc.md)   
 [Свойство RecordType (ADO)](./recordtype-property-ado.md)   
 [Свойство Type (объект Stream ADO)](./type-property-ado-stream.md)