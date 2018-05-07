---
title: Свойства интеллектуального анализа данных | Документы Microsoft
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: ''
ms.topic: article
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: f3b63036a1279280a57886ea69feffaa19c29078
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="data-mining-properties"></a>Свойства интеллектуального анализа данных
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] поддерживают свойства сервера интеллектуального анализа данных, перечисленные в следующих таблицах. Дополнительные сведения о дополнительных свойствах сервера и их настройке см. в разделе [Свойства сервера в службах Analysis Services](../../analysis-services/server-properties/server-properties-in-analysis-services.md).  
  
 **Область применения:** только в многомерном режиме сервера  
  
## <a name="non-specific-category"></a>Общая категория  
 **AllowSessionMiningModels**  
 Логическое свойство, указывающее, можно ли создать модели интеллектуального анализа данных в сеансах.  
  
 Значение этого свойства по умолчанию равно false, что указывает, что модели интеллектуального анализа данных в сеансах создавать нельзя.  
  
 **AllowAdHocOpenRowsetQueries**  
 Логическое свойство, указывающее, разрешены ли специализированные запросы открытых наборов строк.  
  
 Значение этого свойства по умолчанию равно false, что указывает, что запросы открытых наборов строк не разрешены во время сеанса.  
  
 **AllowedProvidersInOpenRowset**  
 Строковое свойство, идентифицирующее, какие поставщики разрешены в открытом наборе строк, состоящее из списка идентификаторов поставщиков ProgID, разделенного запятыми/точками с запятыми, или из строки «[All]».  
  
 **MaxConcurrentPredictionQueries**  
 Свойство с 32-разрядным целочисленным значением со знаком, определяющее максимальное количество параллельных прогнозирующих запросов.  
  
## <a name="algorithms-category"></a>Категория алгоритмов  
 **Microsoft_Association_Rules\ Enabled**  
 Логическое свойство, указывающее, включен ли алгоритм Microsoft_Association_Rules.  
  
 **Microsoft_Clustering\ Enabled**  
 Логическое свойство, указывающее, включен ли алгоритм Microsoft_Clustering.  
  
 **Microsoft_Decision_Trees\ Enabled**  
 Логическое свойство, указывающее, включен ли алгоритм Microsoft_DecisionTrees.  
  
 **Microsoft_Naive_Bayes\ Enabled**  
 Логическое свойство, указывающее, включен ли алгоритм Microsoft_Naive_Bayes.  
  
 **Microsoft_Neural_Network\ Enabled**  
 Логическое свойство, указывающее, включен ли алгоритм Microsoft_Neural_Network.  
  
 **Microsoft_Sequence_Clustering\ Enabled**  
 Логическое свойство, указывающее, включен ли алгоритм Microsoft_Sequence_Clustering.  
  
 **Microsoft_Time_Series\ Enabled**  
 Логическое свойство, указывающее, включен ли алгоритм Microsoft_Time_Series.  
  
 **Microsoft_Linear_Regression\ Enabled**  
 Логическое свойство, указывающее, включен ли алгоритм Microsoft_Linear_Regression.  
  
 **Microsoft_Logistic_Regression\ Enabled**  
 Логическое свойство, указывающее, включен ли алгоритм Microsoft_Logistic_Regression.  
  
> [!NOTE]  
>  В дополнение к свойствам, которые определяют доступные службы интеллектуального анализа данных на сервере, имеются свойства интеллектуального анализа данных, определяющие поведение конкретных алгоритмов. Настройка этих свойств осуществляется при создании каждой отдельной модели интеллектуального анализа данных, а не на уровне сервера. Дополнительные сведения см. в разделе [Алгоритмы интеллектуального анализа данных (службы Analysis Services — интеллектуальный анализ данных)](../../analysis-services/data-mining/data-mining-algorithms-analysis-services-data-mining.md).  
  
## <a name="see-also"></a>См. также:  
 [Физическая архитектура (службы Analysis Services — интеллектуальный анализ данных)](../../analysis-services/data-mining/physical-architecture-analysis-services-data-mining.md)   
 [Свойства сервера в службах Analysis Services](../../analysis-services/server-properties/server-properties-in-analysis-services.md)   
 [Определение режима работы сервера экземпляра служб Analysis Services](../../analysis-services/instances/determine-the-server-mode-of-an-analysis-services-instance.md)  
  
  
