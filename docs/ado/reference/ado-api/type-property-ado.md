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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 0ee1058299becb4a7a4234debc097516cb02dd41
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67937867"
---
# <a name="type-property-ado"></a>Свойство Type (ADO)
Указывает операционный тип или тип данных для [параметра](../../../ado/reference/ado-api/parameter-object.md), [поля](../../../ado/reference/ado-api/field-object.md)или объекта [Свойства](../../../ado/reference/ado-api/property-object-ado.md) .  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Задает или возвращает значение [дататипинум](../../../ado/reference/ado-api/datatypeenum.md) .  
  
## <a name="remarks"></a>Remarks  
 Для объектов **параметров** свойство **Type** доступно для чтения и записи. Для новых **объектов Field** , добавленных к коллекции [Fields](../../../ado/reference/ado-api/fields-collection-ado.md) [записи](../../../ado/reference/ado-api/record-object-ado.md), **тип** доступен только для чтения и записи только после того, как было указано свойство [value](../../../ado/reference/ado-api/value-property-ado.md) для **поля** и поставщик данных успешно добавил новое **поле** , вызвав метод [Update](../../../ado/reference/ado-api/update-method.md) коллекции **Fields** .  
  
 Для всех остальных объектов свойство **Type** доступно только для чтения.  
  
## <a name="applies-to"></a>Применяется к  
  
||||  
|-|-|-|  
|[Объект Field](../../../ado/reference/ado-api/field-object.md)|[Объект Parameter](../../../ado/reference/ado-api/parameter-object.md)|[Объект Property (ADO)](../../../ado/reference/ado-api/property-object-ado.md)|  
  
## <a name="see-also"></a>См. также:  
 [Пример свойства Type (Field) (VB)](../../../ado/reference/ado-api/type-property-example-field-vb.md)   
 [Пример свойства Type (Property) (VC + +)](../../../ado/reference/ado-api/type-property-example-property-vc.md)   
 [Свойство RecordType (ADO)](../../../ado/reference/ado-api/recordtype-property-ado.md)   
 [Свойство Type (объект Stream ADO)](../../../ado/reference/ado-api/type-property-ado-stream.md)
