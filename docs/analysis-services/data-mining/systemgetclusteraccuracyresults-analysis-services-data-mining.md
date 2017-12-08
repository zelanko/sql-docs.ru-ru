---
title: "Метод SystemGetClusterAccuracyResults (службы Analysis Services — Интеллектуальный анализ данных) | Документы Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: sql
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- stored procedures [Analysis Services], data mining
- SystemGetClusterAccuracyResults
- cross-validation [data mining]
ms.assetid: e1701738-50d5-46b4-b406-f1e800545abb
caps.latest.revision: "18"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 592500d3ab749c6ba07a82b0ff650dc7ff282dc1
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="systemgetclusteraccuracyresults-analysis-services---data-mining"></a>Метод SystemGetClusterAccuracyResults (службы Analysis Services — интеллектуальный анализ данных)
  Возвращает показатели точности перекрестной проверки для структуры интеллектуального анализа и связанных с ней моделей кластеризации.  
  
 Эта хранимая процедура возвращает показатели для всего набора данных как единой секции. Чтобы выполнить секционирование набора данных на перекрестные разделы и вернуть метрики для каждой секции, используйте [SystemGetClusterCrossValidationResults (службы Analysis Services — интеллектуальный анализ данных)](../../analysis-services/data-mining/systemgetclustercrossvalidationresults-analysis-services-data-mining.md).  
  
