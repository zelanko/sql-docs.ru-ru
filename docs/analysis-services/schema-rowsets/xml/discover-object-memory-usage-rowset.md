---
title: "Набор строк DISCOVER_OBJECT_MEMORY_USAGE | Документы Microsoft"
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
applies_to: SQL Server 2016 Preview
helpviewer_keywords: DISCOVER_OBJECT_MEMORY_USAGE rowset
ms.assetid: 211cfa04-7bd6-43fe-8bd5-bfbff78bdafb
caps.latest.revision: "13"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 9be5091d26d264d71dad5e6892f7f8d7448d83c4
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="discoverobjectmemoryusage-rowset"></a>Набор строк DISCOVER_OBJECT_MEMORY_USAGE
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Сведения о ресурсах памяти, используемой объектами.  
  
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
|**OBJECT_PARENT_PATH**|**DBTYPE_WSTR**|Необязательный параметр.|  
|**OBJECT_ID**|**DBTYPE_WSTR**|Необязательно|  
  
## <a name="see-also"></a>См. также:  
 [Наборы строк схемы XML для аналитики](../../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
  
  
