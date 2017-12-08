---
title: "Типы данных XML (XML для Аналитики) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: xmla
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
helpviewer_keywords:
- XML data types [XMLA]
- data types [XML for Analysis]
- XMLA, data types
- XML for Analysis, data types
ms.assetid: 979b5384-90d9-4e09-9286-1d1eafdc4864
caps.latest.revision: "35"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: ba74f6ec5cb8ad35d4cdbb76e408bcb6cc203dea
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="xml-data-types-xmla"></a>Типы данных XML (XML для аналитики)
  В дополнение к стандартным примитивным и производным типам, которые были определены в рекомендации XML 1.0, в спецификации XML для аналитики (XMLA) 1.1 были добавлены определения дополнительных типов данных, предназначенных для поддержки представления многомерных и табличных данных.  
  
 Типы данных, используемые XMLA, перечислены в следующей таблице.  
  
|Типы данных|Описание|  
|----------------|-----------------|  
|Boolean|Стандартный тип данных XML **boolean** .|  
|Decimal|Стандартный тип данных XML **decimal** .|  
|[EmptyResult](../../../analysis-services/xmla/xml-data-types/emptyresult-data-type-xmla.md)|Пространство имен элемента **root** . Это пространство имен возвращается, когда команды XML для Аналитики не возвращающие результатов, так как команда XMLA обычно не возвращающие результатов, или из-за ошибки на [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] экземпляра при обработке команды XMLA.|  
|[EnumString](../../../analysis-services/xmla/xml-data-types/enumstring-data-type-xmla.md)|Набор именованных строковых констант для данного перечислителя.|  
|Целочисленный|Стандартный тип данных XML **int** .|  
|[MDDataSet](../../../analysis-services/xmla/xml-data-types/mddataset-data-type-xmla.md)|Многомерные данные, возвращаемые *результат* параметр [Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md) метод.|  
|[Результирующий набор](../../../analysis-services/xmla/xml-data-types/resultset-data-type-xmla.md)|Описывающий сам себя результирующий набор XML, возвращаемый методом **Execute** .|  
|[Функции набора строк](../../../analysis-services/xmla/xml-data-types/rowset-data-type-xmla.md)|Строки из источника данных, структурированные внедренной XML-схемой, возвращаемые методом [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md) метод.|  
|Строковые значения|Тип данных XML **string** .|  
|UnsignedInt|Тип схемы XML **unsignedInt** .|  
  
 Полные описания стандартных типов данных XML см. в соответствующей рекомендации консорциума World Wide Web (WC3).  
  
## <a name="see-also"></a>См. также:  
 [XML-элементы &#40; XML для Аналитики &#41;](http://msdn.microsoft.com/library/40ab2360-efb6-4ba6-bf23-e84964e51008)   
 [XML для аналитики &#40; XML для Аналитики &#41; Ссылка](../../../analysis-services/xmla/xml-for-analysis-xmla-reference.md)  
  
  
