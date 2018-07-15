---
title: Набор строк DISCOVER_DIMENSION_STAT | Документация Майкрософт
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
ms.assetid: 639f8cd7-3b43-40d5-8b84-552daf60d484
caps.latest.revision: 7
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: d70382117367762dc35a6d02663f54436ea63bb3
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37289741"
---
# <a name="discoverdimensionstat-rowset"></a>Набор строк DISCOVER_DIMENSION_STAT
  Предоставляет сведения об измерении, в том числе имя базы данных, в котором оно содержится, имя измерения, его атрибуты и число членов для каждого атрибута. В табличной модели соответствует столбцам в таблице и количеству значений в каждом столбце.  
  
 **Область применения:** табличные модели, многомерные модели  
  
## <a name="rowset-columns"></a>Столбцы наборов строк  
 `DISCOVER_DIMENSION_STAT` Набор строк содержит следующие столбцы.  
  
|Имя столбца|Индикатор типа|Ограничение|Описание|  
|-----------------|--------------------|-----------------|-----------------|  
|`DATABASE_NAME`|`DBTYPE_WSTR`|Обязательно|Имя базы данных, содержащей измерение.<br /><br /> Этот столбец является обязательным в списке ограничений.|  
|`DIMENSION_NAME`|`DBTYPE_WSTR`|Обязательно|Имя измерения.<br /><br /> Этот столбец является обязательным в списке ограничений.|  
|`ATTRIBUTE_NAME`|`DBTYPE_WSTR`||Имя атрибута в измерении.|  
|`ATTRIBUTE_COUNT`|`DBTYPE_I8`||Число значений в именованном атрибуте. Для табличной модели это значение всегда совпадает с количеством строк в таблице.|  
  
 Этот набор строк схемы не отсортирован.  
  
## <a name="using-adomdnet-to-return-the-rowset"></a>Использование ADOMD.NET для возврата набора строк  
 Если для получения метаданных используется ADOMD.NET и набор строк схемы, то для ссылки на объект набора строк схемы в методе GetSchemaDataSet вы можете использовать идентификатор GUID или строку. Дополнительные сведения см. в статье [Working with Schema Rowsets in ADOMD.NET](../../../relational-databases/native-client-ole-db-rowsets/rowsets.md).  
  
 В следующей таблице указываются значения строки и идентификатора GUID, определяющие этот набор строк.  
  
|Аргумент|Значение|  
|--------------|-----------|  
|GUID|a07ccd90-8148-11d0-87bb-00c04fc33942|  
|ADOMDNAME|PartitionDimensionStat|  
  
## <a name="see-also"></a>См. также  
 [Наборы строк схемы XML для аналитики](xml-for-analysis-schema-rowsets.md)  
  
  
