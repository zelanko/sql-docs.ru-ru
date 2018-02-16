---
title: "Набор строк DISCOVER_TRACES | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
ms.assetid: 1be6a035-ffc9-489e-9d4d-7391b3e384e2
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: c79aa16cc7dc0d232c3acaa4407588932befc124
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/15/2018
---
# <a name="discovertraces-rowset"></a>Набор строк DISCOVER_TRACES
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
Содержит сведения о трассировках, которые в настоящее время активны на сервере.  
  
 **Область применения:** табличные модели, многомерные модели  
  
## <a name="rowset-columns"></a>Столбцы наборов строк  
 Набор строк **DISCOVER_TRACES** содержит следующие столбцы.  
  
|Имя столбца|Индикатор типа|Описание|  
|-----------------|--------------------|-----------------|  
|**TraceID**|**DBTYPE_WSTR**|Идентификатор трассировки.|  
|**Имя трассировки**|**DBTYPE_WSTR**|Имя трассировки.|  
|**LogFileName**|**DBTYPE_WSTR**|Имя файла журнала трассировки.|  
|**LogFileSize**|**DBTYPE_I4**|Размер файла журнала трассировки.|  
|**LogFileRollover**|**DBTYPE_BOOL**|Когда параметр соответствует значению true, это означает, что файл журнала необходимо откатить. Если это не так, параметр имеет значение false.|  
|**Автоматический перезапуск**|**DBTYPE_BOOL**|Когда это значение true, это означает, что функция автоматического перезапуска включена. Иначе значение false.|  
|**CreationTime**|**DBTYPE_TIME**|Дата и время создания трассировки.|  
|**StopTime**|**DBTYPE_TIME**|Время остановки трассировки.|  
|**Тип**|**PF_DBTYPE_WSTR**|Тип трассировки.|  
  
 Этот набор строк схемы не отсортирован.  
  
## <a name="restriction-columns"></a>Столбцы ограничений  
 Набор строк **DISCOVER_TRACES** может быть ограничен столбцами, перечисленными в следующей таблице.  
  
|Имя столбца|Индикатор типа|Состояние ограничения|  
|-----------------|--------------------|-----------------------|  
|**TraceId**|**DBTYPE_I4**|Необязательно.|  
|**Тип**|WSTR|Необязательно.|  
  
## <a name="using-adomdnet-to-return-the-rowset"></a>Использование ADOMD.NET для возврата набора строк  
 Если для получения метаданных используется ADOMD.NET и набор строк схемы, то для ссылки на объект набора строк схемы в методе GetSchemaDataSet вы можете использовать идентификатор GUID или строку. Дополнительные сведения см. в статье [Working with Schema Rowsets in ADOMD.NET](../../../analysis-services/multidimensional-models-adomd-net-client/retrieving-metadata-working-with-schema-rowsets.md).  
  
 В следующей таблице указываются значения строки и идентификатора GUID, определяющие этот набор строк.  
  
|Аргумент|Значение|  
|--------------|-----------|  
|GUID|a07ccd1a-8148-11d0-87bb-00c04fc33942|  
|Строковые значения|DISCOVER_TRACES|  
  
## <a name="see-also"></a>См. также  
 [XML для аналитики наборы строк схемы](../../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
  
  
