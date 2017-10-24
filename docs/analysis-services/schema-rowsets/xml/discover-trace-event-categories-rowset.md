---
title: "Набор строк DISCOVER_TRACE_EVENT_CATEGORIES | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
ms.assetid: 1ad74fd2-4740-469d-85b5-abf0171737fd
caps.latest.revision: 7
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 997417427f43a8b626d27330ace4201d243fb044
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="discovertraceeventcategories-rowset"></a>Набор строк DISCOVER_TRACE_EVENT_CATEGORIES
  Отображает список категорий событий, которые поддерживаются поставщиком трассировки.  
  
 **Область применения:** табличные модели, многомерные модели  
  
## <a name="rowset-columns"></a>Столбцы наборов строк  
 Набор строк **DISCOVER_TRACE_EVENT_CATEGORIES** содержит следующие столбцы.  
  
|Имя столбца|Индикатор типа|Длина|Description|  
|-----------------|--------------------|------------|-----------------|  
|**Данные**|**DBTYPE_WSTR**||Содержит закодированную XML-строку, отображающую сведения о категории событий о поставщике трассировки, в том числе имя категории, тип и описание. «Type» — это строка, указывающая на тип категории событий. Возможны следующие значения перечислений:<br /><br /> 0=нормальное<br /><br /> 1=значительное<br /><br /> 2=ошибка|  
  
 Этот набор строк схемы не отсортирован.  
  
## <a name="using-adomdnet-to-return-the-rowset"></a>Использование ADOMD.NET для возврата набора строк  
 Если для получения метаданных используется ADOMD.NET и набор строк схемы, то для ссылки на объект набора строк схемы в методе GetSchemaDataSet вы можете использовать идентификатор GUID или строку. Дополнительные сведения см. в статье [Working with Schema Rowsets in ADOMD.NET](../../../analysis-services/multidimensional-models-adomd-net-client/retrieving-metadata-working-with-schema-rowsets.md).  
  
 В следующей таблице указываются значения строки и идентификатора GUID, определяющие этот набор строк.  
  
|Аргумент|Значение|  
|--------------|-----------|  
|GUID|a07ccd19-8148-11d0-87bb-00c04fc33942|  
|Строковые значения|DISCOVER_TRACE_EVENT_CATEGORIES|  
  
## <a name="see-also"></a>См. также:  
 [XML для аналитики наборы строк схемы](../../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
  
  

