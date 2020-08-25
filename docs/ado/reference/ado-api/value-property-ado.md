---
description: Свойство Value (ADO)
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
ms.openlocfilehash: 1ab44fcbb8409cd866167d4fb58bebc1de906274
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2020
ms.locfileid: "88776974"
---
# <a name="value-property-ado"></a>Свойство Value (ADO)

Указывает значение, присваиваемое [полю](./field-object.md), [параметру](./parameter-object.md)или объекту [Свойства](./property-object-ado.md) .
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения

Задает или возвращает значение **типа Variant** , указывающее значение объекта. Значение по умолчанию зависит от свойства [Type](./type-property-ado.md) .
  
## <a name="remarks"></a>Remarks

Свойство **value** используется для задания или возврата данных из объектов **полей** , для задания или возврата значений параметров с помощью объектов **параметров** , а также для установки или возврата параметров свойств с объектами **свойств** . Является ли свойство **value** доступно для чтения и записи или только для чтения, зависит от множества факторов. Дополнительные сведения см. в разделах, посвященных соответствующим объектам.

ADO позволяет задавать и возвращать длинные двоичные данные со свойством **value** .
  
> [!NOTE]
> Для объектов **параметров** ADO считывает свойство **value** только один раз от поставщика. Если команда содержит **параметр** , свойство **value** которого пусто, и вы создаете [набор записей](./recordset-object-ado.md) из команды, убедитесь, что сначала закрываете **набор записей** , прежде чем получать свойство **value** . В противном случае для некоторых поставщиков свойство **value** может быть пустым и не будет содержать правильное значение.
> 
> Для новых объектов **field** , которые были добавлены к коллекции [Fields](./fields-collection-ado.md) объекта [Record](./record-object-ado.md) , необходимо задать свойство **value** , прежде чем можно будет указать другие свойства **поля** . Во-первых, конкретное значение свойства **value** должно быть назначено и [Обновлено](./update-method.md) в коллекции **Fields** с именем. Затем можно получить доступ к другим свойствам, например к [типу](./type-property-ado.md) или [атрибутам](./attributes-property-ado.md) .
  
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

[Пример свойства Value (Visual Basic)](./value-property-example-vb.md) 
 [Пример свойства Value (](./value-property-example-vc.md) Visual c++)