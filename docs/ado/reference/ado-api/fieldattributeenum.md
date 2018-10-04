---
title: FieldAttributeEnum | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- FieldAttributeEnum
helpviewer_keywords:
- FieldAttributeEnum enumeration [ADO]
ms.assetid: 6e34d886-005a-40dc-bd5c-6adcbf81e5cd
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 80fb27aa51d6e0a44f8f006711708e24cd04bef3
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47632322"
---
# <a name="fieldattributeenum"></a>FieldAttributeEnum
Указывает один или несколько атрибутов [поле](../../../ado/reference/ado-api/field-object.md) объекта.  
  
|Константа|Значение|Описание|  
|--------------|-----------|-----------------|  
|**adFldCacheDeferred**|0x1000|Указывает, что поставщик кэширует значения полей и что последующие операции чтения выполняются из кэша.|  
|**adFldFixed**|0x10|Указывает, что поле содержит данные фиксированной длины.|  
|**adFldIsChapter**|0x2000|Указывает, что поле содержит значение главы, указывающий набор дочерних записей, связанных с этой родительское поле. Обычно Глава поля используются с формирования данных или фильтры.|  
|**adFldIsCollection**|0x40000|Указывает, что поле задает, что с ресурсом, представленным запись является коллекцией других ресурсов, например в папке, а не простой ресурс, например, текстовый файл.|  
|**adFldKeyColumn**|0x8000|Указывает, что поле задает полностью или частично столбца первичного ключа.|  
|**adFldIsDefaultStream**|0x20000|Указывает, что поле содержит поток по умолчанию для ресурса, представленного записи. Например поток по умолчанию может быть содержимое HTML в корневой папке веб-сайта, который обслуживается автоматически в том случае, если указан корневой URL-адрес.|  
|**adFldIsNullable**|0x20|Указывает, что поле может принимать значения null.|  
|**adFldIsRowURL**|0x10000|Указывает, что поле содержит URL-адреса, имена ресурсов из хранилища данных, представленный записи.|  
|**adFldLong**|0x80|Указывает, что поле является длинным двоичным полем. Также указывает, что можно использовать [AppendChunk](../../../ado/reference/ado-api/appendchunk-method-ado.md) и [GetChunk](../../../ado/reference/ado-api/getchunk-method-ado.md) методы.|  
|**adFldMayBeNull**|0x40|Указывает, что можно прочитать значения null из поля.|  
|**adFldMayDefer**|0x2|Указывает, что поле откладывается — то есть значения полей не извлекаются из источника данных с помощью всей записи, но только в том случае, если вы явным образом обращаться к ним.|  
|**adFldNegativeScale**|0x4000|Указывает, что поле представляет числовое значение из столбца, который поддерживает отрицательные значения масштабирования. Масштаб задается [NumericScale](../../../ado/reference/ado-api/numericscale-property-ado.md) свойство.|  
|**adFldRowID**|0x100|Указывает, что поле содержит постоянный идентификатор строк, не может быть записан и имеющий отсутствии содержательного значения, за исключением того, чтобы определить строки (например, номер записи, уникальный идентификатор и так далее).|  
|**adFldRowVersion**|0x200|Указывает, что поле содержит какой-то отметку времени или даты, используемый для отслеживания обновлений.|  
|**adFldUnknownUpdatable**|0x8|Указывает, что поставщик не может определить, если можно написать с полем.|  
|**adFldUnspecified**|-1 0xFFFFFFFF|Указывает, что поставщик не указывает атрибутов полей.|  
|**adFldUpdatable**|0x4|Указывает, что можно записывать в поле.|  
  
## <a name="adowfc-equivalent"></a>Эквивалент ADO и WFC  
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
