---
title: Содержимое элемента (ASSL) | Документы Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: e0efd6cc31b00c4029e88adab40b56aa88f50dc8
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="content-element-assl"></a>Элемент Content (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
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
  
## <a name="remarks"></a>Примечания  
 Это перечисление описывает тип содержимого, представленного столбцом структуры интеллектуального анализа данных, и может быть расширено по мере необходимости с применением поставщиков алгоритма интеллектуального анализа данных. Дополнительные сведения о типах содержимого и типах данных см. в разделе [Типы содержимого (интеллектуальный анализ данных)](../../../analysis-services/data-mining/content-types-data-mining.md).  
  
 Значения, перечисленные в следующей таблице, обычно поддерживаются всеми поставщиками алгоритма интеллектуального анализа.  
  
|Значение|Описание|  
|-----------|-----------------|  
|*Дискретные*|Столбец содержит дискретные значения.|  
|*Непрерывные*|Значения для этого столбца определяют непрерывный набор числовых данных.|  
|*Дискретизации*|Значения в этом столбце представляют группы (или сегменты) значений, полученных из непрерывного столбца.|  
|*упорядоченные*|Значения для этого столбца определяют упорядоченный набор.|  
|*Cyclical*|Значения для этого столбца определяют циклический, упорядоченный набор.|  
|*Вероятность*|Значения для этого столбца определяют вероятность для столбцов, содержащихся в [ClassifiedColumns](../../../analysis-services/scripting/collections/classifiedcolumns-element-assl.md) родителя **ScalarMiningStructureColumn**.|  
|*Variance*|Значения для этого столбца указывают дисперсию для столбцов, содержащихся в **ClassifiedColumns** родителя **ScalarMiningStructureColumn**.|  
|*StdDev*|Значения для этого столбца указывают стандартное отклонение для столбцов, содержащихся в **ClassifiedColumns** родителя **ScalarMiningStructureColumn**.|  
|*ProbabilityVariance*|Значения для этого столбца указывают дисперсию вероятности для столбцов, содержащихся в **ClassifiedColumns** родителя **ScalarMiningStructureColumn**.|  
|*ProbabilityStdDev*|Значения для этого столбца указывают стандартное отклонение вероятности для столбцов, содержащихся в **ClassifiedColumns** родителя **ScalarMiningStructureColumn**.|  
|*Поддержка*|Значения для этого столбца указывают данные поддержки для столбца, содержащегося в **ClassifiedColumns** родителя **ScalarMiningStructureColumn**.<br /><br /> Примечание: Этот столбец предоставляется как часть стандарта для сторонних поставщиков алгоритмов интеллектуального анализа данных. Корпорация Майкрософт предоставляет алгоритмы не следует использовать этот столбец.|  
|*Key*|Столбец является ключевым.<br /><br /> Примечание: Этот тип содержимого применима только к ключевым столбцам, в которой **IsKey** задан равным **True**.|  
  
 Помимо этих стандартных значений, интеллектуального анализа данных поставщиков алгоритмов, входящий в состав [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] поддерживают значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|*Сочетание клавиш*|Этот столбец является ключевым столбцом, и значения для этого столбца представляют собой последовательность событий.<br /><br /> Примечание: Этот тип содержимого применима только к ключевым столбцам, в которой **IsKey** задан равным **True**.|  
|*Ключевой столбец времени*|Этот столбец является ключевым столбцом, и значения для этого столбца представляют собой единицы измерения времени.<br /><br /> Примечание: Этот тип содержимого применима только к ключевым столбцам, в которой **IsKey** задан равным **True**.|  
|*Последовательность*|Значения для этого столбца представляют собой последовательность событий.|  
|*Time*|Значения для этого столбца представляют собой единицы измерения времени.|  
  
 Перечисление, соответствующее разрешенным значениям для **содержимого** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn>.  
  
## <a name="see-also"></a>См. также  
 [Элемент ClassifiedColumns &#40;ASSL&#41;](../../../analysis-services/scripting/collections/classifiedcolumns-element-assl.md)   
 [Свойства & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
