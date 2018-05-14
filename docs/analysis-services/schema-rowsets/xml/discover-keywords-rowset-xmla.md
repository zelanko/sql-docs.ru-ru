---
title: Набор строк DISCOVER_KEYWORDS (XMLA) | Документы Microsoft
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: schema-rowsets
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 4950b157fcf2b64bf6dd634f20a59dc82eb072d9
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="discoverkeywords-rowset-xmla"></a>Набор строк DISCOVER_KEYWORDS (XMLA)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Возвращает сведения о ключевых словах, зарезервированных [!INCLUDE[msCoName](../../../includes/msconame-md.md)] XML для аналитики (XMLA) поставщика.  
  
 При вызове метода [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md) метод с **DISCOVER_KEYWORDS** значения перечисления в [RequestType](../../../analysis-services/xmla/xml-elements-properties/requesttype-element-xmla.md) элемент, **Discover** метод возвращает **DISCOVER_KEYWORDS** набора строк.  
  
## <a name="rowset-columns"></a>Столбцы наборов строк  
 **DISCOVER_KEYWORDS** набор строк содержит следующие столбцы.  
  
|Имя столбца|Индикатор типа|Длина|Описание|  
|-----------------|--------------------|------------|-----------------|  
|**Ключевое слово**|**DBTYPE_WSTR**||Список всех ключевых слов, зарезервированных поставщиком.<br /><br /> Пример: **AND**|  
  
 Этот набор строк схемы не отсортирован.  
  
## <a name="restriction-columns"></a>Столбцы ограничений  
 **DISCOVER_KEYWORDS** строк может быть ограничен столбцами, перечисленными в следующей таблице.  
  
|Имя столбца|Индикатор типа|Состояние ограничения|  
|-----------------|--------------------|-----------------------|  
|**Ключевое слово**|**DBTYPE_WSTR**|Необязательно.|  
  
## <a name="see-also"></a>См. также  
 [XML для аналитики наборы строк схемы](../../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)   
 [Набор строк DISCOVER_LITERALS](../../../analysis-services/schema-rowsets/xml/discover-literals-rowset.md)  
  
  
