---
title: Набор рядов Discover_partition_dimension_stat | Документы Microsoft
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: schema-rowsets
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: fe43b694b8fdeb4128ae1ad2aa9dc137d2bc9d42
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
ms.locfileid: "34034515"
---
# <a name="discoverpartitiondimensionstat-rowset"></a>Набор рядов DISCOVER_PARTITION_DIMENSION_STAT
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Возвращает статистику по измерению, связанному с секцией  
  
 **Область применения:** табличные модели, многомерные модели  
  
## <a name="rowset-columns"></a>Столбцы наборов строк  
 Набор строк **DISCOVER_PARTITION_DIMENSION_STAT** содержит следующие столбцы.  
  
|Имя столбца|Индикатор типа|Ограничение|Описание|  
|-----------------|--------------------|-----------------|-----------------|  
|**ИМЯ_БАЗЫ_ДАННЫХ**|**DBTYPE_WSTR**|Обязательно|Имя базы данных.<br /><br /> Этот столбец является обязательным в списке ограничений.|  
|**CUBE_NAME**|**DBTYPE_WSTR**|Обязательно|Имя куба или табличной модели.<br /><br /> Этот столбец является обязательным в списке ограничений.|  
|**MEASURE_GROUP_NAME**|**DBTYPE_WSTR**|Обязательно|Имя группы мер.<br /><br /> Этот столбец является обязательным в списке ограничений.|  
|**ИМЯ_РАЗДЕЛА**|**DBTYPE_WSTR**|Обязательно|Имя секции.<br /><br /> Этот столбец является обязательным в списке ограничений.|  
|**DIMENSION_NAME**|**DBTYPE_WSTR**||Имя измерения.<br /><br /> Этот столбец является обязательным в списке ограничений.|  
|**ATTRIBUTE_NAME**|**DBTYPE_WSTR**||Имя атрибута в измерении.|  
|**ATTRIBUTE_INDEXED**|**DBTYPE_BOOL**||Если значение true, это означает, что атрибут индексируется, иначе значение false.|  
|**ATTRIBUTE_COUNT_MIN**|**DBTYPE_I8**||Минимальное количество атрибутов.|  
|**ATTRIBUTE_COUNT_MAX**|**DBTYPE_I8**||Максимальное количество атрибутов.|  
  
 Этот набор строк схемы не отсортирован.  
  
## <a name="using-adomdnet-to-return-the-rowset"></a>Использование ADOMD.NET для возврата набора строк  
 Если для получения метаданных используется ADOMD.NET и набор строк схемы, то для ссылки на объект набора строк схемы в методе GetSchemaDataSet вы можете использовать идентификатор GUID или строку. Дополнительные сведения см. в статье [Working with Schema Rowsets in ADOMD.NET](../../../analysis-services/multidimensional-models-adomd-net-client/retrieving-metadata-working-with-schema-rowsets.md).  
  
 В следующей таблице указываются значения строки и идентификатора GUID, определяющие этот набор строк.  
  
|Аргумент|Значение|  
|--------------|-----------|  
|GUID|a07ccd8e-8148-11d0-87bb-00c04fc33942|  
|ADOMDNAME|PartitionDimensionStat|  
  
## <a name="see-also"></a>См. также:  
 [XML для аналитики наборы строк схемы](../../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
  
  
