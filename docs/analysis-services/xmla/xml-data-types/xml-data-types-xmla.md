---
title: Типы данных XML (XML для Аналитики) | Документы Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: c52717a6f061f4708b2d3e46c6d34f837b2039af
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/02/2018
ms.locfileid: "34573786"
---
# <a name="xml-data-types-xmla"></a>Типы данных XML (XML для аналитики)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  В дополнение к стандартным примитивным и производным типам, которые были определены в рекомендации XML 1.0, в спецификации XML для аналитики (XMLA) 1.1 были добавлены определения дополнительных типов данных, предназначенных для поддержки представления многомерных и табличных данных.  
  
 Типы данных, используемые XMLA, перечислены в следующей таблице.  
  
|Типы данных|Описание|  
|----------------|-----------------|  
|Логическое значение|Стандартный тип данных XML **boolean** .|  
|Decimal|Стандартный тип данных XML **decimal** .|  
|[EmptyResult](../../../analysis-services/xmla/xml-data-types/emptyresult-data-type-xmla.md)|Пространство имен элемента **root** . Это пространство имен возвращается в том случае, когда команды XML для Аналитики не возвращающие результатов, так как команда XMLA обычно не возвращающие результатов или произошла ошибка на экземпляре служб Analysis Services при выполнении команды XML для Аналитики.|  
|[EnumString](../../../analysis-services/xmla/xml-data-types/enumstring-data-type-xmla.md)|Набор именованных строковых констант для данного перечислителя.|  
|Целочисленный|Стандартный тип данных XML **int** .|  
|[MDDataSet](../../../analysis-services/xmla/xml-data-types/mddataset-data-type-xmla.md)|Многомерные данные, возвращаемые *результат* параметр [Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md) метод.|  
|[Результирующий набор](../../../analysis-services/xmla/xml-data-types/resultset-data-type-xmla.md)|Описывающий сам себя результирующий набор XML, возвращаемый методом **Execute** .|  
|[Функции набора строк](../../../analysis-services/xmla/xml-data-types/rowset-data-type-xmla.md)|Строки из источника данных, структурированные внедренной XML-схемой, возвращаемые методом [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md) метод.|  
|String|Тип данных XML **string** .|  
|UnsignedInt|Тип схемы XML **unsignedInt** .|  
  
 Полные описания стандартных типов данных XML см. в соответствующей рекомендации консорциума World Wide Web (WC3).  
  
## <a name="see-also"></a>См. также
 [XML-элементы &#40;XML для Аналитики&#41;](http://msdn.microsoft.com/library/40ab2360-efb6-4ba6-bf23-e84964e51008)   
 [XML для аналитики &#40;XMLA&#41; ссылки](../../../analysis-services/xmla/xml-for-analysis-xmla-reference.md)  
  
  
