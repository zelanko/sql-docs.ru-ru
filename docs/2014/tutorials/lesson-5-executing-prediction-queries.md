---
title: 'Занятие 5: Выполнение прогнозирующих запросов | Документы Microsoft'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0037bd2f-aa2d-464b-bf86-b0210f0438b1
caps.latest.revision: 25
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 91fd3e41ce0a1055a0f5babe4eb3234bc1ff03bd
ms.sourcegitcommit: 8c040e5b4e8c7d37ca295679410770a1af4d2e1f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/21/2018
ms.locfileid: "36312942"
---
# <a name="lesson-5-executing-prediction-queries"></a>Занятие 5: Выполнение прогнозирующих запросов
  На этом занятии будет использоваться [SELECT FROM \<модель > PREDICTION JOIN (DMX)](/sql/dmx/select-from-model-cases-dmx) форма инструкции SELECT для создания двух различных типов прогнозов, основанных на дереве принятия решений модели, которую вы создали в [ Занятие 2: Добавление моделей интеллектуального анализа к структуре интеллектуального анализа взаимосвязей](../../2014/tutorials/lesson-2-adding-mining-models-to-the-market-basket-mining-structure.md). Эти типы прогнозов определены ниже.  
  
 Одноэлементный запрос  
 Одноэлементный запрос используется для получения произвольно выбранных значений в процессе прогнозирования. Например, можно определить, какова вероятность, что данный клиент купит велосипед. Для этого в запрос передаются такие величины, как расстояние от дома до работы покупателя, его почтовый индекс или, например, количество его детей. Одноэлементный запрос возвращает вероятность приобретения данным покупателем велосипеда, рассчитанную на основании введенных величин.  
  
 Пакетный запрос  
 Пакетный запрос используется для определения, кто из потенциальных клиентов, представленных в таблице, приобретет велосипед. Например, если отдел маркетинга предоставит список клиентов и их атрибутов, то пакетный прогноз используется для предсказания, кто из клиентов, представленных в списке, с наибольшей вероятностью приобретет велосипед.  
  
 [SELECT FROM \<модель > PREDICTION JOIN (DMX)](/sql/dmx/select-from-model-cases-dmx) форма инструкции SELECT содержит три части:  
  
-   Список столбцов модели интеллектуального анализа данных и прогнозирующих функций, которые возвращаются в результатах. Результаты также могут содержать входные столбцы источника данных.  
  
-   Запрос-источник, определяющий данные, которые используются при создании прогноза. Например, в пакетном запросе это может быть список клиентов.  
  
-   Сопоставление столбцов модели интеллектуального анализа данных с исходными данными. При совпадении этих имен можно использовать синтаксис NATURAL и пропустить процесс сопоставления столбцов.  
  
 Запрос можно расширить функциями прогнозирования. Функции прогнозирования предоставляют дополнительные сведения, например вероятность реализации прогноза, и обеспечивают поддержку прогноза в учебном наборе данных. Дополнительные сведения о функциях прогнозирования см. в разделе [функции &#40;расширений интеллектуального анализа данных&#41;](/sql/dmx/functions-dmx).  
  
 Прогнозы в этом учебнике основаны на таблице ProspectiveBuyer из образца базы данных [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)]. Таблица ProspectiveBuyer содержит список потенциальных клиентов и их характеристики. Клиенты, представленные в этой таблице, не зависят от клиентов, использовавшихся для создания дерева модели интеллектуального анализа данных.  
  
 Прогнозы можно также создавать, используя построитель прогнозирующих запросов в среде [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].  
  
## <a name="lesson-tasks"></a>Задачи занятия  
 На этом занятии будут выполнены следующие задачи.  
  
-   Создание одноэлементного запроса для определения вероятности покупки велосипеда конкретным клиентом.  
  
-   Пакетный запрос используется для определения того, кто из клиентов, представленных в таблице, приобретет велосипед.  
  
