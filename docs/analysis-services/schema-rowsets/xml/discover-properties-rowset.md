---
title: "Набор строк DISCOVER_PROPERTIES | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
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
ms.openlocfilehash: a5a68b41673466ef2e27846f598d070ee68903e7
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/08/2017
---
# <a name="discoverproperties-rowset"></a>Набор строк DISCOVER_PROPERTIES
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Возвращает список сведений и значений свойства стандартных и поставщика, поддерживаемых [!INCLUDE[msCoName](../../../includes/msconame-md.md)] XML для аналитики (XMLA) поставщика для указанного источника данных. Неподдерживаемые свойства в возвращаемом результирующем наборе не указываются.  
  
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
  
  
