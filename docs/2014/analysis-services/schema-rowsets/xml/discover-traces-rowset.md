---
title: Набор строк DISCOVER_TRACES | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
ms.assetid: 1be6a035-ffc9-489e-9d4d-7391b3e384e2
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 26d40f737db108ea2a9f8a9cee05f3ee9503c73c
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48168246"
---
# <a name="discovertraces-rowset"></a>Набор строк DISCOVER_TRACES
  Содержит сведения о трассировках, которые в настоящее время активны на сервере.  
  
 **Область применения:** табличные модели, многомерные модели  
  
## <a name="rowset-columns"></a>Столбцы наборов строк  
 `DISCOVER_TRACES` Набор строк содержит следующие столбцы.  
  
|Имя столбца|Индикатор типа|Описание|  
|-----------------|--------------------|-----------------|  
|`TraceID`|`DBTYPE_WSTR`|Идентификатор трассировки.|  
|`TraceName`|`DBTYPE_WSTR`|Имя трассировки.|  
|`LogFileName`|`DBTYPE_WSTR`|Имя файла журнала трассировки.|  
|`LogFileSize`|`DBTYPE_I4`|Размер файла журнала трассировки.|  
|`LogFileRollover`|`DBTYPE_BOOL`|Когда параметр соответствует значению true, это означает, что файл журнала необходимо откатить. Если это не так, параметр имеет значение false.|  
|`AutoRestart`|`DBTYPE_BOOL`|Когда это значение true, это означает, что функция автоматического перезапуска включена. Иначе значение false.|  
|`CreationTime`|`DBTYPE_TIME`|Дата и время создания трассировки.|  
|`StopTime`|`DBTYPE_TIME`|Время остановки трассировки.|  
|`Type`|`PF_DBTYPE_WSTR`|Тип трассировки.|  
  
 Этот набор строк схемы не отсортирован.  
  
## <a name="restriction-columns"></a>Столбцы ограничений  
 Набор строк `DISCOVER_TRACES` может быть ограничен столбцами, перечисленными в следующей таблице.  
  
|Имя столбца|Индикатор типа|Состояние ограничения|  
|-----------------|--------------------|-----------------------|  
|**TraceId**|`DBTYPE_I4`|Необязательный параметр.|  
|`Type`|WSTR|Необязательный параметр.|  
  
## <a name="using-adomdnet-to-return-the-rowset"></a>Использование ADOMD.NET для возврата набора строк  
 Если для получения метаданных используется ADOMD.NET и набор строк схемы, то для ссылки на объект набора строк схемы в методе GetSchemaDataSet вы можете использовать идентификатор GUID или строку. Дополнительные сведения см. в статье [Working with Schema Rowsets in ADOMD.NET](../../../relational-databases/native-client-ole-db-rowsets/rowsets.md).  
  
 В следующей таблице указываются значения строки и идентификатора GUID, определяющие этот набор строк.  
  
|Аргумент|Значение|  
|--------------|-----------|  
|GUID|a07ccd1a-8148-11d0-87bb-00c04fc33942|  
|String|DISCOVER_TRACES|  
  
## <a name="see-also"></a>См. также  
 [Наборы строк схемы XML для аналитики](xml-for-analysis-schema-rowsets.md)  
  
  
