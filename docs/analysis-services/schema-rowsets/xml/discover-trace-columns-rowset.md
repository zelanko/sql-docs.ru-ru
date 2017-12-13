---
title: "Набор строк DISCOVER_TRACE_COLUMNS | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
ms.assetid: 02baf401-52b0-4a73-8a7b-3b5b5e568626
caps.latest.revision: "6"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: f9cdeebfead1e664db65d9a08112497199442ca1
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/08/2017
---
# <a name="discovertracecolumns-rowset"></a>Набор строк DISCOVER_TRACE_COLUMNS
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Возвращает XML-документ с описанием столбцов, доступных в трассировке.  
  
 **Область применения:** табличные модели, многомерные модели  
  
## <a name="rowset-columns"></a>Столбцы наборов строк  
 Набор строк **DISCOVER_TRACE_COLUMNS** содержит следующие столбцы.  
  
|Имя столбца|Индикатор типа|Ограничение|Description|  
|-----------------|--------------------|-----------------|-----------------|  
|**Данные**|**DBTYPE_WSTR**|Да|Содержит закодированную XML-строку с описанием сведений о столбцах трассировки, предоставленных поставщиком трассировки.|  
  
 Этот набор строк схемы не отсортирован.  
  
## <a name="using-adomdnet-to-return-the-rowset"></a>Использование ADOMD.NET для возврата набора строк  
 Если для получения метаданных используется ADOMD.NET и набор строк схемы, то для ссылки на объект набора строк схемы в методе GetSchemaDataSet вы можете использовать идентификатор GUID или строку. Дополнительные сведения см. в статье [Working with Schema Rowsets in ADOMD.NET](../../../analysis-services/multidimensional-models-adomd-net-client/retrieving-metadata-working-with-schema-rowsets.md).  
  
 В следующей таблице указываются значения строки и идентификатора GUID, определяющие этот набор строк.  
  
|Аргумент|Значение|  
|--------------|-----------|  
|GUID|a07ccd18-8148-11d0-87bb-00c04fc33942|  
|ADOMDNAME|TraceColumns|  
  
## <a name="see-also"></a>См. также:  
 [Наборы строк схемы XML для аналитики](../../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
  
  
