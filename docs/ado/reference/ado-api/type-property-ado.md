---
title: Введите свойство (ADO) | Документация Майкрософт
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
manager: craigg
ms.openlocfilehash: 02c5b9193b89c131095ccfec6ef185d5ff39f4d5
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62910853"
---
# <a name="type-property-ado"></a>Свойство Type (ADO)
Тип рабочей типа или данных [параметр](../../../ado/reference/ado-api/parameter-object.md), [поле](../../../ado/reference/ado-api/field-object.md), или [свойство](../../../ado/reference/ado-api/property-object-ado.md) объекта.  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Возвращает или задает [DataTypeEnum](../../../ado/reference/ado-api/datatypeenum.md) значение.  
  
## <a name="remarks"></a>Примечания  
 Для **параметр** объектов, **тип** свойство доступно для чтения/записи. Для новых **поле** объекты, добавленные [поля](../../../ado/reference/ado-api/fields-collection-ado.md) коллекцию [записи](../../../ado/reference/ado-api/record-object-ado.md), **тип** доступно для чтения и записи только после [ Значение](../../../ado/reference/ado-api/value-property-ado.md) свойство для **поле** была определена и успешно добавил новый поставщик данных **поле** путем вызова [обновить](../../../ado/reference/ado-api/update-method.md)метод **поля** коллекции.  
  
 Для всех остальных объектов **тип** свойство доступно только для чтения.  
  
## <a name="applies-to"></a>Объект применения  
  
||||  
|-|-|-|  
|[Объект Field](../../../ado/reference/ado-api/field-object.md)|[Объект Parameter](../../../ado/reference/ado-api/parameter-object.md)|[Объект Property (ADO)](../../../ado/reference/ado-api/property-object-ado.md)|  
  
## <a name="see-also"></a>См. также  
 [Пример свойства Type (объект Field) (Visual Basic)](../../../ado/reference/ado-api/type-property-example-field-vb.md)   
 [Пример свойства Type (свойство) (Visual C++)](../../../ado/reference/ado-api/type-property-example-property-vc.md)   
 [Свойство RecordType (ADO)](../../../ado/reference/ado-api/recordtype-property-ado.md)   
 [Свойство Type (объект Stream ADO)](../../../ado/reference/ado-api/type-property-ado-stream.md)
