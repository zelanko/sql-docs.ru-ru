---
title: Типы данных XML (XML для Аналитики) | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
topic_type:
- apiref
- apinav
helpviewer_keywords:
- XML data types [XMLA]
- data types [XML for Analysis]
- XMLA, data types
- XML for Analysis, data types
ms.assetid: 979b5384-90d9-4e09-9286-1d1eafdc4864
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: d7a21691474e890ba8614715b18e972d1353b2c6
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36109777"
---
# <a name="xml-data-types-xmla"></a>Типы данных XML (XML для аналитики)
  В дополнение к стандартным примитивным и производным типам, которые были определены в рекомендации XML 1.0, в спецификации XML для аналитики (XMLA) 1.1 были добавлены определения дополнительных типов данных, предназначенных для поддержки представления многомерных и табличных данных.  
  
 Типы данных, используемые XMLA, перечислены в следующей таблице.  
  
|Типы данных|Описание|  
|----------------|-----------------|  
|Логическое значение|Стандартный тип данных XML `boolean`.|  
|Decimal|Стандартный тип данных XML `decimal`.|  
|[EmptyResult](emptyresult-data-type-xmla.md)|Пространство имен элемента `root`. Это пространство имен возвращается, когда команды XML для Аналитики не возвращающие результатов, так как команда XMLA обычно не возвращающие результатов, или из-за ошибки на [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] экземпляра при обработке команды XMLA.|  
|[EnumString](enumstring-data-type-xmla.md)|Набор именованных строковых констант для данного перечислителя.|  
|Целочисленный|Стандартный тип данных XML `int`.|  
|[MDDataSet](mddataset-data-type-xmla.md)|Многомерные данные, возвращаемые *результат* параметр [Execute](../xml-elements-methods-execute.md) метод.|  
|[Результирующий набор](resultset-data-type-xmla.md)|Описывающий сам себя результирующий набор XML, возвращаемый методом `Execute`.|  
|[Функции набора строк](rowset-data-type-xmla.md)|Строки из источника данных, структурированные внедренной XML-схемой, возвращаемые методом [Discover](../xml-elements-methods-discover.md) метод.|  
|String|Тип данных XML `string`.|  
|UnsignedInt|Тип схемы XML `unsignedInt`.|  
  
 Полные описания стандартных типов данных XML см. в соответствующей рекомендации консорциума World Wide Web (WC3).  
  
## <a name="see-also"></a>См. также  
 [XML-элементы &#40;XML для Аналитики&#41;](../../dev-guide/xml-elements-xmla.md)   
 [XML для аналитики &#40;XMLA&#41; ссылки](../xml-for-analysis-xmla-reference.md)  
  
  