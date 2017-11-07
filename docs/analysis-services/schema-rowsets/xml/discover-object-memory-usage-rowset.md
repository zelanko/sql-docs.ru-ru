---
title: "Набор строк DISCOVER_OBJECT_MEMORY_USAGE | Документы Microsoft"
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
helpviewer_keywords:
- DISCOVER_OBJECT_MEMORY_USAGE rowset
ms.assetid: 211cfa04-7bd6-43fe-8bd5-bfbff78bdafb
caps.latest.revision: 13
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 6bfd0d6517f974b60b3d35f25e5836bcd6a7c8e2
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="discoverobjectmemoryusage-rowset"></a>Набор строк DISCOVER_OBJECT_MEMORY_USAGE
  Предоставляет сведения об использовании ресурсов памяти объектами.  
  
## <a name="rowset-columns"></a>Столбцы наборов строк  
 Набор строк **DISCOVER_OBJECT_MEMORY_USAGE** содержит следующие столбцы.  
  
|Имя столбца|Индикатор типа|Длина|Description|  
|-----------------|--------------------|------------|-----------------|  
|**OBJECT_PARENT_PATH**|**DBTYPE_WSTR**||Путь к родительскому объекту для текущего объекта.|  
|**OBJECT_ID**|**DBTYPE_WSTR**||Идентификатор объекта, определенный при создании.|  
|**OBJECT_MEMORY_SHRINKABLE**|**DBTYPE_I8**||Общий объем памяти (в байтах), который используется всеми сжимаемыми объектами, непосредственно принадлежащими текущему объекту. В это значение не включается память объектов, принадлежащих именованным объектам, которые в свою очередь принадлежат текущему объекту.|  
|**OBJECT_MEMORY_NONSHRINKABLE**|**DBTYPE_I8**||Объем памяти (в байтах) всех несжимаемых объектов, которые принадлежат напрямую текущему объекту. В это значение не включается память объектов, принадлежащих именованным объектам, которые в свою очередь принадлежат текущему объекту.|  
|**OBJECT_VERSION**|**DBTYPE_I4**||Номер версии метаданных объекта. Этот номер изменяется при каждом изменении объекта.|  
|**OBJECT_DATA_VERSION**|**DBTYPE_I4**||Номер журнала обращений и преобразований для данных в объекте. Этот номер увеличивается каждый раз при обработке объекта.|  
|**OBJECT_TYPE_ID**|**DBTYPE_I4**||Зарезервировано для внутреннего использования.|  
|**OBJECT_TIME_CREATED**|**DBTYPE_DBTIMESTAMP**||Время сервера в формате UTC, когда был создан объект.|  
  
 Этот набор строк схемы не отсортирован.  
  
## <a name="restriction-columns"></a>Столбцы ограничений  
 Набор строк **DISCOVER_OBJECT_MEMORY_USAGE** может быть ограничен столбцами, перечисленными в следующей таблице.  
  
|Имя столбца|Индикатор типа|Состояние ограничения|  
|-----------------|--------------------|-----------------------|  
|**OBJECT_PARENT_PATH**|**DBTYPE_WSTR**|Необязательно.|  
|**OBJECT_ID**|**DBTYPE_WSTR**|Необязательно|  
  
## <a name="see-also"></a>См. также:  
 [XML для аналитики наборы строк схемы](../../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
  
  

