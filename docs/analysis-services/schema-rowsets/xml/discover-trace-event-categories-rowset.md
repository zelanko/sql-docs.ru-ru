---
title: "Набор строк DISCOVER_TRACE_EVENT_CATEGORIES | Документы Microsoft"
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
ms.assetid: 1ad74fd2-4740-469d-85b5-abf0171737fd
caps.latest.revision: "7"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 1adc4b7e60c566ac1c46a4b51c06e2ee505916ee
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/08/2017
---
# <a name="discovertraceeventcategories-rowset"></a>Набор строк DISCOVER_TRACE_EVENT_CATEGORIES
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Отображается список категорий событий, которые поддерживаются поставщиком трассировки.  
  
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
 [Наборы строк схемы XML для аналитики](../../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
  
  
