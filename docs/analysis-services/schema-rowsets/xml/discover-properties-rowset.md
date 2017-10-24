---
title: "Набор строк DISCOVER_PROPERTIES | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- DISCOVER_PROPERTIES
apitype: NA
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- DISCOVER_PROPERTIES rowset
ms.assetid: 3e2b50e2-3855-4091-8b02-4968e8e57d4c
caps.latest.revision: 32
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 374ca8fc9ce17f7da659a9718e8a7a531e8c3ca5
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

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
 [XML для аналитики наборы строк схемы](../../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
  
  

