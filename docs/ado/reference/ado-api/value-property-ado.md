---
title: Значение свойства (ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 03/20/2018
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Field20::Value
- _Parameter::Value
helpviewer_keywords:
- Value property [ADO]
ms.assetid: 48919c74-86d4-462e-99b9-8854ceb8d683
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8c7e4d42bc58321c5b650df5e8e842290094fcf4
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63043699"
---
# <a name="value-property-ado"></a>Свойство Value (ADO)

Указывает значение, присваиваемое [поле](../../../ado/reference/ado-api/field-object.md), [параметр](../../../ado/reference/ado-api/parameter-object.md), или [свойство](../../../ado/reference/ado-api/property-object-ado.md) объекта.
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения

Возвращает или задает **Variant** значение, указывающее значение объекта. Значение по умолчанию зависит от [тип](../../../ado/reference/ado-api/type-property-ado.md) свойства.
  
## <a name="remarks"></a>Примечания

Используйте **значение** свойство задание или возврат данных из **поле** объектов, задание или возврат значения параметров с **параметр** объектов, или чтобы задание или возврат параметров свойств с **Свойство** объектов. Ли **значение** свойство доступно для чтения/записи или только для чтения зависит от множество факторов. См. Дополнительные сведения можно найти в разделах соответствующего объекта.

ADO разрешает задание и возвращает двоичные данные с **значение** свойства.
  
> [!NOTE]
> Для **параметр** объектов, операции чтения ADO **значение** только один раз свойства от поставщика. Если она содержит **параметр** которого **значение** свойство пусто, и создается [записей](../../../ado/reference/ado-api/recordset-object-ado.md) из команды, убедитесь, что после закрытия  **Набор записей** до извлечения **значение** свойства. В противном случае некоторые поставщики предоставляют **значение** свойство может быть пустым и не будет содержать правильное значение.
> 
> Для новых **поле** объекты, добавленные [поля](../../../ado/reference/ado-api/fields-collection-ado.md) коллекцию [записи](../../../ado/reference/ado-api/record-object-ado.md) объекта, **значение** свойство должно иметь значение перед любыми другими **поле** свойства могут быть указаны. Во-первых, конкретное значение для **значение** свойство, которое должна быть назначена и [обновление](../../../ado/reference/ado-api/update-method.md) на **поля** коллекцию с именем. Затем, другие свойства, такие как [тип](../../../ado/reference/ado-api/type-property-ado.md) или [атрибуты](../../../ado/reference/ado-api/attributes-property-ado.md) возможен.
  
## <a name="applies-to"></a>Объект применения
  
||||  
|-|-|-|  
|[Объект Field](../../../ado/reference/ado-api/field-object.md)|[Объект Parameter](../../../ado/reference/ado-api/parameter-object.md)|[Объект Property (ADO)](../../../ado/reference/ado-api/property-object-ado.md)|
  
## <a name="see-also"></a>См. также

[Пример свойства (Visual Basic) значение](../../../ado/reference/ado-api/value-property-example-vb.md)
[значение пример свойства (Visual C++)](../../../ado/reference/ado-api/value-property-example-vc.md) 