## <a name="singleton-query"></a>Одноэлементный запрос  
 Первый шаг заключается в использовании [SELECT FROM &#60;модель&#62; PREDICTION JOIN &#40;расширений интеллектуального анализа данных&#41; ](/sql/dmx/select-from-model-cases-dmx) в Одноэлементный прогнозирующий запрос. В следующем фрагменте показан общий пример одноэлементной инструкции:  
  
```  
SELECT <select list> FROM [<mining model name>]   
NATURAL PREDICTION JOIN  
(SELECT '<value>' AS [<column>], ...)  
AS [<input alias>]  
```  
  
 В первой строке кода определяются столбцы модели интеллектуального анализа данных, которые возвращает запрос, а также указывается имя модели интеллектуального анализа данных, которая использовалась для создания прогноза:  
  
```  
SELECT <select list> FROM [<mining model name>]   
```  
  
 В следующей строке определяются характеристики клиента, использованного в прогнозе:  
  
```  
NATURAL PREDICTION JOIN  
(SELECT '<value>' AS [<column>], ...)  
AS [<input alias>]  
ORDER BY <expression>  
```  
  
 Если задана инструкция NATURAL PREDICTION JOIN, сервер сопоставляет каждый столбец из модели интеллектуального анализа данных входному столбцу по имени. Если имена столбцов не совпадают, эти столбцы пропускаются.  
  
#### <a name="to-create-a-singleton-prediction-query"></a>Создание одноэлементного прогнозирующего запроса  
  
1.  В **обозревателя объектов**, щелкните правой кнопкой мыши экземпляр [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], пункты **новый запрос**, а затем нажмите кнопку **расширений интеллектуального анализа данных**.  
  
     Откроется редактор запросов, содержащий новый, пустой запрос.  
  
2.  Скопируйте общий пример одноэлементной инструкции в пустой запрос.  
  
3.  Вместо  
  
    ```  
    <select list>   
    ```  
  
     вставьте  
  
    ```  
    [Bike Buyer] AS Buyer, PredictHistogram([Bike Buyer]) AS Statistics  
    ```  
  
     Инструкция AS используется для создания псевдонимов столбцов, которые возвращает запрос. [PredictHistogram](/sql/dmx/predicthistogram-dmx) функция возвращает статистические данные прогноза, включая вероятность и поддержку. Дополнительные сведения о функциях, которые можно использовать в инструкции прогноза см. в разделе [функции &#40;расширений интеллектуального анализа данных&#41;](/sql/dmx/functions-dmx).  
  
4.  Вместо  
  
    ```  
    [<mining model>]   
    ```  
  
     вставьте  
  
    ```  
    [Decision Tree]  
    ```  
  
5.  Вместо  
  
    ```  
    (SELECT '<value>' AS [<column name>], ...)  AS t  
    ```  
  
     вставьте  
  
    ```  
    (SELECT 35 AS [Age],  
      '5-10 Miles' AS [Commute Distance],  
      '1' AS [House Owner Flag],  
      2 AS [Number Cars Owned],  
      2 AS [Total Children]) AS t  
    ```  
  
     Полная инструкция теперь должна выглядеть следующим образом.  
  
    ```  
    SELECT  
       [Bike Buyer] AS Buyer,  
       PredictHistogram([Bike Buyer]) AS Statistics  
    FROM  
       [Decision Tree]  
    NATURAL PREDICTION JOIN  
    (SELECT 35 AS [Age],  
       '5-10 Miles' AS [Commute Distance],  
       '1' AS [House Owner Flag],  
       2 AS [Number Cars Owned],  
       2 AS [Total Children]) AS t  
    ```  
  
6.  В меню **Файл** щелкните **Сохранить DMXQuery1.dmx как**.  
  
7.  В **Сохранить как** диалоговое окно, перейдите к соответствующей папке и присвойте файлу имя `Singleton_Query.dmx`.  
  
8.  На панели инструментов нажмите кнопку **Выполнить** .  
  
     Запрос возвращает прогноз, купит ли клиент с заданными характеристиками велосипед, а также статистические данные прогноза.  
  
## <a name="batch-query"></a>Пакетный запрос  
 Следующий шаг заключается в использовании [SELECT FROM &#60;модель&#62; PREDICTION JOIN &#40;расширений интеллектуального анализа данных&#41; ](/sql/dmx/select-from-model-cases-dmx) в пакетном прогнозирующем запросе. Ниже представлен общий пример пакетной инструкции:  
  
```  
SELECT TOP <number> <select list>   
FROM [<mining model name>]  
PREDICTION JOIN  
OPENQUERY([<datasource>],'<SELECT statement>')  
  AS [<input alias>]  
ON <on clause, mapping,>  
WHERE <where clause, boolean expression,>  
ORDER BY <expression>  
```  
  
 Как и в одноэлементном запросе, первые две строки кода определяют столбцы из модели интеллектуального анализа, которые возвращает запрос, а также имя модели интеллектуального анализа данных, которая используется для создания прогноза. Начало \<номер > инструкция указывает, что запрос будет возвращать только числа или результатов, заданное параметром \<число >.  
  
 Следующие строки кода определяют источник данных, на котором основан прогноз:  
  
```  
OPENQUERY([<datasource>],'<SELECT statement>')  
  AS [<input alias>]  
```  
  
 Имеется несколько вариантов метода получения исходных данных, но в этом учебнике используется инструкция OPENQUERY. Дополнительные сведения о доступных параметрах см. в разделе [ &#60;запросом источника данных&#62;](/sql/dmx/source-data-query).  
  
 В следующей строке определяется соответствие исходных столбцов в модели интеллектуального анализа данных столбцам исходных данных:  
  
```  
ON <column mappings>  
```  
  
 Предложение WHERE фильтрует результаты, возвращенные прогнозирующим запросом:  
  
```  
WHERE <where clause, boolean expression,>  
```  
  
 Последняя (необязательная) строка кода задает столбец, по которому упорядочиваются результаты:  
  
```  
ORDER BY <expression> [DESC|ASC]  
```  
  
 Использовать ORDER BY в сочетании с ВЕРХНЕЙ \<номер > инструкции для фильтрации возвращенных результатов. Например, в этом прогнозе возвращаются первые десять покупателей велосипедов, упорядоченных по степени вероятности реализации прогноза. Для управления порядком вывода результатов можно использовать синтаксис [DESC|ASC].  
  
#### <a name="to-create-a-batch-prediction-query"></a>Создание пакетного прогнозирующего запроса  
  
1.  В **обозревателя объектов**, щелкните правой кнопкой мыши экземпляр [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], пункты **новый запрос**, а затем нажмите кнопку **расширений интеллектуального анализа данных**.  
  
     Откроется редактор запросов, содержащий новый, пустой запрос.  
  
2.  Скопируйте общий пример пакетной инструкции в пустой запрос.  
  
3.  Вместо  
  
    ```  
    <select list>   
    ```  
  
     вставьте  
  
    ```  
    SELECT  
      TOP 10  
      t.[LastName],  
      t.[FirstName],  
      [Decision Tree].[Bike Buyer],  
      PredictProbability([Bike Buyer])  
    ```  
  
     Предложение TOP 10 указывает, что запрос должен возвратить только десять первых результатов. Инструкция ORDER BY в этом запросе упорядочивает результаты по степени вероятности прогноза, поэтому возвращаются только десять самых вероятных результатов.  
  
4.  Вместо заполнителя:  
  
    ```  
    [<mining model>]   
    ```  
  
     используйте имя модели:  
  
    ```  
    [Decision Tree]  
    ```  
  
5.  Замените следующую универсальную инструкцию OPENQUERY:  
  
    ```  
    OPENQUERY([<datasource>],'<SELECT statement>')  
    ```  
  
     инструкцией, ссылающейся на текущее хранилище данных Adventureworks, например:  
  
    ```  
    OPENQUERY([Adventure Works DW 2014],  
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
    ```  
  
6.  Замените следующий универсальный синтаксис:  
  
    ```  
    <ON clause, mapping,>   
    WHERE <where clause, boolean expression,>  
    ORDER BY <expression>  
    ```  
  
     сопоставлением столбцов, которое требуется для этой модели и входного набора данных:  
  
    ```  
    [Decision Tree].[Marital Status] = t.[MaritalStatus] AND  
      [Decision Tree].[Gender] = t.[Gender] AND  
      [Decision Tree].[Yearly Income] = t.[YearlyIncome] AND  
      [Decision Tree].[Total Children] = t.[TotalChildren] AND  
      [Decision Tree].[Number Children At Home] = t.[NumberChildrenAtHome] AND  
      [Decision Tree].[Education] = t.[Education] AND  
      [Decision Tree].[Occupation] = t.[Occupation] AND  
      [Decision Tree].[House Owner Flag] = t.[HouseOwnerFlag] AND  
      [Decision Tree].[Number Cars Owned] = t.[NumberCarsOwned]  
    WHERE [Decision Tree].[Bike Buyer] =1  
    ORDER BY PredictProbability([Bike Buyer]) DESC  
    ```  
  
     Чтобы первыми вывести наиболее вероятные результаты, задайте `DESC`.  
  
     Полная инструкция теперь должна выглядеть следующим образом.  
  
    ```  
    SELECT  
      TOP 10  
      t.[LastName],  
      t.[FirstName],  
      [Decision Tree].[Bike Buyer],  
      PredictProbability([Bike Buyer])  
    FROM  
      [Decision Tree]  
    PREDICTION JOIN  
      OPENQUERY([Adventure Works DW 2014],  
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
      [Decision Tree].[Marital Status] = t.[MaritalStatus] AND  
      [Decision Tree].[Gender] = t.[Gender] AND  
      [Decision Tree].[Yearly Income] = t.[YearlyIncome] AND  
      [Decision Tree].[Total Children] = t.[TotalChildren] AND  
      [Decision Tree].[Number Children At Home] = t.[NumberChildrenAtHome] AND  
      [Decision Tree].[Education] = t.[Education] AND  
      [Decision Tree].[Occupation] = t.[Occupation] AND  
      [Decision Tree].[House Owner Flag] = t.[HouseOwnerFlag] AND  
      [Decision Tree].[Number Cars Owned] = t.[NumberCarsOwned]  
    WHERE [Decision Tree].[Bike Buyer] =1  
    ORDER BY PredictProbability([Bike Buyer]) DESC  
    ```  
  
7.  В меню **Файл** щелкните **Сохранить DMXQuery1.dmx как**.  
  
8.  В **Сохранить как** диалоговое окно, перейдите к соответствующей папке и присвойте файлу имя `Batch_Prediction.dmx`.  
  
9. На панели инструментов нажмите кнопку **Выполнить** .  
  
     Запрос возвращает таблицу с именами клиентов, прогноз о том, приобретет ли каждый клиент велосипед, и степень вероятности реализации прогноза.  
  
 Это последний шаг занятия «Покупатель велосипеда». Теперь есть набор моделей интеллектуального анализа данных, которые можно использовать для изучения сходства клиентов и предсказания, будут ли потенциальные клиенты покупать велосипеды.  
  
 Сведения об использовании расширений интеллектуального анализа данных в сценарии потребительской корзины, в разделе [учебника расширений интеллектуального анализа данных «Потребительская корзина»](../../2014/tutorials/market-basket-dmx-tutorial.md).  
  
  
