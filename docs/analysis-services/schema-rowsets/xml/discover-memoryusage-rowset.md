---
title: "Набор строк DISCOVER_MEMORYUSAGE | Документы Microsoft"
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
ms.assetid: e416ea61-9615-468c-a96f-bbf731f803b1
caps.latest.revision: 7
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 3dcbb314e1816757562f93290d95a3f9e345460b
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="discovermemoryusage-rowset"></a>Набор строк DISCOVER_MEMORYUSAGE
  Возвращает статистику DISCOVER_MEMORYUSAGE для различных объектов, выделенных сервером.  
  
> [!WARNING]  
>  Этот набор строк может создавать очень большие результирующие наборы. Если результаты не удастся отобразить из-за того, что им требуется больше памяти для отображения, чем позволяет выделить среда SQL Server Management Studio, результаты будут записаны во временный файл, по умолчанию имеющий следующее размещение:  
>   
>  "\<диск >: \Users\\< имя_пользователя\>\AppData\Local\Temp\\< fileID\>XML-файла".  
  
 **Область применения:** табличные модели, многомерные модели  
  
## <a name="rowset-columns"></a>Столбцы наборов строк  
 **DISCOVER_MEMORYUSAGE** набор строк содержит следующие столбцы.  
  
|Имя столбца|Индикатор типа|Ограничение|Description|  
|-----------------|--------------------|-----------------|-----------------|  
|**MemoryID**|**DBTYPE_UI8**||Число, определяющее память.|  
|**MemoryName**|**DBTYPE_WSTR**||Имя объекта, задействующего память.|  
|**SPID**|**DBTYPE_UI4**|Да|Сеанс, в ходе которого выделена память. Нуль означает, что память не привязана к конкретному сеансу.|  
|**CreationTime**|**DBTYPE_DBTIMESTAMP**||Либо «время, за которое был создан объект», либо «время, за которое была выделена память».|  
|**Значением BaseObjectType**|**DBTYPE_UI4**|Да|Это номер, описывающий тип объекта. Объекты с одним значением BaseObjectType имеют одинаковый тип.|  
|**MemoryUsed**|**DBTYPE_UI8**|Да|Это текущий размер объекта, который может быть меньше, чем объем памяти, выделенной для использования объектом.|  
|**MemoryAllocated**|**DBTYPE_UI8**||Объем памяти, выделенный для использования объектом, который может превышать фактический объем памяти, используемый объектом.|  
|**MemoryAllocBase**|**DBTYPE_UI8**||Байты, первоначально выделенные для самого объекта (исключая дополнительные выделения для содержания объекта).|  
|**MemoryAllocFromAlloc**|**DBTYPE_UI8**||Память, выделенная для содержания этого объекта.|  
|**Значение ElementCount**|**DBTYPE_UI4**||Для объекта-контейнера это количество объектов, содержащихся в этом объекте.|  
|**Пределы возможного**|**DBTYPE_BOOL**|Да|Логическое значение, указывающее, является ли память сжимаемой (то есть может быть освобождена в связи с нехваткой памяти). Если это значение true, то память является сжимаемой; если значение false, то память не является сжимаемой.|  
|**ObjectParentPath**|**DBTYPE_WSTR**||Строка, определяющая полный путь этого объекта.|  
|**ObjectID**|**DBTYPE_WSTR**||Строка, определяющая объект. Полный путь этого объекта, представленного этой строкой: (ObjectParentPath + "." + ObjectId).|  
  
 Этот набор строк схемы не отсортирован.  
  
## <a name="using-adomdnet-to-return-the-rowset"></a>Использование ADOMD.NET для возврата набора строк  
 Если для получения метаданных используется ADOMD.NET и набор строк схемы, то для ссылки на объект набора строк схемы в методе GetSchemaDataSet вы можете использовать идентификатор GUID или строку. Дополнительные сведения см. в статье [Working with Schema Rowsets in ADOMD.NET](../../../analysis-services/multidimensional-models-adomd-net-client/retrieving-metadata-working-with-schema-rowsets.md).  
  
 В следующей таблице указываются значения строки и идентификатора GUID, определяющие этот набор строк.  
  
|Аргумент|Значение|  
|--------------|-----------|  
|GUID|A07CCD21-8148-11D0-87BB-00C04FC33942|  
|ADOMDNAME|MemoryUsage|  
  
## <a name="see-also"></a>См. также:  
 [XML для аналитики наборы строк схемы](../../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
  
  

