---
title: "Набор строк DISCOVER_LITERALS | Документы Microsoft"
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
apiname: DISCOVER_LITERALS
apitype: NA
applies_to: SQL Server 2016 Preview
helpviewer_keywords: DISCOVER_LITERALS rowset
ms.assetid: 1bf0a2e2-a419-4c25-b271-37dfa44de2ea
caps.latest.revision: "33"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 1e66c7b388fd0f488bdb95f4e18de07de7773036
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/08/2017
---
# <a name="discoverliterals-rowset"></a>Набор строк DISCOVER_LITERALS
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Возвращает сведения о литералах, включая типы данных и значения, поддерживаемые [!INCLUDE[msCoName](../../../includes/msconame-md.md)] XML для аналитики (XMLA) поставщика.  
  
 При вызове метода [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md) метод с **DISCOVER_LITERALS** значения перечисления в [RequestType](../../../analysis-services/xmla/xml-elements-properties/requesttype-element-xmla.md) элемент, **Discover** метод возвращает **DISCOVER_LITERALS** набора строк.  
  
## <a name="rowset-columns"></a>Столбцы наборов строк  
 **DISCOVER_LITERALS** набор строк содержит следующие столбцы.  
  
|Имя столбца|Индикатор типа|Длина|Description|  
|-----------------|--------------------|------------|-----------------|  
|**LiteralName**|**DBTYPE_WSTR**||Имя литерала, описанное в строке.<br /><br /> Например: **DBLITERAL_LIKE_PERCENT**|  
|**LiteralValue**|**DBTYPE_WSTR**||Фактическое литеральное значение.<br /><br /> Например если **LiteralName** — **DBLITERAL_LIKE_PERCENT** и знак процента (**%**) выделяет ноль или более символов в предложении LIKE, значение из **LiteralValue** столбец «**%**».|  
|**LiteralInvalidChars**|**DBTYPE_WSTR**||Недопустимые символы в литерале.<br /><br /> Например, если имена таблиц могут содержать ничего, кроме числовой символ, эта строка является «**0123456789**».|  
|**LiteralInvalidStartingChars**|**DBTYPE_WSTR**||Символы, которые являются недопустимыми, если они представляют собой первый символ литерала. Если литерал можно начать с любой допустимый символ, это **null**.|  
|**LiteralMaxLength**|**DBTYPE_I4**||Максимальное количество символов в литерале. Если неизвестны максимальное и минимальное значения, то значение -1.|  
|**LiteralNameEnumValue**|**DBTYPE_I4**|||  
  
 Этот набор строк схемы не отсортирован.  
  
## <a name="restriction-columns"></a>Столбцы ограничений  
 **DISCOVER_LITERALS** строк может быть ограничен на столбцы в таблице ниже.  
  
|Имя столбца|Индикатор типа|Состояние ограничения|  
|-----------------|--------------------|-----------------------|  
|**LiteralName**|**DBTYPE_WSTR**|Необязательно.|  
  
## <a name="see-also"></a>См. также:  
 [XML для аналитики наборы строк схемы](../../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)   
 [Набор строк DISCOVER_KEYWORDS &#40; XML для Аналитики &#41;](../../../analysis-services/schema-rowsets/xml/discover-keywords-rowset-xmla.md)  
  
  
