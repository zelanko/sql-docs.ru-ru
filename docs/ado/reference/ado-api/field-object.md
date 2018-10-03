---
title: Поле объекта | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Field
helpviewer_keywords:
- Field object [ADO]
ms.assetid: b10a72fc-3c4b-4186-a70b-993dc9f7a092
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 002e0f570aa2143ddba4a5b55f3cba1537389e77
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47753322"
---
# <a name="field-object"></a>Объект Field
Представляет столбец данных с типом данных.  
  
## <a name="remarks"></a>Примечания  
 Каждый **поле** соответствует столбец в [записей](../../../ado/reference/ado-api/recordset-object-ado.md). Использовании [значение](../../../ado/reference/ado-api/value-property-ado.md) свойство **поле** объекты задание или возврат данных для текущей записи. В зависимости от функции предоставляет поставщик, некоторые коллекции, методы или свойства **поле** могут оказаться недоступными.  
  
 С помощью коллекций, методы и свойства **поле** объекта, можно сделать следующее:  
  
-   Возвращает имя поля с [имя](../../../ado/reference/ado-api/name-property-ado.md) свойство.  
  
-   Просмотр или изменение данных в поле с **значение** свойства. **Значение** — свойство по умолчанию **поле** объекта.  
  
-   Возвращает основные характеристики поле с [тип](../../../ado/reference/ado-api/type-property-ado.md), [точности](../../../ado/reference/ado-api/precision-property-ado.md), и [NumericScale](../../../ado/reference/ado-api/numericscale-property-ado.md) свойства.  
  
-   Возвращать декларируемый размер поля с [DefinedSize](../../../ado/reference/ado-api/definedsize-property.md) свойство.  
  
-   Возвращает фактический размер данных в этом поле с [ActualSize](../../../ado/reference/ado-api/actualsize-property-ado.md) свойство.  
  
-   Определить, какие функции поддерживаются для заданного поля с [атрибуты](../../../ado/reference/ado-api/attributes-property-ado.md) свойство и [свойства](../../../ado/reference/ado-api/properties-collection-ado.md) коллекции.  
  
-   Изменять значения полей, содержащих двоичные или долго символьных данных с помощью [AppendChunk](../../../ado/reference/ado-api/appendchunk-method-ado.md) и [GetChunk](../../../ado/reference/ado-api/getchunk-method-ado.md) методы.  
  
-   Если поставщик поддерживает пакетные обновления, устранить несоответствия в значения полей во время обновления пакета с [OriginalValue](../../../ado/reference/ado-api/originalvalue-property-ado.md) и [UnderlyingValue](../../../ado/reference/ado-api/underlyingvalue-property.md) свойства.  
  
 Все свойства метаданных (**имя**, **тип**, **DefinedSize**, **точности**, и **NumericScale**) доступны перед открытием **поле** объекта **записей**. Задание их в этот момент полезно за динамическое создание форм.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Объект свойств поля, методы и события](../../../ado/reference/ado-api/field-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>См. также  
 [Коллекция Fields (ADO)](../../../ado/reference/ado-api/fields-collection-ado.md)   
 [Коллекция Properties (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)   
 [Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)
