---
title: Атрибуты свойства (ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Connection15::Attributes
- Field20::Attributes
- _Parameter::Attributes
helpviewer_keywords:
- Attributes property [ADO]
ms.assetid: acc15d40-68a6-4ba9-85bd-12d331aecaa6
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 91425029546402edbd5bde7df45586c77e38d83b
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66696382"
---
# <a name="attributes-property-ado"></a>Свойство Attributes (ADO)
Указывает один или несколько характеристик объекта.  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Возвращает или задает **Long** значение.  
  
 Для [подключения](../../../ado/reference/ado-api/connection-object-ado.md) объекта, **атрибуты** свойство чтения/записи и его значение может быть сумма одного или нескольких [XactAttributeEnum](../../../ado/reference/ado-api/xactattributeenum.md) значения. Значение по умолчанию равно нулю (0).  
  
 Для [параметр](../../../ado/reference/ado-api/parameter-object.md) объекта, **атрибуты** свойство чтения/записи и его значение может быть сумма одного или нескольких [ParameterAttributesEnum](../../../ado/reference/ado-api/parameterattributesenum.md) значения. По умолчанию используется **adParamSigned**.  
  
 Для [поле](../../../ado/reference/ado-api/field-object.md) объекта, **атрибуты** свойство может быть сумма одного или нескольких [FieldAttributeEnum](../../../ado/reference/ado-api/fieldattributeenum.md) значения. Это обычно предназначены только для чтения. Тем не менее, для новых **поле** объекты, добавленные [поля](../../../ado/reference/ado-api/fields-collection-ado.md) коллекцию [записи](../../../ado/reference/ado-api/record-object-ado.md), **атрибуты** доступно для чтения и записи только После [значение](../../../ado/reference/ado-api/value-property-ado.md) свойство для **поле** была определена и новый **поле** успешно добавлен в поставщике данных путем вызова [ Обновление](../../../ado/reference/ado-api/update-method.md) метод **поля** коллекции.  
  
 Для [свойство](../../../ado/reference/ado-api/property-object-ado.md) объекта, **атрибуты** свойство доступно только для чтения, и его значение может быть сумма одного или нескольких [PropertyAttributesEnum](../../../ado/reference/ado-api/propertyattributesenum.md) значения.  
  
## <a name="remarks"></a>Примечания  
 Используйте **атрибуты** свойство задание или возврат характеристики **подключения** объектов, **параметр** объектов, **поле** объектов, или **Свойство** объектов.  
  
 Если задано несколько атрибутов, можно просуммировать соответствующие константы. Если задать значение свойства с суммой, включая несовместимые константы, возникает ошибка.  
  
> [!NOTE]
>  **Удаленное использование службы данных** это свойство доступно не на стороне клиента **подключения** объекта.  
  
## <a name="applies-to"></a>Объект применения  
  
|||  
|-|-|  
|[Объект Connection (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)|[Объект Field](../../../ado/reference/ado-api/field-object.md)|  
|[Объект Parameter](../../../ado/reference/ado-api/parameter-object.md)|[Объект Property (ADO)](../../../ado/reference/ado-api/property-object-ado.md)|  
  
## <a name="see-also"></a>См. также  
 [Примеры Attributes и Name свойства (Visual Basic)](../../../ado/reference/ado-api/attributes-and-name-properties-example-vb.md)   
 [Примеры Attributes и Name свойства (Visual C++)](../../../ado/reference/ado-api/attributes-and-name-properties-example-vc.md)   
 [Метод AppendChunk (ADO)](../../../ado/reference/ado-api/appendchunk-method-ado.md)   
 [Примеры BeginTrans, CommitTrans и RollbackTrans методы (ADO)](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-ado.md)   
 [Метод GetChunk (ADO)](../../../ado/reference/ado-api/getchunk-method-ado.md)
