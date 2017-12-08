---
title: "Содержимое элемента (ASSL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: scripting
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: Content Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: Content
helpviewer_keywords: Content element
ms.assetid: 221addef-2f88-49c5-b8f5-9eee330497a9
caps.latest.revision: "43"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 98f996bf7b1b274afed0313ef326596f3e88d5f2
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="content-element-assl"></a>Элемент Content (ASSL)
  Описывает содержимое столбца в [MiningStructure](../../../analysis-services/scripting/objects/miningstructure-element-assl.md) элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<ScalarMiningStructureColumn>  
   ...  
   <Content>...</Content>  
   ...  
</ScalarMiningStructureColumn>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|String (перечисление)|  
|Значение по умолчанию|None|  
|Количество элементов|1-1: обязательный элемент, который может появляться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[ScalarMiningStructureColumn](../../../analysis-services/scripting/data-type/scalarminingstructurecolumn-data-type-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Замечания  
 Это перечисление описывает тип содержимого, представленного столбцом структуры интеллектуального анализа данных, и может быть расширено по мере необходимости с применением поставщиков алгоритма интеллектуального анализа данных. Дополнительные сведения о типах содержимого и типах данных см. в разделе [Типы содержимого (интеллектуальный анализ данных)](../../../analysis-services/data-mining/content-types-data-mining.md).  
  
 Значения, перечисленные в следующей таблице, обычно поддерживаются всеми поставщиками алгоритма интеллектуального анализа.  
  
|Значение|Description|  
|-----------|-----------------|  
|*Дискретные*|Столбец содержит дискретные значения.|  
|*Непрерывные*|Значения для этого столбца определяют непрерывный набор числовых данных.|  
|*Дискретизации*|Значения в этом столбце представляют группы (или сегменты) значений, полученных из непрерывного столбца.|  
|*Упорядоченные*|Значения для этого столбца определяют упорядоченный набор.|  
|*Cyclical*|Значения для этого столбца определяют циклический, упорядоченный набор.|  
|*Вероятность*|Значения для этого столбца определяют вероятность для столбцов, содержащихся в [ClassifiedColumns](../../../analysis-services/scripting/collections/classifiedcolumns-element-assl.md) родителя **ScalarMiningStructureColumn**.|  
|*Variance*|Значения для этого столбца указывают дисперсию для столбцов, содержащихся в **ClassifiedColumns** родителя **ScalarMiningStructureColumn**.|  
|*StdDev*|Значения для этого столбца указывают стандартное отклонение для столбцов, содержащихся в **ClassifiedColumns** родителя **ScalarMiningStructureColumn**.|  
|*ProbabilityVariance*|Значения для этого столбца указывают дисперсию вероятности для столбцов, содержащихся в **ClassifiedColumns** родителя **ScalarMiningStructureColumn**.|  
|*ProbabilityStdDev*|Значения для этого столбца указывают стандартное отклонение вероятности для столбцов, содержащихся в **ClassifiedColumns** родителя **ScalarMiningStructureColumn**.|  
|*Поддержка*|Значения для этого столбца указывают данные поддержки для столбца, содержащегося в **ClassifiedColumns** родителя **ScalarMiningStructureColumn**.<br /><br /> Примечание: Этот столбец предоставляется как часть стандарта для сторонних поставщиков алгоритмов интеллектуального анализа данных. Корпорация Майкрософт предоставляет алгоритмы не следует использовать этот столбец.|  
|*Key*|Столбец является ключевым.<br /><br /> Примечание: Этот тип содержимого применима только к ключевым столбцам, в которой **IsKey** задан равным **True**.|  
  
 Помимо этих стандартных значений, интеллектуального анализа данных поставщиков алгоритмов, входящий в состав [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] поддерживают значения, приведенные в следующей таблице.  
  
|Значение|Description|  
|-----------|-----------------|  
|*Сочетание клавиш*|Этот столбец является ключевым столбцом, и значения для этого столбца представляют собой последовательность событий.<br /><br /> Примечание: Этот тип содержимого применима только к ключевым столбцам, в которой **IsKey** задан равным **True**.|  
|*Ключевой столбец времени*|Этот столбец является ключевым столбцом, и значения для этого столбца представляют собой единицы измерения времени.<br /><br /> Примечание: Этот тип содержимого применима только к ключевым столбцам, в которой **IsKey** задан равным **True**.|  
|*Последовательность*|Значения для этого столбца представляют собой последовательность событий.|  
|*Time*|Значения для этого столбца представляют собой единицы измерения времени.|  
  
 Перечисление, соответствующее разрешенным значениям для **содержимого** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn>.  
  
## <a name="see-also"></a>См. также:  
 [Элемент ClassifiedColumns &#40; ASSL &#41;](../../../analysis-services/scripting/collections/classifiedcolumns-element-assl.md)   
 [Свойства &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
