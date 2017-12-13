---
title: "Типы данных XML (XML для Аналитики) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
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
ms.openlocfilehash: a65065437ced53d1554ddd11035e7aa687872e9f
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/08/2017
---
# <a name="xml-data-types-xmla"></a>Типы данных XML (XML для аналитики)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]Дополнение к стандартным примитивным и производным типам рекомендации XML 1.0 XML для аналитики (XMLA) 1.1 спецификация определяет дополнительные типы данных для поддержки представления многомерных и табличных данных.  
  
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
  
  
