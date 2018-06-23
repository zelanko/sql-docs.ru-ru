---
title: Набор строк DISCOVER_XEVENT_TRACE_DEFINITION | Документы Microsoft
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
ms.assetid: e1ce2d2d-f994-4318-801a-ee0385aecd84
caps.latest.revision: 6
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 2994ce526ff0f8035d16485bf99b146e2366389e
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36100106"
---
# <a name="discoverxeventtracedefinition-rowset"></a>Набор строк DISCOVER_XEVENT_TRACE_DEFINITION
  Содержит сведения о трассировках XEvent, которые в настоящее время активны на сервере.  
  
 **Область применения:** табличные модели, многомерные модели  
  
## <a name="rowset-columns"></a>Столбцы наборов строк  
 `DISCOVER_XEVENT_TRACE_DEFINITION` Набор строк содержит следующие столбцы.  
  
|Имя столбца|Индикатор типа|Длина|Описание|  
|-----------------|--------------------|------------|-----------------|  
|`Data`|`DBTYPE_WSTR`||XML-определение трассировки XEvent.|  
  
 Этот набор строк схемы не отсортирован.  
  
## <a name="using-adomdnet-to-return-the-rowset"></a>Использование ADOMD.NET для возврата набора строк  
 Если для получения метаданных используется ADOMD.NET и набор строк схемы, то для ссылки на объект набора строк схемы в методе GetSchemaDataSet вы можете использовать идентификатор GUID или строку. Дополнительные сведения см. в статье [Working with Schema Rowsets in ADOMD.NET](../multidimensional-models-adomd-net-client/retrieving-metadata-working-with-schema-rowsets.md).  
  
 В следующей таблице указываются значения строки и идентификатора GUID, определяющие этот набор строк.  
  
|Аргумент|Значение|  
|--------------|-----------|  
|GUID|a07ccd1c-8148-11d0-87bb-00c04fc33942|  
|String|DISCOVER_XEVENT_TRACE_DEFINITION|  
  
## <a name="see-also"></a>См. также  
 [XML для аналитики наборы строк схемы](../schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)   
 [Использование расширенных событий SQL Server &#40;XEvents&#41; для наблюдения за Analysis Services](../instances/monitor-analysis-services-with-sql-server-extended-events.md)   
 [Используйте динамические административные представления &#40;динамических административных представлений&#41; для наблюдения за Analysis Services](../instances/use-dynamic-management-views-dmvs-to-monitor-analysis-services.md)  
  
  