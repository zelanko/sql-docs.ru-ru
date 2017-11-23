---
title: "SELECT FROM &lt;модель&gt; PREDICTION JOIN (DMX) | Документы Microsoft"
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
f1_keywords:
- PREDICTION
- PREDICTION_JOIN
- SELECT
- join
- FROM
- PREDICTION JOIN
dev_langs: DMX
helpviewer_keywords:
- prediction joins [DMX]
- PREDICTION JOIN statement
- natural prediction joins [DMX]
- open query predictions
- singleton query predictions [DMX]
- SELECT FROM <model> PREDICTION JOIN statement
ms.assetid: 7ca37fec-4a50-4d79-b1d6-1c7c12176946
caps.latest.revision: "43"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 2d8f5e26541b8d2062174f5e64eb226a4bc6843a
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="select-from-ltmodelgt-prediction-join-dmx"></a>SELECT FROM &lt;модель&gt; PREDICTION JOIN (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Использует модель интеллектуального анализа данных для прогнозирования состояний столбцов внешнего источника данных. **PREDICTION JOIN** оператор производит согласование каждого варианта исходного запроса к модели.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
SELECT [FLATTENED] [TOP <n>] <select expression list>   
FROM <model> | <sub select> [NATURAL] PREDICTION JOIN   
<source data query> [ON <join mapping list>]   
[WHERE <condition expression>]  
[ORDER BY <expression> [DESC|ASC]]  
```  
  
## <a name="arguments"></a>Аргументы  
 *n*  
 Необязательно. Целое число, указывающее количество возвращаемых строк.  
  
 *Выберите список выражений*  
 Разделенный запятыми список идентификаторов столбцов и выражений, производных от модели интеллектуального анализа данных.  
  
 *model*  
 Идентификатор модели.  
  
 *Выберите Sub*  
 Внедренная инструкция SELECT.  
  
 *запрос источника данных*  
 Исходный запрос.  
  
 *список соответствия соединения*  
 Необязательно. Логическое выражение сравнения столбцов модели со столбцами исходного запроса.  
  
 *Условное выражение*  
 Необязательно. Условие ограничения значений, возвращаемых из списка столбцов.  
  
 *expression*  
 Необязательно. Выражение, возвращающее скалярное значение.  
  
## <a name="remarks"></a>Замечания  
 Предложение ON определяет сопоставление столбцов исходного запроса со столбцами модели интеллектуального анализа данных. Такое сопоставление используется для того, чтобы направить столбцы из исходного запроса в столбцы модели интеллектуального анализа данных и чтобы при создании прогнозов можно было использовать эти столбцы в качестве входных. Столбцы в \< *списка сопоставления соединения*> соотносятся с помощью знака равенства (=), как показано в следующем примере:  
  
```  
[MiningModel].ColumnA = [source data query].Column1 AND   
[MiningModel].ColumnB = [source data query].Column2 AND  
...  
```  
  
 Привязывая вложенную таблицу в предложении ON, удостоверьтесь в том, что ключевой столбец привязан к каким-либо неключевым столбцам, чтобы алгоритм мог верно идентифицировать вариант, которому принадлежит запись вложенного столбца.  
  
 Исходный запрос для прогнозируемого соединения может представлять собой таблицу или одноэлементный запрос.  
  
 Можно указывать прогнозирующие функции, которые не возвращают табличное выражение в \< *список выражение select*> и \< *условия выражения*>.  
  
 **NATURAL PREDICTION JOIN** автоматически сопоставляет имена столбцов исходного запроса, совпадающих с именами столбцов в модели. Если вы используете **ЕСТЕСТВЕННОЕ ПРОГНОЗИРУЕМОЕ**, можно опустить предложения ON.  
  
 Условие WHERE можно применять только к прогнозируемым столбцам или к связанным столбцам.  
  
 Предложение ORDER BY может принять в качестве аргумента только один столбец, т. е. нельзя сортировать по нескольким столбцам.  
  
## <a name="example-1-singleton-query"></a>Пример 1: Одноэлементный запрос  
 В следующем примере показывается, как создать запрос, прогнозирующий вероятность приобретения указанным лицом велосипеда в реальном времени. В этом запросе данные не хранятся в таблице или в другом источнике данных; они вводятся непосредственно в запрос. Человек в запросе обладает следующими характеристиками:  
  
-   Возраст 35 лет  
  
-   Владеет домом  
  
-   Владеет двумя автомобилями  
  
-   У него дома живут двое детей  
  
 С помощью модели интеллектуального анализа данных TM-дерева принятия решений и известные характеристики субъекта, запрос возвращает логическое значение, которое описывает ли пользователь купили велосипед и набор табличных значений, возвращенных [PredictHistogram &#40; расширений интеллектуального анализа данных &#41;](../dmx/predicthistogram-dmx.md) функции, которые описывают, как был сделан прогноз.  
  
```  
SELECT  
  [TM Decision Tree].[Bike Buyer],  
  PredictHistogram([Bike Buyer])  
FROM  
  [TM Decision Tree]  
NATURAL PREDICTION JOIN  
(SELECT 35 AS [Age],  
  '5-10 Miles' AS [Commute Distance],  
  '1' AS [House Owner Flag],  
  2 AS [Number Cars Owned],  
  2 AS [Total Children]) AS t  
```  
  
## <a name="example-2-using-openquery"></a>Пример 2: Использование функции OPENQUERY  
 В следующем примере показано, как создать пакетный прогнозирующий запрос с помощью списка потенциальных клиентов, который хранится во внешнем наборе данных. Поскольку таблица является частью представление источника данных, который был определен в экземпляре [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], можно использовать запрос [OPENQUERY](../dmx/source-data-query-openquery.md) для извлечения данных. Поскольку имена столбцов таблицы отличаются от имеющихся в модели интеллектуального анализа данных, **ON** предложение должно использоваться для сопоставления столбцов в таблице со столбцами в модели.  
  
 Запрос возвращает список имен и фамилий каждого человека в таблице наряду с логическим столбцом, указывающим на вероятность покупки им велосипеда, где 0 означает «вероятно, не будет покупать велосипед», а 1 означает «вероятно, купит велосипед». Последний столбец содержит значение вероятности прогнозируемого результата.  
  
```  
SELECT  
  t.[LastName],  
  t.[FirstName],  
  [TM Decision Tree].[Bike Buyer],  
  PredictProbability([Bike Buyer])  
From  
  [TM Decision Tree]  
PREDICTION JOIN  
  OPENQUERY([Adventure Works DW Multidimensional 2012],  
    'SELECT  
      [LastName],  
      [FirstName],  
      [MaritalStatus],  
      [Gender],  
      [YearlyIncome],  
      [TotalChildren],  
      [NumberChildrenAtHome],  
      [Education],  
      [Occupation],  
      [HouseOwnerFlag],  
      [NumberCarsOwned]  
    FROM  
      [dbo].[ProspectiveBuyer]  
    ') AS t  
ON  
  [TM Decision Tree].[Marital Status] = t.[MaritalStatus] AND  
  [TM Decision Tree].[Gender] = t.[Gender] AND  
  [TM Decision Tree].[Yearly Income] = t.[YearlyIncome] AND  
  [TM Decision Tree].[Total Children] = t.[TotalChildren] AND  
  [TM Decision Tree].[Number Children At Home] = t.[NumberChildrenAtHome] AND  
  [TM Decision Tree].[Education] = t.[Education] AND  
  [TM Decision Tree].[Occupation] = t.[Occupation] AND  
  [TM Decision Tree].[House Owner Flag] = t.[HouseOwnerFlag] AND  
  [TM Decision Tree].[Number Cars Owned] = t.[NumberCarsOwned]  
```  
  
 Чтобы ограничить набор данных только теми клиентами, которые по прогнозу приобретут велосипед, а затем отсортировать список по имени клиентов, можно к предыдущему примеру добавить предложения WHERE и ORDER BY.  
  
```  
WHERE [BIKE Buyer]  
ORDER BY [LastName] ASC  
```  
  
## <a name="example-3-predicting-associations"></a>Пример 3: Прогноз взаимосвязей  
 Следующий пример показывает способ создания прогноза с помощью модели, построенной из [!INCLUDE[msCoName](../includes/msconame-md.md)] алгоритм взаимосвязей. Прогнозы на основе модели взаимосвязей можно использовать для рекомендации связанных продуктов. Например, следующий запрос возвращает три продукта, которые, скорее всего, будут приобретены вместе:  
  
-   Держатель фляги для велосипеда Mountain  
  
-   Камера шины для велосипеда Mountain  
  
-   Велосипед Mountain-200  
  
 [Predict &#40; расширений интеллектуального анализа данных &#41;](../dmx/predict-dmx.md) функция полиморфна и может использоваться со всеми типами моделей. Значение value3 используется в качестве аргумента функции, чтобы ограничить число элементов, возвращаемых запросом. **ВЫБЕРИТЕ** список, который следует за предложением NATURAL PREDICTION JOIN предоставляет значения для использования в качестве входных данных для прогноза.  
  
```  
SELECT FLATTENED  
  PREDICT([Association].[v Assoc Seq Line Items], 3)  
FROM  
  [Association]  
NATURAL PREDICTION JOIN  
(SELECT (SELECT 'Mountain Bottle Cage' AS [Model]  
  UNION SELECT 'Mountain Tire Tube' AS [Model]  
  UNION SELECT 'Mountain-200' AS [Model]) AS [v Assoc Seq Line Items ]) AS t  
```  
  
 Пример результатов:  
  
|Expression.Model|  
|----------------------|  
|Шина для велосипеда HL Mountain|  
|Фляга для воды|  
|Набор крыльев для велосипеда Mountain|  
  
 Поскольку столбец, содержащий прогнозируемый атрибут `[v Assoc Seq Line Items]`, представляет собой столбец таблицы, запрос возвращает один столбец, который содержит вложенную таблицу. По умолчанию этот столбец с вложенной таблицей имеет имя `Expression`. Если поставщик не поддерживает иерархические наборы строк, можно использовать **FLATTENED** ключевое слово, как показано в следующем примере, чтобы сделать результаты удобнее для чтения.  
  
## <a name="see-also"></a>См. также:  
 [ВЫБЕРИТЕ &#40; РАСШИРЕНИЙ ИНТЕЛЛЕКТУАЛЬНОГО АНАЛИЗА ДАННЫХ &#41;](../dmx/select-dmx.md)   
 [Расширения интеллектуального анализа данных &#40; расширений интеллектуального анализа данных &#41; Инструкции определения данных](../dmx/dmx-statements-data-definition.md)   
 [Расширения интеллектуального анализа данных &#40; расширений интеллектуального анализа данных &#41; Инструкции управления данными](../dmx/dmx-statements-data-manipulation.md)   
 [Расширения интеллектуального анализа данных &#40; расширений интеллектуального анализа данных &#41; Справка по инструкции](../dmx/data-mining-extensions-dmx-statements.md)  
  
  
