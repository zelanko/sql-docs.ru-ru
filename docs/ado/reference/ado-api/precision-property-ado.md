---
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 26da0367e494bd74253b904393a2dad62308a608
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67931630"
---
# <a name="precision-property-ado"></a>Свойство Precision (ADO)
Указывает степень точности для числовых значений в объекте [параметра](../../../ado/reference/ado-api/parameter-object.md) или для числовых объектов [полей](../../../ado/reference/ado-api/field-object.md) .  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Задает или возвращает значение **типа Byte** , указывающее максимальное количество цифр, используемых для представления значений.  
  
## <a name="remarks"></a>Remarks  
 Используйте свойство **Precision** , чтобы определить максимальное количество цифр, используемых для представления значений числового **параметра** или объекта **поля** .  
  
 Значение доступно для чтения и записи в объекте **Parameter** .  
  
 Для объекта **поля** **точность** обычно доступна только для чтения. Однако для новых объектов **field** , добавленных к коллекции [Fields](../../../ado/reference/ado-api/fields-collection-ado.md) [записи](../../../ado/reference/ado-api/record-object-ado.md), **точность** доступна только для чтения и записи только после того, как было указано свойство [value](../../../ado/reference/ado-api/value-property-ado.md) для **поля** и поставщик данных успешно добавил новое **поле** , вызвав метод [Update](../../../ado/reference/ado-api/update-method.md) коллекции **Fields** .  
  
## <a name="applies-to"></a>Применяется к  
  
|||  
|-|-|  
|[Объект Field](../../../ado/reference/ado-api/field-object.md)|[Объект Parameter](../../../ado/reference/ado-api/parameter-object.md)|  
  
## <a name="see-also"></a>См. также:  
 [Пример свойств NumericScale и Precision (Visual Basic)](../../../ado/reference/ado-api/numericscale-and-precision-properties-example-vb.md)   
 [Пример свойств NumericScale и Precision (Visual c++)](../../../ado/reference/ado-api/numericscale-and-precision-properties-example-vc.md)   
 [Свойство NumericScale (ADO)](../../../ado/reference/ado-api/numericscale-property-ado.md)
