---
title: Набор строк DISCOVER_LITERALS | Документы Microsoft
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: schema-rowsets
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: ed865f22291b3e2e47c4934e455e0e75795d35cc
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="discoverliterals-rowset"></a>Набор строк DISCOVER_LITERALS
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Возвращает сведения о литералах, включая типы данных и значения, поддерживаемые поставщиком XML для аналитики [!INCLUDE[msCoName](../../../includes/msconame-md.md)].  
  
 При вызове метода [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md) метод с **DISCOVER_LITERALS** значения перечисления в [RequestType](../../../analysis-services/xmla/xml-elements-properties/requesttype-element-xmla.md) элемент, **Discover** метод возвращает **DISCOVER_LITERALS** набора строк.  
  
## <a name="rowset-columns"></a>Столбцы наборов строк  
 **DISCOVER_LITERALS** набор строк содержит следующие столбцы.  
  
|Имя столбца|Индикатор типа|Длина|Описание|  
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
  
## <a name="see-also"></a>См. также  
 [XML для аналитики наборы строк схемы](../../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)   
 [Набор строк DISCOVER_KEYWORDS & #40; XML для Аналитики & #41;](../../../analysis-services/schema-rowsets/xml/discover-keywords-rowset-xmla.md)  
  
  
