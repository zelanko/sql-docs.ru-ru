---
title: Свойство Value (ADO) | Документация Майкрософт
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 6648fcabe8890ef653558636738735a4f5e4012f
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2020
ms.locfileid: "82759450"
---
# <a name="value-property-ado"></a>Свойство Value (ADO)

Указывает значение, присваиваемое [полю](../../../ado/reference/ado-api/field-object.md), [параметру](../../../ado/reference/ado-api/parameter-object.md)или объекту [Свойства](../../../ado/reference/ado-api/property-object-ado.md) .
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения

Задает или возвращает значение **типа Variant** , указывающее значение объекта. Значение по умолчанию зависит от свойства [Type](../../../ado/reference/ado-api/type-property-ado.md) .
  
## <a name="remarks"></a>Remarks

Свойство **value** используется для задания или возврата данных из объектов **полей** , для задания или возврата значений параметров с помощью объектов **параметров** , а также для установки или возврата параметров свойств с объектами **свойств** . Является ли свойство **value** доступно для чтения и записи или только для чтения, зависит от множества факторов. Дополнительные сведения см. в разделах, посвященных соответствующим объектам.

ADO позволяет задавать и возвращать длинные двоичные данные со свойством **value** .
  
> [!NOTE]
> Для объектов **параметров** ADO считывает свойство **value** только один раз от поставщика. Если команда содержит **параметр** , свойство **value** которого пусто, и вы создаете [набор записей](../../../ado/reference/ado-api/recordset-object-ado.md) из команды, убедитесь, что сначала закрываете **набор записей** , прежде чем получать свойство **value** . В противном случае для некоторых поставщиков свойство **value** может быть пустым и не будет содержать правильное значение.
> 
> Для новых объектов **field** , которые были добавлены к коллекции [Fields](../../../ado/reference/ado-api/fields-collection-ado.md) объекта [Record](../../../ado/reference/ado-api/record-object-ado.md) , необходимо задать свойство **value** , прежде чем можно будет указать другие свойства **поля** . Во-первых, конкретное значение свойства **value** должно быть назначено и [Обновлено](../../../ado/reference/ado-api/update-method.md) в коллекции **Fields** с именем. Затем можно получить доступ к другим свойствам, например к [типу](../../../ado/reference/ado-api/type-property-ado.md) или [атрибутам](../../../ado/reference/ado-api/attributes-property-ado.md) .
  
## <a name="applies-to"></a>Применяется к
  
||||  
|-|-|-|  
|[Объект Field](../../../ado/reference/ado-api/field-object.md)|[Объект Parameter](../../../ado/reference/ado-api/parameter-object.md)|[Объект Property (ADO)](../../../ado/reference/ado-api/property-object-ado.md)|
  
## <a name="see-also"></a>См. также

[Пример свойства Value (Visual Basic)](../../../ado/reference/ado-api/value-property-example-vb.md) 
 [Пример свойства Value (](../../../ado/reference/ado-api/value-property-example-vc.md) Visual c++) 
