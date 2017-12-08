---
title: "Элемент (XMLA) запроса | Документы Microsoft"
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
apiname: Query Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#Query
- microsoft.xml.analysis.query
- http://schemas.microsoft.com/analysisservices/2003/engine#Query
helpviewer_keywords: Query element
ms.assetid: 5a4544e4-012f-4a47-942c-23596400ea16
caps.latest.revision: "14"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 8502824a41e2193a31e0e2b34b41e9ffb3515eaa
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="query-element-xmla"></a>Элемент Query (XML для аналитики)
  Содержит запрос в [запросы](../../../analysis-services/xmla/xml-elements-properties/queries-element-xmla.md) коллекции, используемой [DesignAggregations](../../../analysis-services/xmla/xml-elements-commands/designaggregations-element-xmla.md) команды во время оптимизации с учетом использования.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Queries>  
   ...  
   <Query>...</Query>  
   ...  
</Queries>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|Строковые значения|  
|Значение по умолчанию|None|  
|Количество элементов|0—1: необязательный элемент, который может появляться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Запросы](../../../analysis-services/xmla/xml-elements-properties/queries-element-xmla.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Замечания  
 В команде **DesignAggregations** поддержка оптимизации с учетом использования обеспечивается включением элементов **Query** в коллекцию **Queries** данной команды. Каждый элемент **Query** представляет собой целевой запрос, с помощью которого при проектировании можно определить агрегаты, охватывающие наиболее часто используемые запросы. Можно определить целевые запросы самостоятельно, или воспользуйтесь сведениями, хранящимися на экземпляре [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] в журнале запросов для получения сведений о наиболее часто используемые запросы.  
  
 При итеративном проектировании агрегатов, достаточно передачи целевых запросов в первом **DesignAggregations** команда, поскольку [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] экземпляр сохраняет целевые запросы и использует их при выполнении последующих  **DesignAggregations** команд. После передачи целевых запросов в первой команде **DesignAggregations** многократной обработки, любые последующие команды **DesignAggregations** , в свойстве **Queries** которых содержатся поисковые запросы, приведут к формированию ошибки.  
  
 Элемент **Query** содержит значение с разделителями-запятыми, включающее следующие аргументы.  
  
 *Frequency*,*Dataset*[,*Dataset*...]  
  
 *Частота*  
 Весовой коэффициент, соответствующий количеству предыдущих выполнений данного запроса. Если элемент **Query** представляет новый запрос, значение *Frequency* представляет весовой коэффициент, использованный во время проектирования в целях оценки запроса. По мере увеличения частоты, увеличивается и вес, присвоенный запросу во время проектирования.  
  
 *Набор данных*  
 Числовая строка, определяющая атрибуты измерения, включаемые в запрос. Количество символов в данной строке должно совпадать с количеством атрибутов в измерении. Ноль (0) обозначает, что атрибут, находящийся на указанной порядковой позиции, в запрос для указанного измерения не включается, тогда как единица (1) обозначает включение атрибута, находящегося на указанной порядковой позиции, в запрос для указанного измерения.  
  
 Так, например, строка «011» относится к запросу, в котором задействовано измерение с тремя атрибутами, причем в запрос включены только второй и третий атрибут.  
  
> [!NOTE]  
>  Некоторые атрибуты не рассматриваются в наборе данных. Дополнительные сведения об исключенных атрибутах см. в разделе [свойства (XMLA)](../../../analysis-services/xmla/xml-elements-properties/query-element-xmla.md).  
  
 Каждое измерение в группе мер, включающее статистическую схему, представлено значением *Dataset* в элементе **Query** . Порядок значений *Dataset* должен соответствовать порядку измерений, включенных в группу мер.  
  
## <a name="see-also"></a>См. также:  
 [Проектирование агрегатов &#40; XML для Аналитики &#41;](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/designing-aggregations-xmla.md)   
 [Свойства &#40; XML для Аналитики &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
