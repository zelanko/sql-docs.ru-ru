---
title: FieldAttributeEnum | Документы Microsoft
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- FieldAttributeEnum
helpviewer_keywords:
- FieldAttributeEnum enumeration [ADO]
ms.assetid: 6e34d886-005a-40dc-bd5c-6adcbf81e5cd
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c54502119e76de0357551600f4288bac5d59cc9c
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="fieldattributeenum"></a>FieldAttributeEnum
Указывает один или несколько атрибутов [поле](../../../ado/reference/ado-api/field-object.md) объекта.  
  
|Константа|Значение|Описание|  
|--------------|-----------|-----------------|  
|**adFldCacheDeferred**|0x1000|Указывает, что поставщик хранит значения полей и что последующие операции чтения выполняются из кэша.|  
|**adFldFixed**|0x10|Указывает, что поле содержит данные фиксированной длины.|  
|**adFldIsChapter**|0x2000|Указывает, что поле содержит значение главе, который указывает набор дочерних записей, связанных с этой родительское поле. Обычно поля главе используются с формирования данных или фильтры.|  
|**adFldIsCollection**|0x40000|Означает, что поле указывает, что ресурсом, представленным записи — это совокупность другие ресурсы, например в папке, а не простой ресурс, такие как текстовый файл.|  
|**adFldKeyColumn**|0x8000|Означает, что поле указывает все или часть столбцов первичного ключа.|  
|**adFldIsDefaultStream**|0x20000|Указывает, что поле содержит поток по умолчанию для ресурса, представленного записи. Например поток по умолчанию может быть HTML-содержимого в корневой папке веб-сайта, который обслуживается автоматически, если указан корневой URL-адрес.|  
|**adFldIsNullable**|0x20|Указывает, что поле может принимать значения null.|  
|**adFldIsRowURL**|0x10000|Указывает, что поле содержит URL-адрес с именем ресурса из хранилища данных, представленных в записи.|  
|**adFldLong**|0x80|Указывает, что поле является длинным двоичным полем. Также показывает, что можно использовать [AppendChunk](../../../ado/reference/ado-api/appendchunk-method-ado.md) и [GetChunk](../../../ado/reference/ado-api/getchunk-method-ado.md) методы.|  
|**adFldMayBeNull**|0x40|Указывает, что можно прочитать значения null из поля.|  
|**adFldMayDefer**|0x2|Указывает, что поле откладывается — то есть, значения полей не извлекаются из источника данных с записью целиком, но только в том случае, если вы явным образом получить к ним доступ.|  
|**adFldNegativeScale**|0x4000|Указывает, что поле представляет числовое значение из столбца, поддерживающий масштабировать отрицательные значения. Масштаб задается [NumericScale](../../../ado/reference/ado-api/numericscale-property-ado.md) свойство.|  
|**adFldRowID**|0x100|Указывает, что поле содержит постоянный идентификатор строки, не может быть записан и не может применяться значение, за исключением того, чтобы идентифицировать строку (например, номер записи, уникальный идентификатор и так далее).|  
|**adFldRowVersion**|0x200|Указывает, что поле содержит какой-то Отметка даты и времени, используемая для отслеживания обновлений.|  
|**adFldUnknownUpdatable**|0x8|Указывает, что поставщик не может определить, можно написать для поля.|  
|**adFldUnspecified**|-1 0xFFFFFFFF|Указывает, что поставщик не указывает атрибуты поля.|  
|**adFldUpdatable**|0x4|Указывает, что можно написать для поля.|  
  
## <a name="adowfc-equivalent"></a>Эквивалент ADO/WFC  
 Пакет: **com.ms.wfc.data**  
  
|Константа|  
|--------------|  
|AdoEnums.FieldAttribute.CACHEDEFERRED|  
|AdoEnums.FieldAttribute.FIXED|  
|AdoEnums.FieldAttribute.ISNULLABLE|  
|AdoEnums.FieldAttribute.LONG|  
|AdoEnums.FieldAttribute.MAYBENULL|  
|AdoEnums.FieldAttribute.MAYDEFER|  
|AdoEnums.FieldAttribute.NEGATIVESCALE|  
|AdoEnums.FieldAttribute.ROWID|  
|AdoEnums.FieldAttribute.ROWVERSION|  
|AdoEnums.FieldAttribute.UNKNOWNUPDATABLE|  
|AdoEnums.FieldAttribute.UNSPECIFIED|  
|AdoEnums.FieldAttribute.UPDATABLE|  
  
## <a name="applies-to"></a>Объект применения  
  
|||  
|-|-|  
|[Метод Append (ADO)](../../../ado/reference/ado-api/append-method-ado.md)|[Свойство Attributes (ADO)](../../../ado/reference/ado-api/attributes-property-ado.md)|
