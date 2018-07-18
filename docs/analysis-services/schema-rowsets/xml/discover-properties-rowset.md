---
title: Набор строк DISCOVER_PROPERTIES | Документы Microsoft
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: schema-rowsets
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 8752af7b67b69659ec3d9a348b4ec7c647f41c55
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
ms.locfileid: "34030295"
---
# <a name="discoverproperties-rowset"></a>Набор строк DISCOVER_PROPERTIES
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Возвращает список сведений и значений для стандартных свойств и определяемых поставщиком свойств, которые поддерживаются поставщиком [!INCLUDE[msCoName](../../../includes/msconame-md.md)] XML для аналитики (XMLA) для указанного источника данных. Неподдерживаемые свойства в возвращаемом результирующем наборе не указываются.  
  
 При вызове метода [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md) метод с **DISCOVER_PROPERTIES** значения перечисления в [RequestType](../../../analysis-services/xmla/xml-elements-properties/requesttype-element-xmla.md) элемент, **Discover** метод возвращает **DISCOVER_PROPERTIES** строк...  
  
## <a name="rowset-columns"></a>Столбцы наборов строк  
 Набор строк **DISCOVER_PROPERTIES** содержит следующие столбцы.  
  
|Имя столбца|Тип|Длина|Описание|  
|-----------------|----------|------------|-----------------|  
|**propertyName**|**DBTYPE_WSTR**||Имя свойства.|  
|**PropertyDescription**|**DBTYPE_WSTR**||Текст локализованного описания свойства. Может возвращать значение **NULL**.|  
|**PropertyType**|**DBTYPE_WSTR**||Тип данных XML свойства.<br /><br /> Может возвращать значение **NULL**.|  
|**PropertyAccessType**|**DBTYPE_WSTR**||Доступ для свойства. Значением может быть **Read**, **Write**или **ReadWrite**.|  
|**Параметры IsRequired**|**DBTYPE_BOOL**||Логическое значение, указывающее, является ли свойство обязательным.<br /><br /> Значение true, если свойство является обязательным. В противном случае — значение false.<br /><br /> Может возвращать значение **NULL**.|  
|**Value**|**DBTYPE_WSTR**||Текущее значение свойства.<br /><br /> Может возвращать значение **NULL**.|  
  
 Этот набор строк схемы не отсортирован.  
  
## <a name="restriction-columns"></a>Столбцы ограничений  
 Набор строк **DISCOVER_PROPERTIES** может быть ограничен столбцом, указанным в следующей таблице.  
  
|Имя столбца|Индикатор типа|Состояние ограничения|  
|-----------------|--------------------|-----------------------|  
|**propertyName**|**DBTYPE_WSTR**||  
  
## <a name="see-also"></a>См. также  
 [XML для аналитики наборы строк схемы](../../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
  
  
