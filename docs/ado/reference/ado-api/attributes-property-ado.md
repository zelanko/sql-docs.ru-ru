---
title: "Атрибуты свойства (ADO) | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
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
- Connection15::Attributes
- Field20::Attributes
- _Parameter::Attributes
helpviewer_keywords:
- Attributes property [ADO]
ms.assetid: acc15d40-68a6-4ba9-85bd-12d331aecaa6
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c2b63ff111ddf295784a6e8d3d574f0c36267f19
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/09/2018
---
# <a name="attributes-property-ado"></a>Свойства атрибутов (ADO)
Указывает один или несколько характеристик объекта.  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Возвращает или задает **длинные** значение.  
  
 Для [подключения](../../../ado/reference/ado-api/connection-object-ado.md) объекта, **атрибуты** свойство доступно для чтения/записи, и его значение может быть суммы одного или нескольких [XactAttributeEnum](../../../ado/reference/ado-api/xactattributeenum.md) значения. Значение по умолчанию равно нулю (0).  
  
 Для [параметр](../../../ado/reference/ado-api/parameter-object.md) объекта, **атрибуты** свойство доступно для чтения/записи, и его значение может быть суммы одного или нескольких [ParameterAttributesEnum](../../../ado/reference/ado-api/parameterattributesenum.md) значения. Значение по умолчанию — **adParamSigned**.  
  
 Для [поле](../../../ado/reference/ado-api/field-object.md) объекта, **атрибуты** свойство может быть суммы одного или нескольких [FieldAttributeEnum](../../../ado/reference/ado-api/fieldattributeenum.md) значения. Это обычно доступны только для чтения. Однако для новых **поле** объектов, добавленных в [поля](../../../ado/reference/ado-api/fields-collection-ado.md) коллекцию [запись](../../../ado/reference/ado-api/record-object-ado.md), **атрибуты** доступен для чтения и записи только После [значение](../../../ado/reference/ado-api/value-property-ado.md) свойство **поле** был указан и новых **поле** успешно добавлен в поставщике данных путем вызова [ Обновление](../../../ado/reference/ado-api/update-method.md) метод **поля** коллекции.  
  
 Для [свойство](../../../ado/reference/ado-api/property-object-ado.md) объекта, **атрибуты** свойство доступно только для чтения, и его значение может быть суммы одного или нескольких [PropertyAttributesEnum](../../../ado/reference/ado-api/propertyattributesenum.md) значения.  
  
## <a name="remarks"></a>Remarks  
 Используйте **атрибуты** свойство задание или возврат характеристики **подключения** объектов, **параметр** объектов, **поле** объекты, или **Свойство** объектов.  
  
 При установке нескольких атрибутов, можно просуммировать соответствующие константы. Если значение свойства равно сумму, включая несовместимые константы, возникает ошибка.  
  
> [!NOTE]
>  **Удаленное использование службы данных** это свойство доступно не на стороне клиента **подключения** объекта.  
  
## <a name="applies-to"></a>Объект применения  
  
|||  
|-|-|  
|[Объект Connection (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)|[Объект Field](../../../ado/reference/ado-api/field-object.md)|  
|[Объект Parameter](../../../ado/reference/ado-api/parameter-object.md)|[Объект Property (ADO)](../../../ado/reference/ado-api/property-object-ado.md)|  
  
## <a name="see-also"></a>См. также  
 [Атрибуты и примере имя свойства (Visual Basic)](../../../ado/reference/ado-api/attributes-and-name-properties-example-vb.md)   
 [Атрибуты и свойства пример имени (VC ++)](../../../ado/reference/ado-api/attributes-and-name-properties-example-vc.md)   
 [Метод AppendChunk (ADO)](../../../ado/reference/ado-api/appendchunk-method-ado.md)   
 [BeginTrans CommitTrans и методы RollbackTrans (ADO)](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-ado.md)   
 [Метод GetChunk (ADO)](../../../ado/reference/ado-api/getchunk-method-ado.md)
