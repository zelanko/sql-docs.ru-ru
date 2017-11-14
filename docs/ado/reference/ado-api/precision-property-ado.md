---
title: "Свойство точности (ADO) | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- _Parameter::Precision
- Field20::Precision
helpviewer_keywords:
- Precision property [ADO]
ms.assetid: 1fa38e78-6b5b-414d-ba0a-3dd26b29b766
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: ce6c07fa24f146664ffe5433869e4edf45abdd69
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="precision-property-ado"></a>Свойство точности (ADO)
Указывает степень точность для числовых значений в [параметр](../../../ado/reference/ado-api/parameter-object.md) объекта или для числовых [поле](../../../ado/reference/ado-api/field-object.md) объектов.  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Возвращает или задает **байтов** значение, указывающее максимальное число разрядов, используемых для представления значений.  
  
## <a name="remarks"></a>Замечания  
 Используйте **точности** свойства, чтобы определить максимальное число разрядов, используемых для представления значений для числового **параметр** или **поле** объекта.  
  
 Значение — чтение и запись на **параметр** объекта.  
  
 Для **поле**объекта, **точности** обычно доступны только для чтения. Однако для новых **поле** объектов, добавленных в [поля](../../../ado/reference/ado-api/fields-collection-ado.md) коллекцию [запись](../../../ado/reference/ado-api/record-object-ado.md), **точности** доступен для чтения и записи только После [значение](../../../ado/reference/ado-api/value-property-ado.md) свойство **поле** был указан и поставщик данных успешно добавлен новый **поле** путем вызова [Обновление](../../../ado/reference/ado-api/update-method.md) метод **поля** коллекции.  
  
## <a name="applies-to"></a>Объект применения  
  
|||  
|-|-|  
|[Объект field](../../../ado/reference/ado-api/field-object.md)|[Объект параметра](../../../ado/reference/ado-api/parameter-object.md)|  
  
## <a name="see-also"></a>См. также:  
 [NumericScale и пример точности свойства (Visual Basic)](../../../ado/reference/ado-api/numericscale-and-precision-properties-example-vb.md)   
 [Пример свойства точности (VC ++) и NumericScale](../../../ado/reference/ado-api/numericscale-and-precision-properties-example-vc.md)   
 [Свойство NumericScale (ADO)](../../../ado/reference/ado-api/numericscale-property-ado.md)

