---
title: "Общие функции прогнозирования (расширения интеллектуального анализа данных) | Документы Microsoft"
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- DMX
helpviewer_keywords:
- DMX [Analysis Services], functions
- mapping functions to query types [DMX]
- DMX [Analysis Services], prediction queries
- prediction queries [DMX]
- SELECT statement [DMX]
- Data Mining Extensions [Analysis Services], functions
- Data Mining Extensions [Analysis Services], prediction queries
ms.assetid: e128159a-0458-43c9-bfe9-129cb6cfbe1c
caps.latest.revision: 48
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: f63573a32882c40619e28666e2a251794c121621
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="general-prediction-functions-dmx"></a>Общие функции прогнозирования (расширения интеллектуального анализа данных)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Можно использовать **ВЫБЕРИТЕ** инструкции в расширений интеллектуального анализа (DMX) для создания различных типов запросов. С помощью запроса можно получить сведения о самой модели интеллектуального анализа данных, сделать новый прогноз или изменить модель путем обучения ее с помощью новых данных. [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]предоставляет разнообразные специализированные функции, управляющие типом сведений, возвращаемых в запросе. Добавив эти функции к DMX-запросу, можно получить дополнительную статистику или столбцы данных. Однако каждый тип запроса и каждый тип модели поддерживает только определенные функции.  
  
## <a name="common-functions"></a>Общие функции  
 Можно использовать функции для расширения результатов, возвращаемых моделью интеллектуального анализа данных. Следующие функции можно использовать для любых **ВЫБЕРИТЕ** инструкции, возвращающей табличное выражение:  
  
