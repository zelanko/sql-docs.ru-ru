---
description: Свойство Precision (ADO)
title: Свойство Precision (ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Parameter::Precision
- Field20::Precision
helpviewer_keywords:
- Precision property [ADO]
ms.assetid: 1fa38e78-6b5b-414d-ba0a-3dd26b29b766
author: rothja
ms.author: jroth
ms.openlocfilehash: 59a42a7f577ae8f4712e679853d53939fd6f6ed1
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2020
ms.locfileid: "88773143"
---
# <a name="precision-property-ado"></a>Свойство Precision (ADO)
Указывает степень точности для числовых значений в объекте [параметра](./parameter-object.md) или для числовых объектов [полей](./field-object.md) .  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Задает или возвращает значение **типа Byte** , указывающее максимальное количество цифр, используемых для представления значений.  
  
## <a name="remarks"></a>Remarks  
 Используйте свойство **Precision** , чтобы определить максимальное количество цифр, используемых для представления значений числового **параметра** или объекта **поля** .  
  
 Значение доступно для чтения и записи в объекте **Parameter** .  
  
 Для объекта **поля** **точность** обычно доступна только для чтения. Однако для новых объектов **field** , добавленных к коллекции [Fields](./fields-collection-ado.md) [записи](./record-object-ado.md), **точность** доступна только для чтения и записи только после того, как было указано свойство [value](./value-property-ado.md) для **поля** и поставщик данных успешно добавил новое **поле** , вызвав метод [Update](./update-method.md) коллекции **Fields** .  
  
## <a name="applies-to"></a>Применение  

:::row:::
    :::column:::
        [Объект Field](./field-object.md)  
    :::column-end:::
    :::column:::
        [Объект Parameter](./parameter-object.md)  
    :::column-end:::
:::row-end:::

## <a name="see-also"></a>См. также  
 [Пример свойств NumericScale и Precision (Visual Basic)](./numericscale-and-precision-properties-example-vb.md)   
 [Пример свойств NumericScale и Precision (Visual c++)](./numericscale-and-precision-properties-example-vc.md)   
 [Свойство NumericScale (ADO)](./numericscale-property-ado.md)