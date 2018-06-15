---
title: Свойство точности (ADO) | Документы Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
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
manager: craigg
ms.openlocfilehash: 630bae40ab9e473656abeb3fa8cdb79de89e258c
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/11/2018
ms.locfileid: "35280643"
---
# <a name="precision-property-ado"></a>Свойство точности (ADO)
Указывает степень точность для числовых значений в [параметр](../../../ado/reference/ado-api/parameter-object.md) объекта или для числовых [поле](../../../ado/reference/ado-api/field-object.md) объектов.  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Возвращает или задает **байтов** значение, указывающее максимальное число разрядов, используемых для представления значений.  
  
## <a name="remarks"></a>Примечания  
 Используйте **точности** свойства, чтобы определить максимальное число разрядов, используемых для представления значений для числового **параметр** или **поле** объекта.  
  
 Значение — чтение и запись на **параметр** объекта.  
  
 Для **поле**объекта, **точности** обычно доступны только для чтения. Однако для новых **поле** объектов, добавленных в [поля](../../../ado/reference/ado-api/fields-collection-ado.md) коллекцию [запись](../../../ado/reference/ado-api/record-object-ado.md), **точности** доступен для чтения и записи только После [значение](../../../ado/reference/ado-api/value-property-ado.md) свойство **поле** был указан и поставщик данных успешно добавлен новый **поле** путем вызова [Обновление](../../../ado/reference/ado-api/update-method.md) метод **поля** коллекции.  
  
## <a name="applies-to"></a>Объект применения  
  
|||  
|-|-|  
|[Объект Field](../../../ado/reference/ado-api/field-object.md)|[Объект Parameter](../../../ado/reference/ado-api/parameter-object.md)|  
  
## <a name="see-also"></a>См. также  
 [NumericScale и пример точности свойства (Visual Basic)](../../../ado/reference/ado-api/numericscale-and-precision-properties-example-vb.md)   
 [Пример свойства точности (VC ++) и NumericScale](../../../ado/reference/ado-api/numericscale-and-precision-properties-example-vc.md)   
 [Свойство NumericScale (ADO)](../../../ado/reference/ado-api/numericscale-property-ado.md)
