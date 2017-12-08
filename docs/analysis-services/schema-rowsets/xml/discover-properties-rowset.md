---
title: "Набор строк DISCOVER_PROPERTIES | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: schema-rowsets
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: DISCOVER_PROPERTIES
apitype: NA
applies_to: SQL Server 2016 Preview
helpviewer_keywords: DISCOVER_PROPERTIES rowset
ms.assetid: 3e2b50e2-3855-4091-8b02-4968e8e57d4c
caps.latest.revision: "32"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: b695d3affd1783782e1eb8bde27d6c90157e4bab
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="discoverproperties-rowset"></a>Набор строк DISCOVER_PROPERTIES
  Возвращает список сведений и значений для стандартных свойств и определяемых поставщиком свойств, которые поддерживаются поставщиком [!INCLUDE[msCoName](../../../includes/msconame-md.md)] XML для аналитики (XMLA) для указанного источника данных. Неподдерживаемые свойства в возвращаемом результирующем наборе не указываются.  
  
 При вызове метода [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md) метод с **DISCOVER_PROPERTIES** значения перечисления в [RequestType](../../../analysis-services/xmla/xml-elements-properties/requesttype-element-xmla.md) элемент, **Discover** метод возвращает **DISCOVER_PROPERTIES** строк...  
  
## <a name="rowset-columns"></a>Столбцы наборов строк  
 Набор строк **DISCOVER_PROPERTIES** содержит следующие столбцы.  
  
|Имя столбца|Тип|Длина|Description|  
|-----------------|----------|------------|-----------------|  
|**PropertyName**|**DBTYPE_WSTR**||Имя свойства.|  
|**PropertyDescription**|**DBTYPE_WSTR**||Текст локализованного описания свойства. Может возвращать значение **NULL**.|  
|**PropertyType**|**DBTYPE_WSTR**||Тип данных XML свойства.<br /><br /> Может возвращать значение **NULL**.|  
|**PropertyAccessType**|**DBTYPE_WSTR**||Доступ для свойства. Значением может быть **Read**, **Write**или **ReadWrite**.|  
|**Параметры IsRequired**|**DBTYPE_BOOL**||Логическое значение, указывающее, является ли свойство обязательным.<br /><br /> Значение true, если свойство является обязательным. В противном случае — значение false.<br /><br /> Может возвращать значение **NULL**.|  
|**Значение**|**DBTYPE_WSTR**||Текущее значение свойства.<br /><br /> Может возвращать значение **NULL**.|  
  
 Этот набор строк схемы не отсортирован.  
  
## <a name="restriction-columns"></a>Столбцы ограничений  
 Набор строк **DISCOVER_PROPERTIES** может быть ограничен столбцом, указанным в следующей таблице.  
  
|Имя столбца|Индикатор типа|Состояние ограничения|  
|-----------------|--------------------|-----------------------|  
|**PropertyName**|**DBTYPE_WSTR**||  
  
## <a name="see-also"></a>См. также:  
 [Наборы строк схемы XML для аналитики](../../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
  
  