|||  
|-|-|  
|[BottomCount &#40; расширений интеллектуального анализа данных &#41;](../dmx/bottomcount-dmx.md)|[RangeMin &#40; расширений интеллектуального анализа данных &#41;](../dmx/rangemin-dmx.md)|  
|[BottomPercent &#40; расширений интеллектуального анализа данных &#41;](../dmx/bottompercent-dmx.md)|[TopCount &#40; расширений интеллектуального анализа данных &#41;](../dmx/topcount-dmx.md)|  
|[Прогноз &#40; расширений интеллектуального анализа данных &#41;](../dmx/predict-dmx.md)|[TopPercent &#40; расширений интеллектуального анализа данных &#41;](../dmx/toppercent-dmx.md)|  
|[RangeMax &#40; расширений интеллектуального анализа данных &#41;](../dmx/rangemax-dmx.md)|[TopSum &#40; расширений интеллектуального анализа данных &#41;](../dmx/topsum-dmx.md)|  
|[RangeMid &#40; расширений интеллектуального анализа данных &#41;](../dmx/rangemid-dmx.md)||  
  
 Кроме того, следующие функции поддерживаются почти всеми типами моделей.  
  
-   [Существует &#40; расширений интеллектуального анализа данных &#41;](../dmx/exists-dmx.md)  
  
-   [IsDescendant &#40; расширений интеллектуального анализа данных &#41;](../dmx/isdescendant-dmx.md)  
  
-   [IsTestCase &#40; расширений интеллектуального анализа данных &#41;](../dmx/istestcase-dmx.md)  
  
-   [IsTrainingCase &#40; расширений интеллектуального анализа данных &#41;](../dmx/istrainingcase-dmx.md)  
  
-   [Прогноз &#40; расширений интеллектуального анализа данных &#41;](../dmx/predict-dmx.md)  
  
-   [RangeMax &#40; расширений интеллектуального анализа данных &#41;](../dmx/rangemax-dmx.md)  
  
-   [RangeMid &#40; расширений интеллектуального анализа данных &#41;](../dmx/rangemid-dmx.md)  
  
-   [RangeMin &#40; расширений интеллектуального анализа данных &#41;](../dmx/rangemin-dmx.md)  
  
-   [StructureColumn &#40; расширений интеллектуального анализа данных &#41;](../dmx/structurecolumn-dmx.md)  
  
 Отдельные алгоритмы могут поддерживать дополнительные функции. Список функций, которые поддерживаются для всех типов моделей см. в разделе [запросов интеллектуального анализа данных](../analysis-services/data-mining/data-mining-queries.md).  
  
## <a name="functions-specific-to-select-syntax"></a>Функции, специфичные для инструкции SELECT  
 В следующей таблице перечислены функции, которые можно использовать для каждого типа **ВЫБЕРИТЕ** инструкции.  
  
 Общие сведения о функциях в расширениях интеллектуального анализа данных см. в разделе [расширений интеллектуального анализа данных &#40; расширений интеллектуального анализа данных &#41; Функция ссылка](../dmx/data-mining-extensions-dmx-function-reference.md).  
  
|Тип запроса|Поддерживаемые функции|Замечания|  
|----------------|-------------------------|-------------|  
|[SELECT DISTINCT FROM \<модели >](../dmx/select-distinct-from-model-dmx.md)|[RangeMin &#40; расширений интеллектуального анализа данных &#41;](../dmx/rangemin-dmx.md)<br /><br /> [RangeMid &#40; расширений интеллектуального анализа данных &#41;](../dmx/rangemid-dmx.md)<br /><br /> [RangeMax &#40; расширений интеллектуального анализа данных &#41;](../dmx/rangemax-dmx.md)|Эти функции используются для получения максимальных, минимальных и средних значений столбцов с числовыми данными любого типа — как непрерывными, так и дискретизированными.|  
|[SELECT FROM \<модели >. СОДЕРЖИМОЕ](../dmx/select-from-model-content-dmx.md)<br /><br /> либо<br /><br /> [SELECT FROM \<модели >. DIMENSION_CONTENT](../dmx/select-from-model-dimension-content-dmx.md)|[IsDescendant &#40; расширений интеллектуального анализа данных &#41;](../dmx/isdescendant-dmx.md)|Эта функция получает дочерние узлы указанного узла модели. Ее можно использовать, например, для просмотра всех узлов содержимого модели интеллектуального анализа данных. Порядок узлов в модели интеллектуального анализа данных зависит от типа модели. Сведения о структуре для каждого типа модели интеллектуального анализа данных см. в разделе [содержимое модели интеллектуального анализа данных &#40; Службы Analysis Services — Интеллектуальный анализ данных &#41; ](../analysis-services/data-mining/mining-model-content-analysis-services-data-mining.md).<br /><br /> Если содержимое модели интеллектуального анализа данных сохранено в виде измерения, можно использовать также другие существующие функции многомерных выражений (MDX) для запросов к иерархии атрибутов.|  
|[SELECT FROM \<модели >. ВАРИАНТЫ](../dmx/select-from-model-cases-dmx.md)|[IsInNode &#40; расширений интеллектуального анализа данных &#41;](../dmx/isinnode-dmx.md)<br /><br /> [Класс ClientSettingsGeneralFlag](../relational-databases/wmi-provider-configuration-classes/clientsettingsgeneralflag-class/clientsettingsgeneralflag-class.md)<br /><br /> [IsTrainingCase &#40; расширений интеллектуального анализа данных &#41;](../dmx/istrainingcase-dmx.md)<br /><br /> [IsTestCase &#40; расширений интеллектуального анализа данных &#41;](../dmx/istestcase-dmx.md)|Функция Lag поддерживается только для модели временных рядов.<br /><br /> Функция IsTestCase поддерживается в модели, основанные на структуре, который был создан с параметром контрольных данных, чтобы создать набор проверочных данных. Если для структуры, на которой основана модель, не был создан набор проверочных данных с помощью параметров контрольных данных, все варианты считаются обучающими.|  
|[SELECT FROM \<модели >. SAMPLE_CASES](../dmx/select-from-model-sample-cases-dmx.md)|[IsInNode &#40; расширений интеллектуального анализа данных &#41;](../dmx/isinnode-dmx.md)|В этом контексте Функция IsInNode возвращает вариант, принадлежащий множеству идеализированных вариантов-образцов.|  
|SELECT FROM \<модели >. PMML|Неприменимо. Используйте вместо этого функции запросов XML.|Представления языка разметки прогнозирующей модели (PMML) поддерживаются только для следующих типов моделей:<br /><br /> алгоритм дерева принятия решений ([!INCLUDE[msCoName](../includes/msconame-md.md)]);<br /><br /> алгоритм кластеризации ([!INCLUDE[msCoName](../includes/msconame-md.md)]);|  
|[SELECT FROM \<модель > PREDICTION JOIN](../dmx/select-from-model-prediction-join-dmx.md)|Функции прогноза, характерные для алгоритма, который используется для построения модели.|Список прогнозирующих функций для каждого типа модели см. в разделе [запросов интеллектуального анализа данных](../analysis-services/data-mining/data-mining-queries.md).|  
|[SELECT FROM \<модели >](../dmx/select-from-model-dmx.md)|Функции прогноза, характерные для алгоритма, который используется для построения модели.|Список прогнозирующих функций для каждого типа модели см. в разделе [запросов интеллектуального анализа данных](../analysis-services/data-mining/data-mining-queries.md).|  
  
## <a name="see-also"></a>См. также:  
 [Расширения интеллектуального анализа данных &#40; расширений интеллектуального анализа данных &#41; Ссылка](../dmx/data-mining-extensions-dmx-reference.md)   
 [Расширения интеллектуального анализа данных &#40; расширений интеллектуального анализа данных &#41; Справочник по функциям](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Расширения интеллектуального анализа данных &#40; расширений интеллектуального анализа данных &#41; Справочник по операторам](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Расширения интеллектуального анализа данных &#40; расширений интеллектуального анализа данных &#41; Справка по инструкции](../dmx/data-mining-extensions-dmx-statements.md)   
 [Расширения интеллектуального анализа данных &#40; расширений интеллектуального анализа данных &#41; Синтаксические обозначения](../dmx/data-mining-extensions-dmx-syntax-conventions.md)   
 [Расширения интеллектуального анализа данных &#40; расширений интеллектуального анализа данных &#41; Элементы синтаксиса](../dmx/data-mining-extensions-dmx-syntax-elements.md)   
 [Структура и использовании прогнозирующих запросов расширений интеллектуального анализа данных](../dmx/structure-and-usage-of-dmx-prediction-queries.md)   
 [Основные сведения об инструкции расширений интеллектуального анализа данных Select](../dmx/understanding-the-dmx-select-statement.md)  
  
  

