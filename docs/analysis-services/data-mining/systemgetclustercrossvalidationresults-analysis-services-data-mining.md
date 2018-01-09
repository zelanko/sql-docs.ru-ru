---
title: "Хранимая процедура SystemGetClusterCrossValidationResults (службы Analysis Services — Интеллектуальный анализ данных) | Документы Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- SystemGetClusterCrossValidationResults
- stored procedures [Analysis Services], data mining
- cross-validation [data mining]
ms.assetid: 79de9b81-9f2e-4f20-ace9-e3b19d6a9759
caps.latest.revision: "21"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: fdd5623be105cba70aa9404aba2c4d87cd0574cc
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="systemgetclustercrossvalidationresults-analysis-services---data-mining"></a>Хранимая процедура SystemGetClusterCrossValidationResults (службы Analysis Services — интеллектуальный анализ данных)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]Секций, структуры интеллектуального анализа данных в указанное число разрезов, обучает модель для каждой секции, а затем возвращает метрики точности для каждой секции.  
  
 **Примечание** .   Эта хранимая процедура может использоваться только со структурой интеллектуального анализа, содержащей по крайней мере одну модель кластеризации. Для перекрестной проверки некластеризованных моделей используется [SystemGetCrossValidationResults (службы Analysis Services — интеллектуальный анализ данных)](../../analysis-services/data-mining/systemgetcrossvalidationresults-analysis-services-data-mining.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
SystemGetClusterCrossValidationResults(  
<structure name>,   
[,<mining model list>]  
,<fold count>}  
,<max cases>  
<test list>])  
```  
  
## <a name="arguments"></a>Аргументы  
 *структура интеллектуального анализа данных*  
 Имя структуры интеллектуального анализа данных в текущей базе данных.  
  
 (обязательно)  
  
 *список моделей интеллектуального анализа данных*  
 Список моделей интеллектуального анализа данных для проверки с разделителями-запятыми.  
  
 Если не указан список моделей интеллектуального анализа, перекрестная проверка выполняется в отношении всех моделей кластеризации, связанных с заданной структурой интеллектуального анализа.  
  
> [!NOTE]  
>  Для перекрестной проверки моделей, не являющихся моделями кластеризации, необходимо использовать отдельную хранимую процедуру [SystemGetCrossValidationResults (службы Analysis Services — интеллектуальный анализ данных)](../../analysis-services/data-mining/systemgetcrossvalidationresults-analysis-services-data-mining.md).  
  
 (необязательно).  
  
 *количество сверток*  
 Целое число, указывающее количество секций, на которое разделяется набор данных. Минимальное значение — 2. Максимальное число сверток равно минимальному из следующих двух значений — **maximum integer** и количество вариантов.  
  
 Каждая секция будет содержать примерно следующее количество вариантов: *максимальное количество вариантов*/*количество сверток*.  
  
 Значение по умолчанию отсутствует.  
  
> [!NOTE]  
>  Количество сверток оказывает существенное влияние на время, необходимое для перекрестной проверки. Если выбрать слишком большое количество сверток, запрос может выполняться очень долго, а в некоторых случаях сервер может стать недоступным или превысить лимит времени ожидания.  
  
 (обязательно)  
  
 *максимальное количество вариантов*  
 Целое число, определяющее максимальное количество вариантов, которые можно проверять.  
  
 Значение 0 показывает, что будут использоваться все варианты в источнике данных.  
  
 Если указано число, превышающее фактическое количество вариантов в наборе данных, будут использоваться все варианты в источнике данных.  
  
 (обязательно)  
  
 *список тестирования*  
 Строка, указывающая параметры тестирования.  
  
 **Примечание.** Этот параметр зарезервирован для использования в будущем.  
  
 (необязательно).  
  
## <a name="return-type"></a>Тип возвращаемых данных  
 Таблица возвращаемых типов содержит оценки каждой отдельной секции и статистических функций для всех моделей.  
  
 В следующей таблице приводятся описания возвращаемых столбцов.  
  
|Имя столбца|Description|  
|-----------------|-----------------|  
|ModelName|Имя протестированной модели.|  
|AttributeName|Имя прогнозируемого столбца. Для кластерных моделей всегда имеет значение **null**.|  
|AttributeState|Заданное целевое значение в прогнозируемом столбце. Для кластерных моделей всегда имеет значение **null.**|  
|PartitionIndex|Начинающийся с 1 индекс, определяющий, к какой секции применяются результаты.|  
|PartitionSize|Целое число, показывающее, сколько вариантов было включено в каждую секцию.|  
|Тест|Тип выполненного теста.|  
|Measure|Имя меры, возвращенной тестом. Меры для каждой модели зависят от типа прогнозируемого значения. Определение каждой меры см. в разделе [Перекрестная проверка (службы Analysis Services — интеллектуальный анализ данных)](../../analysis-services/data-mining/cross-validation-analysis-services-data-mining.md).<br /><br /> Список мер, возвращаемых для каждого прогнозируемого типа, см. в разделе [Меры в отчете перекрестной проверки](../../analysis-services/data-mining/measures-in-the-cross-validation-report.md).|  
|Значение|Значение указанной проверочной меры.|  
  
## <a name="remarks"></a>Remarks  
 Для возвращения показателей точности для всего набора данных используется [SystemGetClusterAccuracyResults (службы Analysis Services — интеллектуальный анализ данных)](../../analysis-services/data-mining/systemgetclusteraccuracyresults-analysis-services-data-mining.md).  
  
 Кроме того, если модель интеллектуального анализа данных уже секционирована на свертки, можно обойти обработку и возвратить только результаты перекрестной проверки с помощью [SystemGetClusterAccuracyResults (службы Analysis Services — интеллектуальный анализ данных)](../../analysis-services/data-mining/systemgetclusteraccuracyresults-analysis-services-data-mining.md).  
  
## <a name="examples"></a>Примеры  
 В следующем примере показано, как секционировать структуру интеллектуального анализа на три свертки, и далее проводится проверка двух моделей кластеризации, связанных с этой структурой интеллектуального анализа.  
  
 В третьей строке кода приведен список моделей интеллектуального анализа, предназначенных для проверки. Если не задать список, будут использоваться все модели кластеризации, связанные с этой структурой.  
  
 В четвертой строке кода задано количество сверток, а на пятой – максимальное число вариантов.  
  
 Поскольку это модели кластеризации, не обязательно указывать прогнозируемый атрибут или значение.  
  
```  
CALL SystemGetClusterCrossValidationResults(  
[v Target Mail],  
[Cluster 1], [Cluster 2],  
3,  
10000  
)  
```  
  
 Образец результатов.  
  
|ModelName|AttributeName|AttributeState|PartitionIndex|PartitionSize|Тест|Мера|Значение|  
|---------------|-------------------|--------------------|--------------------|-------------------|----------|-------------|-----------|  
|Кластер 1|||1|3025|Кластеризация|Вероятность варианта|0.930524511864121|  
|Кластер 1|||2|3025|Кластеризация|Вероятность варианта|0.919184178430778|  
|Кластер 1|||3|3024|Кластеризация|Вероятность варианта|0.929651120490248|  
|Кластер 2|||1|1289|Кластеризация|Вероятность варианта|0.922789726933607|  
|Кластер 2|||2|1288|Кластеризация|Вероятность варианта|0.934865535691068|  
|Кластер 2|||3|1288|Кластеризация|Вероятность варианта|0.924724595688798|  
  
## <a name="requirements"></a>Требования  
 Перекрестная проверка доступна только в версиях [!INCLUDE[ssEnterprise](../../includes/ssenterprise-md.md)] , начиная с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)].  
  
## <a name="see-also"></a>См. также:  
 [SystemGetCrossValidationResults (службы Analysis Services — интеллектуальный анализ данных)](../../analysis-services/data-mining/systemgetcrossvalidationresults-analysis-services-data-mining.md)   
 [SystemGetAccuracyResults &#40; Службы Analysis Services — Интеллектуальный анализ данных &#41;](../../analysis-services/data-mining/systemgetaccuracyresults-analysis-services-data-mining.md)   
 [Хранимая процедура SystemGetClusterCrossValidationResults](../../analysis-services/data-mining/systemgetclustercrossvalidationresults-analysis-services-data-mining.md)   
 [SystemGetClusterAccuracyResults (службы Analysis Services — интеллектуальный анализ данных)](../../analysis-services/data-mining/systemgetclusteraccuracyresults-analysis-services-data-mining.md)  
  
  
