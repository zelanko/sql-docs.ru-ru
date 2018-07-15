---
title: Набор строк DISCOVER_PARTITION_DIMENSION_STAT | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: bf4626b3-4d6b-4795-bb01-df335fb9c09a
caps.latest.revision: 6
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 9f4dc209f985cafe804f81fa54fa68c56655d3e4
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37310744"
---
# <a name="discoverpartitiondimensionstat-rowset"></a>Набор рядов DISCOVER_PARTITION_DIMENSION_STAT
  Возвращает статистику по измерению, связанному с секцией  
  
 **Область применения:** табличные модели, многомерные модели  
  
## <a name="rowset-columns"></a>Столбцы наборов строк  
 `DISCOVER_PARTITION_DIMENSION_STAT` Набор строк содержит следующие столбцы.  
  
|Имя столбца|Индикатор типа|Ограничение|Описание|  
|-----------------|--------------------|-----------------|-----------------|  
|`DATABASE_NAME`|`DBTYPE_WSTR`|Обязательно|Имя базы данных.<br /><br /> Этот столбец является обязательным в списке ограничений.|  
|`CUBE_NAME`|`DBTYPE_WSTR`|Обязательно|Имя куба или табличной модели.<br /><br /> Этот столбец является обязательным в списке ограничений.|  
|`MEASURE_GROUP_NAME`|`DBTYPE_WSTR`|Обязательно|Имя группы мер.<br /><br /> Этот столбец является обязательным в списке ограничений.|  
|`PARTITION_NAME`|`DBTYPE_WSTR`|Обязательно|Имя секции.<br /><br /> Этот столбец является обязательным в списке ограничений.|  
|`DIMENSION_NAME`|`DBTYPE_WSTR`||Имя измерения.<br /><br /> Этот столбец является обязательным в списке ограничений.|  
|`ATTRIBUTE_NAME`|`DBTYPE_WSTR`||Имя атрибута в измерении.|  
|`ATTRIBUTE_INDEXED`|`DBTYPE_BOOL`||Если значение true, это означает, что атрибут индексируется, иначе значение false.|  
|`ATTRIBUTE_COUNT_MIN`|`DBTYPE_I8`||Минимальное количество атрибутов.|  
|`ATTRIBUTE_COUNT_MAX`|`DBTYPE_I8`||Максимальное количество атрибутов.|  
  
 Этот набор строк схемы не отсортирован.  
  
## <a name="using-adomdnet-to-return-the-rowset"></a>Использование ADOMD.NET для возврата набора строк  
 Если для получения метаданных используется ADOMD.NET и набор строк схемы, то для ссылки на объект набора строк схемы в методе GetSchemaDataSet вы можете использовать идентификатор GUID или строку. Дополнительные сведения см. в статье [Working with Schema Rowsets in ADOMD.NET](../../../relational-databases/native-client-ole-db-rowsets/rowsets.md).  
  
 В следующей таблице указываются значения строки и идентификатора GUID, определяющие этот набор строк.  
  
|Аргумент|Значение|  
|--------------|-----------|  
|GUID|a07ccd8e-8148-11d0-87bb-00c04fc33942|  
|ADOMDNAME|PartitionDimensionStat|  
  
## <a name="see-also"></a>См. также  
 [Наборы строк схемы XML для аналитики](xml-for-analysis-schema-rowsets.md)  
  
  
