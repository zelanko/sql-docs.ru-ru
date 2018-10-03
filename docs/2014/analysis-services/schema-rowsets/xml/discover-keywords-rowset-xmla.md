---
title: Набор строк DISCOVER_KEYWORDS (XMLA) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- DISCOVER_KEYWORDS
topic_type:
- apiref
helpviewer_keywords:
- DISCOVER_KEYWORDS rowset
ms.assetid: 99945e53-3a1b-4d7b-9aff-712977db8b2d
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: f7395447d832e7cc9f0a0eec745ca419ad19c6c3
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48050924"
---
# <a name="discoverkeywords-rowset-xmla"></a>Набор строк DISCOVER_KEYWORDS (XMLA)
  Возвращает сведения о ключевых словах, зарезервированных [!INCLUDE[msCoName](../../../includes/msconame-md.md)] XML для аналитики (XMLA) поставщика.  
  
 При вызове метода [Discover](../../xmla/xml-elements-methods-discover.md) метод с `DISCOVER_KEYWORDS` значение перечисления в [RequestType](../../xmla/xml-elements-properties/type-element-xmla.md) элемент, `Discover` возвращает метод `DISCOVER_KEYWORDS` набора строк.  
  
## <a name="rowset-columns"></a>Столбцы наборов строк  
 `DISCOVER_KEYWORDS` Набор строк содержит следующие столбцы.  
  
|Имя столбца|Индикатор типа|Длина|Описание|  
|-----------------|--------------------|------------|-----------------|  
|`Keyword`|`DBTYPE_WSTR`||Список всех ключевых слов, зарезервированных поставщиком.<br /><br /> Пример: `AND`|  
  
 Этот набор строк схемы не отсортирован.  
  
## <a name="restriction-columns"></a>Столбцы ограничений  
 Набор строк `DISCOVER_KEYWORDS` может быть ограничен столбцами, перечисленными в следующей таблице.  
  
|Имя столбца|Индикатор типа|Состояние ограничения|  
|-----------------|--------------------|-----------------------|  
|`Keyword`|`DBTYPE_WSTR`|Необязательный параметр.|  
  
## <a name="see-also"></a>См. также  
 [XML для анализа наборов строк схемы](xml-for-analysis-schema-rowsets.md)   
 [Набор строк DISCOVER_LITERALS](discover-literals-rowset.md)  
  
  
