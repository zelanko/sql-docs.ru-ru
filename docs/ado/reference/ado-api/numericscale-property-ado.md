---
title: "Свойство NumericScale (ADO) | Документы Microsoft"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- _Parameter::NumericScale
- Field20::NumericScale
helpviewer_keywords:
- NumericScale property [ADO]
ms.assetid: 29a02992-64be-4fcd-be13-445cba205893
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 98f5c141f0cf9483ab7d527f46911a36257ced47
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="numericscale-property-ado"></a>Свойство NumericScale (ADO)
Указывает шкалу числовых значений в [параметр](../../../ado/reference/ado-api/parameter-object.md) или [поле](../../../ado/reference/ado-api/field-object.md) объекта.  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Возвращает или задает **байтов** значение, указывающее число десятичных разрядов для числового значения, которые будут разрешены.  
  
## <a name="remarks"></a>Замечания  
 Используйте **NumericScale** свойства, чтобы определить, сколько цифр справа от десятичной запятой будет использоваться для представления значений для числового **параметр** или **поле** объекта.  
  
 Для **параметр** объектов, **NumericScale** свойство доступно для чтения/записи.  
  
 Для **поле**объекта, **NumericScale** обычно доступны только для чтения. Однако для новых **поле** объектов, добавленных в [поля](../../../ado/reference/ado-api/fields-collection-ado.md) коллекцию [запись](../../../ado/reference/ado-api/record-object-ado.md), **NumericScale** доступен для чтения и записи только после [значение](../../../ado/reference/ado-api/value-property-ado.md) свойство **поле** был указан и поставщик данных успешно добавлен новый **поле** путем вызова [ Обновление](../../../ado/reference/ado-api/update-method.md) метод [поля](../../../ado/reference/ado-api/fields-collection-ado.md) коллекции.  
  
## <a name="applies-to"></a>Объект применения  
  
|||  
|-|-|  
|[Объект параметра](../../../ado/reference/ado-api/parameter-object.md)|[Объект field](../../../ado/reference/ado-api/field-object.md)|  
  
## <a name="see-also"></a>См. также:  
 [NumericScale и пример точности свойства (Visual Basic)](../../../ado/reference/ado-api/numericscale-and-precision-properties-example-vb.md)   
 [Пример свойства точности (VC ++) и NumericScale](../../../ado/reference/ado-api/numericscale-and-precision-properties-example-vc.md)   
 [Свойство точности (ADO)](../../../ado/reference/ado-api/precision-property-ado.md)

