---
title: "Поле объекта | Документы Microsoft"
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
- Field
helpviewer_keywords:
- Field object [ADO]
ms.assetid: b10a72fc-3c4b-4186-a70b-993dc9f7a092
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: f876e76b29dbc2436d6d1dba317c5035ebbc9ca1
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="field-object"></a>Объект Field
Представляет столбец данных с общим типом данных.  
  
## <a name="remarks"></a>Замечания  
 Каждый **поле** объекта соответствует столбцу в [записей](../../../ado/reference/ado-api/recordset-object-ado.md). Вы используете [значение](../../../ado/reference/ado-api/value-property-ado.md) свойство **поле** объектов, чтобы задать или получить данные для текущей записи. В зависимости от функции предоставляет поставщик, некоторые коллекции, методы или свойства **поле** могут оказаться недоступными.  
  
 С коллекциями, методы и свойства **поле** объекта, можно сделать следующее:  
  
-   Возвращает имя поля с [имя](../../../ado/reference/ado-api/name-property-ado.md) свойства.  
  
-   Просмотр или изменение данных в поле с **значение** свойства. **Значение** — свойство по умолчанию **поле** объекта.  
  
-   Возвращает основные характеристики поля с [тип](../../../ado/reference/ado-api/type-property-ado.md), [точности](../../../ado/reference/ado-api/precision-property-ado.md), и [NumericScale](../../../ado/reference/ado-api/numericscale-property-ado.md) свойства.  
  
-   Возвращать объявленный размер поля с [DefinedSize](../../../ado/reference/ado-api/definedsize-property.md) свойство.  
  
-   Возвращает фактический размер данных в данном поле с [ActualSize](../../../ado/reference/ado-api/actualsize-property-ado.md) свойство.  
  
-   Определить, какие функции поддерживаются для данного поля с [атрибуты](../../../ado/reference/ado-api/attributes-property-ado.md) свойство и [свойства](../../../ado/reference/ado-api/properties-collection-ado.md) коллекции.  
  
-   Изменять значения полей, содержащих двоичные или долго символьных данных с помощью [AppendChunk](../../../ado/reference/ado-api/appendchunk-method-ado.md) и [GetChunk](../../../ado/reference/ado-api/getchunk-method-ado.md) методы.  
  
-   Если поставщик поддерживает пакетные обновления, устранить несоответствия в значения полей во время обновления пакета с [OriginalValue](../../../ado/reference/ado-api/originalvalue-property-ado.md) и [UnderlyingValue](../../../ado/reference/ado-api/underlyingvalue-property.md) свойства.  
  
 Все свойства метаданных (**имя**, **тип**, **DefinedSize**, **точности**, и **NumericScale**) доступны перед открытием **поле** объекта **записей**. Установка их в это время полезна для динамического создания форм.  
  
 Этот раздел содержит следующий раздел.  
  
-   [Свойства объекта поля, методы и события](../../../ado/reference/ado-api/field-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>См. также:  
 [Коллекция Fields (ADO)](../../../ado/reference/ado-api/fields-collection-ado.md)   
 [Коллекция свойств (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)   
 [Объект набора записей (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)

