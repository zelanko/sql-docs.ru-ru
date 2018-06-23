---
title: Элемент (XMLA) запроса | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- Query Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#Query
- microsoft.xml.analysis.query
- http://schemas.microsoft.com/analysisservices/2003/engine#Query
helpviewer_keywords:
- Query element
ms.assetid: 5a4544e4-012f-4a47-942c-23596400ea16
caps.latest.revision: 14
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: e01c14cb889a7d2953c98d8dfeee3bb89eee344e
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36101143"
---
# <a name="query-element-xmla"></a>Элемент Query (XML для аналитики)
  Содержит запрос в [запросы](queries-element-xmla.md) коллекции, используемой [DesignAggregations](../xml-elements-commands/designaggregations-element-xmla.md) команды во время оптимизации с учетом использования.  
  
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
|Тип данных и длина|String|  
|Значение по умолчанию|None|  
|Количество элементов|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Запросы](queries-element-xmla.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 В команде `DesignAggregations` поддержка оптимизации с учетом использования обеспечивается включением элементов `Query` в коллекцию `Queries` данной команды. Каждый `Query` элемент представляет собой целевой запрос, процесс разработки можно определить агрегаты, охватывающие наиболее часто используемые запросы. Можно определить целевые запросы самостоятельно, или воспользуйтесь сведениями, хранящимися на экземпляре [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] в журнале запросов для получения сведений о наиболее часто используемые запросы.  
  
 При итеративном проектировании агрегатов, достаточно передачи целевых запросов в первом `DesignAggregations` команда, поскольку [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] экземпляр сохраняет целевые запросы и использует их при выполнении последующих `DesignAggregations` команд. После передачи целевых запросов в первой команде `DesignAggregations` многократной обработки, любые последующие команды `DesignAggregations`, в свойстве `Queries` которых содержатся поисковые запросы, приведут к формированию ошибки.  
  
 Элемент `Query` содержит значение с разделителями-запятыми, включающее следующие аргументы.  
  
 *Frequency*,*Dataset*[,*Dataset*...]  
  
 *Частота*  
 Весовой коэффициент, соответствующий количеству предыдущих выполнений данного запроса. Если `Query` элемент представляет новый запрос, *частоты* значение представляет весовой коэффициент, использованный во время проектирования в целях оценки запроса. По мере увеличения частоты, увеличивается и вес, присвоенный запросу во время проектирования.  
  
 *Набор данных*  
 Числовая строка, определяющая атрибуты измерения, включаемые в запрос. Количество символов в данной строке должно совпадать с количеством атрибутов в измерении. Ноль (0) обозначает, что атрибут, находящийся на указанной порядковой позиции, в запрос для указанного измерения не включается, тогда как единица (1) обозначает включение атрибута, находящегося на указанной порядковой позиции, в запрос для указанного измерения.  
  
 Так, например, строка «011» относится к запросу, в котором задействовано измерение с тремя атрибутами, причем в запрос включены только второй и третий атрибут.  
  
> [!NOTE]  
>  Некоторые атрибуты не рассматриваются в наборе данных. Дополнительные сведения об исключенных атрибутах см. в разделе [свойства (XMLA)](query-element-xmla.md).  
  
 Каждое измерение в группе мер, включающее статистическую схему, представленного *Dataset* значение в `Query` элемент. Порядок значений *Dataset* должен соответствовать порядку измерений, включенных в группу мер.  
  
## <a name="see-also"></a>См. также  
 [Проектирование агрегатов &#40;XML для Аналитики&#41;](../../multidimensional-models-scripting-language-assl-xmla/designing-aggregations-xmla.md)   
 [Свойства &#40;XML для Аналитики&#41;](xml-elements-properties.md)  
  
  