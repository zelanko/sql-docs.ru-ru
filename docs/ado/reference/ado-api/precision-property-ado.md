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
manager: jroth
ms.openlocfilehash: 59bfebe5885d0f18811b6b6c8df0f12634ed316f
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/05/2019
ms.locfileid: "66703246"
---
# <a name="precision-property-ado"></a>Свойство Precision (ADO)
Указывает степень точности для числовых значений в [параметр](../../../ado/reference/ado-api/parameter-object.md) объекта или для числовых [поле](../../../ado/reference/ado-api/field-object.md) объектов.  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Возвращает или задает **байтов** значение, указывающее максимальное число разрядов, используемых для представления значений.  
  
## <a name="remarks"></a>Примечания  
 Используйте **точности** свойства, чтобы определить максимальное число разрядов, используемых для представления значений для числового **параметр** или **поле** объекта.  
  
 Значение доступно для чтения/записи на **параметр** объекта.  
  
 Для **поле**объекта, **точности** обычно предназначены только для чтения. Тем не менее, для новых **поле** объекты, добавленные [поля](../../../ado/reference/ado-api/fields-collection-ado.md) коллекцию [записи](../../../ado/reference/ado-api/record-object-ado.md), **точности** доступно для чтения и записи только После [значение](../../../ado/reference/ado-api/value-property-ado.md) свойство для **поле** была определена и успешно добавил новый поставщик данных **поле** путем вызова [Обновления](../../../ado/reference/ado-api/update-method.md) метод **поля** коллекции.  
  
## <a name="applies-to"></a>Объект применения  
  
|||  
|-|-|  
|[Объект Field](../../../ado/reference/ado-api/field-object.md)|[Объект Parameter](../../../ado/reference/ado-api/parameter-object.md)|  
  
## <a name="see-also"></a>См. также  
 [Свойств NumericScale и Precision (Visual Basic)](../../../ado/reference/ado-api/numericscale-and-precision-properties-example-vb.md)   
 [Свойств NumericScale и Precision (Visual C++)](../../../ado/reference/ado-api/numericscale-and-precision-properties-example-vc.md)   
 [Свойство NumericScale (ADO)](../../../ado/reference/ado-api/numericscale-property-ado.md)
