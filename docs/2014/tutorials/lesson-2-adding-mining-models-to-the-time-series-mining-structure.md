---
title: 'Занятие 2: Добавление моделей интеллектуального анализа данных для структуры интеллектуального анализа данных временных рядов | Документы Microsoft'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 75c2a74b-21ce-44fb-a26b-68be4c685c12
caps.latest.revision: 16
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: cee3d839ae7a7bcce62c8a3a1d2f7cb62b1155e2
ms.sourcegitcommit: 8c040e5b4e8c7d37ca295679410770a1af4d2e1f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/21/2018
ms.locfileid: "36312492"
---
# <a name="lesson-2-adding-mining-models-to-the-time-series-mining-structure"></a>Занятие 2: Добавление моделей интеллектуального анализа данных для структуры интеллектуального анализа данных временных рядов
  На этом занятии вы добавите новой модели интеллектуального анализа данных для структуры интеллектуального анализа данных, который вы только что создали [занятия 1: Создание модели интеллектуального анализа данных временных рядов и структуры интеллектуального анализа данных](../../2014/tutorials/lesson-1-creating-a-time-series-mining-model-and-mining-structure.md).  
  
## <a name="alter-mining-structure-statement"></a>Инструкция ALTER MINING STRUCTURE  
 Чтобы добавить новую модель интеллектуального анализа данных к существующей структуре интеллектуального анализа данных, используйте [ALTER MINING STRUCTURE &#40;расширений интеллектуального анализа данных&#41;] (инструкция (~/dmx/alter-mining-structure-dmx.md). Код инструкции можно разбить на следующие части:  
  
-   Определение структуры интеллектуального анализа данных  
  
-   Указание имени модели интеллектуального анализа  
  
-   Определение ключевого столбца  
  
-   Определение прогнозируемых столбцов  
  
-   Задание алгоритма и изменений параметров  
  
 В следующем фрагменте показан общий пример инструкции ALTER MINING STRUCTURE.  
  
```  
ALTER MINING STRUCTURE [<mining structure name>]  
ADD MINING MODEL [<mining model name>]  
   ([<key columns>],  
    <mining model columns>  
   )  
USING <algorithm name>([<algorithm parameters>])  
[WITH DRILLTHROUGH]  
```  
  
 В первой строке кода идентифицируется существующая структура интеллектуального анализа данных, к которой будут добавлены модели интеллектуального анализа данных:  
  
```  
ALTER MINING STRUCTURE [<mining structure name>]  
```  
  
 В следующей строчке кода модели интеллектуального анализа данных, добавляемой к структуре интеллектуального анализа, присваивается имя:  
  
```  
ADD MINING MODEL [<mining model name>]  
```  
  
 Сведения о присвоении имени объекту в расширениях интеллектуального анализа данных см. в разделе [идентификаторы &#40;расширений интеллектуального анализа данных&#41;](/sql/dmx/identifiers-dmx).  
  
 Следующие строки кода задают столбцы из структуры интеллектуального анализа, которые будут использоваться моделью интеллектуального анализа:  
  
```  
[<key columns>],  
<mining model columns>  
```  
  
 Можно использовать только существующие столбцы структуры интеллектуального анализа, причем первый столбец из списка должен быть ключевым столбцом структуры интеллектуального анализа.  
  
 В следующих строках кода определяется алгоритм интеллектуального анализа, который создает модель интеллектуального анализа данных, и параметры, которые можно задать в алгоритме и указать, можно ли на основании модели интеллектуального анализа выполнять детализацию углублением подробных данных представления в обучающих вариантах.  
  
```  
USING <algorithm name>([<algorithm parameters>])  
WITH DRILLTHROUGH  
```  
  
 Дополнительные сведения о задаваемых параметрах алгоритма см. в разделе [Microsoft Time Series Algorithm Technical Reference](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm-technical-reference.md).  
  
 С помощью следующего синтаксиса можно указать столбец модели интеллектуального анализа, который следует использовать для прогнозирования:  
  
```  
<mining model column> PREDICT  
```  
  
## <a name="lesson-tasks"></a>Задачи занятия  
 На этом занятии будут выполнены следующие задачи.  
  
-   Добавление в структуру новой модели интеллектуального анализа временных рядов.  
  
-   Изменение параметров алгоритма для использования другого метода анализа и прогнозирования  
  
## <a name="adding-an-arima-time-series-model-to-the-structure"></a>Добавление в структуру модели временных рядов ARIMA  
 Первым шагом является добавление новой модели интеллектуального анализа прогнозирования в существующую структуру. По умолчанию [!INCLUDE[msCoName](../includes/msconame-md.md)] алгоритма временных рядов создает модели интеллектуального анализа данных временных рядов с помощью двух алгоритмов — ARIMA и ARTXP — и объединяет результаты. Можно, однако, указать для использования один алгоритм, либо задать смешивание алгоритмов. На этом шаге добавляется новая модель, которая использует только алгоритм ARIMA. Этот алгоритм оптимизирован для долгосрочного прогнозирования.  
  
#### <a name="to-add-an-arima-time-series-mining-model"></a>Добавление модели интеллектуального анализа временных рядов ARIMA  
  
1.  В **обозревателя объектов**, щелкните правой кнопкой мыши экземпляр [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], пункты **новый запрос**, а затем нажмите кнопку **расширений интеллектуального анализа данных** для открытия редактора запросов и создать новый, пустой запрос.  
  
2.  Скопируйте стандартный пример использования инструкции ALTER MINING STRUCTURE в пустое окно запроса.  
  
3.  Вместо  
  
    ```  
    <mining structure name>   
    ```  
  
     вставьте  
  
    ```  
    [Forecasting_MIXED_Structure]  
    ```  
  
4.  Вместо  
  
    ```  
    <mining model name>   
    ```  
  
     вставьте  
  
    ```  
    Forecasting_ARIMA  
    ```  
  
5.  Вместо  
  
    ```  
    <key columns>,  
    ```  
  
     вставьте  
  
    ```  
    [ReportingDate],  
    [ModelRegion]  
    ```  
  
     Следует отметить, что не нужно повторять сведения для типа данных или содержимого, которые предоставлены в инструкции CREATE MINING MODEL, поскольку они уже сохранены в структуре интеллектуального анализа.  
  
6.  Вместо  
  
    ```  
    <mining model columns>  
    ```  
  
     вставьте  
  
    ```  
    ([Quantity] PREDICT,  
    [Amount] PREDICT  
    )  
    ```  
  
7.  Вместо  
  
    ```  
    USING <algorithm name>([<algorithm parameters>])   
    [WITH DRILLTHROUGH]  
    ```  
  
     вставьте  
  
    ```  
    USING Microsoft_Time_Series (AUTO_DETECT_PERIODICITY = .08, FORECAST_METHOD = 'ARIMA')  
    WITH DRILLTHROUGH  
    ```  
  
     В результате инструкция должна выглядеть следующим образом:  
  
    ```  
    ALTER MINING STRUCTURE [Forecasting_MIXED_Structure]  
    ADD MINING MODEL [Forecasting_ARIMA]  
       (  
       ([ReportingDate],  
        [ModelRegion],  
        ([Quantity] PREDICT,  
        [Amount] PREDICT  
       )   
    USING Microsoft_Time_Series (AUTO_DETECT_PERIODICITY = .08, FORECAST_METHOD = 'ARIMA')  
    WITH DRILLTHROUGH  
    ```  
  
8.  В меню **Файл** щелкните **Сохранить DMXQuery1.dmx как**.  
  
9. В **Сохранить как** диалоговое окно, перейдите к соответствующей папке и присвойте файлу имя `Forecasting_ARIMA.dmx`.  
  
10. На панели инструментов нажмите кнопку **Выполнить** .  
  
## <a name="adding-an-artxp-time-series-model-to-the-structure"></a>Добавление в структуру модели временных рядов ARTXP  
 В SQL Server 2005 алгоритм ARTXP использовался по умолчанию и был оптимизирован для краткосрочного прогнозирования. Для сравнения прогнозов, выполняемых тремя алгоритмами временных рядов, будет добавлена еще одна модель, основанная на алгоритме ARTXP.  
  
#### <a name="to-add-an-artxp-time-series-mining-model"></a>Добавление модели интеллектуального анализа временных рядов ARTXP  
  
1.  Скопируйте следующий код в пустое окно запроса.  
  
     Следует отметить, что нет необходимости изменять что-либо, за исключением имени новой модели интеллектуального анализа и значения параметра FORECAST_METHOD.  
  
    ```  
    ALTER MINING STRUCTURE [Forecasting_MIXED_Structure]  
    ADD MINING MODEL [Forecasting_ARTXP]  
       (  
       ([ReportingDate],  
        [ModelRegion],  
        ([Quantity] PREDICT,  
        [Amount] PREDICT  
       )   
    USING Microsoft_Time_Series (AUTO_DETECT_PERIODICITY = .08, FORECAST_METHOD = 'ARTXP')  
    WITH DRILLTHROUGH  
    ```  
  
2.  В меню **Файл** щелкните **Сохранить DMXQuery1.dmx как**.  
  
3.  В **Сохранить как** диалоговое окно, перейдите к соответствующей папке и присвойте файлу имя `Forecasting_ARTXP.dmx`.  
  
4.  На панели инструментов нажмите кнопку **Выполнить** .  
  
 На следующем занятии будет выполнена обработка всех моделей и структуры интеллектуального анализа.  
  
## <a name="next-lesson"></a>Следующее занятие  
 [Урок 3. Обработка структуры и моделей временных рядов](../../2014/tutorials/lesson-3-processing-the-time-series-structure-and-models.md)  
  
## <a name="see-also"></a>См. также  
 [Алгоритм временных рядов](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm.md)   
 [Технический справочник по алгоритму временных рядов (Майкрософт)](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm-technical-reference.md)  
  
  