> [!NOTE]  
>  Эта хранимая процедура работает только с моделями кластеризации. Для некластеризованных моделей используется [SystemGetAccuracyResults (службы Analysis Services — интеллектуальный анализ данных)](../../analysis-services/data-mining/systemgetaccuracyresults-analysis-services-data-mining.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
SystemGetClusterAccuracyResults(  
<mining structure>   
[,<mining model list>]  
,<data set>  
,<test list>])  
```  
  
## <a name="arguments"></a>Аргументы  
 *структура интеллектуального анализа данных*  
 Имя структуры интеллектуального анализа данных в текущей базе данных.  
  
 (обязательно)  
  
 *список моделей интеллектуального анализа данных*  
 Список моделей для проверки с разделителями-запятыми.  
  
 По умолчанию значение **null**, означающее, что используются все применимые модели. При использовании значения по умолчанию некластеризованные модели автоматически исключаются из списка обработки.  
  
 (необязательно)  
  
 *набор данных*  
 Целочисленное значение, указывающее, что секция в структуре интеллектуального анализа должна использоваться для тестирования. Это значение получается из битовой маски, которая представляет сумму следующих значений, каждое из которых в отдельности является необязательным:  
  
|||  
|-|-|  
|Обучающие варианты|0x0001|  
|Проверочные варианты|0x0002|  
|Фильтр модели|0x0004|  
  
 Полный список возможных значений см. в подразделе «Примечания» этого раздела.  
  
 (обязательно)  
  
 *список тестирования*  
 Строка, указывающая параметры тестирования. Этот параметр зарезервирован для использования в будущем.  
  
 (необязательно)  
  
## <a name="return-type"></a>Тип возвращаемых данных  
 Таблица, содержащая оценки каждой отдельной секции и статистических функций для всех моделей.  
  
 Следующая таблица содержит список столбцов, возвращаемых методом **SystemGetClusterAccuracyResults**. Дополнительные сведения об интерпретации сведений, возвращаемых этой хранимой процедурой, см. в разделе [Меры в отчете перекрестной проверки](../../analysis-services/data-mining/measures-in-the-cross-validation-report.md).  
  
|Имя столбца|Description|  
|-----------------|-----------------|  
|ModelName|Имя протестированной модели. Значение**Все** указывает, что результат представляет собой статистическое выражение, полученное для всех моделей.|  
|AttributeName|Неприменимо к моделям кластеризации.|  
|AttributeState|Неприменимо к моделям кластеризации.|  
|PartitionIndex|Число, указывающее секцию.<br /><br /> Для этой хранимой процедуры оно всегда будет равно 0.|  
|PartitionCases|Целое число, указывающее количество проверенных вариантов.|  
|Тест|Тип выполненного теста.|  
|Measure|Имя меры, возвращенной тестом. Меры для каждой модели зависят от типа модели и типа прогнозируемого значения.<br /><br /> Список мер, возвращаемых для каждого прогнозируемого типа, см. в разделе [Меры в отчете перекрестной проверки](../../analysis-services/data-mining/measures-in-the-cross-validation-report.md).<br /><br /> Определение каждой меры см. в разделе [Перекрестная проверка (службы Analysis Services — интеллектуальный анализ данных)](../../analysis-services/data-mining/cross-validation-analysis-services-data-mining.md).|  
|Значение|Оценка вероятности, указывающая вероятность кластерного варианта.|  
  
## <a name="remarks"></a>Замечания  
 В следующей таблице приводятся примеры значений, с помощью которых можно указать в структуре интеллектуального анализа данные, используемые для перекрестной проверки. Если для перекрестной проверки нужно использовать проверочные варианты, то структура интеллектуального анализа данных должна содержать набор проверочных данных. Сведения о том, как определить набор проверочных данных во время создания структуры интеллектуального анализа данных, см. в разделе [Обучающие и проверочные наборы данных](../../analysis-services/data-mining/training-and-testing-data-sets.md).  
  
|Целое значение|Description|  
|-------------------|-----------------|  
|1|Используются только обучающие варианты.|  
|2|Используются только проверочные варианты.|  
|3|Используются и обучающие и проверочные варианты.|  
|4|Недопустимое сочетание.|  
|5|Используются только обучающие варианты, и применяется фильтр модели.|  
|6|Используются только проверочные варианты, и применяется фильтр модели.|  
|7|Используются и обучающие и проверочные варианты, и применяется фильтр модели.|  
  
 Дополнительные сведения о сценариях, в которых применяется перекрестная проверка, см. в разделе [Тестирование и проверка (интеллектуальный анализ данных)](../../analysis-services/data-mining/testing-and-validation-data-mining.md).  
  
## <a name="examples"></a>Примеры  
 Этот пример возвращает меры точности для двух моделей кластеризации, `Cluster 1` и `Cluster 2`, которые связаны со структурой интеллектуального анализа vTargetMail. Код в четвертой строке указывает, что результаты должны быть основаны только на проверке вариантов, без использования фильтров, которые могут быть связаны с каждой моделью.  
  
```  
CALL SystemGetClusterAccuracyResults (  
[vTargetMail],  
[Cluster 1], [Cluster 2],  
2  
)  
```  
  
 Образец результатов:  
  
|ModelName|AttributeName|AttributeState|PartitionIndex|PartitionSize|Тест|Measure|Значение|  
|---------------|-------------------|--------------------|--------------------|-------------------|----------|-------------|-----------|  
|Кластер 1|||0|5545|Кластеризация|Вероятность варианта|0.796514342249313|  
|Кластер 2|||0|5545|Кластеризация|Вероятность варианта|0.732122471228572|  
  
## <a name="requirements"></a>Требования  
 Перекрестная проверка доступна только в версиях [!INCLUDE[ssEnterprise](../../includes/ssenterprise-md.md)] , начиная с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)].  
  
## <a name="see-also"></a>См. также  
 [SystemGetCrossValidationResults (службы Analysis Services — интеллектуальный анализ данных)](../../analysis-services/data-mining/systemgetcrossvalidationresults-analysis-services-data-mining.md)   
 [SystemGetAccuracyResults &#40; Службы Analysis Services — Интеллектуальный анализ данных &#41;](../../analysis-services/data-mining/systemgetaccuracyresults-analysis-services-data-mining.md)   
 [Хранимая процедура SystemGetClusterCrossValidationResults &#40; Службы Analysis Services — Интеллектуальный анализ данных &#41;](../../analysis-services/data-mining/systemgetclustercrossvalidationresults-analysis-services-data-mining.md)   
 [SystemClusterGetAccuracyResults](../../analysis-services/data-mining/systemgetclusteraccuracyresults-analysis-services-data-mining.md)  
  
  
