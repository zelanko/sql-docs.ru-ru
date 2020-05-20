---
title: Свойство Attributes (ADO) | Документация Майкрософт
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 488fe5a46b994ed664c6355e24fe8d567d5ff11d
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2020
ms.locfileid: "82762911"
---
# <a name="attributes-property-ado"></a>Свойство Attributes (ADO)
Указывает одну или несколько характеристик объекта.  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Задает или возвращает значение **типа Long** .  
  
 Для объекта [соединения](../../../ado/reference/ado-api/connection-object-ado.md) свойство **Attributes** доступно для чтения и записи, а его значение может быть суммой одного или нескольких значений [ксактаттрибутинум](../../../ado/reference/ado-api/xactattributeenum.md) . Значение по умолчанию равно нулю (0).  
  
 Для объекта [параметра](../../../ado/reference/ado-api/parameter-object.md) свойство **Attributes** доступно для чтения и записи, а его значение может быть суммой любого одного или нескольких значений [параметераттрибутесенум](../../../ado/reference/ado-api/parameterattributesenum.md) . Значение по умолчанию — **адпарамсигнед**.  
  
 Для объекта [field](../../../ado/reference/ado-api/field-object.md) свойство **Attributes** может быть суммой одного или нескольких значений [фиелдаттрибутинум](../../../ado/reference/ado-api/fieldattributeenum.md) . Обычно он доступен только для чтения. Однако для новых объектов **field** , добавленных к коллекции [Fields](../../../ado/reference/ado-api/fields-collection-ado.md) [записи](../../../ado/reference/ado-api/record-object-ado.md), **атрибуты** доступны только для чтения и записи только после того, как было указано свойство [value](../../../ado/reference/ado-api/value-property-ado.md) для **поля** и новое **поле** было успешно добавлено поставщиком данных путем вызова метода [Update](../../../ado/reference/ado-api/update-method.md) коллекции **Fields** .  
  
 Для объекта [Property](../../../ado/reference/ado-api/property-object-ado.md) свойство **Attributes** доступно только для чтения, а его значение может быть суммой любого одного или нескольких значений [пропертяттрибутесенум](../../../ado/reference/ado-api/propertyattributesenum.md) .  
  
## <a name="remarks"></a>Remarks  
 Свойство **Attributes** используется для задания или возвращения характеристик объектов **соединения** , объектов **параметров** , объектов **полей** или объектов **свойств** .  
  
 При задании нескольких атрибутов можно суммировать соответствующие константы. Если задать для свойства значение Sum, включая несовместимые константы, возникает ошибка.  
  
> [!NOTE]
>  **Использование удаленной службы данных** Это свойство недоступно для объекта **подключения** на стороне клиента.  
  
## <a name="applies-to"></a>Применяется к  
  
|||  
|-|-|  
|[Объект Connection (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)|[Объект Field](../../../ado/reference/ado-api/field-object.md)|  
|[Объект Parameter](../../../ado/reference/ado-api/parameter-object.md)|[Объект Property (ADO)](../../../ado/reference/ado-api/property-object-ado.md)|  
  
## <a name="see-also"></a>См. также  
 [Пример атрибутов и свойств имени (Visual Basic)](../../../ado/reference/ado-api/attributes-and-name-properties-example-vb.md)   
 [Пример атрибутов и свойств имени (Visual c++)](../../../ado/reference/ado-api/attributes-and-name-properties-example-vc.md)   
 [Метод AppendChunk (ADO)](../../../ado/reference/ado-api/appendchunk-method-ado.md)   
 [Методы примеры BeginTrans, CommitTrans и RollbackTrans (ADO)](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-ado.md)   
 [Метод GetChunk (ADO)](../../../ado/reference/ado-api/getchunk-method-ado.md)
