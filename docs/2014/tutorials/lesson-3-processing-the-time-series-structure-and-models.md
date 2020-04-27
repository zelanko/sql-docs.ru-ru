---
title: Занятие 3. Обработка структуры и моделей временных рядов | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 16e27b57-eae1-47a7-a02c-47b6ed487d87
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 493d27c9836eb765c655eba5bbb004e4d48cde40
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "63042880"
---
# <a name="lesson-3-processing-the-time-series-structure-and-models"></a>Урок 3. Обработка структуры и моделей временных рядов
  На этом занятии для обработки созданных структур интеллектуального анализа данных и моделей интеллектуального анализа данных с использованием временных рядов используется инструкция [INSERT INTO &#40;DMX&#41;](/sql/dmx/insert-into-dmx) .  
  
 При обработке структуры интеллектуального анализа данных службы [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] считывают исходные данные и создают структуры, поддерживающие модели интеллектуального анализа данных. Всегда необходимо выполнять обработку модели интеллектуального анализа данных и структуры при первом создании. Если задана структура интеллектуального анализа данных при использовании инструкции INSERT INTO, инструкция обрабатывает эту структуру и все связанные с ней модели интеллектуального анализа данных.  
  
 При добавлении модели интеллектуального анализа данных к уже обработанной структуре интеллектуального анализа данных можно использовать инструкцию `INSERT INTO MINING MODEL` для обработки новой модели интеллектуального анализа данных с помощью существующих данных.  
  
 Дополнительные сведения об обработке моделей интеллектуального анализа данных см. в разделе [требования к обработке и рекомендации &#40;&#41;интеллектуального анализа ](../../2014/analysis-services/data-mining/processing-requirements-and-considerations-data-mining.md).  
  
## <a name="insert-into-statement"></a>Инструкция INSERT INTO  
 Чтобы обучить структуру интеллектуального анализа данных временных рядов и все связанные с ней модели интеллектуального анализа данных, используйте инструкцию [INSERT в &#40;DMX&#41;](/sql/dmx/insert-into-dmx) . Код инструкции можно разбить на следующие части.  
  
-   Определение структуры интеллектуального анализа данных  
  
-   Список столбцов структуры интеллектуального анализа  
  
-   Определение обучающих данных  
  
 Далее приведен общий пример инструкции `INSERT INTO`:  
  
```  
INSERT INTO MINING STRUCTURE [<mining structure name>]  
(  
   <mining structure columns>  
)  
OPENQUERY (<source data definition>)  
```  
  
 В первой строчке кода задается структура интеллектуального анализа данных, которую необходимо обучить:  
  
```  
INSERT INTO MINING STRUCTURE [<mining structure name>]  
```  
  
 Следующие строки кода указывают столбцы, определенные структурой интеллектуального анализа данных. Необходимо перечислить все столбцы структуры интеллектуального анализа данных, и каждый столбец должен сопоставляться с каким-либо столбцом из данных исходного запроса.  
  
```  
(  
   <mining structure columns>  
)  
```  
  
 Последние строки кода определяют данные, которые будут использованы для обучения структуры интеллектуального анализа данных.  
  
```  
OPENQUERY (<source data definition>)  
```  
  
 На этом занятии требуется определить исходные данные с помощью инструкции `OPENQUERY`. Дополнительные сведения о других методах определения запроса к исходным данным см. в разделе [&#60;Source Data query&#62;](/sql/dmx/source-data-query).  
  
## <a name="lesson-tasks"></a>Задачи занятия  
 На этом занятии требуется выполнить следующую задачу:  
  
-   обработать структуру интеллектуального анализа данных Forecasting_MIXED_Structure;  
  
-   обработать связанные модели интеллектуального анализа данных Forecasting_MIXED, Forecasting_ARIMA и Forecasting_ARTXP.  
  
## <a name="processing-the-time-series-mining-structure"></a>Обработка структуры интеллектуального анализа данных временных рядов  
  
#### <a name="to-process-the-mining-structure-and-related-mining-models-by-using-insert-into"></a>Обработка структуры интеллектуального анализа данных и связанных с ней моделей с помощью инструкции INSERT INTO  
  
1.  В окне **Обозреватель объектов**щелкните правой кнопкой мыши экземпляр служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], укажите **Создать запрос**, а затем выберите пункт **Расширения интеллектуального анализа данных**.  
  
     Откроется редактор запросов, содержащий новый, пустой запрос.  
  
2.  Скопируйте стандартный пример использования инструкции INSERT INTO в пустое окно запроса.  
  
3.  Вместо  
  
    ```  
    [<mining structure>]  
    ```  
  
     на:  
  
    ```  
    Forecasting_MIXED_Structure  
    ```  
  
4.  Вместо  
  
    ```  
    <mining structure columns>  
    ```  
  
     на:  
  
    ```  
    [ReportingDate],  
    [ModelRegion]   
    ```  
  
5.  Вместо  
  
    ```  
    OPENQUERY(<source data definition>)  
    ```  
  
     на:  
  
    ```  
    OPENQUERY([Adventure Works DW 2008R2],'SELECT [ReportingDate], [ModelRegion], [Quantity], [Amount]  
    FROM vTimeSeries ORDER BY [ReportingDate]')  
    ```  
  
     Исходный запрос ссылается на источник [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] данных, определенный в образце проекта интермедиатетуториал. Этот источник данных используется запросом для доступа к представлению vTimeSeries. Это представление содержит исходные данные, которые будут использованы для обучения модели интеллектуального анализа данных. Если вы не знакомы с этим проектом или представлениями, см. раздел[занятие 2. Создание сценария прогнозирования &#40;руководстве по интеллектуальному анализу данных&#41;](../../2014/tutorials/lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial.md).  
  
     Полная инструкция теперь должна выглядеть следующим образом.  
  
    ```  
    INSERT INTO MINING STRUCTURE [Forecasting_MIXED_Structure]  
    (  
       [ReportingDate],[ModelRegion],[Quantity],[Amount])  
    )  
    OPENQUERY(  
    [Adventure Works DW 2008R2],  
    'SELECT [ReportingDate],[ModelRegion],[Quantity],[Amount] FROM vTimeSeries ORDER BY [ReportingDate]'  
    )   
    ```  
  
6.  В меню **Файл** щелкните **Сохранить DMXQuery1.dmx как**.  
  
7.  В диалоговом окне **Сохранить как** перейдите в соответствующую папку и присвойте файлу `ProcessForecastingAll.dmx`имя.  
  
8.  На панели инструментов нажмите кнопку **Выполнить** .  
  
 После окончания выполнения запроса можно создавать прогнозы с использованием обработанных моделей интеллектуального анализа данных. В следующем занятии будет создано несколько прогнозов на основе созданных моделей интеллектуального анализа данных.  
  
## <a name="next-lesson"></a>Следующее занятие  
 [Занятие 4: Создание прогнозов на основе временных рядов с помощью расширений интеллектуального анализа данных](../../2014/tutorials/lesson-4-creating-time-series-predictions-using-dmx.md)  
  
## <a name="see-also"></a>См. также  
 [Требования к обработке и рекомендации &#40;&#41;интеллектуального анализа данных](../../2014/analysis-services/data-mining/processing-requirements-and-considerations-data-mining.md)   
 [&#62;запроса источника данных&#60;](/sql/dmx/source-data-query)   
 [OPENQUERY &#40;РАСШИРЕНИЙ ИНТЕЛЛЕКТУАЛЬНОГО АНАЛИЗА ДАННЫХ&#41;](/sql/dmx/source-data-query-openquery)  
  
  
